# SSH-to-HTTPS

Github Action to reconfigure git to use HTTP authentication instead of SSH

## Security concerns

There is no difference in terms of transport security, HTTPS and SSH rely on similar underlying crypto. 

Persisting your credentials by adding your [secret Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) to the global git config does have security implications, but it's the default behavior of the [checkout action](https://github.com/actions/checkout) already (using `persist-credentials: true`) so no security is _"lost"_.

_If you don't want the PAT hanging around, run some form of [post-job cleanup](https://github.com/actions/checkout/blob/25a956c84d5dd820d28caab9f86b8d183aeeff3d/src/main.ts#L31)._

## How to use

You need to use this action after the `actions/checkout` (with `persist-credentials: false`):

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
