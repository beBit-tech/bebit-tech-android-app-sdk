[![](https://jitpack.io/v/beBit-tech/bebit-tech-android-app-sdk.svg)](https://jitpack.io/#beBit-tech/bebit-tech-android-app-sdk)

# bebit-tech-android-app-sdk

For installaction detial, please see [Installation Document in this repository wiki](https://github.com/beBit-tech/bebit-tech-android-app-sdk/wiki/Installation).

## Automatic test app update PRs

After a tag push or published release, `Request test app SDK update` dispatches the exact SDK version to `beBit-tech/test-android-app`. The receiver checks the JitPack AAR before opening an upgrade PR. Duplicate events reuse the PR; stable and beta versions are included.

Merge the test app receiver first. Set repository secret `WORKFLOW_TRIGGER_TOKEN` to a fine-grained PAT with `test-android-app` repository access and **Actions: read/write** (Metadata remains read-only). The test app also needs its own `SDK_UPDATE_TOKEN` with Contents and Pull requests read/write. See [setup and validation](https://github.com/beBit-tech/test-android-app/blob/main/docs/sdk-update-automation.md).

For an existing tag or a missed event, run this workflow manually with that version. Default `GITHUB_TOKEN`-created tag/release events do not start another workflow: any future automated publisher must dispatch the receiver directly using `WORKFLOW_TRIGGER_TOKEN`, or use an appropriately scoped PAT/App token when publishing.
