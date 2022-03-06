### Quickstart

#### test_codecov.yml
##### summary
* runs pytest and coverage
* publishes to a codecov account
##### In local repo:
* requirements file must be in ```src/requirements.txt```
* codecov token passed as ```codecovtoken``` secret 
* github repo secret name expected is ```CODECOV_TOKEN```
* example github workflow usage on every push:
```
name: Push

on:
  push:
jobs:
  test-codecov:
    uses: fptiangco/github-actions-workflows/.github/workflows/test_codecov.yml@main
    secrets:
       codecovtoken: ${{ secrets.CODECOV_TOKEN }}
```

---
#### build_push.yml
##### summary
* Logs in to dockerhub
* Create a git tag from input
* Builds from dockerfile and pushes image to dockerhub account 
##### inputs
* image_name
* tag
##### In local repo:
* Dockerfile must be in current directory
* github repo secret names expected are ```DOCKER_USER``` and ```DOCKER_PASSWORD```
* example github workflow usage on every tag:
```
name: Tag

on:
  push:
    tags:        
      - '*'
jobs:

  docker-build-push:
    needs: test-codecov
    uses: fptiangco/github-actions-workflows/.github/workflows/build_push.yml@main
    with:
      image_name: ${{github.event.repository.name}}
      tag: ${{github.ref_name}}
    secrets:
      registry_username: ${{secrets.DOCKER_USER}}
      registry_password: ${{secrets.DOCKER_PASSWORD}}

```
