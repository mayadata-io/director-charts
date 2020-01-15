DirectorOnPrem
=====================


Introduction
------------

This chart bootstraps DirectorOnPrem on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites
- Kubernetes 1.12.0+ with RBAC enabled.
- iSCSI PV support in the underlying infrastructure.
- Create a secret with docker registry credentials and use it during helm install as parameter for value 'dockerSecret'.

## Installing DirectorOnPrem
```
helm install --namespace <yournamespace> .
```

## Configuration

The following table lists the configurable parameters of the DirectorOnPrem chart and their default values.

| Parameter                                       | Description                                   | Default                                   |
| ------------------------------------------------|-----------------------------------------------| ------------------------------------------|
| `platform`                           | Choose your kubernetes platform          |      default                                |
| `server.dockerSecret`                           | Docker secret for pulling the images          |      none                                 |
| `server.protocol`                               | http/https protocol for accessing the UI      |      http                                 |
| `server.url`                                    | url/IP address:port for UI                    |      none                                 |
| `server.apiAuthAccessMode`                   | TBD                                           |      unrestricted                         |
| `server.serverDefaultAccessGrant`            | TBD                                           |      true                                 |
| `server.apiUiEnabled`                         | TBD                                           |      true                                 |
| `server.setupName`                             | TBD                                           |      mayaonprem                     |
| `server.apiAuthExternalProviderEnabled`     | TBD                                           |      true                                 |
| `server.apiAuthExternalProviderConfigured`  | TBD                                           |      githubconfig                         |
| `server.apiAuthInternalProviderEnabled`     |  Enable local authentication                  |      true                                     |
| `server.apiAuthInternalProviderConfigured`  |  Type of local authentication (u/p, ldap etc) |      localAuthConfig                          |
| `server.apiAuthEnabler`                       | TBD                                           |      none                                 |
| `server.apiAuthGithubClientId`              | TBD                                           |      none                                 |
| `server.apiAuthGithubClientSecret`          | TBD                                           |      none                                 |
| `server.apiAuthGoogleClientId`              | TBD                                           |      none                                 |
| `server.apiAuthGoogleClientSecret`          | TBD                                           |      none                                 |
| `server.clusterDomain`                         | TBD                                           |      cluster.local                        |
| `server.featureSubscriptionDisable`           | TBD                                           |      true                                 |
| `server.subscriptionType`                      | TBD                                           |      none                                 |
| `server.featureBillingDisable`                | TBD                                           |      true                                 |
| `server.billingType`                           | TBD                                           |      external                             |
| `server.featureEmailDisable`                  | TBD                                           |      true                                 |
| `server.senderEmailAddress`                    | TBD                                           |      none                                 |
| `server.senderEmailPassword`                  | TBD                                           |      none                                 |
| `server.featureDocsDisable`                   | TBD                                           |      false                                |
| `server.docsUrl`                               | TBD                                           |      https://help.mayadata.io/hc/en-us        |
| `server.featureChatBotDisable`                | TBD                                           |      true                                 |
| `server.slackConfigBotClientId`             | TBD                                           |      none                                 |
| `server.slackConfigBotClientSecret`         | TBD                                           |      none                                 |
| `server.slackNotificationWelcomeMessage`     | TBD                                           |      none                                 |
| `server.featureKialiDisable`                  | TBD                                           |      true                                 |
| `server.analyticsGoogleCode`                  | TBD                                           |      none                                 |
| `server.autoconnectLocalCluster`                | Autoconnect local cluster to openebs director |       true                                |
|                                                 |                                               |                                           |
| `mysql.storageClass`                            | TBD                                           |      standard                             |
|                                                 |                                               |                                           |
| `elasticSearch.storageClass`                    | TBD                                           |      standard                             |
| `elasticSearch.replicas`                        | TBD                                           |      1                                    |
|                                                 |                                               |                                           |
| `cassandra.storageClass`                        | TBD                                           |      standard                             |
| `cassandra.replicas`                            | TBD                                           |      1                                    |
|                                                 |                                               |                                           |
| `mayaStore.storageClass`                        | TBD                                           |      standard                             |
|                                                 |                                               |                                           |
| `grafana.storageClass`                          | TBD                                           |      standard                             |
|                                                 |                                               |                                           |
| `cortex.replicationFactor`                      | TBD                                           |      1                                    |
| `cortex.timeout`                                | TBD                                           |      20s                                  |
|                                                 |                                               |                                           |
| `alertStore.replicationFactor`                  | TBD                                           |      1                                    |
-----------------------------------------------------------------------------------------------------------------------------------------------


# Platform
   The `Platform` flag let you choose which platfrom you want to intall. 
    -  Default value is for GKE, Packet
    -  SUSE value is for SUSE Kubernetes platform

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```shell
helm install -f values.yaml .
```

Once DOP pods are in running state, it can be accessible from browser using NodeIp given in URL along with NodePort(Nodeip:port)

> **Tip**: You can use the default [values.yaml](values.yaml)

> **Tip**: Intial login credentails for Administrator. Username: **Administrator** Password: **password**
