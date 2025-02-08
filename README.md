## loki-grafana-tempo-prometheus single node - java opentelemetry sample

- helm uprade -i lgtm-single -n lgtm --create-namespace
- access grafana.local ingress admin / admin
- build java-samnple with otel agent
- generate load with watch curl -vL http://localhost:8080 inside dice pod
- check grafana trace and log
