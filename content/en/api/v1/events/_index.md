---
title: Events
description: >-
  The events service allows you to programmatically post events to the event
  stream

  and fetch events from the event stream. Events are limited to 4000 characters.
  If an event is sent out with a message

  containing more than 4000 characters only the 4000 first characters are
  displayed.
actions:
  ListEvents:
    description: >-
      The event stream can be queried and filtered by time, priority, sources
      and tags.


      **Note**: If the event you’re querying contains markdown formatting of any
      kind, you may see characters such as %,\,n in your output.
    summary: Query the event stream
    responses:
      '200':
        description: OK
        schema_description: An event list response.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
  CreateEvent:
    description: |-
      This endpoint allows you to post events to the stream.
      Tag them, set priority and event aggregate them with other events.
    summary: Post an event
    responses:
      '202':
        description: OK
        schema_description: Object containing an event response.
      '400':
        description: Bad Request
        schema_description: Error response object.
    request_description: Event request object
    request_schema_description: Object representing an event.
  GetEvent:
    description: >-
      This endpoint allows you to query for event details.


      **Note**: If the event you’re querying contains markdown formatting of any
      kind,

      you may see characters such as `%`,`\`,`n` in your output.
    summary: Get an event
    responses:
      '200':
        description: OK
        schema_description: Object containing an event response.
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '404':
        description: Item Not Found
        schema_description: Error response object.
---
