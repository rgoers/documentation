---
title: Embeddable Graphs
description: Interact with embeddable graphs through the API.
actions:
  ListEmbeddableGraphs:
    description: Gets a list of previously created embeddable graphs.
    summary: Get all embeds
    responses:
      '200':
        description: OK
        schema_description: Response with embeddable graphs.
      '403':
        description: Authentication Error
        schema_description: Error response object.
  CreateEmbeddableGraph:
    description: >-
      Creates a new embeddable graph.


      Note: If an embed already exists for the exact same query in a given
      organization,

      the older embed is returned instead of creating a new embed.


      If you are interested in using template variables, see

      [Embeddable Graphs with Template
      Variables](https://docs.datadoghq.com/dashboards/faq/embeddable-graphs-with-template-variables).
    summary: Create embed
    responses:
      '200':
        description: Payload accepted
        schema_description: Embeddable graph.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
    request_description: Embeddable Graph body
    request_schema_description: Payload to create new embeddable graph.
  GetEmbeddableGraph:
    description: Get the HTML fragment for a previously generated embed with `embed_id`.
    summary: Get specific embed
    responses:
      '200':
        description: OK
        schema_description: Embeddable graph.
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '404':
        description: Not found
        schema_description: Error response object.
  EnableEmbeddableGraph:
    description: Enable a specified embed.
    summary: Enable embed
    responses:
      '200':
        description: OK
        schema_description: A JSON containing the success message
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '404':
        description: Not found
        schema_description: Error response object.
  RevokeEmbeddableGraph:
    description: Revoke a specified embed.
    summary: Revoke embed
    responses:
      '200':
        description: OK
        schema_description: A JSON containing the success message
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '404':
        description: Not found
        schema_description: Error response object.
---
