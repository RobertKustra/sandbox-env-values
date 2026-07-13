# sandbox-env-values

Environment-specific values for Sandbox deployments.

## Structure

- base/ - common Helm values shared by all environments
- overlays/dev/ - environment overlay for development
- overlays/test/ - environment overlay for testing
- overlays/prod/ - environment overlay for production

Each overlay directory includes the shared base and adds only environment-specific overrides. Flux consumes the overlay paths from the cluster-config repository.
