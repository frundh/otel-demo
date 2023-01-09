# OpenTelemetry Demo
Deploys the [OpenTelemetry Demo](https://github.com/open-telemetry/opentelemetry-demo) application together with Grafana Tempo and OpenSearch.

## Quick Start

### Install
```bash
helmwave up --build
```

### Uninstall
```bash
helmwave down
```

### Access
All services are available via the Frontend proxy: http://localhost:8080 by running these commands:
```bash
kubectl -n otel-demo port-forward svc/otel-demo-frontendproxy 8080:8080
```

The following services are available at these paths once the proxy is exposed:
```
Webstore           http://localhost:8080/
Grafana            http://localhost:8080/grafana/
Feature Flags UI   http://localhost:8080/feature/
Load Generator UI  http://localhost:8080/loadgen/
```

OpenTelemetry Collector OTLP/HTTP receiver (required for browser spans to be emitted)
```bash
kubectl -n otel-demo port-forward svc/otel-demo-otelcol 4318:4318
```

OpenSearch Dashboards (not required)
```bash
kubectl -n opensearch port-forward svc/opensearch-dashboards 5601:5601
```
