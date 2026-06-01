# L'IMAD DIGITAL BANK - USER FLOW MAPPING DOCUMENT
## Core Retail Banking Journeys & Sub-Journeys

**Version:** 2.0  
**Date:** May 28, 2026  
**Updated:** Per client requirements for core journey structure  
**Framework:** Product Manager Multi-Agent Framework v1.0.0

---

## DOCUMENT PURPOSE

This document provides detailed user flow mappings for all core retail banking journeys at L'Imad Digital Bank. Each journey is broken down into sub-journeys with step-by-step user flows, decision points, system responses, and edge cases.

**Core Journeys Covered:**
1. Account Opening
2. Onboarding
3. Login & Authentication
4. Account Management
5. Deposits
6. Servicing

---

# JOURNEY 1: ACCOUNT OPENING

## Overview
**Purpose:** Enable prospective customers to initiate and complete the account opening process  
**Primary Users:** New customers (affluent UAE residents)  
**Success Criteria:** Account approved and ready for onboarding  
**Average Duration:** 5-8 minutes  
**Launch Phase:** Must-Have

---

## Sub-Journey 1.1: Application Initiation

### User Flow JY-1.1: Start Account Application

**Entry Points:**
- Download app from App Store / Google Play
- Click "Open Account" on marketing website
- Referral link from existing customer
- QR code from marketing materials

**Flow Steps:**

1. **Landing Screen**
   - User: Opens L'Imad app for first time
   - System: Displays welcome screen with "Open Account" CTA
   - System: Shows benefits carousel (Sharia-compliant, 5-6% profit-sharing, free transfers)

2. **Phone Number Entry**
   - User: Taps "Open Account"
   - System: Requests phone number (UAE format: +971 XX XXX XXXX)
   - User: Enters phone number
   - System: Validates format (must be UAE mobile number)
   - **Decision Point:** Valid number? → YES: Continue | NO: Show error "Please enter valid UAE mobile number"

3. **OTP Verification**
   - System: Sends 6-digit OTP via SMS
   - System: Displays OTP entry screen with 60-second countdown timer
   - User: Enters OTP
   - System: Verifies OTP against backend
   - **Decision Point:** Correct OTP? → YES: Continue | NO: Allow retry (max 3 attempts)
   - **Edge Case:** OTP not received → "Resend OTP" button appears after 30 seconds

4. **Eligibility Check**
   - System: Displays eligibility criteria screen
   - System: Shows checklist:
     - ✓ 18 years or older
     - ✓ UAE resident with valid Emirates ID
     - ✓ Not a US person (for tax purposes)
     - ✓ Not a politically exposed person (PEP)
   - User: Confirms eligibility by checking boxes
   - User: Taps "Continue"

**Success Outcome:** Phone verified, eligibility confirmed, ready for Emirates ID verification

**Exit Points:**
- User exits app → Save progress, allow resume within 7 days
- Invalid phone number → Loop back to phone entry
- Failed OTP 3 times → Locked for 1 hour, contact support message

---

## Sub-Journey 1.2: Identity Verification (Emirates ID)

### User Flow JY-1.2: Emirates ID Scan and Verification

**Prerequisite:** Phone number verified, eligibility confirmed

**Flow Steps:**

1. **Emirates ID Scan Introduction**
   - System: Displays instruction screen with visual guide
   - System: Shows sample Emirates ID positioning in frame
   - System: Lists requirements: "Good lighting, flat surface, avoid glare"
   - User: Taps "Scan Front of Emirates ID"

2. **Front Side Scan**
   - System: Opens camera with overlay frame
   - System: Provides real-time feedback: "Move closer", "Reduce glare", "Hold steady"
   - User: Positions Emirates ID (front) within frame
   - System: Auto-captures when positioned correctly
   - System: OCR extracts data (Name, ID Number, DOB, Nationality, Expiry Date)
   - **Decision Point:** Successful extraction? → YES: Continue | NO: Retry with better positioning

3. **Back Side Scan**
   - System: Prompts "Now scan back of Emirates ID"
   - User: Flips card and positions back side
   - System: Auto-captures back image
   - System: Extracts additional data (Address, Occupation if visible)
   - **Decision Point:** Successful extraction? → YES: Continue | NO: Retry

4. **Government Database Verification (ICP)**
   - System: Displays "Verifying with UAE authorities..." with loading indicator
   - System: Calls UAE government ICP API with extracted data
   - System: Waits for response (5-10 seconds)
   - **Decision Point:** Verification result?
     - ✓ **Verified:** Continue to facial recognition
     - ✗ **Failed:** Show error "Unable to verify Emirates ID. Please ensure it's valid and not expired"
     - ⚠ **Manual Review Required:** Tag application for back-office review, notify user "Additional verification needed - we'll contact you within 24 hours"

5. **Data Confirmation**
   - System: Displays extracted data in editable form
   - System: Pre-populates: Full Name, Emirates ID Number, DOB, Nationality, Expiry Date, Address
   - User: Reviews and corrects any OCR errors
   - User: Confirms data accuracy
   - User: Taps "Confirm Details"

**Success Outcome:** Emirates ID verified via government database, data extracted and confirmed

**Exit Points:**
- Failed scan after 3 attempts → Offer manual entry option
- Government verification failed → Escalate to manual review queue
- User exits → Save progress with captured images

---

## Sub-Journey 1.3: Biometric Verification (Facial Recognition)

### User Flow JY-1.3: Facial Recognition with Liveness Detection

**Prerequisite:** Emirates ID verified

**Flow Steps:**

1. **Facial Recognition Introduction**
   - System: Displays instruction screen
   - System: Shows animation of proper positioning (face centered, well-lit, remove glasses/hijab if covering face)
   - System: Notes: "We'll ask you to blink and turn your head to verify you're a real person"
   - User: Taps "Start Facial Recognition"

2. **Face Capture**
   - System: Opens front camera with face overlay guide
   - System: Provides real-time feedback: "Move closer", "Look directly at camera", "Improve lighting"
   - User: Positions face within oval guide
   - System: Auto-captures face when positioned correctly

3. **Liveness Detection - Step 1 (Blink)**
   - System: Displays instruction "Please blink twice"
   - User: Blinks twice
   - System: Detects blink using facial landmark tracking
   - **Decision Point:** Blink detected? → YES: Continue | NO: Prompt again (max 2 retries)

4. **Liveness Detection - Step 2 (Head Turn)**
   - System: Displays instruction "Slowly turn your head to the left"
   - User: Turns head left
   - System: Detects head rotation angle
   - System: Displays instruction "Now slowly turn your head to the right"
   - User: Turns head right
   - System: Detects head rotation
   - **Decision Point:** Both rotations detected? → YES: Continue | NO: Retry

5. **Face Matching**
   - System: Displays "Verifying your identity..." with loading indicator
   - System: Compares live face capture with Emirates ID photo
   - System: Uses facial recognition algorithm (target: 98%+ confidence match)
   - **Decision Point:** Match result?
     - ✓ **High Confidence Match (98%+):** Continue to account details
     - ⚠ **Medium Confidence (90-97%):** Flag for manual review, allow user to continue
     - ✗ **Low Confidence (<90%):** Request retry, offer manual verification via video call

