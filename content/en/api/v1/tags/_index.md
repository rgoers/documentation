---
title: Tags
description: |-
  The tag endpoint allows you to assign tags to hosts,
  for example: `role:database`. Those tags are applied to
  all metrics sent by the host. Refer to hosts by name
  (`yourhost.example.com`) when fetching and applying
  tags to a particular host.

  The component of your infrastructure responsible for a tag is identified
  by a source. For example, some valid sources include nagios, hudson, jenkins,
  users, feed, chef, puppet, git, bitbucket, fabric, capistrano, etc.

  Read more about tags on the dedicated
  [documentation page](https://docs.datadoghq.com/tagging).
actions:
  ListHostTags:
    description: Return a mapping of tags to hosts for your whole infrastructure.
    summary: Get Tags
    responses:
      '200':
        description: OK
        schema_description: >-
          In this object, the key is the tag, the value is a list of host names
          that are reporting that tag.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  DeleteHostTags:
    description: |-
      This endpoint allows you to remove all user-assigned tags
      for a single host.
    summary: Remove host tags
    responses:
      '204':
        description: OK
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  GetHostTags:
    description: Return the list of tags that apply to a given host.
    summary: Get host tags
    responses:
      '200':
        description: OK
        schema_description: Set of tags to associate with your host.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
  CreateHostTags:
    description: |-
      This endpoint allows you to add new tags to a host,
      optionally specifying where these tags come from.
    summary: Add tags to a host
    responses:
      '201':
        description: Created
        schema_description: Set of tags to associate with your host.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
    request_description: Update host tags request body.
    request_schema_description: Set of tags to associate with your host.
  UpdateHostTags:
    description: |-
      This endpoint allows you to update/replace all tags in
      an integration source with those supplied in the request.
    summary: Update host tags
    responses:
      '201':
        description: OK
        schema_description: Set of tags to associate with your host.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not Found
        schema_description: Error response object.
    request_description: Add tags to host
    request_schema_description: Set of tags to associate with your host.
---
