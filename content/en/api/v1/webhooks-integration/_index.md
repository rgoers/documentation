---
title: Webhooks Integration
description: |-
  Configure your Datadog-Webhooks integration directly through the Datadog API.
  For more information about the Datadog-Webhooks integration,
  see the [integration page](https://docs.datadoghq.com/integrations/webhooks).
actions:
  CreateWebhooksIntegrationCustomVariable:
    description: Creates an endpoint with the name `<CUSTOM_VARIABLE_NAME>`.
    summary: Create a custom variable
    responses:
      '201':
        description: OK
        schema_description: Custom variable for Webhook integration.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Define a custom variable request body.
    request_schema_description: Custom variable for Webhook integration.
  DeleteWebhooksIntegrationCustomVariable:
    description: Deletes the endpoint with the name `<CUSTOM_VARIABLE_NAME>`.
    summary: Delete a custom variable
    responses:
      '200':
        description: OK
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
  GetWebhooksIntegrationCustomVariable:
    description: >-
      Shows the content of the custom variable with the name
      `<CUSTOM_VARIABLE_NAME>`.


      If the custom variable is secret, returns `null` for the
      `<CUSTOM_VARIABLE_VALUE>`

      in the response payload.
    summary: Get a custom variable
    responses:
      '200':
        description: OK
        schema_description: Custom variable for Webhook integration.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
  UpdateWebhooksIntegrationCustomVariable:
    description: Updates the endpoint with the name `<CUSTOM_VARIABLE_NAME>`.
    summary: Update a custom variable
    responses:
      '200':
        description: OK
        schema_description: Custom variable for Webhook integration.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
    request_description: Update an existing custom variable request body.
    request_schema_description: |-
      Update request of a custom variable object.

      *All properties are optional.*
  CreateWebhooksIntegration:
    description: Creates an endpoint with the name `<WEBHOOK_NAME>`.
    summary: Create a webhooks integration
    responses:
      '201':
        description: OK
        schema_description: Datadog-Webhooks integration.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Create a webhooks integration request body.
    request_schema_description: Datadog-Webhooks integration.
  DeleteWebhooksIntegration:
    description: Deletes the endpoint with the name `<WEBHOOK NAME>`.
    summary: Delete a webhook
    responses:
      '200':
        description: OK
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
  GetWebhooksIntegration:
    description: Gets the content of the webhook with the name `<WEBHOOK_NAME>`.
    summary: Get a webhook integration
    responses:
      '200':
        description: OK
        schema_description: Datadog-Webhooks integration.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
  UpdateWebhooksIntegration:
    description: Updates the endpoint with the name `<WEBHOOK_NAME>`.
    summary: Update a webhook
    responses:
      '200':
        description: OK
        schema_description: Datadog-Webhooks integration.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
    request_description: Update an existing Datadog-Webhooks integration.
    request_schema_description: |-
      Update request of a Webhooks integration object.

      *All properties are optional.*
---
