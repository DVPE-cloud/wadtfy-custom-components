# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [3.2.5]

### Changed
* Updated CHANGELOG descriptions

## [3.2.4]

### Changed
* Reset transform types in tenant-default-composition and tenant-system-composition to regexp matcher.

## [3.2.3]
> DO NOT USE, VERSION DOES NOT WORK
### Changed
* Fixed typo.

## [3.2.2]
> DO NOT USE, VERSION DOES NOT WORK
### Changed
* Adjusted transform type in tenant-default-composition and tenant-system-composition

## [3.2.1]
> DO NOT USE, VERSION DOES NOT WORK
### Changed
* Fixed typos.

## [3.2.0]
> DO NOT USE, VERSION DOES NOT WORK
### Changed
* Replaced freeform field in secret-stored xrd with specific variable

## [3.1.0]
> DO NOT USE, VERSION DOES NOT WORK
### Changed
* Passing new property in tenant-default-composition and tenant-system-composition for setting default secret store name
* Adjusted secretstore-composition to use new properties

## [3.0.0]
> DO NOT USE, VERSION DOES NOT WORK
### Changed
* Naming of SecretStore resource has been changed from secret-store-<product>-<namespace> to secret-store-<namespace>

## [2.0.0]

### Removed
* Parameter `region`

### Changed
* Read `region` from wadtfy-env instead of setting it as an explicit parameter in xsecretstore
* Read `kubernetesproviderconf` from wadtfy-env instead of setting it as an explicit parameter in xsecretstore

## [1.2.0]

### Replaced
* Helm variable has been replaced by crossplane environment patch set

## [1.1.0]

### Changed
* Generated names of Provider Config overcome 64 characters. Name generation therefore has been shortened.

## [1.0.0]

> NOTE: This is a Major Release  
> This release contains breaking changes, since the way how a tenant will be created changed from previous versions.  
> Tenant's will now be provisioned with a Crossplane `EnvironmentConfig` holding relevant information of the tenant connection.
> This `EnvironmentConfig` will then be used by other custom Components in order to avoid bloating each component with redundant
> enironment related information.

### Added
* env-xrd and env-composition as temporary nested component to allow patching from `EnvironmentConfig`
* tenant-default and tenant-system compositions for allowing different tenant types to be created

### Replaced
* external-secret-store templates with secret-store templates

## [0.1.2]

### Added

* new label for tenant composition. necessary for distinction of tenants and wadtfy system resources

## [0.1.1]

### Bugfix

* Fixed incorrect values reference in helm chart

## [0.1.0]

### Added

* Initial Version

[0.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-0.1.0-v1beta1/charts/v1beta1/tenant
[0.1.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-0.1.1-v1beta1/charts/v1beta1/tenant
[0.1.2]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-0.1.2-v1beta1/charts/v1beta1/tenant
[1.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-1.0.0-v1beta1/charts/v1beta1/tenant
[1.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-1.1.0-v1beta1/charts/v1beta1/tenant
[1.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-1.2.0-v1beta1/charts/v1beta1/tenant
[2.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-2.0.0-v1beta1/charts/v1beta1/tenant
[3.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-3.0.0-v1beta1/charts/v1beta1/tenant
[3.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-3.1.0-v1beta1/charts/v1beta1/tenant
[3.2.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-3.2.0-v1beta1/charts/v1beta1/tenant
[3.2.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-3.2.1-v1beta1/charts/v1beta1/tenant
[3.2.2]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-3.2.2-v1beta1/charts/v1beta1/tenant
[3.2.3]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-3.2.3-v1beta1/charts/v1beta1/tenant
[3.2.4]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-3.2.4-v1beta1/charts/v1beta1/tenant
