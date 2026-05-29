# L'IMAD DIGITAL BANK - FEATURE CATALOG & USER STORIES
## Framework Steps 05-09: Features, Journeys, Epics, User Stories

**Version:** 1.0.0  
**Date:** May 28, 2026  
**Phase Coverage:** Launch (March 2027), Wave 2A-C (2027), Wave 3 (2028-2030)

---

## STEP 05: FEATURE DEFINITION & USER JOURNEYS

### CATEGORY 1: ACCOUNTS & PAYMENTS

#### Feature FE-001: Profit-Sharing Investment Accounts (Launch)
**Hypothesis Source:** HY-001  
**Description:** Sharia-compliant accounts with competitive profit-sharing rates (5-6% p.a.)

**In Scope:**
- Multiple account types: Current, Savings, Call (notice period), Time Deposit
- Transparent profit-sharing calculation and display
- Monthly profit distribution
- Zakat calculation integrated
- Auto-transfer to Zakat fund option
- Profit rate comparison vs. market

**Out of Scope:**
- Conventional interest-bearing accounts
- Investment advisory on profit rates
- Guarantee of specific profit rates (market-dependent)

**User Journey JY-001: Open Profit-Sharing Savings Account**
1. User taps "Add Account" in app
2. System displays account types: Current, Savings, Call, Time Deposit
3. User selects "Savings Account"
4. System shows current profit-sharing rate (e.g., 5.5% p.a.), Sharia certification badge
5. User enters account name (e.g., "Emergency Fund"), initial deposit amount
6. System validates minimum deposit (AED 100)
7. User confirms; system creates account instantly
8. System displays success, account IBAN, virtual card option
9. User receives welcome notification with profit calculation details

**Success Outcome:** User has active profit-sharing savings account earning competitive returns

---

#### Feature FE-002: Instant Emirates ID Onboarding (Launch)
**Hypothesis Source:** HY-002  
**Description:** Sub-2-minute account opening with government database integration

**In Scope:**
- Emirates ID scanning and OCR
- UAE government database verification (ICP integration)
- Facial recognition with liveness detection
- Instant IBAN generation
- Instant virtual card issuance
- SMS/email verification
- Address verification
- Occupation and income declaration

**Out of Scope:**
- Manual document review for standard cases
- Video call verification
- Physical card instant issuance (3-5 day delivery standard)

**User Journey JY-002: Complete Onboarding**
1. User downloads L'Imad app, taps "Open Account"
2. System requests phone number, sends OTP
3. User enters OTP, verifies phone
4. System prompts Emirates ID scan (front and back)
5. User positions Emirates ID, system captures and extracts data via OCR
6. System verifies with UAE government database (ICP) - 5 seconds
7. System prompts facial recognition with liveness detection
8. User follows on-screen prompts (blink, turn head), system validates
9. System requests address confirmation, occupation, estimated monthly income
10. User reviews terms of service, Sharia compliance agreement, data privacy
11. User sets biometric login (Face ID or fingerprint) and 6-digit PIN
12. System creates account, generates IBAN, issues instant virtual card
13. User sees success screen: "Welcome to L'Imad! Your account is ready"
14. User receives email with account details, IBAN, virtual card in Apple/Google Pay

**Success Outcome:** User has fully verified account with IBAN and virtual card in <2 minutes

---

#### Feature FE-003: Free Domestic & International Transfers (Launch)
**Hypothesis Source:** HY-001  
**Description:** Zero-fee domestic transfers, competitive FX for international

**In Scope:**
- Free instant local UAE transfers (UAEFTS)
- AANI Pay integration (India-UAE instant)
- SWIFT transfers to 50+ countries
- Competitive FX rates (market rate + 0.5% max markup)
- Real-time FX rate display
- Transfer tracking and notifications
- Beneficiary management
- Scheduled and recurring transfers

**Out of Scope:**
- Cash pickup services
- Same-currency international transfers free (AED to AED charged per receiving bank)

