# Merchant Portal & Admin Portal Sync Guide

## Overview

The B-ticket platform has two portals that must stay in sync:

- **Merchant Portal** — where merchants manage their business, coupons, and ads
- **Admin Portal** — where the B-ticket team approves, moderates, and oversees everything

Every merchant action that affects what consumers see requires **admin approval** before going live.

---

## Approval Workflows

### 1. Merchant Registration

| Step | Merchant Portal | Admin Portal |
|------|----------------|--------------|
| 1 | Merchant fills 5-step registration (Business Info, Details, Photos, Documents, Review) | -- |
| 2 | Merchant submits application | Application appears in **Merchants > Pending** tab |
| 3 | -- | Admin reviews business info, documents (Business Permit, BIR, Valid ID), photos, signed contract |
| 4 | -- | Admin checks verification checklist, then **Approve**, **Reject**, or **Request Changes** |
| 5 | Merchant receives email notification | Status updates in merchant table |

**Fields to sync:** Business Name, Category, Sub-category, Description, Owner Name, Email, Phone, Address, Business Hours, Price Range, Social Media, Logo, Cover Photo, Interior/Food Photos, Documents, Contract Signature

### 2. Coupon Creation

| Step | Merchant Portal | Admin Portal |
|------|----------------|--------------|
| 1 | Merchant creates coupon (4-step: Basic Details, Photos & Terms, Redemption Rules, Review) | -- |
| 2 | Merchant submits for approval | Coupon appears in **Coupons > Pending** tab |
| 3 | -- | Admin reviews title, discount, prices, validity, terms, photos, redemption frequency |
| 4 | -- | Admin sees consumer app preview, merchant history, then **Approve**, **Reject**, or **Request Changes** |
| 5 | Merchant receives push notification | Coupon moves to **Active** tab |

**Fields to sync:** Title (max 60 chars), Description (max 500 chars), Discount Type (Percentage/Fixed/BOGO/Free Item/Bundle), Discount Value, Original Price, Discounted Price, Valid From/Until, Max Redemptions, Available Branches, Photos (up to 5), Terms (up to 5 items), Redemption Frequency (daily/weekly/monthly/one-time), Daily Cap, Auto-pause toggle, Show Remaining toggle

### 3. Coupon Pause/Resume

| Step | Merchant Portal | Admin Portal |
|------|----------------|--------------|
| 1 | Merchant clicks **Pause** on an active coupon | -- |
| 2 | Status changes to **"Pause Requested"** with "Pending Admin Approval" message | Request appears in **Coupons > Pending** tab + **Dashboard > Pause & Resume Requests** card |
| 3 | -- | Admin clicks **Approve** (coupon is paused) or **Deny** (coupon stays active) |
| 4 | Same flow for **Resume** — merchant requests, admin approves/denies | -- |

**Important:** Coupons do NOT pause/resume instantly. They stay in their current state until admin approves.

### 4. Coupon Edit (After Approval)

| Step | Merchant Portal | Admin Portal |
|------|----------------|--------------|
| 1 | Merchant edits an approved/active coupon | -- |
| 2 | -- | Edit appears in admin's coupon review queue for re-approval |
| 3 | -- | Admin reviews changes, approves (coupon updated) or rejects (old version stays) |

### 5. Ad Campaign Creation

| Step | Merchant Portal | Admin Portal |
|------|----------------|--------------|
| 1 | Merchant selects ad format (Hero/Top/Pop-up/Full-Screen), uploads creative, pays | -- |
| 2 | -- | Ad appears in **Ad Approvals > Pending Review** tab |
| 3 | -- | Admin reviews creative dimensions, content, payment status, then **Approve**, **Reject**, or **Request Revision** |
| 4 | If rejected: full refund processed via Xendit | -- |

**Fields to sync:** Campaign Name, Format (with dimensions), Creative Image, Start/End Date, Tap Destination (profile/coupon/URL), Payment Amount, Payment Method, Transaction ID

### 6. Ad Pause/Resume

