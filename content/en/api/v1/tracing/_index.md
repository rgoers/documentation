---
title: Tracing
description: >-
  Learn more about [tracing with Datadog](https://docs.datadoghq.com/tracing)

  and [the APM
  terminology](https://docs.datadoghq.com/tracing/visualization/services_list).


  The tracing API is an Agent API rather than a service side API.

  Submit your traces to the `http://localhost:8126/v0.3/traces` local endpoint

  so your Agent can forward them to Datadog.
actions:
  SubmitTraces:
    description: >-
      Datadog’s APM allows you to collect performance metrics by tracing your
      code

      to determine which parts of your application are slow or inefficient.


      Tracing data is sent to the Datadog Agent via an HTTP API.

      We provide some [official
      libraries](https://docs.datadoghq.com/tracing/#instrument-your-application)

      that simplify sending metrics to the Datadog Agent, however you may want
      to

      interact directly with the API to instrument applications that cannot use

      the libraries or are written in languages that don’t yet have an official

      Datadog Tracing library.
    summary: Send traces
    responses:
      '200':
        description: OK
    request_description: >-
      Traces can be sent as an array of traces:

          [ trace1, trace2, trace3 ]

      and each trace is an array of spans:

          trace1 = [ span, span2, span3 ]

      and each span is a dictionary with a `trace_id`, `span_id`, `resource`...


      [Learn more about the APM & Distributed Tracing
      terminology](https://docs.datadoghq.com/tracing/visualization/services_list)


      **Note:** Each span within a trace should use the same `trace_id`.

      However, `trace_id` and `span_id` must have different values.
    request_schema_description: An array of traces.
---
