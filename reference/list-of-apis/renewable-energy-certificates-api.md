---
description: >-
  This API provides comprehensive data about Filecoin Storage Providers
  renewable energy purchases and consumption.
---

# 📈 Renewable Energy Certificates API

## Filecoin Storage Providers with RECs purchases

Listing all Filecoin Storage Providers who has purchased and consumed RECs.

{% swagger method="get" path="" baseUrl="https://proofs-api.zerolabs.green/api/partners/filecoin/nodes" summary="List Filecoin Storage Providers with purchased and consumed RECs" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="JSON response" %}
```javascript
[
  {
    "id": "f01051178",
    "buyerId": "6f48fb1a-5c54-4067-9ad3-430e24c506ec",
    "blockchainAddress": null,
    "createdAt": "2022-02-07T15:52:00.419Z",
    "updatedAt": "2022-02-07T15:52:00.419Z"
  },
  {
    "id": "f066596",
    "buyerId": "53fb6148-eb21-42de-91d6-f6195d028520",
    "blockchainAddress": null,
    "createdAt": "2022-02-07T15:52:00.419Z",
    "updatedAt": "2022-02-07T15:52:00.419Z"
  },
  {
    "id": "f0763337",
    "buyerId": "53fb6148-eb21-42de-91d6-f6195d028520",
    "blockchainAddress": null,
    "createdAt": "2022-02-07T15:52:00.419Z",
    "updatedAt": "2022-02-07T15:52:00.419Z"
  }
]
```
{% endswagger-response %}
{% endswagger %}
