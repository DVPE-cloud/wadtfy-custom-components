# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.4.0-v1beta1]

### Change

* Switched to new upbound family provider
  * TenantFileSystem >= 2.6.0 required
  * Provider Family `provider-aws-efs` required

## [0.3.0-v1beta1]

### Added

* Implemented crossplane `Usage` resources in tenantfilesystem to avoid orphaned deletions
  * Crossplane >= 1.14 required

## [0.2.0-v1beta1]

### Changed

* Renamed chart


## [0.1.2-v1beta1]

### Added

* `components.mounttarget.fileSystemIDRef.name` property
* `components.mounttarget.securityGroupRef.name` property

## [0.1.1-v1beta1]

### Added

* `metadata.name` property

## [0.1.0-v1beta1]

### Changed

* Replaced crossplane resource being built. Now a set of AWS Mount Targets will be generated. 

## [0.0.4-v1beta1]

### Changed

* quote tag values

## [0.0.3-v1beta1]

### Added

* Single Crossplane KMS Key component

### Removed

* Custom Composition and XRD

## [0.0.2-v1beta1]

### Added

* empty string in default values

## [0.0.1-v1beta1]

### Added

* Initial Version

[0.0.1-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.0.1-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.0.2-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.0.2-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.0.3-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.0.3-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.0.4-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.0.4-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.1.0-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.1.0-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.1.1-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.1.1-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.1.2-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.1.2-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.2.0-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.2.0-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.3.0-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.3.0-v1beta1/charts/v1beta1/tenantfilesystem-abstraction
[0.4.0-v1beta1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenantfilesystem-abstraction-0.4.0-v1beta1/charts/v1beta1/tenantfilesystem-abstraction

