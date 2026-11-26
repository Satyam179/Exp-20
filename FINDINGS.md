# Static vs dynamic findings

| Finding | Source | Static tool | Risk/severity (assessment) | Confidence | Dynamic evidence | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Path traversal | `filename = input(...)` -> `"records/" + filename` -> `open(...)` | Custom Semgrep taint rule | High | High | `../private.txt` read a file outside `records/` | Confirmed |
| Missing positive-age validation | `age = int(input(...))` -> displayed without range check | Custom Semgrep pattern rule | Low (business-rule flaw in this demo) | Medium (pattern heuristic) | `-10` was accepted and displayed | Confirmed |

SonarQube issues: **0**. Semgrep standard Python rules: **0**. Semgrep custom rules: **2**. Neither issue is claimed to be a SonarQube finding. No false positive was demonstrated; broader untested behaviours require further investigation.
