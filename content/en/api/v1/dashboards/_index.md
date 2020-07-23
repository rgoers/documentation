---
title: Dashboards
description: >-
  Interact with your dashboard lists through the API to make it easier to
  organize,

  find, and share all of your dashboards with your team and organization.
actions:
  ListDashboards:
    description: |-
      Get all dashboards.

      **Note**: This query will only return custom created or cloned dashboards.
      This query will not return preset dashboards.
    summary: Get all dashboards
    responses:
      '200':
        description: OK
        schema_description: Dashboard summary response.
      '403':
        description: Authentication Error
        schema_description: Error response object.
  CreateDashboard:
    description: Create a dashboard using the specified options.
    summary: Create a new dashboard
    responses:
      '200':
        description: OK
        schema_description: >-
          A dashboard is Datadog’s tool for visually tracking, analyzing, and
          displaying

          key performance metrics, which enable you to monitor the health of
          your infrastructure.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Create a dashboard request body.
    request_schema_description: >-
      A dashboard is Datadog’s tool for visually tracking, analyzing, and
      displaying

      key performance metrics, which enable you to monitor the health of your
      infrastructure.
  DeleteDashboard:
    description: Delete a dashboard using the specified ID.
    summary: Delete a dashboard
    responses:
      '200':
        description: OK
        schema_description: Response from the delete dashboard call.
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '404':
        description: Dashboards Not Found
        schema_description: Error response object.
  GetDashboard:
    description: Get a dashboard using the specified ID.
    summary: Get a dashboard
    responses:
      '200':
        description: OK
        schema_description: >-
          A dashboard is Datadog’s tool for visually tracking, analyzing, and
          displaying

          key performance metrics, which enable you to monitor the health of
          your infrastructure.
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
  UpdateDashboard:
    description: Update a dashboard using the specified ID.
    summary: Update a dashboard
    responses:
      '200':
        description: OK
        schema_description: >-
          A dashboard is Datadog’s tool for visually tracking, analyzing, and
          displaying

          key performance metrics, which enable you to monitor the health of
          your infrastructure.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
    request_description: Update Dashboard request body.
    request_schema_description: >-
      A dashboard is Datadog’s tool for visually tracking, analyzing, and
      displaying

      key performance metrics, which enable you to monitor the health of your
      infrastructure.
---
