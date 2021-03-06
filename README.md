# Publishing a Multi-Platform Project

## Documentation

To find more detailed documentation, please visit https://docs.valist.io

## Usage

### Configuring platform/architecture mappings

```yaml
name: Valist Publish
on:
  release:
    types: [published]
jobs:
  valist-publish:
    runs-on: ubuntu-latest
    steps:
      - uses: robinraju/release-downloader@v1.3
        with:
          repository: "awantoch/valist-publish-gha-example"
          latest: true
          tarBall: true
          zipBall: true
          fileName: "*"
      - uses: valist-io/valist-github-action@v2.3.0
        with:
          private-key: ${{ secrets.VALIST_SIGNER }}
          account: test0987-1
          project: test
          release: ${{ github.ref_name }}
          path: '.'
          install-name: 'hello-go'
          install-darwin-amd64: './hello-darwin-amd64'
          install-darwin-arm64: './hello-darwin-arm64'
          install-linux-amd64: './hello-linux-amd64'
          install-windows-amd64: './hello-windows-amd64'
          
```

Then, create a GitHub Release with the hello-* binaries in the uploader. Voila!

## View on Valist

To view this project on Valist, navigate to the following link!

<https://app.valist.io/test0987-1/test>
