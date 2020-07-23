---
title: Logs
description: >-
  Send your logs to your Datadog platform over HTTP. Limits per HTTP request
  are:


  - Maximum content size per payload: 5MB

  - Maximum size for a single log: 256kB

  - Maximum array size if sending multiple logs in an array: 500 entries


  Any log exceeding 256KB is accepted and truncated by Datadog:

  - For a single log request, the API truncates the log at 256KB and returns a
  2xx.

  - For a multi-logs request, the API processes all logs, truncates only logs
  larger than 256KB, and returns a 2xx.


  We encourage you to send your logs compressed.

  Add the `Content-Encoding: gzip` header to the request when sending compressed
  logs.
actions:
  ListLogs:
    description: >-
      List endpoint returns logs that match a log search query.

      [Results are paginated][1].


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
        schema_description: Response returned by the Logs API when errors occur.
      '403':
        description: Authentication error
        schema_description: Error response object.
    request_description: Logs filter
    request_schema_description: >-
      Object to send with the request to retrieve a list of logs from your
      Organization.
  SubmitLog:
    description: >-
      Send your logs to your Datadog platform over HTTP. Limits per HTTP request
      are as follows.

      - Maximum content size per payload is 5MB.

      - Maximum size for a single log is 256kB.

      - Maximum array size if sending multiple logs in an array is 500 entries.


      Any log exceeding 256KB is accepted and truncated by server

      - For a single log request, the API truncates the log at 256KB and returns
      a 2xx.

      - For a multi-logs request, the API processes all logs,

      truncates only logs larger than 256KB, and returns a 2xx.


      We encourage you to send your logs compressed.

      Add the `Content-Encoding: gzip` header to the request when sending
      compressed logs.
    summary: Send logs
    responses:
      '200':
        description: Response from server (always 200 empty JSON).
      default:
        description: unexpected error
        schema_description: Invalid query performed.
    request_description: Log to send (JSON format).
    request_schema_description: Structured log message.
---
