# Offline Connectivity Support using Gateway and Azure IoT Edge
## Status
ACCEPTED
## Context 
In the development of the Fish Watch application, ensuring connectivity in remote areas with poor cellular signal is a critical requirement. To address this challenge, a solution is needed to support offline operations at fish farm locations using physical gateway devices and Azure IoT Edge.
## Decision
We have decided to implement offline connectivity support using physical gateway devices installed at each fish farm location, coupled with Azure IoT Edge for local data processing and analytics.
## Rationale
* **Connectivity Challenges:**

Fish farms are often located in remote areas with limited or no cellular signal, posing challenges for continuous connectivity. Supporting offline operations is essential to ensure uninterrupted functionality of the Fish Watch application in such environments.

* **Gateway Installation:**

Installing a physical gateway device at each farm location serves as a local hub for data collection, processing, and communication. This gateway device acts as a bridge between the local environment and the cloud, enabling offline operations and data synchronization.

* **Azure IoT Edge:**

Leveraging Azure IoT Edge allows for deploying and managing containerized workloads on edge devices, such as the physical gateway devices installed at fish farm locations. IoT Edge enables local data processing, analytics, and decision-making capabilities, even when connectivity to the cloud is unavailable.

* **Offline Connectivity Support:**

By utilizing Azure IoT Edge, the Fish Watch application can continue operating offline, performing essential data processing and analytics tasks locally on the gateway devices. Once connectivity is restored, the gateway devices can synchronize data with the cloud, ensuring seamless integration and data consistency.

## Consequences
* **Hardware Requirements:** Deploying physical gateway devices at each farm location incurs additional hardware costs and maintenance overhead. Careful consideration of hardware specifications and deployment logistics is necessary to ensure optimal performance and reliability.
  
* **Edge Computing Complexity:** Implementing Azure IoT Edge introduces complexities associated with edge computing, including managing containerized workloads, updating software, and ensuring security and compliance standards are met.
  
* **Data Synchronization Challenges:** Ensuring data consistency and integrity between offline and online environments requires robust synchronization mechanisms and conflict resolution strategies. Regular monitoring and testing of data synchronization processes are essential to maintain data accuracy and reliability.