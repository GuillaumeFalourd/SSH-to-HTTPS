# SSH-to-HTTPS

[![Action test on Ubuntu](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/ubuntu-test-action.yml/badge.svg)](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/ubuntu-test-action.yml) [![Action test on MacOS](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/macos-test-action.yml/badge.svg)](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/macos-test-action.yml) [![Action test on Windows](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/windows-test-action.yml/badge.svg)](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/windows-test-action.yml)

Github Action to configure git to use HTTPS authentication instead of SSH

## 📚 Usage

[![Public workflows that use this action.](https://img.shields.io/endpoint?url=https%3A%2F%2Fapi-endbug.vercel.app%2Fapi%2Fgithub-actions%2Fused-by%3Faction%3DGuillaumeFalourd%SSH-to-HTTPS%26badge%3Dtrue)](https://github.com/search?o=desc&q=GuillaumeFalourd+SSH-to-HTTPS+path%3A.github%2Fworkflows+language%3AYAML&s=&type=Code) ☞ [Who is using this action? 🧑‍💻](https://github.com/search?q=GuillaumeFalourd+SSH-to-HTTPS+path%3A.github%2Fworkflows+language%3AYAML&type=code)

### Requirements

⚠️    The [`actions/checkout`](https://github.com/marketplace/actions/checkout) is mandatory to use this action, with `persist-credentials: false`.

### Without PAT

```yaml
      - name: Checkout
        uses: actions/checkout@v2
        with:
          persist-credentials: false

      - name: Reconfigure git to use HTTPS authentication
        uses: GuillaumeFalourd/SSH-to-HTTPS@v1
```

### With PAT

```yaml
      - name: Checkout
        uses: actions/checkout@v2.3.4
        with:
          persist-credentials: false

      - name: Reconfigure git to use HTTPS authentication
        uses: GuillaumeFalourd/SSH-to-HTTPS@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

## Eventual security concerns

There is no difference in terms of transport security, HTTPS and SSH rely on similar underlying crypto.

Persisting your credentials by adding your [secret Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) to the global git config does have security implications, but it's the default behavior of the [checkout action](https://github.com/actions/checkout) already (using `persist-credentials: true`) so no security is _"lost"_.

_If you don't want the PAT hanging around, run some form of [post-job cleanup](https://github.com/actions/checkout/blob/25a956c84d5dd820d28caab9f86b8d183aeeff3d/src/main.ts#L31)._

## 🤝 Contributing

☞ [Guidelines](https://github.com/GuillaumeFalourd/test-cli-commands-action/blob/main/CONTRIBUTING.md)

## 🏅 Licensed

☞ This repository uses the [Apache License 2.0](https://github.com/GuillaumeFalourd/test-cli-command-action/blob/main/LICENSE)
