# Experiment 20 - Static Analysis with SonarQube and Semgrep

**Application:** `unvalidated.py` from Lab 8 (two dynamically tested abuse cases).

**Results:** SonarQube 0 issues; Semgrep standard Python rules 0; custom rules 2 findings (path traversal and negative-age input). The custom age-input rule is a pattern heuristic; the dynamic test confirms rejection was absent in this test program. The two confirmed behaviours do **not** imply that SonarQube independently detected them.

**Evidence:** PNG screenshots plus the PDF report included here. No SonarQube tokens or secrets are committed.

Run the custom Semgrep rules locally:

```powershell
semgrep scan --config path_rule.yml unvalidated.py
```

To reproduce the SonarQube scan, create a local SonarQube project with key `exp20-static-analysis`, configure `SONAR_TOKEN` privately, and run the installed SonarScanner against `unvalidated.py`.

Run only using fictional test files; the sample is intentionally insecure.
