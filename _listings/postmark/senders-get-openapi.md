---
swagger: "2.0"
x-collection-name: Postmark
x-complete: 0
info:
  title: Postmark Account List Sender Signatures
  description: List sender signatures.
  version: 0.9.0
host: api.postmarkapp.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /domains:
    get:
      summary: List Domains
      description: List domains.
      operationId: listDomains
      x-api-path-slug: domains-get
      parameters:
      - in: query
        name: count
        description: Number of records to return per request
      - in: query
        name: offset
        description: Number of records to skip
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Domains
    post:
      summary: Create a Domain
      description: Create a domain.
      operationId: createDomain
      x-api-path-slug: domains-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Domains
  /domains/{domainid}:
    delete:
      summary: Delete a Domain
      description: Delete a domain.
      operationId: deleteDomain
      x-api-path-slug: domainsdomainid-delete
      parameters:
      - in: path
        name: domainid
        description: The ID for the Domain that should be deleted by the request
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Domains
      - Domainid
    get:
      summary: Get a Domain
      description: Get a domain.
      operationId: getDomain
      x-api-path-slug: domainsdomainid-get
      parameters:
      - in: path
        name: domainid
        description: The ID for the Domain that should be retrieved
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Domains
      - Domainid
    put:
      summary: Update a Domain
      description: Update a domain.
      operationId: editDomain
      x-api-path-slug: domainsdomainid-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: domainid
        description: The ID for the Domain that should be modified by the request
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Domains
      - Domainid
  /domains/{domainid}/rotatedkim:
    post:
      summary: Rotate DKIM Key
      description: "Creates a new DKIM key to replace your current key. Until the
        DNS entries are confirmed, \nthe new values will be in the `DKIMPendingHost`
        and `DKIMPendingTextValue` fields. \nAfter the new DKIM value is verified
        in DNS, the pending values will migrate to \n`DKIMTextValue` and `DKIMPendingTextValue`
        and Postmark will begin to sign emails \nwith the new DKIM key."
      operationId: rotateDKIMKeyForDomain
      x-api-path-slug: domainsdomainidrotatedkim-post
      parameters:
      - in: path
        name: domainid
        description: The ID for the Sender Signature for which a new DKIM Key should
          be generated
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Domains
      - Domainid
      - Rotatedkim
  /domains/{domainid}/verifyspf:
    post:
      summary: Request DNS Verification for SPF
      description: Request dns verification for spf.
      operationId: requestSPFVerificationForDomain
      x-api-path-slug: domainsdomainidverifyspf-post
      parameters:
      - in: path
        name: domainid
        description: The ID for the Domain for which SPF DNS records should be verified
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Domains
      - Domainid
      - Verifyspf
  /senders:
    get:
      summary: List Sender Signatures
      description: List sender signatures.
      operationId: listSenderSignatures
      x-api-path-slug: senders-get
      parameters:
      - in: query
        name: count
        description: Number of records to return per request
      - in: query
        name: offset
        description: Number of records to skip
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Senders
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---