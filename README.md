# ts-infi-authkey-action

This action is designed to be used with the [Tailscale GitHub Action](https://github.com/tailscale/github-action). It provides an authkey that is generated using OAuth credentials and the [ts-infi-authkey](https://github.com/nfielder/ts-infi-authkey) utility.

It is suggested to the store the values for the inputs `client_id` and `client_secret` as GitHub Actions secrets.

## Usage

```yaml
- name: Get authkey
  id: get-authkey
  uses: nfielder/ts-infi-authkey-action@v1
  with:
    client_id: ${{ secrets.TAILSCALE_CLIENT_ID }}
    client_secret: ${{ secrets.TAILSCALE_CLIENT_SECRET }}
    tags: 'tag:custom-tag1,tag:custom-tag2'
- name: Tailscale
  uses: tailscale/github-action@v1
  with:
    authkey: ${{ steps.get-authkey.outputs.authkey }}
```

## Inputs

|Input|Description|Required?|
|---|---|---|
|client_id|Tailscale OAuth client ID|Yes|
|client_secret|Tailscale OAuth client secret|Yes|
|tags|Comma separated list of tags to apply to the authkey|Yes|
|version|ts-infi-authkey version to use|Yes|
|ephemeral|Whether the created authkey is ephemeral|No|
|expiry|Expiry time of the created authkey|No|
|preauth|Whether the created authkey is preauthorised|No|
|reusable|Whether the created authkey is reusable|No|

## Outputs

|Output|Description|
|---|---|
|authkey|The generated authkey|
