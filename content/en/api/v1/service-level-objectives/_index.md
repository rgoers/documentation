---
title: Service Level Objectives
description: >-
  [Service Level
  Objectives](https://docs.datadoghq.com/monitors/service_level_objectives/#configuration)

  (or SLOs) are a key part of the site reliability engineering toolkit.

  SLOs provide a framework for defining clear targets around application
  performance,

  which ultimately help teams provide a consistent customer experience,

  balance feature development with platform stability,

  and improve communication with internal and external users.
actions:
  ListSLOs:
    description: Get multiple service level objective objects by their IDs.
    summary: Search SLOs
    responses:
      '200':
        description: OK
        schema_description: A response with one or more service level objective.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  CreateSLO:
    description: Create a service level objective object.
    summary: Create a SLO object
    responses:
      '200':
        description: OK
        schema_description: A response with one or more service level objective.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Service level objective request object.
    request_schema_description: >-
      A service level objective object includes a service level indicator,
      thresholds

      for one or more timeframes, and metadata (`name`, `description`, `tags`,
      etc.).
  DeleteSLOTimeframeInBulk:
    description: >-
      Delete (or partially delete) multiple service level objective objects.


      This endpoint facilitates deletion of one or more thresholds for one or
      more

      service level objective objects. If all thresholds are deleted, the
      service level

      objective object is deleted as well.
    summary: Bulk Delete SLO Timeframes
    responses:
      '200':
        description: OK
        schema_description: |-
          The bulk partial delete service level objective object endpoint
          response.

          This endpoint operates on multiple service level objective objects, so
          it may be partially successful. In such cases, the "data" and "error"
          fields in this response indicate which deletions succeeded and failed.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Delete multiple service level objective objects request body.
    request_schema_description: |-
      A map of service level objective object IDs to arrays of timeframes,
      which indicate the thresholds to delete for each ID.
  CheckCanDeleteSLO:
    description: |-
      Check if a SLO can be safely deleted. For example,
      assure an SLO can be deleted without disrupting a dashboard.
    summary: Check if SLOs can be safely deleted
    responses:
      '200':
        description: OK
        schema_description: A service level objective response containing the requested object.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '409':
        description: Conflict
        schema_description: A service level objective response containing the requested object.
  DeleteSLO:
    description: |-
      Permanently delete the specified service level objective object.

      If an SLO is used in a dashboard, the `DELETE /v1/slo/` endpoint returns
      a 409 conflict error because the SLO is referenced in a dashboard.
    summary: Delete a SLO
    responses:
      '200':
        description: OK
        schema_description: A response list of all service level objective deleted.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not found
        schema_description: Error response object.
      '409':
        description: Conflict
        schema_description: A response list of all service level objective deleted.
  GetSLO:
    description: Get a service level objective object.
    summary: Get a SLO's details
    responses:
      '200':
        description: OK
        schema_description: >-
          A service level objective response containing a single service level
          objective.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not found
        schema_description: Error response object.
  UpdateSLO:
    description: Update the specified service level objective object.
    summary: Update a SLO
    responses:
      '200':
        description: OK
        schema_description: A response with one or more service level objective.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
    request_description: The edited service level objective request object.
    request_schema_description: >-
      A service level objective object includes a service level indicator,
      thresholds

      for one or more timeframes, and metadata (`name`, `description`, `tags`,
      etc.).
  GetSLOHistory:
    description: >-
      Get a specific SLO’s history, regardless of its SLO type.


      The detailed history data is structured according to the source data type.

      For example, metric data is included for event SLOs that use

      the metric source, and monitor SLO types include the monitor transition
      history.


      **Note:** There are different response formats for event based and time
      based SLOs.

      Examples of both are shown.
    summary: Get an SLO's history
    responses:
      '200':
        description: OK
        schema_description: A service level objective history response.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
---
