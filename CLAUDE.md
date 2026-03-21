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
- **Admin Approval Gate**: All merchants, coupons, ads, pause/resume, and profile changes require admin approval before going live

## Admin Portal Screens

| Screen | Sidebar Item | Description |
|--------|-------------|-------------|
| Dashboard | Dashboard | KPIs, pending approvals, pause/resume requests, profile changes, support tickets, activity feed |
| Merchants | Merchants | Merchant list with Pending/Active/Suspended tabs, detail view with documents/photos/branches/staff |
| Add Merchant | Merchants > Add Merchant | 5-step wizard with collapsible sidebar |
| Coupons | Coupons | Coupon list with Pending/Active/Rejected/Expired/All tabs, detail view with consumer preview |
| Create Coupon | Coupons > Create Coupon | 4-step wizard (Basic Details, Photos & Terms, Redemption Rules, Review) with collapsible sidebar |
| Ad Approvals | Ad Approvals | Ad list with Pending/Active/Rejected/Expired tabs, detail view with creative review |
| Create Ad | Ad Approvals > Create Ad | 3-step wizard (Format, Details, Payment) |
| Users | Users & Subscribers | User list with filter tabs, search, detail slide-out panel |
| Revenue | Revenue & Analytics | MRR, ad revenue, payment processing, forecasts, redemption monitoring |
| Content | Content Management | Featured Banners and Curated Collections (2 tabs) |
| Categories | Categories | Expandable tree view: Category > Sub-category > merchant count with View link |
| Reviews | Reviews | Review moderation with flags, detail panel |
| Refunds | Refunds | Refund requests with slide-out detail panel, eligibility check, Xendit integration |
| Activity Log | Activity Log | Searchable/filterable audit trail |
| Notifications | Notifications | Email/push/SMS template management |
| Settings | Settings | Platform configuration, ad slot management |

## Approval Workflows
1. **Merchant Registration** — Merchant submits 5-step form > Admin reviews > Approve/Reject/Request Changes
2. **Coupon Creation** — Merchant creates coupon > Admin reviews with consumer preview > Approve/Reject
3. **Coupon Pause/Resume** — Merchant requests > Shows "Pause Requested"/"Resume Requested" > Admin approves/denies
4. **Coupon Edit** — Merchant edits active coupon > Admin re-approves
5. **Ad Campaign** — Merchant submits creative + payment > Admin reviews > Approve/Reject (refund if rejected)
6. **Ad Pause/Resume** — Same as coupon pause/resume flow
7. **Profile Changes** — Merchant edits profile > Admin sees old vs new > Approve/Reject
8. **New Branch** — Merchant adds branch > Shows as "Pending" in merchant detail > Admin approves
9. **Refund Requests** — Subscriber requests > Admin reviews eligibility > Approve/Reject/Credit

## Categories & Sub-categories
- Food & Beverage (Japanese, Korean, Chinese, Asian, Western, Filipino, Cafes & Dessert, Bars & Nightlife, Fast Food, Catering)
- Wellness & Beauty (Spas & Massage, Hair & Nail Salons, Lash & Brow Studios, Aesthetics & Skincare, Sauna & Wellness)
- Services (Auto Services, Pet Services, Laundry & Cleaning, Repair & Maintenance, Event Services)
- Entertainment & Leisure (Karaoke / KTV, Sports & Games, Theme Parks, Activity & Event Venues)
- Fitness & Sports (Gyms & Training, Yoga & Pilates, Dance & Movement, Sports Clubs)
- Hotels & Stays (Hotels & Resorts, Boutique Hotels, Serviced Apartments, Villas, Hostels, Staycation Packages)
- Academy & Learning (Language & Academic, Music & Dance, Art & Creative, Cooking & Lifestyle, Certification & Test Prep, Kids Programs)
- Travel & Experiences (Tours & Packages, Transport Services, Vehicle Rentals, Adventure & Outdoor, City & Attraction Passes)

## Key Entities
- **Merchant**: Business applying to list on B-ticket (status: pending/approved/rejected/suspended)
- **Coupon**: Digital voucher submitted by merchant (status: pending/approved/rejected/active/paused/pause-requested/resume-requested/expired)
- **Ad**: Paid advertisement (status: pending/approved/rejected/active/pause-requested/resume-requested/expired)
- **Consumer/Subscriber**: End user (₱99/mo or ₱949/yr subscription)
- **Redemption**: Record of coupon use at a branch
- **Branch**: Physical merchant location (status: active/pending)
- **Staff Account**: Merchant team member (roles: Owner, Manager, Scanner Only)

## RBAC (Role-Based Access Control)
| Role | Can Approve | Can Create | Can View | Can Edit Settings |
|------|-----------|-----------|---------|------------------|
| Super Admin | All | All | All | Yes |
| Admin | Merchants, Coupons, Ads | Merchants, Coupons | All | No |
| Moderator | Coupons, Ads | -- | Merchants, Coupons, Ads, Content, Categories, Reviews | No |
| Support | -- | -- | Dashboard, Merchants (view-only), Coupons (view-only), Users, Reviews, Refunds | No |

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
- **No emojis** — use SVG icons only

## Prototype Files

| File | Description |
|------|-------------|
| `index.html` | Main interactive admin portal (all 16 screens, full functionality) |
| `admin-portal-interactive.html` | Mirror of index.html (kept in sync for IT review) |
| `admin-portal.html` | Original admin portal mockup (legacy) |
| `admin-portal-ads.html` | Ad management screens (legacy) |
| `admin-portal-remaining.html` | Additional admin screens (legacy) |
| `docs/merchant-admin-sync-guide.md` | IT guide for syncing merchant and admin portals |
| `docs/categories.md` | Category and sub-category reference |
| `docs/ad-rate-card.md` | Ad format pricing and specs |

## Conventions
- Self-contained HTML prototypes (no build tools needed)
- Poppins font via Google Fonts CDN
- No external image dependencies (use SVG or inline assets)
- All interactive elements must have working click handlers
- Use brand colors consistently
- No emojis — use inline SVG icons
- Philippine context: ₱ currency, +63 phone numbers
- Always sync index.html to admin-portal-interactive.html after changes

## Demo Credentials
- **Email**: admin@bticket.ph
- **Password**: admin123
- (Any non-empty credentials will work — prototype does not validate against a backend)

## Live Demos
- **Merchant Portal**: https://bticket-merchant-portal.netlify.app
- **Admin Portal**: https://bticket-admin-portal.netlify.app

## Team
- **CEO**: Kento-san
- **CTO**: Mura-san
- **PM**: Sheena
- **IT Team Lead**: Vincent
