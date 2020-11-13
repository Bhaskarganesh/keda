apiVersion: keda.k8s.io/v1alpha1
kind: ScaledObject
metadata:
  name: dtc-product-app-scaledobject
  namespace: default
  labels:
    deploymentName: dtc-product-app
spec:
  scaleTargetRef:
    deploymentName: dtc-product-app
  pollingInterval: 30
  cooldownPeriod:  30
  minReplicaCount: 1
  maxReplicaCount: 5
  triggers:
  - type: prometheus
    metadata:
      serverAddress: http://prometheus-service.monitoring.svc.cluster.local:9090
      metricName: http_server_requests_seconds_count
      threshold: '5'
      query: sum(rate(http_server_requests_seconds_count{app="dtc-product-app"}[1m]))
