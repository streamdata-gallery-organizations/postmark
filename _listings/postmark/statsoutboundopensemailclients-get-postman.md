{
  "info": {
    "name": "Postmark Get Stats Outbound Opens Emailclients",
    "_postman_id": "d02ffb06-c1d8-40a6-9822-b567616849a7",
    "description": "Get stats outbound opens emailclients.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Stats",
      "item": [
        {
          "id": "390ab78c-5c20-4fa6-ac05-087a7e2f2589",
          "name": "getStatsOutboundOpensEmailclients",
          "request": {
            "url": "http://spamcheck.postmarkapp.com/stats/outbound/opens/emailclients?fromdate=%7B%7D&tag=%7B%7D&todate=%7B%7D",
            "method": "GET",
            "header": [
              {
                "key": "X-Postmark-Server-Token",
                "value": "{}",
                "description": "The token associated with the Server on which this request will operate",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "Get stats outbound opens emailclients."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "2cd53853-bbe1-4052-8f99-78b75eab42be"
            }
          ]
        }
      ]
    }
  ]
}