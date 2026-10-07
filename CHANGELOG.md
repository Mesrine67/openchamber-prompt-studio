# Changelog

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
