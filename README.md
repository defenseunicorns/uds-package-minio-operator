# 🏭 UDS Minio-operator Package

[![Latest Release](https://img.shields.io/github/v/release/defenseunicorns/uds-package-minio-operator)](https://github.com/defenseunicorns/uds-package-minio-operator/releases)
[![Build Status](https://img.shields.io/github/actions/workflow/status/defenseunicorns/uds-package-minio-operator/tag-and-release.yaml)](https://github.com/defenseunicorns/uds-package-minio-operator/actions/workflows/tag-and-release.yaml)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/defenseunicorns/uds-package-minio-operator/badge)](https://api.securityscorecards.dev/projects/github.com/defenseunicorns/uds-package-minio-operator)

This package is designed for use as part of a bundle deployed on [UDS Core](https://github.com/defenseunicorns/uds-core).

## Flavors

| Flavor | Description | Example Creation |
| ------ | ----------- | ---------------- |
| upstream | Uses upstream images within the package. | `zarf package create . -f upstream` |

## Releases

The released packages can be found in [ghcr](https://github.com/defenseunicorns/uds-package-minio-operator/pkgs/container/packages%2Fuds%2Fminio-operator).

## UDS Tasks (for local dev and CI)

*For local dev, this requires you install [uds-cli](https://github.com/defenseunicorns/uds-cli?tab=readme-ov-file#install)

> :white_check_mark: **Tip:** To get a list of tasks to run you can use `uds run --list`!

## Contributing

Please see the [CONTRIBUTING.md](./CONTRIBUTING.md)