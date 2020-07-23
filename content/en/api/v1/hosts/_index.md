---
title: Hosts
description: Get information about your live hosts in Datadog.
actions:
  MuteHost:
    description: Mute a host.
    summary: Mute a host
    responses:
      '200':
        description: OK
        schema_description: Response with the list of muted host for your organization.
      '400':
        description: Invalid Parameter Error
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Mute a host request body.
    request_schema_description: Combination of settings to mute a host.
  UnmuteHost:
    description: Unmutes a host. This endpoint takes no JSON arguments.
    summary: Unmute a host
    responses:
      '200':
        description: OK
        schema_description: Response with the list of muted host for your organization.
      '400':
        description: Invalid Parameter Error
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  ListHosts:
    description: |-
      This endpoint allows searching for hosts by name, alias, or tag.
      Hosts live within the past 3 hours are included by default.
      Retention is 7 days.
      Results are paginated with a max of 1000 results at a time.
    summary: Get all hosts for your organization
    responses:
      '200':
        description: OK
        schema_description: Response with Host information from Datadog.
      '400':
        description: Invalid Parameter Error
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  GetHostTotals:
    description: >-
      This endpoint returns the total number of active and up hosts in your
      Datadog account.

      Active means the host has reported in the past hour, and up means it has
      reported in the past two hours.
    summary: Get the total number of active hosts
    responses:
      '200':
        description: OK
        schema_description: Total number of host currently monitored by Datadog.
      '400':
        description: Invalid Parameter Error
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
---
