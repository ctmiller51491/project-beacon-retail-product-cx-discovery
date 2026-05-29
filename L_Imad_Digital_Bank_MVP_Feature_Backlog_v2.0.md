# 📋 L'IMAD DIGITAL BANK — MVP FEATURE BACKLOG & ROADMAP

**Version:** 2.0 (Revised - Embedded Finance → Wave 3, Credit Cards → Wave 2B)  
**Date:** May 27, 2026  
**Scope:** MVP Launch (March 2027) + Product Waves through 2030  
**Status:** Ready for Product Development & Engineering Planning

---

## 🎯 EXECUTIVE SUMMARY

This feature backlog translates the retail banking benchmark into a concrete, prioritized product roadmap for L'Imad's digital banking platform.

### **MVP Scope (March 2027 Launch)**

**3 Product Categories:**
- ✅ **Accounts & Payments** (Demand, Call, Time accounts + P2P + Cheques)
- ✅ **Cards** (Debit physical + Virtual cards)
- ✅ **Investments** (3rd-party platform integration)

**Core Retail Banking Journeys:**
- ✅ Onboarding (account creation, KYC, funding)
- ✅ Login & Authentication (biometric, password, security)
- ✅ Account Management (view balances, transaction history, settings)
- ✅ Marketing Preferences (communications, offers, opt-in/out)
- ✅ Customer Support (FAQs, chat, escalation)

**MVP Target:**
- 100K+ accounts by Month 3 (March 2027)
- 4.7★+ app rating
- 80K monthly active users
- AED 500M AUM (investments)
- Zero defects in core flows

### **Key Strategic Decisions (v2.0)**

| Category | Decision | Wave | Reason |
|----------|----------|------|--------|
| **Embedded Finance** | Deferred to Wave 3 | 2028-2030 | Requires stable core products; 500+ partnerships need operational maturity |
| **Credit Cards** | Deferred to Wave 2B | Q3 2027 | Depends on debit card infrastructure + Islamic structure planning |
| **Personal Lending** | Prioritized in Wave 2A | Q2 2027 | Core differentiator, high ROI, complements MVP well |
| **Mortgages** | Phased: P1 (2A), P2 (2B), P3 (2C) | Q2 2027+ | Staged approach allows learning + optimization |

---

## 📊 ROADMAP TIMELINE

```
LAUNCH         WAVE 2A         WAVE 2B         WAVE 2C         WAVE 3
March 2027     Q2 2027         Q3 2027         Q4 2027         2028-2030
───────────    ───────────     ───────────     ───────────     ──────────

MVP             Core Expansion  Product Polish  Monetization    Ecosystem
• Accounts      • Personal      • Credit Cards  • Wealth Mgmt   • Embedded
• Debit Cards     Lending       • Mortgages     • Premium Tier    Finance
• Investments   • Mortgages       (Phase 2)    • Salary Adv.   • Education
• Journeys      • BNPL          • Insurance     • Corporate     • Travel
                • Intl Payments • Enhanced UX   • Trading       • Health
                • Health (lite) • Analytics     • Zakat         • Utilities
                                                                 • Global
                                                                 • APIs
```

---

# 📱 MVP FEATURE BACKLOG (Launch March 2027)

## **TIER 0: CORE INFRASTRUCTURE (P0 - Critical Path)**

### **0.1: Platform Foundation**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Mobile App Architecture** | iOS + Android native apps (React Native or Flutter) | App runs on iOS 13+, Android 8+ with <100MB size | P0 | 4 weeks |
| **Backend API Infrastructure** | RESTful API with JWT authentication | 99.9% uptime, <500ms response time, load test 10K concurrent | P0 | 4 weeks |
| **Database & Data Layer** | PostgreSQL with high availability, backup, encryption | Data encrypted at rest + in transit, RTO <1hr | P0 | 3 weeks |
| **Security Framework** | SSL/TLS, key management, API security | All data encrypted, OAuth 2.0 implemented, DFSA compliance | P0 | 3 weeks |
| **CI/CD Pipeline** | Automated build, test, deploy | Deploy to prod in <30 min, automated tests on every commit | P0 | 3 weeks |
| **Monitoring & Logging** | Real-time monitoring, error tracking, analytics | <5 min alert for any critical issues, centralized logging | P0 | 2 weeks |
| **Third-Party Integration Framework** | Investment platform API, payment processor integration | Standardized adapter pattern, easy to add new partners | P0 | 2 weeks |

**Subtotal P0:** ~22 weeks (foundation team, highly parallelizable)

---

## **TIER 1: ACCOUNTS & PAYMENTS FEATURES**

### **1.1: Account Opening & Onboarding**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Digital KYC (Know Your Customer)** | Video selfie + ID scan + address verification | <5 min completion, 95%+ auto-approve rate, DFSA compliant | P0 | 3 weeks |
| **Account Type Selection** | User chooses Demand, Call, Time account | Clear UX showing rates, features, liquidity terms | P0 | 1 week |
| **Demand Deposit Account (DDA)** | Checking-like account, real-time access, Sharia-compliant | Instant funds transfer, no withdrawal limits | P0 | 2 weeks |
| **Call Deposit Account** | Notice required before withdrawal (e.g., 7-30 days notice) | 3-4% interest rate, flexible terms | P1 | 2 weeks |
| **Time Deposit Account (FD)** | Fixed term (1-12 months), 4-5.5% rate, Sharia Murabaha | Auto-renewal option, early withdrawal penalty display | P1 | 2 weeks |
| **Account Funding** | Link bank account, debit card, or transfer from existing | Support 10+ currencies, real-time settlement | P0 | 2 weeks |
| **Welcome Flow** | Post-signup onboarding (set password, biometric, preferences) | <2 min completion, clear next steps | P0 | 1 week |
| **Account Statement Download** | PDF/CSV export, monthly auto-email | 3-year history available, compliant format | P1 | 1 week |

**Subtotal Onboarding:** ~16 weeks

