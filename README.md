# pipecd-test-app

Test application manifests for manual testing of the `kubernetes_multicluster` PipeCD plugin.

Each folder is a self-contained app registered in PipeCD pointing to a specific stage being tested.

## Folders

| Folder | Stage(s) tested |
|---|---|
| `canary-test-no-service/` | `K8S_CANARY_ROLLOUT` — no service |
| `canary-test-with-service/` | `K8S_CANARY_ROLLOUT` — with service |
| `canary-clean-no-service/` | `K8S_CANARY_ROLLOUT` → `K8S_CANARY_CLEAN` |
| `canary-clean-with-service/` | `K8S_CANARY_ROLLOUT` → `K8S_CANARY_CLEAN` with service |
| `primary-rollout-no-service/` | `K8S_PRIMARY_ROLLOUT` — no service |
| `primary-rollout-with-service/` | `K8S_PRIMARY_ROLLOUT` — with service |
| `baseline-test/` | `K8S_CANARY_ROLLOUT` → `K8S_BASELINE_ROLLOUT` |
| `baseline-clean-test/` | `K8S_CANARY_ROLLOUT` → `K8S_BASELINE_ROLLOUT` → `K8S_CANARY_CLEAN` → `K8S_BASELINE_CLEAN` |

## Usage

See `manual_test.md` in the main pipecd repo for full setup and test instructions.

Each folder contains:
- `app.pipecd.yaml` — PipeCD app config with the pipeline stages
- `deployment.yaml` — Kubernetes Deployment manifest
- `service.yaml` — Kubernetes Service manifest (where applicable)

## Branch requirements

Some test cases require specific feature branches of the plugin to be built and running:

| Stage | Branch |
|---|---|
| `K8S_CANARY_ROLLOUT` | `feat/k8s-multi-canary-rollout` |
| `K8S_CANARY_CLEAN` | `feat/k8s-multi-canary-clean` |
| `K8S_PRIMARY_ROLLOUT` | `feat/k8s-multi-primary-rollout` |
| `K8S_BASELINE_ROLLOUT` | `feat/k8s-multi-baseline-rollout` |
| `K8S_BASELINE_CLEAN` | `feat/k8s-multi-baseline-clean` |
