# OpenTelemetry Jaeger Trace Exporter
[![Gitter chat][gitter-image]][gitter-url]
[![dependencies][dependencies-image]][dependencies-url]
[![devDependencies][devDependencies-image]][devDependencies-url]
[![Apache License][license-image]][license-image]

OpenTelemetry Jaeger Trace Exporter allows the user to send collected traces to Jaeger.

[Jaeger](https://jaeger.readthedocs.io/en/latest/), inspired by [Dapper](https://research.google.com/pubs/pub36356.html) and [OpenZipkin](http://zipkin.io/), is a distributed tracing system released as open source by [Uber Technologies](http://uber.github.io/). It is used for monitoring and troubleshooting microservices-based distributed systems, including:

- Distributed context propagation
- Distributed transaction monitoring
- Root cause analysis
- Service dependency analysis
- Performance / latency optimization

## Prerequisites

Get up and running with Jaeger in your local environment.

[Jaeger](https://www.jaegertracing.io/docs/1.13/) stores and queries traces exported by
applications instrumented with OpenTelemetry. The easiest way to [start a Jaeger
server](https://www.jaegertracing.io/docs/1.13/getting-started/) is to paste the below:

```bash
docker run -d --name jaeger \
  -e COLLECTOR_ZIPKIN_HTTP_PORT=9411 \
  -p 5775:5775/udp \
  -p 6831:6831/udp \
  -p 6832:6832/udp \
  -p 5778:5778 \
  -p 16686:16686 \
  -p 14268:14268 \
  -p 9411:9411 \
  jaegertracing/all-in-one:1.13
```

Or run the `jaeger-all-in-one(.exe)` executable from the [binary distribution archives](https://www.jaegertracing.io/download/):

```bash
jaeger-all-in-one --collector.zipkin.http-port=9411
```

You can then navigate to http://localhost:16686 to access the Jaeger UI.

## Installation

```
npm install --save @opentelemetry/exporter-jaeger
```

## Usage

Install the exporter on your application and pass the options, it must contain a service name.

```
import { JaegerExporter } from '@opentelemetry/exporter-jaeger';

const options = {
  serviceName: 'my-service',
  tags: [], // optional
  host: 'localhost', // optional
  port: 6832, // optional
  maxPacketSize: 65000 // optional
}
const exporter = new JaegerExporter(options);
```
> TODO : add how to register the exporter.

## Useful links
- For more information on OpenTelemetry, visit: <https://opentelemetry.io/>
- For more about OpenTelemetry JavaScript: <https://github.com/open-telemetry/opentelemetry-js>
- For help or feedback on this project, join us on [gitter][gitter-url]

## License

Apache 2.0 - See [LICENSE][license-url] for more information.

[gitter-image]: https://badges.gitter.im/open-telemetry/opentelemetry-js.svg
[gitter-url]: https://gitter.im/open-telemetry/opentelemetry-node?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge
[license-url]: https://github.com/open-telemetry/opentelemetry-js/blob/master/LICENSE
[license-image]: https://img.shields.io/badge/license-Apache_2.0-green.svg?style=flat
[dependencies-image]: https://david-dm.org/open-telemetry/opentelemetry-js/status.svg?path=packages/opentelemetry-exporter-jaeger
[dependencies-url]: https://david-dm.org/open-telemetry/opentelemetry-js?path=packages%2Fopentelemetry-exporter-jaeger
[devDependencies-image]: https://david-dm.org/open-telemetry/opentelemetry-js/dev-status.svg?path=packages/opentelemetry-exporter-jaeger
[devDependencies-url]: https://david-dm.org/open-telemetry/opentelemetry-js?path=packages%2Fopentelemetry-exporter-jaeger&type=dev