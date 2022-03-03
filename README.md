### Quickstart

#### test_codecov.yml
##### summary
* runs a pytest and coverage
* publishes to a codecov account
##### In local repo:
* requirements file must be in ```src/requirements.txt```
* codecov token passed as ```codecovtoken``` secret 
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


#### build_push.yml
##### summary
* 

##### example usage
* 
```

```
