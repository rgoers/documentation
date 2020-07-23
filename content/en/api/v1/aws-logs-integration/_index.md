---
title: AWS Logs Integration
description: >-
  Configure your Datadog-AWS-Logs integration directly through Datadog API.

  For more information, see the [AWS integration
  page](https://docs.datadoghq.com/api/?lang=bash#integration-aws-logs).
actions:
  DeleteAWSLambdaARN:
    description: >-
      Delete a Datadog-AWS logs configuration by removing the specific Lambda
      ARN associated with a given AWS account.
    summary: Delete an AWS Logs integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Delete AWS Lambda ARN request body.
    request_schema_description: AWS account ID and Lambda ARN.
  ListAWSLogsIntegrations:
    description: List all Datadog-AWS Logs integrations configured in your Datadog account.
    summary: List all AWS Logs integrations
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
  CreateAWSLambdaARN:
    description: >-
      Attach the Lambda ARN of the Lambda created for the Datadog-AWS log
      collection to your AWS account ID to enable log collection.
    summary: Add AWS Log Lambda ARN
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: AWS Log Lambda Async request body.
    request_schema_description: AWS account ID and Lambda ARN.
  CheckAWSLogsLambdaAsync:
    description: >-
      Test if permissions are present to add a log-forwarding triggers for the
      given services and AWS account. The input

      is the same as for Enable an AWS service log collection. Subsequent
      requests will always repeat the above, so this

      endpoint can be polled intermittently instead of blocking.


      - Returns a status of 'created' when it's checking if the Lambda exists in
      the account.

      - Returns a status of 'waiting' while checking.

      - Returns a status of 'checked and ok' if the Lambda exists.

      - Returns a status of 'error' if the Lambda does not exist.
    summary: Check that an AWS Lambda Function exists
    responses:
      '200':
        description: OK
        schema_description: >-
          A list of all Datadog-AWS logs integrations available in your Datadog
          organization.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Check AWS Log Lambda Async request body.
    request_schema_description: AWS account ID and Lambda ARN.
  ListAWSLogsServices:
    description: >-
      Get the list of current AWS services that Datadog offers automatic log
      collection. Use returned service IDs with the services parameter for the
      Enable an AWS service log collection API endpoint.
    summary: Get list of AWS log ready services
    responses:
      '200':
        description: OK
      '403':
        description: Authentication Error
        schema_description: Error response object.
  EnableAWSLogServices:
    description: >-
      Enable automatic log collection for a list of services. This should be run
      after running `CreateAWSLambdaARN` to save the configuration.
    summary: Enable an AWS Logs integration
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Enable AWS Log Services request body.
    request_schema_description: >-
      A list of current AWS services for which Datadog offers automatic log
      collection.
  CheckAWSLogsServicesAsync:
    description: >-
      Test if permissions are present to add log-forwarding triggers for the

      given services and AWS account. Input is the same as for
      `EnableAWSLogServices`.

      Done async, so can be repeatedly polled in a non-blocking fashion until

      the async request completes.


      - Returns a status of `created` when it's checking if the permissions
      exists
        in the AWS account.
      - Returns a status of `waiting` while checking.

      - Returns a status of `checked and ok` if the Lambda exists.

      - Returns a status of `error` if the Lambda does not exist.
    summary: Check permissions for log services
    responses:
      '200':
        description: OK
        schema_description: >-
          A list of all Datadog-AWS logs integrations available in your Datadog
          organization.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Check AWS Logs Async Services request body.
    request_schema_description: >-
      A list of current AWS services for which Datadog offers automatic log
      collection.
---
