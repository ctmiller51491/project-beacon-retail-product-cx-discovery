# L'IMAD DIGITAL BANK - JOURNEY 7: KYC (KNOW YOUR CUSTOMER)
## Complete User Flow Mapping

**Document Version:** 2.1  
**Date:** June 1, 2026  
**Journey Added:** KYC as separate core retail journey per client request  
**Status:** ✅ Complete

---

## JOURNEY 7 OVERVIEW: KYC (KNOW YOUR CUSTOMER)

**Journey Purpose:** Verify customer identity, assess risk profile, ensure regulatory compliance (UAE Central Bank, AML/CFT, FATCA/CRS), and maintain ongoing due diligence throughout customer lifecycle

**Strategic Context:**
- **UAE Regulatory Requirement:** All digital banks must integrate with National KYC Digital Platform (Federal Decree-Law No. 30/2024)
- **Sharia Compliance:** Source of Wealth/Funds must originate from Sharia-compliant activities
- **Affluent Focus:** Enhanced verification for HNW customers with specialized SoW/SoF requirements
- **Sovereign Banking:** L'Imad's government backing enables unique access to UAE gov systems (ICA, ICP, UAE Pass)

**Success Metrics:**
- **Primary KYC completion rate:** >90% (initial verification during account opening)
- **Average KYC processing time:** <3 minutes for low-risk retail, <10 minutes for affluent
- **False positive rate:** <5% (sanctions/PEP screening)
- **Annual refresh completion:** >95% (scheduled reviews)
- **Regulatory compliance score:** 100% (zero violations)
- **Customer satisfaction:** >4.5/5 (verification process experience)

**Key Differentiators vs. Competitors:**
- Integrated with UAE government systems (ICA, ICP, UAE Pass) for instant verification
- Sharia-compliant SoW verification with specialized documentation
- Affluent-focused KYC with wealth management integration
- Perpetual KYC with real-time monitoring (not just annual reviews)
- Multilingual support (English, Arabic, Hindi, Urdu)

---

## JOURNEY 7 SUB-JOURNEYS (8 Total)

### Sub-Journey Overview

| ID | Sub-Journey Name | User Type | Trigger | Frequency | Complexity | Priority |
|----|------------------|-----------|---------|-----------|------------|----------|
| **JY-7.1** | Initial Identity Verification | New customer | Account opening | Once | High | Launch |
| **JY-7.2** | Document Collection & OCR | All customers | KYC initiation | As needed | Medium | Launch |
| **JY-7.3** | Biometric Verification | All customers | KYC initiation | As needed | Medium | Launch |
| **JY-7.4** | Risk Assessment & Screening | All customers | KYC initiation, periodic | Continuous | High | Launch |
| **JY-7.5** | Enhanced Due Diligence (EDD) | HNW, PEPs, high-risk | Risk triggers | As needed | Very High | Launch |
| **JY-7.6** | Source of Wealth/Funds Verification | Affluent, HNW | Large transactions, EDD | As needed | High | Wave 2A |
| **JY-7.7** | Periodic KYC Refresh | All customers | Schedule or triggers | Annual+ | Medium | Wave 2A |
| **JY-7.8** | Ongoing Monitoring (Perpetual KYC) | All customers | Real-time events | Continuous | High | Wave 2B |

**Launch Phase Focus:** JY-7.1 through JY-7.5 (core verification and compliance)  
**Wave 2A:** JY-7.6 and JY-7.7 (wealth verification and periodic reviews)  
**Wave 2B:** JY-7.8 (perpetual KYC automation)

---

## JY-7.1: INITIAL IDENTITY VERIFICATION

**Purpose:** Verify customer's legal identity using Emirates ID and government databases

**Entry Points:**
- Account opening (new customer)
- Existing customer upgrading from basic to premium account
- Customer re-verifying after document expiry
- Regulatory requirement for reverification

**User Type:** All new customers (retail, affluent, HNW)

**Prerequisites:**
- Customer has valid Emirates ID (UAE nationals/residents)
- Customer has smartphone with camera (for mobile app)
- Customer consents to identity verification and data processing

**Integration Points:**
- **ICA (Federal Authority for Identity & Citizenship):** Emirates ID validation via online gateway
- **ICP (Identity Card Program):** Biometric database cross-reference
- **UAE Pass:** Optional digital identity verification
- **National KYC Digital Platform:** Mandatory integration per UAE law

---

### USER FLOW: JY-7.1 Initial Identity Verification

#### Step 1: Verification Initiation
**User Action:** During account opening, reaches "Verify Your Identity" screen  
**System Response:** 
- Displays verification requirements: "We need to verify your identity to comply with UAE regulations"
- Shows required documents: Emirates ID (front + back)
- Offers two pathways:
  - **Option A:** Emirates ID + facial recognition (faster, 90% of users)
  - **Option B:** Emirates ID + UAE Pass (alternative, 10% of users)
- Displays estimated time: "This will take 2-3 minutes"
- Shows security badges: "Your data is encrypted and secure"

**Decision Point:** User selects verification pathway (A or B)

---

#### Step 2A: Emirates ID Capture (Option A - Standard Path)
**User Action:** Taps "Scan Emirates ID" → positions ID within camera frame guides  
**System Response:**
- Activates camera with real-time overlay guides (front/back card outlines)
- Auto-captures when card detected and in focus (no manual shutter button)
- Shows capture confirmation with checkmark: "Front captured ✓"
- Prompts: "Now scan the back of your card"
- Auto-captures back side
- Shows upload progress: "Uploading securely..."

**Technical Process (Backend):**
- OCR extraction: Name, ID number, nationality, DOB, gender, address, expiry date
- Chip reading (if NFC-enabled phone): Biometric data hash
- MRZ code validation (Machine Readable Zone)
- Document authenticity checks: Security features (holograms, UV patterns, watermarks)

