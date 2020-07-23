---
title: Users
description: |-
  Create, edit, and disable users. [Read more about team management][1].

  [1]: https://docs.datadoghq.com/account_management/team
actions:
  ListUsers:
    description: Get all users for your organization.
    summary: Get all users
    responses:
      '200':
        description: OK
        schema_description: Array of Datadog users for a given organization.
      '403':
        description: Authentication error
        schema_description: Error response object.
  CreateUser:
    description: |-
      Create a user for your organization.

      **Note**: Users can only be created with the admin access role
      if application keys belong to administrators.
    summary: Create a user
    responses:
      '200':
        description: User created
        schema_description: A Datadog User.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '409':
        description: Conflict
        schema_description: Error response object.
    request_description: User object that needs to be created.
    request_schema_description: 'Create, edit, and disable users.'
  DisableUser:
    description: >-
      Delete a user from an organization.


      **Note**: This endpoint can only be used with application keys belonging
      to

      administrators.
    summary: Disable a user
    responses:
      '200':
        description: User disabled
        schema_description: Array of user disabled for a given organization.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  GetUser:
    description: Get a user's details.
    summary: Get user details
    responses:
      '200':
        description: OK for get user
        schema_description: A Datadog User.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  UpdateUser:
    description: >-
      Update a user information.


      **Note**: It can only be used with application keys belonging to
      administrators.
    summary: Update a user
    responses:
      '200':
        description: User updated
        schema_description: A Datadog User.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
    request_description: Description of the update.
    request_schema_description: 'Create, edit, and disable users.'
---
