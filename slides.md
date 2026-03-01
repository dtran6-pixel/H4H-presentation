---
theme: seriph
background: https://images.unsplash.com/photo-1614613535308-eb5fbd3d2c17?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80
title: gem - AI Music & Visualization
info: |
  ## gem: An Orchestra for the Deaf
  Astro + TypeScript + Convex + SCSS + ElevenLabs + Vercel AI SDK

  A mood-driven creative suite for AI music composition and real-time audio-to-color visualization.
class: text-center
transition: slide-left
mdc: true
---

# gem

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

# Project Mission
## "An Orchestra for the Deaf"

**gem** bridges the gap between auditory and visual experiences, translating complex soundscapes into intuitive, perceptually uniform color data.

<v-clicks>

- 🎵 **Mood-Driven Creation**: Compose original music by defining emotional parameters.
- 🌈 **Living Color**: Visualize any audio source through a deep feature extraction engine.
- ♿ **Accessibility First**: Making the nuances of music visible and "felt" through color.
- 🛠️ **Modern Stack**: Built with Astro 5, Convex, and ElevenLabs for real-time performance.

</v-clicks>

---
layout: image-right
image: https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80
---

# Interactive Music Composer

A section-based workflow for guiding AI to generate structured musical tracks.

- **Granular Control**: Define parameters for Intro, Verse, Chorus, Bridge, and Outro.
- **Emotional Mapping**: Select moods and energy patterns instead of simple text prompts.
- **Lyric Engine**: Auto-generate or write lyrics synchronized with each section.
- **Streaming Audio**: Powered by **ElevenLabs Music API** with real-time cloud persistence.

---
layout: image-left
image: https://images.unsplash.com/photo-1557683316-973673baf926?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80
---

# Audio to Color Visualizer

A sophisticated client-side engine that translates sound into emotional visual feedback in real time.

- **Multi-Source Input**: File uploads, microphone, or browser speaker output.
- **Deep Feature Extraction**: Analyzes **25 distinct audio features** per frame.
- **OKLCH Color Space**: Maps audio "feel" to perceptually uniform colors.
- **Real-time Processing**: Zero-latency analysis using the Web Audio API.

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

# Engineering Standards
## Semantic SCSS

Strict architectural patterns using **OpenProps** design tokens.

- **Anti-Tailwind**: Zero utility classes; all styles are semantic and scoped.
- **Design Tokens**: Standardized variables for sizes, shadows, and colors.
- **Data Attributes**: Managing state and variants cleanly.
- **Clean SSR**: Styled with Astro's zero-JS CSS approach.

::right::

<div class="pl-8 pt-10">

```scss
// Example Component Style
.composer-card {
  @include card-base;
  padding: var(--size-4);
  background: var(--surface-2);

  &[data-active='true'] {
    border-color: var(--blue-5);
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
layout: center
class: text-center
---

# Conclusion

**gem** redefines the boundary between sound and vision, providing a powerful platform for AI-assisted creativity and accessibility.

<div class="mt-12 flex justify-center gap-8">
  <div class="flex flex-col items-center">
    <carbon:logo-github class="text-4xl mb-2"/>
    <span class="text-xs">Open Source</span>
  </div>
  <div class="flex flex-col items-center">
    <carbon:accessibility class="text-4xl mb-2"/>
    <span class="text-xs">Inclusive Design</span>
  </div>
  <div class="flex flex-col items-center">
    <carbon:flash class="text-4xl mb-2"/>
    <span class="text-xs">Real-time Performance</span>
  </div>
</div>

<PoweredBySlidev mt-10 />