**Edge Cases:**
- **Card not detected:** "Please position card within frame" with visual guides
- **Blurry image:** "Image unclear, please try again" with auto-retry
- **Glare detected:** "Please avoid glare" with lighting tips
- **Expired ID:** "Your Emirates ID expired on [date]. Please renew before continuing"
- **Damaged ID:** Routes to manual review: "We need to verify your ID manually. This may take 24-48 hours"

**SLA Target:** 10 seconds per capture (front + back)

---

#### Step 2B: UAE Pass Verification (Option B - Alternative Path)
**User Action:** Taps "Verify with UAE Pass" → redirected to UAE Pass app  
**System Response:**
- Opens UAE Pass authentication screen
- User authenticates (PIN, biometric, or face recognition)
- UAE Pass shares verified identity data with L'Imad (with user consent)
- Returns to L'Imad app with confirmation: "Identity verified via UAE Pass ✓"

**Data Received from UAE Pass:**
- Verified name, ID number, nationality, DOB
- Address (if consented)
- Digital signature confirming authenticity

**Edge Cases:**
- **UAE Pass not installed:** "Please install UAE Pass app" with App Store/Play Store link
- **UAE Pass authentication failure:** "Authentication failed. Please try Emirates ID scan instead"
- **User cancels UAE Pass flow:** Returns to pathway selection screen

**SLA Target:** 30 seconds (assuming UAE Pass already installed)

---

#### Step 3: ICA Validation
**User Action:** Waits while system validates Emirates ID with government database  
**System Response:**
- Displays progress: "Verifying with government database..." with animated spinner
- Sends Emirates ID number and biometric hash to ICA online gateway (encrypted)
- ICA responds with validation status:
  - ✅ **Valid:** ID is active, not expired, not reported lost/stolen
  - ❌ **Invalid:** ID expired, canceled, or flagged
  - ⚠️ **Pending:** Manual review required (rare cases)

**Decision Point:** 
- **If Valid:** Proceeds to Step 4 (Facial Recognition)
- **If Invalid:** Shows error: "We couldn't verify your Emirates ID. Reason: [expired/canceled/flagged]. Please contact support"
- **If Pending:** Shows message: "Your verification is under review. We'll update you within 24 hours" → triggers manual review queue

**Security Measures:**
- API calls encrypted with TLS 1.3
- Emirates ID number stored encrypted at rest
- Audit log of all ICA queries (compliance requirement)

**SLA Target:** 5 seconds (ICA API response time)

---

#### Step 4: Facial Recognition (Liveness Detection)
**User Action:** Follows on-screen prompts for facial biometric capture  
**System Response:**
- Displays camera with face oval overlay
- Randomized liveness challenges (anti-spoofing):
  - **Active Challenges:** "Smile", "Turn head left", "Blink twice", "Nod slowly"
  - **Passive Challenges:** Micro-movement detection (no user action required)
- Captures 3-5 frames during challenges
- Shows success confirmation: "Face verified ✓"

**Technical Process (Backend):**
- Compares captured face against Emirates ID photo (from OCR or ICA database)
- Facial matching confidence score: Must be >85% to pass
- Liveness detection score: Must be >90% to pass (prevents photo/video spoofing)
- Age estimation: Cross-reference with DOB from Emirates ID (detect mismatch fraud)

**Edge Cases:**
- **Face not detected:** "Please position your face within the oval"
- **Poor lighting:** "Please move to a well-lit area"
- **Match score too low (70-84%):** Routes to video KYC: "We need to verify you via video call"
- **Liveness check fails:** "Please follow the prompts carefully" → retry up to 3 attempts
- **3 failed attempts:** Routes to manual review: "We need to verify manually. This may take 24-48 hours"

**Accessibility:**
- Voice guidance for visually impaired users
- Alternative verification for users unable to complete facial recognition (video KYC with agent)

**SLA Target:** 15 seconds (capture + backend processing)

---

#### Step 5: Cross-Reference Check
**User Action:** Waits while system performs additional verification  
**System Response:**
- Displays: "Finalizing verification..." with progress indicator
- Backend processes:
  1. **ICP Biometric Cross-Reference:** Matches facial biometric against ICP database (if available)
  2. **Address Validation:** Cross-references address from Emirates ID with utility databases (optional)
  3. **Historical Check:** Searches for existing L'Imad accounts under same Emirates ID (duplicate prevention)

**Decision Point:**
- **All checks pass:** Proceeds to Step 6 (Success)
- **Duplicate account found:** Shows error: "You already have an account with L'Imad. Please log in"
- **Biometric mismatch:** Routes to manual review (fraud alert)
- **Address validation fails:** Proceeds but flags for address proof collection later

**SLA Target:** 10 seconds

---

#### Step 6: Verification Success
**User Action:** Receives confirmation that identity is verified  
**System Response:**
- Displays success screen with checkmark animation
- Message: "Identity verified! ✓ Your Emirates ID: [masked: xxxx-xxxx-1234]"
- Next steps displayed: "Next, we'll collect additional documents"
- CTA button: "Continue"
- Progress indicator updated: "Step 1 of 4 complete"

**Backend Actions:**
- Stores verified identity data in customer profile (encrypted)
- Assigns risk category based on nationality, age, address (low/medium/high)
- Triggers next sub-journey: JY-7.2 (Document Collection) or JY-7.4 (Risk Screening) depending on risk level
- Sends confirmation email/SMS: "Your identity has been verified"
- Logs event in audit trail (compliance)

