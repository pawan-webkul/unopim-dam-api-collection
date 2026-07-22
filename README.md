# UnoPim DAM API Collection

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.postman.com/unopim/unopim-apis)

Postman collection for the **UnoPim Digital Asset Management (DAM)** REST API.

Companion to the [Official UnoPim API collection](https://github.com/unopim/unopim-api-collection) — same workspace, same auth, separate collection.

## What's Included

Base URL: `{{url}}/api/v1/rest`

23 requests across 6 resource groups:

| Resource | Requests |
|---|---|
| Asset | List, Get by ID, Upload, Re-upload, Update, Delete, Download |
| Directory | List, Get by ID, Create, Update, Delete |
| Comment | Get by ID, Create, Delete |
| Property | Get by ID, Create, Update, Delete |
| Tag | Get by ID, Create, Remove |
| Linked Resources | Get by asset ID |

Not yet covered (endpoints exist in the DAM package): `PUT /assets/edit/{id}`,
`GET /assets/signUrlDownload/{id}` (signed), `PUT /comments/{id}`.

## Getting Started

### 1. Import the Collection

Click the **Run in Postman** button above, or manually import:

1. Download `collections/Unopim-DAM-API.postman_collection.json`
2. In Postman → **Import** → select the file

### 2. Import the Environment

1. Download `environments/UnoPim-DAM-Local.postman_environment.json`
2. In Postman → **Environments** → **Import** → select the file
3. Fill in your values:

| Variable | Description |
|---|---|
| `url` | Your UnoPim instance URL (e.g. `http://localhost:8000`) |
| `clientId` | OAuth client ID from UnoPim admin |
| `secret` | OAuth client secret from UnoPim admin |
| `username` | Admin email (e.g. `admin@example.com`) |
| `password` | Admin password |
| `token` | Bearer token — auto-filled after running the Auth request |
| `refreshToken` | Auto-filled after running the Auth request |

### 3. Authenticate

DAM endpoints authenticate with `Authorization: Bearer {{token}}` using the same OAuth 2.0
password grant as the core API. This collection has no auth requests of its own — run
**Authentication by password** from the [Official UnoPim APIs collection](https://github.com/unopim/unopim-api-collection);
it auto-sets `token` and `refreshToken` in the shared environment.

## Repository Setup

The two workflows need these repository secrets (**Settings → Secrets and variables → Actions**):

| Secret | Value |
|---|---|
| `POSTMAN_API_KEY` | Postman API key with access to the `unopim` workspace |
| `POSTMAN_COLLECTION_ID` | UID of the *Unopim DAM API* collection |
| `POSTMAN_ENVIRONMENT_ID` | UID of the DAM environment in Postman |

Get the UIDs from `GET https://api.getpostman.com/collections` and
`GET https://api.getpostman.com/environments` with the same API key.

## Contributing

1. Fork this repository
2. Import the collection + environment into your local Postman
3. Make your changes in Postman → export the updated collection JSON
4. Replace `collections/Unopim-DAM-API.postman_collection.json` with the new export
5. Open a Pull Request with a clear description of what changed

Once merged, the **Push to Postman** GitHub Action automatically syncs the updated collection to the official Postman workspace.

## Workflows

| Workflow | Trigger | Direction |
|---|---|---|
| **Push Collection to Postman** | On push to `main` (collection file changed) | GitHub → Postman |
| **Sync Postman Collection** | On GitHub Release published, or manual dispatch | Postman → GitHub |

Editing in Postman is fine — publish a release (or run *Sync* manually) to pull those edits back into git.
Editing the JSON in git is fine — merging to `main` pushes it to Postman. Avoid doing both at once.

## Links

- [UnoPim Website](https://unopim.com)
- [UnoPim Documentation](https://docs.unopim.com)
- [UnoPim GitHub](https://github.com/unopim/unopim)
- [Official UnoPim API Collection](https://github.com/unopim/unopim-api-collection)
- [Postman Workspace](https://www.postman.com/unopim/unopim-apis)
