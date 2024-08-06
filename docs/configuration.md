# Configuration

Minio is configured through the upstream [Minio Operator and Tenat charts](https://github.com/minio/operator/tree/master/helm) as well as a UDS configuration chart that supports the following:

## Networking

Network policies are controlled via the `uds-minio-config` chart in accordance with the [common patterns for networking within UDS Software Factory](https://github.com/defenseunicorns/uds-software-factory/blob/main/docs/networking.md).  Because minio does not interact with external resources like databases or object storage it only implements `custom` networking for the `minio` namespace. The custom key allows the ability to define additional network policies **only** for the tenant namespace:

- `custom`: sets custom network policies for the `minio` namespace (i.e. to allow clients like GitLab to connect)

## Cross-Namespace Password

Minio is currently configured to expect a single tenant using it - to enable this workload to exist in another namespace without needing elevated permissions itself, the `uds-minio-config` chart supports the following keys to place the Minio password in another namespace:

- `copyPassword.enabled`: enables the copying of the minio password secret to another namespace
- `copyPassword.namespace`: the namespace to copy the Kubernetes secret into
- `copyPassword.secretName`: the name to give the Kubernetes secret in the other namespace
- `copyPassword.secretIDKey`: the key to place the ID/user under within the Kubernetes secret
- `copyPassword.secretPasswordKey`: the key to place the password under within the Kubernetes secret

## SSO

Currently SSO for minio is not fully integrated with uds-core. To enable SSO on your deployment, some additional steps are required. First follow the guide [here](https://min.io/docs/minio/macos/operations/external-iam/configure-keycloak-identity-management.html) for generating a client in keycloak with the clientid in the format of `<minio-tenant-name>-sso` and configuring the correct protocol mappers and user attribute assignments. Next, in your bundle, override `sso.enabled` in the config chart to `true` and provide the client secret via the `identityOpenidClientSecret` config chart value.
