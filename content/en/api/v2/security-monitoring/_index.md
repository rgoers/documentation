---
title: Security Monitoring
description: Detection rules for generating signals and listing of generated signals
actions:
  ListSecurityMonitoringRules:
    description: List rules.
    summary: List rules
    responses:
      '200':
        description: OK
        schema_description: List of rules.
      '400':
        description: Bad Request
        schema_description: API error response.
  CreateSecurityMonitoringRule:
    description: Create a detection rule.
    summary: Create a detection rule
    responses:
      '200':
        description: OK
        schema_description: Detection rule.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Not Authorized
        schema_description: API error response.
    request_description: ''
    request_schema_description: Create a new rule.
  DeleteSecurityMonitoringRule:
    description: Delete an existing rule. Default rules cannot be deleted.
    summary: Delete an existing rule
    responses:
      '204':
        description: OK
      '403':
        description: Not Authorized
        schema_description: API error response.
      '404':
        description: Not Found
        schema_description: API error response.
  GetSecurityMonitoringRule:
    description: Get a rule's details.
    summary: Get a rule's details
    responses:
      '200':
        description: OK
        schema_description: Detection rule.
      '404':
        description: Not Found
        schema_description: API error response.
  UpdateSecurityMonitoringRule:
    description: >-
      Update an existing rule. When updating `cases`, `queries` or `options`,
      the whole field

      must be included. For example, when modifying a query all queries must be
      included.

      Default rules can only be updated to be enabled and to change
      notifications.
    summary: Update an existing rule
    responses:
      '200':
        description: OK
        schema_description: Detection rule.
      '400':
        description: Bad Request
        schema_description: API error response.
      '401':
        description: Concurrent Modification
        schema_description: API error response.
      '403':
        description: Not Authorized
        schema_description: API error response.
      '404':
        description: Not Found
        schema_description: API error response.
    request_description: ''
    request_schema_description: Update an existing rule.
  ListSecurityMonitoringSignals:
    description: >-
      The list endpoint returns security signals that match a search query.

      Both this endpoint and the POST endpoint can be used interchangeably when
      listing

      security signals.
    summary: Get a quick list of security signals
    responses:
      '200':
        description: OK
        schema_description: >-
          The response object with all security signals matching the request and
          pagination information.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Not Authorized
        schema_description: API error response.
  SearchSecurityMonitoringSignals:
    description: >-
      Returns security signals that match a search query.

      Both this endpoint and the GET endpoint can be used interchangeably for
      listing

      security signals.
    summary: Get a list of security signals
    responses:
      '200':
        description: OK
        schema_description: >-
          The response object with all security signals matching the request and
          pagination information.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Not Authorized
        schema_description: API error response.
    request_description: ''
    request_schema_description: The request for a security signal list.
---
