# Eleva.js 🚀

> **Version:** `1.2.0` | **Size:** ~6KB min (~2.5KB gzip) | **Dependencies:** Zero | **TypeScript:** Yes
>
> *Also known as: elevajs, eleva*

**Best DX + AX for Building the Best UX** — Pure JavaScript, AI-Ready, Simply Elegant.

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![GitHub package.json version](https://img.shields.io/github/package-json/v/tarekraafat/eleva?label=github)](https://github.com/TarekRaafat/eleva)
[![Version](https://img.shields.io/npm/v/eleva.svg?style=flat)](https://www.npmjs.com/package/eleva)
![100% Javascript](https://img.shields.io/github/languages/top/TarekRaafat/eleva?color=yellow)
![Zero Dependencies](https://img.shields.io/badge/dependencies-0-green.svg)
[![codecov](https://codecov.io/gh/TarekRaafat/eleva/branch/master/graph/badge.svg?token=LFA6KENM24)](https://codecov.io/gh/TarekRaafat/eleva)
[![Minified Size](https://badgen.net/bundlephobia/min/eleva@latest)](https://bundlephobia.com/package/eleva@latest)
[![Gzipped Size](https://badgen.net/bundlephobia/minzip/eleva@latest)](https://bundlephobia.com/package/eleva@latest)
[![](https://data.jsdelivr.com/v1/package/npm/eleva/badge?style=rounded)](https://www.jsdelivr.com/package/npm/eleva)

<br>

<p align="center">
  <a href="https://elevajs.com/"><img src="./docs/imgs/eleva.js Full Logo.png" alt="Eleva.js Logo - A minimalist, lightweight pure vanilla JavaScript frontend framework" width="50%"></a>
</p>

<p align="center">
  <a href="https://www.producthunt.com/posts/eleva?embed=true&utm_source=badge-featured&utm_medium=badge&utm_souce=badge-eleva" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=938663&theme=light&t=1741247713068" alt="eleva.js - A&#0032;minimalist&#0044;&#0032;pure&#0032;vanilla&#0032;javascript&#0032;frontend&#0032;framework&#0046; | Product Hunt" style="width: 250px; height: 54px;" width="250" height="54" /></a>
</p>

<br>
<br>
<br>

**A minimalist, lightweight, pure vanilla JavaScript frontend runtime framework.**
_Designed for the best Developer Experience (DX) and **Agent Experience (AX)** to help you build exceptional User Experiences (UX). Built with love for native JavaScript and a minimal core that can be extended through a powerful plugin system — including built-in AI agent support. Because sometimes, less really is more!_ 😊

> **Stable Release**: This is `v1.2.0` - The latest stable release of Eleva.js!



Welcome to Eleva! This is my humble, experimental playground for a fresh approach to frontend development. Eleva was born out of my genuine passion for pure vanilla JavaScript-no frameworks, no bloat, just the power of native code. I hope you'll have fun exploring, testing, and contributing to make Eleva even better. 🚀

---

## What is Eleva.js?

**Eleva** is a minimalist, lightweight (~2.5KB gzipped), pure vanilla JavaScript frontend framework crafted for **exceptional Developer Experience (DX)** and **Agent Experience (AX)**. When developers enjoy building, users enjoy using — Eleva makes it effortless to create beautiful, responsive, and performant User Interfaces (UI) without the complexity, bundle size, or build tool requirements of traditional frameworks.

Unlike React, Vue, or Angular, Eleva:
- **Has zero dependencies** - No node_modules bloat
- **Requires no build step** - Works directly in browsers via CDN
- **Uses real DOM** - No virtual DOM overhead for simple apps
- **Provides signal-based reactivity** - Fine-grained updates like Solid.js
- **Includes TypeScript support** - Built-in type declarations
- **Is AI-agent-ready** - Built-in Agent plugin for LLM integration, action registry, and audit logging
- **Is just JavaScript** - If it works in vanilla JS, it works in Eleva

Eleva is ideal for developers building performance-critical applications, AI-agent-powered interfaces, data-intensive dashboards (10K+ rows), micro-frontends, or anyone seeking a simpler, AI-ready alternative to React, Vue, or Angular.

---

## Table of Contents

- [Eleva.js 🚀](#elevajs-)
  - [What is Eleva.js?](#what-is-elevajs)
  - [Table of Contents](#table-of-contents)
  - [Quick Reference](#quick-reference)
  - [Introduction](#introduction)
  - [Design Philosophy](#design-philosophy)
  - [Best-in-Class Developer Experience (DX) & Agent Experience (AX)](#best-in-class-developer-experience-dx--agent-experience-ax)
  - [Features](#features)
  - [When to Use Eleva](#when-to-use-eleva)
  - [Version Strategy](#version-strategy)
  - [Version Guide](#version-guide)
  - [Performance](#performance)
  - [Performance Benchmarks](#performance-benchmarks)
  - [Eleva vs. Popular Frameworks](#eleva-vs-popular-frameworks)
  - [Browser Support](#browser-support)
  - [Installation](#installation)
  - [Usage](#usage)
    - [ES Module Example](#es-module-example)
    - [UMD Example](#umd-example)
  - [API Reference](#api-reference)
    - [TemplateEngine](#templateengine)
    - [Signal](#signal)
    - [Emitter](#emitter)
    - [Renderer](#renderer)
    - [Eleva (Core)](#eleva-core)
    - [Plugins](#plugins)
      - [Core Framework Only (Lightweight)](#core-framework-only-lightweight)
      - [Attr Plugin](#attr-plugin)
      - [Router Plugin](#router-plugin)
      - [Store Plugin](#store-plugin)
  - [Development](#development)
  - [Testing](#testing)
  - [Contributing](#contributing)
  - [Sponsor Eleva](#sponsor-eleva)
  - [License](#license)
  - [Contact](#contact)

---

## Quick Reference

### Minimal Setup (30 seconds)

```javascript
import Eleva from "eleva";

const app = new Eleva("MyApp");

app.component("Counter", {
  setup: ({ signal }) => ({ count: signal(0) }),
  template: (ctx) => `<button @click="() => count.value++">${ctx.count.value}</button>`
});

app.mount(document.getElementById("app"), "Counter");
```

### API at a Glance

| Method | Purpose |
|--------|---------|
| `new Eleva(name)` | Create app |
| `app.component(name, def)` | Register component |
| `app.mount(el, name)` | Mount to DOM |
| `app.use(plugin)` | Add plugin |
| `signal(value)` | Reactive state |
| `emitter.on/emit` | Events |

### Template Syntax

> **Quick Rule:** `${}` needs `ctx.` — `@events` and `:props` don't.

| Syntax | Use | `ctx.`? |
|--------|-----|:-------:|
| `${expr}` | JS value interpolation | ✓ |
| `@click` | Event handler | ✗ |
| `:prop` | Pass to child | ✗ |

> **How it works:** Use `${ctx.value}` to interpolate values into your template. For `@events` and `:props`, expressions are evaluated against the component context directly — no `ctx.` prefix needed. This allows cleaner syntax like `:user="userData"` instead of `:user="${ctx.userData}"`.

---

## Introduction

Eleva is a lightweight, no-nonsense runtime framework for frontend applications. Built with love for **pure vanilla JavaScript**, Eleva features a minimal core with essential functionality that can be extended through a powerful plugin system. This approach lets you create highly modular and scalable applications without the overhead of large frameworks. I built Eleva to prove that you don't need heavy frameworks or libraries to build amazing user interfaces-sometimes, the simplest approach is the most powerful.

**My Inspiration:**  
The idea behind Eleva comes from a deep appreciation for native JavaScript. I wanted to create a tool that stays true to the language without introducing new syntax or complexity, making it easy to integrate into your projects.

**Core Principles:**

- **🌱 Minimalism:** Only essential features in the core, keeping the framework lean and focused.
- **🔌 Extensibility:** Extend functionality by plugging in your own ideas, such as custom state management, routing, and more.
- **🚀 Performance:** Fast, efficient, and designed with modern browsers in mind.
- **🍦 Pure Vanilla:** No dependencies, no magic-just plain JavaScript.
- **🔍 Transparent:** No hidden layers or abstractions — if it works in vanilla JS, it works in Eleva.

---

## Design Philosophy

**Eleva is an unopinionated framework with a minimal core philosophy.**

Unlike monolithic frameworks that include everything out-of-the-box, Eleva intentionally provides only essential features in its core, relying on a powerful plugin system for extensibility. This architectural choice means:

- **🔄 Flexibility:** Architect your application your way-no rigid structure required.
- **🎯 Native JavaScript:** Built using pure vanilla JavaScript, Eleva integrates seamlessly with your existing code without unfamiliar syntax.
- **⚙️ Configurability:** Extend Eleva's functionality with a simple API and optional plugins.
- **🆓 Freedom:** Decide the best way to implement features without unnecessary constraints.
- **🔍 Transparent:** No magic, no hidden abstractions — what you write is what runs.

### Core Philosophy

> **💡 Vanilla JavaScript. Elevated.**

Eleva takes plain vanilla JavaScript to the next level. Signals for reactivity. Components for structure. Your JS knowledge stays front and center, not hidden behind abstractions. **If it works in vanilla JS, it works in Eleva.**

---

## Best-in-Class Developer Experience (DX) & Agent Experience (AX)

Eleva is built on a simple principle: **great DX + AX leads to great UX**. When developers have intuitive tools — and agents have a first-class integration surface — they build better interfaces. Every aspect of Eleva's design prioritizes your productivity and enjoyment.

**Why Eleva's DX Stands Out:**

| DX Feature | How It Helps You Build Better UX |
|------------|----------------------------------|
| **Zero Config** | Start building immediately — no webpack, no bundlers, no setup |
| **Intuitive API** | Learn in minutes, master in hours — more time for polishing UI |
| **Pure JavaScript** | No JSX, no compilation — what you write is what runs |
| **Instant Feedback** | Signal-based reactivity shows changes immediately |
| **TypeScript Built-in** | Full autocomplete and type safety out of the box |
| **Tiny Bundle** | ~2.5KB gzipped means instant page loads for your users |
| **Agent-Ready (AX)** | Built-in Agent plugin for AI/LLM integration with action registry, audit logging, and permissions |

- **🎨 Craftsmanship:** Every line of code is written with care, keeping the framework lightweight, efficient, and easy to understand.
- **🛠️ Developer-First:** Intuitive API and minimal core mean you spend less time wrestling with the framework and more time perfecting your UI.
- **🌟 No Magic:** Pure vanilla JavaScript with no hidden abstractions — debug easily, ship confidently.
- **🏗️ Scales With You:** From prototype to production, Eleva grows with your project without added complexity.

> _"The best UX comes from developers who love their tools — and agents that speak their framework's language."_ — Eleva's DX + AX philosophy

---

## Features

- **🧩 Component-Based Architecture:** Create reusable UI components with a rich context API
- **⚡ Signal-Based Reactivity:** Fine-grained reactivity that updates only what's needed
- **🔔 Event Handling:** Built-in event emitter for robust inter-component communication
- **📝 Template Parsing:** Dynamic interpolation with a custom TemplateEngine (trusted templates only)
- **🔄 DOM Diffing & Patching:** High-performance updates without a virtual DOM
- **🔄 Lifecycle Hooks:** Complete lifecycle management with before/after mount and update hooks
- **🧹 Automatic Cleanup:** Proper cleanup of resources, watchers, and child components on unmount
- **🔌 Plugin System:** Extensible architecture with a simple plugin API
- **🎯 Built-in Plugins:** Attr for advanced attributes, Router for client-side routing, Store for reactive state management, and Agent for AI/LLM integration (AX)
- **📦 UMD & ES Module Builds:** Supports modern build tools and browser environments
- **🤝 Friendly API:** A gentle learning curve for both beginners and seasoned developers
- **💎 Tiny Footprint & TypeScript Support:** Approximately ~2.5KB gzipped (~6KB minified) with built-in TypeScript declarations

---

## When to Use Eleva

Eleva is ideal for developers seeking a lightweight, flexible, and high-performance solution for building frontend applications. Here are some scenarios where Eleva shines:

- **⚡ Performance-Critical Applications:** 240fps-capable rendering handles everything from simple counters to 10K+ row dashboards (via virtual scrolling).
- **📦 Bundle-Sensitive Projects:** At ~2.5KB gzipped with zero dependencies, ideal for embedded widgets, micro-frontends, and mobile-first apps.
- **🔄 Unopinionated & Flexible:** Architect your application your way with a straightforward API and plugin system.
- **🎯 Developer-Friendly:** Stick to pure vanilla JavaScript with familiar syntax and built-in TypeScript support.
- **🧪 Rapid Prototyping:** Start building immediately—no build tooling required.
- **🔌 Extensible:** Easily add features like routing or state management through plugins.
- **🚀 Built-in Routing:** Advanced client-side routing with navigation guards and reactive state via Router plugin.
- **🎯 Advanced Attributes:** Sophisticated attribute handling with ARIA support via Attr plugin.
- **🏪 Reactive State Management:** Centralized, reactive data store with persistence and namespacing via Store plugin.
- **📦 Module Format Flexibility:** Choose from ESM, CommonJS, or UMD formats based on your project's needs.

---

## Version Strategy

I believe in clear versioning that reflects the maturity of the project:

- **Stable Versions:** Version `1.0.0` and above follow semantic versioning with full backward compatibility guarantees within major versions.
- **Semantic Versioning:** Eleva follows semantic versioning strictly to clearly communicate any breaking changes.

---

## Version Guide

I follow [Semantic Versioning (SemVer)](https://semver.org/):

- **🔢 Major Version:** Breaking changes or major overhauls (e.g., from `1.0.0` to `2.0.0`).
- **🔢 Minor Version:** New features in a backward-compatible manner (e.g., from `1.1.0` to `1.2.0`).
- **🔢 Patch Version:** Backward-compatible bug fixes and minor improvements (e.g., `1.0.1`).
- **📌 Pre-release Identifiers:** Suffixes like `-alpha`, `-beta`, or `-rc` denote unstable releases (e.g., `1.2.0-alpha`).

---

## Performance

Eleva is crafted for performance:

- **Lightweight:** Approximately ~6KB minified and ~2.5KB gzipped.
- **Efficient Reactivity:** Signal-based updates ensure only necessary DOM parts are updated.
- **Optimized Diffing:** Renderer efficiently patches changes without the overhead of a virtual DOM.
- **No Bloat:** Pure vanilla JavaScript with zero dependencies keeps your project nimble.
- **Tree-Shakable:** ESM format allows bundlers to eliminate unused code.
- **Format-Specific Optimizations:** Each module format is optimized for its target environment.

---

## Performance Benchmarks

Benchmarks using [js-framework-benchmark](https://krausest.github.io/js-framework-benchmark/) methodology (1,000 rows):

| **Framework**                 | **Bundle Size (gzipped)** | **Create 1K Rows** (ms) | **Partial Update** (ms) | **Memory** (MB)* |
| ----------------------------- | -------------------------- | ----------------------- | ----------------------- | ---------------- |
| **Eleva** (Direct DOM)        | **~2.5KB**                 | **~25**                 | ~86                     | **~0.5** (Chrome) |
| **React 19** (Virtual DOM)    | ~55KB                      | 40-70                   | 10-20                   | 2-5              |
| **Vue 3.5** (Reactive)        | ~45KB                      | 25-45                   | 5-15                    | 2-4              |
| **SolidJS 1.9** (Signals)     | ~7KB                       | 35-45                   | 5-10                    | 1-2              |
| **Preact 10** (Virtual DOM)   | ~5KB                       | 45-60                   | 10-15                   | 2-3              |
| **Angular 19** (Signals)      | ~62KB                      | 50-80                   | 15-25                   | 3-6              |

**Eleva's Strengths:**
- **Smallest bundle size** (~2.5KB vs 5-62KB gzipped)
- **Competitive initial render** (~25ms for 1K rows)
- **Zero dependencies** and minimal runtime overhead
- **Direct DOM diffing** without virtual DOM overhead

**Performance Tips:**
- Use `key` attribute on list items for optimal diffing
- Eleva excels at initial renders and memory efficiency
- For large lists (10K+ rows), use [virtual scrolling](https://elevajs.com/examples/patterns/lists/virtual-scrolling.html) for **5.5x less memory** and **10x faster creation**
- See [Large List Performance](https://elevajs.com/examples/patterns/best-practices/performance.html#large-list-performance) for detailed patterns and benchmarks

> 💡 **Run benchmarks yourself:** `bun run test:benchmark` | [Detailed benchmark results](https://github.com/TarekRaafat/eleva/blob/master/test/__results__/performance/BENCHMARKS.md)

---

## Eleva vs. Popular Frameworks

How does Eleva compare to popular JavaScript frameworks like React, Vue, Svelte, SolidJS, Preact, and Angular?

| Feature | Eleva 1 | React 19 | Vue 3.5 | Svelte 5 | SolidJS 1.9 | Preact 10 | Angular 19 |
|---------|-----------|----------|---------|----------|-------------|-----------|------------|
| **Bundle Size (gzipped)** | ~2.5KB | ~55KB | ~45KB | ~3KB* | ~7KB | ~5KB | ~62KB |
| **Dependencies** | 0 | 3+ | 0 | 0 | 0 | 0 | 10+ |
| **Virtual DOM** | No | Yes | Yes | No | No | Yes | No |
| **Reactivity** | Signals | useState/Hooks | Refs/Reactive | Compiler | Signals | useState/Hooks | Zone.js |
| **TypeScript** | Built-in | Optional | Optional | Built-in | Built-in | Optional | Built-in |
| **Build Required** | No | Yes | Optional | Yes | Yes | Optional | Yes |
| **Learning Curve** | Low | Medium | Medium | Low | Medium | Low | High |
| **AI/Agent Support** | Built-in | No | No | No | No | No | No |

_*Svelte compiles away, so runtime is minimal but build step is required._

Eleva offers a refreshing alternative to frameworks like React, Vue, and Angular:

- **Simplicity:** No virtual DOM, JSX, or complex state management-just plain JavaScript.
- **Modularity:** Easily extend via plugins to suit your project's needs.
- **Size:** A fraction of the size of mainstream frameworks.
- **Learning Curve:** Familiar syntax and a clear API make it accessible to all developers.

_Note:_ Eleva isn't trying to replace these giants but provides a lightweight option when you want simplicity and speed. 🌟

---

## Browser Support

Eleva targets **modern evergreen browsers** and requires no polyfills.

| Browser | Minimum Version |
|---------|-----------------|
| Chrome | 71+ |
| Firefox | 69+ |
| Safari | 12.1+ |
| Edge | 79+ (Chromium) |
| iOS Safari | 12.2+ |

**Not Supported:** Internet Explorer, Legacy Edge (< 79)

**Why?** Eleva uses modern JavaScript features (`queueMicrotask`, ES6 Classes, async/await) to maintain its tiny footprint. These browsers cover **96%+ of global web traffic**.

> 💡 For legacy browser support, use Babel with appropriate polyfills.

---

## Installation

Eleva is available on npm. Try it out and share your thoughts!

```bash
npm install eleva
```

Or include it directly via CDN:

```html
<!-- jsDelivr (Recommended) -->
<script src="https://cdn.jsdelivr.net/npm/eleva"></script>
```

or

```html
<!-- unpkg -->
<script src="https://unpkg.com/eleva"></script>
```

---

## Usage

### ES Module Example

```js
// Import Eleva (using ES modules)
import Eleva from "eleva";

// Create a new Eleva instance
const app = new Eleva("MyApp");

// Define a component
app.component("HelloWorld", {
  // The setup method is optional; if omitted, an empty state is used.
  setup({ signal }) {
    const count = signal(0);
    return { 
      count,
      onMount: ({ container, context }) => {
        console.log('Component mounted!');
      }
    };
  },
  template: (ctx) => `
    <div>
      <h1>Hello, Eleva! 👋</h1>
      <p>Count: ${ctx.count.value}</p>
      <button @click="() => count.value++">Increment</butt