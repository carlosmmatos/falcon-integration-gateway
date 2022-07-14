# AWS CloudTrail Lake Backend

Integration with AWS CloudTrail Lake.

### Example Configuration file

[config/config.ini](https://github.com/CrowdStrike/falcon-integration-gateway/blob/main/config/config.ini) configures Falcon Integration Gateway. Below is a minimal configuration example for AWS CloudTrail Lake:
```
[main]
# Cloud backends that are enabled. The gateway will push events to the cloud providers specified below
backends=CLOUDTRAIL_LAKE

[cloudtrail_lake]
# AWS CloudTrail Lake section is applicable only when CLOUDTRAIL_LAKE backend is enabled in the [main] section.

# Uncomment to provide the aws account ID. Alternatively, use ACCOUNT_ID env variable.
#account_id =

# Uncomment to provide the Ingestion Channel ID. Alternatively, use INGESTION_CHANNEL_ID env variable.
#ingestion_channel_id =

# Uncomment to provide the Role ARN to push events. Alternatively, use ROLE_ARN env variable.
#role_arn =

# Uncomment to provide aws region (Default: us-east-1). Alternatively, use REGION env variable
#region = us-east-1
```

### Developer Guide

 - Build the image
   ```
   docker build . -t falcon-integration-gateway
   ```
 - Run the application
   ```
   docker run -it --rm \
       -e FALCON_CLIENT_ID="$FALCON_CLIENT_ID" \
       -e FALCON_CLIENT_SECRET="$FALCON_CLIENT_SECRET" \
       -e FALCON_CLOUD_REGION="us-1" \
       -e ACCOUNT_ID="$ACCOUNT_ID" \
       -e INGESTION_CHANNEL_ID="$INGESTION_CHANNEL_ID" \
       -e ROLE_ARN="$ROLE_ARN" \
       -e REGION="$REGION" \
       falcon-integration-gateway:latest
   ```