**User Journey JY-003: Send International Transfer to India**
1. User taps "Send Money" → "International"
2. System displays popular corridors: India, Philippines, Pakistan, UK, US
3. User selects "India (AANI Instant)"
4. User enters recipient details: Name, Indian bank account, IFSC code
5. System validates account details via AANI network
6. User enters amount in AED (e.g., AED 5,000)
7. System displays: INR received (₹115,000), FX rate, fees (AED 0), total cost (AED 5,000)
8. User reviews, confirms source of funds (Savings Account)
9. System prompts Face ID / biometric confirmation
10. System processes transfer via AANI network - arrives in 5 seconds
11. User receives confirmation: "Transfer successful! ₹115,000 sent to [Name]"
12. Recipient receives instant SMS notification in India

**Success Outcome:** User sends money to India instantly with transparent fees and competitive rates

---

### CATEGORY 2: CARDS

#### Feature FE-004: Unlimited Virtual Cards with Spending Controls (Launch)
**Hypothesis Source:** HY-006  
**Description:** Generate unlimited virtual cards with granular merchant and amount controls

**In Scope:**
- Instant virtual card generation (disposable and recurring)
- Individual spending limits per card
- Merchant category code (MCC) restrictions
- Expiry date setting (1 week, 1 month, 6 months, 1 year, never)
- Freeze/unfreeze individual cards
- Delete cards instantly
- Apple Pay, Google Pay, Samsung Pay tokenization per virtual card
- Card nicknames and color coding
- Link cards to specific sub-accounts

**Out of Scope:**
- Physical card customization beyond standard designs
- Shared virtual cards (multi-user)

**User Journey JY-004: Create Virtual Card for Online Shopping**
1. User taps "Cards" → "Add Virtual Card"
2. System displays: "Recurring Virtual Card" or "Single-Use Card"
3. User selects "Recurring Virtual Card"
4. User enters nickname: "Amazon Shopping"
5. User sets monthly spending limit: AED 2,000
6. User selects merchant categories allowed: "Online Retail" only
7. User links to sub-account: "Shopping Budget"
8. User sets expiry: 1 year from today
9. System generates card instantly: 16-digit number, CVV, expiry displayed
10. User taps "Add to Apple Pay" - card tokenized
11. System confirms: "Virtual card ready! Use for online shopping up to AED 2,000/month"

**Success Outcome:** User has dedicated virtual card for secure online shopping with automatic budget controls

---

#### Feature FE-005: Premium Tier with Concierge & Lounges (Wave 2A)
**Hypothesis Source:** HY-003  
**Description:** Premium subscription (AED 200-250/month) with affluent lifestyle benefits

**In Scope:**
- Metal physical card (premium design)
- 24/7 lifestyle concierge (Albertine or similar provider)
- 1,000+ airport lounge access (Priority Pass)
- Enhanced profit-sharing rate (+1.5% p.a. bonus = 7% total)
- Travel insurance (AED 500,000 coverage, medical, trip cancellation, baggage)
- Device insurance (phone, laptop, tablet up to AED 5,000)
- Annual subscription bundle (The National, gym membership, streaming services)
- 2% cashback on all purchases, 5% on rotating categories
- Free ATM withdrawals globally (unlimited)
- Dedicated premium customer support (priority queue)

**Out of Scope:**
- In-person relationship manager (digital-only service)
- Private jet/yacht booking (concierge can arrange but not subsidized)

**User Journey JY-005: Subscribe to Premium Tier**
1. User sees in-app banner: "Upgrade to Premium - Exclusive Benefits"
2. User taps to view premium features list
3. System displays comparison: Standard (Free) vs. Premium (AED 250/month)
4. User views benefits: Concierge, Lounges, 7% profit-sharing, Travel Insurance
5. User taps "Start 30-Day Free Trial"
6. System confirms: No charges for 30 days, cancel anytime
7. User confirms; system upgrades account immediately
8. System orders metal card (3-5 day delivery)
9. System emails Priority Pass membership number and digital card
10. User receives welcome email: "Welcome to L'Imad Premium" with concierge hotline
11. User can immediately access concierge via in-app chat

