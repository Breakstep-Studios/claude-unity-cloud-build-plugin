---
name: unity-cloud-build
description: Interact with the Unity Cloud Build API — list targets, update configs, trigger builds, and more.
user_invocable: true
---

# Unity Cloud Build API Skill

You are helping the user interact with the Unity Cloud Build REST API.

## Setup

Credentials are stored in the project's `.env` file. Load them before making any API call:

```bash
source .env
```

The variables are:
- `UNITY_CLOUD_BUILD_API_KEY` — API key for authentication
- `UNITY_CLOUD_BUILD_ORG_ID` — Organization ID
- `UNITY_CLOUD_BUILD_PROJECT_ID` — Project ID

Each Unity project should have its own `.env` file at the project root with these variables. The `.env` file should be added to `.gitignore` to keep credentials out of version control.

## Base URL

```
https://build-api.cloud.unity3d.com/api/v1/orgs/${UNITY_CLOUD_BUILD_ORG_ID}/projects/${UNITY_CLOUD_BUILD_PROJECT_ID}
```

## Authentication

All requests use the header:
```
Authorization: Basic ${UNITY_CLOUD_BUILD_API_KEY}
```

## Common Operations

### List build targets
```bash
curl -s "$BASE_URL/buildtargets" -H "Authorization: Basic $UNITY_CLOUD_BUILD_API_KEY"
```

### Get a specific build target
```bash
curl -s "$BASE_URL/buildtargets/{buildtargetid}" -H "Authorization: Basic $UNITY_CLOUD_BUILD_API_KEY"
```

### Update a build target
```bash
curl -s -X PUT "$BASE_URL/buildtargets/{buildtargetid}" \
  -H "Authorization: Basic $UNITY_CLOUD_BUILD_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{ ... }'
```

### Trigger a build
```bash
curl -s -X POST "$BASE_URL/buildtargets/{buildtargetid}/builds" \
  -H "Authorization: Basic $UNITY_CLOUD_BUILD_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"clean": false}'
```

### List builds for a target
```bash
curl -s "$BASE_URL/buildtargets/{buildtargetid}/builds" -H "Authorization: Basic $UNITY_CLOUD_BUILD_API_KEY"
```

### Get build status
```bash
curl -s "$BASE_URL/buildtargets/{buildtargetid}/builds/{buildnumber}" -H "Authorization: Basic $UNITY_CLOUD_BUILD_API_KEY"
```

## Instructions

1. Always `source .env` from the project root before making API calls.
2. Never display the API key in output to the user.
3. When listing build targets, format the output as a readable summary (name, platform, enabled status, branch).
4. When updating configs, show the user what will change before making the PUT request.
5. Parse the user's request and determine which API endpoint to call. If the request is ambiguous, ask for clarification.
6. Handle errors gracefully — check HTTP status codes and display meaningful messages.
