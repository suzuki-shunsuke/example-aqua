# example-aqua

Example of [aqua](https://github.com/suzuki-shunsuke/aqua).

* [.github/workflows/test.yml](https://github.com/suzuki-shunsuke/example-aqua/blob/main/.github/workflows/test.yml)
* [aqua.yaml](https://github.com/suzuki-shunsuke/example-aqua/blob/main/aqua.yaml)

## Install tools in CI/CD

In this example, tools are installed in CI with aqua.

[.github/workflows/test.yml](https://github.com/suzuki-shunsuke/example-aqua/blob/main/.github/workflows/test.yml)

```yaml
      - uses: suzuki-shunsuke/aqua-installer@main
        with:
          version: v0.2.0
      - run: aqua i --only-link
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      - run: echo "$PWD/.aqua/bin" >> $GITHUB_PATH

      - run: golangci-lint help
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

## Install tools for this project's local development

Requirements.

* [aqua](https://github.com/suzuki-shunsuke/aqua-installer#shell)
* [GITHUB_TOKEN](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token). The permission `repo` is needed

Add `$HOME/.aqua/bin` to the environment variable `PATH`.

```
$ export PATH=$HOME/.aqua/bin:$PATH
```

Create links.

```
$ aqua i --only-link
```

That's it. For example, `golangci-lint` is installed.

```
$ command -v golangci-lint
$ golangci-lint version
```

## License

[MIT](LICENSE)
