---
theme: seriph
background: https://images.unsplash.com/photo-1441974231531-c6227db76b6e?ixlib=rb-4.0.3&auto=format&fit=crop&w=2560&q=80
title: Audio to Visualizer - Hack for Humanity 2026
info: |
  ## gem: An Orchestra for the Deaf
  Built for **Hack for Humanity 2026**
  A sustainable, accessibility-first suite for AI music and visualization.
class: text-center
transition: slide-left
mdc: true
---

# gem

**Hack for Humanity 2026**
AI-Powered Music Composition & Real-time Audio Visualization

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white op-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-3">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 hover:opacity-100">
    <carbon:edit />
  </button>
  <a href="https://github.com/adarshrkumar/H4H-26-Project-Code" target="_blank" alt="GitHub" title="GitHub" class="text-xl slidev-icon-btn opacity-50 hover:opacity-100">
    <carbon:logo-github />
  </a>
</div>

---
layout: default
---

# Humanity & Sustainability Mission
## "An Orchestra for the Deaf"

**gem** is designed as a sustainable piece of digital infrastructure, bridging the gap between auditory and visual experiences through efficient, low-impact technology.

<v-clicks>

- 🌍 **Sustainable AI**: Using lean, high-efficiency models to minimize carbon footprint.
- ♿ **Inclusion as Standard**: Designed specifically for the deaf and hard-of-hearing communities.
- ♻️ **Evergreen Design**: Modular architecture (Astro + Convex) ensuring long-term maintainability.
- 🎵 **Emotional Equity**: Providing every human, regardless of hearing ability, the right to "feel" music.

</v-clicks>

---
layout: image-right
image: https://images.unsplash.com/photo-1516733725897-1aa73b87c8e8?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80
---

# Interactive Music Composer

A section-based workflow for guiding AI to generate structured musical tracks.

- **Granular Control**: Define parameters for Intro, Verse, Chorus, Bridge, and Outro.
- **Human-Centric Design**: Focus on emotion and intent rather than just technical prompts.
- **Sustainable Hosting**: Powered by **Vercel Edge** for low-latency, energy-efficient delivery.
- **Streaming Audio**: Real-time cloud persistence via **Convex** for zero-waste data management.

---
layout: image-left
image: https://images.unsplash.com/photo-1550751827-4bd374c3f58b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80
---

# Audio to Color Visualizer

A sophisticated client-side engine that translates sound into emotional visual feedback in real time.

- **Zero-Waste Processing**: 100% client-side analysis; no server-side audio processing required.
- **OKLCH Color Space**: Perceptually uniform colors that respect human vision.
- **Real-time Accessibility**: Zero-latency feedback, critical for live interactions.
- **Multi-Source Input**: Adaptable to any environment—from home to concert halls.

---

# Real-time Audio Analysis

The visualization engine extracts complex features using FFT and time-domain analysis.

```ts {all|2-5|7-11|13-17|all}
// 25+ features extracted in every frame:
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
layout: two-cols
---

# Engineering for Good
## Sustainable Semantic SCSS

Strict architectural patterns using **OpenProps** for minimal CSS weight.

- **Eco-friendly Code**: Minimalist styles reduce bandwidth and battery consumption.
- **Anti-Tailwind**: Clean, semantic markup for better screen reader compatibility.
- **Design Tokens**: Standardized green-palette variables for visual consistency.
- **Zero-JS CSS**: Utilizing Astro's SSR capabilities for maximum efficiency.

::right::

<div class="pl-8 pt-10">

```scss
// Example Component Style
.composer-card {
  @include card-base;
  padding: var(--size-4);
  background: var(--surface-2); // Earthy tone

  &[data-active='true'] {
    border-color: var(--green-5); // Sustainably green
    box-shadow: var(--shadow-4);
  }
}
```

</div>

---

# Backend & Cloud Infrastructure

A reactive, serverless backend optimized for real-time audio data and file handling.

- 🌊 **Convex**: Real-time database for track metadata and user sessions.
- 📁 **UploadThing**: Reliable hosting for generated MP3 files.
- ⚡ **Vercel Edge**: Low-latency execution for AI orchestration.
- 🔒 **Type Safety**: Automatic TypeScript definitions for the entire schema.

```ts
// Real-time track persistence
export const saveSection = mutation({
  args: { trackId: v.id("tracks"), section: v.string(), mood: v.string() },
  handler: async (ctx, args) => {
    return await ctx.db.patch(args.trackId, { [args.section]: args.mood });
  }
});
```

---

# AI Integration Stack

The platform leverages specialized AI providers for music, text, and search.

<div grid="~ cols-3 gap-8" m="t-10">

<div>
<h3>ElevenLabs</h3>
<ul>
  <li><strong>Music API</strong> for track generation</li>
  <li>Voice synthesis for UI feedback</li>
  <li>High-fidelity audio output</li>
</ul>
</div>

<div>
<h3>Vercel AI SDK</h3>
<ul>
  <li><strong>OpenAI</strong> integration for lyrics</li>
  <li>Unified Gateway for LLMs</li>
  <li>Streaming text responses</li>
</ul>
</div>

<div>
<h3>Exa Search</h3>
<ul>
  <li>Neural search for music context</li>
  <li>Category-aware filtering</li>
  <li>Content extraction for agents</li>
</ul>
</div>

</div>

---
layout: image-left
image: https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80
---

# Tooling & Validation

- 🧪 **Testing**: Robust E2E coverage with **Playwright**.
- 🔍 **Linting**: Strict `stylelint` and `eslint` configurations.
- 🏗️ **CI/CD**: Automatic Vercel deployments on every push.
- 📱 **PWA**: Installable experience via `vite-plugin-pwa`.

```bash
# Core workflows
npm run dev      # Local development
npm run convex   # Backend synchronization
npm run test     # Headless browser testing
npm run check    # Type & Astro validation
```

---

# Visualizing Sound for Accessibility
## Making Music Informative & Intuitive

To ensure the experience is both **interactive** and **informative** for the deaf, we employ several mapping methodologies:

<v-clicks>

- 🧠 **Perceptual Uniformity (OKLCH)**: Unlike RGB, OKLCH ensures that changes in brightness and intensity are felt consistently across the color spectrum.
- 🌊 **Kinetic Feedback**: Sound energy is mapped to **physical scale and vibration** (CSS transforms), allowing users to "see" the beat and pressure.
- 🎨 **Emotional Hue Mapping**: High frequencies (treble) map to cooler, sharper hues, while low frequencies (bass) map to warmer, broader hues.
- 📊 **Informative Telemetry**: Real-time energy and frequency data provide a "data-first" layer for those who want to understand the technical structure of the sound.

</v-clicks>

---
layout: center
---

# Live Prototype: Audio-to-Color

<SoundVisualizer />

---
layout: center
class: text-center
---

# Humanity & Sustainability Impact

**gem** redefines the boundary between sound and vision, providing a powerful platform for AI-assisted creativity and accessibility.

<div class="mt-12 flex justify-center gap-8">
  <div class="flex flex-col items-center">
    <carbon:earth class="text-4xl mb-2 text-green-500"/>
    <span class="text-xs">Sustainable Tech</span>
  </div>
  <div class="flex flex-col items-center">
    <carbon:accessibility class="text-4xl mb-2 text-blue-500"/>
    <span class="text-xs">Inclusive Design</span>
  </div>
  <div class="flex flex-col items-center">
    <carbon:flash class="text-4xl mb-2 text-yellow-500"/>
    <span class="text-xs">Human-Centric AI</span>
  </div>
</div>

<PoweredBySlidev mt-10 />
