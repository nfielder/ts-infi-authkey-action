# ts-infi-authkey-action

This action is designed to be used with the [Tailscale GitHub Action](https://github.com/tailscale/github-action). It provides an authkey that is generated using OAuth credentials and the [ts-infi-authkey](https://github.com/nfielder/ts-infi-authkey) utility.

```yaml
- name: Get authkey
  id: get-authkey
  uses: nfielder/ts-infi-authkey-action@v1
  with:
    client_id: ${{ secrets.TAILSCALE_CLIENT_ID }}
    client_secret: ${{ secrets.TAILSCALE_CLIENT_SECRET }}
- name: Tailscale
  uses: tailscale/github-action@v1
  with:
    authkey: ${{ steps.get-authkey.outputs.authkey }}
```
