# Workflow: Process Brazil Order (PIX/Boleto)

## Objective
Fulfill a customer order from Catalog selection to Payment reconciliation using PIX or Boleto.

## Participants
- **Lead**: Commerce & Sales Lead
- **Support**: Platform Architect

## Steps

### Phase 1: Discovery (Commerce Lead)
1.  **Trigger**: User sends a text asking for products.
2.  **Action**: Send **Multi-Product Message (MPM)** using `whatsapp-catalog-manager`.
    - *Select*: Top 30 items from connected Catalog.

### Phase 2: Order Placement (Commerce Lead)
1.  **Trigger**: Webhook `messages` -> `type: order` (Shopping Cart received).
2.  **Calculation**:
    - Parse `product_items`.
    - Calculate Total (Item Price * Quantity).
    - **Currency**: Ensure `BRL` and correct offset (x100).

### Phase 3: Payment Request (Commerce Lead)
1.  **Generate Payment**: Call PSP API (internal) to get PIX Code or Boleto Line.
2.  **Send Request**:
    - Use `whatsapp-payment-br`.
    - **Type**: `interactive` -> `order_details`.
    - **Action**: `review_and_pay`.
    - **Payload**: Include `pix_dynamic_code` or `boleto` object.

### Phase 4: Fulfillment (Commerce Lead + Platform Architect)
1.  **Monitor**: Wait for PSP webhook confirming payment (External event).
2.  **Update User**:
    - Send `order_status` message.
    - **Status**: `processing` -> `shipped`.
3.  **Security Check (Architect)**: Ensure `reference_id` matches the original request to prevent spoofing.
