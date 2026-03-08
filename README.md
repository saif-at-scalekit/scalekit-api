# Scalekit API Reference

[![License](https://img.shields.io/github/license/scalar/starter)](https://github.com/scalar/starter/blob/main/LICENSE)
[![Scalekit](https://img.shields.io/badge/Scalekit-Enterprise%20Auth-blue)](https://www.scalekit.com)

Complete API documentation for Scalekit - the enterprise authentication platform that lets you build enterprise-grade authentication for you and your customers.

## About Scalekit

Scalekit provides APIs to implement:

- **Single Sign-On (SSO)** - Redirect users to authenticate with their chosen Identity Provider (IdP)
- **Organization Management** - Create and manage customer accounts and details
- **Admin Portal APIs** - Let users configure their own authentication from your app
- **Connection APIs** - Control SSO connections to enable/disable them in real-time
- **Directory Sync** - Synchronize users and groups from enterprise directories (SCIM)

## Getting Started

To use the Scalekit API:

1. [Sign up](https://www.scalekit.com) for a Scalekit account
2. Get your credentials from the Scalekit Dashboard > API Config:
   - Client ID
   - Client Secret
   - Environment URL
3. Read the developer documentation at [docs.scalekit.com](https://docs.scalekit.com)

## Preview Documentation

Use the [Scalar CLI](https://scalar.com/tools/cli/getting-started) to render a live preview of the API documentation locally:

```bash
npx @scalar/cli project preview
```

This will start a local development server where you can view and interact with the documentation in real-time.

## Validate Configuration

Ensure your project configuration is properly set up by running the configuration validation command:

```bash
npx @scalar/cli project check-config
```

This will verify that your `scalar.config.json` file contains valid settings and help identify any configuration issues.

### GitHub Action

This repository includes a GitHub Action workflow that automatically validates the configuration on every push and pull request. See [`.github/workflows/validate-scalar-configuration.yml`](./.github/workflows/validate-scalar-configuration.yml).

## Authentication

Scalekit API uses [OAuth2 client credentials](https://www.oauth.com/oauth2-servers/access-tokens/client-credentials) based authentication to consume the APIs. You'll need to obtain an access token using your client credentials before making API requests.

## Project Structure

```
scalekit-api/
├── docs/
│   ├── api-reference/      # OpenAPI specifications for Scalekit endpoints
│   └── content/            # Guides and documentation
├── scalar.config.json      # Scalar documentation configuration
└── README.md
```

## Configuration

All project configuration is managed through the [`scalar.config.json`](./scalar.config.json) file. This file controls:

- Documentation structure and navigation
- OpenAPI document sources
- Theme and styling options
- Build and deployment settings

## API Endpoints

The Scalekit API reference includes:

- **Authentication** - OAuth2 authorization and token management
- **Organizations** - Create and manage customer tenant accounts
- **Connections** - Configure SAML and OIDC SSO connections
- **Directories** - SCIM directory synchronization and management
- **Admin Portal** - Generate admin portal links for customers

## Resources

- [Scalekit Developer Documentation](https://docs.scalekit.com)
- [Scalar Docs](https://scalar.com/products/docs/getting-started)
- [OpenAPI Specification](https://github.com/OAI/OpenAPI-Specification)
- [Scalekit Support](mailto:support@scalekit.com)

## License

This documentation is licensed under MIT. See [LICENSE](./LICENSE) for details.