**Success Outcome:** User subscribed to premium tier with instant benefit access and metal card on the way

---

### CATEGORY 3: INVESTMENTS

#### Feature FE-006: Fractional Halal Shares Investment (Launch)
**Hypothesis Source:** HY-005  
**Description:** AI-powered Halal investment screening with AED 10 minimum via 3rd-party platform

**In Scope:**
- Partnership with Sharia-compliant wealth platform (Sarwa, Wahed, or similar)
- Fractional shares from AED 10 minimum
- Access to S&P Dow Jones Islamic Index, MSCI Islamic indices
- AI-powered Halal screening (excludes alcohol, tobacco, gambling, conventional finance, pork)
- Commission-free trading (revenue share with platform partner)
- Goal-based investing (Education, Retirement, Wealth Building)
- Automated portfolio rebalancing
- Real-time portfolio value and performance tracking
- In-app educational content on Islamic investing

**Out of Scope:**
- Individual stock picking (curated Halal portfolios only at Launch)
- Crypto trading (Wave 2B pending Sharia approval)
- Options, futures, derivatives (not Sharia-compliant)

**User Journey JY-006: Start Investing for Retirement Goal**
1. User taps "Invest" tab in app
2. System displays: "Start investing from AED 10 | Sharia-Compliant"
3. User taps "Get Started"
4. System asks: "What are you investing for?" - Options: Retirement, Education, Wealth, House, Other
5. User selects "Retirement"
6. System asks: "How much can you invest monthly?" - User enters AED 1,000
7. System asks: "What's your investment horizon?" - User selects "20+ years"
8. System asks: "Risk tolerance?" - User selects "Moderate"
9. System generates recommended portfolio: 60% Global Halal Equities, 30% Sukuk, 10% Gold
10. System displays expected annual return: 7-9% (historical, not guaranteed)
11. System shows Sharia compliance badge with certification details
12. User reviews, taps "Invest AED 1,000 Now"
13. System links to funding source (Main Account), confirms transaction
14. System purchases fractional shares across portfolio
15. User receives confirmation: "Investment successful! Portfolio created"
16. System sets up automatic monthly investment of AED 1,000

**Success Outcome:** User has diversified Halal investment portfolio with automatic monthly contributions toward retirement goal

---

## STEP 06: UI/UX STRESS TEST

### UX Risk Assessment

**UXR-001: Sharia Compliance Transparency**
- **Risk:** Users may not understand profit-sharing vs. conventional interest
- **Severity:** High
- **Affected User:** All users, especially non-Muslim or less religiously-aware customers
- **Mitigation:** 
  - Clear in-app educational content: "How Profit-Sharing Works"
  - Visual comparison chart: Profit-Sharing vs. Interest
  - Sharia certification badge prominently displayed
  - Link to Sharia Supervisory Board profiles and contact
  - FAQ section addressing common questions
- **Accessibility Check:** Pass - Text-based explanations with visual aids
- **Status:** Mitigation required before Launch
- **Source Features:** FE-001 (Profit-Sharing Accounts)

**UXR-002: Onboarding Drop-Off Risk**
- **Risk:** Users may abandon if Emirates ID scan fails or government verification is slow
- **Severity:** High
- **Affected User:** All new users, especially those with older Emirates IDs or poor lighting
- **Mitigation:**
  - Clear guidance: "Position Emirates ID in frame" with visual example
  - Retry mechanism with improved instructions after failed scan
  - Fallback: Manual entry if scan fails 3 times
  - Progress indicator: "Step 2 of 5" to show proximity to completion
  - Save progress: Allow users to resume if they exit mid-onboarding
  - Customer support chat available during onboarding
- **Accessibility Check:** Risk - Facial recognition may struggle with certain facial features, hijabs, glasses
- **Status:** Mitigation required - ensure liveness detection works with diverse facial features and religious attire
- **Source Features:** FE-002 (Emirates ID Onboarding)

