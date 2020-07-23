---
title: Monitors
description: >-
  [Monitors][1] allow you to watch a metric or
  check that you care about,

  notifying your team when some defined threshold is exceeded.

  Refer to the Creating Monitors page for more information on creating monitors.
actions:
  ListMonitors:
    description: Get details about the specified monitor from your organization.
    summary: Get all monitor details
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  CreateMonitor:
    description: >-
      Create a monitor using the specified options.


      #### Monitor Types


      The type of monitor chosen from:


      - anomaly: `query alert`

      - APM: `query alert` or `trace-analytics alert`

      - composite: `composite`

      - custom: `service check`

      - event: `event alert`

      - forecast: `query alert`

      - host: `service check`

      - integration: `query alert` or `service check`

      - live process: `process alert`

      - logs: `log alert`

      - metric: `metric alert`

      - network: `service check`

      - outlier: `query alert`

      - process: `service check`

      - rum: `rum alert`

      - watchdog: `event alert`


      #### Query Types


      **Metric Alert Query**


      Example: `time_aggr(time_window):space_aggr:metric{tags} [by {key}]
      operator #`


      - `time_aggr`: avg, sum, max, min, change, or pct_change

      - `time_window`: `last_#m` (with `#` being 5, 10, 15, or 30) or
      `last_#h`(with `#` being 1, 2, or 4), or `last_1d`

      - `space_aggr`: avg, sum, min, or max

      - `tags`: one or more tags (comma-separated), or *

      - `key`: a 'key' in key:value tag syntax; defines a separate alert for
      each tag in the group (multi-alert)

      - `operator`: <, <=, >, >=, ==, or !=

      - `#`: an integer or decimal number used to set the threshold


      If you are using the `_change_` or `_pct_change_` time aggregator, instead
      use `change_aggr(time_aggr(time_window),

      timeshift):space_aggr:metric{tags} [by {key}] operator #` with:


      - `change_aggr` change, pct_change

      - `time_aggr` avg, sum, max, min [Learn
      more](https://docs.datadoghq.com/monitors/monitor_types/#define-the-conditions)

      - `time_window` last\_#m (1, 5, 10, 15, or 30), last\_#h (1, 2, or 4), or
      last_#d (1 or 2)

      - `timeshift` #m_ago (5, 10, 15, or 30), #h_ago (1, 2, or 4), or 1d_ago


      Use this to create an outlier monitor using the following query:

      `avg(last_30m):outliers(avg:system.cpu.user{role:es-events-data} by
      {host}, 'dbscan', 7) > 0`


      **Service Check Query**


      Example: `"check".over(tags).last(count).count_by_status()`


      - **`check`** name of the check, e.g. `datadog.agent.up`

      - **`tags`** one or more quoted tags (comma-separated), or "*". e.g.:
      `.over("env:prod", "role:db")`

      - **`count`** must be at >= your max threshold (defined in the `options`).

      e.g. if you want to notify on 1 critical, 3 ok and 2 warn statuses count
      should be 3. It is limited to 100.


      **Event Alert Query**


      Example: `events('sources:nagios status:error,warning priority:normal
      tags: "string query"').rollup("count").last("1h")"`


      - **`event`**, the event query string:

      - **`string_query`** free text query to match against event title and
      text.

      - **`sources`** event sources (comma-separated).

      - **`status`** event statuses (comma-separated). Valid options: error,
      warn, and info.

      - **`priority`** event priorities (comma-separated). Valid options: low,
      normal, all.

      - **`host`** event reporting host (comma-separated).

      - **`tags`** event tags (comma-separated).

      - **`excluded_tags`** excluded event tags (comma-separated).

      - **`rollup`** the stats roll-up method. `count` is the only supported
      method now.

      - **`last`** the timeframe to roll up the counts. Examples: 60s, 4h.
      Supported timeframes: s, m, h and d. This value should not exceed 48
      hours.


      **Process Alert Query**


      Example: `processes(search).over(tags).rollup('count').last(timeframe)
      operator #`


      - **`search`** free text search string for querying processes.

      Matching processes match results on the [Live
      Processes](https://docs.datadoghq.com/infrastructure/process/?tab=linuxwindows)
      page.

      - **`tags`** one or more tags (comma-separated)

      - **`timeframe`** the timeframe to roll up the counts. Examples: 60s, 4h.
      Supported timeframes: s, m, h and d

      - **`operator`** <, <=, >, >=, ==, or !=

      - **`#`** an integer or decimal number used to set the threshold


      **Logs Alert Query**


      Example: `logs(query).index(index_name).rollup(rollup_method[,
      measure]).last(time_window) operator #`


      - **`query`** The search query - following the [Log search
      syntax](https://docs.datadoghq.com/logs/search_syntax/).

      - **`index_name`** For multi-index organizations, the log index in which
      the request is performed.

      - **`rollup_method`** The stats roll-up method - supports `count`, `avg`
      and `cardinality`.

      - **`measure`** For `avg` and cardinality `rollup_method` - specify the
      measure or the facet name you want to use.

      - **`time_window`** #m (5, 10, 15, or 30), #h (1, 2, or 4, 24)

      - **`operator`** `<`, `<=`, `>`, `>=`, `==`, or `!=`.

      - **`#`** an integer or decimal number used to set the threshold.


      **Composite Query**


      Example: `12345 && 67890`, where `12345` and `67890` are the IDs of
      non-composite monitors


      * **`name`** [*required*, *default* = **dynamic, based on query**]: The
      name of the alert.

      * **`message`** [*required*, *default* = **dynamic, based on query**]: A
      message to include with notifications for this monitor.

      Email notifications can be sent to specific users by using the same
      '@username' notation as events.

      * **`tags`** [*optional*, *default* = **empty list**]: A list of tags to
      associate with your monitor.

      When getting all monitor details via the API, use the `monitor_tags`
      argument to filter results by these tags.

      It is only available via the API and isn't visible or editable in the
      Datadog UI.
    summary: Create a monitor
    responses:
      '200':
        description: OK
        schema_description: Object describing a monitor.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Create a monitor request body.
    request_schema_description: Object describing a monitor.
  CheckCanDeleteMonitor:
    description: Check if the given monitors can be deleted.
    summary: Check if a monitor can be deleted
    responses:
      '200':
        description: OK
        schema_description: Response of monitor IDs that can or can't be safely deleted.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '409':
        description: Deletion conflict error
        schema_description: Response of monitor IDs that can or can't be safely deleted.
  SearchMonitorGroups:
    description: Search and filter your monitor groups details.
    summary: Monitors group search
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  SearchMonitors:
    description: Search and filter your monitors details.
    summary: Monitors search
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  ValidateMonitor:
    description: Validate the monitor provided in the request.
    summary: Validate a monitor
    responses:
      '200':
        description: OK
        schema_description: Object describing a monitor.
      '400':
        description: Invalid JSON
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Monitor request object
    request_schema_description: Object describing a monitor.
  DeleteMonitor:
    description: Delete the specified monitor
    summary: Delete a monitor
    responses:
      '200':
        description: OK
        schema_description: Response from the delete monitor call.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '401':
        description: Authentication error
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Item not found error
        schema_description: Error response object.
  GetMonitor:
    description: Get details about the specified monitor from your organization.
    summary: Get a monitor's details
    responses:
      '200':
        description: OK
        schema_description: Object describing a monitor.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Monitor Not Found error
        schema_description: Error response object.
  UpdateMonitor:
    description: Edit the specified monitor.
    summary: Edit a monitor
    responses:
      '200':
        description: OK
        schema_description: Object describing a monitor.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '401':
        description: Authentication error
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Monitor Not Found error
        schema_description: Error response object.
    request_description: Edit a monitor request body.
    request_schema_description: Object describing a monitor update request.
  MuteMonitor:
    description: Mute the specified monitor.
    summary: Mute a monitor
    responses:
      '200':
        description: OK
        schema_description: Object describing a monitor.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '401':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Monitor Not Found error
        schema_description: Error response object.
  UnmuteMonitor:
    description: Mute the specified monitor.
    summary: Unmute a monitor
    responses:
      '200':
        description: OK
        schema_description: Object describing a monitor.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '401':
        description: Authentication error
        schema_description: Error response object.
      '404':
        description: Monitor Not Found error
        schema_description: Error response object.
  ResolveMonitor:
    description: Resolve monitor.
    summary: Resolve Monitor
    responses:
      '200':
        description: OK
    request_description: >-
      Array of group(s) to resolve for a given monitor_id, e.g.:

      `{"monitor_id": "group_to_resolve"}`.


      It supports multiple groups per monitor, e.g.:

      `resolve: [{"monitor_id": "group_1"}, {"monitor_id": "group_2"}]`.


      It can also resolve all triggered groups with the pseudo-group
      `ALL_GROUPS`:

      `resolve: [{"monitor_id": "ALL_GROUPS"}]`.
    request_schema_description: ''
  MuteAllMonitors:
    description: |-
      Muting prevents all monitors from notifying through email and posts to the
      [event stream][2].
      State changes are only visible by checking the alert page.
    summary: Mute all monitors
    responses:
      '200':
        description: OK
        schema_description: Object describing a monitor.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '401':
        description: Authentication error
        schema_description: Error response object.
  UnmuteAllMonitors:
    description: |-
      Disables muting all monitors. Throws an error if mute all
      was not enabled previously.
    summary: Unmute all monitors
    responses:
      '200':
        description: OK
      '400':
        description: Bad Request
      '401':
        description: Authentication error
        schema_description: Error response object.
---
[1]: https://docs.datadoghq.com/monitors
[2]: https://docs.datadoghq.com/events
