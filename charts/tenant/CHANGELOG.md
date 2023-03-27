# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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

[0.1.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-0.1.0/charts/tenant
[0.1.1]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-0.1.1/charts/tenant
[0.1.2]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-0.1.2/charts/tenant
[1.0.0]: https://github.com/DVPE-cloud/wadtfy-custom-components/tree/tenant-1.0.0/charts/tenant
