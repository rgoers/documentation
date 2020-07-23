---
title: Dashboard Lists
description: |-
  Interact with your dashboard lists through the API to make it easier to
  organize, find, and share all of your dashboards with your team and
  organization.
actions:
  DeleteDashboardListItems:
    description: Delete dashboards from an existing dashboard list.
    summary: Delete items from a dashboard list
    responses:
      '200':
        description: OK
        schema_description: Response containing a list of deleted dashboards.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not Found
        schema_description: API error response.
    request_description: Dashboards to delete from the dashboard list.
    request_schema_description: Request containing a list of dashboards to delete.
  GetDashboardListItems:
    description: Fetch the dashboard list’s dashboard definitions.
    summary: Get a Dashboard List
    responses:
      '200':
        description: OK
        schema_description: Dashboards within a list.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not Found
        schema_description: API error response.
  CreateDashboardListItems:
    description: Add dashboards to an existing dashboard list.
    summary: Add Items to a Dashboard List
    responses:
      '200':
        description: OK
        schema_description: Response containing a list of added dashboards.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not Found
        schema_description: API error response.
    request_description: Dashboards to add to the dashboard list.
    request_schema_description: Request containing a list of dashboards to add.
  UpdateDashboardListItems:
    description: Update dashboards of an existing dashboard list.
    summary: Update items of a dashboard list
    responses:
      '200':
        description: OK
        schema_description: Response containing a list of updated dashboards.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not Found
        schema_description: API error response.
    request_description: New dashboards of the dashboard list.
    request_schema_description: Request containing the list of dashboards to update to.
---