---

### **1.2: Domestic & International Payments**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **P2P Transfer (Within L'Imad)** | Send money to other L'Imad customers by phone/email | <30 sec execution, real-time settlement, 24/7 available | P0 | 1 week |
| **Interbank Transfer (Domestic)** | UAEDH rail (BATCH), same-bank transfers | <2 hours settlement during business hours, 0% fee | P0 | 2 weeks |
| **Bill Pay** | Pay utilities (Du, Etisalat), insurance, subscriptions | 50+ biller network, scheduled & one-time payments | P0 | 2 weeks |
| **International Wire Transfer** | Send money abroad (SWIFT, IBAN) | 40+ countries, competitive FX rates (0% markup), 24-48hr delivery | P1 (Wave 2A) | 3 weeks |
| **Multi-Currency Accounts** | Hold & transfer in AED, USD, EUR, GBP, INR, SAR | Real-time FX rates, zero markup on mid-market | P1 | 2 weeks |
| **Recurring Payments** | Set up automatic monthly/weekly transfers | Clear management UI, pause/cancel anytime | P1 | 1 week |
| **Transaction Limits** | Customize daily/monthly spending limits | Per-category limits, real-time blocking | P0 | 1 week |
| **Payment History & Receipts** | View all transactions with receipts | Search, filter by date/amount/recipient, export | P0 | 1 week |
| **Request Payment** | Request money from other users (bill splitting) | Notification system, easy acceptance/decline | P2 | 1 week |

**Subtotal Payments:** ~15 weeks
**Note:** International wire transfers deferred to Wave 2A

---

### **1.3: Cheque Management**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Mobile Cheque Deposit** | Take photo of cheque, upload for clearing | OCR recognition of cheque details, <5 min processing | P1 | 2 weeks |
| **Cheque Book Ordering** | Request physical cheque books in-app | 5 business day delivery, link to home address | P2 | 1 week |
| **Cheque Status Tracking** | Track cheque clearing status | Show when cheque cleared, bounced, or pending | P1 | 1 week |
| **Cheque Issuance History** | View all cheques issued, amount, payee | Search & filter by date/amount, export list | P2 | 1 week |

**Subtotal Cheques:** ~5 weeks

---

### **1.4: Account Management & Settings**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Dashboard/Home Screen** | Summary of balances, recent transactions, quick actions | <2 sec load time, shows accounts + investment summary | P0 | 2 weeks |
| **Account Overview** | View balance, account number, IBAN, statement | Real-time balance updates, account details accessible | P0 | 1 week |
| **Transaction History** | Searchable list of all transactions | Filter by date/amount/type, 2-year history | P0 | 1 week |
| **Spending Insights** | Categorized spending, monthly trends, budgeting | AI-powered categorization, comparison to budget | P1 (Wave 2A) | 2 weeks |
| **Profile Management** | Edit name, email, phone, address | Photo upload for profile, change password | P0 | 1 week |
| **Security Settings** | Password change, 2FA setup, biometric toggle | Support fingerprint + face recognition, security logs | P0 | 2 weeks |
| **Device Management** | View logged-in devices, remote logout | Show device type/location/last access | P1 | 1 week |
| **Notification Preferences** | Email/SMS/push notification settings | Granular control (transactions, marketing, security) | P0 | 1 week |

**Subtotal Account Management:** ~12 weeks

---

## **TIER 2: CARDS FEATURES**

### **2.1: Debit Card - Physical**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Card Issuance** | Apply for physical debit card in app | Card arrives in 3-5 business days (expedited 1-day available) | P0 | 2 weeks |
| **Card Activation** | Activate card via app/SMS before first use | Biometric confirmation, security question | P0 | 1 week |
| **Card Details View** | See card number, expiry, CVV, limits | Masked display for security, show only when requested | P0 | 1 week |
| **Card PIN Management** | Set/change PIN, forgot PIN recovery | SMS verification, reset via video call | P0 | 1 week |
| **Multi-Currency Debit Card** | Support 15+ currencies on single card | Auto-convert at mid-market rates, no FX markup | P1 (Wave 2A) | 2 weeks |
| **Card Lock/Unlock** | Temporarily freeze card from app | Instant lock/unlock, clear status display | P0 | 1 week |
| **Card Replacement** | Request replacement for lost/damaged/expiry | New card in 3-5 days, expedited options | P1 | 1 week |
| **Card Spending Limits** | Set daily/monthly/per-transaction limits | Customize for security, real-time enforcement | P0 | 1 week |
| **Merchant Controls** | Block specific merchants or categories | Block by category (e.g., alcohol, gambling, fuel) | P1 (Wave 2B) | 1 week |
| **Geographic Controls** | Allow/block transactions by country | Whitelist/blacklist countries, travel mode | P1 (Wave 2B) | 1 week |
| **Contactless Payment** | NFC-enabled for tap payments | Support for Apple Pay, Google Pay provisioning | P0 | 2 weeks |
| **ATM Cash Withdrawal** | Withdraw from 5,000+ ATMs globally | Zero domestic ATM fees, international fee display | P0 | 1 week |
| **Transaction Notifications** | Real-time alerts for every transaction | SMS + push + email (configurable) | P0 | 1 week |
| **Dispute Management** | Report fraud or incorrect charge | File claim in-app, status tracking, 48-72hr resolution | P1 (Wave 2B) | 2 weeks |
| **Card Analytics** | Spending by merchant, category, geography | Charts, comparisons to previous period | P2 | 1 week |

**Subtotal Debit Card:** ~20 weeks

---

