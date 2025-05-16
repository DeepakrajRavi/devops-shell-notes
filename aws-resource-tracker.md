## 🧾 Sample Shell Script: AWS Resource Tracker

This script helps quickly audit common AWS services using the AWS CLI and `jq`:

### Features:
- 🔍 Lists all S3 buckets
- 🖥️ Lists all EC2 instances
- ⚙️ Lists all Lambda functions
- 👤 Lists all IAM users

### Prerequisites:
- AWS CLI installed and configured (`aws configure`)
- `jq` installed (for JSON parsing)

### Script: `aws_resource_tracker.sh`
```bash
#!/bin/bash

#####################################################
# Author: Deepak
# Date: 16 May 2025
# Version: v1
# Description: This script reports AWS resource usage
#####################################################

set -x

echo "S3 Buckets:"
aws s3 ls

echo "EC2 Instances:"
aws ec2 describe-instances | jq '.Reservations[].Instances[].InstanceId'

echo "Lambda Functions:"
aws lambda list-functions

echo "IAM Users:"
aws iam list-users
🚀 Usage:
chmod +x aws_resource_tracker.sh
./aws_resource_tracker.sh

