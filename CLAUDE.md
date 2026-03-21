# B-ticket Admin Portal — Interactive Prototype

## Project Overview
This is the **Admin Portal** prototype for B-ticket, the Philippines' leading digital coupon marketplace. The Admin Portal is where the B-ticket team approves merchants, moderates coupons, manages ads, and oversees the platform.

## Product Context
B-ticket connects SMEs with local consumers and tourists through digital coupons. The full ecosystem:

| # | Product | Repo |
|---|---------|------|
| 1 | Consumer App | `bticket-consumer-app` |
| 2 | Consumer Website | (planned) |
| 3 | **Merchant Portal** | `bticket-merchant-portal` |
| 4 | Merchant Scanner App | (planned) |
| 5 | **Admin Portal** | **this repo** |

## Business Model
- **Consumer Subscription**: ₱99/month or ₱949/year
- **Merchant Listing**: FREE (no fees, no commissions)
- **In-App Advertising**: Hero ₱15K/mo, Top ₱8K/mo, Pop-up ₱20K/mo, Full-Screen ₱25K/mo
- **Admin Approval Gate**: All merchants, coupons, and ads require admin approval before going live

## Admin Portal Responsibilities
1. **Merchant Management** — Review applications, approve/reject, suspend accounts
2. **Coupon Moderation** — Review submitted coupons, approve/reject, flag violations
3. **Ad Management** — Review ad creatives, approve/reject, manage slot assignments
4. **User Management** — View subscribers, handle support tickets
5. **Dashboard & Analytics** — Platform-wide KPIs, revenue tracking, growth metrics
6. **Content Moderation** — Review photos, descriptions, ensure quality standards
7. **Category Management** — Manage business categories and sub-categories
8. **Settings** — Platform settings, notification templates, approval workflows

## Categories
- Food & Beverage (Japanese, Korean, Chinese, Asian, Western, Filipino, Cafes, Bars, Fast Food, Catering)
- Wellness & Beauty (Spas, Salons, Lash Studios, Aesthetics, Sauna)
- Services (Auto, Pet, Laundry, Repair, Events)
- Entertainment & Leisure (KTV, Sports, Theme Parks, Venues)
- Fitness & Sports (Gyms, Yoga, Dance, Sports Clubs)
- Hotels & Stays (Hotels, Boutique, Apartments, Villas, Hostels, Staycation)
- Academy & Learning (Language, Music, Art, Cooking, Certification, Kids)
- Travel & Experiences (Tours, Transport, Rentals, Adventure, Passes)

## Key Entities
- **Merchant**: Business applying to list on B-ticket (status: pending/approved/rejected/suspended)
- **Coupon**: Digital voucher submitted by merchant (status: pending/approved/rejected/active/paused/expired)
- **Ad**: Paid advertisement (status: pending/approved/rejected/active/completed)
- **Consumer/Subscriber**: End user (₱99/mo subscription)
- **Redemption**: Record of coupon use at a branch
- **Branch**: Physical merchant location

## Design System
- **Primary**: #205C50 (Deep Sea Green)
- **Secondary**: #56A66F (Dark Pastel Green)
- **Accent**: #84BEA1 (Pale Teal)
- **Dark**: #221F1F (Dark Jungle Green)
- **Error/Reject**: #EE4036 (Coral Red)
- **Warning/Pending**: #F9A250 (Pale Orange)
- **Highlight**: #F1E048 (Dandelion Yellow)
- **Info**: #50C9EF (Crystal Blue)
- **Font**: Poppins (weights: 300-900)
- **Border radius**: 16px cards, 10px inputs, 24px pills
- **Shadows**: Multi-layer subtle (0 1px 3px + 0 6px 16px)

## Existing Prototype Files

| File | Description |
|------|-------------|
| `index.html` | Main interactive admin portal (dark sidebar, full dashboard) |
| `admin-portal.html` | Original admin portal mockup |
| `admin-portal-ads.html` | Ad management screens |
| `admin-portal-remaining.html` | Additional admin screens |
| `admin-portal-interactive.html` | Interactive version (same as index.html) |

## What Needs To Be Built/Improved
- Login page for admin users
- Merchant application review with detail view (documents, photos, branches)
- Coupon moderation with side-by-side preview (admin view + consumer app preview)
- Ad approval workflow with creative review
- Subscriber management and analytics
- Revenue dashboard (subscription + ad revenue)
- Platform settings and configuration
- Notification/email template management
- Activity log / audit trail
- Role-based access (Super Admin, Moderator, Support)

## Multi-Agent Team
This project uses specialized Claude Code agents in `.claude/agents/`:

| Agent | Role | Use When |
|-------|------|----------|
| `frontend` | Web development | Building screens, components, interactions |
| `uiux` | Design system & UX | Wireframes, flows, design tokens |
| `qa` | Testing & QA | Test plans, bug investigation, validation |
| `product-owner` | Requirements | User stories, feature specs |
| `security` | Security & compliance | Auth, permissions, data protection |
| `data-analyst` | Analytics & metrics | KPIs, dashboards, data modeling |
| `orchestrator` | Team coordination | Multi-agent workflows |
| `senior-designer` | Premium UI design | High-quality, production-grade interfaces |
| `admin` | Testing & review | Prototype QA, UI bugs, interaction testing, design compliance |

## Conventions
- Self-contained HTML prototypes (no build tools needed)
- Poppins font via Google Fonts CDN
- No external image dependencies (use SVG or inline assets)
- All interactive elements should have working click handlers
- Use brand colors consistently
- Philippine context: ₱ currency, +63 phone numbers

## Live Demos
- **Merchant Portal**: https://bticket-merchant-portal.netlify.app
- **Admin Portal**: (deploy after improvements)

## Team
- **CEO**: Kento-san
- **CTO**: Mura-san
- **PM**: Sheena
