# Webhook Payload Examples

## 1. Incoming Text Message
```json
{
  "object": "whatsapp_business_account",
  "entry": [{
    "id": "WABA_ID",
    "changes": [{
      "value": {
        "messaging_product": "whatsapp",
        "metadata": { "display_phone_number": "12345", "phone_number_id": "PN_ID" },
        "contacts": [{ "profile": { "name": "Leo" }, "wa_id": "15550109999" }],
        "messages": [{
          "from": "15550109999",
          "id": "MSG_ID",
          "timestamp": "1665012345",
          "text": { "body": "Hello!" },
          "type": "text"
        }]
      },
      "field": "messages"
    }]
  }]
}
```

## 2. Message Status (Delivered/Read)
```json
{
  "entry": [{
    "changes": [{
      "value": {
        "statuses": [{
          "id": "MSG_ID",
          "status": "delivered",
          "timestamp": "1665012350",
          "recipient_id": "15550109999",
          "conversation": { "id": "CONV_ID", "origin": { "type": "marketing" } },
          "pricing": { "billable": true, "pricing_model": "CBP", "category": "marketing" }
        }]
      }
    }]
  }]
}
```

## 3. Template Status Update (Account Event)
```json
{
  "entry": [{
    "changes": [{
      "value": {
        "event": "APPROVED",
        "message_template_id": "123",
        "message_template_name": "seasonal_promo",
        "message_template_language": "en_US",
        "reason": null
      },
      "field": "message_template_status_update"
    }]
  }]
}
```
