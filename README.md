# github-ip-lists

Daily-refreshed plain-text CIDR lists from `https://api.github.com/meta`,
suitable for OPNsense / pfSense **URL Table (IPs)** aliases.

## Raw URLs

Use these in your firewall alias (one per line, refresh = 1 day):

- Actions runners (egress): `https://raw.githubusercontent.com/nirnx/github-ip-lists/main/lists/actions.txt`
- API:                      `https://raw.githubusercontent.com/nirnx/github-ip-lists/main/lists/api.txt`
- Webhooks (inbound):       `https://raw.githubusercontent.com/nirnx/github-ip-lists/main/lists/hooks.txt`
- Web UI:                   `https://raw.githubusercontent.com/nirnx/github-ip-lists/main/lists/web.txt`
- Git:                      `https://raw.githubusercontent.com/nirnx/github-ip-lists/main/lists/git.txt`

Per-family variants are also published as `*-v4.txt` and `*-v6.txt`.

`updated.txt` holds the last refresh timestamp (UTC).

## How it works

A scheduled GitHub Actions workflow (`.github/workflows/update-ips.yml`)
fetches `api.github.com/meta` once a day, splits each category into a
sorted, deduplicated text file, and commits the result only if something
actually changed.

Trigger a manual refresh from **Actions → Update GitHub meta IP lists →
Run workflow**, or via:

```bash
gh workflow run "Update GitHub meta IP lists"
```
