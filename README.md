# SSH-to-HTTPS

[![Action test on Ubuntu](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/ubuntu-test-action.yml/badge.svg)](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/ubuntu-test-action.yml) [![Action test on MacOS](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/macos-test-action.yml/badge.svg)](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/macos-test-action.yml) [![Action test on Windows](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/windows-test-action.yml/badge.svg)](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/actions/workflows/windows-test-action.yml)

Github Action to reconfigure git to use HTTPS authentication instead of SSH

## 📚 Usage

### Requirements

⚠️    The [`actions/checkout`](https://github.com/marketplace/actions/checkout) is mandatory to use this action, with `persist-credentials: false`.

### Action inputs

Field | Mandatory | Observation
------------ | ------------  | -------------
**github_token** | NO | [How to create a PAT](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

### Without Github PAT

```yaml
      - name: Checkout
        uses: actions/checkout@v2.3.4
        with:
          persist-credentials: false

      - name: Reconfigure git to use HTTPS authentication
        uses: GuillaumeFalourd/SSH-to-HTTPS@v1
```

### With Github PAT

```yaml
      - name: Checkout
        uses: actions/checkout@v2.3.4
        with:
          persist-credentials: false

      - name: Reconfigure git to use HTTPS authentication
        uses: GuillaumeFalourd/SSH-to-HTTPS@v1
        with:
          github_token: ${{ secrets.ACCESS_TOKEN }}
```

_Note: You can use the default `${{ secrets.GITHUB_TOKEN }}` or your PAT with ${{ secrets.ACCESS_TOKEN }}._

## Eventual security concerns

There is no difference in terms of transport security, HTTPS and SSH rely on similar underlying crypto.

Persisting your credentials by adding your [secret Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) to the global git config does have security implications, but it's the default behavior of the [checkout action](https://github.com/actions/checkout) already (using `persist-credentials: true`) so no security is _"lost"_.

_If you don't want the PAT hanging around, run some form of [post-job cleanup](https://github.com/actions/checkout/blob/25a956c84d5dd820d28caab9f86b8d183aeeff3d/src/main.ts#L31)._

## 🤝 Contributing

☞ [Guidelines](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/blob/main/CONTRIBUTING.md)

## 🏅 Licensed

☞ This repository uses the [Apache License 2.0](https://github.com/GuillaumeFalourd/SSH-to-HTTPS/blob/main/LICENSE)
