# initial-testing

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square)

Initial Testing

## Installation
Initial Testing

### Add Helm repository

```shell
helm repo add dvpe https://dvpe-cloud.github.io/wadtfy-custom-components
helm repo update
```

## Install intial chart

```sh
helm install initial . -f values.yaml
```

## Configuration

The following table lists the configurable parameters of the chart and its default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| provider.kubernetes | string | `nil` | The name of the Kubernetes Crossplane Provider used to provision this component. |
