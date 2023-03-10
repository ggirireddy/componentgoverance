# Default values for bts-chart.
# This is a YAML-formatted file.
# Declare variables to be passed into your templates.

appName: "ew-cg"
appEnv: "dev"
replicaCount: 1

image:
  repository: btseusdevacr.azurecr.io/ew-cg
  pullPolicy: Always
  tag: "v1.0.0"

imagePullSecrets: []
nameOverride: ""
fullnameOverride: ""

# Use this section for service.yaml
service:
  type: ClusterIP
  port: 80

# Use this section for Nginx ingress.yaml
ingress:
  enabled: true
  #annotations:
  #  nginx.ingress.kubernetes.io/rewrite-target: /$2
  hosts:
    - host: componentgovernancedev.brightspeed.com
      paths:
        - path: /ew/
          pathType: Prefix
  tls:
    - secretName: componentgovernancedev.brightspeed.com-tls
      hosts:
       - componentgovernancedev.brightspeed.com

# Use this section for HPA
autoscaling:
  enabled: false
  minReplicas: 1
  maxReplicas: 100
  targetCPUUtilizationPercentage: 80
  targetMemoryUtilizationPercentage: 80

nodeSelector:
  agentpool: default

# Use this section for the Deployment.yaml
deployment:
  code:
    ports:
      - name: http
        containerPort: 3000
        protocol: TCP
