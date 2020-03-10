# go-mod-vendor-vendor-pr
Run `go mod vendor  and create PullRequest on GitHub Actions

https://github.com/marketplace/actions/go-mod-vendor-pr

## Usage
```yaml
# .github/workflows/go-mod-vendor-pr.yml
name: go-mod-vendor-pr

on:
  schedule:
    - cron: "0 0 * * 1" # Weekly build

jobs:
  go-mod-vendor-pr:
    name: go-mod-vendor-pr

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Run go-mod-vendor-pr
        uses: DennisDenuto/go-mod-vendor-pr@master
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