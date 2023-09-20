# FSXLustre vs s3cp

FSx for Lustre is based on the open-source Lustre file system, which is known for its scalability, high throughput, and low latency. FSx for Lustre provides two deployment options: scratch and persistent. Scratch file systems are designed for temporary storage and shorter-term processing of data. Persistent file systems are designed for longer-term storage and workloads.

<img
  src="/FSXLustre_vs_s3cp/img/lustre.png"
  alt="ArgoWF stresstest tree"
  style="display: inline-block; margin: 0 auto; max-width: 500px">

The s3 cp command is not a standard command in Unix or Linux, but it appears to be related to Amazon Web Services (AWS) and their S3 (Simple Storage Service) command-line interface (CLI). AWS provides a set of command-line tools for interacting with various AWS services, including S3, and s3 cp is likely a reference to one of these commands.

The s3 cp command in AWS CLI is used to copy files and directories to and from an Amazon S3 bucket. Here's a basic overview of how it works:

`This folder has two child folders with name argowf_templates and k8s_manifest each of them is used to prepare your environment to run comprasion between s3cp and fsx lustre so please follow the documentation in each of them and hopefully you will succeed.`
