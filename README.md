# sandbox-env-values

Environment-specific values for Sandbox deployments.

## Structure

- dev/ - values for the development environment
- test/ - values for the test environment
- prod/ - values for production

These files are consumed by Flux through the HelmRelease definitions in the cluster-config repository.
