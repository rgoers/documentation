---
title: Users
description: 'Create, edit, and disable users.'
actions:
  SendInvitations:
    description: Sends emails to one or more users inviting them to join the organization.
    summary: Send invitation emails
    responses:
      '201':
        description: OK
        schema_description: User invitations as returned by the API.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
    request_description: ''
    request_schema_description: Object to invite users to join the organization.
  GetInvitation:
    description: Returns a single user invitation by its UUID.
    summary: Get a user invitation
    responses:
      '200':
        description: OK
        schema_description: User invitation as returned by the API.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  ListUsers:
    description: >-
      Get the list of all users in the organization. This list includes all
      users even if they are disabled or unverified.
    summary: List all users
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
  CreateUser:
    description: Create a user for your organization.
    summary: Create a user
    responses:
      '201':
        description: OK
        schema_description: Response containing information about a single user.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Authentication error
        schema_description: API error response.
    request_description: ''
    request_schema_description: Create a user.
  DisableUser:
    description: >-
      Disable a user. Can only be used with an application key belonging to an
      administrator user.
    summary: Disable a user
    responses:
      '204':
        description: OK
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  GetUser:
    description: Get a user in the organization specified by the user’s `user_id`.
    summary: Get a user
    responses:
      '200':
        description: OK for get user
        schema_description: Response containing information about a single user.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  UpdateUser:
    description: >-
      Edit a user. Can only be used with an application key belonging to an
      administrator user.
    summary: Update a user
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
      '422':
        description: Unprocessable Entity
        schema_description: API error response.
    request_description: ''
    request_schema_description: Update a user.
  ListUserOrganizations:
    description: >-
      Get a user organization. Returns the user information and all
      organizations joined by this user.
    summary: Get a user organization
    responses:
      '200':
        description: OK
        schema_description: Response containing information about a single user.
      '403':
        description: Authentication error
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  ListUserPermissions:
    description: >-
      Get a user permission set. Returns a list of the user’s permissions
      granted by the associated user's roles.
    summary: Get a user permissions
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
---
