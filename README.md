# GitLab Runner Helm Chart

This chart deploys a GitLab Runner instance into your Kubernetes
cluster. For more information, please review [our documentation](https://docs.gitlab.com/charts/charts/gitlab/gitlab-runner).

# Install
```
helm install  --create-namespace --namespace gitlab-runner gitlab-runner -f values.yaml 
```

```
https://docs.gitlab.com/runner/configuration/advanced-configuration.html
https://docs.gitlab.com/runner/configuration/advanced-configuration.html#the-runnerscaches3-section

```

```
### role poc-gitlab-runner allow s3 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:GetObjectVersion",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::poc-git-runner/*"
            ]
        }
    ]
}

trust policy poc-gitlab-runner
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "pods.eks.amazonaws.com",
                "AWS": "arn:aws:iam::340752821097:role/poc-gitlab-runner"
            },
            "Action": [
                "sts:AssumeRole",
                "sts:TagSession"
            ]
        }
    ]
}
```