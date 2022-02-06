# Release Drafter template

> WIP

Repo to POC and template release automation based on PRs with wame principles as conventional commit but enforced on PR instead of commit.

## PR

- Lint PR for conventional commit message. 
- PRs are squashed by default
- Auto labeling to calculate next release and create GitHub release notes

## On default branch

- Update draft release

## Release

- Manually and time based triggers
- Only release when changes are detected
- For first release (or other cases).

### Available outputs of template:

- `steps.release.outputs.upload_url` Assets upload url
- `steps.release.outputs.tag_name`: Tag / version
- `steps.version.outputs.major`: Major version

Adding assets to a release:

```yaml
      - name: Upload Release Asset
        id: upload-release-asset 
        uses: actions/upload-release-asset@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          upload_url: ${{ steps.release.outputs.upload_url }}  
          asset_path: ./my-artifact.zip
          asset_name: my-artifact.zip
          asset_content_type: application/zip
```
