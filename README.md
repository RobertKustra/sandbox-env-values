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

Generated ConfigMap names used by HelmRelease manifests:

- `sandbox-nginx-values-base` and `sandbox-nginx-values-env`
- `sandbox-redis-values-base` and `sandbox-redis-values-env`
