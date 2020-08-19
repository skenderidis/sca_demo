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
 


---


