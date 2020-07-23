---
title: Dashboard Lists
description: >-
  This endpoint is deprecated. Use the [new dashboard list
  endpoint](https://docs.datadoghq.com/api/v2/dashboard-lists/) instead.
actions:
  ListDashboardLists:
    description: Fetch all of your existing dashboard list definitions.
    summary: Get all dashboard lists
    responses:
      '200':
        description: OK
        schema_description: Information on your dashboard lists.
      '403':
        description: Forbidden
        schema_description: Error response object.
  CreateDashboardList:
    description: Create an empty dashboard list.
    summary: Create a dashboard list
    responses:
      '200':
        description: OK
        schema_description: Your Datadog Dashboards.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Create a dashboard list request body.
    request_schema_description: Your Datadog Dashboards.
  DeleteDashboardList:
    description: Delete a dashboard list.
    summary: Delete a dashboard list
    responses:
      '200':
        description: OK
        schema_description: Deleted dashboard details.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  GetDashboardList:
    description: Fetch an existing dashboard list's definition.
    summary: Get a dashboard list
    responses:
      '200':
        description: OK
        schema_description: Your Datadog Dashboards.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  UpdateDashboardList:
    description: Update the name of a dashboard list.
    summary: Update a dashboard list
    responses:
      '200':
        description: OK
        schema_description: Your Datadog Dashboards.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
    request_description: Update a dashboard list request body.
    request_schema_description: Your Datadog Dashboards.
---
