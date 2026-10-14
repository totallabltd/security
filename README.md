# security.totallab.com

TotalLab's vulnerability disclosure policy, `security.txt` and published
security advisories, served by GitHub Pages at <https://security.totallab.com>.
Pages renders the Markdown; there is no build step to run.

| Path | What it is |
| --- | --- |
| `index.md` | Home page: how to report, and the list of advisories (generated from `advisories/`) |
| `policy.md` | Coordinated vulnerability disclosure policy |
| `.well-known/security.txt` | RFC 9116 contact file; expires a year after it is written |
| `advisories/<id>.md`, `advisories/<id>.json` | One advisory: web page and CSAF 2.0 document |
| `CNAME` | The custom domain |

## Publish an advisory

Advisories are drafted and approved in Julian (build_process `docs/julian.md`,
"Public security advisories"; `docs/cra-runbook.md`, "Public disclosure"). Once
one is approved:

```sh
git switch -c advisory/TL-SA-2026-0001
julian disclosure export --julian-url https://sock.taildc30fe.ts.net/julian --to .
git add advisories && git commit -m "Publish TL-SA-2026-0001"
```

Review the diff and merge it through a pull request. Never edit an advisory
here by hand: revise it in Julian and export again, so the published copy
matches Julian's approved record.

## Renew security.txt

`security.txt` must be renewed before its `Expires` date:

```sh
julian disclosure security-txt --contact mailto:security@totallab.com \
  --policy https://security.totallab.com/policy \
  --canonical https://security.totallab.com/.well-known/security.txt > .well-known/security.txt
```

totallab.com's own `/.well-known/security.txt` should redirect here.

## Domain

`security.totallab.com` is a CNAME to `totallabltd.github.io`; the custom
domain and "Enforce HTTPS" are set in the repository's Pages settings.
