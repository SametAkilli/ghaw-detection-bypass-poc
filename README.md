# gh-aw safe-job threat-detection gating bypass — PoC

Security research reproduction. See `.github/workflows/repro.yml`.
Demonstrates that a job gated `if: (!cancelled()) && ... contains(output_types,'create_branch')`
(as used by compiled gh-aw safe-jobs `create_branch`/`mention_owners`) executes even when the
`detection` (threat/prompt-injection) job FAILS, while a properly-gated `safe_outputs`
job (`needs.detection.result == 'success'`) is skipped.
