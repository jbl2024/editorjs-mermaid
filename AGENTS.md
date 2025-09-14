# Repository Guidelines

## Project Structure & Module Organization
- `src/`: Source code (`index.js`, `index.css`). Main entry is `src/index.js`.
- `dist/`: Built UMD bundle (`bundle.js`) exported as `MermaidTool`.
- `webpack.config.js`: Build pipeline (Babel + CSS loaders, Webpack 5).
- `package.json`: Scripts, dependencies (Mermaid, nanoid), metadata.
- `README.md`: Usage and output data reference.

## Build, Test, and Development Commands
- `npm install`: Installs dependencies.
- `npm run build`: Produces production bundle in `dist/bundle.js`.
- `npm run build:dev`: Development build with `--watch` for rapid iteration.

Tip: To test locally in a host app, point Editor.js to `dist/bundle.js`, or use `npm link` to develop against a local project.

## Coding Style & Naming Conventions
- **Language**: JavaScript (CommonJS in source, UMD output).
- **Indentation**: 2 spaces; include semicolons; single quotes preferred.
- **Naming**: `UpperCamelCase` for classes (e.g., `MermaidTool`), `lowerCamelCase` for functions/variables, kebab-case for files if multiple words.
- **Formatting/Linting**: No enforced linter. Match existing style; if adding tooling, prefer ESLint + Prettier with 2-space indent.

## Testing Guidelines
- No test suite is configured. If contributing tests:
  - Use Jest, place tests under `__tests__/` or co-locate as `*.test.js`.
  - Aim for coverage of parsing/render behavior (e.g., `parse()` error states) with DOM mocks (jsdom).
  - Run via `npm test` (add script) and document any new commands.

## Commit & Pull Request Guidelines
- **Commits**: Conventional Commits style is used in history (e.g., `fix: add dist`, `docs: update jsdelivr url`). Use types like `feat`, `fix`, `docs`, `chore`.
- **PRs**: Include clear description, linked issue(s), and testing notes. When UI behavior changes, add a short GIF/screenshot of the block in Editor.js. Keep PRs focused and small.

## Security & Configuration Tips
- Prefer `MermaidTool.config({...})` via Editor.js `onReady` for mermaid settings; avoid injecting untrusted code.
- Guard against XSS: only render mermaid code from trusted sources; do not enable HTML in captions.
