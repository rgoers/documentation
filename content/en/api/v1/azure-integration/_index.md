---
title: Azure Integration
description: >-
  Configure your Datadog-Azure integration directly through the Datadog API.

  For more information, see the [Datadog-Azure integration
  page](https://docs.datadoghq.com/integrations/azure).
actions:
  DeleteAzureIntegration:
    description: Delete a given Datadog-Azure integration from your Datadog account.
    summary: Delete an Azure integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Delete a given Datadog-Azure integration request body.
    request_schema_description: Datadog-Azure integrations configured for your organization.
  ListAzureIntegration:
    description: List all Datadog-Azure integrations configured in your Datadog account.
    summary: List all Azure integrations
    responses:
      '200':
        description: OK
        schema_description: Accounts configured for your organization.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
  CreateAzureIntegration:
    description: >-
      Create a Datadog-Azure integration.


      Using the `POST` method updates your integration configuration by adding
      your new

      configuration to the existing one in your Datadog organization.


      Using the `PUT` method updates your integration configuration by replacing
      your

      current configuration with the new one sent to your Datadog organization.
    summary: Create an Azure integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Create a Datadog-Azure integration for your Datadog account request body.
    request_schema_description: Datadog-Azure integrations configured for your organization.
  UpdateAzureIntegration:
    description: >-
      Update a Datadog-Azure integration. Requires an existing `tenant_name` and
      `client_id`.

      Any other fields supplied will overwrite existing values. To overwrite
      `tenant_name` or `client_id`,

      use `new_tenant_name` and `new_client_id`. To leave a field unchanged, do
      not supply that field in the payload.
    summary: Update an Azure integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Update a Datadog-Azure integration request body.
    request_schema_description: Datadog-Azure integrations configured for your organization.
  UpdateAzureHostFilters:
    description: >-
      Update the defined list of host filters for a given Datadog-Azure
      integration.
    summary: Update Azure integration host filters
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Update a Datadog-Azure integration's host filters request body.
    request_schema_description: Datadog-Azure integrations configured for your organization.
---
