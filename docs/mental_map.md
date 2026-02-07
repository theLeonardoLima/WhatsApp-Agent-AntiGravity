# WhatsApp Business Platform - Mental Map (Final Update)

## 1. Core Architecture & Operations
- **API**: Cloud API (Data Processor). Meta manages E2EE keys.
- **Data Privacy**:
    - **Local Storage**: Choose a specific country for data-at-rest.
    - **No Storage**: Data kept for 1h max; no persistence at rest (high privacy, low TTL).
- **Identity**: **Identity Change** alerts for user crypto-key changes (re-auth recommended).
- **Support**: **API Status Page** (RSS feed available) and Graph-based **Error Codes**.

## 2. Business Assets & Solution Providers
- **Provider Tiers**:
    - **Solution Partner**: Full service + Credit Lines (Invoicing).
    - **Tech Provider**: Full service, but clients manage own billing with Meta.
    - **Tech Partner**: Tech Provider + Meta Business Partner (SMB Accelerator).
- **Onboarding**: **Embedded Signup** for automated WABA/Phone setup.
- **App Review**: Required for providers to gain Advanced Access to client assets.

## 3. Messaging & Limits
- **Portfolio Limits**: Scale from 250 -> Unlimited based on quality (GREEN/YELLOW/RED).
- **Block Users API**: Block users within 24h of their last message.
- **Opt-in**: Mandatory, clear consent required via SMS, Web, or IVR.

## 4. E-commerce & Catalogs
- **Catalog**: 1 per WABA. Upload via Commerce API or CSV.
- **Sharing**: 
    - **Multi-Product (MPM)**: Up to 30 items.
    - **Single-Product (SPM)**: One item + "View" button.
    - **Catalog Message**: Link to full catalog.
- **Flow**: Order Message Webhook (Shopping Cart) -> Fulfillment.

## 5. Payments (Brazil Focus)
- **Workflow**: `order_details` (Interactive msg) -> `order_status` (Update).
- **PIX**: Dynamic codes (`pix_dynamic_code`). User copies to bank app.
- **Boleto**: Digital line (`boleto`).
- **Payment Links**: Offsite checkout.
- **Currency**: `BRL` (offset 100, e.g., 5000 = R$50.00).
- **Reconciliation**: Business responsibility via `reference_id` and PSP.

## 6. Advanced Templates & Webhooks
- **Templates**: Marketing (Custom, Carousel, LTO), Utility, Auth (Zero-tap).
- **Webhooks**: 
    - **Verification**: `hub.verify_token` handshake.
    - **Security**: `X-Hub-Signature-256`.
    - **Events**: `messages`, `statuses`, `account_update`, `user_preferences`, `security`, `payment_configuration_update`.
