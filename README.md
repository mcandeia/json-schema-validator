# JSON Schema Validator

A Github Action for validating JSON using specified JSON schema.

## How to use it?

Create `.github/workflows/<workflow_name>.yml`

```yaml
on:
  pull_request:
    branches:
      - master
name: Pull request workflow
jobs:
  validate_configurations:
    name: Validate configurations
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Validate any json file
        uses: mcandeia/json-schema-validator@v1.0.0
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          send_comment: true
          clear_comments: true
```

| Inputs           | Required | Default | Description                                                                                         |
| ---------------- | -------- | ------- | --------------------------------------------------------------------------------------------------- |
| `token`          | Yes      | -       | GitHub token to access pull request details. GitHub provides one here `${{ secrets.GITHUB_TOKEN }}` |
| `send_comment`   | No       | False   | Create a comment containing validation errors                                                       |
| `clear_comments` | No       | False   | Clear previous error comment(s)                                                                     |
