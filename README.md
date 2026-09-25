# sandbox-env-values

Environment-specific values for Sandbox deployments.

## Structure

- `namespaces/base/` - shared Namespace manifest
- `namespaces/overlays/<env>/` - environment-specific Namespace name, labels, and annotations
- `sandbox-nginx/base/` and `sandbox-nginx/overlays/<env>/` - nginx values
- `sandbox-redis/base/` and `sandbox-redis/overlays/<env>/` - Redis values
- `sandbox-ai-consumer/base/` and `sandbox-ai-consumer/overlays/<env>/` - AI consumer values

Each module owns its base and environment overlays. Flux reconciles the Namespace module first, then the application values modules, and finally the workloads from `sandbox-cluster-config`.

## Current values sets

- sandbox-nginx values: base `nginx-values.yaml` + overlay `sandbox-nginx.yaml`
- sandbox-redis values: base `sandbox-redis-values.yaml` + overlay `sandbox-redis-values.yaml`
- sandbox-ai-consumer values: base `sandbox-ai-consumer-values.yaml` + overlay `sandbox-ai-consumer-values.yaml`

Generated ConfigMap names used by HelmRelease manifests:

- `sandbox-nginx-values-base` and `sandbox-nginx-values-env`
- `sandbox-redis-values-base` and `sandbox-redis-values-env`
- `sandbox-ai-consumer-values-base` and `sandbox-ai-consumer-values-env`

## Image automation

Flux image automation manages AI consumer image setters in the application module.

- `sandbox-ai-consumer/overlays/dev/` follows the `flux-system:sandbox-ai-consumer-dev` image policy.
- `sandbox-ai-consumer/overlays/prod/` contains the `flux-system:sandbox-ai-consumer-prod` setter.
- `sandbox-ai-consumer/overlays/test/` is managed manually and does not contain an image automation setter.