**UXR-003: Virtual Card Overwhelm**
- **Risk:** "Unlimited virtual cards" may confuse users who create too many without clear organization
- **Severity:** Medium
- **Affected User:** Less tech-savvy users, older affluent customers
- **Mitigation:**
  - Default card list view with clear nicknames and usage stats
  - "Inactive cards" automatically archived after 90 days
  - Suggested card templates: "Online Shopping," "Subscriptions," "Dining," "Travel"
  - Visual color coding and icons per card
  - Search and filter by card name, spending limit, or merchant category
  - Onboarding tooltip: "Create cards for different spending categories to stay in budget"
- **Accessibility Check:** Pass - Screen reader compatible with clear card labels
- **Status:** Mitigation implemented in design
- **Source Features:** FE-004 (Virtual Cards)

**UXR-004: Premium Tier Value Perception**
- **Risk:** Users may not perceive AED 250/month as worthwhile vs. free tier
- **Severity:** Medium
- **Affected User:** Price-sensitive affluent users, those who don't travel frequently
- **Mitigation:**
  - Free 30-day trial with no credit card required
  - In-app calculator: "Your potential savings" based on usage patterns
  - Clear benefit value breakdown: "Lounges: AED 100/visit, Insurance: AED 150/month value, etc."
  - Testimonials from existing premium users
  - Downgrade option with no penalty
  - Usage analytics: "You saved AED 450 this month with premium benefits"
- **Accessibility Check:** Pass - Text and visual value communication
- **Status:** Mitigation built into pricing page design
- **Source Features:** FE-005 (Premium Tier)

**UXR-005: Investment Risk Understanding**
- **Risk:** Users may not understand that investments can lose value despite Halal compliance
- **Severity:** High
- **Affected User:** First-time investors, users confusing investments with savings accounts
- **Mitigation:**
  - Mandatory risk disclosure before first investment with "I Understand" checkbox
  - Clear language: "Investments can go down as well as up. You may get back less than you invest."
  - Historical performance charts showing both gains and losses
  - Investment education module: "Investing 101" with video content
  - Goal-based framing emphasizes long-term horizon
  - Portfolio simulation: "See how your investment might perform over 20 years"
- **Accessibility Check:** Pass - Video captions, text transcripts available
- **Status:** Mitigation required - regulatory compliance team to review disclosures
- **Source Features:** FE-006 (Fractional Shares)

---

## STEP 07: EPIC CREATION

### EPIC EP-001: Sharia-Compliant Account Foundation
**Module:** Accounts & Payments  
**Objective:** Enable customers to open and manage profit-sharing accounts with full Sharia compliance and competitive returns

**Linked Features:** FE-001 (Profit-Sharing Accounts)  
**Linked Hypotheses:** HY-001 (Sharia compliance as differentiator)  
**Source UX Risks:** UXR-001 (Sharia transparency)

**Success Metrics:**
- 5-6% profit-sharing rate competitive with market leaders
- 30%+ of sign-ups cite Sharia compliance as primary reason for choosing L'Imad
- 90%+ customer satisfaction with profit-sharing transparency
- Zero Sharia compliance complaints or violations

**Priority:** Must-Have (Launch)

---

### EPIC EP-002: Lightning-Fast Onboarding
**Module:** Core Retail Journeys  
**Objective:** Achieve industry-leading onboarding conversion with sub-2-minute account opening and instant banking access

**Linked Features:** FE-002 (Emirates ID Onboarding)  
**Linked Hypotheses:** HY-002 (Fast onboarding drives conversion)  
**Source UX Risks:** UXR-002 (Drop-off risk)

**Success Metrics:**
- 80%+ conversion rate from app download to active account
- <2 minutes median onboarding time (from app download to IBAN issued)
- <5% customer support tickets related to onboarding issues
- Instant virtual card issuance 100% of successful onboardings

**Priority:** Must-Have (Launch)

---

