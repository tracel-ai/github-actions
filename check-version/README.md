# check-version

A simple GitHub Action that verifies the tag version (e.g., `v1.2.3`) matches the version declared in a `Cargo.toml`.

## Inputs

| Name               | Default                  | Description                          |
|--------------------|--------------------------|--------------------------------------|
| `tag`              | `${{ github.ref_name }}` | The tag to compare (e.g., `v1.2.3`). |
| `cargo_toml_path`  | `Cargo.toml`             | Path to the Cargo.toml to read.      |

## Outputs

| Name           | Description                                      |
|----------------|--------------------------------------------------|
| `file_version` | Version read from Cargo.toml                     |
| `tag_version`  | Version parsed from the tag (without `v` prefix) |
| `matches`      | `"true"` or `"false"`                            |

## Example

```yaml
jobs:
  check-version:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: tracel-ai/github-actions/check-version@v8
        with:
          tag: ${{ github.ref_name }}
          cargo_toml_path: Cargo.toml
```
