# Dugo+ OpenCode starter: System Admin screens

Setup
1. Put this folder at your project root and run `opencode` in it.
2. Authenticate Figma MCP when prompted (`opencode mcp auth figma`, or follow the in-app prompt).
3. Pick Gemini Flash as the model in OpenCode (/models).
4. Use Plan mode (Tab key) for prompts 00-03. Switch to Build mode for 04+.

Scope: **System Admin screens only** (A1 to A9, see `docs/screen-plan.md`). Hospital work is archived in `docs/archive/hospital/`.

Order: prompts/00 -> 01 -> 02 (repeat until NO REMAINING QUESTIONS; Q28 to Q36 are waiting) -> 03 -> 04 -> 05 (one session per screen) -> 06 -> 07.
Start a fresh session for each prompt. State lives in /docs, not in the chat.

Source of truth: `docs/dugo-spec-final.md` (Docu_Final). `docs/dugo-spec.md` is text extracted from the older PDF and is kept as a legacy reference.
# mcp-dugo-admin
