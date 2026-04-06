# Unity Cloud Build Plugin for Claude Code

A Claude Code plugin for interacting with the Unity Cloud Build API — list targets, update configs, trigger builds, and more.

## Installation

```bash
/plugin install Breakstep-Studios/claude-unity-cloud-build-plugin
```

## Per-Project Setup

Each Unity project needs a `.env` file at its root with the following variables:

```env
UNITY_CLOUD_BUILD_API_KEY=your_api_key_here
UNITY_CLOUD_BUILD_ORG_ID=your_org_id_here
UNITY_CLOUD_BUILD_PROJECT_ID=your_project_id_here
```

Make sure `.env` is in your `.gitignore`.

## Usage

Invoke the skill in Claude Code:

```
/unity-cloud-build list build targets
/unity-cloud-build update Unity version on release templates to 6000_3_11f1
/unity-cloud-build trigger a build for template-android-release
/unity-cloud-build get build status for release-0-158-x-ios build #5
```

## Getting Your Credentials

1. **API Key**: Unity Dashboard > Cloud Build > Settings > API Key
2. **Org ID**: Found in your Unity Dashboard URL or organization settings
3. **Project ID**: Found in your Unity Dashboard project settings
