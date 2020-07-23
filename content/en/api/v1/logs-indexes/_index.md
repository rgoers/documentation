---
title: Logs Indexes
description: >-
  Manage configuration of [log
  indexes](https://docs.datadoghq.com/logs/indexes/).

  You need an API and application key with Admin rights to interact with this
  endpoint.
actions:
  GetLogsIndexOrder:
    description: >-
      Get the current order of your log indexes. This endpoint takes no JSON
      arguments.
    summary: Get indexes order
    responses:
      '200':
        description: OK
        schema_description: Object containing the ordered list of log index names.
      '403':
        description: Forbidden
        schema_description: Error response object.
  UpdateLogsIndexOrder:
    description: >-
      This endpoint updates the index order of your organization.

      It returns the index order object passed in the request body when the
      request is successful.
    summary: Update indexes order
    responses:
      '200':
        description: OK
        schema_description: Object containing the ordered list of log index names.
      '400':
        description: Bad Request
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Object containing the new ordered list of index names
    request_schema_description: Object containing the ordered list of log index names.
  ListLogIndexes:
    description: >-
      The Index object describes the configuration of a log index.

      This endpoint returns an array of the `LogIndex` objects of your
      organization.
    summary: Get all indexes
    responses:
      '200':
        description: OK
        schema_description: Object with all Index configurations for a given organization.
      '403':
        description: Forbidden
        schema_description: Error response object.
  GetLogsIndex:
    description: >-
      Get one log index from your organization. This endpoint takes no JSON
      arguments.
    summary: Get an index
    responses:
      '200':
        description: OK
        schema_description: Object describing a Datadog Log index.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Response returned by the Logs API when errors occur.
  UpdateLogsIndex:
    description: >-
      Update an index as identified by its name.

      Returns the Index object passed in the request body when the request is
      successful.


      Using the `PUT` method updates your index’s configuration by **replacing**

      your current configuration with the new one sent to your Datadog
      organization.
    summary: Update an index
    responses:
      '200':
        description: OK
        schema_description: Object describing a Datadog Log index.
      '400':
        description: Invalid Parameter Error
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '429':
        description: Too Many Requests
        schema_description: Response returned by the Logs API when errors occur.
    request_description: Object containing the new `LogsIndex`.
    request_schema_description: Object describing a Datadog Log index.
---
