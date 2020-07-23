---
title: Metrics
description: |-
  The metrics endpoint allows you to:

  - Post metrics data so it can be graphed on Datadog’s dashboards
  - Query metrics from any time period

  **Note**: A graph can only contain a set number of points
  and as the timeframe over which a metric is viewed increases,
  aggregation between points occurs to stay below that set number.

  Datadog has a soft limit of 100 timeseries per host
  where a timeseries is defined as a unique combination of metric name and tag.
actions:
  ListActiveMetrics:
    description: Get the list of actively reporting metrics from a given time until now.
    summary: Get active metrics list
    responses:
      '200':
        description: OK
        schema_description: Object listing all metric names stored by Datadog since a given time.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  GetMetricMetadata:
    description: Get metadata about a specific metric.
    summary: Get metric metadata
    responses:
      '200':
        description: OK
        schema_description: Object with all metric related metadata.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  UpdateMetricMetadata:
    description: >-
      Edit metadata of a specific metric. Find out more about [supported
      types](https://docs.datadoghq.com/developers/metrics).
    summary: Edit metric metadata
    responses:
      '200':
        description: OK
        schema_description: Object with all metric related metadata.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
    request_description: New metadata.
    request_schema_description: Object with all metric related metadata.
  QueryMetrics:
    description: Query timeseries points.
    summary: Query timeseries points
    responses:
      '200':
        description: OK
        schema_description: >-
          Response Object that includes your query and the list of metrics
          retrieved.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  ListMetrics:
    description: Search for metrics from the last 24 hours in Datadog.
    summary: Search metrics
    responses:
      '200':
        description: OK
        schema_description: Object containing the list of metrics matching the search query.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  SubmitMetrics:
    description: >-
      The metrics end-point allows you to post time-series data that can be
      graphed on Datadog’s dashboards.

      The limit for compressed payloads is 3.2 megabytes (3200000), and 62
      megabytes (62914560) for decompressed payloads.


      If you’re submitting metrics directly to the Datadog API without using
      DogStatsD, expect


      - 64 bits for the timestamp

      - 64 bits for the value

      - 20 bytes for the metric names

      - 50 bytes for the timeseries

      - The full payload is approximately ~ 100 bytes. However, with the
      DogStatsD API,

      compression is applied, which reduces the payload size.
    summary: Submit metrics
    responses:
      '202':
        description: Payload accepted
        schema_description: The payload accepted for intake.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '408':
        description: Request timeout
        schema_description: Error response object.
      '413':
        description: Payload too large
        schema_description: Error response object.
    request_description: ''
    request_schema_description: The metrics' payload.
---
