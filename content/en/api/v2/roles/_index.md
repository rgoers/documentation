---
title: Roles
description: |-
  The Roles API is used to create and manage Datadog roles, what
  [global permissions](https://docs.datadoghq.com/account_management/rbac/)
  they grant, and which users belong to them.

  Permissions related to specific account assets can be granted to roles
  in the Datadog application without using this API. For example, granting
  read access on a specific log index to a role can be done in Datadog from the
  [Pipelines page](https://app.datadoghq.com/logs/pipelines).
actions:
  ListPermissions:
    description: 'Returns a list of all permissions, including name, description, and ID.'
    summary: List permissions
    responses:
      '200':
        description: OK
        schema_description: Payload with API-returned permissions.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
  ListRoles:
    description: 'Returns all roles, including their names and IDs.'
    summary: List roles
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple roles.
      '403':
        description: Authentication error
        schema_description: API error response.
  CreateRole:
    description: Create a new role for your organization.
    summary: Create role
    responses:
      '200':
        description: OK
        schema_description: Response containing information about a created role.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
    request_description: ''
    request_schema_description: Create a role.
  DeleteRole:
    description: Disables a role.
    summary: Delete role
    responses:
      '204':
        description: OK
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  GetRole:
    description: Get a role in the organization specified by the role’s `role_id`.
    summary: Get a role
    responses:
      '200':
        description: OK for get role
        schema_description: Response containing information about a single role.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  UpdateRole:
    description: >-
      Edit a role. Can only be used with application keys belonging to
      administrators.
    summary: Update a role
    responses:
      '200':
        description: OK
        schema_description: Response containing information about an updated role.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
      '422':
        description: Unprocessable Entity
        schema_description: API error response.
    request_description: ''
    request_schema_description: Update a role.
  RemovePermissionFromRole:
    description: Removes a permission from a role.
    summary: Revoke permission
    responses:
      '200':
        description: OK
        schema_description: Payload with API-returned permissions.
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
    request_schema_description: Relationship to a permissions object.
  ListRolePermissions:
    description: Returns a list of all permissions for a single role.
    summary: List permissions for a role
    responses:
      '200':
        description: OK
        schema_description: Payload with API-returned permissions.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  AddPermissionToRole:
    description: Adds a permission to a role.
    summary: Grant permission to a role
    responses:
      '200':
        description: OK
        schema_description: Payload with API-returned permissions.
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
    request_schema_description: Relationship to a permissions object.
  RemoveUserFromRole:
    description: Removes a user from a role.
    summary: Remove a user from a role
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple users.
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
    request_schema_description: Relationship to user.
  ListRoleUsers:
    description: Gets all users of a role.
    summary: Get all users of a role
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple users.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  AddUserToRole:
    description: Adds a user to a role.
    summary: Add a user to a role
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple users.
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
    request_schema_description: Relationship to user.
---
