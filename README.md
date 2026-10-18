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

---

## 📸 UI Overview & Feature Capabilities

Below is a visual breakdown of the application interface, demonstrating how the core extraction logic and state management features are configured directly on the mobile device.

### 1. Main Orchestration Dashboard & Task Creation
<img src="screenshots/home_ui.jpg" width="800" alt="Main Dashboard"><br>
<img src="screenshots/adding_scrapper_task.jpg" width="800" alt="Adding Scraper Task"><br>
The central hub of the engine. Here, multiple concurrent extraction tasks (monitors) are managed and new tasks are initialized. The UI displays the target name, the most recent extracted data payload, and active polling intervals. Users can toggle specific data pipelines on or off in real-time.

### 2. Multi-Modal Extraction Rules
<img src="screenshots/types_search_technique.jpg" width="800" alt="Extraction Rules Menu"><br>
The engine provides a robust dropdown menu for defining exactly how data is pulled from the DOM. Users can adapt to any target structure by selecting Contextual Parent Traversal, Custom CSS Selectors, XPath, Regular Expressions (Regex), or raw JavaScript Code injection.

### 3. Granular Searching Scope
<img src="screenshots/granular_searching_scope.jpg" width="800" alt="Granular Searching Scope"><br>
Prevents selector ambiguity by setting strict HTML boundaries. Users can isolate the extraction engine to only search within a specific Parent Node, ensuring highly accurate data retrieval even on deeply nested and messy DOM structures.

### 4. Advanced JavaScript Injection (DOM Parsing)
<img src="screenshots/advanced_search_using_js.jpg" width="800" alt="JavaScript Injection Config"><br>
For complex pages like modern SPAs or ATS job boards, users can write and inject custom JavaScript blocks. This screen shows a script iterating over node arrays, scraping nested elements, and formatting a clean, structured string output *before* returning the payload to the Android OS.

### 5. Pre-Extraction DOM Manipulation (Auto-Click Sequences)
<img src="screenshots/adding_click_in_hidden_webview.jpg" width="800" alt="Auto Click Sequence Setup"><br>
To bypass lazy-loading, cookie banners, or hidden tabs, users can define an "Auto-Click Sequence". This configuration demonstrates targeting a specific tab, enforcing a programmatic delay, and triggering a physical click event to change the page state prior to data extraction.

### 6. Alert Conditions, Jitter, & State Management
<img src="screenshots/timer_notification_config.jpg" width="800" alt="Alert Conditions and Timers"><br>
This section controls the logic of *when* the engine decides to act:
*   **Trigger Rules:** Set conditions like "Contains Target" to filter noise.
*   **Stateful Tracking:** The "Ignore duplicate alerts" toggle ensures the engine caches the previous state and only pushes notifications upon a data mutation (delta).
*   **Anti-Heuristic Timers:** Allows setting a base Interval alongside a randomized `Jitter` variable (in minutes) to prevent IP blocking by mimicking organic, unpredictable human traffic.

### 7. Cross-Environment JSON Session Injection
<img src="screenshots/site_data_injection.jpg" width="800" alt="JSON Cookie Import Dialog"><br>
<img src="screenshots/webview.jpg" width="800" alt="Authenticated WebView"><br>
To bypass captchas and strict 2FA gates without triggering bot protections, users can export their active session cookies from a desktop browser. The first image shows the interface where this JSON array is pasted. The second image shows the result: the engine instantly injects these cookies into a hidden WebView, spawning a fully authenticated session natively.

### 8. Stateful Delta History Logs
<img src="screenshots/log_sample.jpg" width="800" alt="Extraction History Log"><br>
The engine maintains a localized, chronologically ordered history cache of all state changes. This log displays the historical timeline of updates extracted from a target, proving the engine's reliability in maintaining sessions and tracking variations over extended periods of time.

---

## 🛠️ The Engineering Workflow

**Role:** Systems Architecture, State Management, & Project Orchestration.  
**Execution:** Designed the comprehensive system logic, database schema, and background Android threading architecture. Extensively leveraged AI-assisted workflows to rapidly prototype, write, and deploy the native boilerplate code, optimizing for speed and enterprise-grade functional output.

> 🔒 **SECURITY & IP NOTICE: PRIVATE SOURCE CODE**
> *Because this architecture successfully bypasses enterprise Web Application Firewalls (Cloudflare, SEON) and utilizes hidden DOM rendering, the actual source code is kept strictly private to prevent malicious use and protect proprietary intellectual property. This repository serves as an architectural showcase. I am happy to provide a live technical code-walkthrough of the Android background services and extraction logic on a secure screen-share during interviews.*
