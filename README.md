# Deployment of Siemens NX on Azure Virtual Desktop
Presented In Order To Obtain the National Engineering Diploma
made within **Piterion Tunisia**

## Introduction
This project aims to provide an automated solution for deploying Siemens NX on Azure Virtual Desktop. The proposed solution addresses the challenges of manual setup, monitoring, and cost optimization by utilizing Terraform, a CI/CD pipeline with GitHub Actions, and various Azure services.

### Analysis of the Existing and Problematic
Deploying Siemens NX on Azure Virtual Desktop presents several challenges:

- **Complex and Time-Consuming Setup**: Manual setup involves precise configuration of virtual machines, network settings, and software installation.
- **Lack of Comprehensive Monitoring**: Manual deployment often lacks robust monitoring capabilities.
- **Suboptimal Cost Management**: Without automated tools, tracking and optimizing resource usage becomes challenging.

### Proposed Solution
- **Terraform for Automated Deployment**: Use Terraform, an infrastructure as code (IaC) tool, to automate the deployment process, ensuring consistent and error-free setup.
- **CI/CD Pipeline with GitHub Actions**: Integrate Terraform with a CI/CD pipeline via GitHub Actions to streamline the deployment process.
- **Cost Optimization with VM Control System**: Implement Azure services to manage VMs, start and stop them based on working hours, and monitor CPU usage to shut down VMs when not needed.

## VM Control System
###Sequence Diagram
![sequence_diag](/images/sequence%20diagram.png)
The VM Control System includes:

**Azure Functions**:
*HTTP Trigger Function*: Manages scheduling and sequencing scenarios, ensuring task completion.
AutoStop HTTP Trigger Function: Automatically stops processes or services when conditions are met, optimizing resource usage.
Azure Logic Apps: Configures and manages VM start and stop schedules. Automatically creates five Logic Apps instances for the following scenarios:

*Scheduled*: Start and stop actions based on a specified schedule.
*Sequenced*: Start and stop actions for VMs with predefined sequencing tags based on a schedule.

**Application Insights**: Transmits all trace logging information to a linked Application Insights instance, storing telemetry data viewable via a shared Azure dashboard.
### Post Deployment
![post_dep](/images/azure%20portal.png)