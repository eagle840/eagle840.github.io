# Kubernetes Best Practices

Most taken from Google

## 1. Keep Images Small
- (through using Docker 'Builder Pattern')
(eg node:8 ~ 670MB,   node:8-alpine ~ 65MB)
- this will increase performance, pull speed, and better security
- See 'Google Container Builder', Google can scan GCS for vulnerabilities)

## 2. Use Namespaces
use Kubens
use network policies to help isolate namespaces

## 3. Use Health Checks
-Liveness: Alive - keep up,  Dead - create a new pod
-Readiness: No traffic until up (ready)
- 3 types :HTTP(path), CMD(exec), TCP(port)

## 4. Use Requests and Limits
- 2 cpus: cpu & memory
-Limit resources wrt namespaces: 
ResourceQuotas (kind) for nameespaaces
LimitRange (kind) for contains and pods  CHECK! Pods specs have 'priority', lowest terminated 1st
Overcommitment K8S will shut down pods/containers

## 5. Terminate with Grace (handle SIGTERM)
K8S live cycle:
Pod stops getting traffic
Sent 'preStop Hook'
Sent SIGTERM
K8S checks pod spec: 'terminationGracePeriodSeconds' and waits that.
Sent SIGKILL

## 6. Map External Services

REDO VIDEO!
and lookup 'endpoints'

## 7. Keep Your Cluster Upto Date
No HA, you'll get no control plan (API server)
Use HA to makes sure your API server stays up (GKE use Regional)
Use Node Pools (groups) to power down a group and power up a new set with new ver.

## 8. Others
- Keep it portable, use PV and PVC's (not Volumes)
- Use an application.yaml (kind: List) Even better use something Like Helm
- K8S princles: 1) declarative over Imparative
2) No Hidden APIs
3) Meet the use were they live
4) ?? Work load routability ??
5) any more ??

