# Environment Setup

## Overview

This document provides step-by-step instructions for setting up your development environment to work with the AI Reference Implementation. Before you can deploy the AI Reference Implementation on Azure using Terraform, you need to ensure that your system is properly configured with the necessary tools and dependencies.

## Prerequisites

Before proceeding with the setup, ensure you have the following:

1. **Operating System:** This guide assumes you are using a Unix-based system (e.g., macOS or Linux) or Windows with WSL (Windows Subsystem for Linux). Most commands should work similarly across environments, but you may need to adapt them for your specific OS.
    
2. **Azure Subscription:** You must have access to an Azure subscription where you can deploy the necessary resources. Ensure that you have appropriate permissions to create resources within this subscription.
    

## Step 1: Install Terraform

Terraform is the infrastructure as code tool that will be used to deploy and manage your Azure resources. Follow the instructions below to install Terraform on your system.

### macOS (using Homebrew)

```bash
brew install terraform
```

### Linux

1. Download the latest version of Terraform from the official Terraform website.
    
2. Unzip the downloaded package.
    
    ```bash
    unzip terraform_*.zip
    ```
    
3. Move the Terraform binary to a directory included in your system's PATH.
    
    ```bash
    sudo mv terraform /usr/local/bin/
    ```
    
4. Verify the installation by checking the Terraform version.
    
    ```bash
    terraform version
    ```
    

### Windows (using Chocolatey)

If you are using WSL, you can follow the Linux installation instructions above. For native Windows:

```powershell
choco install terraform
```

## Step 2: Install Azure CLI

The Azure CLI is required to interact with your Azure subscription and manage resources. Install it by following the appropriate instructions below.

### macOS (using Homebrew)

```bash
brew install azure-cli
```

### Linux

Follow the installation instructions provided in the [Azure CLI documentation](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).

### Windows (using MSI Installer)

Download and install the Azure CLI using the MSI installer from the [Azure CLI installation page](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli).

## Step 3: Authenticate with Azure

Once the Azure CLI is installed, you need to authenticate to your Azure subscription. This ensures that Terraform can interact with Azure to create and manage resources.

### Login to Azure

Use the following command to login to Azure:

```bash
az login
```

This command will open a web browser where you can sign in with your Azure account credentials. After successful login, your CLI session will be authenticated and ready to use.

### Set Default Subscription (Optional)

If you have access to multiple subscriptions, you may want to set a default subscription for your session:

```bash
az account set --subscription "<your_subscription_id>"
```

## Step 4: Install Additional Tools (Optional)

Depending on your specific use case and development environment, you may need to install additional tools. Below are some common tools that might be useful:

* **Visual Studio Code:** A powerful, lightweight code editor that integrates well with Terraform and Azure. Install from [Visual Studio Code](https://code.visualstudio.com/).
    
* **Terraform Linter (tflint):** Helps with identifying errors and best practices in your Terraform code. Install via Homebrew:
    
    ```bash
    brew install tflint
    ```
    
* **Git:** Version control system for managing your Terraform configurations. Install via Homebrew:
    
    ```bash
    brew install git
    ```
    

## Step 5: Verify Your Setup

To ensure everything is set up correctly, you can run the following commands to verify your environment:

1. **Check Terraform Installation:**
    
    ```bash
    terraform version
    ```
    
2. **Check Azure CLI Installation:**
    
    ```bash
    az version
    ```
    
3. **Verify Azure Authentication:**
    
    ```bash
    az account show
    ```
    
    This command should return details about your currently selected Azure subscription.
    

## Conclusion

Your environment should now be set up and ready to work with the AI Reference Implementation. If you encounter any issues during setup, consult the [troubleshooting guide](./troubleshooting.md) for help. You can now proceed to the [Getting Started](./getting_started.md) guide to begin deploying your AI environment on Azure.