**Success Outcome:** Live face matched to Emirates ID photo with high confidence

**Exit Points:**
- Failed liveness detection (3 attempts) → Offer video call verification
- Failed face match → Retry capture, then escalate to video verification
- Camera permission denied → Show instruction to enable camera in settings

**Accessibility Considerations:**
- **Hijab Wearers:** Face matching works with hijab as long as face is visible
- **Glasses:** System should work with glasses; prompt removal only if glare detected
- **Disabilities:** Alternative verification via video call available

---

## Sub-Journey 1.4: Personal Information Collection

### User Flow JY-1.4: Complete Personal Details

**Prerequisite:** Identity verified (Emirates ID + Facial Recognition)

**Flow Steps:**

1. **Address Confirmation**
   - System: Displays address extracted from Emirates ID (pre-populated)
   - User: Confirms or edits address
   - User: Adds additional address details (Building name, Apartment number)
   - **Decision Point:** Address in UAE? → YES: Continue | NO: Show error "Must have UAE residential address"

2. **Occupation and Income**
   - System: Requests occupation information
   - User: Selects occupation category from dropdown (Professional, Business Owner, Employed, Self-Employed, Retired, Student)
   - User: Enters employer name (if employed)
   - User: Selects estimated monthly income range:
     - AED 10,000 - 20,000
     - AED 20,000 - 30,000
     - AED 30,000 - 50,000
     - AED 50,000 - 100,000
     - AED 100,000+ (Affluent tier trigger)
   - **Decision Point:** Income < AED 10,000? → Flag for review (target is affluent segment)

3. **Source of Funds (AML/KYC)**
   - System: Requests primary source of funds
   - User: Selects from list:
     - Salary/Employment Income
     - Business Profits
     - Investment Returns
     - Inheritance/Gift
     - Savings
     - Other (specify)
   - **Decision Point:** "Other" or suspicious source? → Flag for enhanced due diligence

4. **Tax Residency (FATCA/CRS Compliance)**
   - System: Asks "Are you a tax resident of any country other than UAE?"
   - User: Selects "No" or "Yes"
   - **If Yes:**
     - User: Selects countries from list
     - User: Enters Tax Identification Number (TIN) for each country
     - System: Records for CRS reporting

5. **PEP Declaration**
   - System: Displays PEP definition and examples
   - System: Asks "Are you or any immediate family member a Politically Exposed Person (PEP)?"
   - User: Selects "No" or "Yes"
   - **If Yes:**
     - User: Provides details (position, country, relationship)
     - System: Flags for enhanced due diligence and senior management approval

**Success Outcome:** Complete personal profile with AML/KYC data collected

**Exit Points:**
- PEP declaration → Enhanced due diligence workflow (may take 2-5 business days)
- High-risk occupation (e.g., money services, crypto) → Enhanced due diligence
- User exits → Save progress, can resume later

---

## Sub-Journey 1.5: Account Selection and Configuration

### User Flow JY-1.5: Choose Account Type and Settings

**Prerequisite:** Personal information complete

**Flow Steps:**

1. **Account Type Selection**
   - System: Displays available account types with comparison table:
     - **Current Account:** Day-to-day banking, no minimum balance, profit-sharing on average balance
     - **Savings Account:** Higher profit-sharing rate (5-6% p.a.), min balance AED 1,000
     - **Premium Account:** 7% profit-sharing, AED 250/month fee, concierge & lounge access
   - User: Selects desired account type
   - **Decision Point:** Premium selected? → Show premium benefits modal, confirm upgrade intent

2. **Initial Deposit Selection**
   - System: Shows minimum deposit requirement based on account type:
     - Current: AED 100 minimum
     - Savings: AED 1,000 minimum
     - Premium: AED 5,000 minimum
   - User: Enters intended initial deposit amount
   - User: Selects funding method:
     - Transfer from another UAE bank (IBAN required)
     - Cash deposit at partner locations (list provided)
     - Debit card from another bank
   - **Decision Point:** Amount < minimum? → Show error and required minimum

3. **Account Features Configuration**
   - System: Offers optional features to enable:
     - ✓ Apple Pay / Google Pay / Samsung Pay
     - ✓ International transfers enabled
     - ✓ Zakat auto-calculation
     - ✓ Debit card (physical) – 3-5 day delivery
     - ✓ Checkbook (optional, free)
   - User: Selects desired features
   - User: Taps "Continue"

4. **Account Nickname (Optional)**
   - System: Suggests nickname "My Main Account"
   - User: Can customize nickname (e.g., "Salary Account", "Emergency Fund")
   - User: Taps "Continue"

**Success Outcome:** Account type selected, initial deposit planned, features configured

---

## Sub-Journey 1.6: Terms, Consent & Approval

### User Flow JY-1.6: Review Terms and Submit Application

**Prerequisite:** Account configuration complete

**Flow Steps:**

1. **Terms and Conditions Review**
   - System: Displays scrollable terms document
   - System: Highlights key sections:
     - Profit-sharing calculation methodology
     - Fees and charges schedule
     - Account closure terms
     - Data privacy policy
   - User: Scrolls through document
   - System: Enables "I Accept" button only after scrolling to bottom
   - User: Checks "I have read and accept the Terms and Conditions"
   - User: Taps "Accept"

2. **Sharia Compliance Agreement**
   - System: Displays Sharia compliance statement
   - System: Shows Sharia Supervisory Board members and certification
   - System: Explains profit-sharing vs. conventional interest
   - User: Checks "I understand this is a Sharia-compliant account"
   - User: Taps "Continue"

3. **FATCA/CRS Declaration**
   - System: Displays FATCA and CRS self-certification form
   - User: Confirms tax residency declarations
   - User: Signs electronically (signature pad or typed name)
   - System: Records timestamped consent

4. **Data Privacy Consent**
   - System: Displays data privacy notice (GDPR-style)
   - System: Shows how data will be used, stored, shared
   - System: Offers granular consent options:
     - ✓ Essential: Account operation (required, cannot opt out)
     - ☐ Marketing: Promotional emails and SMS (optional)
     - ☐ Analytics: Usage data for service improvement (optional)
     - ☐ Partner Offers: Offers from L'Imad partners (optional)
   - User: Selects consent preferences
   - User: Taps "Confirm Consents"

5. **Application Summary & Submission**
   - System: Displays application summary:
     - Personal details
     - Account type
     - Initial deposit amount
     - Selected features
   - System: Shows "Review carefully - you can edit before submitting"
   - User: Reviews all information
   - **Decision Point:** Need changes? → "Edit" buttons for each section → Return to relevant sub-journey
   - User: Taps "Submit Application"

