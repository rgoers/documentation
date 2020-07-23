---
title: Service Checks
description: >-
  The service check endpoint allows you to post check statuses for use with
  monitors.

  Service check messages are limited to 500 characters. If a check is posted
  with a message

  containing more than 500 characters, only the first 500 characters are
  displayed.


  - [Read more about Service Check monitors.][1]

  - [Read more about Process Check monitors.][2]

  - [Read more about Network Check monitors.][3]

  - [Read more about Custom Check monitors.][4]


  [1]: https://docs.datadoghq.com/monitors/monitor_types/host/?tab=checkalert

  [2]:
  https://docs.datadoghq.com/monitors/monitor_types/process_check/?tab=checkalert

  [3]: https://docs.datadoghq.com/monitors/monitor_types/network/?tab=checkalert

  [4]:
  https://docs.datadoghq.com/monitors/monitor_types/custom_check/?tab=checkalert
actions:
  SubmitServiceCheck:
    description: |-
      Submit a list of Service Checks.

      **Note**: A valid API key is required.
    summary: Submit a Service Check
    responses:
      '202':
        description: Payload accepted
        schema_description: The payload accepted for intake.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication Error
        schema_description: Error response object.
      '408':
        description: Request timeout
        schema_description: Error response object.
      '413':
        description: Payload too large
        schema_description: Error response object.
    request_description: Service Check request body.
    request_schema_description: The service checks.
---
