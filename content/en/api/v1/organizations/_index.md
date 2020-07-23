---
title: Organizations
description: >-
  Create, edit, and manage your organizations. Read more about [multi-org
  accounts](https://docs.datadoghq.com/account_management/multi_organization).
actions:
  ListOrgs:
    description: List your managed organizations.
    summary: List your managed organizations
    responses:
      '200':
        description: OK
        schema_description: Response with the list of organizations.
      '403':
        description: Forbidden
        schema_description: Error response object.
  CreateChildOrg:
    description: >-
      Create a child organization.


      This endpoint requires the

      [multi-organization
      account](https://docs.datadoghq.com/account_management/multi_organization/)

      feature and must be enabled by

      [contacting support](https://docs.datadoghq.com/help/).


      Once a new child organization is created, you can interact with it

      by using the `org.public_id`, `pi_key.key`, and

      `application_key.hash` provided in the response.
    summary: Create a child organization
    responses:
      '200':
        description: OK
        schema_description: Response object for an organization creation.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: Organization object that needs to be created
    request_schema_description: Object describing an organization to create.
  GetOrg:
    description: Get organization information.
    summary: Get organization information
    responses:
      '200':
        description: OK
        schema_description: Response with an organization.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
  UpdateOrg:
    description: Update your organization.
    summary: Update your organization
    responses:
      '200':
        description: OK
        schema_description: Response with an organization.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
    request_description: ''
    request_schema_description: 'Create, edit, and manage organizations.'
  UploadIdPForOrg:
    description: |-
      There are a couple of options for updating the Identity Provider (IdP)
      metadata from your SAML IdP.

      * **Multipart Form-Data**: Post the IdP metadata file using a form post.

      * **XML Body:** Post the IdP metadata file as the body of the request.
    summary: Upload IdP metadata
    responses:
      '200':
        description: OK
        schema_description: The IdP response object.
      '400':
        description: Bad Request
        schema_description: Error response object.
      '403':
        description: Forbidden
        schema_description: Error response object.
      '415':
        description: Unsupported Media Type
        schema_description: Error response object.
    request_description: ''
---
