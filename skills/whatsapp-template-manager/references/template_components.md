# Template Component Reference

## 1. Header Formats
- **TEXT**: 60 chars max.
- **MEDIA**: Image, Video, Document.
- **LOCATION**: (Marketing/Utility only).

## 2. Button Types (Max 10 total)
- **QUICK_REPLY**: Max 3. Triggers webhook with payload.
- **URL**: Max 2. Dynamic suffix supported.
- **PHONE_NUMBER**: One-tap dial.
- **COPY_CODE**: Copies coupon to clipboard (Marketing only).
- **OTP**: (Authentication only).
- **MPM/SPM**: Multi/Single product message buttons.

## 3. Carousel Component
- **Cards**: 2 to 10 cards.
- **Card Content**: Media header + Body + 1-2 buttons.
- **Consistency**: All cards must have the same button types.

## 4. Limited-Time Offer
- **Logic**: Injects a countdown timer or expiration date.
- **Category**: MUST be MARKETING.
- **Exclusion**: Footer components are NOT allowed with this component.
