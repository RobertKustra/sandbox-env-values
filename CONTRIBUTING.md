# Contributing

## Scope of image automation

This repository follows a mixed release model for image tags:

- `dev` and `prod` overlays are updated by Flux image automation.
- `test` is intentionally excluded from image automation and must be updated manually.

## Working on values

- Keep overlay-specific overrides inside the matching `overlays/<env>/` directory.
- Preserve the `imagepolicy` setter comments on `dev` and `prod` image tags.
- Do not add image automation setters to `test` unless the release policy changes.

## Pull request expectations

- Explain whether the change affects `dev`, `prod`, or `test`.
- Include validation evidence for changes that affect Helm values or image tags.
- Keep documentation aligned with any change to the image automation policy.