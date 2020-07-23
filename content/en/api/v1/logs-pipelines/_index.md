---
title: Logs Pipelines
description: >-
  Pipelines and processors operate on incoming logs, parsing

  and transforming them into structured attributes for easier querying.


  - See the [pipelines configuration
  page](https://app.datadoghq.com/logs/pipelines)
    for a list of the pipelines and processors currently configured in our UI.

  - Additional API-related information about processors can be found in the
    [processors documentation](https://docs.datadoghq.com/logs/processing/processors/?tab=api#lookup-processor).

  - For more information about Pipelines, see the
    [pipeline documentation](https://docs.datadoghq.com/logs/processing).

  **Note:** These endpoints are only available for admin users.

  Make sure to use an application key created by an admin.
actions:
  GetLogsPipelineOrder:
    description: |-
      Get the current order of your pipelines.
      This endpoint takes no JSON arguments.
    summary: Get pipeline order
    responses:
      '200':
        description: OK
        schema_description: Object containing the ordered list of pipeline IDs.
      '403':
        description: Forbidden
        schema_description: Error response object.
  UpdateLogsPipelineOrder:
    description: >-
      Update the order of your pipelines. Since logs are processed sequentially,
      reordering a pipeline may change

      the structure and content of the data processed by other pipelines and
      their processors.


      **Note**: Using the `PUT` method updates your pipeline order by replacing
      your current order

      with the new one sent to your Datadog organization.
    summary: Update pipeline order
    responses:
      '200':
        description: OK
        schema_description: Object containing the ordered list of pipeline IDs.
      '400':
        description: Bad Request
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '422':
        description: Unprocessable Entity
        schema_description: Response returned by the Logs API when errors occur.
    request_description: Object containing the new ordered list of pipeline IDs.
    request_schema_description: Object containing the ordered list of pipeline IDs.
  ListLogsPipelines:
    description: |-
      Get all pipelines from your organization.
      This endpoint takes no JSON arguments.
    summary: Get all pipelines
    responses:
      '200':
        description: OK
        schema_description: Array of pipeline ID strings.
      '403':
        description: Forbidden
        schema_description: Error response object.
  CreateLogsPipeline:
    description: Create a pipeline in your organization.
    summary: Create a pipeline
    responses:
      '200':
        description: OK
        schema_description: >-
          Pipelines and processors operate on incoming logs,

          parsing and transforming them into structured attributes for easier
          querying.


          **Note**: These endpoints are only available for admin users.

          Make sure to use an application key created by an admin.
      '400':
        description: Bad Request
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Definition of the new pipeline.
    request_schema_description: >-
      Pipelines and processors operate on incoming logs,

      parsing and transforming them into structured attributes for easier
      querying.


      **Note**: These endpoints are only available for admin users.

      Make sure to use an application key created by an admin.
  DeleteLogsPipeline:
    description: |-
      Delete a given pipeline from your organization.
      This endpoint takes no JSON arguments.
    summary: Delete a pipeline
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Forbidden
        schema_description: Error response object.
  GetLogsPipeline:
    description: |-
      Get a specific pipeline from your organization.
      This endpoint takes no JSON arguments.
    summary: Get a pipeline
    responses:
      '200':
        description: OK
        schema_description: >-
          Pipelines and processors operate on incoming logs,

          parsing and transforming them into structured attributes for easier
          querying.


          **Note**: These endpoints are only available for admin users.

          Make sure to use an application key created by an admin.
      '400':
        description: Bad Request
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Forbidden
        schema_description: Error response object.
  UpdateLogsPipeline:
    description: >-
      Update a given pipeline configuration to change it’s processors or their
      order.


      **Note**: Using this method updates your pipeline configuration by
      **replacing**

      your current configuration with the new one sent to your Datadog
      organization.
    summary: Update a pipeline
    responses:
      '200':
        description: OK
        schema_description: >-
          Pipelines and processors operate on incoming logs,

          parsing and transforming them into structured attributes for easier
          querying.


          **Note**: These endpoints are only available for admin users.

          Make sure to use an application key created by an admin.
      '400':
        description: Bad Request
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: New definition of the pipeline.
    request_schema_description: >-
      Pipelines and processors operate on incoming logs,

      parsing and transforming them into structured attributes for easier
      querying.


      **Note**: These endpoints are only available for admin users.

      Make sure to use an application key created by an admin.
---
