# FSXLustre vs s3cp

[FSx for Lustre](https://aws.amazon.com/fsx/lustre/) is based on the open-source Lustre file system, which is known for its scalability, high throughput, and low latency. FSx for Lustre provides two deployment options: scratch and persistent. Scratch file systems are designed for temporary storage and shorter-term processing of data. Persistent file systems are designed for longer-term storage and workloads.

<img
  src="/FSXLustre_vs_s3cp/img/lustre.png"
  alt="ArgoWF stresstest tree"
  style="display: inline-block; margin: 0 auto; max-width: 500px">

The [s3](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3/client/copy.html) module in Boto3 provides functionality for working with Amazon S3, and it includes the boto3.client('s3').cp function for copying objects between S3 buckets or within the same bucket. This function is similar in purpose to the aws s3 cp command-line tool but is used in Python scripts.

`This folder has two child folders with name **argowf_templates** and **k8s_manifest** each of them is used to prepare your environment to run comprasion between s3cp and fsx lustre so please follow the documentation in each of them and hopefully you will succeed.`
