# iStampit GitHub Action — Timestamp your releases & artifacts

> [!WARNING]
> **This action is retired.** iStampit was sunset in May 2026. This repository is archived for reference. No new releases will be published.
>
> See the [iStampit retirement notice](https://istampit.io/) for details.

[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-iStampit--action-blue?logo=github)](https://github.com/marketplace/actions/istampit-timestamp)
[![Self Test](https://github.com/SinAi-Inc/istampit-action/actions/workflows/self-test.yml/badge.svg)](https://github.com/SinAi-Inc/istampit-action/actions/workflows/self-test.yml)
[![CodeQL](https://github.com/SinAi-Inc/istampit-action/actions/workflows/codeql.yml/badge.svg)](https://github.com/SinAi-Inc/istampit-action/actions/workflows/codeql.yml)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/SinAi-Inc/istampit-action/badge)](https://securityscorecards.dev/viewer/?uri=github.com/SinAi-Inc/istampit-action)

Composite GitHub Action that:

1. Installs the [OpenTimestamps](https://opentimestamps.org/) client
2. Hashes target files
3. Produces `.ots` receipts and (optionally) upgrades them against calendars
4. Lets you upload receipts as workflow artifacts or attach them to GitHub Releases

![Usage Demo](./docs/usage-demo.gif)

> Placeholder GIF: add a short capture of stamping a file locally and showing the .ots receipt.

---

## 🔧 Usage

```yaml
jobs:
  stamp:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Timestamp artifacts
        id: stamp
        uses: SinAi-Inc/istampit-action@v1
        with:
          paths: "dist/**/*"
          upgrade: "true"
      - name: Show receipts
        run: |
          echo "Receipts: ${{ steps.stamp.outputs.receipts }}"
          python - <<'PY'
import json, os
receipts = json.loads(os.environ['RECEIPTS'])
print('\n'.join(receipts))
PY
        env:
          RECEIPTS: ${{ steps.stamp.outputs.receipts }}
```

## 📥 Inputs

* `paths` (**required**) — comma-separated glob(s) of files to stamp.
* `upgrade` (optional, default `false`) — attempt calendar upgrade for better attestations.

## 📤 Outputs

* `receipts` — JSON array of generated `.ots` receipt file paths.

Access with `${{ steps.stamp.outputs.receipts }}` (stringified JSON array). Parse as needed.

## 🔒 Provenance (Optional)

Add SLSA provenance generation to assert build integrity (planned). A future workflow will attach a provenance attestation to each release.

## 📝 Releases

See CHANGELOG and GitHub Releases:

* v1.0.3 – Parser stability, badges corrected, CI self-test green.
* v1.0.2 – Manifest fix + branding + outputs via GITHUB_OUTPUT.


## 📜 License

MIT (wrapper code). OTS client is LGPL-3.0.

---

The moving tag `v1` always points to the latest stable, parser-verified release.
