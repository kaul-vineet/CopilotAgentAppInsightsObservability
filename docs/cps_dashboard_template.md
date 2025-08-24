# CPS Dashboard JSON Template Documentation

This document provides a structured overview of the CPS Dashboard JSON Template, designed for generating and monitoring system performance and operational metrics in App Insights.

---

## Sections and Metrics Overview

### 1. CPS Performance Metrics
A comprehensive view of system performance by summarizing key timing and error data. This section serves as the foundation for analyzing the health and efficiency of the CPS.

#### Key Metrics:
- **Flow, Connector, and Gen AI Execution Times**: Captures execution times for various flows, connectors, and AI-driven components.
- **90th Percentile Response Time (ms)**: Measures response time at the 90th percentile to understand high-latency edge cases.
- **Avg Response Time (ms)**: Provides the average response time for all requests.
- **Total Requests**: Counts the total number of requests handled by the system.
- **Throughput**: Measures the number of requests processed per unit time.

---

### 2. Error Monitoring
Tracks and analyzes errors occurring in the system, aiding in troubleshooting and improving reliability.

#### Key Metrics:
- **Error Count**: Total number of errors encountered.
- **Error Rate**: Percentage of requests resulting in errors.
- **Bot Error Rate**: Tracks errors specific to bot-related requests.
- **Error Logs**: Detailed logs of errors for in-depth debugging.
- **Conversations with Errors**: Identifies conversations where errors occurred for targeted analysis.

---

### 3. Response Time Analysis
Focuses on the response time performance to identify trends and anomalies.

#### Key Metrics:
- **Response Time Frequency**: Distribution of response times, filterable by time range, e.g., between `datetime("2024-11-05T23:00:00.000Z")..datetime("2024-11-05T23:30:00.000Z")`.
- **Topics by Max Response Time**: Highlights topics with the longest response times to target optimizations.

---

### 4. Correlation and Conversation Insights
Maps relationships between conversation IDs and correlation IDs to trace user interactions and system processes.

#### Key Metrics:
- **Conversation ID by Correlation ID**: Links conversation identifiers to correlation IDs for traceability.
- **Correlation ID by Conversation ID**: Reverse mapping for identifying system interactions linked to user conversations.
- **Steps for Given Conversation ID**: Breaks down the steps executed within a specific conversation.

---

### 5. Health and Reliability Monitoring
Tracks the overall health of the CPS system and highlights potential issues.

#### Key Metrics:
- **HealthCheck**: Status checks to ensure all services and components are operational.

---

## Usage Instructions
The metrics above should be configured and visualized within the App Insights to monitor and analyze bot performance effectively. The structure and insights provided aim to assist in:

- Identifying bottlenecks in execution times.
- Monitoring and reducing error rates.
- Understanding conversation and correlation mappings for end-to-end traceability.
- Ensuring system health and readiness for operations.

## FAQ
1. How does Total Requests on dashboard is calculated?
   Total Requests is the total count of "BotMessageReceived" events in the logs. Each message received by the bot is counted as a request.
2. How does HealthCheck work?
   CPS health check evaluates the status by comparing the actual number of BotMessageReceived events to the expected number, calculated based on a defined interval (intervalMinutes) within a given time range. The time range is specified dynamically through {timerange}, and the health status is determined as "Healthy" or "Unhealthy" based on whether the actual requests meet or exceed the expected count.

## Import Template
To import the CPS Dashboard Template into App Insights, follow these steps:
1. Navigate to the App Insights on Azure portal portal and create an instance.
2. Click on the newly created application insights instance. -> Click on Monitoring -> Click on Workbooks.
3. Click on New -> Advanced Editior icon
4. Copy the template content from the `cps_dashboard_template.workbook` file to Gallery Template.
5. Click on Apply.

## Create Dashboard
1. Go to Dashboard Hub on Azure Portal
2. Click on Create a Dashboard
3. Go to the workbook created previously and click on Pin All
4. Select the dashboard created in (1). You will also have option to create new dashboard here
5. Now restructure the tiles on the dashboard as per your requirement