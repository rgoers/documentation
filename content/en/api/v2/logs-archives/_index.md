---
title: Logs Archives
description: |-
  Archives forward all the logs ingested to a cloud storage system.

  See the [Archives Page](https://app.datadoghq.com/logs/pipelines/archives)
  for a list of the archives currently configured in our UI.
actions:
  ListLogsArchives:
    description: Get the list of configured logs archives with their definitions.
    summary: Get all archives
    responses:
      '200':
        description: OK
        schema_description: The available archives.
      '403':
        description: Forbidden
        schema_description: API error response.
  CreateLogsArchive:
    description: Create an archive in your organization.
    summary: Create an archive
    responses:
      '200':
        description: OK
        schema_description: The logs archive.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
    request_description: The definition of the new archive.
    request_schema_description: The logs archive.
  DeleteLogsArchive:
    description: Delete a given archive from your organization.
    summary: Delete an archive
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  GetLogsArchive:
    description: Get a specific archive from your organization.
    summary: Get an archive
    responses:
      '200':
        description: OK
        schema_description: The logs archive.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  UpdateLogsArchive:
    description: >-
      Update a given archive configuration.


      **Note**: Using this method updates your archive configuration by
      **replacing**

      your current configuration with the new one sent to your Datadog
      organization.
    summary: Update an archive
    responses:
      '200':
        description: OK
        schema_description: The logs archive.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
    request_description: New definition of the archive.
    request_schema_description: The logs archive.
  RemoveRoleFromArchive:
    description: >-
      Removes a role from an archive. ([Roles
      API](https://docs.datadoghq.com/api/v2/roles/))
    summary: Revoke role from an archive
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
    request_description: ''
    request_schema_description: Relationship to role.
  ListArchiveReadRoles:
    description: Returns all read roles a given archive is restricted to.
    summary: List read roles for an archive
    responses:
      '200':
        description: OK
        schema_description: Response containing information about multiple roles.
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
  AddReadRoleToArchive:
    description: >-
      Adds a read role to an archive. ([Roles
      API](https://docs.datadoghq.com/api/v2/roles/))
    summary: Grant role to an archive
    responses:
      '204':
        description: OK
      '400':
        description: Bad Request
        schema_description: API error response.
      '403':
        description: Forbidden
        schema_description: API error response.
      '404':
        description: Not found
        schema_description: API error response.
    request_description: ''
    request_schema_description: Relationship to role.
---
