# Prompt Studio for OpenChamber

**Prompt Express** is a small, focused OpenChamber panel for turning a rough idea into a clear, self-contained prompt. It asks a few useful questions, drafts the final prompt, and lets you review, edit, save, copy, or place it in the OpenChamber composer.

> French UI is available automatically when OpenChamber uses French. The extension never sends the prompt to a session: **Insert in chat** only fills the composer, and you decide whether to send it.

## What it does

- Helps clarify a goal, context, scope, constraints, expected format, and success criteria.
- Asks up to three focused follow-up questions when the answers would change the prompt.
- Creates an editable prompt that stands on its own, marking important unknowns instead of inventing details.
- Saves drafts and a small personal prompt library in OpenChamber extension storage.
- Copies a prompt or inserts it into the current OpenChamber composer.
- Follows the host theme and supports French and English.
- Uses the active project/session title automatically; a session menu action can import the current conversation as optional context.
- Generates through OpenChamber's configured Small Model/provider. It never calls a model provider directly.

## Install

In OpenChamber, open **Settings → Extensions** and add this repository's Git URL, or select the local extension folder. The extension manifest is in `package.json`.

For a local checkout:

1. Clone this repository.
2. Add its folder in **Settings → Extensions**.
3. Enable **Prompt Studio** and open its panel.

To seed Prompt Studio with the discussion you are currently in, open that chat's session menu and choose **Créer un prompt depuis cette discussion**. The session action declares `payload: ["messages"]`, which lets OpenChamber derive the `conversation` permission for that action. The selected discussion text is sent to the configured model only when you send a coaching message or finalize the prompt. The rail panel receives project/session metadata but cannot read the transcript unless you launch this explicit session action.

## Build from source

Requires [Bun](https://bun.sh/) and Node-compatible TypeScript tooling.

```sh
bun install --frozen-lockfile
bun run check
```

`check` runs strict TypeScript checking and bundles the panel into `panel/main.js`. The bundled file is committed because OpenChamber loads extension assets directly and does not compile TypeScript at install time.

## Privacy and permissions

Prompt Studio requests the OpenChamber `model` capability. Its explicit session action requests the `conversation` permission through its `payload: ["messages"]` declaration. It does not add a server, make direct network requests, load remote scripts, collect analytics, or ask for API keys.

- The conversation and final-prompt request are sent to the Small Model configured in OpenChamber only after you submit a message or click **Create final prompt**. Model-provider policies, token usage, and any provider charges are controlled by your OpenChamber configuration.
- Imported chat context is opt-in: it is provided only when you open Prompt Studio from **Create prompt from this conversation**. The extension limits the context to the latest 60 messages and 24,000 characters, does not persist imported transcript text in its prompt library, and offers **Remove context**. The active project directory and session title are passed as context when generation is requested.
- Conversation and project text are treated as untrusted reference material by the coach; they cannot override its prompt-writing rules. The coach drafts instructions only; it does not execute the task or send messages into the active session.
- Drafts and saved prompts are stored through OpenChamber's extension storage for the current host instance. They are not synchronized by this extension between Windows and WSL.
- **Copy** uses the host clipboard API. **Insert in chat** replaces the current composer contents and does not submit the message.
- Treat prompts as potentially sensitive: the text you choose to submit is processed by your configured model provider.

## Compatibility

Targets OpenChamber `>=2.0.0` and uses `@openchamber/sdk` 2.1.1. A Small Model must be configured in OpenChamber for AI coaching and finalization. The prompt editor, saved library, and composer actions do not perform the described task.

## Release checklist

1. Update `version` in `package.json` and add a matching entry to `CHANGELOG.md`.
2. Run `bun install` if dependency metadata changed, then run `bun run check`.
3. Commit the generated `panel/main.js` with the source changes.
4. Push the version change to the Git branch users install. A `v*` tag runs the release workflow; install the repository URL with `#v0.2.1` to pin a release.
5. In OpenChamber, open **Settings → Extensions** to check for updates; Git-installed extensions are checked at most once an hour there. **Check for updates** requests an immediate check.

See the [OpenChamber extension update guide](https://docs.openchamber.dev/extensions/#update) for branch and tag behavior.

## License

MIT. See [LICENSE](LICENSE).