6. **Application Processing**
   - System: Displays "Processing your application..." with progress indicator
   - System: Runs automated checks:
     - ✓ Sanctions screening (OFAC, UN, UAE lists)
     - ✓ Credit bureau check (if applicable)
     - ✓ Fraud detection algorithms
     - ✓ Duplicate account check
   - System: Processing time: 10-30 seconds
   - **Decision Point:** Automated approval result?
     - ✓ **Approved:** Continue to onboarding immediately
     - ⚠ **Manual Review Required:** "Your application is under review - we'll notify you within 24 hours"
     - ✗ **Rejected:** Show rejection reason and next steps (appeal process)

**Success Outcome:** Application approved, account created, ready for onboarding

**Exit Points:**
- Manual review required → Email and SMS sent, application queued for back-office
- Rejected → Show reason (sanctions hit, fraud concern) and contact details for support
- User exits → Application saved as draft, can resume via email link

---

## Journey 1 Success Metrics

**Target Metrics:**
- Application initiation to submission: <8 minutes (median)
- Automated approval rate: 85%+
- Emirates ID scan success rate (first attempt): 80%+
- Facial recognition match success: 90%+
- Drop-off rate: <15% at any single step
- Application approval time (automated): <30 seconds
- Manual review turnaround: <24 hours

---

# JOURNEY 2: ONBOARDING

## Overview
**Purpose:** Welcome approved customers and guide them through initial account setup  
**Primary Users:** Newly approved customers (immediately after Account Opening)  
**Success Criteria:** Customer has functional account with IBAN, virtual card, and understanding of key features  
**Average Duration:** 3-5 minutes  
**Launch Phase:** Must-Have

---

## Sub-Journey 2.1: Welcome and Account Activation

### User Flow JY-2.1: Account Activation and Welcome

**Entry Point:** Immediately after account approval (or via email/SMS link if user closed app)

**Flow Steps:**

1. **Welcome Screen**
   - System: Displays celebration animation "Welcome to L'Imad! Your account is approved"
   - System: Shows personalized message with customer's first name
   - System: Displays key benefits carousel:
     - "5-6% profit-sharing on your savings"
     - "Free domestic and international transfers"
     - "Instant virtual card ready now"
     - "Sharia-compliant banking you can trust"
   - User: Taps "Get Started"

2. **IBAN Assignment**
   - System: Generates unique IBAN (UAE format: AE XX LIMAD XXXX XXXX XXXX XXX)
   - System: Displays IBAN prominently with "Your Account Number"
   - System: Shows copy button and share button
   - User: Taps "Copy IBAN" or "Share IBAN" (to email/SMS for salary transfer setup)
   - System: Confirmation "IBAN copied to clipboard"

3. **Initial Funding Reminder**
   - System: Shows "Ready to fund your account?"
   - System: Displays minimum deposit reminder based on account type
   - System: Lists funding options:
     - Transfer from another bank (show IBAN again)
     - Cash deposit at partner locations
     - Link debit card for transfer
   - User: Selects "Fund Now" or "Remind Me Later"
   - **If Fund Now:** Jump to Sub-Journey 5.1 (Deposits - External Transfer)
   - **If Later:** Continue onboarding

**Success Outcome:** Customer sees IBAN, understands funding options

---

## Sub-Journey 2.2: Virtual Card Issuance

### User Flow JY-2.2: Instant Virtual Debit Card

**Prerequisite:** IBAN assigned

**Flow Steps:**

1. **Virtual Card Introduction**
   - System: Displays "Your instant virtual card is ready!"
   - System: Shows benefits:
     - "Shop online immediately"
     - "Add to Apple Pay / Google Pay"
     - "Safe for online shopping (can be frozen instantly)"
   - User: Taps "View My Card"

