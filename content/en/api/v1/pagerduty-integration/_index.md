---
title: PagerDuty Integration
description: >-
  Configure your [Datadog-PagerDuty
  integration](https://docs.datadoghq.com/api/?lang=bash#integration-pagerduty)

  directly through the Datadog API.
actions:
  CreatePagerDutyIntegrationService:
    description: Create a new service object in the PagerDuty integration.
    summary: Create a new service object
    responses:
      '201':
        description: OK
        schema_description: PagerDuty service object name.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Create a new service object request body.
    request_schema_description: The PagerDuty service that is available for integration with Datadog.
  DeletePagerDutyIntegrationService:
    description: Delete a single service object in the Datadog-PagerDuty integration.
    summary: Delete a single service object
    responses:
      '200':
        description: OK
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
  GetPagerDutyIntegrationService:
    description: Get service name in the Datadog-PagerDuty integration.
    summary: Get a single service object
    responses:
      '200':
        description: OK
        schema_description: PagerDuty service object name.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
  UpdatePagerDutyIntegrationService:
    description: Update a single service object in the Datadog-PagerDuty integration.
    summary: Update a single service object
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
    request_description: Update an existing service object request body.
    request_schema_description: PagerDuty service object key.
---
