# Description
Docker env that contains aws cli, gcloud cli, azure cli, kubectl and terraform.  
The build areguments are optional, and if specified will also initiate the cli authentication.

# Usage  
Build the container:
~~~
docker build \
    # GCP credentials used to generate the usual json keyfile
    --build-arg 'GCP_PROJECT_ID=<gcp_project_id>' \
    --build-arg 'GCP_KEY_ID=<gcp_key_id>' \
    --build-arg 'GCP_PRIVATE_KEY=<gcp_private_key>' \
    --build-arg 'GCP_CLIENT_ID=<gcp_client_id>' \
    # GCP path to the generated credentials file (inside container) 
    --build-arg 'GOOGLE_CLOUD_KEYFILE_JSON=~/.gcloud/gcloud_credentials.json' \
    # Azure secrets
    --build-arg 'ARM_CLIENT_ID=<arm_client_id>' \
    --build-arg 'ARM_CLIENT_SECRET=<arm_client_secret>' \
    --build-arg 'ARM_TENANT_ID=<arm_tenant_id>' \
    --build-arg 'ARM_SUBSCRIPTION_ID=<arm_subscription_id>' \
    # AWS secrets
    --build-arg 'AWS_ACCESS_KEY_ID=<arm_access_key_id>' \
    --build-arg 'AWS_SECRET_ACCESS_KEY=<aws_secret_access_key>' \
    --build-arg 'AWS_DEFAULT_REGION=<aws_default_region>' \
    -t multicloud-env .
~~~
Run the container:
~~~
docker run -it multicloud-env bash
~~~
# Info
In order to get the google credentials, you need to download the secret file and extract the required values.  
More info: https://cloud.google.com/iam/docs/creating-managing-service-account-keys#creating_service_account_keys
