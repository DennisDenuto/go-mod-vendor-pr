# go-vendor-vendor-pr
Run `go vendor  and create PullRequest on GitHub Actions

https://github.com/marketplace/actions/go-vendor-pr

## Usage
```yaml
# .github/workflows/go-vendor-pr.yml
name: go-vendor-pr

on:
  schedule:
    - cron: "0 0 * * 1" # Weekly build

jobs:
  go-vendor-pr:
    name: go-vendor-pr

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Run go-vendor-pr
        uses: sue445/go-vendor-pr@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          git_user_name: GitHub Actions
          git_user_email: github-actions@example.cpm
```

## Parameters
* `github_token` **Required**
  *  GitHub Token
* `git_user_name` **Required**
  * Username for commit
* `git_user_email` **Required**
  * E-mail for commit
* `base`
  * The base branch in the "[OWNER:]BRANCH" format. Defaults to the default branch of the upstream repository (usually "master").
  * See https://hub.github.com/hub-pull-request.1.html
* `go_vendor_directory` **Required**
  * Directory where `go.mod` is located
  * Default. `.`
* `debug`
  * Whether print debug logging
* `duplicate`
  * Whether create PullRequest even if it has already existed