Same flow as coupon pause/resume — merchant requests, admin approves/denies.

### 7. Profile Changes (After Approval)

| Step | Merchant Portal | Admin Portal |
|------|----------------|--------------|
| 1 | Merchant edits business profile (hours, description, photos, etc.) | -- |
| 2 | -- | Change appears in **Dashboard > Pending Profile Changes** card |
| 3 | -- | Admin sees old value vs new value, then **Approve** or **Reject** |

**Fields that require re-approval:** Business Name, Description, Business Hours, Cover Photo, Logo, Address

**Fields that do NOT require re-approval:** Social Media links, Website, Notification Preferences, Password, Staff Accounts

### 8. New Branch Addition

| Step | Merchant Portal | Admin Portal |
|------|----------------|--------------|
| 1 | Merchant adds a new branch location | -- |
| 2 | -- | New branch appears in merchant detail > **Branch Locations** card with "Pending" badge |
| 3 | -- | Admin reviews branch details, then **Approve** or **Reject** |

---

## Status Mapping

| Entity | Merchant Portal Status | Admin Portal Status |
|--------|----------------------|-------------------|
| **Merchant** | Submitted / Pending Approval | Pending |
| | Approved | Active |
| | Rejected | Rejected |
| | -- | Suspended (admin-initiated) |
| **Coupon** | Draft | -- (not visible to admin) |
| | Pending Approval | Pending |
| | Active | Active |
| | Pause Requested | Pause Requested (in Pending tab) |
| | Resume Requested | Resume Requested (in Pending tab) |
| | Paused | Paused |
| | Expired | Expired |
| **Ad** | Pending Review | Pending Review |
| | Active (Running) | Active |
| | Pause Requested | Pause Requested (in Pending tab) |
| | Rejected | Rejected (refund processed) |
| | Completed | Expired |

---

## Categories & Sub-categories

Both portals use the same category/sub-category structure. When a merchant selects a category during registration, the sub-category dropdown updates dynamically.

| Category | Sub-categories |
|----------|---------------|
| Food & Beverage | Japanese, Korean, Chinese, Asian, Western, Filipino, Cafes & Dessert, Bars & Nightlife, Fast Food, Catering |
| Wellness & Beauty | Spas & Massage, Hair & Nail Salons, Lash & Brow Studios, Aesthetics & Skincare, Sauna & Wellness |
| Services | Auto Services, Pet Services, Laundry & Cleaning, Repair & Maintenance, Event Services |
| Entertainment & Leisure | Karaoke / KTV, Sports & Games, Theme Parks, Activity & Event Venues |
| Fitness & Sports | Gyms & Training, Yoga & Pilates, Dance & Movement, Sports Clubs |
| Hotels & Stays | Hotels & Resorts, Boutique Hotels, Serviced Apartments, Villas, Hostels, Staycation Packages |
| Academy & Learning | Language & Academic, Music & Dance, Art & Creative, Cooking & Lifestyle, Certification & Test Prep, Kids Programs |
| Travel & Experiences | Tours & Packages, Transport Services, Vehicle Rentals, Adventure & Outdoor, City & Attraction Passes |

**Admin manages categories** via the Categories screen — can edit category names, add/remove sub-categories. Changes should reflect in the merchant portal's registration dropdown.

---

## Notification Flow

| Admin Action | Merchant Notification |
|-------------|----------------------|
| Approve merchant application | Email: "Your business has been approved on B-ticket" |
| Reject merchant application | Email: "Your application needs changes" with reason |
| Approve coupon | Push: "Your coupon is now live on B-ticket!" |
| Reject coupon | Email: "Your coupon submission needs changes" with reason |
| Approve ad | Push: "Your ad has been approved and scheduled" |
| Reject ad | Email: "Your ad creative was not approved" + refund notification |
| Approve pause/resume | Push: "Your coupon/ad has been paused/resumed" |
| Deny pause/resume | Push: "Your pause/resume request was denied" |
| Suspend merchant | Email: "Your account has been suspended" with reason |
| Profile change approved | Push: "Your profile update has been approved" |
| Admin sends message | Email/Push/SMS based on channel selection |