2. **Virtual Card Reveal**
   - System: Displays animated virtual card (L'Imad branded design)
   - System: Shows card details:
     - 16-digit card number (with show/hide toggle for security)
     - Cardholder name
     - Expiry date (4 years from issue)
     - CVV (3 digits, with show/hide toggle)
   - System: Shows "Copy Card Number" and "Copy CVV" buttons
   - User: Views card details

3. **Digital Wallet Integration**
   - System: Displays "Add to your mobile wallet for contactless payments"
   - System: Shows buttons: "Add to Apple Pay" | "Add to Google Pay" | "Add to Samsung Pay"
   - User: Selects preferred wallet (or "Skip for Now")
   - **If Add to Wallet:**
     - System: Initiates wallet tokenization process
     - System: Opens Apple/Google/Samsung Pay with card pre-loaded
     - User: Confirms card addition in wallet app
     - System: Returns to L'Imad app with confirmation "Card added to [Wallet]!"

4. **First Purchase Incentive**
   - System: Displays offer "Make your first purchase within 7 days and earn AED 50 cashback!"
   - System: Shows progress tracker: "0% complete - Make first purchase"
   - User: Acknowledges offer
   - User: Taps "Continue"

**Success Outcome:** Virtual card issued, optionally added to digital wallet, customer can make purchases immediately

---

## Sub-Journey 2.3: Security Setup

### User Flow JY-2.3: Biometric Login and Security Preferences

**Prerequisite:** Virtual card issued

**Flow Steps:**

1. **Biometric Login Setup**
   - System: Displays "Set up secure login"
   - System: Detects device capabilities (Face ID / Touch ID / Fingerprint)
   - **Decision Point:** Biometric available?
     - **If Yes (Face ID):**
       - System: Requests "Enable Face ID for secure login?"
       - User: Taps "Enable Face ID"
       - System: iOS prompts Face ID enrollment
       - User: Authenticates with Face ID
       - System: Confirmation "Face ID enabled"
     - **If Yes (Touch ID / Fingerprint):**
       - System: Requests "Enable fingerprint login?"
       - User: Taps "Enable"
       - System: Android/iOS prompts fingerprint authentication
       - User: Authenticates with fingerprint
       - System: Confirmation "Fingerprint login enabled"
     - **If No biometric:**
       - System: Skips to PIN setup

2. **6-Digit PIN Setup (Backup Method)**
   - System: Displays "Create a 6-digit PIN for backup access"
   - User: Enters 6-digit PIN
   - System: Validates (cannot be 000000, 123456, or repeated digits)
   - User: Re-enters PIN to confirm
   - System: Validates match
   - **Decision Point:** PINs match? → YES: Continue | NO: Retry
   - System: Confirmation "PIN created successfully"

3. **Transaction Notification Preferences**
   - System: Displays "Stay informed about your transactions"
   - System: Shows notification preference toggles:
     - ✓ Push notifications (recommended, default ON)
     - ✓ SMS for transactions over AED 1,000 (default ON)
     - ☐ Email transaction summaries (default OFF)
   - User: Adjusts preferences
   - User: Taps "Save Preferences"

4. **Spending Limits Setup (Optional)**
   - System: Offers "Set daily spending limits for added security?"
   - User: Selects "Set Limits" or "Skip"
   - **If Set Limits:**
     - System: Shows default limits:
       - Daily card purchases: AED 10,000
       - Daily ATM withdrawals: AED 5,000
       - Daily transfers: AED 50,000
     - User: Adjusts limits using sliders
     - User: Taps "Save Limits"
   - **If Skip:** Continue with default limits

**Success Outcome:** Biometric login enabled, PIN created, security preferences set

---

## Sub-Journey 2.4: Account Personalization

### User Flow JY-2.4: Customize Experience and Set Goals

**Prerequisite:** Security setup complete

**Flow Steps:**

1. **Account Nickname**
   - System: Displays "Personalize your account"
   - System: Shows default nickname "Main Account" (editable field)
   - User: Edits to preferred name (e.g., "My Salary Account", "Emergency Fund")
   - User: Taps "Continue"

2. **Financial Goals Setup (Optional)**
   - System: Asks "Do you have any savings goals?"
   - User: Selects "Yes" or "Not Now"
   - **If Yes:**
     - System: Shows goal templates:
       - Emergency Fund (3-6 months expenses)
       - Home Down Payment
       - Education
       - Hajj/Umrah
       - Wedding
       - Vacation
       - Custom Goal
     - User: Selects goal(s)
     - For each goal:
       - User: Enters target amount (e.g., AED 50,000)
       - User: Selects target date
       - User: Enters optional monthly contribution
       - System: Creates sub-account for goal with progress tracker
     - System: Confirmation "Goal created! Start saving toward [Goal Name]"

3. **Zakat Setup (Sharia Feature)**
   - System: Displays "Set up automatic Zakat calculation?"
   - System: Explains: "We'll track your Nisab (minimum wealth) and calculate 2.5% Zakat automatically"
   - User: Selects "Enable Auto-Zakat" or "I'll Calculate Manually"
   - **If Enable:**
     - System: Sets up Zakat tracking on all accounts
     - System: Asks "Where should we transfer your Zakat when due?"
       - L'Imad Sadaqah Fund
       - Specific charity (user enters details)
       - Remind me (no auto-transfer)
     - User: Selects preference
     - System: Confirmation "Zakat auto-calculation enabled"

4. **Referral Program Introduction**
   - System: Displays "Invite friends and earn AED 100 each"
   - System: Shows referral mechanics:
     - "You: AED 100 when friend opens account"
     - "Friend: AED 100 welcome bonus"
   - System: Shows unique referral code and link
   - User: Taps "Copy Link" or "Share" (WhatsApp, SMS, Email)
   - System: Tracks referral link generation

**Success Outcome:** Account personalized, goals optionally set, Zakat configured, referral link shared

---

## Sub-Journey 2.5: Feature Discovery and Education

### User Flow JY-2.5: Guided Tour of Key Features

**Prerequisite:** Account personalization complete

**Flow Steps:**

1. **Interactive Feature Tour**
   - System: Displays "Let's show you around" with "Take Tour" or "Skip" options
   - User: Selects "Take Tour" (recommended) or "Skip"
   - **If Take Tour:**
     - System: Shows tooltips overlaid on actual app interface (5 steps):
       - Step 1: "This is your home screen - see balances and recent transactions"
       - Step 2: "Tap Cards to view your virtual card and create more"
       - Step 3: "Tap Transfers to send money instantly - free domestic!"
       - Step 4: "Tap Invest to start growing your wealth (Halal investments from AED 10)"
       - Step 5: "Tap More for settings, support, and account management"
     - User: Taps "Next" through each step
     - System: Highlights relevant UI sections during each step

2. **Key Feature Highlights**
   - System: Displays "New features you'll love:"
     - ✨ Unlimited virtual cards with spending controls
     - ✨ Free international transfers to 50+ countries
     - ✨ AI spending insights coming soon (Wave 2A)
     - ✨ Upgrade to Premium for concierge & lounges
   - User: Scrolls through feature cards
   - User: Taps "Got It"

3. **Help Resources Introduction**
   - System: Shows "Need help? We're here for you"
   - System: Lists support options:
     - 24/7 Chat support (tap chat icon in app)
     - FAQ library (searchable)
     - Video tutorials
     - Call support: +971 X XXXX XXXX
   - User: Taps "Continue"

4. **Onboarding Completion Celebration**
   - System: Displays "You're all set! Welcome to L'Imad 🎉"
   - System: Shows onboarding completion checklist:
     - ✓ Account approved with IBAN
     - ✓ Virtual card ready
     - ✓ Security enabled
     - ✓ Preferences set
   - System: Shows next steps:
     - → Fund your account to start earning profit-sharing
     - → Make your first purchase for AED 50 cashback
     - → Invite friends to earn AED 100 each
   - User: Taps "Start Banking"

**Success Outcome:** Customer understands key features, knows how to get help, onboarding complete

**Exit Points:**
- User can skip tour → Directly to home screen
- Tour is dismissible at any step → User goes to home screen
- Onboarding can be revisited later → "Help > Onboarding Tour" in menu

---

## Journey 2 Success Metrics

**Target Metrics:**
- Onboarding completion rate: 95%+ (of approved customers)
- Time to complete onboarding: <5 minutes (median)
- Virtual card activation rate: 100% (auto-issued)
- Digital wallet addition rate: 70%+
- Biometric login setup rate: 90%+
- Financial goal creation rate: 40%+
- Tour completion rate: 80%+
- First transaction within 24 hours: 60%+
- First transaction within 7 days: 85%+

---

# JOURNEY 3: LOGIN & AUTHENTICATION

## Overview
**Purpose:** Securely authenticate users for app access and sensitive operations  
**Primary Users:** All customers  
**Success Criteria:** Fast, secure authentication with minimal friction for returning users  
**Average Duration:** <5 seconds (biometric) to 30 seconds (password reset)  
**Launch Phase:** Must-Have

---

## Sub-Journey 3.1: Standard Login

### User Flow JY-3.1: App Launch and Biometric Login

**Entry Point:** User opens L'Imad app on registered device

**Flow Steps:**

1. **App Launch**
   - User: Taps L'Imad app icon
   - System: Checks device registration status
   - **Decision Point:** Recognized device?
     - **YES:** Continue to biometric prompt
     - **NO:** Redirect to Sub-Journey 3.3 (New Device Login)

2. **Biometric Authentication Prompt**
   - System: Displays L'Imad splash screen
   - System: Triggers biometric prompt (Face ID / Touch ID / Fingerprint)
   - System: Shows message "Unlock with [Face ID / Fingerprint]"
   - User: Authenticates with biometric
   - **Decision Point:** Biometric success?
     - **✓ Success:** Load home screen immediately (<2 seconds)
     - **✗ Failure:** Offer retry (up to 3 attempts) or "Use PIN" option

3. **PIN Fallback (If Biometric Fails)**
   - System: Displays "Enter your 6-digit PIN"
   - User: Enters 6-digit PIN using on-screen keypad
   - System: Validates PIN against backend
   - **Decision Point:** PIN correct?
     - **✓ Correct:** Load home screen
     - **✗ Incorrect:** Show "Incorrect PIN" with remaining attempts (3 total)
     - **✗ Failed 3 times:** Lock account for 1 hour, show "Too many attempts. Try again in 1 hour or contact support"

**Success Outcome:** User authenticated and home screen loaded in <5 seconds

**Edge Cases:**
- Biometric hardware failure → Automatically fallback to PIN
- Network connectivity issues → Show cached account data with banner "Offline mode - some features unavailable"

---

## Sub-Journey 3.2: First-Time Login (Post-Onboarding)

### User Flow JY-3.2: Initial Login After Account Activation

**Entry Point:** User returns to app after onboarding completion (may have closed app)

**Flow Steps:**

1. **Device Recognition**
   - System: Checks if biometric was set up during onboarding
   - **Decision Point:** Biometric configured?
     - **YES:** Use standard login (JY-3.1)
     - **NO:** Prompt to set up biometric now (optional)

2. **Optional Biometric Setup (If Skipped During Onboarding)**
   - System: Shows "Set up [Face ID / Fingerprint] for faster login?"
   - User: Selects "Enable" or "Use PIN Only"
   - **If Enable:**
     - System: Requests biometric enrollment
     - User: Completes biometric authentication
     - System: Saves biometric credential
     - System: Confirmation "Biometric login enabled"
   - **If Use PIN Only:**
     - System: Requests 6-digit PIN
     - User: Enters PIN
     - System: Validates and logs in

**Success Outcome:** User logged in with chosen authentication method

---

## Sub-Journey 3.3: New Device Login

### User Flow JY-3.3: Login from Unrecognized Device

**Entry Point:** User opens L'Imad app on new device (different phone, tablet, or after app reinstall)

**Flow Steps:**

1. **Device Detection**
   - System: Detects unrecognized device (no stored credentials)
   - System: Displays "Welcome back! Log in to continue"
   - System: Shows login options:
     - Phone Number + OTP
     - Emirates ID Number + PIN

2. **Phone Number Login**
   - User: Enters registered phone number (+971 XX XXX XXXX)
   - System: Validates number format
   - System: Sends 6-digit OTP to registered phone
   - User: Enters OTP
   - System: Verifies OTP
   - **Decision Point:** OTP correct?
     - **✓ Correct:** Continue to device authorization
     - **✗ Incorrect:** Allow retry (3 attempts), then lock for 1 hour

3. **Device Authorization**
   - System: Displays "New device detected"
   - System: Shows notification "We've sent a notification to your primary device"
   - System (on primary device): Sends push notification "New login attempt on [Device Name]"
   - **On Primary Device:**
     - User: Opens notification
     - System: Shows "Approve this login? Device: [Device Name], Location: [City], Time: [Timestamp]"
     - User: Taps "Approve" or "Deny"
   - **Back on New Device:**
     - **If Approved:** Continue to device setup
     - **If Denied:** Show "Login denied. Contact support if this wasn't you"
     - **If No Response (2 minutes):** Show "Approval timeout. Try again or contact support"

4. **Device Registration**
   - System: Displays "Set up this device for future quick access"
   - User: Decides to enable biometric for this device
   - User: Completes biometric enrollment
   - System: Saves device fingerprint (device ID + biometric)
   - System: Logs user in and loads home screen

**Success Outcome:** New device authorized and registered for future biometric login

**Security Features:**
- Primary device approval required (2FA)
- Geolocation tracking for suspicious activity
- Email notification sent after successful new device login
- Option to revoke device access in account settings

---

## Sub-Journey 3.4: Password/PIN Reset

### User Flow JY-3.4: Forgotten PIN Recovery

**Entry Point:** User taps "Forgot PIN?" on login screen

**Flow Steps:**

1. **Identity Verification**
   - System: Displays "Let's verify your identity"
   - System: Requests Emirates ID number
   - User: Enters Emirates ID number
   - System: Validates against account records
   - **Decision Point:** Match found?
     - **YES:** Continue to OTP verification
     - **NO:** Show error "Emirates ID not recognized. Contact support"

2. **OTP Verification**
   - System: Sends OTP to registered phone and email
   - System: Displays "Enter the 6-digit code sent to ••• •••• X732 and c••••••n@example.com"
   - User: Enters OTP
   - System: Validates OTP
   - **Decision Point:** OTP correct?
     - **✓ Correct:** Continue to PIN reset
     - **✗ Incorrect:** Allow retry (3 attempts)

3. **New PIN Creation**
   - System: Displays "Create a new 6-digit PIN"
   - User: Enters new 6-digit PIN
   - System: Validates PIN rules:
     - Cannot be same as previous PIN
     - Cannot be simple patterns (000000, 123456, 111111)
     - Must be 6 digits
   - User: Re-enters new PIN to confirm
   - System: Validates match
   - **Decision Point:** PINs match and valid?
     - **✓ Yes:** Save new PIN
     - **✗ No:** Show error and retry

4. **Reset Confirmation**
   - System: Displays "PIN successfully reset"
   - System: Sends confirmation email and SMS
   - System: Logs user in with new PIN
   - System: Prompts "Set up biometric login now for faster access?"
   - User: Chooses to enable biometric or skip

**Success Outcome:** PIN reset successful, user logged in

**Security Measures:**
- PIN reset requires Emirates ID + OTP (2-factor verification)
- Notification sent to email after PIN reset
- Account temporarily flagged for monitoring after reset
- Limited reset attempts (3 per day) to prevent brute force

---

## Sub-Journey 3.5: Step-Up Authentication (Sensitive Operations)

### User Flow JY-3.5: Re-Authentication for High-Risk Actions

**Entry Point:** User attempts sensitive operation (large transfer, settings change, account closure)

**Sensitive Operations Requiring Step-Up:**
- Transfers over AED 10,000
- Adding new beneficiary
- Changing phone number or email
- Disabling security features
- Account closure request
- Viewing full card number/CVV

**Flow Steps:**

1. **Step-Up Trigger**
   - User: Initiates sensitive operation (e.g., "Add New Beneficiary")
   - System: Displays "Additional authentication required for your security"
   - System: Shows reason "Adding new beneficiaries requires re-authentication"

2. **Re-Authentication Prompt**
   - System: Requests authentication method:
     - **Option 1:** Biometric (if enabled) - preferred
     - **Option 2:** 6-digit PIN
     - **Option 3:** OTP to registered phone (fallback)
   - User: Authenticates using chosen method
   - System: Validates authentication
   - **Decision Point:** Authentication successful?
     - **✓ Success:** Grant access to sensitive operation with 5-minute session
     - **✗ Failure:** Show error, allow retry (3 attempts max)

3. **Time-Limited Session**
   - System: Creates step-up session valid for 5 minutes
   - System: Shows banner "Secure session active for [time remaining]"
   - User: Completes sensitive operation(s) within window
   - System: Auto-expires session after 5 minutes of inactivity
   - **Decision Point:** Session expired?
     - System: Requires re-authentication for next sensitive operation

**Success Outcome:** User authenticated for sensitive operation, completed securely

**Security Features:**
- Biometric preferred over PIN for step-up
- Session timeout after 5 minutes
- No session persistence (each sensitive operation may require new step-up)
- Audit log records all step-up authentications

---

## Sub-Journey 3.6: Logout and Session Management

### User Flow JY-3.6: Manual Logout and Auto-Logout

**Entry Point:** User chooses to log out or session expires

**Manual Logout Flow:**

1. **User-Initiated Logout**
   - User: Taps "More" → "Logout"
   - System: Displays confirmation "Are you sure you want to log out?"
   - User: Confirms logout
   - System: Clears session token
   - System: Clears cached sensitive data (card numbers, PINs)
   - System: Returns to login screen
   - System: Shows "Logged out successfully. See you soon!"

**Auto-Logout Flow:**

2. **Inactivity Timeout**
   - System: Monitors user activity (tap, scroll, screen interaction)
   - **Decision Point:** No activity for 10 minutes?
     - System: Displays warning "Still there? You'll be logged out in 60 seconds for security"
     - User: Taps "I'm Here" → Reset timer | Ignores → Continue to logout
   - **After 60 seconds:**
     - System: Auto-logout
     - System: Clears session token
     - System: Shows "Logged out due to inactivity" on next app open

3. **Background App Behavior**
   - User: Switches app to background (Home button / app switcher)
   - System: Starts background timer (5 minutes for sensitive screens, 30 minutes for general screens)
   - User: Returns to app within timer
   - **Decision Point:** Timer expired?
     - **NO (<5 or <30 min):** Resume where left off
     - **YES:** Require biometric/PIN re-authentication
   - **If Sensitive Screen (e.g., card details):** Blur/hide screen content in app switcher preview

**Success Outcome:** User logged out securely, session cleared

**Security Measures:**
- Sensitive data not cached after logout
- Biometric credentials remain on device (not cleared)
- App switcher preview hides sensitive information
- Configurable inactivity timeout in settings (5, 10, 15 minutes options)

---

## Journey 3 Success Metrics

**Target Metrics:**
- Biometric login success rate (first attempt): 95%+
- Average login time (biometric): <3 seconds
- Average login time (PIN): <10 seconds
- New device authorization success rate: 85%+
- PIN reset completion rate: 80%+
- Step-up authentication success rate: 90%+
- User complaints about authentication friction: <1% of customers
- False rejection rate (biometric): <5%
- Security incident rate (unauthorized access): <0.01%

---

# JOURNEY 4: ACCOUNT MANAGEMENT

## Overview
**Purpose:** Enable customers to view, modify, and manage their account details, preferences, and settings  
**Primary Users:** All active customers  
**Success Criteria:** Customers can self-serve for account changes without support intervention  
**Average Duration:** Varies by task (2-10 minutes)  
**Launch Phase:** Must-Have

---

## Sub-Journey 4.1: View Account Details and Balances

### User Flow JY-4.1: Dashboard and Account Overview

**Entry Point:** User logs in and lands on home screen

**Flow Steps:**

1. **Home Screen Dashboard**
   - System: Displays home screen with key information:
     - Total Balance (all accounts combined) - Large, prominent display
     - Individual Account Cards (scrollable carousel):
       - Account Nickname (e.g., "Main Account")
       - Account Type (Current / Savings / Premium)
       - Current Balance
       - Available Balance (if holds exist)
       - Profit-sharing rate (e.g., "Earning 5.5% p.a.")
     - Quick Actions Bar:
       - Send Money
       - Add Money
       - Cards
       - Invest
   - User: Scrolls through account cards

2. **Account Detail Drill-Down**
   - User: Taps on specific account card
   - System: Opens account detail screen showing:
     - Account Nickname
     - Account Number (IBAN)
     - Account Type
     - Opening Date
     - Current Balance (large display)
     - Available Balance
     - Profit Earned This Month
     - Profit Earned Year-to-Date
     - Next Profit Distribution Date
     - Recent Transactions (last 10)
   - System: Shows action buttons:
     - View Full Statement
     - Transfer Money
     - Add Funds
     - Account Settings
   - User: Reviews account details

3. **Multiple Account View**
   - System: If customer has multiple accounts, shows "All Accounts" tab
   - User: Taps "All Accounts"
   - System: Displays list view with all accounts:
     - Account Name | Type | Balance | Quick Actions (Transfer, View)
   - System: Shows total across all accounts at top
   - User: Can sort by: Balance (high to low), Account Name (A-Z), Type

**Success Outcome:** User can quickly view balances and account details

---

## Sub-Journey 4.2: Transaction History and Statements

### User Flow JY-4.2: View and Download Transaction History

**Entry Point:** From account detail screen, user taps "View Full Statement"

**Flow Steps:**

1. **Transaction List View**
   - System: Displays transaction history screen
   - System: Shows transactions in reverse chronological order (newest first)
   - System: For each transaction, displays:
     - Merchant/Beneficiary Name
     - Transaction Type (Card Purchase, Transfer Out, Transfer In, Profit Credit, Fee)
     - Amount (color coded: Red for debits, Green for credits)
     - Date & Time
     - Running Balance (after transaction)
     - Transaction ID (small text)
   - System: Shows filters button and search bar

2. **Transaction Search and Filtering**
   - User: Taps "Filter" icon
   - System: Displays filter options:
     - Date Range: Last 7 days, Last 30 days, Last 3 months, Last 12 months, Custom Range
     - Transaction Type: All, Card Purchases, Transfers, Deposits, Profit, Fees
     - Amount Range: Min - Max (slider)
     - Status: All, Completed, Pending, Failed
   - User: Selects filters
   - System: Applies filters and updates transaction list
   - User: Can also search by merchant name or transaction ID in search bar
   - System: Live search results as user types

3. **Transaction Detail View**
   - User: Taps on specific transaction
   - System: Opens transaction detail modal showing:
     - Transaction ID
     - Date & Time (with timezone)
     - Merchant/Beneficiary Name
     - Category (if card purchase: Dining, Shopping, etc.)
     - Amount (with currency)
     - Fee (if applicable)
     - Running Balance After Transaction
     - Payment Method (e.g., Virtual Card ending in 1234)
     - Status (Completed / Pending / Failed)
     - Receipt (if available) - PDF attachment
   - System: Shows action buttons:
     - Download Receipt
     - Dispute Transaction (if card purchase)
     - Export Transaction
     - Contact Support About This Transaction
   - User: Can take action or close modal

4. **Statement Download**
   - User: Taps "Download Statement" button (top right of transaction history)
   - System: Displays statement download options:
     - Format: PDF or Excel
     - Date Range: Select start and end date (date picker)
     - Accounts: Select which accounts to include (if multiple)
     - Email Statement: Toggle to send to registered email
   - User: Selects options
   - User: Taps "Download Statement"
   - System: Generates statement (5-10 seconds)
   - System: Downloads file or sends to email
   - System: Shows confirmation "Statement downloaded / emailed successfully"

**Success Outcome:** User can view, search, filter transactions and download statements

---

## Sub-Journey 4.3: Personal Information Updates

### User Flow JY-4.3: Update Contact Details and Personal Info

**Entry Point:** User navigates to "More" → "Account Settings" → "Personal Information"

**Flow Steps:**

1. **Personal Information Overview**
   - System: Displays current personal information (read-only view):
     - Full Name (from Emirates ID - cannot edit)
     - Emirates ID Number (cannot edit)
     - Date of Birth (cannot edit)
     - Nationality (cannot edit)
     - Email Address (editable)
     - Phone Number (editable)
     - Residential Address (editable)
     - Occupation (editable)
     - Monthly Income Range (editable)
   - System: Shows "Edit" button next to editable fields

2. **Email Address Update**
   - User: Taps "Edit" next to Email Address
   - System: Displays editable email field with current email pre-filled
   - User: Enters new email address
   - System: Validates email format
   - User: Taps "Save"
   - System: Requires step-up authentication (biometric or PIN)
   - User: Authenticates
   - System: Sends verification email to NEW email address with 6-digit code
   - System: Prompts "Enter the verification code sent to [new email]"
   - User: Checks new email inbox, enters 6-digit code
   - System: Validates code
   - **Decision Point:** Code correct?
     - **✓ Correct:** Update email address, send confirmation to old and new email
     - **✗ Incorrect:** Allow retry (3 attempts)
   - System: Shows "Email address updated successfully"

3. **Phone Number Update**
   - User: Taps "Edit" next to Phone Number
   - System: Displays editable phone number field
   - User: Enters new phone number (must be UAE +971)
   - System: Validates UAE phone format
   - User: Taps "Save"
   - System: Requires step-up authentication
   - User: Authenticates
   - System: Sends OTP to NEW phone number
   - System: Prompts "Enter OTP sent to [new number]"
   - User: Enters OTP
   - System: Validates OTP
   - **Decision Point:** OTP correct?
     - **✓ Correct:** Update phone number, send SMS to old and new number
     - **✗ Incorrect:** Allow retry (3 attempts)
   - System: Shows "Phone number updated successfully"
   - System: Note: "You'll use this number for future logins and OTPs"

4. **Address Update**
   - User: Taps "Edit" next to Residential Address
   - System: Displays address form with current address pre-filled:
     - Flat/Villa Number
     - Building Name
     - Street Name
     - Area/District
     - City (dropdown: Dubai, Abu Dhabi, Sharjah, etc.)
     - Emirate (auto-populated based on city)
     - P.O. Box (optional)
   - User: Edits address fields
   - User: Taps "Save"
   - System: Requires step-up authentication
   - User: Authenticates
   - System: Saves new address
   - System: Shows "Address updated successfully"
   - System: Note: "New debit cards will be sent to this address"

5. **Occupation and Income Update**
   - User: Taps "Edit" next to Occupation or Income Range
   - System: Displays dropdown/selection fields
   - User: Updates occupation and/or income range
   - User: Taps "Save"
   - System: Requires step-up authentication (these are KYC fields)
   - User: Authenticates
   - System: Saves changes
   - System: Flags account for potential review if significant income change
   - System: Shows "Information updated successfully"

**Success Outcome:** Personal information updated with verification where needed

**Security Measures:**
- Step-up authentication required for all editable fields
- Email/phone updates require verification on new contact method
- Old contact method notified of change
- Audit trail logged for all changes

---

## Sub-Journey 4.4: Sub-Account Creation and Management

### User Flow JY-4.4: Create and Manage Sub-Accounts (Pots/Spaces)

**Entry Point:** From home screen, user taps "Add Account" or "Create Sub-Account"

**Flow Steps:**

1. **Sub-Account Creation Wizard**
   - System: Displays "Create a new sub-account"
   - System: Shows suggested templates:
     - 💰 Savings Goal (specify target amount and date)
     - 🏠 Bills & Rent (recurring expenses)
     - 🎯 Emergency Fund (recommended 3-6 months expenses)
     - 🎓 Education Fund
     - ✈️ Travel Fund
     - 💍 Wedding Fund
     - 🕋 Hajj/Umrah Fund
     - 🎨 Custom Goal
   - User: Selects template or "Custom Goal"

2. **Sub-Account Configuration**
   - System: Requests sub-account details:
     - **Account Nickname:** (e.g., "Emergency Fund", "Dubai Trip 2027")
     - **Goal Amount:** (optional, for savings goals)
     - **Target Date:** (optional, date picker)
     - **Monthly Auto-Transfer:** (optional, amount to auto-transfer from main account)
     - **Initial Transfer:** (optional, transfer funds now from main account)
   - User: Fills in details
   - User: Taps "Create Sub-Account"

3. **Sub-Account Creation Confirmation**
   - System: Creates sub-account instantly
   - System: Generates unique account number/reference
   - System: Issues dedicated virtual card for this sub-account (optional toggle)
   - System: Shows success screen:
     - "Emergency Fund created!"
     - Current Balance: AED 0 (or initial transfer amount)
     - Goal Progress: 0% of AED 50,000 (if goal set)
     - Next Auto-Transfer: [Date] (if configured)
   - System: Shows action buttons:
     - Add Funds Now
     - Create Virtual Card
     - Set Up Auto-Transfer
     - View Sub-Account

**Sub-Account Management Features:**

4. **View All Sub-Accounts**
   - User: Taps "Accounts" tab
   - System: Shows main account + all sub-accounts in list/card view
   - System: For each sub-account shows:
     - Nickname
     - Current Balance
     - Goal Progress (if applicable): "25% of AED 50,000"
     - Visual progress bar
     - Quick actions: Transfer In, Transfer Out, Settings

5. **Transfer Between Sub-Accounts**
   - User: Taps on sub-account, then "Transfer"
   - System: Displays "Transfer funds"
   - System: Shows "From" dropdown (select source account)
   - System: Shows "To" dropdown (select destination account)
   - User: Enters transfer amount
   - System: Validates sufficient balance
   - User: Taps "Transfer Now"
   - System: Executes instant internal transfer
   - System: Updates both account balances in real-time
   - System: Shows confirmation "AED [amount] transferred from [Source] to [Destination]"

6. **Sub-Account Settings**
   - User: Opens sub-account, taps "Settings"
   - System: Shows settings options:
     - Edit Nickname
     - Edit Goal (amount, date)
     - Auto-Transfer Settings (enable/disable, amount, frequency)
     - Virtual Card (create/view/freeze/delete)
     - Close Sub-Account
   - User: Makes changes
   - User: Taps "Save Changes"
   - System: Updates settings and confirms

7. **Close Sub-Account**
   - User: Taps "Close Sub-Account" in settings
   - System: Displays warning "This will close the sub-account and move remaining funds to your Main Account. Continue?"
   - User: Confirms closure
   - System: Requires step-up authentication
   - User: Authenticates
   - System: Transfers remaining balance to main account
   - System: Closes sub-account
   - System: Archives transaction history (still viewable in main account statements)
   - System: Shows "Sub-account closed. AED [amount] transferred to Main Account"

**Success Outcome:** User can create, manage, transfer between, and close sub-accounts

**Sub-Account Limits:**
- Maximum 20 sub-accounts per customer
- Sub-accounts share main account IBAN (internal routing)
- Each sub-account can have its own virtual card
- Profit-sharing calculated on combined balance across all accounts

---

## Sub-Journey 4.5: Preferences and Settings Management

### User Flow JY-4.5: Manage App Preferences and Communication Settings

**Entry Point:** User navigates to "More" → "Settings" → "Preferences"

**Flow Steps:**

1. **Notification Preferences**
   - System: Displays notification settings with toggles:
     - **Push Notifications:**
       - ✓ Transaction alerts (recommended)
       - ✓ Security alerts (cannot disable)
       - ☐ Marketing offers
       - ☐ Product updates
       - ☐ Tips and insights
     - **SMS Notifications:**
       - ✓ Transactions over AED 1,000
       - ✓ Security alerts (OTPs, login notifications)
       - ☐ Monthly statements
     - **Email Notifications:**
       - ✓ Security alerts
       - ☐ Transaction summaries (daily/weekly/monthly)
       - ☐ Marketing offers
       - ☐ Account statements
   - User: Toggles preferences on/off
   - User: Taps "Save Preferences"
   - System: Saves changes and shows "Preferences updated"

2. **Language and Regional Settings**
   - System: Displays language and format settings:
     - **App Language:** English (default) | العربية (Arabic)
     - **Currency Display:** AED (default) | USD | EUR | GBP
     - **Date Format:** DD/MM/YYYY | MM/DD/YYYY
     - **Time Format:** 24-hour | 12-hour AM/PM
     - **Calendar:** Gregorian | Hijri (Islamic)
   - User: Selects preferences
   - User: Taps "Save"
   - System: Applies settings immediately (may require app refresh for language change)

3. **Privacy Settings**
   - System: Displays privacy controls:
     - **Data Sharing:**
       - ✓ Essential (required for app function)
       - ☐ Usage analytics (help improve app)
       - ☐ Marketing data (personalized offers)
       - ☐ Share with partners (e.g., BNPL, travel)
     - **App Permissions:**
       - Camera: Allowed (for cheque deposits, ID scanning)
       - Location: Allowed when using app (for fraud detection)
       - Contacts: Denied (for easy transfers - optional)
       - Notifications: Allowed
     - System: Shows "Manage in iOS/Android Settings" links for permissions
   - User: Adjusts data sharing preferences
   - User: Taps "Save Privacy Settings"
   - System: Updates backend preferences

4. **Transaction Limits and Controls**
   - System: Displays spending limit settings:
     - **Daily Card Limit:** AED 10,000 (slider: AED 0 - 50,000)
     - **Daily ATM Withdrawal:** AED 5,000 (slider: AED 0 - 10,000)
     - **Daily Transfer Limit:** AED 50,000 (slider: AED 0 - 100,000)
     - **International Transactions:** Enabled (toggle)
     - **Contactless Payments:** Enabled (toggle)
     - **Online Transactions:** Enabled (toggle)
   - User: Adjusts limits using sliders
   - User: Toggles controls on/off
   - User: Taps "Save Limits"
   - System: Requires step-up authentication
   - User: Authenticates
   - System: Applies new limits immediately
   - System: Shows "Spending limits updated"

5. **Auto-Pay and Recurring Transfers**
   - System: Displays recurring payment settings:
     - **List of Active Auto-Pays:**
       - DEWA (Electricity) - AED 500/month - Next: June 5
       - Etisalat (Mobile) - AED 200/month - Next: June 1
       - Savings Auto-Transfer - AED 1,000/month to Emergency Fund - Next: June 1
     - System: Shows "Add New Auto-Pay" button
   - User: Taps on existing auto-pay to edit or disable
   - User: Or taps "Add New Auto-Pay"
   - System: Opens auto-pay setup:
     - Beneficiary Name
     - Amount (fixed or variable with max limit)
     - Frequency (Monthly, Quarterly, Annually, Custom)
     - Start Date
     - End Date (optional, for finite commitments)
   - User: Configures auto-pay
   - User: Taps "Save Auto-Pay"
   - System: Requires step-up authentication
   - User: Authenticates
   - System: Schedules recurring payment
   - System: Shows "Auto-pay created. First payment: [Date]"

**Success Outcome:** User has customized app preferences and controls to match their needs

---

## Sub-Journey 4.6: Document Management

### User Flow JY-4.6: View and Download Account Documents

**Entry Point:** User navigates to "More" → "Documents"

**Flow Steps:**

1. **Document Library Overview**
   - System: Displays document categories:
     - Account Opening Documents (Terms & Conditions, Sharia Agreement)
     - Statements (Monthly/Quarterly/Annual)
     - Tax Documents (Form 1099, FATCA/CRS declarations)
     - Card Documents (Card terms, PIN mailer)
     - Correspondence (Letters, notices from L'Imad)
     - Certificates (Sharia compliance certificate, Account certificate)
   - User: Taps on category to expand

2. **View and Download Statements**
   - User: Taps "Statements" category
   - System: Shows list of available statements:
     - May 2026 Statement - PDF (120 KB)
     - April 2026 Statement - PDF (115 KB)
     - March 2026 Statement - PDF (98 KB)
     - ... (up to 7 years history)
   - User: Taps on statement to view
   - System: Opens PDF viewer in-app
   - User: Can download or share via share button

3. **Generate Account Certificate**
   - User: Taps "Certificates" → "Generate Account Certificate"
   - System: Displays "What do you need this certificate for?"
     - Visa application
     - Loan application
     - Proof of address
     - Salary transfer
     - Other
   - User: Selects purpose
   - System: Generates PDF certificate with:
     - Customer name
     - Account number (IBAN)
     - Account type
     - Opening date
     - Current balance (optional - toggle on/off)
     - Bank letterhead and seal
     - Purpose statement
   - System: Downloads certificate
   - System: Sends email copy
   - System: Shows "Certificate generated and emailed to you"

4. **Request Additional Documents**
   - User: Taps "Request Document"
   - System: Shows document request form:
     - Document Type (dropdown): Account history, Transaction details for specific period, Letter of good standing, Other
     - Purpose (text field)
     - Date range needed (if applicable)
     - Language preference (English / Arabic)
   - User: Fills form
   - User: Taps "Submit Request"
   - System: Creates support ticket
   - System: Shows "Request submitted. We'll email you within 2 business days"

**Success Outcome:** User can access all account documents and generate certificates on-demand

---

## Journey 4 Success Metrics

**Target Metrics:**
- Account balance check frequency: 3-5 times per week (average customer)
- Transaction history views: 60%+ of customers monthly
- Statement downloads: 40%+ of customers quarterly
- Sub-account creation: 50%+ of customers create at least one
- Average sub-accounts per customer: 2-3
- Personal information update success rate: 95%+
- Preference changes: 70%+ of customers customize at least one setting
- Document download success rate: 100%
- Support tickets for account management: <5% of customers monthly

---

*[Document continues with Journeys 5 (Deposits) and 6 (Servicing) in Part 2...]*
