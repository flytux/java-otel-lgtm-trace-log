## loki-grafana-tempo-prometheus single node - java opentelemetry sample

#### 1. install lgtm single service
- helm uprade -i lgtm-single -n lgtm --create-namespace
- access grafana.local ingress admin / admin

#### 2. build and deployt spring boot java with otel agent
- build java-sample (dice:v1) with otel agent
- generate load with watch curl -vL http://localhost:8080 inside dice pod
- check grafana trace and log

#### 3. install otel operator 
- install cert-manager
- install otel operator
- deploy java instrumentation CR
- deploy dice:auto applicationh with auto injection annotation
- generate load with watch curl -vL http://localhost:8080 inside dice-auto pod
- check grafana trace and log
