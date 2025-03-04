# run-file-udpates

Tekton task to create InternalRequests for each repository that needs to be updated. This information is extracted from
the field `spec.extraData.fileUpdates` in the ReleasePlanAdmission resource.

## Parameters

| Name            | Description                                                   | Optional | Default value                 |
|-----------------|---------------------------------------------------------------|----------|-------------------------------|
| jsonKey         | JSON key where the information is defined                     | Yes      | .spec.extraData.fileUpdates[] |
| fileUpdatesPath | Path to the JSON file containing the key                      | No       |                               |
| snapshotPath    | Path to the JSON string of the Snapshot spec in the data workspace | No | snapshot_spec.json |
| request         | Type of request to be created                                 | Yes      | file-updates                  |
| synchronously   | Whether the task should wait for InternalRequests to complete | Yes      | true                          |

## Changelog

### changes since 0.2
- application name from snapshot is now provided to update-paths

### changes since 0.1
- adds parameter `snapshotPath`.
- calls `update-paths` script to run the `{{ }}` enclosed yq updates set in the `paths` key
  of the defined `fileUpdatesPath` file.
