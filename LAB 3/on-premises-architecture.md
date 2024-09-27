 **On-Premises Architecture**

 **Overview**

The current infrastructure is hosted on-premises and consists of the following components:

1. **Web Application (Monolithic)**: Hosted on physical servers and handling all business logic.
2. **SQL Server Database**: A relational database that stores business-critical information.
3. **File Storage**: A local file system is used for storing documents, media files, and other assets.
4. **Networking**: The company uses physical routers and firewalls to manage internal and external traffic.
5. **Email Services**: The company manages client email notifications through either internal or third-party services.

   **Architecture Diagram**

Here is the Mermaid diagram representing the on-premises architecture:

graph TD
    subgraph On-Premises Architecture
        A[Web Application] --> B[SQL Server Database]
        A --> C[File Storage (Local File System)]
        A --> D[Networking (Routers/Firewalls)]
        A --> E[Email Service]
    end
    B --> D
    C --> D
    E --> D
