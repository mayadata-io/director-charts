Maya On prem
=====================


Introduction
------------

This chart bootstraps MayaOnprem on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites
- Kubernetes 1.12.0+ with RBAC enabled.
- iSCSI PV support in the underlying infrastructure.
- Deploy openebs(0.9.0 and above) and create a storagepoolclaim using external disks and create a storageClass name cstor-storage-class.
- Create a github Oauth app and have the client id,secret and auth enable ready.
- Create a secret with docker registry credentials and use it during helm install as parameter for value 'dockersecret'.

## Installing MayaOnprem
```
helm install --namespace <yournamespace> .
```

## Configuration

The following table lists the configurable parameters of the MayaOnprem chart and their default values.

| Parameter                                       | Description                                   | Default                                   |
| ------------------------------------------------|-----------------------------------------------| ------------------------------------------|
| `server.dockersecret`                           | Docker secret for pulling the images          |      none                                 |
| `server.namespace`                              | Namespace for MayaOnprem installations  |      default                              |
| `server.PROTOCOL`                               | http/https protocol for accessing the UI      |      http                                 |
| `server.URL`                                    | URL/IP address:port for UI                    |      none                                 |
| `server.API_AUTH_ACCESS_MODE`                   | TBD                                           |      unrestricted                         |
| `server.SERVER_DEFAULT_ACCESS_GRANT`            | TBD                                           |      true                                 |
| `server.API_UI_ENABLED`                         | TBD                                           |      true                                 |
| `server.SETUP_NAME`                             | TBD                                           |      mayaonprem                     |
| `server.API_AUTH_EXTERNAL_PROVIDER_ENABLED`     | TBD                                           |      true                                 |
| `server.API_AUTH_EXTERNAL_PROVIDER_CONFIGURED`  | TBD                                           |      githubconfig                         |
| `server.API_AUTH_INTERNAL_PROVIDER_ENABLED`     | TBD                                           |      false                                |
| `server.API_AUTH_INTERNAL_PROVIDER_CONFIGURED`  | TBD                                           |      none                                 |
| `server.API_AUTH_ENABLER`                       | TBD                                           |      none                                 |
| `server.API_AUTH_GITHUB_CLIENT_ID`              | TBD                                           |      none                                 |
| `server.API_AUTH_GITHUB_CLIENT_SECRET`          | TBD                                           |      none                                 |
| `server.API_AUTH_GOOGLE_CLIENT_ID`              | TBD                                           |      none                                 |
| `server.API_AUTH_GOOGLE_CLIENT_SECRET`          | TBD                                           |      none                                 |
| `server.CLUSTER_DOMAIN`                         | TBD                                           |      cluster.local                        |
| `server.FEATURE_SUBSCRIPTION_DISABLE`           | TBD                                           |      true                                 |
| `server.SUBSCRIPTION_TYPE`                      | TBD                                           |      none                                 |
| `server.FEATURE_BILLING_DISABLE`                | TBD                                           |      true                                 |
| `server.BILLING_TYPE`                           | TBD                                           |      external                             |
| `server.FEATURE_EMAIL_DISABLE`                  | TBD                                           |      true                                 |
| `server.SENDER_EMAIL_ADRESS`                    | TBD                                           |      none                                 |
| `server.SENDER_EMAIL_PASSWORD`                  | TBD                                           |      none                                 |
| `server.FEATURE_DOCS_DISABLE`                   | TBD                                           |      false                                |
| `server.DOCS_URL`                               | TBD                                           |      https://docs.mayaonline.io           |
| `server.FEATURE_CHATBOT_DISABLE`                | TBD                                           |      true                                 |
| `server.SLACK_CONFIG_BOT_CLIENT_ID`             | TBD                                           |      none                                 |
| `server.SLACK_CONFIG_BOT_CLIENT_SECRET`         | TBD                                           |      none                                 |
| `server.SLACK_NOTIFICATION_WELCOME_MESSAGE`     | TBD                                           |      none                                 |
| `server.FEATURE_KIALI_DISABLE`                  | TBD                                           |      true                                 |
| `server.ANALYTICS_GOOGLE_CODE`                  | TBD                                           |      none                                 |
|                                                 |                                               |                                           |
| `mysql.storageclass`                            | TBD                                           |      openebs-jiva-default                 |
|                                                 |                                               |                                           |
| `elasticsearch.storageclass`                    | TBD                                           |      openebs-hostpath                     |
| `elasticsearch.replicas`                        | TBD                                           |      1                                    |
|                                                 |                                               |                                           |
| `cassandra.storageclass`                        | TBD                                           |      openebs-hostpath                     |
| `cassandra.replicas`                            | TBD                                           |      1                                    |
|                                                 |                                               |                                           |
| `mayastore.storageclass`                        | TBD                                           |      cstor-storage-class                  |
|                                                 |                                               |                                           |
| `grafana.storageclass`                          | TBD                                           |      cstor-storage-class                  |
|                                                 |                                               |                                           |
| `cortex.replicationfactor`                      | TBD                                           |      1                                    |
| `cortex.timeout`                                | TBD                                           |      20s                                  |
|                                                 |                                               |                                           |
| `alertstore.replicationfactor`                  | TBD                                           |      1                                    |
-----------------------------------------------------------------------------------------------------------------------------------------------


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```shell
helm install -f values.yaml .
```

Once MOD pods are in running state, it can be accessible from browser using NodeIp given in URL along with NodePort(Nodeip:port)

> **Tip**: You can use the default [values.yaml](values.yaml)
