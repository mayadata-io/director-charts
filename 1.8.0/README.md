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
| `platform`                                      | Choose your kubernetes platform          |      default                                |
| `server.dockerSecret`                           | Docker secret for pulling the images          |      none                                 |
| `server.protocol`                               | http/https protocol for accessing the UI      |      http                                 |
| `server.url`                                    | url/IP address                    |      none                                 |
| `server.apiAuthAccessMode`                   | TBD                                           |      unrestricted                            |
| `server.serverDefaultAccessGrant`            | Allow users to sign-up and use Director without explicit approval from admin  |      true    |
| `server.apiUiEnabled`                         | Allow a rich API viewer                       |      true                                 |
| `server.setupName`| Name of the setup, should be set to directoronprem unless requested otherwise by MayaData |      directoronprem       |
| `server.apiAuthExternalProviderEnabled`     | Enable OAuth one click sign-in via Google and/or GitHub  |      true                         |
| `server.apiAuthExternalProviderConfigured`  | Specify supported authentication providers, e.g. githubconfig\,googleconfig |      githubconfig   |
| `server.apiAuthInternalProviderEnabled`     |  Enable local and directory authentication services  |      true                              |
| `server.apiAuthInternalProviderConfigured`  |  Types of local authentication (e.g. localAuthConfig\,adconfig ) |      localAuthConfig     |
| `server.apiAuthGithubClientId`              | GitHub Oauth client-id if github external auth provider is enabled    |   none                |
| `server.apiAuthGithubClientSecret`          | GitHub Oauth client-secret if github external auth provider is enabled   |      none         |
| `server.apiAuthGoogleClientId`              | Google Oauth client-id if Google external auth provider is enabled    |      none       |
| `server.apiAuthGoogleClientSecret`          |  Google Oauth client-secret if Google external auth provider is enabled  |      none                                 |
| `server.clusterDomain`                      | TBD                                           |      cluster.local                        |
| `server.featureSubscriptionDisable`         | TBD                                           |      true                                 |
| `server.subscriptionType`                   | TBD                                           |      none                                 |
| `server.featureBillingDisable`              | TBD                                           |      true                                 |
| `server.billingType`                        | TBD                                           |      external                             |
| `server.featureEmailDisable`     | Email feature is disabled when users' environment doesn't have dedicated mail accounts of a mailserver to send out mails via DirectorOnPrem   |  true |
| `server.senderEmailAddress`         | bot email account at a mailserver to send out emails via this application   |   none              |
| `server.senderEmailPassword`                  | password of the bot email account           |      none                                 |
| `server.featureDocsDisable`                   | TBD                                         |      false                                |
| `server.docsUrl`                              | TBD                                         |      https://help.mayadata.io/hc/en-us    |
| `server.featureChatBotDisable`                | TBD                                         |      true                                 |
| `server.slackConfigBotClientId`             | TBD                                           |      none                                 |
| `server.slackConfigBotClientSecret`         | TBD                                           |      none                                 |
| `server.slackNotificationWelcomeMessage`     | TBD                                          |      none                                 |
| `server.featureKialiDisable`                  | TBD                                         |      true                                 |
| `server.featureAnalyticsDisable`              | Disable anonymous usage data collection     |      none                                 |
| `server.autoconnectLocalCluster`              | Autoconnect host cluster to openebs director |       true                                |
| `server.maxMemberCountInOneProject`           | Maximum member count in one project. Some special values -  0 -> You can add as many members as you want. 1 -> You can not add any member(Disable teaming).         |       10                                |
|                                                 |                                               |                                           |
| `mysql.storageClass`                            | storage engine/backend for MySQL              |      standard                             |
|                                                 |                                               |                                           |
| `elasticSearch.storageClass`                    | storage engine/backend for your logs storage  |      standard                             |
| `elasticSearch.replicas`                        | storage replication for logs         |      1                                    |
|                                                 |                                               |                                           |
| `cassandra.storageClass`                        | storage engine/backend for Cassandra          |      standard                             |
| `cassandra.replicas`                            | storage replication for Cassandra             |      1                                    |
|                                                 |                                               |                                           |
| `mayaStore.storageClass`                        | storage engine/backend for mayastore          |      standard                             |
|                                                 |                                               |                                           |
| `grafana.storageClass`                          | storage engine/backend for grafana            |      standard                             |
|                                                 |                                               |                                           |
| `cortex.replicationFactor`                      | TBD                                           |      1                                    |
| `cortex.timeout`                                | TBD                                           |      20s                                  |
|                                                 |                                               |                                           |
| `alertStore.replicationFactor`                  | TBD                                           |      1                                    |
-----------------------------------------------------------------------------------------------------------------------------------------------


# Platform
   The `Platform` flag let you choose which platform you want to intall.
    -  Default value is for GKE, Packet
    -  SUSE value is for SUSE Kubernetes platform

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```shell
helm install -f values.yaml .
```

Once DOP pods are in running state, it can be accessible from browser using NodeIp given in URL. If ingress is used as deployment then URL is given along with NodePort(Nodeip:port)

> **Tip**: You can use the default [values.yaml](values.yaml)

> **Tip**: Initial login credentials for Administrator. Username: **Administrator** Password: **password**
