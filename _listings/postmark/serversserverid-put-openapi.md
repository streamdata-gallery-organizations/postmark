---
swagger: "2.0"
x-collection-name: Postmark
x-complete: 0
info:
  title: Postmark Account Edit a Server
  description: Edit a server.
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
    post:
      summary: Create a Sender Signature
      description: Create a sender signature.
      operationId: createSenderSignature
      x-api-path-slug: senders-post
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
      - Senders
  /senders/{signatureid}:
    delete:
      summary: Delete a Sender Signature
      description: Delete a sender signature.
      operationId: deleteSenderSignature
      x-api-path-slug: senderssignatureid-delete
      parameters:
      - in: path
        name: signatureid
        description: The ID for the Sender Signature that should be deleted by the
          request
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Senders
      - Signatureid
    get:
      summary: Get a Sender Signature
      description: Get a sender signature.
      operationId: getSenderSignature
      x-api-path-slug: senderssignatureid-get
      parameters:
      - in: path
        name: signatureid
        description: The ID for the Sender Signature that should be retrieved
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Senders
      - Signatureid
    put:
      summary: Update a Sender Signature
      description: Update a sender signature.
      operationId: editSenderSignature
      x-api-path-slug: senderssignatureid-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: signatureid
        description: The ID for the Sender Signature that should be modified by the
          request
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Senders
      - Signatureid
  /senders/{signatureid}/requestnewdkim:
    post:
      summary: Request a new DKIM Key
      description: "Requests a new DKIM key to be created. Until the DNS entries are
        confirmed, \nthe new values will be in the `DKIMPendingHost` and `DKIMPendingTextValue`
        fields. \nAfter the new DKIM value is verified in DNS, the pending values
        will migrate to \n`DKIMTextValue` and `DKIMPendingTextValue` and Postmark
        will begin to sign emails \nwith the new DKIM key."
      operationId: requestNewDKIMKeyForSenderSignature
      x-api-path-slug: senderssignatureidrequestnewdkim-post
      parameters:
      - in: path
        name: signatureid
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
      - Senders
      - Signatureid
      - Requestnewdkim
  /senders/{signatureid}/resend:
    post:
      summary: Resend Signature Confirmation Email
      description: Resend signature confirmation email.
      operationId: resendSenderSignatureConfirmationEmail
      x-api-path-slug: senderssignatureidresend-post
      parameters:
      - in: path
        name: signatureid
        description: The ID for the Sender Signature that should have its confirmation
          email resent
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Senders
      - Signatureid
      - Resend
  /senders/{signatureid}/verifyspf:
    post:
      summary: Request DNS Verification for SPF
      description: Request dns verification for spf.
      operationId: requestSPFVerificationForSenderSignature
      x-api-path-slug: senderssignatureidverifyspf-post
      parameters:
      - in: path
        name: signatureid
        description: The ID for the Sender Signature for which SPF DNS records should
          be verified
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Senders
      - Signatureid
      - Verifyspf
  /servers:
    get:
      summary: List servers
      description: List servers.
      operationId: listServers
      x-api-path-slug: servers-get
      parameters:
      - in: query
        name: count
        description: Number of servers to return per request
      - in: query
        name: name
        description: Filter by a specific server name
      - in: query
        name: offset
        description: Number of servers to skip
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Servers
    post:
      summary: Create a Server
      description: Create a server.
      operationId: createServer
      x-api-path-slug: servers-post
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
      - Servers
  /servers/{serverid}:
    delete:
      summary: Delete a Server
      description: Delete a server.
      operationId: deleteServer
      x-api-path-slug: serversserverid-delete
      parameters:
      - in: path
        name: serverid
        description: The ID of the Server that should be deleted
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Servers
      - Serverid
    get:
      summary: Get a Server
      description: Get a server.
      operationId: getServerInformation
      x-api-path-slug: serversserverid-get
      parameters:
      - in: path
        name: serverid
        description: The ID of the Server to get
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Servers
      - Serverid
    put:
      summary: Edit a Server
      description: Edit a server.
      operationId: editServerInformation
      x-api-path-slug: serversserverid-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: serverid
        description: The ID of the Server to update
      - in: header
        name: X-Postmark-Account-Token
        description: The token associated with the Account on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Servers
      - Serverid
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