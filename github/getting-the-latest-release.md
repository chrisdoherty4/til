# Getting the latest release

```bash
curl -s https://api.github.com/repos/[group]/[repository]/releases/latest | \
jq -r '.assets[] | select(.name | contains("'"$(uname | tr '[:upper:]' '[:lower:]')"'_amd64")) | .browser_download_url'
```