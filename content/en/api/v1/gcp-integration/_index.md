---
title: GCP Integration
description: >-
  Configure your Datadog-Google Cloud Platform (GCP) integration directly

  through the Datadog API. Read more about the [Datadog-Google Cloud Platform
  integration](https://docs.datadoghq.com/integrations/google_cloud_platform).
actions:
  DeleteGCPIntegration:
    description: Delete a given Datadog-GCP integration.
    summary: Delete a GCP integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Delete a given Datadog-GCP integration.
    request_schema_description: Your Google Cloud Platform Account.
  ListGCPIntegration:
    description: List all Datadog-GCP integrations configured in your Datadog account.
    summary: List all GCP integrations
    responses:
      '200':
        description: OK
        schema_description: Array of GCP account responses.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
  CreateGCPIntegration:
    description: Create a Datadog-GCP integration.
    summary: Create a GCP integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Create a Datadog-GCP integration.
    request_schema_description: Your Google Cloud Platform Account.
  UpdateGCPIntegration:
    description: >-
      Update a Datadog-GCP integrations host_filters and/or auto-mute.

      Requires a `project_id` and `client_email`, however these fields cannot be
      updated.

      If you need to update these fields, delete and use the create (`POST`)
      endpoint.

      The unspecified fields will keep their original values.
    summary: Update a GCP integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Update a Datadog-GCP integration.
    request_schema_description: Your Google Cloud Platform Account.
---
