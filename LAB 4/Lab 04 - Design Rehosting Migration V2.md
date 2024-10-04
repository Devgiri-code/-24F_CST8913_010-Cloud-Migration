# Lab 04 - Design Rehosting Migration V2

## Containerized Application with Managed Database

**Objective**:  
This high-level design (HLD) document outlines a lift-and-shift migration for an application composed of two virtual machines: WebServerVM and SQLVM. The goal is to rehost these components in Azure by containerizing the web server and migrating the SQL database to a managed SQL service, ensuring high availability and scalability with no more than 6 hours of downtime.

---

## Target Architecture Overview:
The target architecture will involve:

### Containerization of the Web Application:
- The WebServerVM, which hosts a lightweight Node.js application, will be containerized using **Docker**.
- The containerized application will be deployed and orchestrated on **Azure Kubernetes Service (AKS)** to ensure scalability and high availability.

### Migration of the SQL Database:
- The SQLVM, currently hosting a SQL Server database, will be migrated to a **Managed SQL Database** service on Azure.
- The managed database service will provide automatic backups, high availability, and minimal maintenance efforts.

---

## Solution Diagram:
![mermaid-diagram-2024-10-04-173815](https://github.com/user-attachments/assets/422436d5-91fe-4008-926e-343938b22ada)

---

## Migration Steps:

### Containerization of the Web Application:
1. The first step is to install **Docker** on the WebServerVM and create a Docker image for the Node.js web application.
2. The Docker image will then be pushed to **Azure Container Registry (ACR)** for easy management and integration with AKS.
3. Once the image is ready, it will be deployed to the **AKS cluster**.

### Migration of the Database to Managed SQL Service:
1. The SQL database hosted on the SQLVM will be backed up and restored in Azure's **Managed SQL Database** service.
2. The Managed SQL service will handle replication, backups, and scaling automatically, ensuring minimal downtime during migration.

### Configuration of Kubernetes Cluster for High Availability:
1. The **Azure Kubernetes Service (AKS)** cluster will be configured to run multiple replicas (pods) of the web application to ensure redundancy and load balancing.
2. AKS will automatically scale the number of running pods based on incoming traffic to maintain performance during peak times.
3. **Azure Load Balancer** will be set up to distribute traffic evenly across the pods, ensuring high availability.
4. The database will be integrated with the application using secure connections to the managed SQL service.

---

## Conclusion:
The proposed migration plan leverages containerization and **Azure Kubernetes Service (AKS)** for the web server, ensuring that the Node.js application can scale efficiently with high availability. The SQL database will be migrated to a **Managed SQL Database** service, which simplifies management while offering enhanced reliability. By following this migration strategy, the application will be rehosted in the cloud with minimal downtime, meeting the 6-hour limit.
