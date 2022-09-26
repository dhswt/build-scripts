# Build Scripts > Gitlab

## Container images with Kaniko 

Add to .gitlab-ci.yml

```yaml

include:
  - remote: 'https://raw.githubusercontent.com/dhswt/build-scripts/master/gitlab/ContainerBuildKaniko.yml'

docker-image:
  extends: .BuildImageWithKaniko
  # stage: package

  # overwrite to change defaults for variables below
  # variables:
    # TAG_COMMIT_ENABLE: "true"
    # TAG_COMMIT_PREFIX: "commit-"
    # TAG_REF_SLUG_ENABLE: "true"
    # DOCKERFILE: "$CI_PROJECT_DIR/Dockerfile"
    # CONTEXT_DIR: "$CI_PROJECT_DIR"
    # ADDITIONAL_REGISTRY_DESTINATIONS: ""
    # ADD_GITLAB_REGISTRY_AUTH: "true"

  # add gitlab job dependencies
  # dependencies:
  #  - build

  # only build relevant branches/tags
  # only:
  #   refs:
  #     # - master
  #     - /^env\/.*$/i
  #     - /^v[0-9].*$/i

```
