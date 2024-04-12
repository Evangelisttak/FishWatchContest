# The "Fish Watch" System

![image](./Images/Title.png)

#### Meeting the Needs of Modern Fish Farming

Authors:

* [Kuldeep Shrivastav](https://www.linkedin.com/in/kuldeep-shrivastav-0966a214)
* [Akhil Nayta](https://www.linkedin.com/in/akhil-nayta-27564749)
* [Tarun Mittal](https://www.linkedin.com/in/tarun-mittal-734268155)

## Prelude

Nestled in the heart of Scotland, Livestock Insights Incorporated is a global powerhouse, its flagship service Fish Watch revolutionizing the aquaculture industry. With a keen focus on fish health and farm management, Fish Watch harnesses cutting-edge technology to provide farmers with invaluable insights. From monitoring individual fish to analyzing water quality and weather data, it offers a comprehensive solution tailored to the needs of modern aquaculture. Fish farmers worldwide rely on its precision to detect signs of disease, parasites, and optimize harvest timing for maximum yield. As a beacon of innovation, Livestock Insights continues to expand its reach, empowering farmers and fostering sustainable practices across the globe. With Fish Watch at their side, fish farmers navigate the complexities of aquaculture with confidence, ensuring a prosperous future for the industry.

## Vision

The vision for Livestock Insights Incorporated is to be the global leader in empowering aquaculture farmers with cutting-edge technology and insights, ensuring sustainable and efficient practices that benefit both the industry and the environment. We envision a world where **Fish Watch** becomes synonymous with excellence in fish farming, enabling farmers to optimize production, minimize environmental impact, and enhance the health and welfare of their livestock. Through innovation, collaboration, and a steadfast commitment to integrity, we aspire to transform the aquaculture landscape, driving positive change that reverberates throughout the entire supply chain. Together, we aim to build a future where aquaculture thrives as a cornerstone of global food security, powered by data-driven solutions and a shared vision of responsible stewardship.

## Business Requirements

* **Scalability:** The system should be able to handle varying scales of customers, from those with a single farm to those with hundreds, each containing potentially millions of fish.
* **Real-time Data Processing:** The architecture must support real-time processing of data from water monitors(Including PH, temperature, salinity, oxygen levels and other factors), underwater cameras (( fish health , Size , activity,  parasite detection), and fish recognition systems (to monitor health and life cycle of fish),   to provide timely insights to farmers .
* **Customizable Dashboards:** Farmers should be able to customize their dashboards to view relevant information about their farms, including water quality, fish health, and alerts.
* **Alerting Mechanism:** The system needs to trigger alerts based on customizable thresholds set by farmers, including both simple parameters like pH levels , more complex events like adverse weather conditions and water quality.
* **Data Modeling for Harvest Optimization:** The architecture should support the collection and analysis of data to build AI models that predict factors contributing to successful harvests.
* **Cross-Farm Insights:** Large customers should be able to derive insights across multiple farms, enabling centralized management and decision-making.
* **Device Accessibility:** The system should be accessible from various devices ( mobile , web application), including rugged industrial devices used at sea during harvests.
* **Connectivity Challenges:** Considering that fish farms are often in remote areas with poor cellular signal, the architecture should address connectivity challenges including offline support.
* **Multi Geo Location Support:** The architecture should support the devices deployed across various farms present in multiple geographical location.q
* **Extensibility for Future Enhancements:** The architecture should be flexible and extensible to accommodate future enhancements, such as adding capabilities for other livestock or aquarium management.

## Assumptions

* **Nature of Devices:** The devices deployed in farms are categorized as IoT devices.
* **Device Capabilities:** Devices can store essential identifiers like enclosure, farm, and geographical location.
* **Gateway Installation:** A physical gateway device is installed at each farm location to support offline operations.
* **Preference for Azure Services:** The organization prefers using Microsoft Azure services for affordability and effectiveness.
* **Utilization of Azure Managed Services:** The organization is inclined to use various managed services offered by Azure wherever suitable.
* **Self-Storage Capability:** Devices, along with gateways, possess self-storage capacity. (Using  lightweight, embedded databases (e.g., SQLite, Berkeley DB) that can run directly on the IoT device to store data temporarily until an internet connection is available)
* **Gateway Communication:** Gateways can communicate with devices using wired or wireless protocols (e.g., Bluetooth) without reliance on internet connectivity

## Major Abilities supported in the architecture

* [Major Abilities](./MajorAbility.md)

## The Architecture

### [Functional Architecture](./Architecture/FunctionalArchitecture.md)

* Illustrates the functional components and their interactions within the system.
* Provides a high-level overview of the system's functionality without diving into technical details.
* Focuses on the logical organization of components and their relationships.
* Helps stakeholders understand the system's behavior and flow of data or processes.

### [Application Architecture](./Architecture/ApplicationArchitecture.md)

* Builds upon the functional architecture by incorporating the technical stack and communication protocols.
* Details the specific technologies, tools, and frameworks used in the system.
* Describes how the functional components are implemented using the chosen technical stack.
* Specifies the communication protocols between different components and services.

### [Deployment Architecture](./Architecture/DeploymentArchitecture.md)

* Specifies how the system is deployed across various environments.
* Describes the infrastructure components such as servers, containers, and networking configurations.
* Provides insights into scalability, reliability, and resilience aspects of the system's deployment.

### [Final Architecture](./Architecture/FinalArchitecture.md)

* the technical architectural idea.

## Business continuity plan and availability

The below are built-in features that are typically available by default and do not incur additional costs in the mentioned Azure managed services which support business continuity:

### Utilizing Inbuilt Features of Managed Services:

* **Managed Database Service ( Azure Cosmos DB):** Backup, replication, and failover mechanisms ensure data redundancy and automatic failover.
* **Managed Kubernetes Service:** Replication and failover capabilities ensure uninterrupted application availability.

### Ensuring Uninterrupted Business Operations:

* Regular backups and restore mechanisms for application and databases.
* Replication and failover minimize downtime and ensure continuous service delivery.

### Business Continuity in Incidents:

* Swift disaster recovery through replica promotion or backup restoration.
* Automatic failover and replication minimize downtime, ensuring business continuity.

## Monitoring and Logging with Azure Application Insights

Azure Application Insights offers comprehensive capabilities for real-time performance monitoring, error tracking, usage analytics, and custom logging. Integrated with application microservices, it enables proactive issue resolution and optimization, ultimately delivering exceptional user experiences.

* **Real-time Performance Monitoring:** Track response times, request rates, and resource utilization to optimize application performance.
* **Error Tracking:** Automatically detect and log exceptions and errors, enabling proactive issue identification and resolution.
* **Usage Analytics:** Collect telemetry data on user interactions to understand user behavior and prioritize feature development.
* **Custom Logging:** Integrate custom logging and tracing for capturing tailored diagnostic information.
* **Alerting and Notifications:** Set up customizable alerts based on predefined metrics thresholds for proactive monitoring and timely response.
* **Integration with Azure Monitor:** Seamlessly integrate with Azure Monitor for centralized monitoring and correlation of telemetry data across services.
* **Microservice Integration:** Integrate Application Insights with application microservices for deep insights into service health and performance, facilitating proactive optimization and exceptional user experiences.

## Security Measures

Security Measures Overview:

### Incoming Traffic:

* Azure IOT hub being the entry point for device traffic , below security measures are implemented.
* Azure IoT Hub provides built-in security features to protect incoming traffic, including.
* **Device Authentication:** IoT devices must authenticate with Azure IoT Hub using security tokens or X.509 certificates, ensuring that only authorized devices can connect to the hub.
* **Device-to-Cloud Communication Encryption:** Data transmitted from devices to Azure IoT Hub is encrypted using industry-standard encryption protocols (TLS/SSL), preventing eavesdropping and data interception during transmission.

### Component Security:

* Managed Kubernetes Service: Secure configurations and access controls.
* Managed Database Service: Encryption, access control, and network or firewall policies.
* Managed Blob Storage: Data encryption, access controls and network or firewall policies.

### Communication between various services:

**Secure Communication Channels:** Encrypted data in transit and at rest , access control using network security policies , firewall.

### Authentication and Authorization:

Using Azure Active directory for authentication , following Industry standard protocol Oauth 2.0.

## Conclusion:

* Robust and scalable architecture.
* Utilization of managed services for scalability and optimal performance.
* Security measures with managed security services, firewalls, and secure communication channels.
* Integration of Azure ADD for secure authentication and authorization.
* Reliable data management with managed database and blob storage services.
* Business continuity ensured through inbuilt features of managed services for backup, replication, and failover.
* Effective monitoring and logging with a managed service for proactive issue detection.
* Solid foundation for future growth and success of Fish watch.
* Offline connectivity support using gateway and IOT edge.
