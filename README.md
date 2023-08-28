# action-dnclient

This GitHub Action configures `dnclient` to join your [Defined Networking](https://defined.net) overlay network during your Action run. After you add the step below, all other steps in your Action will be able to connect to other hosts on your overlay network. This Action uses [quickvm/defined-systemd-units](https://github.com/quickvm/defined-systemd-units) under the hood. See that project's [README](https://github.com/quickvm/defined-systemd-units/blob/master/README.md) for more details on how to configure `dnclient` with this Action.

## Usage

You can enable your GitHub Action to join your overlay network by adding the following step to your workflow.

```yaml
  - name: dnclient
    uses: quickvm/action-dnclient@v1
    with:
      dn-api-key: ${{ secrets.DN_API_KEY }}
      dn-network-id: ${{ secrets.DN_NETWORK_ID }}
      dn-role-id: ${{ secrets.DN_ROLE_ID }}
```

The following inputs are required:

```yaml
dn-api-key: ${{ secrets.DN_API_KEY }}
dn-network-id: ${{ secrets.DN_NETWORK_ID }}
dn-role-id: ${{ secrets.DN_ROLE_ID }}
```

and they should be stored as a [GitHub Encrypted Secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets).

The following inputs are optional:

```yaml
dn-client-version: 1.2.1
dn-hostname: my-repo-gh-action
dn-ip-address: "100.100.0.69"
```

and you can store them as [GitHub Variables](https://docs.github.com/en/actions/learn-github-actions/variables).

Note: If you set a static hostname and IP address and you have more than one Action run the same Workflow at a same time you might see failures. Names and IP addresses have to be unique in Defined.net. Use the `dn-hostname` and `dn-ip-address` inputs at your own risk!

## License

MIT License

Copyright (c) 2023 QuickVM

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
