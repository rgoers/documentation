---
title: Slack Integration
description: >-
  Configure your [Datadog-Slack
  integration](https://docs.datadoghq.com/integrations/slack)

  directly through Datadog API.
actions:
  DeleteSlackIntegration:
    description: Delete a Datadog-Slack integration.
    summary: Delete a Slack integration
    responses:
      '200':
        description: OK
      '403':
        description: Authentication error
        schema_description: Error response object.
  GetSlackIntegration:
    description: Get all information about your Datadog-Slack integration.
    summary: Get info about a Slack integration
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
  CreateSlackIntegration:
    description: >-
      Create a Datadog-Slack integration. Once created, add a channel to it with
      the

      [Add channels to Slack integration
      endpoint](https://docs.datadoghq.com/api/?lang=bash#add-channels-to-slack-integration).


      This method updates your integration configuration by **adding**

      your new configuration to the existing one in your Datadog organization.
    summary: Create a Slack integration
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Create Datadog-Slack integration request body.
    request_schema_description: A new Datadog-Slack integration.
  UpdateSlackIntegration:
    description: >-
      Add channels to your existing Datadog-Slack integration.


      This method updates your integration configuration by **replacing**

      your current configuration with the new one sent to your Datadog
      organization.
    summary: Add channels to Slack integration
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Update an existing Datadog-Slack integration request body.
    request_schema_description: Configuration of your Slack channels.
---
