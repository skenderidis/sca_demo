# Secure Cloud Architecture Demo
> A tool to demo a F5 Secure Cloud Architecture along with Automation ToolChain


# Overview

This tool will help you deploy a full infrastructure on Azure including F5 VEs, VNETs, NSG, Linux and Applications with the use of Terraform and help you demonstrate the Automation lifecycle with F5's Automation Toolchain (DO, AS3 and TS). 

[![INSERT YOUR GRAPHIC HERE](https://github.com/skenderidis/sca_demo/blob/master/images/sca_11.png?raw=true)]()

---

## Installation
The demo tool runs as a docker container. 

```shell
$ docker run -dit -p 80:80 skenderidis/sca_demo
```

> To get started...

## Pre-requisities

### DNS Domain
In order for the demo to work you need to have your DNS zone configured in Azure under a resource group called "f5demo_dns". This zone is used to register the F5 devices that will be created as well as provide a public FQDN for the apps that we will be publishing. 
Note: It is important that the Resource Group is called "f5demo_dns" as it is being used by terraform to make all the neccessary configurations.

### Service Account
Follow the instructions on the following link on how to create a service principal. https://clouddocs.f5.com/training/community/azure-saca/html/class1/intro.html#create-a-service-principal 

### Enable Programmatic deployment
Follow the instructions on the following link on how to create programmatic deployments. https://clouddocs.f5.com/training/community/azure-saca/html/class1/intro.html#enable-programmatic-deployment.
You have to enable programmatic deployment for the following 4 types:

        "F5 BIG-IP Virtual Edition - BEST (PAYG, 25Mbps)"    
        "F5 BIG-IP Virtual Edition - BEST (PAYG, 200Mbps)"    
        "F5 Advanced WAF (PAYG, 200Mbps)"    
        "F5 BIG-IP VE – ALL (BYOL, 2 Boot Locations)"    
 

## Instructions

### Step 1 - Deploying the infrastructure
To successfully deploy the infrastructure you will need to fill in at least the following information:
1) Resource Group name (The RG name cannot already exist on your Azure)
2) DNS Zone name (you should have already created this DNS Zone under f5demo_dns Resource Group name
3) Select the license type you require (PAYG 25Mbps, BYOL, etc)
4) Service principal details

### Step 2 - Configuring F5 appliances with DO
Once the infrastructure is deployed, the Declerative Onboarding step will appear. 
Select only the modules you want to proviion and if you selected BYOL then you will be required to provide licenses for the F5 devices.

Important Note: For API High Availability you will need to press the "Configure CFE" button. Before you press the button you will need to go to Azure portal, select the resource group you have just created, go to Access Control and add role assignment (Contributor) for the 2 F5 VMs that we have just created. This will allow the F5 VMs to communicate with Azure API.

### Step 3 - Publishing applicaiton workloads with AS3
To  publish a workload  fill in the following information:
1) Application Name
2) Select the backend Services and the ports
3) Choose if you require Persistence
4) Select which functionalities to enable. (WAF, BOT and DDoS are not enabled yet)

### Step 4 (FUTURE) - Demo all key functionalites of F5
This step is yet to be developed

---