### EPIC EP-003: Borderless Money Movement
**Module:** Accounts & Payments  
**Objective:** Provide zero-fee domestic transfers and competitive international transfers to primary corridors (GCC, India, Philippines, UK)

**Linked Features:** FE-003 (Domestic & International Transfers)  
**Linked Hypotheses:** HY-001 (Competitive offering drives adoption)  
**Source UX Risks:** None identified

**Success Metrics:**
- 100% domestic transfers processed instantly (real-time settlement)
- 90%+ international transfers completed within 24 hours
- FX markup ≤0.5% vs. mid-market rate
- 50%+ of customers make at least one international transfer within 6 months

**Priority:** Must-Have (Launch)

---

### EPIC EP-004: Intelligent Spending Control
**Module:** Cards  
**Objective:** Empower customers with unlimited virtual cards and granular spending controls to manage budgets and prevent fraud

**Linked Features:** FE-004 (Virtual Cards with Controls)  
**Linked Hypotheses:** HY-006 (Virtual cards drive security and engagement)  
**Source UX Risks:** UXR-003 (Card overwhelm)

**Success Metrics:**
- Average 3+ virtual cards per active customer
- 50%+ of customers set at least one merchant category restriction
- Fraud rate <0.1% (vs. industry average 0.15%)
- 70%+ of online transactions use virtual cards

**Priority:** Must-Have (Launch)

---

### EPIC EP-005: Premium Affluent Experience
**Module:** Cards (Premium Tier)  
**Objective:** Attract and retain affluent customers with premium subscription offering best-in-class lifestyle benefits

**Linked Features:** FE-005 (Premium Tier)  
**Linked Hypotheses:** HY-003 (Premium tier drives ARPU and loyalty)  
**Source UX Risks:** UXR-004 (Value perception)

**Success Metrics:**
- 15-20% of customer base upgrades to premium within 12 months
- NPS 80+ for premium tier customers
- <10% premium churn rate monthly
- AED 2,400-3,000 annual revenue per premium customer
- 60%+ premium customers use concierge service at least once per month

**Priority:** Should-Have (Wave 2A)

---

### EPIC EP-006: Halal Wealth Building
**Module:** Investments  
**Objective:** Democratize access to Sharia-compliant investing with low minimums and AI-powered Halal screening

**Linked Features:** FE-006 (Fractional Halal Shares)  
**Linked Hypotheses:** HY-005 (Investment access drives differentiation and AUM)  
**Source UX Risks:** UXR-005 (Risk understanding)

**Success Metrics:**
- 30% of active customers make at least one investment within 12 months
- AED 50M+ assets under management (AUM) within 12 months of launch
- Average investment account balance AED 5,000+
- 80%+ customers complete investment education module before first investment

**Priority:** Must-Have (Launch - basic integration)

---

## STEP 08: USER STORIES

### Epic EP-001: Sharia-Compliant Account Foundation

**Story US-001: Open Profit-Sharing Savings Account**
- **Epic ID:** EP-001
- **Module:** Accounts & Payments
- **Story Points:** 5
- **Title:** As an affluent Muslim customer, I want to open a Sharia-compliant savings account with competitive profit-sharing rates, so that I can grow my wealth while adhering to my religious values
- **Journey Reference:** JY-001 (Open Profit-Sharing Savings Account)
- **Priority:** Must-Have

**Acceptance Criteria:**
1. **Given** I am logged into the app, **When** I navigate to "Add Account" and select "Savings Account", **Then** I see the current profit-sharing rate (e.g., 5.5% p.a.), Sharia certification badge, account features, and minimum deposit requirement (AED 100)
2. **Given** I am creating a savings account, **When** I enter an account nickname and initial deposit amount ≥ AED 100, **Then** the system validates the amount and allows me to proceed
3. **Given** I have entered valid account details, **When** I confirm the account creation, **Then** the system creates the account instantly, generates a unique IBAN, and displays a success message with account details
4. **Given** I have successfully opened a savings account, **When** I view the account details, **Then** I see transparent profit-sharing calculation methodology, expected monthly profit based on current balance, last profit distribution date, and a link to Sharia Supervisory Board certification

