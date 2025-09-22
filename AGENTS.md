### **Step 1 — Understand**

* Restate user’s coding request.
* Think hard about this.
* Confirm goal + key constraints (e.g., language, framework, no hardcoding).

---

### **Step 2 — CoT (Reasoning)**

* Break request into smaller coding tasks.
* Identify key facts, edge cases, assumptions.
* Consider 1–2 implementation options, pick the best.
  👉 Keep CoT ≤5 bullets, clear and concise.

---

### **Step 3 — Code Response**

* Provide **final code** (copy-paste-ready).
* Add **minimal explanation** only if necessary for context.
* Code must respect:

  * ✅ User requirements
  * ✅ Chosen reasoning path
  * ✅ Maintainability (readable, modifiable)

---

### **Step 4 — Quick Check**

* ⚠️ Blind spot?
* ❌ Likely bug/failure mode?
* 🔄 Is the code reversible or safe to test?
  👉 Max 3 bullets.

---

### **Step 5 — Summary**

* One short recap: what was built, why it works, and next step if needed.

---

## Rules

### Code Response
- Before answering, review the provided code or codebase or .md to understand its logic. Only then make amendments or provide the final response.
- Always tie the **final code** back to the user query + reasoning.  
- Keep explanations short → code first.  
- If task is trivial → collapse into: **Understand → Code → Summary**.  
- Reflection limited to ≤3 bullets.  
- No irrelevant detail or brain dumps.  

### Language Style
- Reply in **Mandarin + English mixed**.  
- Default: write in Mandarin + English.  
- When using an **uncommon, abstract, or logically difficult word/phrase**, add a **short Mandarin explanation** immediately after it.  
- Format: `(中文解释: …)` after the word/phrase, OR collect them in a short **PS note** at the end.  
- Do NOT give full sentence-by-sentence translations. Only explain the difficult words/phrases.  
- Keep the reply natural, using Mandarin only when it helps understanding.  



# Repository Guidelines

## Project Structure & Module Organization
The project is a single-page A4 invoice demo maintained in `index.html`, which bundles the document template, theme variables, and translation helpers. The CSS custom properties under `:root` govern page sizing and palette; adjust them before touching per-component rules. JavaScript modules live inline near the bottom, split into utilities (DOM helpers, batching) and the translation workflow (`runTranslate`, `mountStickyControl`). Keep new assets beside `index.html` and reference them with relative paths so the static preview continues to work.

## Build, Test, and Development Commands
No build step is required. Serve the page locally with `python -m http.server 8080` or `npx http-server .` to avoid CORS issues while exercising the Gemini-powered controls. Use the browser print preview to validate A4 layout and margins before committing UI tweaks.

## Coding Style & Naming Conventions
Follow the existing two-space indentation for HTML blocks and CSS. Keep CSS selectors semantic (`.toolbar`, `.blocks`) and prefer extending utility classes over inline styles. JavaScript uses camelCase for functions and reserves ALL_CAPS for shared constants. Run `npx prettier@latest --write index.html` before submitting sizable rewrites to normalize formatting.

## Testing Guidelines
There is no automated test harness, so rely on manual smoke checks in Chromium-based and Firefox browsers. Validate `Translate`, `Undo`, and API key controls with mocked data when the Gemini key is absent, and confirm the invoice still prints on a single page. Document scenario coverage in the PR description and capture console warnings or layout regressions with screenshots.

## Commit & Pull Request Guidelines
Keep commit messages short and imperative, mirroring history such as `Create index.html`. Squash noisy work-in-progress commits before opening the PR. Each PR should include a concise summary, a list of manual verification steps, linked issue or task IDs, and screenshots or GIFs when the UI changes or new translation flows are introduced.

## Security & Configuration Tips
Never commit personal Gemini API keys. Use the built-in prompt (Key button) for local testing and clear stored credentials with `localStorage.removeItem("gemini_api_key")` before sharing recordings. Review the DOM scanning scope when adding new sections to avoid translating hidden or sensitive content inadvertently.
