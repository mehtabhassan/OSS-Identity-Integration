# Identity Integration

A Node.js monorepo that houses middleware integrations for multiple identity and user-management providers behind a consistent interface.

Each provider lives in its own package under [`packages/`](packages/) and is developed, versioned, and consumed independently. The first integration is Clerk; additional providers (e.g. Keycloak) will be added over time as new packages.

## Goals

- Provide a unified middleware layer so downstream apps can switch providers with minimal code change
- Keep each provider self-contained — dependencies, env vars, and routes stay scoped to its package
- Standardize cross-cutting concerns (session verification, user lookup, webhook handling, error shape)

## Supported Providers

| Package | Provider | Status |
|---|---|---|
| [`packages/clerk`](packages/clerk) | Clerk | In progress |
| _additional providers_ | _tbd_ | Planned |

## Tech Stack

- **Runtime**: Node.js (>= 18.x)
- **Language**: JavaScript
- **Framework**: Express.js
- **Workspaces**: npm workspaces

## Repository Layout

```
identity-integration/
├── packages/
│   └── clerk/              # Clerk integration (SDK, middleware, webhooks)
├── .env.example
├── package.json            # Monorepo root (workspaces)
└── README.md
```

Each package under `packages/` owns:

- `src/config/` — provider-specific configuration
- `src/middleware/` — Express middleware (auth, error handling)
- `src/routes/` — API routes exposed by the integration
- `src/services/` — provider SDK wrappers
- `src/webhooks/` — provider webhook handlers
- `package.json` — provider-specific dependencies

## Getting Started

### Prerequisites

- Node.js >= 18.x
- npm >= 9 (for workspaces support)
- Credentials for whichever provider(s) you plan to run

### Installation

```bash
git clone https://github.com/mehtabhassan1995/OSS-Identity-Integration.git
cd OSS-Identity-Integration
npm install
```

This installs dependencies for the root and every workspace under `packages/`.

### Configuration

Copy the example environment file and fill in the credentials for the provider(s) you intend to run:

```bash
cp .env.example .env
```

Env vars are grouped per provider in `.env.example`. You only need to populate the section(s) for the provider(s) you're enabling.

### Running a Provider

Run a specific package via its workspace name:

```bash
# Development (hot reload)
npm run dev --workspace packages/clerk

# Production
npm start --workspace packages/clerk
```

## Adding a New Provider

1. Create a new directory under `packages/<provider>/`
2. Add a `package.json` scoped to that provider's dependencies
3. Follow the standard package layout (`config/`, `middleware/`, `routes/`, `services/`, `webhooks/`)
4. Add a provider-specific section to the root `.env.example`
5. Register the package in the Supported Providers table above

## Contributing

Contributions are welcome. Please open an issue or submit a pull request.

## License

MIT
