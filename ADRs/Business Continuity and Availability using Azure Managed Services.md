# Business Continuity and Availability using Azure Managed Services
## Status
ACCEPTED
## Context 
In the development of the Fish Watch application, ensuring business continuity and availability are critical requirements to minimize downtime and maintain uninterrupted service delivery. Leveraging Azure managed services offers built-in features that provide backup, replication, failover mechanisms, and other capabilities to support business continuity and ensure high availability.
## Decision
We have decided to utilize the inbuilt features of Azure managed services, specifically Azure Cosmos DB for data storage and Azure Kubernetes Service (AKS) for container orchestration, to ensure business continuity and availability in the Fish Watch application.
## Rationale
* **Managed Database Service (Azure Cosmos DB):**

**Backup and Replication:** Azure Cosmos DB provides built-in backup, replication, and failover mechanisms that ensure data redundancy and automatic failover in the event of hardware failures or other disruptions. This minimizes the risk of data loss and ensures continuous availability of critical data.

* **Managed Kubernetes Service (Azure Kubernetes Service):**

**Replication and Failover:** AKS offers replication and failover capabilities that support uninterrupted application availability. This ensures that Fish Watch application instances are automatically redeployed or scaled out to maintain service availability during planned or unplanned outages.
* **Regular Backups and Restore Mechanisms:**

Implementing regular backups and restore mechanisms for both the application and databases ensures that data and application state can be recovered quickly in the event of a disaster or data corruption. This contributes to business continuity by minimizing downtime and data loss.

* **Swift Disaster Recovery:**

Leveraging replica promotion or backup restoration capabilities enables swift disaster recovery in the event of a major incident or catastrophic failure. This ensures that Fish Watch application components can be restored to a functional state with minimal disruption to business operations.
* **Automatic Failover and Replication:**

Automatic failover and replication mechanisms provided by Azure managed services minimize downtime by automatically redirecting traffic to healthy instances or replicas in the event of a service disruption. This ensures continuous service delivery and enhances the reliability of the Fish Watch application.
## Consequences
* **Cost Considerations:** While the built-in features of Azure managed services do not incur additional costs, optimizing resource usage and capacity planning are necessary to manage overall operational costs effectively.
  
* **Dependency on Azure:** Relying on Azure managed services for business continuity and availability necessitates a dependency on Azure as the cloud provider. Mitigation strategies should be in place to address potential service outages or disruptions.
  
* **Monitoring and Testing:** Regular monitoring and testing of backup, replication, and failover mechanisms are essential to ensure their effectiveness and reliability in real-world scenarios. Continuous improvement and refinement of disaster recovery procedures may be required based on performance insights and lessons learned from incidents.