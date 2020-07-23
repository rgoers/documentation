---
title: AWS Integration
description: >-
  Configure your Datadog-AWS integration directly through the Datadog API.

  For more information, see the [AWS integration
  page](https://docs.datadoghq.com/integrations/amazon_web_services).
actions:
  DeleteAWSAccount:
    description: >-
      Delete a Datadog-AWS integration matching the specified `account_id` and
      `role_name parameters`.
    summary: Delete an AWS integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: AWS request object
    request_schema_description: Returns the AWS account associated with this integration.
  ListAWSAccounts:
    description: List all Datadog-AWS integrations available in your Datadog organization.
    summary: List all AWS integrations
    responses:
      '200':
        description: OK
        schema_description: List of enabled AWS accounts.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
  CreateAWSAccount:
    description: >-
      Create a Datadog-Amazon Web Services integration.

      Using the `POST` method updates your integration configuration

      by adding your new configuration to the existing one in your Datadog
      organization.
    summary: Create an AWS integration
    responses:
      '200':
        description: OK
        schema_description: The Response returned by the AWS Create Account call.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: AWS Request Object
    request_schema_description: Returns the AWS account associated with this integration.
  UpdateAWSAccount:
    description: Update a Datadog-Amazon Web Services integration.
    summary: Update an AWS integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: AWS request object
    request_schema_description: Returns the AWS account associated with this integration.
  ListAvailableAWSNamespaces:
    description: >-
      List all namespace rules for a given Datadog-AWS integration. This
      endpoint takes no arguments.
    summary: List namespace rules
    responses:
      '200':
        description: OK
      '403':
        description: Authentication Error
        schema_description: Error response object.
  CreateNewAWSExternalID:
    description: >-
      Generate a new AWS external ID for a given AWS account ID and role name
      pair.
    summary: Generate a new external ID
    responses:
      '200':
        description: OK
        schema_description: The Response returned by the AWS Create Account call.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: >-
      Your Datadog role delegation name.

      For more information about your AWS account Role name,

      see the [Datadog AWS integration configuration
      info](https://github.com/DataDog/documentation/blob/master/integrations/amazon_web_services/#installation).
    request_schema_description: Returns the AWS account associated with this integration.
---
