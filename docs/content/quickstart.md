# Quickstart

Welcome to Scalekit API Documentation. Scalekit is an enterprise authentication platform that provides SSO, SCIM, and full-stack authentication for B2B applications.

## About Scalekit

Scalekit provides APIs for:

- **Single Sign-On (SSO)** - SAML and OIDC authentication
- **Organization Management** - Customer tenant accounts
- **Admin Portal** - Self-service authentication configuration
- **Directory Sync** - SCIM user/group synchronization
- **API Tokens** - Machine-to-machine authentication

## Getting Started

### 1. Get Your Credentials

[Sign up](https://www.scalekit.com) for a Scalekit account and get your API credentials from **Dashboard > Developers > Settings > API credentials**:

- **Environment URL** - Your Scalekit environment (e.g., `https://acme.scalekit.dev`)
- **Client ID** - Your application client ID (e.g., `skc_1234567890abcdef`)
- **Client Secret** - Your application client secret (e.g., `test_abcdef1234567890`)

### 2. Get an Access Token

Scalekit uses OAuth2 client credentials grant for machine-to-machine authentication. Request an access token from the token endpoint:

**Request**

```bash
curl -X POST "https://<SCALEKIT_ENVIRONMENT_URL>/oauth/token" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=client_credentials" \
  -d "client_id=<SCALEKIT_CLIENT_ID>" \
  -d "client_secret=<SCALEKIT_CLIENT_SECRET>"
```

**Response**

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIn0...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

The `access_token` is valid for 1 hour (3600 seconds). Store it securely and request a new token when it expires.

### 3. Make Authenticated API Requests

Include the access token in the `Authorization` header as a Bearer token:

**List Organizations**

```bash
curl -X GET "https://<SCALEKIT_ENVIRONMENT_URL>/api/v1/organizations?page_size=10" \
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

**Create a User in an Organization**

```bash
curl -X POST "https://<SCALEKIT_ENVIRONMENT_URL>/api/v1/organizations/{organization_id}/users" \
  -H "Authorization: Bearer <ACCESS_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "user_profile": {
      "first_name": "John",
      "last_name": "Doe"
    },
    "membership": {
      "roles": ["admin"]
    }
  }'
```

## Using SDKs

Scalekit provides SDKs that handle authentication automatically.

### Node.js

```bash
npm install @scalekit-sdk/node
```

```javascript
import { ScalekitClient } from '@scalekit-sdk/node';

const scalekit = new ScalekitClient(
  process.env.SCALEKIT_ENVIRONMENT_URL,
  process.env.SCALEKIT_CLIENT_ID,
  process.env.SCALEKIT_CLIENT_SECRET
);

// List organizations
const { organizations } = await scalekit.organization.listOrganizations();

// Create a user
const { user } = await scalekit.user.createUserAndMembership('org_123', {
  email: 'user@example.com',
  userProfile: { firstName: 'John', lastName: 'Doe' }
});
```

### Python

```bash
pip install scalekit-sdk-python
```

```python
from scalekit import ScalekitClient

scalekit = ScalekitClient(
    environment_url='<SCALEKIT_ENVIRONMENT_URL>',
    client_id='<SCALEKIT_CLIENT_ID>',
    client_secret='<SCALEKIT_CLIENT_SECRET>'
)

# List organizations
organizations = scalekit.organization.list_organizations()

# Create a user
user = scalekit.user.create_user_and_membership(
    organization_id='org_123',
    email='user@example.com',
    user_profile={'first_name': 'John', 'last_name': 'Doe'}
)
```

## Resources

- [Scalekit Developer Documentation](https://docs.scalekit.com)
- [Scalekit Dashboard](https://dashboard.scalekit.com)
- [Scalekit Support](mailto:support@scalekit.com)
