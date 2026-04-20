# Zidatel Integration

A Node.js middleware service that integrates with the [Zidatel](https://zidatel.com) open source identity management platform.

## Overview

This service acts as a middleware layer between your applications and Zidatel's identity APIs, providing a unified interface for authentication, authorization, and identity lifecycle management.

## Features

- Zidatel API integration (authentication, user management, roles & permissions)
- Middleware layer for seamless identity operations
- RESTful API endpoints for downstream service consumption
- Token validation and session management

## Tech Stack

- **Runtime**: Node.js
- **Language**: JavaScript / TypeScript
- **Framework**: Express.js (or similar)
- **Identity Provider**: Zidatel (open source identity management)

## Getting Started

### Prerequisites

- Node.js >= 18.x
- npm or yarn
- A running Zidatel instance

### Installation

```bash
git clone https://github.com/mehtabhassan1995/Zidatel-Integration.git
cd Zidatel-Integration
npm install
```

### Configuration

Copy the example environment file and fill in your Zidatel instance details:

```bash
cp .env.example .env
```

| Variable | Description |
|---|---|
| `ZIDATEL_BASE_URL` | Base URL of your Zidatel instance |
| `ZIDATEL_CLIENT_ID` | OAuth client ID |
| `ZIDATEL_CLIENT_SECRET` | OAuth client secret |
| `PORT` | Port for this middleware service (default: 3000) |

### Running

```bash
# Development
npm run dev

# Production
npm start
```

## Project Structure

```
Zidatel-Integration/
├── src/
│   ├── config/         # Configuration and environment setup
│   ├── middleware/     # Express middleware (auth, logging, error handling)
│   ├── routes/         # API route definitions
│   ├── services/       # Zidatel API service layer
│   └── index.js        # Application entry point
├── .env.example
├── package.json
└── README.md
```

## API Reference

Documentation for available endpoints will be added as the service grows.

## Contributing

Contributions are welcome. Please open an issue or submit a pull request.

## License

MIT
