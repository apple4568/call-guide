# Cold Call Guide (iPad Edition)

This is a single-file, highly-optimized cold calling teleprompter web application (`index.html`). It has been specifically redesigned to mitigate decision fatigue and panic-scrolling during high-stress live sales calls.

## Key Features & Architecture

### 1. iPad-Optimized Split-View
To maximize space on an iPad but prevent overwhelming the user:
- **Reader Pane (70% width):** Displays the primary linear call track layout. It utilizes massive `42px` typography, distinct tone indicators, and high-contrast buttons limiting decisions to a maximum of 2-3 choices at any given junction.
- **Handler Dock (30% width):** A persistent vertical column containing global objection handlers (e.g., Gatekeeper, "I'm busy", "Is this a sales call?").

### 2. Context-Aware Linear Track & Stacking UI
The app operates on a JavaScript state machine rather than a messy, branching DOM tree:
- **`globalHistory`:** Tracks the main core path (Prep -> Open -> Discover -> ...)
- **`handlerStack` ("Slide-Overs"):** When an objection handler is tapped from the dock, it injects an "objection card" that physically slides up *over* the main reader pane. This allows the user to read the rebuttal and click "Return to script" when done, guaranteeing they never lose their original place mid-sentence.

### 3. High-Speed Navigation
- **Swipe Gestures:** Swipe left to progress the script (like turning a page) and swipe right to go back.
- **Desktop Fallback:** Arrow Left/Right to navigate, and `Escape` to dismiss objection handler cards.

### 4. Backwards Compatible Support
Recent adjustments were made to ensure native support for older iPads and legacy Safari web views:
- Removed modern CSS properties like `inset: 0` in favor of standard absolute positioning (`top`, `left`, `bottom`, `right`).
- Fixed flexbox height resolution bugs (`height: 100%` replaced with `flex: 1` and `min-height`).
- Ensured JavaScript template literals (`\`` and `${}`) are safely formatted without aggressive Regex escaping that causes parsing failures in older engines.

## Usage

Simply open `index.html` in Safari on an iPad, and optionally save it to the Home Screen as a progressive web app (PWA) to strip away the browser URL bar for a fully immersive, distraction-free environment.
