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

Below is a visual breakdown of the application interface. Each section demonstrates how specific extraction logic, scheduling, and state management features are configured directly on the mobile client.

### 1. Main Orchestration Dashboard
<img src="screenshots/home_ui.jpg" width="400" alt="Main Dashboard"><br>
**Description:** The central hub of the orchestration engine. This interface manages all concurrent extraction tasks (monitors). It displays the target name, the most recent extracted data payload, and provides real-time toggle controls to activate or pause specific data pipelines.

### 2. Task Initialization
<img src="screenshots/adding_scrapper_task.jpg" width="400" alt="Adding Scraper Task"><br>
**Description:** The entry point for building a new data pipeline. Users can input the target URL and begin configuring the specific rules required to parse the DOM of that particular endpoint.

### 3. Multi-Modal Extraction Rules
<img src="screenshots/types_search_technique.jpg" width="400" alt="Extraction Rules Menu"><br>
**Description:** A robust dropdown menu allowing the user to define exactly *how* data is pulled from the DOM. Options allow the engine to adapt to varying target structures by supporting Contextual Parent Traversal, Custom CSS Selectors, XPath, Regular Expressions (Regex), or raw JavaScript Code execution.

### 4. Granular Searching Scope
<img src="screenshots/granular_searching_scope.jpg" width="400" alt="Granular Searching Scope"><br>
**Description:** A critical feature for preventing selector ambiguity. By defining a strict Parent HTML boundary, the engine is forced to limit its DOM traversal to a highly specific node area (e.g., a specific div or table), ensuring accurate data retrieval on messy, deeply nested websites.

### 5. Advanced JavaScript Injection (DOM Parsing)
<img src="screenshots/advanced_search_using_js.jpg" width="400" alt="JavaScript Injection Config"><br>
**Description:** For complex targets like Single Page Applications (SPAs) or heavily obfuscated ATS job boards, users can inject raw, custom JavaScript blocks. This allows the engine to iterate over node arrays, extract nested elements, and return a clean, pre-formatted payload directly to the Android OS.

### 6. Interactive DOM Manipulation (Auto-Click Sequences)
<img src="screenshots/adding_click_in_hidden_webview.jpg" width="400" alt="Auto Click Sequence Setup"><br>
**Description:** Designed to bypass lazy-loading, cookie walls, or hidden UI tabs. Users can define a programmatic "Auto-Click Sequence" targeting specific CSS Selectors. The engine triggers physical click events to mutate the page state *before* initiating the data extraction process.

### 7. Alert Conditions, Jitter, & Scheduling
<img src="screenshots/timer_notification_config.jpg" width="400" alt="Alert Conditions and Timers"><br>
**Description:** The core logic controller for task execution. Users set the base polling interval alongside a randomized `Jitter` variable to spoof organic human traffic and evade bot-detection. It also configures dynamic string interpolation (`$s`), piping the sanitized data payload directly into an Android system notification.

### 8. Cross-Environment Session Import
<img src="screenshots/site_data_injection.jpg" width="400" alt="JSON Cookie Import Dialog"><br>
**Description:** Solves the challenge of strict 2FA and CAPTCHA walls. Users authenticate on a secure desktop environment, export the resulting session cookies as a JSON array, and paste them into this interface. 

### 9. Authenticated Hidden WebView
<img src="screenshots/webview.jpg" width="400" alt="Authenticated WebView"><br>
**Description:** The result of the JSON session injection. The engine dynamically spawns an invisible Android WebView, natively applying the imported cookies to create a fully authenticated, persistent session (e.g., logged into an e-commerce platform) ready for background scraping.

### 10. Extraction History Logs
<img src="screenshots/log_sample.jpg" width="400" alt="Extraction History Log"><br>
**Description:** A localized, chronologically ordered cache of all state mutations. This log tracks historical data deltas extracted from the target, verifying the reliability of the polling intervals and maintaining an auditable timeline of updates.

---

## 🛠️ The Engineering Workflow

**Role:** Systems Architecture, State Management, & Project Orchestration.  
**Execution:** Designed the comprehensive system logic, database schema, and background Android threading architecture. Extensively leveraged AI-assisted workflows to rapidly prototype, write, and deploy the native boilerplate code, optimizing for speed and enterprise-grade functional output.

> 🔒 **SECURITY & IP NOTICE: PRIVATE SOURCE CODE**
> *Because this architecture successfully bypasses enterprise Web Application Firewalls (Cloudflare, SEON) and utilizes hidden DOM rendering, the actual source code is kept strictly private to prevent malicious use and protect proprietary intellectual property. This repository serves as an architectural showcase. I am happy to provide a live technical code-walkthrough of the Android background services and extraction logic on a secure screen-share during interviews.*
