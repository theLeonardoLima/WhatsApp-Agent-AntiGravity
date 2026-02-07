---
name: whatsapp-catalog-manager
description: Manage WhatsApp Product Catalogs and inventory. Use for tasks like "Upload this CSV to my catalog" or "Send a multi-product message with these items".
---

# Whatsapp Catalog Manager

## Goal
To manage the integration of e-commerce catalogs with the WhatsApp Business Platform, enabling product discovery and shopping cart submissions.

## Capabilities
1.  **Inventory Management**: Upload and update products via Commerce API or Catalog feeds.
2.  **Product Sharing**: Send Single-Product (SPM) and Multi-Product Messages (MPM).
3.  **Cart Processing**: Parse incoming `order` webhooks to fulfill shopping carts.
4.  **Commerce Settings**: Enable/disable shopping features and cart visibility.

## Workflow

### 1. Catalog Setup
- **Connection**: Ensure the WABA is connected to a Meta Catalog.
- **Retailer IDs**: Use unique `retailer_id`s for each product item.

### 2. Sending Product Messages
**Multi-Product Message (MPM)**:
```json
{
  "messaging_product": "whatsapp",
  "to": "<PHONE_NUMBER>",
  "type": "interactive",
  "interactive": {
    "type": "product_list",
    "header": { "type": "text", "text": "Our Menu" },
    "body": { "text": "Check out our latest products!" },
    "action": {
      "catalog_id": "<CATALOG_ID>",
      "sections": [
        {
          "title": "Category 1",
          "product_items": [
            { "product_retailer_id": "item_1" },
            { "product_retailer_id": "item_2" }
          ]
        }
      ]
    }
  }
}
```

### 3. Handling Orders
When a user sends a cart, the webhook will contain an `order` object.
- **Action**: Extract `product_items` (ID, quantity, price) and confirm via `order_status` or a text message.

## Constraints
- **MPM Limit**: Max 30 products across 10 sections.
- **SPM**: One product per message.
- **Compliance**: Products must follow the WhatsApp Commerce Policy.