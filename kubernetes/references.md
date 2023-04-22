# Kubernetes References

## kubectl

## Basics
- https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/

## Services
- https://kubernetes.io/docs/tasks/debug/debug-application/debug-service/

## Secrets
- https://kubernetes.io/docs/tasks/configmap-secret/

## Networking
- https://www.digitalocean.com/community/tutorials/how-to-inspect-kubernetes-networking
- https://kubernetes.io/docs/concepts/services-networking/network-policies/
- https://www.tkng.io/ingress/egress/

## Helm
  Jobs:
    - <https://andrewlock.net/deploying-asp-net-core-applications-to-kubernetes-part-9-monitoring-helm-releases-that-use-jobs-and-init-containers/>
    - <https://dwdraju.medium.com/managing-kubernetes-job-with-helm-7c3934937d9e>



NOTES FROM ORI DEV:
K8s:
deployment - versioned, inc. deployment strategy, rollback strategy
  ingress (layer 7 - access to header)

  service (~ load balancer - layer 4 TCP/UDP)
    creates endpoints which go to pods
    endpoints can be internal or external to the cluster network
  replicaSet
    pod

pod-name-replicaSetID-podID

k8s webhooks
  dynamic admission control

kubectl
k8s api server
