---
title: Logs Restriction Queries
description: >-
  **Note: This endpoint is in public beta. If you have any feedback, contact
  [Datadog support](https://docs.datadoghq.com/help/).**


  To grant read access on log data at all, you must grant the `logs_read_data`
  permission.

  From there you can limit what data a role grants read access to by associating
  a Restriction Query with that role.


  A Restriction Query is a logs query that restricts which logs the
  `logs_read_data` permission grants read access to.

  For users whose roles have Restriction Queries, any log query they make only
  returns those log events that also match

  one of their Restriction Queries. This is true whether the user queries log
  events from any log-related feature, including

  the log explorer, Live Tail, re-hydration, or a dashboard widget.


  Restriction Queries currently only support use of the following components of
  log events:


  - Reserved attributes

  - The log message

  - Tags


  The recommended way to manage restricted read access on log data for customers
  with large or complicated organizational structures

  is to add a team tag to log events to indicate which team(s) own(s) them, and
  then to scope Restriction Queries to the appropriate

  values of the team tag. Tags can be applied to log events in many ways, and a
  log event can have multiple tags with the same key (like team)

  and different values—in this way the same log event can be visible to roles
  whose restriction queries are scoped to different team values.
actions:
  ListRestrictionQueries:
    description: 'Returns all restriction queries, including their names and IDs.'
    summary: List restriction queries
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple restriction queries.
      '403':
        description: Authentication error
        schema_description: API error response.
  CreateRestrictionQuery:
    description: Create a new restriction query for your organization.
    summary: Create a restriction query
    responses:
      '200':
        description: OK
        schema_description: Response containing information about a single restriction query.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
    request_description: ''
    request_schema_description: Create a restriction query.
  GetRoleRestrictionQuery:
    description: Get restriction query for a given role.
    summary: Get restriction query for a given role
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple restriction queries.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
  ListUserRestrictionQueries:
    description: Get all restriction queries for a given user.
    summary: Get all restriction queries for a given user
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple restriction queries.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
  DeleteRestrictionQuery:
    description: Deletes a restriction query.
    summary: Delete a restriction query
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  GetRestrictionQuery:
    description: >-
      Get a restriction query in the organization specified by the restriction
      query's `restriction_query_id`.
    summary: Get a restriction query
    responses:
      '200':
        description: OK
        schema_description: Response containing information about a single restriction query.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  UpdateRestrictionQuery:
    description: Edit a restriction query.
    summary: Update a restriction query
    responses:
      '200':
        description: OK
        schema_description: Response containing information about a single restriction query.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
    request_description: ''
    request_schema_description: Update a restriction query.
  RemoveRoleFromRestrictionQuery:
    description: Removes a role from a restriction query.
    summary: Revoke role from a restriction query
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
    request_description: ''
    request_schema_description: Relationship to role.
  ListRestrictionQueryRoles:
    description: Returns all roles that have a given restriction query.
    summary: List roles for a restriction query
    responses:
      '200':
        description: OK
        schema_description: >-
          Response containing information about roles attached to a restriction
          query.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  AddRoleToRestrictionQuery:
    description: Adds a role to a restriction query.
    summary: Grant role to a restriction query
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
    request_description: ''
    request_schema_description: Relationship to role.
---
