---
name: whatsapp-marketing-manager
description: Manage WhatsApp marketing campaigns, including template selection, message sending, and performance tracking. Use for requests like "Send a promo to these users" or "Analyze campaign results".
---

# Whatsapp Marketing Manager

## Goal
To orchestrate effective marketing campaigns on the WhatsApp Business Platform, ensuring compliance with policies, optimizing for delivery, and tracking performance.

## Capabilities
1.  **Campaign Execution**: Send marketing template messages to lists of recipients.
2.  **Template Strategy**: Select appropriate rich media or carousel templates.
3.  **Optimization**: Configure pacing and delivery optimization.
4.  **Analytics**: Interpret delivery, read, and click-through metrics.

## Workflow

### 1. Campaign Setup
- **Identify Audience**: Ensure valid `wa_id`s (phone numbers with country code).
- **Select Template**: Must be a verified **Marketing** category template.
    - *Note*: Use `whatsapp-template-manager` skill to create/verify templates if needed.
- **Define Variables**: Map dynamic parameters (e.g., `{{1}}` for name, `{{2}}` for discount code).

### 2. Sending Messages
Use the `run_shell_command` to execute `curl` requests or a dedicated script.

**Endpoint**: `POST /<PHONE_NUMBER_ID>/messages` (or `/marketing_messages` for optimized delivery)

**Payload Structure**:
```json
{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "<PHONE_NUMBER>",
  "type": "template",
  "template": {
    "name": "<TEMPLATE_NAME>",
    "language": { "code": "<LANG_CODE>" },
    "components": [
      {
        "type": "header",
        "parameters": [{ "type": "image", "image": { "link": "<URL>" } }]
      },
      {
        "type": "body",
        "parameters": [{ "type": "text", "text": "<VARIABLE_VALUE>" }]
      }
    ]
  }
}
```

### 3. Optimization & Tracking
- **Pacing**: For large lists (>10k), use the `marketing_messages` endpoint to spread load.
- **Monitoring**: Check webhooks for `sent`, `delivered`, `read`, and `failed` statuses.

## Constraints
- **24h Window**: Marketing templates can be sent *outside* the 24h window.
- **Opt-in**: ONLY send to users who have explicitly opted in.
- **Quality**: High block rates will downgrade the phone number tier.

## Reference
- **Payloads**: See `references/marketing_payloads.md` for advanced structures (Carousels, CTAs).