### **2.2: Virtual Debit Card**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Instant Virtual Card Issuance** | Generate virtual card number in <30 seconds | Unique card number, CVV, expiry date | P0 | 2 weeks |
| **Single-Use Virtual Cards** | Option for one-time use cards | Auto-expire after first transaction or set date | P1 | 1 week |
| **Multi-Use Virtual Cards** | Reusable virtual card for subscriptions | Option to regenerate if compromised | P0 | 1 week |
| **Card Details Management** | View, copy, regenerate card details | Hide/show CVV, expiry, secure copy to clipboard | P0 | 1 week |
| **Spending Limits on Virtual Cards** | Set limits per card (daily/monthly) | Different limits for different cards | P1 | 1 week |
| **Merchant-Specific Virtual Cards** | Create card tied to specific merchant | Auto-lock to Amazon, Netflix, etc. | P2 | 1 week |
| **Virtual Card Deletion** | Delete/revoke virtual card instantly | Immediate removal from app, clear status | P0 | 1 week |
| **Virtual Card History** | Track all virtual cards created (active + deleted) | Export list, show status, usage | P1 | 1 week |

**Subtotal Virtual Card:** ~9 weeks

---

### **2.3: Card Settings & Management**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Card Rewards/Cashback** | Islamic rewards points (no interest-funded) | Accumulate points, redeem for charity/miles | P2 (Wave 2C) | 2 weeks |
| **Fraud Protection** | AI-based fraud detection, machine learning | Catch 99.5%+ fraud, <5% false positives | P0 | 3 weeks |
| **Card Statement** | Monthly card statement, download PDF | Includes all transactions, fees, interest accrued | P1 | 1 week |

**Subtotal Card Settings:** ~6 weeks

---

## **TIER 3: INVESTMENTS FEATURES**

### **3.1: Third-Party Investment Platform Integration**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Investment Platform Login** | Deep link to 3rd-party platform or embedded view | SSO (single sign-on) via L'Imad credentials | P0 | 2 weeks |
| **Account Linking** | Link L'Imad bank account to investment account | Bi-directional linking, clear verification | P0 | 1 week |
| **Investment Portfolio View** | Display portfolio from 3rd-party platform in L'Imad app | Real-time updates, <5 sec load time | P0 | 2 weeks |
| **Asset Class Display** | Show stocks, ETFs, funds, sukuk separately | Filter by asset class, sector, geography | P0 | 1 week |
| **Performance Tracking** | Display gains/losses, % return, vs benchmark | Daily/weekly/monthly/YTD performance views | P0 | 2 weeks |
| **Watchlist Sync** | Sync watchlist from 3rd-party to L'Imad app | Add/remove from watchlist, see cross-app | P1 | 1 week |
| **Transaction History** | View all investment buy/sell transactions | Export, detailed transaction details | P0 | 1 week |
| **Dividend/Distribution Tracking** | Show dividends received, distribution dates | Reinvestment status, tax lot tracking | P1 | 1 week |
| **Wealth Dashboard** | Total wealth view (bank + investments) | Net worth tracking, allocation pie chart | P1 (Wave 2A) | 2 weeks |
| **Investment Recommendations** | AI-suggested investments based on profile | Sharia-screened, aligned with risk profile | P2 | 2 weeks |

**Subtotal Investments:** ~14 weeks

---

## **TIER 4: CORE RETAIL BANKING JOURNEYS**

### **4.1: Authentication & Security**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Login Flow** | Username/email + password or biometric | <5 sec to dashboard, secure session management | P0 | 2 weeks |
| **Biometric Authentication** | Fingerprint (Touch ID) + Face recognition (Face ID) | Works offline, fallback to password, PCI-DSS compliant | P0 | 2 weeks |
| **Two-Factor Authentication (2FA)** | SMS/email verification on login | Optional/mandatory toggle, recovery codes | P0 | 2 weeks |
| **Session Management** | Auto-logout after 15 min inactivity | Clear timeout warning, option to stay logged in | P0 | 1 week |
| **Password Reset** | Forgot password flow (email/SMS verification) | <10 min reset, secure link (24hr expiry) | P0 | 1 week |
| **Account Lock** | Lock account after 5 failed login attempts | Email notification, unlock via support/SMS | P0 | 1 week |
| **Security Audit Log** | Track all login attempts, IP address, device | Accessible to user in Settings, download option | P1 | 1 week |
| **Fraud Alerts** | Alert user of unusual login locations/devices | Allow/deny new device access | P0 | 1 week |

**Subtotal Authentication:** ~11 weeks

---

### **4.2: Onboarding & User Activation**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Sign-Up Flow** | Phone number → OTP → Basic info → KYC video | <5 min end-to-end, clear progress indicator | P0 | 2 weeks |
| **Email Verification** | Confirm email during sign-up | Resend email option, auto-verify with link | P0 | 1 week |
| **KYC Video Capture** | Selfie + ID document scan + address verification | AI auto-approval for 95%, manual review for rest | P0 | 2 weeks |
| **Address Verification** | Capture address during onboarding | Google Maps autocomplete, photo verification option | P0 | 1 week |
| **Account Activation Confirmation** | Email/SMS when account is active | Clear next steps (fund account, order card) | P0 | 1 week |
| **Welcome Communication** | Email/SMS/in-app welcome message | Link to getting started guide, FAQs, support | P0 | 1 week |
| **Onboarding Tutorial** | Interactive walkthrough of key features | Video tours, skip option, accessible later | P1 | 1 week |
| **Referral Sign-Up** | Sign up via referral link from existing user | Bonus incentive for referrer, clear tracking | P2 | 1 week |

**Subtotal Onboarding:** ~10 weeks

---

### **4.3: Communication & Marketing Preferences**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Notification Center** | In-app notification history & management | Filter by type, mark as read, delete | P0 | 1 week |
| **Communication Preferences** | Email/SMS/push notification opt-in/out | Granular control per communication type | P0 | 1 week |
| **Marketing Preferences** | Opt-in/out of promotional offers, news, updates | Separate from transactional notifications | P0 | 1 week |
| **Privacy Policy & T&Cs** | Accessible in app, versioning, acceptance tracking | Link from settings, checkboxes for acceptance | P0 | 1 week |
| **Unsubscribe Link** | Email footer unsubscribe, SMS STOP option | One-click unsubscribe, confirmation message | P0 | 1 week |
| **In-App Messaging** | Push notifications for important updates | Rich media support, deep linking to app sections | P0 | 1 week |
| **Email Marketing** | Promotional offers, product updates, newsletters | Segmentation by customer type, A/B testing | P1 | 1 week |
| **SMS Marketing** | Promotional SMS with codes (opt-in only) | Character limits, clear sender ID, opt-out option | P1 | 1 week |

