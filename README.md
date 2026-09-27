# PrivacyPilot

A free Chrome extension that protects you from accidentally leaking sensitive information into AI tools. Before you paste content into ChatGPT, Claude, Gemini, Perplexity, or Microsoft Copilot, PrivacyPilot catches sensitive data — API keys, SSNs, credit cards, secrets — and masks it locally, on your device, before it ever leaves your browser. No backend, no database, no accounts, no telemetry.

> **Privacy promise:** Your text never leaves your browser. Detection and masking happen locally on your device. Read the full [Privacy Policy](docs/PRIVACY.md).

## Status

This repository is at the scaffolding stage (V1, issue #1). The build, lint, and test tooling are in place; detection, paste interception, site adapters, the toast UI, and the rules updater land in subsequent issues.

The extension shell is wired up — manifest, background service worker, content script, and per-site adapters for the six supported AI tools — but the core pipeline is still stubbed:

| Module                   | State                                      |
| ------------------------ | ------------------------------------------ |
| `src/detector/rules.ts`  | Stub — `defaultRules` is empty             |
| `src/detector/engine.ts` | Stub — `detect()` returns `[]`             |
| `src/content/masker.ts`  | Stub — `mask()` returns the text unchanged |
| `tests/detector.test.ts` | Placeholder assertion only                 |

## Local development

Requires Node.js 20 or newer.

```bash
git clone https://github.com/Almavj/PrivacyPilot.git
cd PrivacyPilot
npm install
npm run build
```

Then load the extension in Chrome:

1. Open `chrome://extensions`
2. Enable **Developer mode** (top right)
3. Click **Load unpacked** and select the generated `dist/` folder
4. The PrivacyPilot icon appears in the toolbar; click it to see the popup

### Scripts

| Script              | Description                               |
| ------------------- | ----------------------------------------- |
| `npm run dev`       | Start Vite in development mode            |
| `npm run build`     | Build the unpacked extension into `dist/` |
| `npm test`          | Run the Vitest unit tests                 |
| `npm run lint`      | Lint with ESLint                          |
| `npm run format`    | Format with Prettier                      |
| `npm run typecheck` | Type-check with the TypeScript compiler   |

## Documentation

- [Product Requirements (PRD)](docs/PRD.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Privacy Policy](docs/PRIVACY.md)
- [Manual Test Plan](docs/TEST_PLAN.md)

## Support

Open an issue — that is the only support channel. There is no support portal, form, or in-extension reporting button, because the extension collects nothing and sends nothing for us to look up.

https://github.com/Almavj/PrivacyPilot/issues

Include the AI site, your browser, and what you expected to happen. Please don't paste sensitive data into an issue; issues are public and permanent.

## License

MIT — see [LICENSE](LICENSE).
