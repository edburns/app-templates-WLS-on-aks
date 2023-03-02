# Oracle WebLogic Server Cargo Tracker Application Deployed to Azure Kubernetes Service (AKS)

## Description

This is a sample app template of the Domain-Driven Design Jakarta EE application. The application is built with Maven and deployed to Oracle WebLogic Server running in Azure Kubernetes Service (AKS). The app template uses the [official Azure offer for running WLS on AKS](https://aka.ms/wls-aks-portal). For a quickstart on this offer, see [https://aka.ms/wls-aks-quickstart](https://aka.ms/wls-aks-quickstart). The application is exposed by Azure Application Gateway.

## Deploy Oracle WebLogic Server Application to Azure Kubernetes Service:

--
Tech stack:

- Azure Infra (VNet)
- Azure Storage Account
- Azure Container Registry
- Azure Kubernetes Service
- Azure Application Gateway
- Azure PostgreSQL DB
- GitHub Actions
- Bicep
- Docker
- Maven
- Java

---

## Introduction

This is a quickstart template. It deploys the following:

* Deploying Cargo Tracker App:
  * Create ProgresSQL Database
  * Create the Cargo Tracker - build with Maven
  * Provisioning Azure Infra Services with ARM templates - build with BICEP
    * Create an Azure Container Registry
    * Build your app, Oracle WebLogic Server and domain configuration models into an image
    * Push your app image to the container registry
    * Create an Azure Kubernetes Service  
    * Deploy your app to AKS
    * Create an Azure Application Gateway
    * Expose your app with the application gateway
  * Verify your app

* Cargo Tracker on Automated CI/CD with GitHub Action
  * CI/CD on GitHub Action
  * CI/CD in action with the app

> Refer to the [App Templates](https://github.com/microsoft/App-Templates) repo Readme for more samples that are compatible with [AzureAccelerators](https://github.com/Azure/azure-dev/).

## Prerequisites

- Local shell with Azure CLI installed or [Azure Cloud Shell](https://ms.portal.azure.com/#cloudshell/)
- Azure Subscription, on which you are able to create resources and assign permissions
  - View your subscription using ```az account show``` 
  - If you don't have an account, you can [create one for free](https://azure.microsoft.com/free). 
- You must have an Oracle account. To create an Oracle account and accept the license agreement for WebLogic Server images, follow the steps in [Oracle Container Registry](https://aka.ms/wls-aks-ocr). Make note of your Oracle Account password and email.
- GitHub CLI (optional, but strongly recommended). To install the GitHub CLI on your dev environment, see [Installation](https://cli.github.com/manual/installation).


## Getting Started

1. Fork the repository by clicking the 'Fork' button on the top right of the page.
This creates a local copy of the repository for you to work in. 

2. Configure GITHUB Actions:  Follow the instructions in the [GITHUB_ACTIONS_CONFIG.md file](.github/GITHUB_ACTIONS_CONFIG.md) (Located in the .github folder.)

4. Manually run the workflow

* Under your repository name, click Actions.
* In the left sidebar, click the workflow "Setup WLS on AKS".
* Above the list of workflow runs, select Run workflow.
* Configure the workflow.
  + Use the Branch dropdown to select the workflow's main branch.
  + For **Included in names to disambiguate. Get from another pipeline execution**, enter disambiguation prefix, e.g. `test01`.

5. Click Run workflow.

## Cargo Tracker Website

![Cargo Tracker Website](cargo_tracker_website.png)

If you wish to view the Cargo Tracker Deployment, you have the following options:

- Log into the Azure Portal
- Navigate to the `wlsd-aks-<your-disambiguate-prefix>-<number>` Resource Group
- Select **Settings**, **Deployments**, **wls-on-aks**, **Outputs**, you will see `clusterExternalUrl`. The application URL is `${clusterExternalUrl}cargo-tracker/`.
- Open your web browser, navigate to the application URL, you will see the Cargo Tracker landing page.

## Learn more about Cargo Tracker

See [Eclipse Cargo Tracker - Applied Domain-Driven Design Blueprints for Jakarta EE](cargo-tracker.md)