**Subtotal Communications:** ~8 weeks

---

### **4.4: Customer Support & Help**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **FAQ/Help Center** | Searchable FAQs, organized by category | AI search, popular articles, 50+ articles minimum | P0 | 2 weeks |
| **Live Chat Support** | In-app chat with support team (9am-9pm daily) | <2 min response time, clear hours, escalation path | P1 (Wave 2A) | 2 weeks |
| **Support Ticket System** | File support tickets, track status | Ticket ID, auto-updates via email, 24hr response SLA | P1 | 1 week |
| **Video Call Support** | Schedule video call with support agent | For complex issues, KYC, password reset | P1 (Wave 2A) | 2 weeks |
| **Contact Support** | Show phone, email, hours, chat, ticket options | Click-to-call option, clear routing | P0 | 1 week |
| **Feedback Survey** | In-app survey after support interaction | 1-5 star rating, open feedback, tracked metrics | P2 | 1 week |
| **Knowledge Base** | Search for common issues | Auto-suggest solutions, link to FAQs | P1 | 1 week |
| **Status Page** | Show system status, scheduled maintenance | Real-time updates, incident history | P2 | 1 week |

**Subtotal Support:** ~11 weeks
**Note:** Live chat and video call support initially available 9am-9pm daily; expanded in Wave 2A

---

### **4.5: Account Settings & Profile**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Profile Photo** | Upload/change profile picture | Crop/resize, clear dimensions (max 5MB) | P1 | 1 week |
| **Personal Information** | Edit name, date of birth, nationality, email, phone | Change limit: 1x per 30 days for security | P0 | 1 week |
| **Address Management** | Update residential address, correspondence address | Google Maps autocomplete, photo verification | P0 | 1 week |
| **Employment Information** | Job title, employer, salary range (for lending) | Used for creditworthiness, secure storage | P2 (Wave 2A) | 1 week |
| **Emergency Contact** | Add emergency contact, relationship | Used for critical alerts, safe storage | P1 | 1 week |
| **Document Upload** | Store copies of ID, passport, visas | Encrypted storage, version history | P2 | 1 week |
| **Account Closure Request** | Request to close account with data deletion | Confirmation step, 30-day cancellation window | P1 | 2 weeks |
| **Data Export** | Download all personal data (GDPR/DFSA compliance) | ZIP file with all account data, monthly transactions | P1 | 1 week |

**Subtotal Account Settings:** ~10 weeks

---

### **4.6: Compliance & Legal**

| Feature | Description | Acceptance Criteria | Priority | Est. Effort |
|---------|-------------|-------------------|----------|------------|
| **Terms & Conditions** | Clear, version-controlled, acceptance tracking | Versioning system, audit log of acceptance | P0 | 1 week |
| **Privacy Policy** | DFSA-compliant privacy notice | Clear language, data usage, retention periods | P0 | 1 week |
| **Sharia Compliance Disclosure** | Document Sharia structures used (Murabaha, etc.) | Link to SSB fatwa, clear explanations | P0 | 1 week |
| **Risk Disclosure** | Investment risk warnings, product-specific | Required for investments, savings products | P0 | 1 week |
| **AML/KYC Documentation** | Store KYC records, verification status | Encrypted, audit trail, compliance tracking | P0 | 1 week |
| **Data Privacy Safeguards** | Encryption, access controls, audit logs | DFSA security requirements, PCI-DSS | P0 | 2 weeks |

**Subtotal Compliance:** ~7 weeks

---

## **MVP FEATURE BACKLOG SUMMARY**

### **Total Effort Estimate**

| Category | Weeks | Notes |
|----------|-------|-------|
| **Core Infrastructure (P0)** | 22 | Foundation, highly parallelizable |
| **Accounts & Payments** | 36 | Largest category, includes all transaction types |
| **Cards** | 35 | Physical + virtual, comprehensive controls |
| **Investments** | 14 | 3rd-party integration, lighter lift |
| **Core Banking Journeys** | 47 | Auth, onboarding, support, settings |
| | | |
| **TOTAL EFFORT** | **154 weeks** | ~3.6 years at 1 team, highly parallelizable |
| **With Parallelization** | **20-24 weeks** | 4-6 cross-functional teams working simultaneously |

### **Critical Path (Must Have for Launch)**

**Critical features (51 weeks on critical path):**
- Core Infrastructure (22w)
- Digital KYC (3w)
- Demand Account (2w)
- Account Funding (2w)
- P2P Transfer (1w)
- Bill Pay (2w)
- Debit Card Physical (2w)
- Virtual Card (2w)
- Investment Platform Integration (2w)
- Dashboard (2w)
- Login/2FA (2w)
- Sign-Up Flow (2w)
- Card Fraud Protection (3w)
- FAQs & Support (1w)

**With optimal parallelization:** 16-20 weeks to MVP launch (October 2026 - January 2027)

---

# 📅 PRODUCT ROADMAP BY WAVE (REVISED v2.0)

## **WAVE 0: MVP LAUNCH (March 2027)**

### **Shipped Features**

