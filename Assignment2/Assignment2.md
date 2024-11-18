
# VMware to Azure Migration Lab Documentation

## Team
1. Abhinav 041129125
2. Devgiri Gosai 041164730

## Table of Contents
1. [Introduction](#introduction)  
2. [Environment Setup](#environment-setup)  
3. [OS Installation](#os-installation)  
4. [Application Deployment](#application-deployment)  
5. [Migration Assessment](#migration-assessment)  
6. [VM Migration Execution](#vm-migration-execution)  
7. [Validation and Failover Testing](#validation-and-failover-testing)  
8. [Reflection](#reflection)  

---

## Introduction
This document summarizes the steps, findings, and outcomes of the VMware to Azure migration lab. The objective was to migrate a Windows Server-based virtual machine (VM) running a “Hello World” web application to Azure using Azure Migrate tools.

---

## Environment Setup
### Task: Install VMware Workstation and create a new VM  
**Objective:** Prepare a VM environment on the local system.  
**Steps Taken:**  
1. Downloaded and installed VMware Workstation.  
2. Created a new virtual machine with allocated resources (e.g., 2 CPUs, 4GB RAM, 60GB HDD).  

**Outcome:**  
The VMware Workstation was successfully set up, and a new VM instance was launched.

---
![image](https://github.com/user-attachments/assets/b4175c2d-a00f-4f07-af4c-674496890b2c)

## OS Installation
### Task: Install Windows Server OS on the VM  
**Objective:** Set up a Windows Server instance as the primary VM environment.  
**Steps Taken:**  
1. Installed Windows Server 2019 from the Azure subscription’s software portal under Education resources.  
2. Performed initial configurations, including:  
   - Setting up an administrator account.  
   - Enabling Remote Desktop and necessary firewall rules.  

**Outcome:**  
The Windows Server OS was successfully installed and configured.

---

## Application Deployment
### Task: Deploy a “Hello World” web application on the Windows Server  
**Objective:** Test basic server and network functionality.  
**Steps Taken:**  
1. Installed .NET on the Windows Server.  
2. Created a new ASP.NET Core application:  
   ```bash
   dotnet new web -o HelloWorldApp
   cd HelloWorldApp
   ```
3.Built and ran the application:

  ```bash
  dotnet build
  dotnet run
  ```
4. Verified access to the application at `http://localhost/5022` within the VM network.  

**Outcome:**  
The application was accessible at `http://localhost/5022` within the VM network.

---

## Migration Assessment
### Task: Use Azure Migrate to perform an assessment of the VM for migration readiness  
**Objective:** Evaluate the VM’s compatibility with Azure and note any necessary adjustments.  
**Steps Taken:**  
1. Created a migration project named "HelloWorldMigration".  
2. Installed the Azure Installer on the VM.  
3. Used PowerShell to run the three scripts required for Azure Migrate on the VM.  

**Challenges Encountered:**  
- **Error 2147942405: Access Denied** while setting up prerequisites for Azure Migrate.  
  - **Resolution:** Resolved the issue by following instructions from [this guide](https://learn.microsoft.com/en-us/answers/questions/514610/azure-migrate-discovery-and-assessment-error-21479). Logged in with my College ID, then proceeded with the migration steps.  
4. Completed the discovery and assessment phases.  
5. Built the business case and assessment report. I have attached the Excel file for both the business case and the assessment report in the outcome.

**Outcome:**  
A migration readiness assessment report was successfully generated, and the migration project was prepared.
![image](https://github.com/user-attachments/assets/74608697-d80b-4ea7-b27c-f110bfc515e2)
![image](https://github.com/user-attachments/assets/d2a8f5a8-7b85-462d-afd5-c47dba36074c)
![image](https://github.com/user-attachments/assets/3bcfa95d-adc7-4ed8-9e91-598835c4e22f)
![image](https://github.com/user-attachments/assets/b04e6723-f820-425e-8bea-cf98a58f252b)
![image](https://github.com/user-attachments/assets/9a8cf7d3-3c45-4a69-9125-d0fe29d9a354)
![image](https://github.com/user-attachments/assets/967559ff-0d02-4d0b-aa9c-faacd6a03e47)
![image](https://github.com/user-attachments/assets/970c5eb6-61ba-477a-af96-176d215536f3)
![image](https://github.com/user-attachments/assets/c6ef2da8-ba67-4bf3-a98d-5c540547eb8a)
![image](https://github.com/user-attachments/assets/0d2c0218-ed87-469e-98e9-5b055b37004f)
![image](https://github.com/user-attachments/assets/f1303ec6-6969-49da-a8b7-4a3eb2ac9683)
![image](https://github.com/user-attachments/assets/01e0688e-7cf4-4ffc-aef9-2d92e1874679)
![image](https://github.com/user-attachments/assets/53fe2de6-1b40-492d-87ba-f1a3231f72bd)

![image](https://github.com/user-attachments/assets/c4d05c95-34d4-4f29-968c-5c0f3edbdb9d)
![image](https://github.com/user-attachments/assets/3d406585-bb6e-4603-8b75-85c163d58df2)
![image](https://github.com/user-attachments/assets/e99e3349-eeed-4779-8a1c-afec5e12413e)


Business Case - [hellowworldapp.xlsx](https://github.com/user-attachments/files/17791092/hellowworldapp.xlsx)
Assessment Report - [HelloWorldAssessment.xlsx](https://github.com/user-attachments/files/17791091/HelloWorldAssessment.xlsx)

---

## VM Migration Execution  
### Task: Migrate the VM to Azure using Azure Migrate tools  
**Objective:** Complete the VM migration to Azure.  

**Steps Taken:**  
1. Created a new replication VM on VMware Workstation to serve as the replication server.  
   - Allocated resources similar to the primary VM.  
2. Installed the Azure Site Recovery (ASR) replication application software on the replication VM to facilitate the migration process.  
   - Configured the replication VM with the necessary credentials and settings to connect with Azure.  
3. Set up the migration project in Azure named **"HelloWorldMigration"** to track progress.  
4. Used the Azure Migrate tool to replicate the primary VM to Azure:  
   - Configured replication settings, including the source VM and target Azure VM parameters.  
   - Created an Azure Virtual Network (VNet) and a Network Security Group (NSG) for the replicated server to ensure secure connectivity.  
5. Resolved challenges encountered during the process:  
   - Faced issues while installing the Mobility Agent on the VM but resolved them using community resources like Stack Overflow and documentation from Microsoft.  
   - The replication process took approximately two hours to complete.  

**Outcome:**  
The VM was successfully replicated and migrated to Azure. Post-migration testing confirmed the functionality of the VM, including access to the **Hello World** application, which was accessible via the Azure-assigned public IP address.
![image](https://github.com/user-attachments/assets/5192259c-c239-44f0-adb1-5ed2309d87c6)

![image](https://github.com/user-attachments/assets/34f131ab-95df-4a9f-a04e-d4372d05afd6)
![image](https://github.com/user-attachments/assets/bc656eaa-9918-410c-a9ae-0fdd7c03e07f)
![image](https://github.com/user-attachments/assets/9a3b1dbd-62b7-448f-9d07-d57a19319b53)
![image](https://github.com/user-attachments/assets/e217d5df-d69f-478e-8e84-bb93ebde5e94)
![image](https://github.com/user-attachments/assets/e2eecc9c-e897-418a-af99-5854f285098e)
![image](https://github.com/user-attachments/assets/442cdb77-f780-44ac-8fef-831a1d744b93)
![image](https://github.com/user-attachments/assets/64047fa9-e37b-403a-936e-7e0bb54d358b)
![image](https://github.com/user-attachments/assets/25cd6cde-62b4-462c-b1c0-99351c9a4a27)

---

## Validation and Failover Testing
### Task: Validate the migrated VM's functionality and conduct a failover test  
**Objective:** Ensure the application runs as expected post-migration and test failover mechanisms.  
**Steps Taken:**  
1. Accessed the “Hello World” application on the Azure VM via a web browser.  
2. Simulated a failover by shutting down the primary VM and testing availability.  

**Outcome:**  
The application was functional in Azure, and failover mechanisms were validated successfully.
![image](https://github.com/user-attachments/assets/823f5810-941b-4c48-92fd-0ab8ded6e68c)
![image](https://github.com/user-attachments/assets/699bf9ad-5e30-4058-94c0-8f1cd4236e9e)
![image](https://github.com/user-attachments/assets/c61dfc16-05fa-407c-9b5c-a99a427a6cc9)
![image](https://github.com/user-attachments/assets/f444771a-ec75-48ee-96d2-1d432c147815)

---

## Reflection  

### Challenges Encountered:  
1. **Azure Migrate Setup:**  
   - Faced the error `Azure Migrate: Discovery and Assessment - Error 2147942405: Access Denied` while setting up the prerequisites.  
   - Resolution: Researched the issue on Microsoft Documentation and resolved it by following the steps provided [here](https://learn.microsoft.com/en-us/answers/questions/514610/azure-migrate-discovery-and-assessment-error-21479).  
2. **Mobility Agent Installation:**  
   - Encountered difficulties installing the Mobility Agent on the VM.  
   - Resolution: Referenced solutions from Stack Overflow and other technical forums, which helped successfully complete the installation.  
3. **Replication Duration:**  
   - The replication process took nearly two hours, requiring patience and monitoring.  
4. **Networking and Accessibility:**  
   - Initially, the application was not accessible post-migration due to Network Security Group (NSG) rules in Azure.  
   - Resolution: Updated the NSG to allow HTTP traffic, ensuring the application was accessible.  

### Insights Gained:  
1. **Pre-migration Preparation is Crucial:**  
   The discovery and assessment phase highlighted the importance of resolving potential compatibility and configuration issues before initiating the migration.  

2. **Documentation Saves Time:**  
   Having detailed instructions from official sources (e.g., Microsoft Docs) and community-driven solutions helped troubleshoot challenges effectively.  

3. **Azure Tools Simplify Migration:**  
   Azure Migrate, combined with replication software, provided an intuitive way to transition on-premises VMs to the cloud with minimal downtime.  

4. **Post-Migration Validation is Essential:**  
   Verifying application functionality and resolving accessibility issues post-migration ensured the application's reliability and readiness for use in Azure.  

5. **Learning from Challenges:**  
   The experience of troubleshooting errors like Mobility Agent installation and NSG configuration reinforced problem-solving and resourcefulness, skills critical in cloud migration projects.  


---
