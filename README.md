# 🧬 Kero - A Cinematic, AI-Powered Research & Analysis Experience

![Status](https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge)
![Vue](https://img.shields.io/badge/vue.js-%234FC08D.svg?style=for-the-badge&logo=vue.js&logoColor=white)
![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Motion](https://img.shields.io/badge/Motion%20One-black?style=for-the-badge&logo=motion&logoColor=white)

Kero is a premium, high-fidelity landing page designed for a modern AI research platform. It features a sophisticated dark-mode aesthetic, blending cinematic landscape photography with advanced glassmorphism and hardware-accelerated motion to create an immersive, professional workspace atmosphere.

---

## 🚀 Features

* **Contextual AI Ecosystem**: Dynamic tab-switching navigation that swaps cinematic background environments and re-triggers core animations using state-driven keys.

* **Glassmorphic Assistant UI**: A floating, high-blur window for "Oliver" (AI Assistant) featuring macOS-inspired window controls and backdrop filters.

* **Atmospheric Ambient Lighting**: A glowing, gradient-driven central sphere and diffuse footer glows that provide depth and visual grounding.

* **Metallic Shimmer Typography**: A custom CSS-shader-inspired watermark footer with a sweeping metallic gloss animation.
  
* **Staggered Feature Grid**: A performant grid of research tools utilizing staggered entrance animations and custom-built geometric SVG icons.

---

## 🛠️ Tech Stack

* **Framework**: Vue 3 (Composition API)

* **Styling**: Tailwind CSS v4

* **Animations**: Framer Motion (Vue)

* **Typography**: Mix of modern Serif (Heading) and clean Sans-serif (UI/Body)

* **Build Tool**: Vite

---

## 🧠 Engineering Highlights

### 1. Key-Based Animation Re-triggering
Utilizes a unique (:key) binding strategy on motion components. When the active tab (Enterprise, Marketing, etc.) changes, the component is forced to re-mount, ensuring that entrance animations play smoothly for every state transition.

### 2. Advanced CSS Masking
Implements (-webkit-mask-image) with radial gradients and elliptical logic to create "cinematic vignettes." This allows high-resolution landscapes to bleed naturally into the deep-black UI background without hard edges.

### 3. Metallic Shimmer Shader
Uses linear-gradient backgrounds clipped to text with an infinite background-position animation to simulate a light source passing over the giant branding watermark.

---

## 📁 Folder Structure

```text
kero-frontend/
├── public/              # Global static assets
├── src/
│   ├── components/      # Modular Cinematic Sections
│   │   ├── Showcase.vue
│   │   ├── RecentArticles.vue
│   │   ├── CTA.vue
│   │   └── Footer.vue
│   ├── App.vue          # Main layout & Section orchestration
│   └── main.js          # Entry point
├── tailwind.config.js   # Custom spacing & color tokens
└── package.json         # Project dependencies
```

---

## Getting Started

### 1. Clone the repository
git clone [https://github.com/YourUsername/KeroLandingPage.git]
cd KeroLandingPage

### 2. Install dependencies
npm install

### 3. Start development server (Laboratory Mode)
npm run dev

### 4. Build for production (Factory Check)
npm run build

---

## Responsive Strategy

### The project utilizes a fluid-density responsive strategy:

* **Dynamic Scaling**: Uses Tailwind's arbitrary value support and CSS **clamp()** for typography that scales smoothly from 320px to 4K displays.

* **Breakpoints**: Optimized for mobile (sm), tablet (md), and high-end desktop (lg/xl).

* **Vignette Adaptation**: Masking percentages on cinematic images adjust dynamically across breakpoints to maintain focal point clarity on vertical mobile screens.

*  **Grid Reflow**: Feature and Article grids transition from **1-column (mobile)** to **3-column (desktop)** layouts with adjusted stagger delays to maintain the "reveal" rhythm.
