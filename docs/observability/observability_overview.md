# Observability Overview

## Introduction

Observability is a crucial aspect of engineering that enables you to understand the internal state of your system based on the data it generates. In the context of the AI Reference Implementation (AIRI), observability is not just about collecting logs and metrics—it's about ensuring that these insights are actionable and that they enable you to maintain the health, performance, and security of your AI environment on Azure.

This document provides an overview of the observability practices integrated into AIRI, detailing the tools, techniques, and key performance indicators (KPIs) that are monitored by default. As with other aspects of AIRI, the goal is to establish a robust, minimal baseline that can be extended and customized to meet specific project needs.

For more detailed information on specific observability topics, refer to the related documents within this observability folder.

## Goals and Scope

The primary goal of AIRI’s observability is to demonstrate and implement good practices around:

- **Telemetry Collection:** Gathering metrics, logs, and traces from various components of the AI environment. (See [Telemetry Collection](./telemetry_collection.md) for more details.)
- **Querying:** Enabling efficient querying and analysis of the collected telemetry data. (Refer to [Querying Logs and Metrics](./querying.md) for detailed instructions.)
- **Visualization:** Providing meaningful visualizations that help you monitor and understand the state of your AI environment. (Learn more in the [Visualization](./visualization.md) document.)
- **Alerting:** While not included by default, AIRI provides guidance on how to set up alerts based on the telemetry collected. (See [Alerting](./alerting.md) for a guide on configuring alerts.)

**Note:** While this implementation includes comprehensive telemetry and visualization capabilities, it purposely excludes alerts by default. However, implementing alerts should be straightforward given the observability foundation provided.

## Tools and Technology

AIRI uses a set of prescriptive tools and technologies to ensure a consistent and reliable observability framework. These tools serve as the foundation for monitoring AI workloads and infrastructure on Azure, allowing you to extend and adapt them as needed for your specific use cases.

### Key Tools

- **Azure Monitor:** Centralized service for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments.
- **Log Analytics:** Provides a powerful query language and tools for querying and analyzing log data.
- **Application Insights:** Used for monitoring live applications, automatically detecting performance anomalies, and including powerful analytics tools to help diagnose issues.
- **Azure Workbooks:** Used for creating rich, interactive reports and dashboards, visualizing data from multiple sources within Azure.

## Key Performance Indicators (KPIs)

AIRI is pre-configured to monitor a set of baseline KPIs that provide insights into both the infrastructure and AI-specific components. These KPIs are intended to serve as a starting point, illustrating the types of observability data that can be extracted from the system.

### Infrastructure KPIs

- **Resource Metrics:** Each Azure resource deployed by AIRI (such as virtual networks, storage accounts, and key vaults) will collect relevant metrics and logs. Examples include CPU utilization, disk I/O, and network throughput.
- **Diagnostic Logs:** Logs related to the health and performance of the infrastructure components, collected via Azure Diagnostic Settings.

### AI-Specific KPIs

#### Metrics

- **Workspaces:** Monitoring the health and performance of Azure Machine Learning Workspaces, including compute usage and experiment tracking.
- **Online Endpoints:** Metrics related to online endpoints for deploying machine learning models, including request latency and throughput.
- **Online Endpoint Deployments:** Monitoring deployments made to online endpoints, tracking deployment status and resource utilization.

#### Logs

- **Registries:** Logging activities related to Azure Container Registries, including image pulls and pushes.
- **Workspaces:** Detailed logging of activities within AI Workspaces, such as model training, experiment tracking, and resource allocation.
- **Workspaces/Online Endpoints:** Logs capturing the interactions and performance of online endpoints within the AI Workspaces.

## Architecture

The observability architecture within AIRI is designed to ensure that all components are covered by telemetry collection and monitoring tools. Below is an overview of the architecture components relevant to observability.

### Telemetry Collection

While AIRI provides the infrastructure for a fully observable solution, it is important to note that the collection of application-specific telemetry (such as custom metrics and traces from AI models) requires additional instrumentation within the application code. However, AIRI ensures that all infrastructure-level telemetry is automatically collected.

For more details on how telemetry is collected and what is included, see the [Telemetry Collection](./telemetry_collection.md) document.

#### Diagnostic Settings

AIRI configures Diagnostic Settings for all deployed resources by default. These settings dictate which metrics and logs are collected for each resource type, as outlined in the [Supported Metrics with Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/metrics-index) documentation.

- **Metrics Collection:** Includes metrics like CPU usage, memory consumption, disk I/O, and network activity.
- **Log Collection:** Captures diagnostic logs, activity logs, and audit logs from Azure resources.

#### Other Telemetry Collected

While AIRI does not include code-level instrumentation by default, it provides an Application Insights resource, allowing developers to add custom telemetry for their applications.

### Visualization

AIRI includes default visualizations provided via Azure Workbooks. These workbooks surface the identified KPIs and offer interactive dashboards that can be used to monitor the health and performance of the AI environment.

- **Default Dashboards:** Pre-configured workbooks for infrastructure metrics, AI workload performance, and resource utilization.
- **Customizable Views:** Users can modify or extend these workbooks to include additional metrics, logs, and data sources relevant to their specific use cases.

For more information on how to customize and use these visualizations, refer to the [Visualization](./visualization.md) document.

### Alerting

Although AIRI does not include alerts by default, you can easily configure alerts based on the telemetry collected. These alerts can notify you of potential issues, such as exceeding performance thresholds or encountering specific errors.

For guidance on setting up alerts, see the [Alerting](./alerting.md) document.

## Cost and Scale Considerations

While AIRI demonstrates how to implement observability effectively, it does not specifically focus on cost reduction or high-scale scenarios. However, to manage costs and avoid excessive data retention, Azure Monitor is configured with a default retention period, and sampling strategies can be implemented for telemetry capture.

## Best Practices

To make the most of the observability framework provided by AIRI, consider the following best practices:

- **Extend and Customize Telemetry:** While AIRI provides a robust baseline, you should extend the telemetry to capture application-specific metrics and logs.
- **Regularly Review Dashboards:** Continuously monitor the provided dashboards to ensure they align with your operational goals and modify them as your environment evolves.
- **Manage Costs:** Be mindful of the data retention and sampling settings in Azure Monitor to prevent runaway costs, especially in large-scale deployments.
- **Implement Alerts:** Use the guidance provided in the [Alerting](./alerting.md) document to set up alerts that notify you of critical events in your AI environment.

## Conclusion

Observability is a fundamental aspect of maintaining a healthy and performant AI environment. The AI Reference Implementation offers a solid foundation for observability, including comprehensive telemetry collection and insightful visualizations. By following the best practices outlined in this document and leveraging the tools provided, you can ensure that your AI environment is well-monitored, efficient, and resilient.

For more detailed information on specific observability components, please refer to the related documents within this observability folder:
- [Telemetry Collection](./telemetry_collection.md)
- [Querying Logs and Metrics](./querying.md)
- [Visualization](./visualization.md)
- [Alerting](./alerting.md)