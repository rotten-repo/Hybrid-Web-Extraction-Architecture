# 🕸️ Hybrid Web Extraction & Orchestration Node (Android-Native)

An advanced, mobile-first data orchestration engine designed to bypass enterprise Web Application Firewalls (WAFs) and execute complex asynchronous data extraction pipelines directly on the Android OS. 

This project solves the fundamental flaws of traditional cloud-based web scrapers (IP blocking, strict 2FA, and JS-obfuscation) by leveraging native mobile device fingerprints, background rendering, and stateful session injection.

---

## 🏗️ Core Architectural Features

### 1. 🛡️ Anti-Bot Evasion & Authentication Portability
*   **Cross-Environment JSON Session Injection:** Bypasses brittle automated login flows (2FA/CAPTCHA). Users can authenticate on a desktop browser, export the state as a JSON array, and natively inject those cookies directly into the Android engine for an instantly authenticated state.
*   **Hidden Background DOM Rendering:** For heavy Single Page Applications (SPAs) or sites shielded by Cloudflare JS challenges, the engine dynamically spins up an invisible, physical Android WebView in a background service. It waits for cryptographic challenges to resolve and the DOM to fully render before executing the extraction payload.
*   **Anti-Heuristic Polling (Jitter):** Defeats server-side machine learning heuristics that flag fixed-interval cron jobs by injecting randomized timing variables (Jitter) into the background polling engine, perfectly mimicking organic human traffic patterns.

### 2. 🎯 Multi-Stage Boundary Isolation & Extraction
*   **Pre-Extraction DOM Manipulation:** Executes automated "Click Sequences" prior to extraction to handle lazy-loading, dismiss cookie banners, or open dropdowns, dynamically transitioning the page state.
*   **Hierarchical DOM Scoping:** Prevents selector ambiguity by setting a strict Parent HTML boundary (e.g., locking the search to a specific `<tbody>` or `<div>`), ensuring the engine only traverses relevant nodes.
*   **Indexed Node Traversal:** Allows strict numerical indexing to target specific node iterations (e.g., targeting the 3rd instance of a keyword within the defined boundary).

### 3. 🧠 Multi-Modal Extraction Modalities
The extraction layer is completely agnostic to the target's code quality, supporting:
*   **Contextual Reverse DOM Navigation:** Anchors onto semantic keywords and traverses *up* the DOM tree (Parent Level Traversal) to capture entire container blocks, defeating randomized CSS class names.
*   **Custom JavaScript Injection:** Allows the injection of complete JS functions into the WebView to orchestrate complex formatting (e.g., iterating through ATS job boards and returning structured data arrays).
*   **Native Modalities:** Supports Custom XPath, CSS Selectors, and Regex.

### 4. 🔄 State Management & Edge Transformation
*   **Stateful Delta Tracking:** The engine caches historical extraction payloads in local memory and performs delta-comparisons on subsequent polls. It strictly drops duplicate data, triggering notifications/actions *only* when the target state mutates.
*   **Edge Data Sanitization:** Cleans structural HTML tags and normalizes whitespace anomalies at the edge, delivering a clean text payload via dynamic string interpolation (`$$` variables) to the Android notification system.
*   **Webhook & Distributed API Delivery (HTTP POST):** The architecture is designed for system-agnostic data delivery. Instead of being limited to local Android notifications, the engine can dynamically pipe the sanitized, extracted payload directly to external Webhooks (Zapier/Make/n8n) or custom HTTPS API endpoints. This effectively turns the mobile device into a seamless, decentralized edge-node pipeline feeding directly into enterprise databases.
---

## 🛠️ The Engineering Workflow

**Role:** Systems Architecture, State Management, & Project Orchestration.
**Execution:** Designed the comprehensive system logic, database schema, and background Android threading architecture. Extensively leveraged AI-assisted workflows to rapidly prototype, write, and deploy the native boilerplate code, optimizing for speed and enterprise-grade functional output.

> 🔒 **SECURITY & IP NOTICE: PRIVATE SOURCE CODE**
> *Because this architecture successfully bypasses enterprise Web Application Firewalls (Cloudflare, SEON) and utilizes hidden DOM rendering, the actual source code is kept strictly private to prevent malicious use and protect proprietary intellectual property. This repository serves as an architectural showcase. I am happy to provide a live technical code-walkthrough of the Android background services and extraction logic on a secure screen-share during interviews.*
