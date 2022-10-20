# GHCR-Action

An opinionated workflow to build and upload your docker image to the GitHub Container Registry.

![Sample Image](assets/sample.png)

## Example

```yaml
name: Build Docker Image

on:
  push:
    branches:
      - '*'
    tags:
      - 'v*'

# Required for secrets.GITHUB_TOKEN
permissions:
  packages: write
  contents: read

jobs:
  docker:
    runs-on: ubuntu-latest
    steps:
      - name: GHCR-Action
        uses: KuhlTime/ghcr-action@v1
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
```

Optionally you can add further build-time arguments that get passed to docker on build:

```yaml
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          build-args: |
            MY_ENV_VARIABLE: "Hello GitHub!"
```
