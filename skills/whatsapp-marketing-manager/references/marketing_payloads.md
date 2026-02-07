# Marketing Message Payloads

## 1. Standard Marketing Template
```json
{
  "messaging_product": "whatsapp",
  "to": "{{PHONE_NUMBER}}",
  "type": "template",
  "template": {
    "name": "seasonal_promo",
    "language": { "code": "en_US" },
    "components": [
      {
        "type": "header",
        "parameters": [
          {
            "type": "image",
            "image": { "link": "https://example.com/banner.png" }
          }
        ]
      },
      {
        "type": "body",
        "parameters": [
          { "type": "text", "text": "Leo" },
          { "type": "text", "text": "20%" }
        ]
      }
    ]
  }
}
```

## 2. Marketing with Carousel (Media Cards)
*As seen in `graph-api.js` `messageWithMediaCardCarousel`*

```json
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "{{PHONE_NUMBER}}",
  "type": "template",
  "template": {
    "name": "recipe_media_carousel",
    "language": { "code": "en_US" },
    "components": [
      {
        "type": "carousel",
        "cards": [
          {
            "card_index": 0,
            "components": [
              {
                "type": "header",
                "parameters": [
                  { "type": "image", "image": { "link": "https://scontent.xx.fbcdn.net/..." } }
                ]
              }
            ]
          },
          {
            "card_index": 1,
            "components": [
              {
                "type": "header",
                "parameters": [
                  { "type": "image", "image": { "link": "https://scontent.xx.fbcdn.net/..." } }
                ]
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## 3. Limited Time Offer (With Expiration)
*As seen in `graph-api.js` `messageWithLimitedTimeOfferTemplate`*

```json
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "{{PHONE_NUMBER}}",
  "type": "template",
  "template": {
    "name": "strawberries_limited_offer",
    "language": { "code": "en_US" },
    "components": [
      {
        "type": "header",
        "parameters": [
          { "type": "image", "image": { "link": "https://scontent.xx.fbcdn.net/..." } }
        ]
      },
      {
        "type": "limited_time_offer",
        "parameters": [
          {
            "type": "limited_time_offer",
            "limited_time_offer": {
              "expiration_time_ms": 1700000000000 // Epoch in MS
            }
          }
        ]
      },
      {
        "type": "button",
        "sub_type": "copy_code",
        "index": 0,
        "parameters": [
          { "type": "coupon_code", "coupon_code": "BERRIES20" }
        ]
      }
    ]
  }
}
```

## 4. Interactive Reply Buttons (Contextual)
*As seen in `graph-api.js` `messageWithInteractiveReply`*

```json
{
  "messaging_product": "whatsapp",
  "to": "{{PHONE_NUMBER}}",
  "type": "interactive",
  "interactive": {
    "type": "button",
    "body": { "text": "Welcome to Jasper's Market! What can we help you with today?" },
    "action": {
      "buttons": [
        {
          "type": "reply",
          "reply": { "id": "reply-interactive-with-media", "title": "Shop online" }
        },
        {
          "type": "reply",
          "reply": { "id": "reply-media-card-carousel", "title": "Get recipe ideas" }
        },
        {
          "type": "reply",
          "reply": { "id": "reply-offer", "title": "Current promo" }
        }
      ]
    }
  }
}
```