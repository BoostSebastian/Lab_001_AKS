<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="">
    <img src="images/logopng2.png" alt="Logo" height="80">
  </a>

<h3 align="center">Telia Cygate</h3>

  <p align="center">
    A short and simple introduction to use AKS in Azure.
    <br />
    <br />
    <a href="https://github.com/BoostSebastian/Lab_001_AKS">View Demo</a>
    ·
    <a href="https://github.com/BoostSebastian/Lab_001_AKS/issues">Report Bug</a>
    ·
    <a href="https://github.com/BoostSebastian/Lab_001_AKS/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>About The Lab</li>
    <li>Getting Started<ul>
        <li>Prerequisites</li>
        <li>Installation</li>
      </ul>
    </li>
    <li>Set Up DevOps Project</li>

  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Lab

<br>
<img src="images/k8saks1-1.jpg" alt="Logo" height="200">
<br>
<br>

<a href="https://azure.microsoft.com/en-us/services/kubernetes-service/">Azure Kubernetes Service (AKS)</a> is the quickest way to use Kubernetes on Azure. Azure Kubernetes Service (AKS) manages your hosted Kubernetes environment, making it quick and easy to deploy and manage containerized applications without container orchestration expertise. It also eliminates the burden of ongoing operations and maintenance by provisioning, upgrading, and scaling resources on demand, without taking your applications offline. Azure DevOps helps in creating Docker images for faster deployments and reliability using the continuous build option.

One of the biggest advantage to use AKS is that instead of creating resources in cloud you can create resources and infrastructure inside Azure Kubernetes Cluster through Deployments and Services manifest files.



This lab uses a Dockerized ASP.NET Core web application - MyHealthClinic (MHC) and is deployed to a Kubernetes cluster running on Azure Kubernetes Service (AKS) using Azure DevOps.

    - There is a mhc-aks.yaml manifest file which consists of definitions to spin up Deployments and Services such as Load Balancer in the front and Redis Cache in the backend. 
    - The MHC application will be running in the mhc-front pod along with the Load Balancer.

The following image will walk you through all the steps explained in this lab

<br>
<img src="images/AKS-workflow.gif" alt="Logo" height="500">

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started



The following tasks will be performed:

- Create an Azure Container Registry (ACR), AKS and Azure SQL server
- Provision the Azure DevOps Team Project with a .NET Core application using the Azure DevOps Demo Generator tool.
- Configure application and database deployment, using Continuous Deployment (CD) in the Azure DevOps
- Initiate the build to automatically deploy the application


## Prerequisites



  - Microsoft Azure Account: You will need a `valid and active Azure account` for the Azure labs. If you do not have one, you can sign up for a free trial.
  - You will need an `Azure DevOps account`. If you do not have one, you can sign up for free <a href="https://azure.microsoft.com/en-us/services/devops/">here</a>.



<p align="right">(<a href="#readme-top">back to top</a>)</p>



##  Set Up Azure & DevOps

### DevOps
1. Follow this link <a href="http://azuredevopsdemogenerator.azurewebsites.net/?TemplateId=77372&Name=AKS">Azure DevOps Demo Generator </a>
2. Login if needed.
3. Fill in as shown below

<img src="images/createproject.png" alt="Logo" height="700">

4. Create Project
5. Wait for project to finish

<img src="images/wait.png" alt="Logo" height="100">

6. Navigate to project

<img src="images/done.png" alt="Logo" height="100">

### Azure

This is what we will deploy.

| **Azure resources**                                                                       | **Description**                                       |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| <img src="images/container_registry.png" alt="Logo" height="25"> Azure Container Registry | Used to store the Docker images privately             |
| <img src="images/aks.png" alt="Logo" height="25"> AKS                                     | Docker images are deployed to Pods running inside AKS |
| <img src="images/sqlserver.png" alt="Logo" height="25"> Azure SQL Server                  | SQL Server on Azure to host database                  |


1. Login to the Azure Portal: <a href="https://portal.azure.com">portal.azure.com</a>
2. Launch the Azure Cloud Shell from the Azure portal and choose Bash.
<br>
<img src="images/cloudshell.png" alt="Logo" height="50">
1. Deploy Kubernetes to Azure, using CLI