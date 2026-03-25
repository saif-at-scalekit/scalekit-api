# Scalekit API Reference

[![License](https://img.shields.io/github/license/scalar/starter)](https://github.com/scalar/starter/blob/main/LICENSE)
[![Scalekit](https://img.shields.io/badge/Scalekit-Enterprise%20Auth-blue)](https://www.scalekit.com)

Complete API documentation for Scalekit - the enterprise authentication platform that lets you build enterprise-grade authentication for you and your customers.

## Scalar CLI Commands

### 1. Authenticate

Login to Scalar CLI to access authenticated features:

```bash
npx @scalar/cli auth login
```

Opens a browser for authentication. Credentials are stored locally for future sessions.

### 2. Preview Documentation

Start a local development server to preview the API documentation:

```bash
npx @scalar/cli project preview
```

This renders the docs using the Scalekit API registry URL configured in `scalar.config.json`.

### 3. Validate Configuration

Check that your `scalar.config.json` is properly configured:

```bash
npx @scalar/cli project check-config
```

### 4. Deploy Documentation

Deploy the documentation to Scalar's hosting platform:

```bash
npx @scalar/cli project deploy
```

## Project Structure

```
scalekit-api/
├── docs/
│   └── content/            # Guides and documentation
├── scalar.config.json      # Scalar documentation configuration
└── README.md
```

## Configuration

The `scalar.config.json` file controls:

- **Navigation** - Documentation structure and routing
- **OpenAPI Source** - API spec URL (uses Scalar registry)
- **Theme** - Visual styling and branding

The Scalekit API is loaded from the Scalar registry:

```json
{
  "type": "openapi",
  "url": "https://registry.scalar.com/@scalekit-team/apis/scalekit-apis@1.0.0"
}
```

## GitHub Actions

This repository includes a GitHub Action that automatically validates the configuration on every push and pull request. See [`.github/workflows/validate-scalar-configuration.yml`](./.github/workflows/validate-scalar-configuration.yml).

## About Scalekit

Scalekit provides APIs for:

- **Single Sign-On (SSO)** - SAML and OIDC authentication
- **Organization Management** - Customer tenant accounts
- **Admin Portal** - Self-service authentication configuration
- **Directory Sync** - SCIM user/group synchronization

## Resources

- [Scalekit Developer Documentation](https://docs.scalekit.com)
- [Scalar CLI Documentation](https://scalar.com/tools/cli/getting-started)
- [Scalar Configuration Reference](https://github.com/scalar/scalar/blob/main/documentation/configuration.md)
- [Scalekit Support](mailto:support@scalekit.com)

## License

MIT. See [LICENSE](./LICENSE) for details.
