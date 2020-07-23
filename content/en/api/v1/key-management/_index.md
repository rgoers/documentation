---
title: Key Management
description: |-
  Manage your Datadog API and application keys.

  You need an API and applications key with Admin rights
  to interact with this endpoint. The full list of keys can be seen on your
  [Datadog API page](https://app.datadoghq.com/account/settings#api).
actions:
  ListAPIKeys:
    description: Get all API keys available for your account.
    summary: Get all API keys
    responses:
      '200':
        description: OK
        schema_description: List of API and application keys available for a given organization.
      '403':
        description: Forbidden
        schema_description: Error response object.
  CreateAPIKey:
    description: Creates an API key with a given name.
    summary: Create an API key
    responses:
      '200':
        description: OK
        schema_description: An API key with its associated metadata.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: ''
    request_schema_description: Datadog API key.
  DeleteAPIKey:
    description: Delete a given API key.
    summary: Delete an API key
    responses:
      '200':
        description: OK
        schema_description: An API key with its associated metadata.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  GetAPIKey:
    description: Get a given API key.
    summary: Get API key
    responses:
      '200':
        description: OK
        schema_description: An API key with its associated metadata.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  UpdateAPIKey:
    description: Edit an API key name.
    summary: Edit an API key
    responses:
      '200':
        description: OK
        schema_description: An API key with its associated metadata.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
    request_description: ''
    request_schema_description: Datadog API key.
  ListApplicationKeys:
    description: Get all application keys available for your Datadog account.
    summary: Get all application keys
    responses:
      '200':
        description: OK
        schema_description: An application key response.
      '403':
        description: Forbidden
        schema_description: Error response object.
  CreateApplicationKey:
    description: Create an application key with a given name.
    summary: Create an application key
    responses:
      '200':
        description: OK
        schema_description: An application key response.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '409':
        description: Conflict
        schema_description: Error response object.
    request_description: ''
    request_schema_description: An application key with its associated metadata.
  DeleteApplicationKey:
    description: Delete a given application key.
    summary: Delete an application key
    responses:
      '200':
        description: OK
        schema_description: An application key response.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  GetApplicationKey:
    description: Get a given application key.
    summary: Get an application key
    responses:
      '200':
        description: OK
        schema_description: An application key response.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  UpdateApplicationKey:
    description: Edit an application key name.
    summary: Edit an application key
    responses:
      '200':
        description: OK
        schema_description: An application key response.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
      '409':
        description: Conflict
        schema_description: Error response object.
    request_description: ''
    request_schema_description: An application key with its associated metadata.
---