**Non-Functional Requirements:**
- Account creation completes within 3 seconds
- IBAN generation follows UAE banking standards
- Sharia certification documentation is accessible via in-app link

**Dependencies:** Core banking system integration, Sharia Supervisory Board approval

---

**Story US-002: Automatic Zakat Calculation and Transfer**
- **Epic ID:** EP-001
- **Module:** Accounts & Payments
- **Story Points:** 3
- **Title:** As a practicing Muslim, I want automatic Zakat calculation on my savings, so that I can fulfill my religious obligation without manual calculation
- **Journey Reference:** Related to JY-001
- **Priority:** Must-Have

**Acceptance Criteria:**
1. **Given** I have a profit-sharing savings account that has held ≥ Nisab (AED 15,027 equivalent) for one lunar year, **When** I access the Zakat Calculator feature, **Then** the system calculates 2.5% Zakat due and displays the amount with calculation breakdown
2. **Given** the Zakat calculator shows an amount due, **When** I choose "Set up Auto-Transfer", **Then** the system allows me to schedule automatic annual Zakat transfer to my chosen charity or L'Imad's Sadaqah fund
3. **Given** I have enabled auto-Zakat transfer, **When** the lunar year anniversary arrives, **Then** the system automatically transfers the calculated Zakat amount and sends me a confirmation notification with tax receipt (if applicable)
4. **Given** I want to review past Zakat payments, **When** I access "Zakat History", **Then** I see a chronological list of all Zakat payments with dates, amounts, recipients, and downloadable receipts

**Non-Functional Requirements:**
- Zakat calculation uses accurate lunar calendar (Hijri calendar integration)
- Nisab threshold updated based on current gold/silver market prices
- Zakat payment history retained for minimum 7 years

---

### Epic EP-002: Lightning-Fast Onboarding

**Story US-003: Scan Emirates ID and Verify Identity**
- **Epic ID:** EP-002
- **Module:** Core Retail Journeys
- **Story Points:** 5
- **Title:** As a UAE resident, I want to open an account by scanning my Emirates ID, so that I can complete onboarding quickly without manual data entry
- **Journey Reference:** JY-002 (Complete Onboarding steps 4-8)
- **Priority:** Must-Have

**Acceptance Criteria:**
1. **Given** I am in the onboarding flow after phone verification, **When** the system prompts Emirates ID scan, **Then** I see clear visual guidance showing how to position the card (front and back) with real-time frame detection
2. **Given** I have positioned my Emirates ID correctly, **When** the system captures the image, **Then** OCR extracts all fields (name, ID number, nationality, DOB, expiry) with 95%+ accuracy and auto-populates the form
3. **Given** the Emirates ID data is extracted, **When** the system verifies with UAE government database (ICP), **Then** verification completes within 10 seconds and returns Pass/Fail status with reason
4. **Given** Emirates ID verification passes, **When** the system prompts facial recognition, **Then** I complete liveness detection (blink, turn head) and the system matches my face to the Emirates ID photo with 98%+ accuracy

**Non-Functional Requirements:**
- Emirates ID scan works in various lighting conditions
- Supports both new (2023+) and old Emirates ID formats
- Government database (ICP) integration has 99.9% uptime SLA
- Fallback to manual review if automated verification fails

**Dependencies:** UAE government ICP API integration, Facial recognition SDK (e.g., Onfido, Jumio)

---

**Story US-004: Receive Instant Virtual Card Upon Account Approval**
- **Epic ID:** EP-002
- **Module:** Core Retail Journeys & Cards
- **Story Points:** 3
- **Title:** As a new customer, I want to receive an instant virtual debit card upon account approval, so that I can start making purchases immediately without waiting for a physical card
- **Journey Reference:** JY-002 (Complete Onboarding step 12-14)
- **Priority:** Must-Have

