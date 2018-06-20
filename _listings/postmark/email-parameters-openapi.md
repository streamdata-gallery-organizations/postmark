---
swagger: "2.0"
x-collection-name: Postmark
x-complete: 0
info:
  title: Postmark Parameters Email
  description: Parameters email.
  version: 1.0.0
host: spamcheck.postmarkapp.com
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