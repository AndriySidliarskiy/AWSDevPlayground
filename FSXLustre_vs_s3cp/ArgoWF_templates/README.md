


| Command | Description |
| --- | --- |
| `create-pvc` | This step creates a PVC (Persistent Volume Claim) based on the storage class we created, namely 'lustre-persistent-sc' |
| `get-fsx-id` | This step retrieves the FSx-ID from a secret uses during the creation of a Data Repository Association (DRA). |
| `s3cp-download-perfomance` | Download a file using the S3CP API. |
| `s3cp-download-md5-validation` | Validate the downloaded file using MD5 checksum |
| `s3cp-action-result-simulation` | Simulate file creation for uploading to a bucket. You may use the 'truncate' command or any appropriate method |
| `s3cp-upload-perfomance` | Upload an action result file to a bucket |
| `s3cp-upload-md5-validation` | Validate the yploaded file using MD5 checksum |
| `fsx-lustre-create-associations` | Create Data Repository Associations (DRA) for FSx Lustre |
| `wait-fsx-dra-status` |  Wait for the completion of the previous step |
| `fsx-download-md5-validation` | Validate the imported file on FSx using MD5 checksum. Unlike S3CP, no additional commands are needed for importing as it happens automatically |
| `fsx-action-result-simulation` | The same what we do in s3cp action step |
| `fsx-upload-perfomance` |  Export a file from FSx |
| `fsx-upload-md5-validation` |  Validate the exported file using MD5 checksum |
| `report` | Generates a report from this workflow about time spent on uploading or downloading files also on creating PVC and DRA |
| `delete-pvc` | Delete PVC |