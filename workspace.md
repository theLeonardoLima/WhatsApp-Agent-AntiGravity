# WhatsApp Business Platform Workspace

## Overview
This workspace is configured to manage a complete WhatsApp Business operation, from marketing campaigns to e-commerce and technical infrastructure. It leverages a specialized team of Agents, procedural Skills, and production-grade **Reference Implementations** based on the Facebook sample application.

## Directory Structure
```
Whatsapp/
├── agents/                 # Agent Personas (System Prompts)
│   ├── marketing_campaign_manager.md  # Strategy & Execution
│   ├── commerce_sales_lead.md         # Catalogs & Brazil Payments
│   └── platform_architect.md          # Security & Infrastructure
├── skills/                 # Procedural Tools (CLI Skills)
│   ├── whatsapp-marketing-manager/
│   │   ├── SKILL.md
│   │   └── references/marketing_payloads.md (Carousels, LTOs, CTAs)
│   ├── whatsapp-template-manager/
│   │   ├── SKILL.md
│   │   ├── scripts/template.sh (Automation: Upload & Create)
│   │   └── references/template_components.md
│   ├── whatsapp-webhook-handler/
│   │   ├── SKILL.md
│   │   ├── assets/services/ (Service Classes: GraphApi, Redis, etc.)
│   │   ├── assets/server/   (Express.js implementation)
│   │   └── references/webhook_examples.md
│   ├── whatsapp-catalog-manager/
│   │   └── SKILL.md
│   └── whatsapp-payment-br/
│       └── SKILL.md
├── workflows/              # Standard Operating Procedures
│   ├── launch_campaign.md
│   └── process_order_br.md
└── docs/
    └── mental_map.md       # Knowledge Base (PIX, Limits, Webhooks)
```

## Reference Implementations
The workspace contains "Gold Standard" code assets to ensure consistency:
- **Server Logic**: Use `whatsapp-webhook-handler/assets/server/app.js` for Express.js setup and signature verification.
- **Service Layer**: Follow the class patterns in `whatsapp-webhook-handler/assets/services/` (`GraphApi.js`, `Conversation.js`, `Redis.js`) for API interaction and state management.
- **Automation**: Use `whatsapp-template-manager/scripts/template.sh` for programmatic asset uploading and template creation.

## How to Use This Workspace

### 1. Activating an Agent
Adopt a persona by reading their file in `agents/`. 
- **Marketing Manager**: "Focus on optimized campaigns and rich media."
- **Sales Lead**: "Focus on Catalog conversions and PIX payments."
- **Platform Architect**: "Focus on server security, webhooks, and Redis state."

### 2. Executing a Workflow
Coordinate multiple agents using `workflows/`.
- **Example**: "Execute the Process Brazil Order workflow." (Commerce Lead manages the cart, Architect verifies the PIX webhook).

### 3. Using Skills
Skills provide the deterministic logic.
- **Marketing** -> `whatsapp-marketing-manager`, `whatsapp-template-manager`
- **Commerce** -> `whatsapp-catalog-manager`, `whatsapp-payment-br`
- **Tech** -> `whatsapp-webhook-handler`

## Key Constraints
- **Pricing**: Per-message pricing (July 2025 model).
- **Quality**: GREEN quality score maintenance is critical.
- **State**: Use **Redis** for message tracking and idempotency as seen in `Redis.js`.
