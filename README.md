
<p align="center">
  <img src=".img/LogoDellTechnologies.png" />
</p>

# Platform as a Service Backup Solution

[![GitHub Release][release-img]][release]
[![Test][test-img]][test]
[![License: Apache-2.0][license-img]][license]

### Target Audience

|Audience |Purpose  |
|--|--|
| Cloud Center of Excellence | Understand the Design of this Service and how to implement it|


## Overview

### Description
This solution installs and configures an autodiscovery proxy backup solution for use case (*) with Avamar and Data Domain, the proxy is implemented in a container technology, 
taking advantage from portability, scaling and repeatability, and can be deployed by devops orchestration tool over Kubernetes or others.
This proxy only requires a configuration file (dps-setup.json) and script setup (dps-setup.sh) to deploy it. 
Proxy is considered as another client for Avamar and Datadomian and for this reason it can be integrated into the flow of administration and control of protection tasks.

This backup proxy is a rule-based engine used to discover cloud resources (1), resources are handled according to tagging or fix values to decide which is backed or restored (2) or not, if the password is needed the proxy will access to a key vault to get it (3). Backup data is sent to the backup server through the Avamar client.

#### File-based use case diagram
	
File-bases use cases mount blob storage as a regular file system using blobfuse. Avamar reads these files using his Linux plug-in. Blobfuse and Avamar client reside in the docker container.

<p align="center">
<img src=".img/bkp-proxy_File-based_use_case.png" alt="File-based use case diagram" width="400">
</p>

#### Database use case diagram

Database use cases dumps or exports data from source to a DDboost FS mounted from the docker container. 
DDboost FS client, Avamar client, and use case especific dump/export command reside in the docker container.
	
<p align="center">
<img src=".img/bkp-proxy_DDBB_use_case.png" alt="Database use case diagram" width="400">
</p>


## How to configure the infraestructure


:link: [Repo layout](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/repo_layout.md)


:link: [DCI and CVM configuration](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/DCI_and_CVM_config.md)


## How to deploy a container


:link: [Container deployment from command line](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/container_deployment_from_DCI.md)

:link: [Container deployment using Jenkins ](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/container_deployment_using_jenkins.md)


## How to do backups and restores

Remember use case specific info:

:link: [Azure use cases specific](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/AzureDockerTypes.csv) 

:link: [AWS use cases specific](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/AWSDockerTypes.csv) 



Please see access requirement by use case:

:link: [Cloud, Avamar, Data Domain and Container requirements](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/cloudBackupAndContainer_requirements.md) 

:link: [ADLS](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/adls_requirements.md)

:link: [Azure SQL](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/azsql_requirements.md)

:link: [Blob storage](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/Blobstorage_requirements.md) 

:link: [Cosmos SQL](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/CosmoSQL_requirements.md)

:link: [Databricks](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/databricks_requirements.md)

:link: [Event Hub](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/eventhub_requirements.md)

:link: [File Storage](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/Filestorage_requirements.md)

:link: [HDInsigth](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/hdinsigth_requirements.md)

:link: [Kafka (IaaS)](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/kafka_requirements.md)

:link: [Key Vault](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/KeyVault_requirements.md)

:link: [MariaDB](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/Maria_DB_requirements.md)

:link: [MinIO](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/minio_requirements.md)

:link: [NetApp Storage](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/Netappstorage_requirements.md)

:link: [PostgreSQL](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/postgresql_requirements.md)

:link: [Purview](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/purview-requirements.md)

:link: [Redis](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/UseCaseRequirements/redis_requirements.md)


### Json configuration guidelines

Files located in  **jsonfilesTemplates** (example **dps-setup.(dockerType).json**) contains the keys to be configurated to deploy a new business container, please follow this link for help  
[JSON ReadME](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/README-dps-setup.json.md). 

### Supported cloud login methods

:link: [Azure login](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/SupportedAzureLoginMethods.md)

### Backup and restore procedures
  
[Avamar backup procedure](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/Backup-Procedure.md). 

[Avamar restore procedure](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/Restore-Procedure.md). 

## Ephemeral Containers 

[Avamar, Data Domain and Docker containers integration full demo](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/EphemeralContainers.md). 


[test]: https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/.github/workflows/terraform.yml
[test-img]: https://github.com/aquasecurity/trivy/actions/workflows/test.yaml/badge.svg
[release]: https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/releases
[release-img]: https://img.shields.io/github/release/aquasecurity/trivy.svg?logo=github
[license]: https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/LICENSE
[license-img]: https://img.shields.io/badge/License-Apache%202.0-blue.svg

### Additional procedures

#### Infra related

[Avamar client upgrade](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/AvamarClientUpgrade.md).

[Autostart Podman Containers](https://github.com/ps-iberia-public-cloud-backup/DellDPS-PaaS-Backup/blob/main/docs/AutostartPodmanContainers.md).
