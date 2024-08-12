# References

This document provides a list of references that are useful for understanding and utilizing the AI Reference Implementation.

## Key Resources

### 1. Azure Verified Modules (AVM)

The AI Reference Implementation is built using Azure Verified Modules, which are pre-built Terraform modules that adhere to Azure's best practices. These modules simplify the deployment of Azure resources by providing secure, scalable, and compliant configurations.

* **Azure Verified Modules (AVM) Documentation:** [AVM Documentation](https://aka.ms/avm)

### 2. AI Reference Implementation Pattern Module

The core of the AI Reference Implementation is the pattern module, which provides the foundational components required to deploy a secure and scalable AI environment on Azure.

* **Pattern Module Repository:** [terraform-azurerm-avm-ptn-ai-reference-implementation](https://github.com/Azure/terraform-azurerm-avm-ptn-ai-reference-implementation)

### 3. AI Reference Implementation Resource Modules

The resource modules used in this reference implementation are specialized modules designed to deploy individual Azure resources. These modules follow Azure's well-architected framework and best practices.

* **Azure Machine Learning Workspace Module:** [terraform-azurerm-avm-res-machinelearningservices-workspace](https://github.com/Azure/terraform-azurerm-avm-res-machinelearningservices-workspace)

## Additional Reading

* **Terraform Documentation:** Terraform by HashiCorp
* **Azure Well-Architected Framework:** [Azure WAF Documentation](https://learn.microsoft.com/en-us/azure/architecture/framework/)
* **Azure Documentation:** [Microsoft Azure Documentation](https://docs.microsoft.com/en-us/azure/)
