# Frontend architecture

## Responsibility
The Pulse web app: dashboard of uptime, pipelines, CVEs and quality gate for the signed-in tenant, with links into Grafana. Deployed as an nginx container.

## Structure
`core` (auth, interceptors, config), `features/<name>` (lazy-loaded routes with smart components), `shared` (thin glue). Presentational components come from `@marcelstypa/pulse-ui`; they are not duplicated here.

## Rules
- Auth: OIDC Authorization Code + PKCE against Keycloak; route guards plus an interceptor that attaches the token
- API access only through the generated client from the backend OpenAPI spec
- Runtime configuration (API URL, Keycloak URL, realm, client id) is injected at container start, never baked in or secret
- Tenant comes from the token; the UI never sends a tenant id the user can edit
