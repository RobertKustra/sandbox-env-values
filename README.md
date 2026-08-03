# sandbox-env-values

Environment-specific values for Sandbox deployments.

## Structure

- base/ - common Helm values shared by all environments
- overlays/dev/ - environment overlay for development
- overlays/test/ - environment overlay for testing
- overlays/prod/ - environment overlay for production

Each overlay directory includes the shared base and adds only environment-specific overrides. Flux consumes the overlay paths from the cluster-config repository.

## Current values sets

- sandbox-nginx values: base `common-values.yaml` + overlay `sandbox-nginx.yaml`
- sandbox-redis values: base `sandbox-redis-values.yaml` + overlay `sandbox-redis-values.yaml`
- sandbox-ai-consumer values: base `sandbox-ai-consumer-values.yaml` + overlay `sandbox-ai-consumer-values.yaml`

Generated ConfigMap names used by HelmRelease manifests:

- `sandbox-nginx-values-base` and `sandbox-nginx-values-env`
- `sandbox-redis-values-base` and `sandbox-redis-values-env`
- `sandbox-ai-consumer-values-base` and `sandbox-ai-consumer-values-env`

## Image automation

Flux image automation is enabled only for `dev` and `prod` overlays.

- `overlays/dev/` follows the `flux-system:sandbox-ai-consumer-dev` image policy.
- `overlays/prod/` follows the `flux-system:sandbox-ai-consumer-prod` image policy.
- `overlays/test/` is managed manually and does not participate in image automation.