**Acceptance Criteria:**
1. **Given** I have completed all onboarding steps and my account is approved, **When** the system creates my account, **Then** a virtual debit card is automatically generated with unique 16-digit number, CVV, expiry date linked to my main account
2. **Given** I have received a virtual card, **When** I view the card details screen, **Then** I see the full card number (with show/hide toggle), CVV, expiry, cardholder name, and options to add to Apple Pay, Google Pay, Samsung Pay
3. **Given** I have a virtual card, **When** I tap "Add to Apple Pay" or "Add to Google Pay", **Then** the system tokenizes the card and adds it to my mobile wallet with confirmation message "Card ready for contactless payments"
4. **Given** I have added the virtual card to my mobile wallet, **When** I make my first contactless payment within 24 hours, **Then** I receive a congratulatory push notification and AED 10 cashback bonus

**Non-Functional Requirements:**
- Virtual card issued within 2 seconds of account approval
- Apple Pay / Google Pay tokenization completes within 5 seconds
- Virtual card works immediately for online and contactless transactions

---

### Epic EP-004: Intelligent Spending Control

**Story US-005: Create Virtual Card with Merchant Category Restrictions**
- **Epic ID:** EP-004
- **Module:** Cards
- **Story Points:** 5
- **Title:** As a budget-conscious customer, I want to create virtual cards with specific merchant category restrictions, so that I can prevent overspending in certain categories like dining or entertainment
- **Journey Reference:** JY-004 (Create Virtual Card for Online Shopping)
- **Priority:** Must-Have

**Acceptance Criteria:**
1. **Given** I am on the Cards screen, **When** I tap "Add Virtual Card" and select "Recurring Virtual Card", **Then** I enter a nickname, set a spending limit, and choose allowed merchant categories from a list (Online Retail, Groceries, Dining, Entertainment, Travel, Gas, Utilities, Healthcare, Other)
2. **Given** I have configured merchant category restrictions (e.g., only "Online Retail"), **When** I attempt to use this card at a merchant in a different category (e.g., a restaurant), **Then** the transaction is declined with SMS notification "Transaction declined - merchant category not allowed for [Card Nickname]"
3. **Given** I have a virtual card with a monthly spending limit (e.g., AED 2,000), **When** I have spent AED 1,900 in the current month, **Then** I receive a push notification "You've used 95% of your [Card Nickname] limit (AED 1,900 / AED 2,000)"
4. **Given** I have reached my virtual card spending limit, **When** I attempt another transaction, **Then** the transaction is declined, I receive a notification "Monthly limit reached for [Card Nickname]", and I see an option in-app to increase the limit or wait until next month

**Non-Functional Requirements:**
- Merchant category detection accuracy ≥98% using MCC codes
- Spending limit enforcement in real-time (no overdrafts)
- Limit resets automatically on the 1st of each month

---

## STEP 09: STORY SIZING & QUALITY GATE

### Sizing Review

**Story US-001: Open Profit-Sharing Savings Account**
- **Original Points:** 5
- **Final Points:** 5
- **Sizing Rationale:** Complex story involving core banking system integration, IBAN generation, Sharia profit-sharing calculation logic, and UI for account creation flow. Requires backend, frontend, and compliance validation. 4 acceptance criteria are comprehensive and directly testable. No split required.
- **Split Required:** No
- **Acceptance Criteria Count:** 4
- **Acceptance Criteria Quality:** Pass - All criteria use Given/When/Then format, are testable, cover happy path and edge cases
- **Reviewer Decision:** Approved

---

**Story US-002: Automatic Zakat Calculation**
- **Original Points:** 3
- **Final Points:** 3
- **Sizing Rationale:** Moderate complexity - requires Hijri calendar integration, Nisab threshold tracking (gold/silver prices), auto-transfer scheduling. Backend calculation logic and frontend UI. 4 acceptance criteria are clear and testable. Appropriate for 3 points.
- **Split Required:** No
- **Acceptance Criteria Count:** 4
- **Acceptance Criteria Quality:** Pass - Criteria are specific, measurable, and relevant to Zakat calculation
- **Reviewer Decision:** Approved

