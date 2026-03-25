# B-Ticket Discount Types

## Overview

Merchants can create coupons with four discount types. Each type determines how the discount is calculated and displayed to consumers.

## Discount Types

### 1. Percentage Off

A percentage reduction from the original price.

| Field | Required | Description |
|-------|----------|-------------|
| Discount Value | Yes | Percentage (1–99%) |
| Original Price | Yes | Regular menu/service price |

**Display**: "50% OFF" badge on coupon card
**Auto-calculated**: Discounted price = Original Price × (1 - Discount%)

**Examples**:
- 50% off ₱900 steak → Consumer pays ₱450
- 20% off ₱1,500 spa → Consumer pays ₱1,200

### 2. Fixed Amount Off

A fixed peso amount deducted from the original price.

| Field | Required | Description |
|-------|----------|-------------|
| Discount Value | Yes | Amount in ₱ (stored as centavos) |
| Original Price | Yes | Regular menu/service price |

**Display**: "₱200 OFF" badge on coupon card
**Auto-calculated**: Discounted price = Original Price - Discount Amount

**Examples**:
- ₱200 off ₱900 steak → Consumer pays ₱700
- ₱500 off ₱2,000 treatment → Consumer pays ₱1,500

### 3. Bundle Deal (Buy X Get Y)

Customizable bundle promotions. Replaces the old fixed "Buy 1 Get 1 Free" option.

| Field | Required | Description | Values |
|-------|----------|-------------|--------|
| Buy Quantity | Yes | Items customer must purchase at full price | 1–5 |
| Get Quantity | Yes | Bonus items received | 1–3 |
| Bonus Item Discount | Yes | Discount applied to the bonus items | 25%, 50%, 100% (free), or custom % |

**Display**: Dynamic label based on configuration (see examples below)

**Common Configurations**:

| Buy | Get | Discount | Consumer-Facing Label |
|-----|-----|----------|----------------------|
| 1 | 1 | 100% | Buy 1, Get 1 Free |
| 1 | 1 | 50% | Buy 1, Get 2nd at 50% Off |
| 2 | 1 | 100% | Buy 2, Get 1 Free |
| 3 | 1 | 100% | Buy 3, Get 1 Free |
| 1 | 2 | 100% | Buy 1, Get 2 Free |
| 2 | 1 | 50% | Buy 2, Get 3rd at 50% Off |

**Label Generation Rules**:
- If discount = 100%: "Buy {X}, Get {Y} Free"
- If discount < 100%: "Buy {X}, Get {ordinal(X+1)} at {discount}% Off" (when get = 1)
- If discount < 100% and get > 1: "Buy {X}, Get {Y} at {discount}% Off"

**Price Calculation**:
- Original Price = price of 1 item
- Total without deal = Original Price × (Buy + Get)
- Total with deal = (Original Price × Buy) + (Original Price × Get × (1 - Discount%))
- Savings = Total without deal - Total with deal

### 4. Free Item

A complimentary item or service with no purchase required.

| Field | Required | Description |
|-------|----------|-------------|
| Item Description | Yes | What the consumer receives for free |

**Display**: "FREE" badge on coupon card

**Examples**:
- Free dessert
- Free consultation
- Free trial class

## Data Model

```typescript
type DiscountType = 'percentage' | 'fixed' | 'bundle' | 'free_item';

interface CouponDiscount {
  type: DiscountType;

  // For percentage type
  percentage?: number; // 1-99

  // For fixed type
  fixedAmount?: number; // in centavos

  // For bundle type
  bundleBuyQty?: number; // 1-5
  bundleGetQty?: number; // 1-3
  bundleGetDiscount?: number; // 1-100 (percentage off bonus items)

  // For free_item type
  freeItemDescription?: string;
}
```

## Validation Rules

| Rule | Description |
|------|-------------|
| Percentage range | 1–99% (100% should use Free Item type) |
| Fixed amount | Must be less than Original Price |
| Bundle buy qty | 1–5 |
| Bundle get qty | 1–3 |
| Bundle discount | 1–100% |
| Original price | Required for percentage, fixed, and bundle types |
