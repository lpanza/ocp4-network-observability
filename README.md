# ocp4-network-observability
This repository is meant to provide a simple demo of the Network Observability Operator.

By adding the root of this repository to an ArgoCD instance, you can simply deploy the monitoring Network Observability Operator provided by RedHat.

As an external prerequisite you will need to have an S3 storage provider, in our case we already have ODF installed because we used the MultiCluster DevSecOps Validated Pattern to install the cluster.

# Careful!
The only manual operation that you need to do is to create the ```logging-loki-s3``` secret in the ```netobserv``` namespace, it should look like this:
```
apiVersion: v1
kind: Secret
metadata:
  name: logging-loki-s3
  namespace: netobserv
stringData:
  access_key_id: <ACCESS_KEY_ID>
  access_key_secret: <ACCESS_KEY_SECRET>
  bucketnames: <BUCKET_NAME>
  endpoint: <S3_ENDPOINT>
  region: <S3_REGION>
```
