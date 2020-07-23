---
title: Downtimes
description: >-
  [Downtiming](https://docs.datadoghq.com/monitors/downtimes) gives

  you greater control over monitor notifications by allowing you to globally
  exclude

  scopes from alerting. Downtime settings, which can be scheduled with start and

  end times, prevent all alerting related to specified Datadog tags.
actions:
  ListDowntimes:
    description: Get all scheduled downtimes.
    summary: Get all downtimes
    responses:
      '200':
        description: OK
      '403':
        description: Forbidden
        schema_description: Error response object.
  CreateDowntime:
    description: Schedule a downtime.
    summary: Schedule a downtime
    responses:
      '200':
        description: OK
        schema_description: |-
          Downtiming gives you greater control over monitor notifications by
          allowing you to globally exclude scopes from alerting.
          Downtime settings, which can be scheduled with start and end times,
          prevent all alerting related to specified Datadog tags.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Schedule a downtime request body.
    request_schema_description: |-
      Downtiming gives you greater control over monitor notifications by
      allowing you to globally exclude scopes from alerting.
      Downtime settings, which can be scheduled with start and end times,
      prevent all alerting related to specified Datadog tags.
  CancelDowntimesByScope:
    description: Delete all downtimes that match the scope of `X`.
    summary: Cancel downtimes by scope
    responses:
      '200':
        description: OK
        schema_description: Object containing array of IDs of canceled downtimes.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Downtimes not found
        schema_description: Error response object.
    request_description: Scope to cancel downtimes for.
    request_schema_description: Cancel downtimes according to scope.
  CancelDowntime:
    description: Cancel a downtime.
    summary: Cancel a downtime
    responses:
      '204':
        description: OK
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Downtime not found
        schema_description: Error response object.
  GetDowntime:
    description: Get downtime detail by `downtime_id`.
    summary: Get a downtime
    responses:
      '200':
        description: OK
        schema_description: |-
          Downtiming gives you greater control over monitor notifications by
          allowing you to globally exclude scopes from alerting.
          Downtime settings, which can be scheduled with start and end times,
          prevent all alerting related to specified Datadog tags.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Downtime not found
        schema_description: Error response object.
  UpdateDowntime:
    description: Update a single downtime by `downtime_id`.
    summary: Update a downtime
    responses:
      '200':
        description: OK
        schema_description: |-
          Downtiming gives you greater control over monitor notifications by
          allowing you to globally exclude scopes from alerting.
          Downtime settings, which can be scheduled with start and end times,
          prevent all alerting related to specified Datadog tags.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Downtime not found
        schema_description: Error response object.
    request_description: Update a downtime request body.
    request_schema_description: |-
      Downtiming gives you greater control over monitor notifications by
      allowing you to globally exclude scopes from alerting.
      Downtime settings, which can be scheduled with start and end times,
      prevent all alerting related to specified Datadog tags.
---
