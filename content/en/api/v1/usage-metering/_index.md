---
title: Usage Metering
description: >-
  The usage metering API allows you to get hourly, daily, and

  monthly usage across multiple facets of Datadog.

  This API is available to all Pro and Enterprise customers.

  Usage is only accessible for [parent-level
  organizations](https://docs.datadoghq.com/account_management/multi_organization/).


  **Note**: Usage data is delayed by up to 72 hours from when it was incurred.

  It is retained for the past 15 months.
actions:
  GetDailyCustomReports:
    description: Get daily custom reports.
    summary: Get the list of available daily custom reports
    responses:
      '200':
        description: OK
      '403':
        description: Forbidden - User is not authorized
  GetSpecifiedDailyCustomReports:
    description: Get specified daily custom reports.
    summary: Get specified daily custom reports
    responses:
      '200':
        description: OK
      '403':
        description: Forbidden - User is not authorized
      '404':
        description: Not Found
  GetMonthlyCustomReports:
    description: Get monthly custom reports.
    summary: Get the list of available monthly custom reports
    responses:
      '200':
        description: OK
      '403':
        description: Forbidden - User is not authorized
  GetSpecifiedMonthlyCustomReports:
    description: Get specified monthly custom reports.
    summary: Get specified monthly custom reports
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
      '404':
        description: Not Found
  GetUsageAnalyzedLogs:
    description: Get hourly usage for analyzed logs (Security Monitoring).
    summary: Get hourly usage for analyzed logs
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageLambda:
    description: Get hourly usage for lambda.
    summary: Get hourly usage for Lambda
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageBillableSummary:
    description: Get billable usage across your multi-org account.
    summary: Get billable usage across your multi-org account
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageFargate:
    description: >-
      Get hourly usage for
      [Fargate](https://docs.datadoghq.com/integrations/ecs_fargate/).
    summary: Get hourly usage for Fargate
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageHosts:
    description: Get hourly usage for hosts and containers.
    summary: Get hourly usage for hosts and containers
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageLogs:
    description: Get hourly usage for logs.
    summary: Get hourly usage for Logs
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageLogsByIndex:
    description: Get hourly usage for logs by index.
    summary: Get hourly usage for Logs by Index
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageNetworkFlows:
    description: Get hourly usage for network flows.
    summary: Get hourly usage for Network Flows
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageNetworkHosts:
    description: Get hourly usage for network hosts.
    summary: Get hourly usage for Network Hosts
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageRumSessions:
    description: >-
      Get hourly usage for
      [RUM](https://docs.datadoghq.com/real_user_monitoring/) Sessions.
    summary: Get hourly usage for RUM Sessions
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageSNMP:
    description: Get hourly usage for SNMP devices.
    summary: Get hourly usage for SNMP devices
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageSummary:
    description: Get usage across your multi-org account.
    summary: Get usage across your multi-org account
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageSynthetics:
    description: >-
      Get hourly usage for [Synthetics
      checks](https://docs.datadoghq.com/synthetics/).
    summary: Get hourly usage for Synthetics Checks
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageSyntheticsAPI:
    description: >-
      Get hourly usage for [synthetics API
      checks](https://docs.datadoghq.com/synthetics/).
    summary: Get hourly usage for Synthetics API Checks
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageSyntheticsBrowser:
    description: Get hourly usage for synthetics browser checks.
    summary: Get hourly usage for Synthetics Browser Checks
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageTimeseries:
    description: >-
      Get hourly usage for [custom
      metrics](https://docs.datadoghq.com/developers/metrics/custom_metrics/).
    summary: Get hourly usage for custom metrics
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageTopAvgMetrics:
    description: >-
      Get top [custom
      metrics](https://docs.datadoghq.com/developers/metrics/custom_metrics/) by
      hourly average.
    summary: Get top 500 custom metrics by hourly average
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
  GetUsageTrace:
    description: Get hourly usage for trace search.
    summary: Get hourly usage for Trace Search
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '403':
        description: Forbidden - User is not authorized
---