---

## API Endpoints Needed

For IT to build the backend sync, these API endpoints are required:

### Merchant
- `POST /api/merchants` — submit application
- `GET /api/merchants` — list all (with filters: status, category)
- `GET /api/merchants/:id` — get detail (includes branches, staff, documents)
- `PUT /api/merchants/:id/approve` — admin approve
- `PUT /api/merchants/:id/reject` — admin reject (with reason)
- `PUT /api/merchants/:id/suspend` — admin suspend
- `PUT /api/merchants/:id/reactivate` — admin reactivate
- `POST /api/merchants/:id/branches` — add branch
- `PUT /api/merchants/:id/branches/:branchId/approve` — approve branch
- `PUT /api/merchants/:id/profile-changes` — submit profile edit for approval
- `PUT /api/merchants/:id/profile-changes/:changeId/approve` — approve change

### Coupons
- `POST /api/coupons` — create coupon (status: pending)
- `GET /api/coupons` — list all (with filters: status, merchant, category)
- `GET /api/coupons/:id` — get detail
- `PUT /api/coupons/:id/approve` — admin approve
- `PUT /api/coupons/:id/reject` — admin reject (with reason)
- `PUT /api/coupons/:id/request-pause` — merchant requests pause
- `PUT /api/coupons/:id/approve-pause` — admin approves pause
- `PUT /api/coupons/:id/request-resume` — merchant requests resume
- `PUT /api/coupons/:id/approve-resume` — admin approves resume
- `PUT /api/coupons/:id` — edit coupon (triggers re-approval if active)

### Ads
- `POST /api/ads` — create ad campaign
- `GET /api/ads` — list all (with filters: status, format, merchant)
- `GET /api/ads/:id` — get detail (includes creative, payment info)
- `PUT /api/ads/:id/approve` — admin approve
- `PUT /api/ads/:id/reject` — admin reject (triggers refund)
- `PUT /api/ads/:id/request-pause` — merchant requests pause
- `PUT /api/ads/:id/approve-pause` — admin approves pause

### Users & Refunds
- `GET /api/users` — list subscribers (with filters: plan, status)
- `GET /api/users/:id` — get detail (includes redemptions)
- `PUT /api/users/:id/suspend` — suspend user
- `POST /api/refunds` — create refund request
- `PUT /api/refunds/:id/approve` — approve refund (triggers Xendit)
- `PUT /api/refunds/:id/reject` — reject refund

### Categories
- `GET /api/categories` — list all with sub-categories
- `POST /api/categories` — create category
- `PUT /api/categories/:id` — edit category
- `POST /api/categories/:id/subcategories` — add sub-category
- `DELETE /api/categories/:id/subcategories/:subId` — remove sub-category

### Notifications
- `POST /api/notifications/send` — admin sends message to merchant
- `GET /api/notifications/templates` — list notification templates

---

## Repos & Deployment

| Portal | GitHub Repo | Netlify URL |
|--------|------------|-------------|
| Admin Portal | `sheenana-dev/bticket-admin-portal` | https://bticket-admin-portal.netlify.app |
| Merchant Portal | `sheenana-dev/bticket-merchant-portal` | https://bticket-merchant-portal.netlify.app |

---

## RBAC (Role-Based Access Control)

The admin portal supports 4 roles:

| Role | Can Approve/Reject | Can Create | Can View | Can Edit Settings |
|------|-------------------|-----------|---------|------------------|
| Super Admin | All | All | All | Yes |
| Admin | Merchants, Coupons, Ads | Merchants, Coupons | All | No |
| Moderator | Coupons, Ads | -- | Merchants, Coupons, Ads, Content, Categories, Reviews | No |
| Support | -- | -- | Dashboard, Merchants (view-only), Coupons (view-only), Users, Reviews, Refunds | No |
