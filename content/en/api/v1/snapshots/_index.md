---
title: Snapshots
description: Take graph snapshots using the API.
actions:
  GetGraphSnapshot:
    description: >-
      Take graph snapshots.

      **Note**: When a snapshot is created, there is some delay before it is
      available.
    summary: Take graph snapshots
    responses:
      '200':
        description: OK
        schema_description: Object representing a graph snapshot.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
---
