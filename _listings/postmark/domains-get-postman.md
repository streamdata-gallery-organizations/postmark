{
  "info": {
    "name": "Postmark Account List Domains",
    "_postman_id": "53841473-d482-462d-8edd-9335ab1df33e",
    "description": "List domains.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Domains",
      "item": [
        {
          "id": "d22f2f6b-612c-43d0-b576-b1a1939b5f82",
          "name": "listDomains",
          "request": {
            "url": "http://api.postmarkapp.com/domains?count=%7B%7D&offset=%7B%7D",
            "method": "GET",
            "header": [
              {
                "key": "X-Postmark-Account-Token",
                "value": "{}",
                "description": "The token associated with the Account on which this request will operate",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "List domains."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "283c67f2-ad72-4670-9fd6-9665dc238d6e"
            }
          ]
        }
      ]
    }
  ]
}