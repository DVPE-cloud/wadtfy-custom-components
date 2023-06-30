# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0]

### Changed
* Refactor naming of ServiceAccount for IamRole to <claim-name>-<namespace-name>

## [1.1.0]
> DO NOT USE, VERSION DOES NOT WORK
### Changed
* Naming of ServiceAccount created by Irsa composition has changed to <claim-name>-<namespace-name>

## [1.0.0]

### Changed

* Read parameter `region` from global wadtfy-env instead of tenant-env

## [0.2.0]

### Replaced

* Helm variable has been replaced by crossplane environment patch set


## [0.1.0]

### Added

* Initial Version

[0.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/irsa-0.1.0-v1beta1/charts/v1beta1/irsa
[0.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/irsa-0.2.0-v1beta1/charts/v1beta1/irsa
[1.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/irsa-1.0.0-v1beta1/charts/v1beta1/irsa
[1.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/irsa-1.1.0-v1beta1/charts/v1beta1/irsa
[1.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/irsa-1.2.0-v1beta1/charts/v1beta1/irsa
