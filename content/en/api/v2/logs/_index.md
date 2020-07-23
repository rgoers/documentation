---
title: Logs
description: |-
  Search your logs in the Datadog platform over HTTP.

  [See API version 1](/api/v1/logs/) for sending logs.
actions:
  AggregateLogs:
    description: >-
      The public API endpoint to aggregate events into buckets and compute
      metrics and timeseries.
    summary: Aggregate events
    responses:
      '200':
        description: OK
        schema_description: The response object for the logs aggregate API endpoint
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Not Authorized
        schema_description: API error response.
    request_description: ''
    request_schema_description: >-
      The object sent with the request to retrieve a list of logs from your
      organization.
  ListLogsGet:
    description: >-
      List endpoint returns logs that match a log search query.

      [Results are paginated][1].


      Both this endpoint and the POST endpoint can be used interchangeably when
      listing

      logs.


      **If you are considering archiving logs for your organization,

      consider use of the Datadog archive capabilities instead of the log list
      API.

      See [Datadog Logs Archive documentation][2].**


      [1]: /logs/guide/collect-multiple-logs-with-pagination

      [2]: https://docs.datadoghq.com/logs/archives
    summary: Get a quick list of logs
    responses:
      '200':
        description: OK
        schema_description: >-
          Response object with all logs matching the request and pagination
          information.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Not Authorized
        schema_description: API error response.
  ListLogs:
    description: >-
      List endpoint returns logs that match a log search query.

      [Results are paginated][1].


      Both this endpoint and the GET endpoint can be used interchangeably when
      listing

      logs.


      **If you are considering archiving logs for your organization,

      consider use of the Datadog archive capabilities instead of the log list
      API.

      See [Datadog Logs Archive documentation][2].**


      [1]: /logs/guide/collect-multiple-logs-with-pagination

      [2]: https://docs.datadoghq.com/logs/archives
    summary: Get a list of logs
    responses:
      '200':
        description: OK
        schema_description: >-
          Response object with all logs matching the request and pagination
          information.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Not Authorized
        schema_description: API error response.
    request_description: ''
    request_schema_description: The request for a logs list.
---
