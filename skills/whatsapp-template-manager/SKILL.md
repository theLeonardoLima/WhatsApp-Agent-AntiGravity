---
name: whatsapp-template-manager
description: Create, update, and manage WhatsApp message templates. Use for tasks like "Create a new coupon template" or "Check why my template was rejected".
---

# Whatsapp Template Manager

## Goal
To manage the lifecycle of WhatsApp message templates, ensuring they are correctly categorized, meet component requirements, and maintain high quality ratings.

## Capabilities
1.  **Template Creation**: Define Marketing, Utility, or Authentication templates.
2.  **Category Management**: Ensure templates are assigned the correct category to avoid rejection.
3.  **Status Monitoring**: Monitor for `APPROVED`, `REJECTED`, or `PAUSED` statuses via API or webhooks.
4.  **Advanced Components**: Implement carousels, limited-time offers, and interactive buttons.

## Workflow

### 1. Planning a Template
- **Category**:
    - **Marketing**: Promotions, mixed content.
    - **Utility**: Order updates, post-purchase (Non-promotional).
    - **Authentication**: OTPs (Use Template Library patterns).
- **TTL (Time-To-Live)**: Set based on urgency (e.g., 10m for OTP, 48h for Promo).

### 2. Implementation
**Endpoint**: `POST /<WABA_ID>/message_templates`

**Component Structure Example (Limited-Time Offer)**:
```json
{
  "name": "flash_sale_v1",
  "category": "MARKETING",
  "language": "en_US",
  "components": [
    {
      "type": "HEADER",
      "format": "IMAGE",
      "example": { "header_handle": ["<HANDLE>"] }
    },
    {
      "type": "BODY",
      "text": "Get {{1}}% off for a limited time!",
      "example": { "body_text": [["20"]] }
    },
    {
      "type": "LIMITED_TIME_OFFER",
      "limited_time_offer": { "has_expiration": true }
    },
    {
      "type": "BUTTONS",
      "buttons": [
        { "type": "COPY_CODE", "example": "SAVE20" }
      ]
    }
  ]
}
```

### 3. Handling Rejections/Pausing
- **Rejection**: Check for positional parameter errors (must be sequential `{{1}}`, `{{2}}`) or policy violations.
- **Pausing**: If a template is `PAUSED` due to low quality (`RED`), edit it to improve clarity or relevance. This re-triggers review.

## Constraints
- **Character Limits**: Header (60), Body (1024), Footer (60).
- **Editing limits**: Approved templates can be edited 10 times in 30 days.
- **Languages**: Must provide locale code (e.g., `pt_BR`, `en_US`).

## Reference
- **Component Details**: See `references/template_components.md` for full button and carousel specs.