**Data Stored:**
- Verified name, Emirates ID number, nationality, DOB, gender, address
- Biometric hash (not raw image)
- Verification timestamp and method (Emirates ID scan or UAE Pass)
- ICA validation status and timestamp

---

### SUCCESS OUTCOME
- Customer identity verified against government database
- Facial biometric captured and matched to Emirates ID
- Risk category assigned (low/medium/high) for downstream processes
- Customer proceeds to document collection or risk screening

---

### EXIT POINTS

1. **Successful Verification:** Proceeds to JY-7.2 (Document Collection) or JY-7.4 (Risk Screening)
2. **Manual Review Required:** Customer notified of 24-48 hour review period → support ticket created
3. **Verification Failed (Fraud):** Account creation blocked → customer support notified
4. **User Abandons:** Progress saved → reminder sent after 24 hours: "Complete your verification in 2 minutes"

---

### EDGE CASES & ERROR HANDLING

| Scenario | System Response | User Action | Outcome |
|----------|-----------------|-------------|---------|
| **Expired Emirates ID** | "Your ID expired on [date]. Please renew first" | Exits app, renews ID | Cannot proceed until renewed |
| **Lost/Stolen ID** | "This ID is reported lost/stolen. Please contact ICA" | Contacts ICA | Account creation blocked |
| **Minor (under 18)** | "You must be 18+ to open an account. Try our Teen Account" | Redirects to teen offering | Cannot open adult account |
| **Non-Resident** | "L'Imad accounts require UAE residency" | Exits app | Cannot proceed |
| **Poor Camera Quality** | "Camera quality insufficient. Try better lighting or another device" | Adjusts environment | May need to retry on different phone |
| **Network Timeout (ICA API)** | "Connection issue. Please try again" with retry button | Taps retry | Auto-retries up to 3 times |
| **Duplicate Emirates ID** | "This ID is already linked to an account. Log in instead?" | Taps "Log In" | Redirects to login screen |
| **System Maintenance** | "Verification temporarily unavailable. Try again in 1 hour" | Exits app | Progress saved, retry later |

---

### SECURITY MEASURES

- **Encryption:** All Emirates ID data encrypted in transit (TLS 1.3) and at rest (AES-256)
- **Data Minimization:** Only collect data required for verification (GDPR/UAE Data Protection compliance)
- **Audit Logging:** All ICA API calls logged with timestamp, user ID, response status
- **Fraud Prevention:** Velocity checks (max 3 verification attempts per Emirates ID per hour)
- **Access Control:** Emirates ID data accessible only to compliance team (role-based permissions)
- **Data Retention:** Raw ID images deleted after verification; only OCR data retained

---

### ACCESSIBILITY CONSIDERATIONS

- **Voice Guidance:** Screen reader support for all steps (Arabic and English)
- **High Contrast Mode:** For visually impaired users
- **Large Text Option:** Adjustable font size
- **Alternative Verification:** Video KYC with agent for users unable to complete automated flow
- **Multilingual:** English, Arabic, Hindi, Urdu support

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **Total verification time** | <3 minutes | Liv: 3-5 min, ADIB: 5-7 min |
| **Emirates ID capture** | <10 seconds | Industry: 15-20 sec |
| **ICA API response** | <5 seconds | Government SLA: 10 sec |
| **Facial recognition** | <15 seconds | Industry: 20-30 sec |
| **Success rate (first attempt)** | >85% | Industry: 70-80% |
| **Manual review rate** | <10% | Industry: 15-20% |

---

## JY-7.2: DOCUMENT COLLECTION & OCR

**Purpose:** Collect and digitize supporting documents required for KYC compliance

**Entry Points:**
- After initial identity verification (JY-7.1)
- During EDD process (JY-7.5)
- Periodic refresh when documents expire (JY-7.7)
- User updates personal information requiring proof

**User Type:** All customers (documents vary by risk category)

**Prerequisites:**
- Identity verified (JY-7.1 complete)
- Customer knows which documents are required (system displays checklist)

**Document Requirements by Customer Segment:**

**Low-Risk Retail:**
- Emirates ID (already captured in JY-7.1)
- Proof of address (optional for UAE nationals)

**Affluent:**Affluent:**
- Emirates ID (captured)
- Proof of address (utility bill, bank statement, tenancy contract - within 3 months)
- Income verification (salary certificate, bank statements - last 3 months)
- Basic Source of Funds declaration (dropdown selection)

**HNW (High-Net-Worth >AED 5M):**
- All affluent documents
- Comprehensive Source of Wealth statement (detailed questionnaire)
- Source of Funds evidence (transaction-specific)
- Business ownership documents (if self-employed): Trade license, ownership structure
- Tax returns (last 2 years)
- Financial statements (if business owner)

**PEPs (Politically Exposed Persons):**
- All HNW documents
- Declaration of PEP status and position
- Relationship mapping (family/close associates)
- Enhanced background check consent

---

### USER FLOW: JY-7.2 Document Collection & OCR

#### Step 1: Document Checklist Display
**User Action:** Lands on "Document Upload" screen after identity verification  
**System Response:**
- Displays personalized checklist based on risk category
- Example (Affluent customer):
  ```
  ✓ Emirates ID - Verified
  ○ Proof of Address - Required
  ○ Income Verification - Required
  ○ Source of Funds - Required
  ```
