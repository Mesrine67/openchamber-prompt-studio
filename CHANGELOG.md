# Changelog

## 0.3.0 - 2026-10-08

- Refine the guided prompt flow with a clearer welcome state, larger controls, and a compact composer.
- Move optional agent and model preferences behind a disclosure so prompt writing stays the main task.
- Improve French and English copy, clarify when imported context is sent, and confirm before clearing an active draft.
- Keep the editor actions readable in narrow panels and localize its accessible label.

## 0.2.4 - 2026-10-08

- Align the composer, welcome state and controls with OpenChamber surface, radius and theme tokens.
- Respect light and dark color schemes and remove the lifted hover effect from the send button.

## 0.2.3 - 2026-10-07

- Add agent and model target preferences, including current-session values and custom identifiers, to guide prompt generation.
- Use OpenChamber UI Kit selects, fields, and button for themed target controls and message submission.
- Clarify that target preferences shape the generated prompt and do not change the active chat's agent or model.

## 0.2.2 - 2026-10-07

- Replace starburst-like marks and placeholder glyphs with an original prompt/chat identity and consistent line icons.
- Refine icon buttons and welcome/example surfaces toward a restrained ChatGPT/Codex-style interface while preserving OpenChamber theme colors.

## 0.2.1 - 2026-10-07

- Fix extension installation by declaring only directly supported capabilities; the session action derives conversation access from its messages payload.

## 0.2.0 - 2026-10-07

- Add an explicit session action to seed prompt generation from the selected OpenChamber conversation.
- Include active project/session metadata and bounded, opt-in transcript context in Small Model requests.
- Add guardrails for untrusted context, uncertainty, hallucinated repository claims, and prompt quality.
- Clarify model-provider and transcript privacy behavior.

## 0.1.0 - 2026-10-07

- First public-ready version of the guided prompt-writing panel.
- Add an optional Small Model coach, editable prompt output, local prompt library,
  and safe compose/copy actions.
- Add French and English UI, theme integration, privacy and installation docs.