---

**Story US-003: Emirates ID Scan and Verify**
- **Original Points:** 5
- **Final Points:** 5
- **Sizing Rationale:** High complexity - OCR integration, government database (ICP) API, facial recognition SDK, liveness detection, error handling for failed scans. Multiple 3rd-party integrations. 4 acceptance criteria cover critical paths. Justifies 5 points.
- **Split Required:** No
- **Acceptance Criteria Count:** 4
- **Acceptance Criteria Quality:** Pass - Criteria specify accuracy thresholds (95%, 98%), timing (10 seconds), and fallback behavior
- **Reviewer Decision:** Approved

---

**Story US-004: Instant Virtual Card Issuance**
- **Original Points:** 3
- **Final Points:** 3
- **Sizing Rationale:** Moderate complexity - card generation logic, Apple/Google Pay tokenization, wallet integration. Some 3rd-party SDK work. 4 acceptance criteria cover issuance, display, wallet integration, and engagement reward. Good fit for 3 points.
- **Split Required:** No
- **Acceptance Criteria Count:** 4
- **Acceptance Criteria Quality:** Pass - Criteria include specific timing requirements (2 seconds, 5 seconds), user actions, system responses
- **Reviewer Decision:** Approved

---

**Story US-005: Virtual Card Merchant Restrictions**
- **Original Points:** 5
- **Final Points:** 5
- **Sizing Rationale:** Complex story - merchant category detection via MCC codes, real-time transaction authorization/decline logic, spending limit tracking, notification system. Requires transaction processing integration and real-time rule engine. 4 comprehensive acceptance criteria justify 5 points.
- **Split Required:** No
- **Acceptance Criteria Count:** 4
- **Acceptance Criteria Quality:** Pass - Criteria test positive flow (creation), negative flow (declines), warnings (95% limit), and recovery (increase limit option)
- **Reviewer Decision:** Approved

---

### Chief Product Reviewer Final Assessment

**Traceability Check:** ✅ Pass
- Research Insights (RS-001 to RS-035) → Competitor Analysis (CA-001 to CA-005) → Hypotheses (HY-001 to HY-010) → Features (FE-001 to FE-006) → Epics (EP-001 to EP-006) → User Stories (US-001 to US-005)
- All IDs follow naming convention; no broken references

**User Story Quality:** ✅ Pass
- All 5 stories use "As a [persona], I want [capability], so that [benefit]" format
- Each story has minimum 4 acceptance criteria
- Acceptance criteria are testable, specific, and relevant to story intent
- No generic or template language; all stories specific to L'Imad context

**Story Sizing:** ✅ Pass
- All stories sized 3-5 points as required
- Sizing rationale provided for each story explains complexity
- No stories flagged for splitting

**Epic Quality:** ✅ Pass
- 6 epics are outcome-oriented (not technical components)
- Each epic has measurable success metrics
- Clear linkage to hypotheses and features

**Open Questions & Assumptions:** ✅ Documented
- Assumptions clearly marked in context section
- Open questions identified for stakeholder clarification

**FINAL DECISION: APPROVED**

**Comments:**
- Comprehensive benchmark covering all 7 banking categories with 35 research insights from UAE, GCC, and global markets
- Strong competitive analysis of 5 relevant players with actionable differentiation opportunities
- 10 testable hypotheses with clear validation methods link research to product strategy
- Feature definitions include clear in-scope/out-of-scope boundaries
- User journeys map complete flows with decision points
- 5 UX risks identified with specific mitigations
- 6 epics with measurable success metrics
- 5 sample user stories demonstrate framework compliance (actual backlog will contain 100+ stories across all categories)
- All quality gates passed; ready for stakeholder review and development planning

---

**Framework Execution Complete**  
**Date:** May 28, 2026  
**Outputs:** limad_digital_bank_benchmark_output.yaml, limad_digital_bank_benchmark_output.xlsx, limad_executive_summary.md, limad_feature_catalog.md
