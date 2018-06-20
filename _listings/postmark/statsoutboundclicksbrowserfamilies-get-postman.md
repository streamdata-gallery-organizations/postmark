{
  "info": {
    "name": "Postmark Get Stats Outbound Clicks Browserfamilies",
    "_postman_id": "057760c0-4539-4543-8cfe-c430d9bffe96",
    "description": "Get stats outbound clicks browserfamilies.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Stats",
      "item": [
        {
          "id": "1140af60-55cb-4c06-80d8-db3af995ce17",
          "name": "getStatsOutboundClicksBrowserfamilies",
          "request": {
            "url": "http://spamcheck.postmarkapp.com/stats/outbound/clicks/browserfamilies?fromdate=%7B%7D&tag=%7B%7D&todate=%7B%7D",
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
            "description": "Get stats outbound clicks browserfamilies."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "3d048464-9089-449a-857a-24343d9031e5"
            }
          ]
        }
      ]
    }
  ]
}