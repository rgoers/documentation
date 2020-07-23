---
title: Synthetics
description: >-
  Datadog Synthetics uses simulated user requests and browser rendering to help
  you ensure uptime,

  identify regional issues, and track your application performance. Datadog
  Synthetics tests come in

  two different flavors, [API
  tests](https://docs.datadoghq.com/synthetics/api_tests/?tab=httptest)

  and [browser tests](https://docs.datadoghq.com/synthetics/browser_tests). You
  can use Datadog’s API to

  manage both test types programmatically.


  For more information about Synthetics, see the [Synthetics
  overview](https://docs.datadoghq.com/synthetics/).
actions:
  ListLocations:
    description: >-
      Get the list of public and private locations available for Synthetics
      tests. No arguments required.
    summary: Get all locations (public and private)
    responses:
      '200':
        description: OK
        schema_description: List of Synthetics locations.
  ListTests:
    description: Get the list of all Synthetic tests (can be filtered by type).
    summary: Get a list of tests
    responses:
      '200':
        description: >-
          OK - Returns the list of all Synthetic tests (properly filtered by
          type).
        schema_description: Object containing an array of Synthetic tests configuration.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Synthetics is not activated for the user.
        schema_description: Error response object.
  CreateTest:
    description: Create a Synthetic test.
    summary: Create a test
    responses:
      '200':
        description: OK - Returns the created test details.
        schema_description: Object containing details about your Synthetic test.
      '400':
        description: |-
          - JSON format is wrong
          - Creation failed
        schema_description: Error response object.
      '402':
        description: Test quota is reached
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Details of the test to create.
    request_schema_description: Object containing details about your Synthetic test.
  GetBrowserTest:
    description: >-
      Get the detailed configuration (including steps) associated with a
      Synthetics browser test.
    summary: Get a test configuration (browser)
    responses:
      '200':
        description: OK
        schema_description: Object containing details about your Synthetic test.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test is not owned by the user
        schema_description: Error response object.
  GetBrowserTestLatestResults:
    description: >-
      Get the last 50 test results summaries for a given Synthetics Browser
      test.
    summary: Get the test's latest results summaries (browser)
    responses:
      '200':
        description: OK
        schema_description: Object with the latest Synthetic browser test run.
      '403':
        description: forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test is not owned by the user
        schema_description: Error response object.
  GetBrowserTestResult:
    description: Get a specific full result from a given (browser) Synthetic test.
    summary: Get a test result (browser)
    responses:
      '200':
        description: OK
        schema_description: Object returned describing a browser test result.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test or result is not owned by the user
        schema_description: Error response object.
  DeleteTests:
    description: Delete multiple Synthetic tests by ID.
    summary: Delete tests
    responses:
      '200':
        description: OK.
        schema_description: Response object for deleting Synthetic tests.
      '400':
        description: >-
          - JSON format is wrong

          - Test cannot be deleted as it's used elsewhere (as a sub-test or in
          an uptime widget)

          - Some IDs are not owned by the user
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Tests to be deleted can't be found
          - Synthetics is not activated for the user
        schema_description: Error response object.
    request_description: Public ID list of the Synthetic tests to be deleted.
    request_schema_description: >-
      A JSON list of the ID or IDs of the Synthetic tests that you want to
      delete.
  TriggerCITests:
    description: Trigger a set of Synthetics tests for continuous integration
    summary: Trigger some Synthetics tests for CI
    responses:
      '200':
        description: OK
        schema_description: Object containing information about the tests triggered.
      '400':
        description: JSON format is wrong
        schema_description: Error response object.
    request_description: Details of the test to trigger.
    request_schema_description: Object describing the synthetics tests to trigger.
  GetTest:
    description: Get the detailed configuration associated with a Synthetics test.
    summary: Get a test configuration (API)
    responses:
      '200':
        description: OK
        schema_description: Object containing details about your Synthetic test.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test is not owned by the user
        schema_description: Error response object.
  UpdateTest:
    description: Edit the configuration of a Synthetic test.
    summary: Edit a test
    responses:
      '200':
        description: OK
        schema_description: Object containing details about your Synthetic test.
      '400':
        description: |-
          - JSON format is wrong
          - Updating sub-type is forbidden
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test is not owned by the user
          - Test can't be found
        schema_description: Error response object.
    request_description: New test details to be saved.
    request_schema_description: Object containing details about your Synthetic test.
  GetAPITestLatestResults:
    description: Get the last 50 test results summaries for a given Synthetics API test.
    summary: Get the test's latest results summaries (API)
    responses:
      '200':
        description: OK
        schema_description: Object with the latest Synthetic API test run.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test is not owned by the user
        schema_description: Error response object.
  GetAPITestResult:
    description: Get a specific full result from a given (API) Synthetic test.
    summary: Get a test result (API)
    responses:
      '200':
        description: OK
        schema_description: Object returned describing a API test result.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test or result is not owned by the user
        schema_description: Error response object.
  UpdateTestPauseStatus:
    description: Pause or start a Synthetics test by changing the status.
    summary: Pause or start a test
    responses:
      '200':
        description: OK - Returns a boolean indicating if the update was successful.
      '400':
        description: JSON format is wrong.
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: |-
          - Synthetic is not activated for the user
          - Test is not owned by the user
        schema_description: Error response object.
    request_description: Status to set the given Synthetic test to.
    request_schema_description: Object to start or pause an existing Synthetic test.
  CreateGlobalVariable:
    description: Create a Synthetics global variable.
    summary: Create a global variable
    responses:
      '200':
        description: OK
        schema_description: Synthetics global variable.
      '400':
        description: Invalid request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Details of the global variable to create.
    request_schema_description: Synthetics global variable.
  DeleteGlobalVariable:
    description: Delete a Synthetics global variable.
    summary: Delete a global variable
    responses:
      '200':
        description: OK
      '400':
        description: JSON format is wrong
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '404':
        description: Not found
        schema_description: Error response object.
  EditGlobalVariable:
    description: Edit a Synthetics global variable.
    summary: Edit a global variable
    responses:
      '200':
        description: OK
        schema_description: Synthetics global variable.
      '400':
        description: Invalid request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Details of the global variable to update.
    request_schema_description: Synthetics global variable.
---