- Each item shows:
  - Document type with info icon (explains what's acceptable)
  - Status indicator (pending, uploaded, verified, rejected)
  - Upload button
- Shows progress: "2 of 4 documents remaining"
- Estimated time: "5 minutes to complete"

**Decision Point:** User selects which document to upload first

---

#### Step 2: Document Capture
**User Action:** Taps "Upload Proof of Address" → chooses photo method  
**System Response:**
- Offers two options:
  - **Take Photo:** Opens camera with document frame guides
  - **Upload from Gallery:** Opens photo picker
- Camera guidelines displayed:
  - "Ensure all corners are visible"
  - "Avoid glare and shadows"
  - "Document must be in focus"
- Auto-crop and perspective correction after capture
- Shows preview: "Does this look clear?" with Retake/Use Photo buttons

**Document Type-Specific Guidance:**
- **Utility Bill:** "DEWA, ADDC, Etisalat, or du bills accepted. Must be within 3 months"
- **Bank Statement:** "Full statement showing name and address. Must be within 3 months"
- **Salary Certificate:** "Company letterhead with authorized signature required"

**Edge Cases:**
- **Poor quality:** "Image too blurry. Please retake in better lighting"
- **Wrong document:** "This appears to be [wrong type]. Please upload [correct type]"
- **Document too old:** "This document is dated [date]. Please provide one within 3 months"
- **Partially visible:** "All corners must be visible. Please retake"

**SLA Target:** 15 seconds per document capture

---

#### Step 3: OCR Processing & Data Extraction
**User Action:** Confirms photo → waits for processing  
**System Response:**
- Displays: "Processing document..." with progress spinner
- Backend OCR process:
  1. **Document Type Classification:** AI identifies document category (utility bill, bank statement, passport, etc.)
  2. **Text Extraction:** OCR extracts all text fields
  3. **Key Field Identification:** Name, address, date, document number, issuer
  4. **Validation:** Cross-references extracted name with Emirates ID name (fuzzy matching for Arabic transliterations)
  5. **Date Check:** Validates document is within required timeframe (3 months for address proof)
  6. **Authenticity Check:** Detects digital manipulation, photocopies (originals preferred)

**Data Extracted (Proof of Address Example):**
- Customer name
- Full address
- Document type (DEWA bill, bank statement, etc.)
- Document date
- Issuer/provider name

**Decision Point:**
- **OCR Success:** Proceeds to Step 4 (Auto-Verification)
- **OCR Partial:** Shows extracted data with editable fields: "Please verify: Name: [John Doe] ✓ Address: [123 Sheikh...] ✓"
- **OCR Failure:** "We couldn't read this document. Please upload a clearer photo" → return to Step 2

**SLA Target:** 10 seconds for OCR processing

---

#### Step 4: Auto-Verification
**User Action:** System automatically verifies document authenticity  
**System Response:**
- Checks against validation rules:
  - **Name Match:** Extracted name matches Emirates ID name (>80% similarity score)
  - **Address Format:** UAE address format validation (emirate, area, street, building)
  - **Date Validation:** Document issued within last 3 months (for address proof)
  - **Issuer Verification:** Known utility provider/bank (DEWA, ADDC, Emirates NBD, ADCB, etc.)
  - **Authenticity Score:** AI-calculated score for forgery detection

**Decision Point:**
- **Auto-Approved (>90% confidence):** Proceeds to Step 5 (Success)
- **Needs Manual Review (70-90% confidence):** Flags for compliance team review (typically within 4 hours)
- **Auto-Rejected (<70% confidence):** Shows error with reason → return to Step 2

**Rejection Reasons:**
- "Name doesn't match your Emirates ID. Please upload a document in your name"
- "Document is too old. Please provide one dated within last 3 months"
- "We couldn't verify this document. Please try a different proof of address"
- "This appears to be a photocopy. Please upload original or digital document"

**Security Measures:**
- Document images encrypted at rest (AES-256)
- Retained for 5 years (UAE compliance requirement)
- Access restricted to compliance team only
- Watermark added to stored images (forensic tracking)

**SLA Target:** 5 seconds for auto-verification

---

#### Step 5: Document Verification Success
**User Action:** Receives confirmation  
**System Response:**
- Updates checklist:
  ```
  ✓ Emirates ID - Verified
  ✓ Proof of Address - Verified
  ○ Income Verification - Required
  ○ Source of Funds - Required
  ```
- Shows toast notification: "Proof of Address verified ✓"
- Progress updated: "1 of 4 documents remaining"
- Prompts: "Upload next document to continue"

**Backend Actions:**
- Stores verified document metadata in customer profile
- Updates risk assessment with new data
- Triggers address validation check (optional: cross-reference with DEWA customer database)

---

#### Step 6: All Documents Collected
**User Action:** Uploads final required document  
**System Response:**
- Updates checklist - all items show checkmarks
- Displays success screen: "All documents verified! ✓"
- Message: "You're ready for the next step"
- CTA: "Continue to Risk Assessment"
- Progress indicator: "Step 2 of 4 complete"

**Backend Actions:**
- Marks document collection sub-journey as complete
- Triggers JY-7.4 (Risk Assessment & Screening)
- Sends confirmation SMS/email: "Your documents have been verified"
- Logs event in audit trail

---

### SUCCESS OUTCOME
- All required documents collected and digitized
- Documents validated against customer identity
- Risk profile updated with new information
- Customer proceeds to risk assessment and sanctions screening

---

### EXIT POINTS

1. **All Documents Verified:** Proceeds to JY-7.4 (Risk Assessment)
2. **Manual Review Required:** Customer notified of 4-24 hour review period → receives email when complete
3. **Document Rejected:** Customer re-uploads alternative document
4. **User Abandons:** Progress saved → reminder sent after 24 hours: "Please upload 2 remaining documents"

---

### EDGE CASES & ERROR HANDLING

| Scenario | System Response | User Action | Outcome |
|----------|-----------------|-------------|---------|
| **Document in Arabic** | OCR processes Arabic text | None (automatic) | Successfully extracted |
| **Multiple Addresses** | "Which address should we use?" with selection | Selects primary address | Uses selected address |
| **Blurry/Unreadable** | "Image unclear. Please retake with better focus" | Retakes photo | Better quality photo required |
| **Wrong Name** | "Name doesn't match: [extracted] vs [expected]" | Explains (e.g., nickname) or uploads correct doc | May route to manual review |
| **Expired Document** | "This expired on [date]. Please provide current document" | Uploads newer document | Continues with valid doc |
| **Photocopy Detected** | "Please upload original or digital document, not photocopy" | Uploads digital bill from email | Accepts digital original |
| **Unknown Issuer** | "We don't recognize this issuer. Try a DEWA/bank statement" | Uploads recognized document | Continues with known issuer |
| **File Too Large** | "File size too large (>10MB). Please compress or use camera" | Compresses or retakes | Uploads smaller file |
| **Network Failure** | "Upload failed. Please check connection" with retry | Taps retry | Resumes upload |
| **Document Already Expired** | "Upload a document dated within last 3 months" | Requests newer bill from provider | Continues with current doc |

---

### SECURITY MEASURES

- **PII Protection:** All documents contain sensitive data; encrypted in transit and at rest
- **Access Logging:** All document views logged with user ID, timestamp, purpose
- **Retention Policy:** Documents retained for 5 years minimum (UAE FIU requirement)
- **Deletion Protocol:** After retention period, automated secure deletion with audit trail
- **Watermarking:** All stored documents watermarked with customer ID and timestamp (forensics)
- **Download Restrictions:** Documents cannot be downloaded by front-office staff; compliance only

---

### ACCESSIBILITY CONSIDERATIONS

- **Voice Instructions:** "Please position the document within the frame" (audio guidance)
- **High Contrast Mode:** Clear document frame outlines
- **File Upload Alternative:** For users unable to use camera, upload from file system
- **Alternative Documents:** Multiple document types accepted for each category (flexibility)
- **Language Support:** OCR supports English and Arabic text extraction

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **Document capture time** | <15 seconds | Industry: 20-30 sec |
| **OCR processing** | <10 seconds | Industry: 15-20 sec |
| **Auto-verification** | <5 seconds | Industry: manual (hours) |
| **Total time (all docs)** | <5 minutes | Liv: 7-10 min, ADIB: 10-15 min |
| **Auto-approval rate** | >75% | Industry: 50-60% |
| **Manual review SLA** | <4 hours (business hours) | Industry: 24-48 hours |

---

## JY-7.3: BIOMETRIC VERIFICATION

**Purpose:** Capture and store biometric data for ongoing authentication and fraud prevention

**Entry Points:**
- After document collection (JY-7.2)
- During account security setup (Journey 2: Onboarding)
- When customer enables biometric login (Journey 4: Account Management)
- When customer adds new device (Journey 3: Login from New Device)

**User Type:** All customers (mandatory for account activation)

**Biometric Methods Supported:**
1. **Facial Recognition** (primary) - 95% adoption
2. **Fingerprint** (alternative) - 4% adoption
3. **Voice Recognition** (future Wave 2B) - planned
4. **Iris Scan** (future Wave 3) - planned

**Regulatory Context:**
- **UAE National KYC Digital Platform:** Biometric verification mandatory
- **Liveness Detection Required:** Anti-spoofing measures per CBUAE guidelines
- **Data Protection:** Biometric data subject to UAE Data Protection Law (Federal Decree-Law No. 45/2021)

---

### USER FLOW: JY-7.3 Biometric Verification

#### Step 1: Biometric Method Selection
**User Action:** Lands on "Secure Your Account" screen  
**System Response:**
- Explains purpose: "We use biometrics to keep your account secure and make login faster"
- Displays two options:
  - **Face Recognition** (Recommended) - "Unlock with your face"
  - **Fingerprint** (Alternative) - "Unlock with your fingerprint"
- Shows benefits:
  - ✓ Faster login (no password needed)
  - ✓ Secure (unique to you)
  - ✓ Convenient (works even offline)
- Privacy note: "Your biometric data never leaves your device and is not shared"
- CTA buttons: "Set Up Face Recognition" or "Set Up Fingerprint"

**Decision Point:** User selects biometric method

---

#### Step 2A: Facial Recognition Setup
**User Action:** Taps "Set Up Face Recognition" → follows camera prompts  
**System Response:**
- Activates front-facing camera
- Displays face oval overlay with guidance: "Position your face in the center"
- Real-time feedback:
  - "Move closer" / "Move back" (distance adjustment)
  - "Look straight ahead" (head pose correction)
  - "Ensure good lighting" (brightness check)
- Captures face from multiple angles (5-7 frames):
  - **Frontal:** Looking straight at camera
  - **Left Profile:** 15° turn left
  - **Right Profile:** 15° turn right
  - **Up Angle:** Slight upward tilt
  - **Down Angle:** Slight downward tilt
- Shows progress: "1 of 5 angles captured"

**Liveness Detection:**
- **Active Challenges:** "Smile", "Blink twice", "Turn head slowly left then right"
- **Passive Detection:** Micro-movement analysis (no user action)
- **Anti-Spoofing:** Detects photo/video/mask spoofing attempts

**Edge Cases:**
- **Face not detected:** "Please remove glasses/hat and try again"
- **Poor lighting:** "Move to a brighter area"
- **Multiple faces:** "Please ensure only your face is visible"
- **Liveness failure:** "Please follow prompts carefully" → retry up to 3 times
- **3 failed attempts:** "Having trouble? Use fingerprint instead" with fallback option

**Technical Process (Backend):**
- Creates facial template (mathematical representation, not actual photo)
- Template encrypted and stored in secure enclave (device-level encryption)
- Backup encrypted template stored on server (for multi-device use)
- Original photos immediately deleted after template creation

**SLA Target:** 30 seconds (all angles captured)

---

#### Step 2B: Fingerprint Setup (Alternative)
**User Action:** Taps "Set Up Fingerprint" → places finger on sensor  
**System Response:**
- Checks device compatibility: Must have fingerprint sensor
- Displays fingerprint icon with animation
- Guidance: "Place your thumb on the sensor and lift repeatedly"
- Captures fingerprint pattern from multiple touch points (8-10 touches)
- Shows progress: "3 of 8 touches complete"
- Vibration feedback on each successful touch

**Edge Cases:**
- **No fingerprint sensor:** "Your device doesn't support fingerprint. Use face recognition instead"
- **Sensor dirty:** "Clean sensor and try again"
- **Finger too wet/dry:** "Dry your finger" / "Moisten your finger slightly"
- **Partial print:** "Please place finger fully on sensor"
- **Failed registration:** "Let's try your index finger instead" (alternative finger)

**Technical Process (Backend):**
- Creates fingerprint template (biometric hash)
- Template stored in device secure enclave (iOS Secure Enclave, Android TEE)
- Backup template stored on server (encrypted with device-specific key)
- Raw fingerprint image never stored

**SLA Target:** 45 seconds (all touches captured)

---

#### Step 3: Biometric Verification Test
**User Action:** Completes initial biometric capture → tests immediately  
**System Response:**
- Prompts: "Let's test your biometric. [Scan face / Touch sensor]"
- User performs biometric action
- System verifies against just-captured template
- Shows result:
  - ✓ **Success:** "Biometric verified! You're all set"
  - ✗ **Failure:** "Try again" → retry up to 2 times

**Decision Point:**
- **Test Passes:** Proceeds to Step 4 (Success)
- **Test Fails (2 attempts):** "Let's re-setup your biometric" → return to Step 2
- **Persistent Failure:** "Having trouble? You can set this up later" → skip for now, prompt in 24 hours

**SLA Target:** 10 seconds for verification test

---

#### Step 4: Biometric Enrollment Success
**User Action:** Receives confirmation  
**System Response:**
- Displays success screen with checkmark animation
- Message: "Your biometric is set up! ✓"
- Shows next-use guidance: "You can now log in quickly with your [face/fingerprint]"
- Backup options displayed:
  - "You can still use your PIN: [masked: ••••]"
  - "Add backup biometric (fingerprint)" [if user chose face recognition]
- CTA: "Continue"
- Progress indicator: "Step 3 of 4 complete"

**Backend Actions:**
- Marks biometric setup as complete in customer profile
- Enables biometric authentication for login (Journey 3)
- Stores device ID with biometric registration (multi-device tracking)
- Sends confirmation email/SMS: "Biometric authentication enabled on [device name]"
- Logs event in security audit trail

**Data Stored:**
- Biometric template (encrypted hash, not image)
- Registration timestamp
- Device ID and name
- Biometric method type (face/fingerprint)

---

### SUCCESS OUTCOME
- Biometric template securely captured and stored
- Customer can use biometric for future logins
- Fraud prevention enhanced with liveness detection
- Customer proceeds to risk assessment

---

### EXIT POINTS

1. **Biometric Setup Complete:** Proceeds to JY-7.4 (Risk Assessment)
2. **User Skips Biometric:** Proceeds to JY-7.4 (can set up biometric later)
3. **Setup Failed:** Fallback to PIN-only authentication → reminder to retry in 24 hours

---

### EDGE CASES & ERROR HANDLING

| Scenario | System Response | User Action | Outcome |
|----------|-----------------|-------------|---------|
| **Device Incompatible** | "Your device doesn't support biometrics. Use PIN instead" | Uses PIN | PIN-only authentication |
| **User Refuses** | "You can skip for now. Set up later in Settings" | Skips | PIN-only, reminder later |
| **Wearing Glasses** | "Please remove glasses for better accuracy" | Removes glasses | Retries face scan |
| **Beard Grown** | (During future login) "Face changed. Re-verify with PIN" | Enters PIN, re-scans | Updates template |
| **Multiple Failed Attempts** | "Having trouble? Use fingerprint/PIN instead" | Switches method | Alternative auth method |
| **Photo/Video Spoof** | "Liveness check failed. Please don't use photos" | Tries live capture | Must pass liveness |
| **Mask Worn (Post-COVID)** | "Please remove mask for face recognition" | Removes mask | Face scan succeeds |
| **Low Battery Warning** | "Low battery. Complete biometric setup after charging?" | Charges phone | Resumes later |

---

### SECURITY MEASURES

- **Template-Only Storage:** Biometric images deleted immediately; only mathematical templates stored
- **Device Encryption:** Templates stored in device secure enclave (hardware-level security)
- **Server Backup Encrypted:** With device-specific key; cannot be used on another device without re-authentication
- **No Biometric Sharing:** Templates never shared with 3rd parties or used for marketing
- **Audit Trail:** All biometric events logged (registration, authentication, updates)
- **Revocation:** User can delete biometric from all devices via Settings → Security
- **Data Minimization:** Only store minimum biometric data required for authentication

**UAE Data Protection Compliance:**
- Consent obtained explicitly before biometric capture
- Purpose clearly explained (authentication, fraud prevention)
- User can withdraw consent and delete biometric data
- Biometric data never used for profiling or tracking

---

### ACCESSIBILITY CONSIDERATIONS

- **Fingerprint Alternative:** For users unable to use facial recognition (e.g., facial differences)
- **PIN Fallback:** Always available for users who cannot use biometrics
- **Voice Guidance:** Audio instructions for biometric capture process
- **Extended Timeout:** Extra time allowed for users with motor impairments
- **Adjustable Sensitivity:** Lower thresholds for users with difficult-to-capture biometrics

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **Face registration time** | <30 seconds | Industry: 45-60 sec |
| **Fingerprint registration** | <45 seconds | Industry: 60-90 sec |
| **Liveness detection** | <3 seconds | Industry: 5-10 sec |
| **Registration success rate** | >90% (first attempt) | Industry: 75-85% |
| **Future login speed** | <2 seconds | Industry: 3-5 sec |
| **False acceptance rate** | <0.01% | Industry standard: <0.1% |
| **False rejection rate** | <1% | Industry standard: 1-3% |

---

## JY-7.4: RISK ASSESSMENT & SCREENING

**Purpose:** Assess customer risk level, perform sanctions/PEP screening, and determine KYC requirements

**Entry Points:**
- After document collection and biometric setup (initial KYC)
- After significant customer data change (address, occupation, nationality)
- Before large transactions (>AED 55,000 CDD threshold)
- Periodic scheduled rescreening (annual for high-risk, biennial for medium, 5-year for low)
- Real-time transaction monitoring alerts

**User Type:** All customers (screening is automatic; customer sees results)

**Screening Databases:**
1. **Sanctions Lists:**
   - UN Consolidated List (mandatory)
   - OFAC (US sanctions)
   - EU Sanctions List
   - UK HM Treasury Financial Sanctions
   - UAE Local Terrorist List (EOCN-maintained)
2. **PEP Databases:**
   - Dow Jones Risk & Compliance
   - WorldCompliance
   - LexisNexis
3. **Adverse Media:**
   - Financial crime news aggregators
   - Court records and legal databases

**Risk Categories:**
- **Low Risk:** UAE national, salaried employee, standard transactions, no flags
- **Medium Risk:** Expat, self-employed, higher transaction volumes, certain nationalities
- **High Risk:** HNW (>AED 5M), PEP, high-risk country, cash-intensive business, frequent international transfers

---

### USER FLOW: JY-7.4 Risk Assessment & Screening

#### Step 1: Automated Risk Scoring
**User Action:** Waits while system calculates risk profile (background process)  
**System Response:**
- Displays: "Completing your verification..." with progress indicator
- Backend risk assessment algorithm calculates score based on:

**Risk Factors (Weighted Scoring Model):**
| Factor | Low Risk | Medium Risk | High Risk |
|--------|----------|-------------|-----------|
| **Nationality** | UAE national | GCC national | High-risk jurisdiction (FATF grey/black list) |
| **Residency** | UAE resident 5+ years | UAE resident <5 years | Non-resident |
| **Occupation** | Salaried employee | Self-employed | Cash-intensive business |
| **Income** | <AED 50K/month | AED 50-200K/month | >AED 200K/month |
| **Expected Transaction Volume** | <AED 50K/month | AED 50-500K/month | >AED 500K/month |
| **Age** | 25-65 | 18-24 or 65+ | <18 (not applicable) |
| **Purpose of Account** | Salary, savings | Business | Investment, international |
| **Industry** | Standard (tech, healthcare) | Regulated (real estate, legal) | High-risk (crypto, forex, jewelry) |

**Composite Risk Score:** 0-100 scale
- **0-30:** Low Risk → Standard CDD
- **31-70:** Medium Risk → Enhanced CDD
- **71-100:** High Risk → Enhanced Due Diligence (EDD) mandatory

**SLA Target:** 5 seconds for risk calculation

---

#### Step 2: Sanctions & PEP Screening
**User Action:** Waits while system screens against global databases  
**System Response:**
- Backend screening process:
  1. **Name Matching:** Fuzzy matching algorithm accounts for:
     - Transliterations (Arabic ↔ English)
     - Name variations (Mohammed/Muhammad/Mohamed)
     - Aliases and known names
     - Maiden names
  2. **Date of Birth Matching:** Cross-references DOB from Emirates ID
  3. **Nationality Matching:** Screens against country-specific lists
  4. **Address Matching:** Geographic risk assessment

**Screening Results:**
- **No Match:** Customer cleared → proceed to Step 3
- **Possible Match (70-90% confidence):** Flagged for manual review
- **Confirmed Match (>90% confidence):** Alert triggered → immediate escalation

**Alert Types:**
- 🔴 **Sanctions Match:** Immediate account freeze, transaction block, FIU notification
- 🟠 **PEP Match:** Route to EDD (JY-7.5), senior management approval required
- 🟡 **Adverse Media:** Manual review by compliance team (within 4 hours)

**Decision Point:**
- **Cleared:** Proceeds to Step 3 (Risk Assignment)
- **PEP Confirmed:** Routes to JY-7.5 (Enhanced Due Diligence)
- **Sanctions Match:** Account creation blocked, customer support notified, FIU report filed

**Security Measures:**
- Real-time API integration with screening databases
- Automatic daily rescreening of all customers (nightly batch job)
- Alert notification to compliance team via SMS + email + dashboard
- goAML reporting integration for sanctions matches

**SLA Target:** 10 seconds for screening

---

#### Step 3: Risk Category Assignment
**User Action:** System automatically assigns risk category  
**System Response:**
- Assigns category based on composite score and screening results:
  - **Low Risk:** Standard CDD, annual refresh, standard transaction limits
  - **Medium Risk:** Enhanced CDD, biennial refresh, higher limits, additional monitoring
  - **High Risk:** EDD required → routes to JY-7.5

**Customer Communication (If Low/Medium):**
- No explicit communication of risk category to customer (internal classification)
- Customer sees: "Verification complete! Your account is ready"
- Progress indicator: "Step 4 of 4 complete"

**Backend Actions:**
- Stores risk category in customer profile
- Sets transaction monitoring thresholds based on category
- Schedules next refresh date (1/2/5 years depending on risk)
- Enables appropriate product features based on risk (investment accounts for low-risk only)
- Logs risk assessment in audit trail (compliance)

**Data Stored:**
- Risk category (low/medium/high)
- Risk score (0-100)
- Risk factors contributing to score
- Screening results (clear/flagged)
- Assessment timestamp
- Next refresh due date

---

#### Step 4: Verification Complete (Low/Medium Risk)
**User Action:** Receives confirmation that KYC is complete  
**System Response:**
- Displays success screen: "Account Verified! ✓"
- Message: "You're all set to start banking with L'Imad"
- Shows account features unlocked:
  - ✓ Send and receive transfers
  - ✓ Virtual debit card (instant)
  - ✓ Physical card (5-7 days delivery)
  - ✓ Investments (low-risk customers only)
- CTA: "Explore Your Account"
- Welcome bonus notification (if applicable): "Claim your AED 100 welcome bonus"

**Backend Actions:**
- Marks KYC journey as complete
- Activates account fully (no restrictions)
- Triggers Welcome email/SMS
- Issues virtual debit card (if selected)
- Orders physical card production
- Enables push notifications
- Starts initial funding journey (Journey 5: Deposits)

---

### SUCCESS OUTCOME (Low/Medium Risk)
- Customer risk profile established
- Sanctions/PEP screening cleared
- KYC journey complete
- Account fully activated and ready to use

---

### HIGH-RISK OUTCOME
- Customer flagged for Enhanced Due Diligence (EDD)
- Routes to JY-7.5 (EDD Sub-Journey)
- Additional documents and verification required
- Account activation pending EDD completion

---

### SANCTIONS MATCH OUTCOME
- Account creation immediately blocked
- Customer sees: "We're unable to proceed with your application at this time"
- Support ticket auto-created for compliance team
- FIU report filed via goAML within 24 hours
- Customer has right to appeal if false positive

---

### EXIT POINTS

1. **Low/Medium Risk Cleared:** Account activated → proceeds to initial funding (Journey 5)
2. **High Risk Flagged:** Routes to JY-7.5 (Enhanced Due Diligence)
3. **PEP Confirmed:** Routes to JY-7.5 (EDD with PEP-specific requirements)
4. **Sanctions Match:** Account blocked → compliance review → possible rejection
5. **Manual Review Required:** 4-24 hour review period → customer notified of outcome

---

### EDGE CASES & ERROR HANDLING

| Scenario | System Response | User Action | Outcome |
|----------|-----------------|-------------|---------|
| **Common Name (e.g., Ahmed Ali)** | Multiple possible PEP matches | Manual review by compliance | Cleared if not actual PEP |
| **Recent PEP (Retired Official)** | Flagged as PEP | EDD required | Treated as PEP for 2 years post-tenure |
| **Family Member of PEP** | Flagged as RCA (Relative/Close Associate) | EDD required | Enhanced monitoring |
| **High-Risk Nationality (Non-Sanctioned)** | Medium-high risk score | Enhanced CDD | May proceed with restrictions |
| **Screening Database Timeout** | "Verification delayed. We'll notify you within 4 hours" | Waits for manual completion | Manual screening by compliance |
| **Conflicting Data** | "Please verify: Your occupation is [X] but income is [Y]" | Explains or corrects | Clarification resolves discrepancy |
| **Historical Adverse Media** | Flagged for review | Compliance investigates | Approved if resolved/irrelevant |
| **Corporate Signatory (Non-Owner)** | Flagged | "Are you a beneficial owner?" question | If no, lower risk |
| **Dual Nationality (One High-Risk)** | Higher risk score | EDD may be required | Assessed case-by-case |

---

### SECURITY MEASURES

- **Daily Rescreening:** All customers automatically rescreened nightly against updated sanctions/PEP lists
- **Real-Time Transaction Screening:** Every transaction screened before execution
- **Alert Escalation:** Sanctions matches trigger immediate SMS to Head of Compliance
- **Audit Trail:** All screening results logged with timestamp, database version, match confidence
- **False Positive Management:** Confirmed cleared customers whitelisted to reduce future false positives
- **Data Retention:** Screening results retained for 5 years (UAE FIU requirement)

---

### REGULATORY COMPLIANCE

**UAE Requirements:**
- **CDD Triggers:** Transactions ≥AED 55,000 require due diligence
- **EDD Mandatory For:** PEPs, high-risk jurisdictions, suspicious activity
- **FIU Reporting:** Sanctions matches reported within 24 hours via goAML
- **Record Keeping:** 5 years minimum retention
- **CBUAE Supervision:** Risk models audited annually

**International Standards:**
- **FATF Compliance:** Risk-based approach aligned with FATF recommendations
- **FATCA:** US person identification triggers reporting
- **CRS:** Non-resident tax reporting to 100+ jurisdictions

---

### ACCESSIBILITY CONSIDERATIONS

- **Transparent Process:** Clear communication if verification delayed (no opaque "processing")
- **Appeal Process:** Customers can appeal false positives (sanctions/PEP matches)
- **Language Support:** Risk notifications in customer's preferred language
- **Customer Support:** Dedicated compliance support line for verification questions

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **Risk scoring time** | <5 seconds | Industry: 10-15 sec |
| **Screening time** | <10 seconds | Industry: 30-60 sec |
| **Auto-clearance rate** | >85% | Industry: 70-80% |
| **Manual review SLA** | <4 hours (business hours) | Industry: 24-48 hours |
| **False positive rate** | <5% | Industry: 10-20% |
| **Sanctions detection** | 100% (zero misses) | Regulatory requirement |

---

*[Document continues with JY-7.5 through JY-7.8 in next part...]*
