# Getting Started with the AI Reference Implementation

Welcome to the AI Reference Implementation! This guide will walk you through the steps to get started with deploying an AI environment on Azure using Terraform. By following these instructions, you can quickly set up a secure, scalable, and compliant AI platform tailored to your specific needs.

***

## Step 1: Assess Your AI Scenario

Before you begin, it’s essential to understand the specific AI scenario you’re working on. The AI Reference Implementation supports a variety of use cases, such as Retrieval-Augmented Generation (RAG), Speech-to-Text call summarization, and more. Each scenario may require different configurations and resources.

1. **Identify Your Scenario:** Determine the AI scenario you want to implement. This will guide the selection of modules and configuration options.
2. **Explore Examples:** Check the `examples/` folder in this repository for pre-configured examples that match your scenario. These examples provide a starting point and demonstrate how to configure the AI Reference Implementation for specific use cases.

* * *

## Step 2: Set Up Prerequisites

To use the AI Reference Implementation, you'll need to set up your development environment with the required tools and dependencies.

1. **Install Required Tools:** Ensure you have the necessary tools, such as Terraform and Azure CLI, installed on your local machine. Detailed instructions for setting up your environment can be found in the Environment Setup document.
    
2. **Authenticate with Azure:** Follow the instructions in the Environment Setup guide to authenticate with Azure and ensure Terraform can manage your resources.
    

* * *

## Step 3: Create a Terraform Project

Now that you have your prerequisites in place, it’s time to create a Terraform project that references the AI Reference Implementation module.

1. **Create a New Directory:** Start by creating a new directory for your Terraform project.
    
    ```bash
    mkdir my-ai-project
    cd my-ai-project
    ```
    
2. **Initialize a Terraform Configuration File:** Create a `main.tf` file in your project directory and reference the AI Reference Implementation module.
    
    ```hcl
    module "ai_reference_implementation" {
      source  = "Azure/avm-ptn-ai-reference-implementation/azurerm"
      version = "x.x.x"
    
      # Required Variables
      resource_group_name  = "<your_resource_group>"
      location             = "<your_location>"
      
      # Scenario-specific Variables
      
    }
    ```
    
3. **Configure Variables:** Modify the variables in your `main.tf` file to match your specific scenario. You can find detailed information about each variable in the module's documentation.
    

* * *

## Step 4: Deploy the Terraform Configuration

With your Terraform project set up, you can now deploy the AI Reference Implementation on Azure.

1. **Initialize Terraform:** Run the following command to initialize your Terraform project. This will download the necessary modules and set up your environment.
    
    ```bash
    terraform init
    ```
    
2. **Plan the Deployment:** Generate an execution plan to see what resources Terraform will create or modify.
    
    ```bash
    terraform plan
    ```
    
3. **Apply the Configuration:** Apply the Terraform configuration to deploy your AI Reference Implementation on Azure.
    
    ```bash
    terraform apply
    ```
    
4. **Confirm the Deployment:** Review the changes Terraform plans to make and type `yes` to confirm the deployment.
    

* * *

## Step 5: Explore Example Use Cases

After deploying the AI Reference Implementation, you can explore the example use cases provided in the `examples/` folder. These examples demonstrate how to configure and extend the AI platform for different scenarios. You can use these as a reference to further customize your deployment or as templates for new projects.

* * *

## Next Steps

Once your AI environment is up and running, you can start building and deploying AI models, integrating additional Azure services, or configuring advanced security and observability features. For more detailed guidance, check out the other documentation files in the `docs/` folder.

Happy building!