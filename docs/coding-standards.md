# Frontend standards

Claude MUST follow these.

- Same Angular conventions as `pulse-ui`: standalone, OnPush, signals, typed inputs and outputs, strict TypeScript
- Smart components load data and compose; presentational components belong in `pulse-ui`
- RxJS: no nested subscriptions; prefer `async` pipe or `toSignal`; unsubscribe through `takeUntilDestroyed`
- Errors and loading states are handled on every data view
- No tokens or secrets in `localStorage` beyond what the OIDC library manages; no secrets in the bundle
- Lazy-load feature routes; keep bundle budgets in `angular.json`