**Accounts & Payments:**
- ✅ Digital KYC & onboarding
- ✅ Demand, Call, Time accounts
- ✅ P2P transfers (within L'Imad)
- ✅ Domestic interbank transfers (UAEDH)
- ✅ Bill pay (50+ billers)
- ✅ Mobile cheque deposit
- ✅ Transaction limits & controls
- ✅ Multi-currency view (10+ currencies)

**Cards:**
- ✅ Physical debit card (3-5 day issuance)
- ✅ Virtual debit card (instant, <30 sec)
- ✅ Card lock/unlock
- ✅ Contactless payments (Apple Pay, Google Pay)
- ✅ ATM withdrawals
- ✅ Transaction alerts
- ❌ Credit cards (deferred to Wave 2B)
- ❌ Merchant/geographic controls (Wave 2B)

**Investments:**
- ✅ 3rd-party platform integration
- ✅ Portfolio view (real-time)
- ✅ Asset class filtering
- ✅ Performance tracking
- ✅ Transaction history

**Core Journeys:**
- ✅ Biometric login + 2FA
- ✅ Account settings & profile
- ✅ Communication preferences
- ✅ FAQ & in-app help
- ✅ Support ticket system

### **MVP Metrics**
- **Accounts:** 100K by Month 3
- **AUM:** AED 500M
- **Monthly Active Users:** 80K
- **App Rating:** 4.7★+
- **Onboarding time:** <5 min
- **Card issuance:** <5 days (physical), <30 sec (virtual)

### **Known Limitations (Document for Users)**
- ❌ International wire transfers (coming Wave 2A)
- ❌ Credit cards (coming Wave 2B)
- ❌ Personal loans (coming Wave 2A)
- ❌ Mortgages (coming Wave 2A)
- ❌ Buy-now-pay-later (coming Wave 2A)
- ❌ Embedded finance (coming Wave 3)

---

## **WAVE 2A: CORE EXPANSION (Q2 2027 - April-June)**

### **New Products & Features**

**Personal Lending (CORE):**
- ✅ Personal loans (Murabaha-based)
- ✅ <5 min AI/ML credit decisioning
- ✅ Same-day funding
- ✅ Loan management dashboard
- ✅ Early repayment (zero penalty)
- ✅ Loan portfolio management

**Mortgages (Phase 1):**
- ✅ Ijarah-based Islamic mortgages
- ✅ 24-hour digital pre-qualification
- ✅ Property valuation automation (AVM)
- ✅ Mortgage calculator
- ✅ Pre-approval letters

**Buy-Now-Pay-Later (BNPL) Phase 1:**
- ✅ BNPL in 2-4 installments (0% Murabaha)
- ✅ 20+ initial merchant partnerships
- ✅ Checkout integration (<30 sec approval)
- ✅ E-commerce focus (noon, Namshi, Carrefour online)
- ✅ BNPL management dashboard

**International Payments:**
- ✅ International wire transfers (SWIFT)
- ✅ 40+ countries supported
- ✅ Competitive FX rates (0% markup)
- ✅ 24-48 hr delivery
- ✅ Remittance corridors (key countries)

**Account Enhancements:**
- ✅ Multi-currency debit card (15+ currencies)
- ✅ Spending insights & budgeting
- ✅ Savings goals tracking
- ✅ Recurring payment automation
- ✅ Card statement download
- ✅ Wealth dashboard (bank + investments)

**Support Expansion:**
- ✅ Live chat support (9am-9pm daily)
- ✅ Video call support for complex issues
- ✅ Knowledge base (100+ articles)

**Health Financing (Lite) - Optional:**
- ✅ Simple medical procedure financing (if time permits)
- ✅ Dental/cosmetic financing
- ⚠️ LIMITED scope — main health push → Wave 3

### **Wave 2A Effort Estimate: ~20 weeks**

| Category | Weeks |
|----------|-------|
| Personal Lending | 4 |
| Mortgages Phase 1 | 4 |
| BNPL Phase 1 | 3 |
| International Transfers | 3 |
| Health Financing (lite) | 2 |
| Account Features | 2 |
| Support Expansion | 2 |
| **Total** | **~20 weeks** |

### **Wave 2A Metrics**
- **Accounts:** 250K (cumulative)
- **AUM:** AED 1.5B
- **Loan Portfolio:** AED 150M
- **BNPL Volume:** AED 30M
- **Monthly Active Users:** 200K
- **App Rating:** 4.8★+
- **Revenue (quarterly):** AED 3-4M

---

## **WAVE 2B: PRODUCT POLISH (Q3 2027 - July-September)**

### **New Features & Refinements**

**Credit Cards (MOVED from Wave 2A):**
- ✅ Credit card (Murabaha-backed Islamic)
- ✅ Digital application & instant approval
- ✅ Multi-currency card (15+ currencies)
- ✅ Card rewards/cashback (Islamic points, no interest-funded)
- ✅ Merchant controls (category blocking)
- ✅ Geographic controls (country blocking)
- ✅ Credit limit management (AI-driven)
- ✅ Islamic profit rate (vs conventional interest)
- ✅ Sharia Supervisory Board approval documentation
- ✅ Statement generation & payment management

**Mortgages (Phase 2):**
- ✅ Full digital mortgage closing (24-hour target)
- ✅ E-signature & blockchain deed recording
- ✅ Automated underwriting
- ✅ Refinancing options (no early payoff penalty)
- ✅ Mortgage porting (move to new property)
- ✅ Investment property mortgages

**BNPL (Phase 2 - Scaling):**
- ✅ Expand to 50+ merchant partners
- ✅ Retail partnerships (Carrefour, Lulu physical stores)
- ✅ Installment plan customization
- ✅ Subscription-based BNPL options
- ✅ Fraud detection for BNPL

**Insurance Bundling:**
- ✅ Takaful (Islamic insurance) partnerships
- ✅ Travel insurance with BNPL flights
- ✅ Medical insurance with lite health products
- ✅ Auto insurance with car loans
- ✅ Life/disability insurance options

**Card Enhancements:**
- ✅ Card dispute resolution (AI-assisted)
- ✅ Enhanced fraud detection (ML models)
- ✅ Instant card replacement (digital)
- ✅ Card analytics & insights
- ✅ Merchant & geographic controls

**Account Features (Enhanced):**
- ✅ Expense forecasting
- ✅ Net worth tracking (bank + investments + loans)
- ✅ Enhanced spending categorization
- ✅ Investment performance analytics

### **Wave 2B Effort Estimate: ~20 weeks**

| Category | Weeks |
|----------|-------|
| Credit Cards | 4 |
| Mortgages Phase 2 | 4 |
| BNPL Phase 2 | 3 |
| Insurance Bundling | 3 |
| Card Enhancements | 2 |
| Account Features (Enhanced) | 2 |
| Testing & Polish | 2 |
| **Total** | **~20 weeks** |

### **Wave 2B Metrics**
- **Accounts:** 350K (cumulative)
- **AUM:** AED 2.5B
- **Credit Card Accounts:** 30K (9% penetration)
- **Loan Portfolio:** AED 400M
- **BNPL Volume:** AED 80M (cumulative)
- **Monthly Active Users:** 280K
- **App Rating:** 4.8★+
- **Revenue (quarterly):** AED 4-5M

---

## **WAVE 2C: MONETIZATION (Q4 2027 - October-December)**

### **New Features & Refinements**

**Wealth Management (Premium Tier):**
- ✅ Dedicated wealth manager (VIP customers, AED 500K+ AUM)
- ✅ Private investment advisory
- ✅ Portfolio rebalancing service
- ✅ Tax optimization strategies
- ✅ Estate planning integration

**Premium Account Tier:**
- ✅ AED 49/month subscription (vs free tier)
- ✅ Unlimited international transfers
- ✅ Priority support (24/7 concierge)
- ✅ Higher transaction limits
- ✅ Exclusive investment opportunities
- ✅ Waived fees on premium products

**Salary Advance Products:**
- ✅ Early salary access (3-7 days early)
- ✅ Employer integrations (payroll systems)
- ✅ Automatic repayment on payday
- ✅ <5 min approval

**Corporate Banking (B2B Pilot):**
- ✅ SME business accounts
- ✅ Business payment solutions
- ✅ Payroll management
- ✅ Business lending (SME loans)

**Trading & Advanced Investments:**
- ✅ Direct stock trading (with 3rd-party partner)
- ✅ Fractional share ownership (if not in MVP)
- ✅ Portfolio analytics dashboard
- ✅ Automated rebalancing

**Mortgages (Phase 3 - Premium Features):**
- ✅ Investment property mortgages (enhanced)
- ✅ Refinancing at competitive rates
- ✅ Automatic payment management
- ✅ Early settlement options

**Enhanced Analytics:**
- ✅ Real-time financial dashboard
- ✅ Predictive spending alerts
- ✅ AI-powered financial coaching
- ✅ Scenario planning tools
- ✅ Tax reporting & optimization

**Zakat Integration:**
- ✅ Automatic Zakat calculation
- ✅ Zakat payment in-app
- ✅ Charitable distribution tracking
- ✅ Zakat education hub

### **Wave 2C Effort Estimate: ~17 weeks**

| Category | Weeks |
|----------|-------|
| Wealth Management | 3 |
| Premium Tier | 2 |
| Salary Advance | 2 |
| Corporate Banking Pilot | 2 |
| Trading & Advanced Investments | 3 |
| Enhanced Analytics | 2 |
| Zakat Integration | 1 |
| Testing & Polish | 2 |
| **Total** | **~17 weeks** |

### **Wave 2C Metrics**
- **Accounts:** 450K (cumulative)
- **Premium Subscribers:** 15K (3% of base)
- **Market Share (UAE):** 15-20%
- **Monthly Active Users:** 350K
- **App Rating:** 4.9★
- **Revenue (quarterly):** AED 6-8M

---

## **WAVE 3: ECOSYSTEM DOMINANCE (2028-2030)**

### **Phase 3A: Embedded Finance Ecosystem (2028)**

**Education Financing:**
- ✅ Tuition financing (2-6 month installments, 0% Murabaha)
- ✅ University partnerships (10+ institutions by phase end)
- ✅ Book/course purchase financing
- ✅ Exam fee financing (GMAT, IELTS, etc.)
- ✅ Education loan management
- ✅ Student loan consolidation
- ✅ Career-based repayment options

**Travel Finance:**
- ✅ Flight/hotel BNPL (0% Murabaha, 2-4 installments)
- ✅ Holiday package financing
- ✅ Travel insurance bundling
- ✅ Currency exchange (0% markup)
- ✅ Booking.com, flydubai, Agoda partnerships
- ✅ Airline partnerships (Emirates, FlyDubai)
- ✅ Travel insurance automated claims

**Health & Wellness Financing:**
- ✅ Medical procedure financing (elective surgery, dental, cosmetic)
- ✅ Wellness subscription financing
- ✅ Doctor/hospital network partnerships
- ✅ Takaful health insurance bundling
- ✅ Preventive care financing
- ✅ Mental health counseling packages
- ✅ Pharmaceutical cost financing

**Utilities & Maintenance:**
- ✅ Auto-pay setup for utilities (full automation)
- ✅ Rent financing (12-month lease → monthly payments)
- ✅ Property maintenance subscriptions
- ✅ Home service provider partnerships (20+ providers)
- ✅ Warranty financing
- ✅ Maintenance escrow services

**Subscription Management (Full Platform):**
- ✅ Consolidated subscription dashboard
- ✅ Netflix, Spotify, gym bundling
- ✅ Monthly payment scheduling
- ✅ Auto-cancellation reminders
- ✅ Subscription analytics & savings recommendations
- ✅ White-label subscription management for B2B partners

**BNPL Expansion:**
- ✅ 500+ merchant partners (vs 50 in Wave 2B)
- ✅ White-label BNPL for corporate partners
- ✅ Embedded lending SDK for 3rd parties
- ✅ B2C2 (business-to-consumer-to-business) model
- ✅ Franchise BNPL infrastructure

**Real Estate Tokenization (Pilot):**
- ✅ Fractional real estate ownership
- ✅ Tokenized property investment
- ✅ Secondary trading market
- ✅ Yield distribution automation

**Islamic Crowdfunding Platform:**
- ✅ Musharaka-based crowdfunding
- ✅ SME business funding
- ✅ Real estate projects
- ✅ Social impact projects

**Embedded Finance Metrics:**
- Partners: 500+
- GMV: AED 500M+
- Monthly transactions: 1M+
- Revenue: AED 30-40M annually

### **Phase 3B: Global Expansion (2028-2029)**

**Geographic Expansion:**
- ✅ GCC-wide launch (KSA, Qatar, Oman, Kuwait)
- ✅ UK/Europe digital banking license
- ✅ Multi-language support (Arabic, English, Urdu, Hindi)
- ✅ Localized partnerships per region

**International Payments (Expansion):**
- ✅ Remittance corridors (zero fee to 20+ key countries)
- ✅ 100+ country coverage
- ✅ Real-time settlement via blockchain (where available)
- ✅ Multi-currency wallets

**B2B Expansion:**
- ✅ Full corporate banking platform
- ✅ Trade finance products
- ✅ Supply chain financing
- ✅ Payroll services (white-label)
- ✅ Invoice financing
- ✅ Vendor management

### **Phase 3C: Fintech Ecosystem (2029-2030)**

**Open Banking APIs:**
- ✅ Developer portal & sandbox
- ✅ 50+ API endpoints
- ✅ 3rd-party app integrations
- ✅ Transaction data access (with consent)

**Cryptocurrency/Digital Assets:**
- ✅ Tokenized sukuk trading (if regulatory approved)
- ✅ Stablecoin support (if regulatory approved)
- ✅ Blockchain-based settlements (where available)
- ✅ Digital asset wallets

**AI/ML Advanced Features:**
- ✅ Predictive financial planning
- ✅ Autonomous portfolio management
- ✅ Fraud detection (99.9%+ accuracy)
- ✅ Natural language financial advice

**Sustainability & ESG:**
- ✅ Green financing products
- ✅ Carbon footprint tracking
- ✅ ESG investment screening
- ✅ Impact measurement & reporting

### **Wave 3 Metrics (End of 2030)**
- **Accounts:** 1M+ (UAE + GCC + International)
- **Market Share (UAE):** 25-30%
- **Embedded Finance GMV:** AED 1B+
- **AUM:** AED 8-10B
- **Loan Portfolio:** AED 2-3B
- **International Users:** 30% of base
- **Monthly Active Users:** 750K+
- **App Rating:** 4.9★+
- **Annualized Revenue:** AED 200-250M (driven by embedded finance)
- **Embedded Finance Revenue:** AED 80-100M (40-50% of total)
- **Gross Margin:** 35-40%
- **ROAE:** 15-20%
- **Profitability:** Achieved by Q3 2030

---

# 🔗 FEATURE DEPENDENCIES & SEQUENCING

## **Critical Path Dependencies (Updated)**

```
INFRASTRUCTURE (Week 0-4)
│
├─→ ONBOARDING & KYC (Week 4-8)
│   │
│   ├─→ ACCOUNTS & PAYMENTS (Week 8-16)
│   │   ├─→ DEBIT CARDS (Week 14-20)
│   │   ├─→ BILL PAY (Week 14-18)
│   │   └─→ INVESTMENTS (Week 16-20)
│   │
│   ├─→ LOGIN & SECURITY (Week 4-8)
│   │   └─→ ACCOUNT MANAGEMENT (Week 8-12)
│   │
│   └─→ SUPPORT & HELP (Week 12-16)
│       └─→ COMMUNICATION PREFERENCES (Week 12-14)
│
├─→ WAVE 2A (Parallel to MVP final weeks)
│   ├─→ PERSONAL LENDING (depends on: Accounts ready)
│   ├─→ MORTGAGES Phase 1 (depends on: Lending infrastructure)
│   ├─→ BNPL Phase 1 (depends on: Bill Pay + Payments)
│   └─→ INTL TRANSFERS (depends on: Payments system)
│
├─→ WAVE 2B
│   ├─→ CREDIT CARDS (depends on: Debit card system + underwriting)
│   ├─→ MORTGAGES Phase 2 (depends on: Phase 1 success)
│   ├─→ BNPL Phase 2 (depends on: Phase 1 at scale)
│   └─→ INSURANCE (depends on: Partner integrations)
│
├─→ WAVE 2C
│   ├─→ WEALTH MANAGEMENT (depends on: AUM > 2B)
│   ├─→ PREMIUM TIER (depends on: Core products mature)
│   └─→ ZAKAT (depends on: SSB framework)
│
└─→ WAVE 3
    ├─→ EMBEDDED FINANCE (depends on: All Wave 2 products stable + partnerships)
    ├─→ GLOBAL EXPANSION (parallel to embedded)
    └─→ FINTECH ECOSYSTEM (depends on: Scale achieved)

LAUNCH (Week 20-24)
```

## **Cannot Build Before (Updated)**

| Feature | Depends On | Wave | Reason |
|---------|-----------|------|--------|
| Debit Cards | Accounts | MVP | Account needed before card issuance |
| Personal Loans | Accounts + KYC | Wave 2A | Need customer identity & funding account |
| Mortgages P1 | Personal Loans | Wave 2A | Underwriting platform reused for mortgages |
| BNPL P1 | Bill Pay + Payments | Wave 2A | Leverage payment rails + merchant partnerships |
| Credit Cards | Debit Card System + Underwriting | Wave 2B | Reuse card infrastructure, require personal lending model |
| Mortgages P2 | Mortgages P1 success | Wave 2B | Iterate on closing automation after P1 learnings |
| Insurance Bundling | BNPL P2 + Mortgages | Wave 2B | Integrate insurance with existing products |
| Wealth Management | AUM > AED 2B + Core stability | Wave 2C | Premium tier only for established customer base |
| Premium Tier | Core products mature | Wave 2C | Stable, feature-complete product base required |
| Embedded Finance | All Wave 2 products + Partnerships | Wave 3 | 500+ partnerships require operational excellence |
| Global Expansion | Embedded Finance proof + Scale | Wave 3 | Prove model in UAE before regional expansion |

---

# 📊 EFFORT BREAKDOWN BY TIMELINE

## **MVP Launch (March 2027)**

### **Personnel & Team Structure**

```
PRODUCT & DESIGN:
├─ VP Product: 1 FTE
├─ Product Manager (Payments): 1 FTE
├─ Product Manager (Cards): 1 FTE
├─ Product Manager (Journeys): 1 FTE
└─ Product Designer: 2 FTE

ENGINEERING:
├─ VP Engineering: 1 FTE
├─ Backend Lead: 1 FTE
├─ Backend Engineers: 4 FTE
├─ Mobile Lead (iOS): 1 FTE
├─ Mobile Engineers (iOS): 2 FTE
├─ Mobile Lead (Android): 1 FTE
├─ Mobile Engineers (Android): 2 FTE
├─ DevOps/Infrastructure: 1 FTE
└─ QA Engineers: 2 FTE

OPERATIONS & COMPLIANCE:
├─ Compliance Officer: 1 FTE
├─ KYC/AML Specialist: 1 FTE
├─ Sharia Advisor: 0.5 FTE (consulting)
└─ Operations Manager: 1 FTE

TOTAL: ~24 FTE for MVP (6-month ramp: May 2026 - Oct 2026)
```

### **Timeline to March 2027**

```
MAY 2026         AUG 2026          NOV 2026         MAR 2027
──────────────   ──────────────    ──────────────   ──────────────
Hiring           MVP Build         Testing          LAUNCH
Infra Setup      Core Features     Beta             100K users
Design           Integration       Polish           4.7★ rating
Planning         User Testing      Hardening
                 Risk Modeling
```

---

## **Wave 2A (Q2 2027) — 12 weeks**

**Team additions:**
- Product Manager (Lending): 1 FTE
- Backend Engineers (Lending/BNPL): 3 FTE
- Mobile Engineers: 1 FTE
- Business Development: 2 FTE
- Data Scientist (Credit modeling): 1 FTE

**Total team size:** ~32 FTE

---

## **Wave 2B (Q3 2027) — 12 weeks**

**Team additions:**
- Backend Engineers (Credit Cards): 2 FTE
- UX Designer (Cards): 1 FTE
- Mortgages Engineer: 1 FTE
- Insurance Specialist: 1 FTE
- Analytics Engineer: 1 FTE

**Total team size:** ~40 FTE

---

## **Wave 2C (Q4 2027) — 12 weeks**

**Team additions:**
- Wealth Manager: 1 FTE
- Trading/Investment Specialist: 1 FTE
- Tax Specialist: 1 FTE
- Corporate Banking PM: 1 FTE
- Sharia Advisor (part-time): 0.5 FTE

**Total team size:** ~45 FTE

---

## **Wave 3 (2028-2030) — 36 months**

**Major team expansion to 80-100 FTE across all phases**

---

# ✅ LAUNCH READINESS CHECKLIST

## **2 Weeks Before Launch**

- [ ] All P0 features complete & tested
- [ ] UAT by 50 beta users complete
- [ ] Performance tested (load, stress, endurance)
- [ ] Security audit passed
- [ ] Compliance review passed by DFSA
- [ ] Customer support trained (50+ FAQs ready)
- [ ] Marketing campaign live
- [ ] App store submission approved
- [ ] Server capacity confirmed
- [ ] Incident response plan documented

## **Launch Day**

- [ ] Apps live on iOS/Android
- [ ] Customer service team monitoring
- [ ] Real-time monitoring dashboard active
- [ ] Social media team monitoring mentions
- [ ] Executive team on standby
- [ ] Rollback plan ready

## **Post-Launch (Week 1)**

- [ ] Monitor all metrics hourly
- [ ] Fix critical bugs immediately
- [ ] Collect user feedback (surveys, interviews)
- [ ] Measure onboarding completion
- [ ] Calculate CAC (customer acquisition cost)
- [ ] Plan Wave 2A features based on feedback

---

# 📄 HOW TO USE THIS BACKLOG

## **For Product Managers**

1. Review MVP scope to understand launch constraints
2. Use effort estimates for sprint planning (2-4 week sprints)
3. Reference dependencies when sequencing work
4. Track metrics against targets in real-time

## **For Engineers**

1. Review technical considerations for architecture decisions
2. Use effort estimates for capacity planning
3. Break down features into 1-2 week engineering tasks
4. Reference dependencies for integration planning

## **For Executives**

1. Review roadmap timeline for investor updates
2. Track metrics for board reporting
3. Monitor team size and budget implications
4. Use Wave metrics for milestone-based funding releases

---

# 🎯 SUCCESS CRITERIA

**MVP is successful when:**

- ✅ 100K+ accounts opened
- ✅ 4.7★+ app rating (500+ reviews)
- ✅ Zero regulatory issues
- ✅ <5 min onboarding time (90th percentile)
- ✅ 80K+ monthly active users
- ✅ 99.9% API uptime
- ✅ <48hr first transaction time (90th percentile)
- ✅ 60+ NPS score
- ✅ 85%+ customer satisfaction
- ✅ Revenue tracking to projections

---

**Document Status:** ✅ READY FOR IMPLEMENTATION (v2.0)

**Version History:**
- v1.0 (Original): Embedded Finance Wave 2A, Credit Cards Wave 2A
- v2.0 (This): Embedded Finance → Wave 3, Credit Cards → Wave 2B

**Key Changes (v2.0):**
- ✅ Embedded Finance (education, travel, health, utilities, subscriptions) moved to Wave 3
- ✅ Credit Cards moved from Wave 2A to Wave 2B  
- ✅ All dependencies updated
- ✅ Effort estimates recalculated
- ✅ Metrics aligned with new sequencing
- ✅ Team sizing adjusted per wave
