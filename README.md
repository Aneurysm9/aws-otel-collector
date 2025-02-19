[![codecov](https://codecov.io/gh/aws-observability/aws-otel-collector/branch/main/graph/badge.svg)](https://codecov.io/gh/aws-observability/aws-otel-collector)
![CI](https://github.com/aws-observability/aws-otel-collector/workflows/CI/badge.svg)
![CD](https://github.com/aws-observability/aws-otel-collector/workflows/CD/badge.svg)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/aws-observability/aws-otel-collector)


### Overview

AWS Distro for OpenTelemetry Collector(AWS OTel Collector) is a AWS supported version of the upstream OpenTelemetry Collector and is distributed by Amazon. It supports the selected components from the OpenTelemetry community. It is fully compatible with AWS computing platforms including EC2, ECS and EKS. It enables users to send telemetry data to AWS CloudWatch Metrics, Traces and Logs backends as well as the other supported backends.

See the [AWS Distro for OpenTelemetry documentation](https://aws-otel.github.io/docs/getting-started/collector) for more information.

### Getting Help

Use the community resources below for getting help with AWS OTel Collector.
* Use [GitHub issues](https://github.com/aws-observability/aws-otel-collector/issues) for reporting bugs and requesting features.
* Join our GitHub [Community](https://github.com/aws-observability/aws-otel-community) for AWS Distro for OpenTelemetry to ask your questions, file issues, request enhancements.
* Open a support ticket with [AWS Support](http://docs.aws.amazon.com/awssupport/latest/user/getting-started.html).
* If you think you may have found a bug, open an [issue](https://github.com/aws-observability/aws-otel-collector/issues/new).
* For contributing guidelines refer [CONTRIBUTING.md](https://github.com/aws-observability/aws-otel-collector/blob/main/CONTRIBUTING.md).

#### AWS OTel Collector Built-in Components

This table represents the supported components of AWS OTel Collector in 2020. The highlighted components below are developed by AWS in-house. The rest of the components in the table are the essential default components that AWS OTel Collector will support.

| Receiver                        | Processor                     | Exporter                           | Extensions             |
|---------------------------------|-------------------------------|------------------------------------|------------------------|
| prometheusreceiver              | attributesprocessor           | `awsxrayexporter`                  | healthcheckextension   |
| otlpreceiver                    | resourceprocessor             | `awsemfexporter`                   | pprofextension         |
| `awsecscontainermetricsreceiver`| batchprocessor                | `awsprometheusremotewriteexporter` | zpagesextension        |
| `awsxrayreceiver`               | memorylimiter                 | loggingexporter                    | `ecsobserver`          |
| `statsdreceiver`                | tailsamplingprocessor         | otlpexporter                       |                        |
| zipkinreceiver                  | probabilisticsamplerprocessor | fileexporter                       |                        |
| jaegerreceiver                  | spanprocessor                 | otlphttpexporter                   |                        |
| `awscontainerinsightreceiver`   | filterprocessor               | prometheusexporter                 |                        |
|                                 | metricstransformprocessor     | datadogexporter                    |                        |
|                                 | resourcedetectionprocessor    | dynatraceexporter                  |                        |
|                                 |                               | newrelicexporter                   |                        |
|                                 |                               | sapmexporter                       |                        |
|                                 |                               | signalfxexporter                   |                        |
|                                 |                               | logzioexporter                     |                        |


#### AWS OTel Collector AWS Components

* [OpenTelemetry Collector](https://github.com/open-telemetry/opentelemetry-collector/)
* [Trace X-Ray Exporter](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/master/exporter/awsxrayexporter)
* [Metrics EMF Exporter](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/master/exporter/awsemfexporter/README.md)
* [ECS Container Metrics Receiver](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/master/receiver/awsecscontainermetricsreceiver)
* [StatsD Receiver](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/receiver/statsdreceiver)
* [ECS Observer Extension](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/extension/observer/ecsobserver)

### Getting Started

#### Prerequisites

To build AWS OTel Collector locally, you will need to have Golang installed. You can download and install Golang [here](https://golang.org/doc/install).

#### AWS OTel Collector Configuration

We built in a [default configuration](https://github.com/aws-observability/aws-otel-collector/blob/main/config.yaml) to our docker image and other format of release.
So you can run AWS OTel Collector out of box with the default settings.
Also, AWS OTel Collector configuration uses the same configuration syntax/design from [OpenTelemetry Collector](https://github.com/open-telemetry/opentelemetry-collector)
so you can customize or porting your OpenTelemetry Collector configuration files when running AWS OTel Collector. please refer `Try out AWS OTel Collector` section on configuring AWS OTel Collector.

#### Try out AWS OTel Collector

AWS OTel Collector supports all AWS computing platforms and docker/kubernetes. Here are some examples on how to run AWS OTel Collector to send telemetry data:

* [Run it with Docker](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/docker-demo.md)
* [Run it with ECS](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/ecs-demo.md)
* [Run it with EKS](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/eks-demo.md)
* [Run it on AWS Linux EC2](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/linux-rpm-demo.md)
* [Run it on AWS Windows EC2](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/windows-other-demo.md)
* [Run it on AWS Debian EC2](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/debian-deb-demo.md)

#### Build Your Own Artifacts

Use the following instruction to build your own AWS OTel Collector artifacts:

* [Build Docker Image](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/build-docker.md)
* [Build RPM/Deb/MSI](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/developers/build-aoc.md)

### Development

See [docs/developers](docs/developers/README.md)

### Release Process

* [Release new version](RELEASING.md)

### Benchmark

The latest performance model result is [here](https://github.com/aws-observability/aws-otel-collector/blob/main/docs/performance_model.md). 
The performance test conducted by following the [instruction](https://github.com/aws-observability/aws-otel-test-framework/blob/terraform/docs/get-performance-model.md) here.

### License

AWS OTel Collector is licensed under an Apache 2.0 license.
