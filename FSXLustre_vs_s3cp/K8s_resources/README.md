## Prerequisites for lauch stresstest workflow
### IAM
Create an iam role that you use to combine with argowf-sa. Please put this permission for the role and also attach AWS Mnaged policy `AmazonFSxFullAccess`
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "secretsmanager:GetResourcePolicy",
                "secretsmanager:GetSecretValue",
                "secretsmanager:DescribeSecret",
                "secretsmanager:ListSecretVersionIds"
            ],
            "Effect": "Allow",
            "Resource": "*"
        },
        {
            "Action": [
                "s3:ListBucket",
                "s3:ListAllMyBuckets"
            ],
            "Effect": "Allow",
            "Resource": "*",
            "Sid": "ListObjectsInBucket"
        },
        {
            "Action": "s3:*Object",
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::*/*"
            ],
            "Sid": "AllObjectActions"
        }
    ]
}
```
### K8s Manifests
After that you must install [Karpenter](https://github.com/aws/karpenter/tree/main/charts/karpenter) and [ArgoWF](https://github.com/argoproj/argo-helm/tree/main/charts/argo-workflows)

And the last step install all required Kubernetes resources it is:

* argowf-sa
```sh
Cahnge PUT_YOUR_ARGOWF_ROLE_ARN - with correct role what you creae before
kubectl apply argowf-sa.yaml -n argowf
```
* karpenter
```sh
Change in fsx-node-template.yaml PUT_YOUR_CLUSTER_NAME - with correct role what you creae before
Cahnge in fsx-node-template.yaml PUT_YOUR_SUBNET - with correct role what you creae before
kubectl apply fsx-node-template.yaml 
kubectl apply fsx-provisioner.yaml
```
* sc
```sh
Change in lustre-persistent1-sc.yaml PUT_YOUR_SG - with correct role what you creae before
Change in lustre-persistent1-sc.yaml PUT_YOUR_SUBNET - with correct role what you creae before
kubectl apply lustre-persistent1-sc.yaml
```
