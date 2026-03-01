---
theme: seriph
background: https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80
title: Audio to Color Visualizer
info: |
  ## Audio Visualizer AI
  Astro + TypeScript + Convex + SCSS + ElevenLabs + Vercel AI SDK

  A modern full-stack architecture featuring a real-time Audio-to-Color visualizer.
class: text-center
transition: slide-left
mdc: true
---

# Audio to Color Visualizer

Modern Full-Stack Architecture & Real-time Audio Visualization

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white op-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-3">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 hover:opacity-100">
    <carbon:edit />
  </button>
  <a href="https://github.com/adarshrkumar/The-ATSDC-Stack" target="_blank" alt="GitHub" title="GitHub" class="text-xl slidev-icon-btn opacity-50 hover:opacity-100">
    <carbon:logo-github />
  </a>
</div>

---
layout: default
---

# Modern AI Audio Stack

A high-performance framework combination optimized for speed, developer experience, and real-time capabilities.

<v-clicks>

- 🚀 **Astro 5**: Island architecture with server-side rendering (`output: 'server'`)
- 📘 **TypeScript**: End-to-step type safety across frontend and backend
- ☁️ **Convex**: Real-time database and cloud functions for seamless sync
- 🎨 **Modern SCSS**: Design tokens via **OpenProps** and strict architectural patterns
- 🤖 **Vercel AI SDK**: Seamless integration with OpenAI and other LLM providers
- 🎙️ **ElevenLabs**: High-fidelity AI voice synthesis for emotional audio feedback

</v-clicks>

---
layout: image-right
image: https://images.unsplash.com/photo-1557683316-973673baf926?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80
---

# Flagship Feature
## Audio to Color Visualizer

A sophisticated client-side engine that translates sound into emotional visual feedback in real time.

- **3 Input Modes**: File upload, Speaker/Tab capture, and Microphone
- **Real-time Processing**: Powered by the Web Audio API
- **Emotional Mapping**: Classifies audio into 30+ distinct moods
- **OKLCH Colors**: Generates perceptually uniform HSL colors

---

# Real-time Audio Analysis

The visualization engine (`IndexScript.astro`) extracts complex features using FFT and time-domain analysis.

```ts {all|2-5|7-11|13-17|all}
// Key features extracted in every frame:
const features = {
    energy:     (sum / N) / 255,           // Perceived volume
    brightness: logCentroid / Math.log2(N), // Spectral centroid
    tempo:      calculateTempo(onsetTimes), // Estimated BPM
    
    // Advanced psychoacoustic metrics:
    flux:             rawFlux / totalAmplitude,
    flatness:         geoMean / arithMean,
    roughness:        adjacentStrongBinEnergy,
    spectralContrast: peakValleyDifference,
    
    // Tonal features:
    chromaStrength:   maxPitchStrength,
    tonnetz:          tonalCoherence,
    harmonicRatio:    harmonicEnergy / totalAmplitude
};
```

---
layout: center
class: text-center
---

# Mood Classification Logic

The system maps audio features to emotional states using a multi-dimensional heuristic.

<div class="grid grid-cols-3 gap-4 mt-8">
  <div v-click class="p-4 border border-gray-700 rounded bg-gray-900/50">
    <h3 class="text-blue-400">Calm</h3>
    <p class="text-sm">Low Energy + Low Brightness</p>
    <div class="text-xs opacity-50 italic">Peaceful, Serene, Meditative</div>
  </div>
  <div v-click class="p-4 border border-gray-700 rounded bg-gray-900/50">
    <h3 class="text-yellow-400">High Energy</h3>
    <p class="text-sm">High Energy + High Brightness</p>
    <div class="text-xs opacity-50 italic">Excited, Euphoric, Uplifting</div>
  </div>
  <div v-click class="p-4 border border-gray-700 rounded bg-gray-900/50">
    <h3 class="text-red-400">Intense</h3>
    <p class="text-sm">High Roughness + High Energy</p>
    <div class="text-xs opacity-50 italic">Angry, Furious, Powerful</div>
  </div>
</div>

---
layout: two-cols
---

# Engineering Standards
## SCSS Architecture

We follow a strict, semantic styling methodology powered by **OpenProps**.

- **No Inline Styles**: All styles in external `.scss` files
- **Semantic Classes**: No utility-first classes (anti-Tailwind)
- **Data Attributes**: Used for variants and states
  - `data-variant="primary"`
  - `data-state="loading"`
- **Design Tokens**: Standardized via OpenProps (`--size-*`, `--shadow-*`)

::right::

<div class="pl-8 pt-10">

```scss
// src/styles/components/button.scss
.btn {
  @include button-base;

  &[data-variant='primary'] {
    @include button-primary;
  }

  &[data-state='loading'] {
    pointer-events: none;
    &::after { ... }
  }
}
```

</div>

---

# Real-time Backend with Convex

Convex handles our persistence layer with automatic reactivity and simplified cloud functions.

```ts
// convex/tracks.ts
export const createTrack = mutation({
    args: {
        title: v.string(),
        storageId: v.id('_storage'),
        mimeType: v.string(),
    },
    handler: async (ctx, args) => {
        const id = await ctx.db.insert('tracks', {
            ...args,
            uploadedAt: Date.now(),
        });
        return await ctx.db.get(id);
    },
});
```

- **Type Safety**: End-to-end types generated from schema
- **Zero Config**: No managing migrations or connection pools
- **File Storage**: Built-in support for audio file uploads

---

# AI Integration & Search

The stack leverages **Vercel AI SDK**, **ElevenLabs**, and **Exa Search** for intelligent features.

<div grid="~ cols-3 gap-8" m="t-10">

<div>
<h3>Vercel AI SDK</h3>
<ul>
  <li>Standardized API for LLMs</li>
  <li>Streaming responses</li>
  <li>Unified provider interface</li>
</ul>
</div>

<div>
<h3>ElevenLabs</h3>
<ul>
  <li>AI Voice synthesis</li>
  <li>Real-time mood narration</li>
  <li>Secure API Key usage</li>
</ul>
</div>

<div>
<h3>Exa Search</h3>
<ul>
  <li>Neural search for agents</li>
  <li>Category-aware filtering</li>
  <li>Content extraction</li>
</ul>
</div>

</div>

---
layout: image-left
image: https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80
---

# Tooling & Infrastructure

- 📱 **PWA**: Fully offline-capable via `vite-plugin-pwa`
- 🧪 **Testing**: Playwright for E2E browser testing
- ⚡ **Deployment**: Vercel for the frontend, Convex for the backend
- 🏗️ **CI/CD**: Automatic checks (`astro check`, `stylelint`) before build

```bash
# Core scripts
npm run dev      # Dev server
npm run convex   # Backend server
npm run check    # Full validation
npm run test     # E2E test suite
```

---
layout: center
class: text-center
---

# Conclusion

The platform provides a robust, type-safe, and real-time foundation for modern web applications, combining the best of server-side performance and interactive client-side experiences.

<div class="mt-12 flex justify-center gap-8">
  <div class="flex flex-col items-center">
    <carbon:logo-github class="text-4xl mb-2"/>
    <span class="text-xs">Open Source</span>
  </div>
  <div class="flex flex-col items-center">
    <carbon:cloud class="text-4xl mb-2"/>
    <span class="text-xs">Cloud Native</span>
  </div>
  <div class="flex flex-col items-center">
    <carbon:flash class="text-4xl mb-2"/>
    <span class="text-xs">Ultra Fast</span>
  </div>
</div>

<PoweredBySlidev mt-10 />
