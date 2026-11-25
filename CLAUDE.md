# CLAUDE.md: pulse-frontend

The Pulse web app (Angular), secured with Keycloak.
Architecture and decisions: the `pulse` overview repo (README, docs/adr).

## Stack
- Angular, OIDC Authorization Code + PKCE
- Consumes @marcelstypa/pulse-ui and the generated API client
- nginx Docker image

## Commands
- `npm test`, `npm run lint`, `npm run build`, `npm start`

## Rules
- Public repo: never write secrets, tokens or real credentials; only `*.example` files
- Conventional Commits (`type(scope): subject`), one logical change per commit, never force-push `main`
- Tests and lint must pass before a commit is proposed
- Every API, DB or auth decision that deviates from an ADR needs a new ADR in `pulse/docs/adr`
- Reusable UI goes into pulse-ui, not here
- No secrets in the bundle; runtime config via environment at container start

## Required reading (before any change)
Read these first; they are normative. On conflict with a request: stop and ask.
- `docs/README.md` (index)
- `docs/architecture.md`
- `docs/coding-standards.md`
- `docs/testing.md`
- `docs/git-and-commits.md`, `docs/security.md`, `docs/ai-workflow.md`
- ADRs: `pulse/docs/adr/`
- Threat model: `pulse/docs/threat-model.md` (mandatory for collectors, auth, tenancy, external input)

## Non-negotiables
- Create commits or push only when the user asks; end AI-assisted commits with the Co-Authored-By trailer
- Report real command output; never claim tests pass without running them
- Do not guess versions, config keys or APIs; verify or say unknown
- Update docs in the same change when behaviour or conventions change
