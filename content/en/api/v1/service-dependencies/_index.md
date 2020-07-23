---
title: Service Dependencies
description: >-
  APM Service Map API. For more information, visit

  the [services map
  documentation](https://docs.datadoghq.com/tracing/visualization/services_map/).
actions:
  ListServiceDependencies:
    description: >-
      Get a list of services and their dependencies. The services retrieved are
      filtered by environment and a

      primary tag, if one is defined.
    summary: Get all service dependencies
    responses:
      '200':
        description: OK
        schema_description: An object containing a list of services and their dependencies.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
  ListSingleServiceDependencies:
    description: >-
      Get a specific service's immediate upstream and downstream services.

      The services retrieved are filtered by environment and a primary tag, if
      one is defined.
    summary: Get one service's dependencies
    responses:
      '200':
        description: OK
        schema_description: >-
          An object with information on service that call, and are called by a
          service.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
---
