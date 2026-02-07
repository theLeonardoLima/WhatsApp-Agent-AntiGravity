# Workflow: Launch Marketing Campaign

## Objective
Launch a compliant, high-conversion marketing campaign using Optimized Marketing Messages.

## Participants
- **Lead**: Marketing Campaign Manager
- **Support**: Platform Architect (for Quality Monitoring)

## Steps

### Phase 1: Asset Preparation (Marketing Manager)
1.  **Define Strategy**: Choose objective (Awareness vs. Sales).
2.  **Create Template**:
    - Use `whatsapp-template-manager`.
    - **Category**: `MARKETING`.
    - **Components**: Add Image Header + Body + Copy Code Button (for tracking).
    - **Action**: Submit for review and wait for `APPROVED` status.

### Phase 2: Audience & Launch (Marketing Manager)
1.  **Segment List**: Filter users who have **Opted-in**.
2.  **Configure Optimization**:
    - Select `optimization_goal` (e.g., `READ` or `CONVERSION`).
    - Set `pacing` if list > 10k users.
3.  **Dispatch**:
    - Use `whatsapp-marketing-manager` to call `POST /marketing_messages`.
    - Map variables (`{{1}}`, `{{2}}`) to user data.

### Phase 3: Monitoring (Platform Architect)
1.  **Real-time Checks**:
    - Listen for `messages` webhooks (Delivered/Read).
    - Monitor `phone_number_quality_update`.
2.  **Intervention**:
    - **Trigger**: If Quality drops to YELLOW.
    - **Action**: Signal Marketing Manager to pause dispatch or switch to a different template.

### Phase 4: Analysis (Marketing Manager)
1.  **Review Metrics**:
    - Access `conversation_analytics`.
    - Compare `cost_per_conversion` vs. benchmarks.
