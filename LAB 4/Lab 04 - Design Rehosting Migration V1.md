# Lab 04 - Design Rehosting Migration (HLD Document) V1

## Application Overview:
The application consists of two virtual machines:
- **WebServerVM**: Frontend server hosting static content.
- **SQLVM**: Backend server hosting the application’s SQL database.

---

## Target Architecture:
To ensure high availability, the application will be deployed in a multi-region setup with the following features:

### Multi-Region Deployment:
- The application will be deployed in two regions, **Region A** and **Region B**, to provide redundancy and handle regional failures. Both regions will host the WebServerVM and SQLVM.

### Load Balancing:
- Load balancers will be deployed in both regions to ensure that traffic is distributed between the WebServerVM instances. The load balancers will intelligently route traffic to the healthy region in case of regional downtime.

### Automatic Failover:
- In the event of a failure in one region (e.g., Region A), the load balancers will automatically redirect traffic to Region B. This includes database failover, ensuring that the SQLVM in Region B takes over seamlessly.

### Replication:
- The WebServerVM will serve static content and will be replicated across both regions. The SQLVM database will also be replicated between regions, ensuring data consistency and minimal downtime during failover.

---

## Target Architecture Diagram:
![mermaid-diagram-2024-10-04-042011](https://github.com/user-attachments/assets/10ec09ce-414e-4147-a29a-2160053fde4b)

---

## Description of Target Architecture:

### High Availability:
To minimize downtime and ensure continuous service availability, the application is deployed across two cloud regions. The WebServerVM and SQLVM are replicated across both regions to handle regional failures. In case of a failure in one region (e.g., Region A), traffic is seamlessly routed to Region B.

### Load Balancing:
Two load balancers are deployed, one in each region. These load balancers will manage incoming traffic and distribute it across the web servers (WebServerVM) in the respective region. If one region becomes unavailable, the load balancer will redirect traffic to the healthy region.

### Replication and Failover:
The SQLVM instances are configured with synchronous replication, ensuring data consistency between the regions. In the event of a failure in Region A, the system automatically fails over to Region B’s SQLVM, ensuring that the backend database remains available with minimal downtime.

---

## Migration Steps:
1. **Replicate Virtual Machines Across Regions**:
   - Deploy WebServerVM and SQLVM to both Region A and Region B.
   - Ensure that both regions are configured identically, with replication enabled for the virtual machines to keep them synchronized.

2. **Configure Load Balancers**:
   - Deploy Load Balancers in both Region A and Region B.
   - Configure them to route traffic to the local WebServerVM instances and provide failover support to the other region in case of failure.

3. **Database Replication and Failover**:
   - Set up synchronous database replication between the SQLVM in Region A and Region B.
   - Configure automatic failover for the SQL database to ensure that in the event of downtime, the application can seamlessly switch to the SQLVM in the secondary region (Region B).
