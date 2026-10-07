# Contributing

Issues and pull requests are welcome. Keep changes focused on the prompt-writing workflow and compatible with the OpenChamber extension SDK.

Before opening a pull request:

1. Install dependencies with `bun install --frozen-lockfile`.
2. Run `bun run check` and include the generated `panel/main.js` when source changes affect it.
3. Update `CHANGELOG.md` for user-visible changes.
4. Do not add analytics, external requests, or additional capabilities without documenting the data flow and reason.

Never include API keys, tokens, private prompts, or personal extension-storage data in issues or commits.
