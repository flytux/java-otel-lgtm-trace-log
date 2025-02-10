### Loki-Grafana-Tempo-Prometheus single node - java opentelemetry sample

![１](./images/otel-lgtm-overview.png)
---
![１](./images/tempo-span-link.png)
---
![２](./images/tempo-loki-trace.png)
---

- LGTM 싱글 노드 서버와 otel collector로 구성된 테스트 서버 구동 (helm chart)
- spring boot 샘플 서비스에 java otel agent를 구성하여 log/trace 발생 (그라파나 확인)
- otel operator을 이용하여 annotation를 적용한 파드에 agent를 자동 주입하여 log/trace 발생 (그라파나 확인)
- log / trace / metric 간 연계 추적확인

#### 1. install lgtm single service
- cd lgtm-single
- helm uprade -i lgtm-single -n lgtm --create-namespace
- access grafana.local ingress admin / admin

#### 2. build and deploy spring boot java with otel agent
- cd java-otlp-agent
- build java-sample (dice:v1) with otel agent
- generate load with watch curl -vL http://localhost:8080 inside dice pod
- check grafana trace and log

#### 3. install otel operator 
- cd otel-operator
- install cert-manager
- install otel operator
- deploy java instrumentation CR
- deploy dice:auto applicationh with auto injection annotation
- generate load with watch curl -vL http://localhost:8080 inside dice-auto pod
- check grafana trace and log

#### 4. install otel collector kubernetes
- cd otel-kube
- install kube-state-metrics
- install node-exporter
- install otel-collector with otel-values
- install grafana dasshboard (https://grafana.com/grafana/dashboards/13332-kube-state-metrics-v2/)
