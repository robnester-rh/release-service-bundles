# update-infra-deployments

* This task clones redhat-appstudio/infra-deployments GH repository.
* It then runs a script obtained from the infra-deployment-update-script key in extraData which can modify text files.
* It then generates pull-request for redhat-appstudio/infra-deployments repository using the modified files.


## Parameters
| Name                    | Description                                                                                  | Optional | Default Value                                                                                                                                    |
|-------------------------|----------------------------------------------------------------------------------------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| extraDataJsonPath       | Path to extraData json file. It should contain a key called 'infra-deployment-update-script' | true     | $(workspaces.data.path)/extra_data.json                                                                                                          |
| snapshotPath            | Path to snapshot json file                                                                   | true     | $(workspaces.data.path)/mapped_snapshot.json                                                                                                     |
| originRepo              | URL of github repository which was built by the Pipeline                                     | false    |                                                                                                                                                  |
| revision                | Git reference which was built by the Pipeline                                                | false    |                                                                                                                                                  |
| targetGHRepo            | GitHub repository of the infra-deployments code                                              | true     | redhat-appstudio/infra-deployments                                                                                                               |
| gitImage                | Image reference containing the git command                                                   | true     | registry.redhat.io/openshift-pipelines/pipelines-git-init-rhel8:v1.8.2-8@sha256:a538c423e7a11aae6ae582a411fdb090936458075f99af4ce5add038bb6983e8 |
| scriptImage             | Image reference for SCRIPT execution                                                         | true     | quay.io/mkovarik/ose-cli-git:4.11                                                                                                                |
| sharedSecret            | Secret in the namespace which contains private key for the GitHub App                        | true     | infra-deployments-pr-creator                                                                                                                     |
| githubAppID             | ID of Github app used for updating PR                                                        | true     | 305606                                                                                                                                           |
| githubAppInstallationID | Installation ID of Github app in the organization                                            | true     | 35269675                                                                                                                                         |
