# GitLab Runner Helm Chart

This chart deploys a GitLab Runner instance into your Kubernetes
cluster. For more information, please review [our documentation](https://docs.gitlab.com/charts/charts/gitlab/gitlab-runner).

# Install
```
helm install  --create-namespace --namespace gitlab-runner gitlab-runner -f values.yaml 
```
