                                                           LAB 2 (CST8913_013)
In this on-premises architecture, the application components are deployed and managed within the organization's own data centre, requiring the organization to handle the provisioning, scaling, and maintenance of the underlying virtual machines and infrastructure.
Here is a detailed description of the on-premises architecture diagram for the application:

![on-premise](https://github.com/user-attachments/assets/79df9efa-1c70-4632-9ec9-a82a74463a06)

	
1.	Web Server (Flask): This component represents the Flask-based web server that handles the backend logic and processing of the application. It is deployed on a dedicated virtual machine within the on-premises data center.
2.	UI Frontend (React): The user interface frontend, built using React, is deployed on a separate virtual machine within the on-premises data center. This component handles the presentation and user interaction aspects of the application.
3.	Database (Postgres): The Postgres database, which stores the application data, is deployed on another dedicated virtual machine within the on-premises data center.
4.	Load Balancer: A load balancer is used to distribute incoming traffic across the web server instances, ensuring high availability and scalability of the application. The load balancer is also deployed within the on-premises data center.
5.	Virtual Network: The virtual machines hosting the various components of the application are connected through a virtual network. This virtual network provides secure communication and network isolation between the components.
6.	On-Premises Data Center: The entire application infrastructure, including the virtual machines, load balancer, and virtual network, is hosted within the organization's on-premises data center. The organization is responsible for the provisioning, scaling, and maintenance of this on-premises infrastructure.


Deploying the Application in the Cloud using IaaS Infrastructure
Diagram for IaaS Deployment

![Iaas 1](https://github.com/user-attachments/assets/7b956784-73e5-4bb7-8ff3-3c6e7e146c33)


Description for IaaS Deployment
In an IaaS (Infrastructure-as-a-Service) deployment, the application components (Web Server, UI Frontend, and Database) can be hosted on virtual machines (VMs) within the cloud infrastructure. The key aspects of this deployment are:
1.	Virtual Machines: The individual components of the application (Web Server, UI Frontend, and Database) can be deployed on separate virtual machines, allowing for scalability and flexibility in resource allocation.
2.	Cloud Storage: The application data, including the Postgres database and any static assets (e.g., images, CSS files) can be stored in cloud storage services like Amazon S3 or Elastic Block Store (EBS).
3.	Load Balancer: A load balancer can be used to distribute incoming traffic across the multiple instances of the Web Server, ensuring high availability and scalability.
4.	Virtual Network: The virtual machines and cloud storage services can be connected through a virtual network, which provides secure communication and network isolation.
This IaaS-based deployment allows for greater control over the underlying infrastructure, enabling the flexibility to customize and manage the individual components as needed. It also provides the ability to scale resources (CPU, memory, storage) independently for each component based on the application's requirements.

Deploying the Application in the Cloud using PaaS Infrastructure
Diagram for PaaS Deployment

![paas 1](https://github.com/user-attachments/assets/e6848894-ea19-43b7-9ad7-31604ea96be6)


Description for PaaS Deployment
In a PaaS (Platform-as-a-Service) deployment, the application components can be hosted on a managed platform provided by the cloud service provider, such as AWS Elastic Beanstalk. The key aspects of this deployment are:
1.	PaaS Platform: The PaaS platform, like AWS Elastic Beanstalk, handles the underlying infrastructure management, including provisioning, scaling, and monitoring of the application components.
2.	Application Deployment: The application components (Web Server, UI Frontend, and Database) can be deployed directly to the PaaS platform, without the need to manage the underlying virtual machines or infrastructure.
3.	Cloud Storage: The application data, including the Postgres database and any static assets, can be stored in cloud storage services like Amazon S3 or Relational Database Service (RDS).
4.	Automatic Scaling: The PaaS platform can automatically scale the application components based on the incoming traffic or resource utilization, ensuring high availability and performance.
This PaaS-based deployment simplifies the infrastructure management and allows the development team to focus more on the application development and deployment, rather than the underlying infrastructure. The PaaS platform handles the provisioning, scaling, and monitoring of the application components, making it a more managed and streamlined approach.


