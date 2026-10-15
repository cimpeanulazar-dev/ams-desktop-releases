# AMS desktop binary distribution

This public repository hosts **compiled, signed desktop releases only** for the private AMS source repository `cimpeanulazar-dev/audit-management-system`.

## Release layout

Publish a GitHub Release containing:
- the signed Linux x86_64 `.AppImage` updater bundle;
- its corresponding `.AppImage.sig` signature;
- `latest.json` pointing to the exact uploaded AppImage URL and containing its signature.

The desktop updater checks:
`https://github.com/cimpeanulazar-dev/ams-desktop-releases/releases/latest/download/latest.json`

Use a valid Tauri 2 static updater manifest, e.g.:

```json
{
  "version": "1.0.5",
  "notes": "Release notes",
  "pub_date": "2026-10-15T12:00:00Z",
  "platforms": {
    "linux-x86_64": {
      "signature": "CONTENTS_OF_THE_MATCHING_APPIMAGE_SIG_FILE",
      "url": "https://github.com/cimpeanulazar-dev/ams-desktop-releases/releases/download/ams-desktop-v1.0.5/ACTUAL_SIGNED_BUNDLE.AppImage"
    }
  }
}
```

The above is a **template, not a published release**. Substitute the actual version, date, signature and uploaded asset URL. Verify the platform key and actual Tauri bundle artifact in CI before release.

## Security
- Never commit signing private keys, passwords, personal access tokens, or client/audit data.
- Releases must be built from approved source revisions, tested and signed with the protected AMS updater signing key.
- Do not publish unverified or unsigned builds as updater releases.
- Source code stays in the private AMS repository.

## Status
Repository created; release publishing and end-to-end updater validation are pending.
