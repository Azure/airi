# Troubleshooting Guide

This troubleshooting guide is designed to help you diagnose and resolve common issues that may arise when using the AI Reference Implementation with Terraform. If you encounter a problem, please review the sections below before seeking further assistance.

## Common Issues and Solutions

### 1. Incorrect Module Reference

**Issue:** Terraform fails to find the correct module or reports an error related to the module source.

**Solution:**

* Ensure that your `main.tf` file correctly references the AI Reference Implementation module. The source URL should point to the correct module, and the version should be specified correctly.
    
    Example reference:
    
    ```hcl
    module "ai_reference_implementation" {
      source  = "Azure/avm-ptn-ai-reference-implementation/azurerm"
      version = "x.x.x"
      ...
    }
    ```
    
* Verify that your internet connection is stable, as Terraform needs to download the module when initializing the project.
    

### 2. Incorrect Azure Account or Subscription

**Issue:** Terraform commands fail with errors related to Azure authentication or subscription, such as `InvalidSubscription` or `AuthenticationFailed`.

**Solution:**

* Ensure you are authenticated to the correct Azure account using the Azure CLI:
    
    ```bash
    az login
    ```
    
* Confirm that you have selected the correct Azure subscription:
    
    ```bash
    az account set --subscription "<your_subscription_id>"
    ```
    
* Verify the subscription ID is correctly referenced in your Terraform configuration if applicable.
    

### 3. Insufficient Permissions

**Issue:** Deployment fails with errors indicating insufficient permissions, such as `AuthorizationFailed`.

**Solution:**

* Verify that your Azure account has the necessary permissions to create and manage resources within the target subscription. Typically, you should have at least the "Contributor" role assigned at the subscription or resource group level.
    
* Check that your Terraform service principal (if using one) also has the required permissions.
    
* You can use the following command to check your role assignments:
    
    ```bash
    az role assignment list --assignee "<your_assignee>"
    ```
    

### 4. Incorrect Environment Setup

**Issue:** Terraform commands fail due to issues with the environment setup, such as missing tools or incompatible versions.

**Solution:**

* Ensure that Terraform and Azure CLI are correctly installed and are on compatible versions.
    
    Verify Terraform installation:
    
    ```bash
    terraform version
    ```
    
    Verify Azure CLI installation:
    
    ```bash
    az version
    ```
    
* Make sure your PATH is correctly set up to include Terraform and Azure CLI executables.
    
* Review the [Environment Setup](./environment_setup.md) guide to ensure all prerequisites are installed and configured correctly.
    

### 5. Incorrect Variable Configuration

**Issue:** Terraform plan or apply fails due to misconfigured or missing variables, leading to errors like `InvalidTemplateDeployment` or `MissingRequiredArgument`.

**Solution:**

* Double-check your `main.tf` file to ensure all required variables are correctly defined and populated with valid values. Refer to the module's documentation for details on required and optional variables.
    
* If you have a `terraform.tfvars` file, verify that it contains all necessary variables and that they are correctly referenced in your configuration.
    
* Run `terraform plan` to preview the deployment and identify any missing or misconfigured variables before applying changes.
    

### 6. Resource Conflicts or Quotas

**Issue:** Deployment fails due to conflicts with existing resources or exceeding Azure service quotas, such as `ResourceQuotaExceeded`.

**Solution:**

* Review your existing Azure resources to ensure there are no conflicts with the resources Terraform is trying to create. Common issues include duplicate resource names or overlapping IP address ranges in virtual networks.
    
* Check your Azure subscription’s resource quotas to ensure you have enough capacity to deploy the required resources. You can view and request quota increases in the Azure portal under the "Usage + quotas" section.
    

### 7. General Debugging Tips

**Issue:** Unclear error messages or unexpected behavior during Terraform operations.

**Solution:**

* **Enable Debug Logging:** You can increase Terraform's verbosity by setting the `TF_LOG` environment variable:
    
    ```bash
    export TF_LOG=DEBUG
    terraform plan
    ```
    
    This will provide more detailed output, which can help diagnose the issue.
    
* **Re-run Terraform Init:** If you suspect an issue with the module or provider plugins, try re-running the initialization process:
    
    ```bash
    terraform init -reconfigure
    ```
    
* **Check State Files:** Ensure that the Terraform state files (`terraform.tfstate`) are not corrupted. You can inspect the state file with:
    
    ```bash
    terraform show
    ```
    
* **Clean Up Resources:** If deployment fails partway through, you may need to clean up partially created resources before retrying. You can manually delete these resources via the Azure portal or use `terraform destroy` to roll back changes. If you delete resources manually, be sure to update your Terraform state file accordingly.
    

## Getting Additional Help

If you’ve tried the above solutions and are still encountering issues, please:

* Review the [Support](../SUPPORT.md) guide for how to file issues or request help.
* Search existing issues in the GitHub repository to see if your problem has already been addressed.