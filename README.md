## SOC Automation Project
This project focuses on designing a Security Operations Center (SOC) lab environment. It includes creating a detailed diagram with Draw.io to visualize the network setup and data flow, involving components like PCs, routers, and key security elements such as the Windows 10 client with Wazuh agent, Wazuh manager, The Hive, and Shuffle, all hosted on servers configured on Digital Ocean. Key tasks include setting up and configuring virtual machines on VirtualBox, installing and configuring security monitoring tools like Sysmon and Wazuh, and integrating an automated workflow with SOAR platforms for efficient threat detection and response. This setup enhances security monitoring and incident response capabilities within a controlled lab environment hosted on cloud servers.

## Designing a SOC Lab Environment Using Draw.io
I crafted a logical diagram using Draw.io to visually represent the data flow and essential components of our SOC lab environment. This diagram includes fundamental icons representing PCs, routers, and internet connections, which outline our network setup. Key components such as the Windows 10 client with Wazuh agent, Wazuh manager, The Hive, and Shuffle are clearly labeled to elucidate their roles and functionalities.

Connections between these elements are depicted with arrows to show the direction of data movement, highlighting different types of interactions such as event sending, alert forwarding, and response actions. The diagram is color-coded and employs various line types to distinguish between these interactions, adding an extra layer of clarity to our SOC setup.

![diagram](https://github.com/scriptsorwhatever/SOC/assets/130718809/927d6cd7-69ab-451e-a972-9c3bf1f000d0)

![workflow (2)](https://github.com/scriptsorwhatever/SOC/assets/130718809/0cd1c754-39da-417c-8fd1-94df628ef910)

## Setting Up Key Components
- **Virtual Machine Creation and Configuration on VirtualBox:** Utilizing VirtualBox, I configured a new Windows 10 virtual machine, ensuring optimal settings for memory, processor, and storage were selected. The installation process was meticulously followed using a Windows 10 ISO image.

- **Sysmon Installation on Windows 10:** After downloading and configuring Sysmon with a custom configuration file, I verified its successful installation through the services and event logs, ensuring it was operational.

- **Wazuh Server Setup on Digital Ocean:** A new virtual machine (droplet) was configured on Digital Ocean, running Ubuntu 20.04, specifically tailored for Wazuh operations. I secured this server with strict firewall rules that limited SSH access exclusively to my public IP.

- **The Hive Installation and Configuration on Digital Ocean:** Another server was prepared on Digital Ocean for The Hive, also running on Ubuntu 20.04. I installed necessary components like Java, Cassandra, and Elasticsearch before finally installing The Hive software. The server was secured with comprehensive firewall rules to protect against unauthorized access.

- **Elasticsearch and Cassandra Configuration:** Adjustments to configuration files for both Elasticsearch and Cassandra were made to reflect the correct settings for our environment. Services were started and enabled to run concurrently, ensuring their active status.

## Operational Workflow and Security Integration
- **Mimikatz Detection and Logging:** I configured Wazuh to log all security events, including those generated by Sysmon and Mimikatz. A custom rule was created in Wazuh to detect Mimikatz usage effectively, ensuring high alert priority for such events.

- **Integration of SOAR Platform with Wazuh and The Hive:** A workflow was established in Shuffle to handle security alerts and automate responses. This included setting up webhooks to receive alerts from Wazuh and configuring automated responses.

- **Automated Alert Handling and Response:** Actions were set up in Shuffle to analyze incoming alert data, apply decision logic, and initiate appropriate responses. Integration with VirusTotal was enabled to assess the reputation of file hashes associated with alerts, enriching the data for better decision-making.

- **Email Notification System:** I integrated an email notification system within the SOC workflow to automatically alert our security analysts when threats are detected. This system uses conditional logic to generate emails with detailed information about the security threats, enabling timely and informed responses.

- **Final Testing of Workflow:** The entire automated workflow, linking Shuffle, Wazuh, and The Hive, was thoroughly tested to ensure it responds correctly to simulated security incidents, validating the efficacy of our SOC setup.

This comprehensive approach not only enhances our security posture but also streamlines the process of monitoring and responding to potential threats, making our SOC environment robust and efficient.
