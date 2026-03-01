<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isRecording = ref(false)
const color = ref('oklch(50% 0 0)')
const energy = ref(0)
const frequency = ref(0)
const error = ref('')

let audioContext: AudioContext | null = null
let analyser: AnalyserNode | null = null
let microphone: MediaStreamAudioSourceNode | null = null
let dataArray: Uint8Array | null = null
let animationId: number | null = null

const startVisualizer = async () => {
  try {
    const stream = await navigator.mediaDevices.getUserMedia({ audio: true })
    audioContext = new (window.AudioContext || (window as any).webkitAudioContext)()
    analyser = audioContext.createAnalyser()
    analyser.fftSize = 2048
    
    microphone = audioContext.createMediaStreamSource(stream)
    microphone.connect(analyser)
    
    const bufferLength = analyser.frequencyBinCount
    dataArray = new Uint8Array(bufferLength)
    
    isRecording.value = true
    error.value = ''
    update()
  } catch (err: any) {
    error.value = 'Error accessing microphone: ' + err.message
  }
}

const stopVisualizer = () => {
  if (animationId) cancelAnimationFrame(animationId)
  if (audioContext) audioContext.close()
  isRecording.value = false
}

const update = () => {
  if (!analyser || !dataArray) return
  
  analyser.getByteFrequencyData(dataArray)
  
  // Calculate average energy (volume)
  let sum = 0
  let maxFreq = 0
  let maxVal = 0
  
  for (let i = 0; i < dataArray.length; i++) {
    sum += dataArray[i]
    if (dataArray[i] > maxVal) {
      maxVal = dataArray[i]
      maxFreq = i
    }
  }
  
  const avgEnergy = sum / dataArray.length
  energy.value = avgEnergy / 255
  
  // Calculate a simplified "brightness" or frequency-based hue
  // Using the peak frequency as a proxy
  frequency.value = maxFreq / (dataArray.length / 2)
  
  // Map to OKLCH
  // L: Lightness (energy/volume)
  // C: Chroma (intensity of sound)
  // H: Hue (frequency)
  
  const lightness = Math.max(30, Math.min(90, energy.value * 100))
  const chroma = Math.min(0.37, energy.value * 0.5)
  const hue = frequency.value * 360
  
  color.value = `oklch(${lightness.toFixed(2)}% ${chroma.toFixed(3)} ${hue.toFixed(2)})`
  
  animationId = requestAnimationFrame(update)
}

onMounted(() => {
  // Initialization logic if needed
})

onUnmounted(() => {
  stopVisualizer()
})

const toggle = () => {
  if (isRecording.value) {
    stopVisualizer()
  } else {
    startVisualizer()
  }
}
</script>

<template>
  <div class="flex flex-col items-center gap-6 p-8 border border-white/10 rounded-2xl bg-black/20 backdrop-blur-md">
    <div 
      class="w-64 h-64 rounded-full transition-all duration-150 ease-out shadow-2xl"
      :style="{ 
        backgroundColor: color,
        transform: `scale(${1 + energy * 0.5})`,
        boxShadow: `0 0 ${energy * 100}px ${color}`
      }"
    ></div>
    
    <div class="flex flex-col items-center gap-2">
      <button 
        @click="toggle"
        class="px-6 py-2 rounded-full font-bold transition-all"
        :class="isRecording ? 'bg-red-500 hover:bg-red-600' : 'bg-blue-500 hover:bg-blue-600'"
      >
        {{ isRecording ? 'Stop Experience' : 'Start Experience' }}
      </button>
      
      <p v-if="error" class="text-red-400 text-sm mt-2">{{ error }}</p>
      
      <div v-if="isRecording" class="mt-4 flex flex-col gap-1 text-xs opacity-60 font-mono">
        <div>Energy: {{ energy.toFixed(4) }}</div>
        <div>Freq: {{ frequency.toFixed(4) }}</div>
        <div>Color: {{ color }}</div>
      </div>
    </div>
    
    <div class="max-w-md text-center">
      <p class="text-sm opacity-80">
        This prototype translates sound energy and frequency into a perceptually uniform color experience (OKLCH).
      </p>
    </div>
  </div>
</template>

<style scoped>
.transition-all {
  transition: all 0.1s linear;
}
</style>
