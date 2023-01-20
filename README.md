# Github Actions Publish Action
This action publishes github actions by tagging the repository.
If the action is a Javascript action, the action will commit either the `dist` directory if it exists
or the `node_modules` directory if it exists, even if these directories are in the `.gitignore`.

## Inputs
### `tag`

**Required** The name of the git tag to use to tag the action.

## Example usage

```yaml
name: Deploy Javascript Action
steps:
  - uses: actions/checkout@v3
  - name: Use Node.js ${{ matrix.node-version }}
    uses: actions/setup-node@v2
    with:
      node-version: ${{ matrix.node-version }}
  - run: npm ci
  - name: Publish action
    uses: github-actions-publish/publish-action@v1
    with:
      tag: v1
```