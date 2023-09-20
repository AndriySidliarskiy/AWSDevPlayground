## Prerequisites for lauch stresstest workflow
### Сreate IAM
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
### Install charts
After that you must install [Karpenter](https://github.com/aws/karpenter/tree/main/charts/karpenter) and [ArgoWF](https://github.com/argoproj/argo-helm/tree/main/charts/argo-workflows)

### Install K8s Manifests

And the last step install all required Kubernetes resources it is:

* argowf-sa
Change in argowf-sa.yaml **PUT_YOUR_ARGOWF_ROLE_ARN** - with the correct role what you creae before
```sh
kubectl apply argowf-sa.yaml -n argowf
```
* karpenter
Change in fsx-node-template.yaml **PUT_YOUR_CLUSTER_NAM** - with the correct Cluster Name
Change in fsx-node-template.yaml **PUT_YOUR_SUBNET** - with the correct subnet in your VPC
```sh
kubectl apply fsx-node-template.yaml 
kubectl apply fsx-provisioner.yaml
```
* sc
Change in lustre-persistent1-sc.yaml **PUT_YOUR_SG** - with the correct sg that you will use for FSX Lustre
Change in lustre-persistent1-sc.yaml **PUT_YOUR_SUBNET** - with the correct subnet that you will use for FSX Lustre
```sh
kubectl apply lustre-persistent1-sc.yaml
```
