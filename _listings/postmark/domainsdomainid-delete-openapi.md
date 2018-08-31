---
swagger: "2.0"
x-collection-name: Postmark
x-complete: 0
info:
  title: Postmark Account Delete a Domain
  description: Delete a domain.
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
  /email:
    parameters:
      summary: Parameters Email
      description: Parameters email.
      operationId: parametersEmail
      x-api-path-slug: email-parameters
      responses:
        200:
          description: OK
      tags:
      - Email
    post:
      summary: Post Email
      description: |-
        Sends e-mails. Currently Postmark supports JSON message format. The mail message format is:

        {
            "From" : "sender@example.com",
            "To" : "receiver@example.com",
            "Cc" : "copied@example.com",
            "Bcc": "blank-copied@example.com",
            "Subject" : "Test",
            "Tag" : "Invitation",
            "HtmlBody" : "Hello",
            "TextBody" : "Hello",
            "ReplyTo" : "reply@example.com",
            "Headers" : [{ "Name" : "CUSTOM-HEADER", "Value" : "value" }],
            "Attachments": [
                {
                     "Name": "readme.txt",
                     "Content": "dGVzdCBjb250ZW50",
                     "ContentType": "text/plain"
                },
                {
                    "Name": "report.pdf",
                    "Content": "dGVzdCBjb250ZW50",
                    "ContentType": "application/octet-stream"
                }
            ]
        }

        You should pass the json encoded message in the body of the request. Both from and to accept name, in the format of John Doe . You can provide HtmlBody for html formatted messages, TextBody for plain text, or both for multipart. Multipart sends html with a text version for clients that don???t support html. Passing headers is optional.

        1. You should have a registered and confirmed sender signature with the sender email. Otherwise you will receive HTTP Response 422 (Unprocessable Entity).
        2. It is possible to override the Name in the sender signature through the API. This is useful if you want to use member???s information in the email while keeping your from email address. just pass the name in the From parameter, From: "John Smith ".
        3. You can pass multiple recipient addresses in the ???To??? field and the optional ???Cc??? and ???Bcc??? fields. Separate multiple addresses with a comma. Note that Postmark has a limit of twenty recipients per message in total. You need to take care not to exceed that limit. Otherwise you will get an error.
        4. You can categorize outgoing email using the optional Tag property. If you use different tags for the different types of emails your application generates, you will be able to get detailed statistics for them through the Postmark user interface.

        Attachments
        Attachments are specified in the Attachments array property. An attachment is an object that has to provide the file name (via the Name property), the content type (ContentType property) and the actual binary data (Content property) that has to be sent with the message.

        The name is the actual file name that will be displayed to the message recipient. Note that the file extension is important. To eliminate the possibility of spreading viruses or spyware we allow only a number of file types. That is, instead of using a list of forbidden files and risking an unanticipated file type spreading infections, we have taken the opposite approach ??? we whitelist document file types that we are certain are safe. Here is the list of allowed files:

        - Media files: gif, jpg, jpeg, png, swf, flv, avi, mpg, mp3, mp4, ogv, wav, rm, mov, psd, ai, tif, tiff
        - Documents: txt, rtf, htm, html, pdf, epub, mobi, doc, docx, ppt, pptx, xls, xlsx, ps, eps, iif
        - Miscellaneous: log, csv, ics, xml, zip

        Contact us if you feel we need to whitelist a file that your application needs.

        The content type is the MIME content type that email clients use to interpret various attachments such as: text/plain, text/html, image/jpeg, etc. Your code can either detect it by the file extension, use a third party library to infer it, ask the user to provide it or just default to application/octet-stream.

        The binary data has to be transmitted as a base64-encoded string. Most programming languages and libraries have this built in e.g. Java, .NET, PHP, Ruby.

        You can use SSL encryption by issuing requests to https://api.postmarkapp.com/email.

        Success
        If all goes well, you will get back a JSON message looking a lot like:

        {
            "ErrorCode" : 0,
            "Message" : "OK",
            "MessageID" : "b7bc2f4a-e38e-4336-af7d-e6c392c2f817",
            "SubmittedAt" : "2010-11-26T12:01:05.1794748-05:00",
            "To" : "receiver@example.com"
        }

        Note the MessageID property. You can log it in your system and use it to associate the message you just sent to a possible bounce that you obtained from a bounce web hook or the bounce API.
      operationId: postEmail
      x-api-path-slug: email-post
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Email
  /email/batch:
    parameters:
      summary: Parameters Email Batch
      description: Parameters email batch.
      operationId: parametersEmailBatch
      x-api-path-slug: emailbatch-parameters
      responses:
        200:
          description: OK
      tags:
      - Email
      - Batch
    post:
      summary: Post Email Batch
      description: "While Postmark is focused on transactional email, we understand
        that developers with higher volumes or processing time constraints need to
        send their messages in batches. To facilitate this we provide a batching endpoint
        that permits you to send up to 500 well-formed Postmark messages in a single
        API call.\n                    \nThe format of the batched message is a JSON
        array containing multiple message requests like the following example:\n[\n
        \   {From: 'sender@example.com', To: 'receiver1@example.com', Subject: 'Postmark
        test #1', HtmlBody: 'Hello dear Postmark user.'},\n    {From: 'sender@example.com',
        To: 'receiver2@example.com', Subject: 'Postmark test #2', HtmlBody: 'Hello
        dear Postmark user.'}\n]\n\nYou can use SSL encryption by issuing requests
        to https://api.postmarkapp.com/email/batch.\n\nSimilarly, you will receive
        a matching JSON array containing each response for the messages you sent in
        your batched call:\n\n[\n    {\n        \"ErrorCode\" : 0,\n        \"Message\"
        : \"OK\",\n        \"MessageID\" : \"b7bc2f4a-e38e-4336-af7d-e6c392c2f817\",\n
        \       \"SubmittedAt\" : \"2010-11-26T12:01:05.1794748-05:00\",\n        \"To\"
        : \"receiver1@example.com\"\n    },\n    {\n        \"ErrorCode\" : 0,\n        \"Message\"
        : \"OK\",\n        \"MessageID\" : \"e2ecbbfc-fe12-463d-b933-9fe22915106d\",\n
        \       \"SubmittedAt\" : \"2010-11-26T12:01:05.1794748-05:00\",\n        \"To\"
        : \"receiver2@example.com\"\n    },\n]"
      operationId: postEmailBatch
      x-api-path-slug: emailbatch-post
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Email
      - Batch
  /deliverystats:
    parameters:
      summary: Parameters Deliverystats
      description: Parameters deliverystats.
      operationId: parametersDeliverystats
      x-api-path-slug: deliverystats-parameters
      responses:
        200:
          description: OK
      tags:
      - Deliverystats
    get:
      summary: Get Deliverystats
      description: Returns a summary of inactive emails and bounces by type.
      operationId: getDeliverystats
      x-api-path-slug: deliverystats-get
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Deliverystats
  /bounces:
    parameters:
      summary: Parameters Bounces
      description: Parameters bounces.
      operationId: parametersBounces
      x-api-path-slug: bounces-parameters
      responses:
        200:
          description: OK
      tags:
      - Bounces
    get:
      summary: Get Bounces
      description: 'Fetches a portion of bounces according to the specified input
        criteria. Supported filters: type, inactive, email like, tag. Paging: page_size
        (count), page_start (offset). Bounces are sorted by BouncedAt in a descending
        order.'
      operationId: getBounces
      x-api-path-slug: bounces-get
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: query
        name: count
        description: Number of bounces to return per request
      - in: query
        name: emailFilter
        description: Filter by email address
      - in: query
        name: fromdate
        description: Filter messages starting from the date specified
      - in: query
        name: inactive
        description: Filter by emails that were deactivated by Postmark due to the
          bounce
      - in: query
        name: messageID
        description: Filter by messageID
      - in: query
        name: offset
        description: Number of bounces to skip
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter messages up to the date specified
      - in: query
        name: type
        description: Filter by type of bounce
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Bounces
  /bounces/{bounceID}:
    parameters:
      summary: Parameters Bounces Bounce
      description: Parameters bounces bounce.
      operationId: parametersBouncesBounce
      x-api-path-slug: bouncesbounceid-parameters
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - BounceID
    get:
      summary: Get Bounces Bounce
      description: Gets details about a single bounce. Note that the bounce ID is
        a numeric value that you typically obtain after a getting a list of bounces.
      operationId: getBouncesBounce
      x-api-path-slug: bouncesbounceid-get
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: path
        name: bounceid
        description: The ID of the bounce to retrieve
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - BounceID
  /bounces/{bounceID}/dump:
    parameters:
      summary: Parameters Bounces Bounce Dump
      description: Parameters bounces bounce dump.
      operationId: parametersBouncesBounceDump
      x-api-path-slug: bouncesbounceiddump-parameters
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - BounceID
      - Dump
    get:
      summary: Get Bounces Bounce Dump
      description: Returns the raw source of the bounce we accepted. If Postmark does
        not have a dump for that bounce, it will return an empty string.
      operationId: getBouncesBounceDump
      x-api-path-slug: bouncesbounceiddump-get
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: path
        name: bounceid
        description: The ID for the bounce dump to retrieve
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - BounceID
      - Dump
  /bounces/tags:
    parameters:
      summary: Parameters Bounces Tags
      description: Parameters bounces tags.
      operationId: parametersBouncesTags
      x-api-path-slug: bouncestags-parameters
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - Tags
    get:
      summary: Get Bounces Tags
      description: Returns a list of tags used for the current server.
      operationId: getBouncesTags
      x-api-path-slug: bouncestags-get
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - Tags
  /bounces/{bounceID}/activate:
    parameters:
      summary: Parameters Bounces Bounce Activate
      description: Parameters bounces bounce activate.
      operationId: parametersBouncesBounceActivate
      x-api-path-slug: bouncesbounceidactivate-parameters
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - BounceID
      - Activate
    put:
      summary: Put Bounces Bounce Activate
      description: Activates a deactivated bounce. Note that you do not need to send
        anything in the request body.
      operationId: putBouncesBounceActivate
      x-api-path-slug: bouncesbounceidactivate-put
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: path
        name: bounceid
        description: The ID of the Bounce to activate
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Bounces
      - BounceID
      - Activate
  /server:
    parameters:
      summary: Parameters Server
      description: Parameters server.
      operationId: parametersServer
      x-api-path-slug: server-parameters
      responses:
        200:
          description: OK
      tags:
      - Server
    get:
      summary: Get Server
      description: Gets the server details and figures out your unique InboundHash
        where you can forward your email. This can be found in the web app in your
        server's Credentials tab or via the API.
      operationId: getServer
      x-api-path-slug: server-get
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: query
        name: Content-Type
        description: The content type of the request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Server
    post:
      summary: Post Server
      description: Sets the URL where we should send JSON data. In order for your
        application receive the emails that we parse, you will need to tell Postmark
        where to send the JSON data for each inbound email it processes, which is
        done via an HTTP POST to a URL of your choice. You can set this URL in the
        Settings page for your Postmark server in the web app, or using the InboundHookUrl
        field in the API. It also lets you choose a domain that you would like to
        listen on for incoming email to be processed by Postmark. We recommend a separate
        subdomain, like inbound.yourdomain.com. Each server can listen to one unique
        domain, so make sure to set the X-Postmark-Server-Token to the correct server
        token in the API call below.
      operationId: postServer
      x-api-path-slug: server-post
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: query
        name: Content-Type
        description: The content type of the request
      responses:
        200:
          description: OK
      tags:
      - Server
    put:
      summary: Put Server
      description: Put server.
      operationId: putServer
      x-api-path-slug: server-put
      parameters:
      - in: body
        name: body
        description: The settings that should be modified for the current server
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Server
  /email/withTemplate:
    post:
      summary: Post Email Withtemplate
      description: Post email withtemplate.
      operationId: postEmailWithtemplate
      x-api-path-slug: emailwithtemplate-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Email
      - WithTemplate
  /messages/inbound:
    get:
      summary: Get Messages Inbound
      description: Get messages inbound.
      operationId: getMessagesInbound
      x-api-path-slug: messagesinbound-get
      parameters:
      - in: query
        name: count
        description: Number of messages to return per request
      - in: query
        name: fromdate
        description: Filter messages starting from the date specified
      - in: query
        name: fromemail
        description: Filter by the sender email address
      - in: query
        name: mailboxhash
        description: Filter by mailboxhash
      - in: query
        name: offset
        description: Number of messages to skip
      - in: query
        name: recipient
        description: Filter by the user who was receiving the email
      - in: query
        name: status
        description: Filter by status (`blocked`, `processed`, `queued`, `failed`,
          `scheduled`)
      - in: query
        name: subject
        description: Filter by email subject
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter messages up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Inbound
  /messages/inbound/{messageid}/bypass:
    put:
      summary: Put Messages Inbound Message Bypass
      description: Put messages inbound message bypass.
      operationId: putMessagesInboundMessageBypass
      x-api-path-slug: messagesinboundmessageidbypass-put
      parameters:
      - in: path
        name: messageid
        description: The ID of the message which should bypass inbound rules
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Inbound
      - Messageid
      - Bypass
  /messages/inbound/{messageid}/details:
    get:
      summary: Get Messages Inbound Message Details
      description: Get messages inbound message details.
      operationId: getMessagesInboundMessageDetails
      x-api-path-slug: messagesinboundmessageiddetails-get
      parameters:
      - in: path
        name: messageid
        description: The ID of the message for which to details will be retrieved
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Inbound
      - Messageid
      - Details
  /messages/inbound/{messageid}/retry:
    put:
      summary: Put Messages Inbound Message Retry
      description: Put messages inbound message retry.
      operationId: putMessagesInboundMessageRetry
      x-api-path-slug: messagesinboundmessageidretry-put
      parameters:
      - in: path
        name: messageid
        description: The ID of the inbound message on which we should retry processing
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Inbound
      - Messageid
      - Retry
  /messages/outbound:
    get:
      summary: Get Messages Outbound
      description: Get messages outbound.
      operationId: getMessagesOutbound
      x-api-path-slug: messagesoutbound-get
      parameters:
      - in: query
        name: count
        description: Number of messages to return per request
      - in: query
        name: fromdate
        description: Filter messages starting from the date specified
      - in: query
        name: fromemail
        description: Filter by the sender email address
      - in: query
        name: offset
        description: Number of messages to skip
      - in: query
        name: recipient
        description: Filter by the user who was receiving the email
      - in: query
        name: status
        description: Filter by status (`queued` or `sent`)
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter messages up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Outbound
  /messages/outbound/clicks:
    get:
      summary: Get Messages Outbound Clicks
      description: Get messages outbound clicks.
      operationId: getMessagesOutboundClicks
      x-api-path-slug: messagesoutboundclicks-get
      parameters:
      - in: query
        name: city
        description: Filter by full name of region messages were opened in, i
      - in: query
        name: client_company
        description: Filter by company, i
      - in: query
        name: client_family
        description: Filter by client family, i
      - in: query
        name: client_name
        description: Filter by client name, i
      - in: query
        name: count
        description: Number of message clicks to return per request
      - in: query
        name: country
        description: Filter by country messages were opened in, i
      - in: query
        name: offset
        description: Number of messages to skip
      - in: query
        name: os_company
        description: Filter by company which produced the OS, i
      - in: query
        name: os_family
        description: Filter by kind of OS used without specific version, i
      - in: query
        name: os_name
        description: Filter by full OS name and specific version, i
      - in: query
        name: platform
        description: Filter by platform, i
      - in: query
        name: recipient
        description: Filter by To, Cc, Bcc
      - in: query
        name: region
        description: Filter by full name of region messages were opened in, i
      - in: query
        name: tag
        description: Filter by tag
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Outbound
      - Clicks
  /messages/outbound/clicks/{messageid}:
    get:
      summary: Get Messages Outbound Clicks Message
      description: Get messages outbound clicks message.
      operationId: getMessagesOutboundClicksMessage
      x-api-path-slug: messagesoutboundclicksmessageid-get
      parameters:
      - in: query
        name: count
        description: Number of message clicks to return per request
      - in: path
        name: messageid
        description: The ID of the Outbound Message for which click statistics should
          be retrieved
      - in: query
        name: offset
        description: Number of messages to skip
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Outbound
      - Clicks
      - Messageid
  /messages/outbound/opens:
    get:
      summary: Get Messages Outbound Opens
      description: Get messages outbound opens.
      operationId: getMessagesOutboundOpens
      x-api-path-slug: messagesoutboundopens-get
      parameters:
      - in: query
        name: city
        description: Filter by full name of region messages were opened in, i
      - in: query
        name: client_company
        description: Filter by company, i
      - in: query
        name: client_family
        description: Filter by client family, i
      - in: query
        name: client_name
        description: Filter by client name, i
      - in: query
        name: count
        description: Number of message opens to return per request
      - in: query
        name: country
        description: Filter by country messages were opened in, i
      - in: query
        name: offset
        description: Number of messages to skip
      - in: query
        name: os_company
        description: Filter by company which produced the OS, i
      - in: query
        name: os_family
        description: Filter by kind of OS used without specific version, i
      - in: query
        name: os_name
        description: Filter by full OS name and specific version, i
      - in: query
        name: platform
        description: Filter by platform, i
      - in: query
        name: recipient
        description: Filter by To, Cc, Bcc
      - in: query
        name: region
        description: Filter by full name of region messages were opened in, i
      - in: query
        name: tag
        description: Filter by tag
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Outbound
      - Opens
  /messages/outbound/opens/{messageid}:
    get:
      summary: Get Messages Outbound Opens Message
      description: Get messages outbound opens message.
      operationId: getMessagesOutboundOpensMessage
      x-api-path-slug: messagesoutboundopensmessageid-get
      parameters:
      - in: query
        name: count
        description: Number of message opens to return per request
      - in: path
        name: messageid
        description: The ID of the Outbound Message for which open statistics should
          be retrieved
      - in: query
        name: offset
        description: Number of messages to skip
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Outbound
      - Opens
      - Messageid
  /messages/outbound/{messageid}/details:
    get:
      summary: Get Messages Outbound Message Details
      description: Get messages outbound message details.
      operationId: getMessagesOutboundMessageDetails
      x-api-path-slug: messagesoutboundmessageiddetails-get
      parameters:
      - in: path
        name: messageid
        description: The ID of the message for which to retrieve details
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Outbound
      - Messageid
      - Details
  /messages/outbound/{messageid}/dump:
    get:
      summary: Get Messages Outbound Message Dump
      description: Get messages outbound message dump.
      operationId: getMessagesOutboundMessageDump
      x-api-path-slug: messagesoutboundmessageiddump-get
      parameters:
      - in: path
        name: messageid
        description: The ID of the message for which to retrieve a dump
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Messages
      - Outbound
      - Messageid
      - Dump
  /stats/outbound:
    get:
      summary: Get Stats Outbound
      description: Get stats outbound.
      operationId: getStatsOutbound
      x-api-path-slug: statsoutbound-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
  /stats/outbound/bounces:
    get:
      summary: Get Stats Outbound Bounces
      description: Get stats outbound bounces.
      operationId: getStatsOutboundBounces
      x-api-path-slug: statsoutboundbounces-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Bounces
  /stats/outbound/clicks:
    get:
      summary: Get Stats Outbound Clicks
      description: Get stats outbound clicks.
      operationId: getStatsOutboundClicks
      x-api-path-slug: statsoutboundclicks-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Clicks
  /stats/outbound/clicks/browserfamilies:
    get:
      summary: Get Stats Outbound Clicks Browserfamilies
      description: Get stats outbound clicks browserfamilies.
      operationId: getStatsOutboundClicksBrowserfamilies
      x-api-path-slug: statsoutboundclicksbrowserfamilies-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Clicks
      - Browserfamilies
  /stats/outbound/clicks/location:
    get:
      summary: Get Stats Outbound Clicks Location
      description: Get stats outbound clicks location.
      operationId: getStatsOutboundClicksLocation
      x-api-path-slug: statsoutboundclickslocation-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Clicks
      - Location
  /stats/outbound/clicks/platforms:
    get:
      summary: Get Stats Outbound Clicks Platforms
      description: Get stats outbound clicks platforms.
      operationId: getStatsOutboundClicksPlatforms
      x-api-path-slug: statsoutboundclicksplatforms-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Clicks
      - Platforms
  /stats/outbound/opens:
    get:
      summary: Get Stats Outbound Opens
      description: Get stats outbound opens.
      operationId: getStatsOutboundOpens
      x-api-path-slug: statsoutboundopens-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Opens
  /stats/outbound/opens/emailclients:
    get:
      summary: Get Stats Outbound Opens Emailclients
      description: Get stats outbound opens emailclients.
      operationId: getStatsOutboundOpensEmailclients
      x-api-path-slug: statsoutboundopensemailclients-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Opens
      - Emailclients
  /stats/outbound/opens/platforms:
    get:
      summary: Get Stats Outbound Opens Platforms
      description: Get stats outbound opens platforms.
      operationId: getStatsOutboundOpensPlatforms
      x-api-path-slug: statsoutboundopensplatforms-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Opens
      - Platforms
  /stats/outbound/opens/readtimes:
    get:
      summary: Get Stats Outbound Opens Readtimes
      description: Get stats outbound opens readtimes.
      operationId: getStatsOutboundOpensReadtimes
      x-api-path-slug: statsoutboundopensreadtimes-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Opens
      - Readtimes
  /stats/outbound/sends:
    get:
      summary: Get Stats Outbound Sends
      description: Get stats outbound sends.
      operationId: getStatsOutboundSends
      x-api-path-slug: statsoutboundsends-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Sends
  /stats/outbound/spam:
    get:
      summary: Get Stats Outbound Spam
      description: Get stats outbound spam.
      operationId: getStatsOutboundSpam
      x-api-path-slug: statsoutboundspam-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats up to the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Spam
  /stats/outbound/tracked:
    get:
      summary: Get Stats Outbound Tracked
      description: Get stats outbound tracked.
      operationId: getStatsOutboundTracked
      x-api-path-slug: statsoutboundtracked-get
      parameters:
      - in: query
        name: fromdate
        description: Filter stats starting from the date specified
      - in: query
        name: tag
        description: Filter by tag
      - in: query
        name: todate
        description: Filter stats starting from the date specified
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Stats
      - Outbound
      - Tracked
  /templates:
    get:
      summary: Get Templates
      description: Get templates.
      operationId: getTemplates
      x-api-path-slug: templates-get
      parameters:
      - in: query
        name: Count
        description: The number of Templates to return
      - in: query
        name: Offset
        description: The number of Templates to skip before returning results
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Templates
    post:
      summary: Post Templates
      description: Post templates.
      operationId: postTemplates
      x-api-path-slug: templates-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Templates
  /templates/validate:
    post:
      summary: Post Templates Valate
      description: Post templates valate.
      operationId: postTemplatesValate
      x-api-path-slug: templatesvalidate-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Templates
      - Validate
  /templates/{templateid}:
    delete:
      summary: Delete Templates Template
      description: Delete templates template.
      operationId: deleteTemplatesTemplate
      x-api-path-slug: templatestemplateid-delete
      parameters:
      - in: path
        name: templateid
        description: The ID for the Template you wish to delete
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Templates
      - Templateid
    get:
      summary: Get Templates Template
      description: Get templates template.
      operationId: getTemplatesTemplate
      x-api-path-slug: templatestemplateid-get
      parameters:
      - in: path
        name: templateid
        description: The ID for the Template you wish to retrieve
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Templates
      - Templateid
    put:
      summary: Put Templates Template
      description: Put templates template.
      operationId: putTemplatesTemplate
      x-api-path-slug: templatestemplateid-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: templateid
        description: The ID for the Template you wish to update
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Templates
      - Templateid
  /triggers/inboundrules:
    get:
      summary: Get Triggers Inboundrules
      description: Get triggers inboundrules.
      operationId: getTriggersInboundrules
      x-api-path-slug: triggersinboundrules-get
      parameters:
      - in: query
        name: count
        description: Number of records to return per request
      - in: query
        name: offset
        description: Number of records to skip
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Inboundrules
    post:
      summary: Post Triggers Inboundrules
      description: Post triggers inboundrules.
      operationId: postTriggersInboundrules
      x-api-path-slug: triggersinboundrules-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Inboundrules
  /triggers/inboundrules/{triggerid}:
    delete:
      summary: Delete Triggers Inboundrules Trigger
      description: Delete triggers inboundrules trigger.
      operationId: deleteTriggersInboundrulesTrigger
      x-api-path-slug: triggersinboundrulestriggerid-delete
      parameters:
      - in: path
        name: triggerid
        description: The ID of the Inbound Rule that should be deleted
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Inboundrules
      - Triggerid
  /triggers/tags:
    get:
      summary: Get Triggers Tags
      description: Get triggers tags.
      operationId: getTriggersTags
      x-api-path-slug: triggerstags-get
      parameters:
      - in: query
        name: count
        description: Number of records to return per request
      - in: query
        name: match_name
        description: Filter by delivery tag
      - in: query
        name: offset
        description: Number of records to skip
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Tags
    post:
      summary: Post Triggers Tags
      description: Post triggers tags.
      operationId: postTriggersTags
      x-api-path-slug: triggerstags-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Tags
  /triggers/tags/{triggerid}:
    delete:
      summary: Delete Triggers Tags Trigger
      description: Delete triggers tags trigger.
      operationId: deleteTriggersTagsTrigger
      x-api-path-slug: triggerstagstriggerid-delete
      parameters:
      - in: path
        name: triggerid
        description: The ID for the Tag Trigger that should be deleted
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Tags
      - Triggerid
    get:
      summary: Get Triggers Tags Trigger
      description: Get triggers tags trigger.
      operationId: getTriggersTagsTrigger
      x-api-path-slug: triggerstagstriggerid-get
      parameters:
      - in: path
        name: triggerid
        description: The ID for the Tag Trigger for which data should be retrieved
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Tags
      - Triggerid
    put:
      summary: Put Triggers Tags Trigger
      description: Put triggers tags trigger.
      operationId: putTriggersTagsTrigger
      x-api-path-slug: triggerstagstriggerid-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: triggerid
        description: The ID of the Tag Trigger that should be modified by this request
      - in: header
        name: X-Postmark-Server-Token
        description: The token associated with the Server on which this request will
          operate
      responses:
        200:
          description: OK
      tags:
      - Triggers
      - Tags
      - Triggerid
  /filter:
    post:
      summary: Post Filter
      description: 'Postmark???s spam API is a RESTfull interface to the Spam filter
        tool SpamAssassin (http://spamassassin.apache.org/). This can be used to pre
        or post process email content when it is used in your application. For instance,
        if you process incoming emails from your users you can first run it through
        the API to filter out junk and avoid clutter in your database and application.
        Keep in mind: This is free to use and may be updated, removed or changed at
        any time. For a detailed explanation of the report generated, as well as the
        test definitions, please visit the SpamAssassin test repository (http://spamassassin.apache.org/tests_3_3_x.html).
        The POST body must have an element "email" which is the raw dump of the email
        to be filtered, including all headers. And an element "options" which must
        either be "long" for a full report of processing rules, or "short" for a score
        request.'
      operationId: postFilter
      x-api-path-slug: filter-post
      parameters:
      - in: query
        name: Accept
        description: The accepted type for the response
      - in: query
        name: Content-Type
        description: The content type of the request
      responses:
        200:
          description: OK
      tags:
      - Filter
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