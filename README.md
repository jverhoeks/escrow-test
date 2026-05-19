# escrow-test

Integration tests for the [escrow](https://github.com/jverhoeks/escrow) supply-chain proxy.

Each job installs real packages through the escrow proxy (age gate + OSV scan) and verifies they load correctly. An `age-gate` job confirms that packages are blocked when `min-days=99999`.

## Jobs

| Job | Ecosystem | Package |
|---|---|---|
| npm | npm | once, lodash |
| pypi | pip | requests, click |
| go | Go modules | golang.org/x/text |
| cargo | Cargo | once_cell, serde |
| nuget | NuGet | Newtonsoft.Json |
| maven | Maven | commons-lang3 |
| age-gate | npm + pip | blocked by min-days=99999 |

## Usage

```yaml
- uses: jverhoeks/escrow@v1
  with:
    ecosystems: 'npm,pypi,go,cargo'
    min-days: '7'
    osv-severity: 'HIGH'
```
