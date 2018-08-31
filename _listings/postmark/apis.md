---
name: Postmark
x-slug: postmark
description: Trusted by thousands of developers, Postmark is a fast and reliable transactional
  email service. Send with Postmark to ensure your transactional emails get to the
  inbox on time, every time.
image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
x-kinRank: "8"
x-alexaRank: "87545"
tags: Postmark
created: "2018-08-30"
modified: "2018-08-30"
url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/apis.md
specificationVersion: "0.14"
apis:
- name: Postmark - Parameters Email
  x-api-slug: email-parameters
  description: Parameters email.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/email-parameters-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/email-parameters-openapi.md
- name: Postmark - Post Email
  x-api-slug: email-post
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
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/email-post-openapi.md
- name: Postmark - Parameters Email Batch
  x-api-slug: emailbatch-parameters
  description: Parameters email batch.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/emailbatch-parameters-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/emailbatch-parameters-openapi.md
- name: Postmark - Post Email Batch
  x-api-slug: emailbatch-post
  description: "While Postmark is focused on transactional email, we understand that
    developers with higher volumes or processing time constraints need to send their
    messages in batches. To facilitate this we provide a batching endpoint that permits
    you to send up to 500 well-formed Postmark messages in a single API call.\n                    \nThe
    format of the batched message is a JSON array containing multiple message requests
    like the following example:\n[\n    {From: 'sender@example.com', To: 'receiver1@example.com',
    Subject: 'Postmark test #1', HtmlBody: 'Hello dear Postmark user.'},\n    {From:
    'sender@example.com', To: 'receiver2@example.com', Subject: 'Postmark test #2',
    HtmlBody: 'Hello dear Postmark user.'}\n]\n\nYou can use SSL encryption by issuing
    requests to https://api.postmarkapp.com/email/batch.\n\nSimilarly, you will receive
    a matching JSON array containing each response for the messages you sent in your
    batched call:\n\n[\n    {\n        \"ErrorCode\" : 0,\n        \"Message\" : \"OK\",\n
    \       \"MessageID\" : \"b7bc2f4a-e38e-4336-af7d-e6c392c2f817\",\n        \"SubmittedAt\"
    : \"2010-11-26T12:01:05.1794748-05:00\",\n        \"To\" : \"receiver1@example.com\"\n
    \   },\n    {\n        \"ErrorCode\" : 0,\n        \"Message\" : \"OK\",\n        \"MessageID\"
    : \"e2ecbbfc-fe12-463d-b933-9fe22915106d\",\n        \"SubmittedAt\" : \"2010-11-26T12:01:05.1794748-05:00\",\n
    \       \"To\" : \"receiver2@example.com\"\n    },\n]"
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/emailbatch-post-openapi.md
- name: Postmark - Parameters Deliverystats
  x-api-slug: deliverystats-parameters
  description: Parameters deliverystats.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/deliverystats-parameters-openapi.md
- name: Postmark - Get Deliverystats
  x-api-slug: deliverystats-get
  description: Returns a summary of inactive emails and bounces by type.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/deliverystats-get-openapi.md
- name: Postmark - Parameters Bounces
  x-api-slug: bounces-parameters
  description: Parameters bounces.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bounces-parameters-openapi.md
- name: Postmark - Get Bounces
  x-api-slug: bounces-get
  description: 'Fetches a portion of bounces according to the specified input criteria.
    Supported filters: type, inactive, email like, tag. Paging: page_size (count),
    page_start (offset). Bounces are sorted by BouncedAt in a descending order.'
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bounces-get-openapi.md
- name: Postmark - Parameters Bounces Bounce
  x-api-slug: bouncesbounceid-parameters
  description: Parameters bounces bounce.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncesbounceid-parameters-openapi.md
- name: Postmark - Get Bounces Bounce
  x-api-slug: bouncesbounceid-get
  description: Gets details about a single bounce. Note that the bounce ID is a numeric
    value that you typically obtain after a getting a list of bounces.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncesbounceid-get-openapi.md
- name: Postmark - Parameters Bounces Bounce Dump
  x-api-slug: bouncesbounceiddump-parameters
  description: Parameters bounces bounce dump.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncesbounceiddump-parameters-openapi.md
- name: Postmark - Get Bounces Bounce Dump
  x-api-slug: bouncesbounceiddump-get
  description: Returns the raw source of the bounce we accepted. If Postmark does
    not have a dump for that bounce, it will return an empty string.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncesbounceiddump-get-openapi.md
- name: Postmark - Parameters Bounces Tags
  x-api-slug: bouncestags-parameters
  description: Parameters bounces tags.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncestags-parameters-openapi.md
- name: Postmark - Get Bounces Tags
  x-api-slug: bouncestags-get
  description: Returns a list of tags used for the current server.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncestags-get-openapi.md
- name: Postmark - Parameters Bounces Bounce Activate
  x-api-slug: bouncesbounceidactivate-parameters
  description: Parameters bounces bounce activate.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncesbounceidactivate-parameters-openapi.md
- name: Postmark - Put Bounces Bounce Activate
  x-api-slug: bouncesbounceidactivate-put
  description: Activates a deactivated bounce. Note that you do not need to send anything
    in the request body.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/bouncesbounceidactivate-put-openapi.md
- name: Postmark - Parameters Server
  x-api-slug: server-parameters
  description: Parameters server.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/server-parameters-openapi.md
- name: Postmark - Get Server
  x-api-slug: server-get
  description: Gets the server details and figures out your unique InboundHash where
    you can forward your email. This can be found in the web app in your server's
    Credentials tab or via the API.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/server-get-openapi.md
- name: Postmark - Post Server
  x-api-slug: server-post
  description: Sets the URL where we should send JSON data. In order for your application
    receive the emails that we parse, you will need to tell Postmark where to send
    the JSON data for each inbound email it processes, which is done via an HTTP POST
    to a URL of your choice. You can set this URL in the Settings page for your Postmark
    server in the web app, or using the InboundHookUrl field in the API. It also lets
    you choose a domain that you would like to listen on for incoming email to be
    processed by Postmark. We recommend a separate subdomain, like inbound.yourdomain.com.
    Each server can listen to one unique domain, so make sure to set the X-Postmark-Server-Token
    to the correct server token in the API call below.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/server-post-openapi.md
- name: Postmark - Post Email Withtemplate
  x-api-slug: emailwithtemplate-post
  description: Post email withtemplate.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/emailwithtemplate-post-openapi.md
- name: Postmark - Get Messages Inbound
  x-api-slug: messagesinbound-get
  description: Get messages inbound.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesinbound-get-openapi.md
- name: Postmark - Put Messages Inbound Message Bypass
  x-api-slug: messagesinboundmessageidbypass-put
  description: Put messages inbound message bypass.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesinboundmessageidbypass-put-openapi.md
- name: Postmark - Get Messages Inbound Message Details
  x-api-slug: messagesinboundmessageiddetails-get
  description: Get messages inbound message details.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesinboundmessageiddetails-get-openapi.md
- name: Postmark - Put Messages Inbound Message Retry
  x-api-slug: messagesinboundmessageidretry-put
  description: Put messages inbound message retry.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesinboundmessageidretry-put-openapi.md
- name: Postmark - Get Messages Outbound
  x-api-slug: messagesoutbound-get
  description: Get messages outbound.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesoutbound-get-openapi.md
- name: Postmark - Get Messages Outbound Clicks
  x-api-slug: messagesoutboundclicks-get
  description: Get messages outbound clicks.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesoutboundclicks-get-openapi.md
- name: Postmark - Get Messages Outbound Clicks Message
  x-api-slug: messagesoutboundclicksmessageid-get
  description: Get messages outbound clicks message.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesoutboundclicksmessageid-get-openapi.md
- name: Postmark - Get Messages Outbound Opens
  x-api-slug: messagesoutboundopens-get
  description: Get messages outbound opens.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesoutboundopens-get-openapi.md
- name: Postmark - Get Messages Outbound Opens Message
  x-api-slug: messagesoutboundopensmessageid-get
  description: Get messages outbound opens message.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesoutboundopensmessageid-get-openapi.md
- name: Postmark - Get Messages Outbound Message Details
  x-api-slug: messagesoutboundmessageiddetails-get
  description: Get messages outbound message details.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesoutboundmessageiddetails-get-openapi.md
- name: Postmark - Get Messages Outbound Message Dump
  x-api-slug: messagesoutboundmessageiddump-get
  description: Get messages outbound message dump.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/messagesoutboundmessageiddump-get-openapi.md
- name: Postmark - Put Server
  x-api-slug: server-put
  description: Put server.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/server-put-openapi.md
- name: Postmark - Get Stats Outbound
  x-api-slug: statsoutbound-get
  description: Get stats outbound.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutbound-get-openapi.md
- name: Postmark - Get Stats Outbound Bounces
  x-api-slug: statsoutboundbounces-get
  description: Get stats outbound bounces.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundbounces-get-openapi.md
- name: Postmark - Get Stats Outbound Clicks
  x-api-slug: statsoutboundclicks-get
  description: Get stats outbound clicks.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundclicks-get-openapi.md
- name: Postmark - Get Stats Outbound Clicks Browserfamilies
  x-api-slug: statsoutboundclicksbrowserfamilies-get
  description: Get stats outbound clicks browserfamilies.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundclicksbrowserfamilies-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundclicksbrowserfamilies-get-openapi.md
- name: Postmark - Get Stats Outbound Clicks Location
  x-api-slug: statsoutboundclickslocation-get
  description: Get stats outbound clicks location.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundclickslocation-get-openapi.md
- name: Postmark - Get Stats Outbound Clicks Platforms
  x-api-slug: statsoutboundclicksplatforms-get
  description: Get stats outbound clicks platforms.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundclicksplatforms-get-openapi.md
- name: Postmark - Get Stats Outbound Opens
  x-api-slug: statsoutboundopens-get
  description: Get stats outbound opens.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundopens-get-openapi.md
- name: Postmark - Get Stats Outbound Opens Emailclients
  x-api-slug: statsoutboundopensemailclients-get
  description: Get stats outbound opens emailclients.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundopensemailclients-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundopensemailclients-get-openapi.md
- name: Postmark - Get Stats Outbound Opens Platforms
  x-api-slug: statsoutboundopensplatforms-get
  description: Get stats outbound opens platforms.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundopensplatforms-get-openapi.md
- name: Postmark - Get Stats Outbound Opens Readtimes
  x-api-slug: statsoutboundopensreadtimes-get
  description: Get stats outbound opens readtimes.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundopensreadtimes-get-openapi.md
- name: Postmark - Get Stats Outbound Sends
  x-api-slug: statsoutboundsends-get
  description: Get stats outbound sends.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundsends-get-openapi.md
- name: Postmark - Get Stats Outbound Spam
  x-api-slug: statsoutboundspam-get
  description: Get stats outbound spam.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundspam-get-openapi.md
- name: Postmark - Get Stats Outbound Tracked
  x-api-slug: statsoutboundtracked-get
  description: Get stats outbound tracked.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/statsoutboundtracked-get-openapi.md
- name: Postmark - Get Templates
  x-api-slug: templates-get
  description: Get templates.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/templates-get-openapi.md
- name: Postmark - Post Templates
  x-api-slug: templates-post
  description: Post templates.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/templates-post-openapi.md
- name: Postmark - Post Templates Valate
  x-api-slug: templatesvalidate-post
  description: Post templates valate.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/templatesvalidate-post-openapi.md
- name: Postmark - Delete Templates Template
  x-api-slug: templatestemplateid-delete
  description: Delete templates template.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/templatestemplateid-delete-openapi.md
- name: Postmark - Get Templates Template
  x-api-slug: templatestemplateid-get
  description: Get templates template.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/templatestemplateid-get-openapi.md
- name: Postmark - Put Templates Template
  x-api-slug: templatestemplateid-put
  description: Put templates template.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/templatestemplateid-put-openapi.md
- name: Postmark - Get Triggers Inboundrules
  x-api-slug: triggersinboundrules-get
  description: Get triggers inboundrules.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggersinboundrules-get-openapi.md
- name: Postmark - Post Triggers Inboundrules
  x-api-slug: triggersinboundrules-post
  description: Post triggers inboundrules.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggersinboundrules-post-openapi.md
- name: Postmark - Delete Triggers Inboundrules Trigger
  x-api-slug: triggersinboundrulestriggerid-delete
  description: Delete triggers inboundrules trigger.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggersinboundrulestriggerid-delete-openapi.md
- name: Postmark - Get Triggers Tags
  x-api-slug: triggerstags-get
  description: Get triggers tags.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggerstags-get-openapi.md
- name: Postmark - Post Triggers Tags
  x-api-slug: triggerstags-post
  description: Post triggers tags.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggerstags-post-openapi.md
- name: Postmark - Delete Triggers Tags Trigger
  x-api-slug: triggerstagstriggerid-delete
  description: Delete triggers tags trigger.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggerstagstriggerid-delete-openapi.md
- name: Postmark - Get Triggers Tags Trigger
  x-api-slug: triggerstagstriggerid-get
  description: Get triggers tags trigger.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggerstagstriggerid-get-openapi.md
- name: Postmark - Put Triggers Tags Trigger
  x-api-slug: triggerstagstriggerid-put
  description: Put triggers tags trigger.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/triggerstagstriggerid-put-openapi.md
- name: Postmark - Post Filter
  x-api-slug: filter-post
  description: 'Postmark???s spam API is a RESTfull interface to the Spam filter tool
    SpamAssassin (http://spamassassin.apache.org/). This can be used to pre or post
    process email content when it is used in your application. For instance, if you
    process incoming emails from your users you can first run it through the API to
    filter out junk and avoid clutter in your database and application. Keep in mind:
    This is free to use and may be updated, removed or changed at any time. For a
    detailed explanation of the report generated, as well as the test definitions,
    please visit the SpamAssassin test repository (http://spamassassin.apache.org/tests_3_3_x.html).
    The POST body must have an element "email" which is the raw dump of the email
    to be filtered, including all headers. And an element "options" which must either
    be "long" for a full report of processing rules, or "short" for a score request.'
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://spamcheck.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/filter-post-openapi.md
- name: Postmark Account-level - List Domains
  x-api-slug: domains-get
  description: List domains.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-postman-collection
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domains-get-postman.md
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domains-get-openapi.md
- name: Postmark Account-level - Create a Domain
  x-api-slug: domains-post
  description: Create a domain.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domains-post-openapi.md
- name: Postmark Account-level - Delete a Domain
  x-api-slug: domainsdomainid-delete
  description: Delete a domain.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domainsdomainid-delete-openapi.md
- name: Postmark Account-level - Get a Domain
  x-api-slug: domainsdomainid-get
  description: Get a domain.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domainsdomainid-get-openapi.md
- name: Postmark Account-level - Update a Domain
  x-api-slug: domainsdomainid-put
  description: Update a domain.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domainsdomainid-put-openapi.md
- name: Postmark Account-level - Rotate DKIM Key
  x-api-slug: domainsdomainidrotatedkim-post
  description: "Creates a new DKIM key to replace your current key. Until the DNS
    entries are confirmed, \nthe new values will be in the `DKIMPendingHost` and `DKIMPendingTextValue`
    fields. \nAfter the new DKIM value is verified in DNS, the pending values will
    migrate to \n`DKIMTextValue` and `DKIMPendingTextValue` and Postmark will begin
    to sign emails \nwith the new DKIM key."
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domainsdomainidrotatedkim-post-openapi.md
- name: Postmark Account-level - Request DNS Verification for SPF
  x-api-slug: domainsdomainidverifyspf-post
  description: Request dns verification for spf.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/domainsdomainidverifyspf-post-openapi.md
- name: Postmark Account-level - List Sender Signatures
  x-api-slug: senders-get
  description: List sender signatures.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senders-get-openapi.md
- name: Postmark Account-level - Create a Sender Signature
  x-api-slug: senders-post
  description: Create a sender signature.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senders-post-openapi.md
- name: Postmark Account-level - Delete a Sender Signature
  x-api-slug: senderssignatureid-delete
  description: Delete a sender signature.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senderssignatureid-delete-openapi.md
- name: Postmark Account-level - Get a Sender Signature
  x-api-slug: senderssignatureid-get
  description: Get a sender signature.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senderssignatureid-get-openapi.md
- name: Postmark Account-level - Update a Sender Signature
  x-api-slug: senderssignatureid-put
  description: Update a sender signature.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senderssignatureid-put-openapi.md
- name: Postmark Account-level - Request a new DKIM Key
  x-api-slug: senderssignatureidrequestnewdkim-post
  description: "Requests a new DKIM key to be created. Until the DNS entries are confirmed,
    \nthe new values will be in the `DKIMPendingHost` and `DKIMPendingTextValue` fields.
    \nAfter the new DKIM value is verified in DNS, the pending values will migrate
    to \n`DKIMTextValue` and `DKIMPendingTextValue` and Postmark will begin to sign
    emails \nwith the new DKIM key."
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senderssignatureidrequestnewdkim-post-openapi.md
- name: Postmark Account-level - Resend Signature Confirmation Email
  x-api-slug: senderssignatureidresend-post
  description: Resend signature confirmation email.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senderssignatureidresend-post-openapi.md
- name: Postmark Account-level - Request DNS Verification for SPF
  x-api-slug: senderssignatureidverifyspf-post
  description: Request dns verification for spf.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/senderssignatureidverifyspf-post-openapi.md
- name: Postmark Account-level - List servers
  x-api-slug: servers-get
  description: List servers.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/servers-get-openapi.md
- name: Postmark Account-level - Create a Server
  x-api-slug: servers-post
  description: Create a server.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/servers-post-openapi.md
- name: Postmark Account-level - Delete a Server
  x-api-slug: serversserverid-delete
  description: Delete a server.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/serversserverid-delete-openapi.md
- name: Postmark Account-level - Get a Server
  x-api-slug: serversserverid-get
  description: Get a server.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/serversserverid-get-openapi.md
- name: Postmark Account-level - Edit a Server
  x-api-slug: serversserverid-put
  description: Edit a server.
  image: http://kinlane-productions.s3.amazonaws.com/screen-capture-api/638-postmark.jpg
  humanURL: http://postmarkapp.com
  baseURL: https://api.postmarkapp.com//
  tags: Target, Imports, Stack Network, Technology, SaaS, Emails, Messages, Relative
    Data, Service API, Relative StreamRank, Streams, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/postmark/master/_listings/postmark/serversserverid-put-openapi.md
x-common:
- type: x--net-library
  url: http://developer.postmarkapp.com/developer-official-libs.html#dot-net
- type: x-api-gallery
  url: http://polygon.api.gallery.streamdata.io
- type: x-api-stack
  url: http://postmark.stack.network
- type: x-base
  url: https://api.postmarkapp.com
- type: x-blog
  url: http://blog.postmarkapp.com/
- type: x-blog-rss
  url: http://blog.postmarkapp.com/rss
- type: x-contact-form
  url: http://support.postmarkapp.com/customer/portal/emails/new
- type: x-crunchbase
  url: https://crunchbase.com/organization/postmark
- type: x-crunchbase
  url: http://www.crunchbase.com/company/postmark
- type: x-developer
  url: http://developer.postmarkapp.com/
- type: x-email
  url: support@postmarkapp.com
- type: x-email
  url: 451d9b70cf9364d23ff6f9d51d870251569e+ahoy@inbound.postmarkapp.com
- type: x-faq
  url: http://support.postmarkapp.com/
- type: x-pricing
  url: http://developer.postmarkapp.com/developer-api-messages.html
- type: x-privacy
  url: https://postmarkapp.com/privacy-policy
- type: x-ruby-library
  url: http://developer.postmarkapp.com/developer-official-libs.html#rails
- type: x-ruby-library
  url: http://developer.postmarkapp.com/developer-official-libs.html#ruby
- type: x-selfservice-registration
  url: https://postmarkapp.com/sign_up
- type: x-status
  url: http://status.postmarkapp.com/
- type: x-terms-of-service
  url: https://postmarkapp.com/terms-of-service
- type: x-twitter
  url: https://twitter.com/postmarkapp
- type: x-webhook
  url: https://postmarkapp.com/developer/webhooks/webhooks-overview
- type: x-website
  url: http://postmarkapp.com
- type: x-website
  url: http://postmarkapp.com/
- type: x-website
  url: https://postmarkapp.com
- type: x-wordpress-pdk
  url: http://developer.postmarkapp.com/developer-official-libs.html#wordpress
include: []
maintainers:
- FN: Kin Lane
  x-twitter: apievangelist
  email: info@apievangelist.com
---