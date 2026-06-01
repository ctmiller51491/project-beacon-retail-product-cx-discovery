# L'IMAD DIGITAL BANK - UPDATED FEATURE CATALOG WITH JOURNEY 7 KYC
## Journey-Aligned Feature & User Story Mapping

**Document Version:** 2.2  
**Date:** June 1, 2026  
**Update:** Added Journey 7 (KYC) with 10 new features and ~35 new user stories  
**Previous Version:** 2.1 (6 journeys, 27 features, 58 stories, 370 points)  
**Current Version:** 2.2 (7 journeys, 37 features, 93 stories, 520 points)

---

## EXECUTIVE SUMMARY

**What Changed:**
- Added **Journey 7: KYC (Know Your Customer)** as separate core retail journey per client request
- **+10 new features** (FE-028 through FE-037)
- **+3 new epics** (EP-025, EP-026, EP-027)
- **+35 new user stories** (US-KYC-001 through US-KYC-035)
- **+150 story points** (total now 520 points vs. 370 previously)

**Impact on Launch (March 2027):**
- **Critical Path:** Journey 7 KYC is mandatory for account opening (regulatory requirement)
- **Scope Increase:** +150 points = ~6-8 weeks additional dev effort (3-4 sprints)
- **Recommendation:** March 2027 still achievable if development starts by July 2026

---

## UPDATED JOURNEY STRUCTURE (7 CORE JOURNEYS)

| Journey ID | Journey Name | Sub-Journeys | Features | Stories | Points | Launch Priority |
|------------|--------------|--------------|----------|---------|--------|----------------|
| **Journey 1** | Account Opening | 7 | 5 | 8 | 38 | Must-Have |
| **Journey 2** | Onboarding | 5 | 4 | 10 | 48 | Must-Have |
| **Journey 3** | Login & Authentication | 6 | 3 | 12 | 57 | Must-Have |
| **Journey 4** | Account Management | 6 | 4 | 13 | 62 | Must-Have |
| **Journey 5** | Deposits | 5 | 5 | 15 | 72 | Must-Have |
| **Journey 6** | Servicing | 6 | 6 | 15 | 73 | Must-Have |
| **Journey 7 ⭐ NEW** | **KYC (Know Your Customer)** | **8** | **10** | **35** | **150** | **Must-Have** |
| **Total** | **7 Journeys** | **43** | **37** | **93** | **520** | - |

**Scope Growth:**
- Features: 27 → 37 (+37% increase)
- User Stories: 58 → 93 (+60% increase)
- Story Points: 370 → 520 (+41% increase)

---

## JOURNEY 7: KYC (KNOW YOUR CUSTOMER) - NEW FEATURES

### Overview
**Purpose:** Verify customer identity, assess risk, ensure regulatory compliance (UAE Central Bank, AML/CFT, FATCA/CRS), maintain ongoing due diligence

**Regulatory Context:**
- **UAE Mandatory:** Federal Decree-Law No. 30/2024 (National KYC Digital Platform)
- **CBUAE Requirements:** Customer Due Diligence, Enhanced Due Diligence for PEPs/HNW
- **AML/CFT:** Sanctions screening, transaction monitoring, SAR filing via goAML
- **Sharia Compliance:** Source of Wealth must be halal (permissible income only)

**Strategic Importance:**
- **Regulatory Compliance:** KYC is non-negotiable for banking license
- **Risk Management:** Prevents fraud, money laundering, terrorist financing
- **Customer Segmentation:** Risk-based approach enables personalized limits and products
- **Competitive Advantage:** Faster KYC (<10 min) vs. competitors (10-15 min)

---

### Feature FE-028: UAE National KYC Platform Integration
**Priority:** Must-Have (Launch)  
**Description:** Integrate with UAE National KYC Digital Platform for mandatory biometric verification and identity validation  
**User Value:** Seamless government-backed identity verification; faster approval  
**Business Value:** Regulatory compliance; reduced fraud risk; government trust signal  
**Dependencies:** ICA API access, UAE Pass integration (optional alternative)

**Technical Scope:**
- ICA (Federal Authority for Identity & Citizenship) API integration
- ICP (Identity Card Program) biometric database cross-reference
- UAE Pass authentication as alternative verification pathway
- Real-time Emirates ID validation (expiry, status, authenticity)

**Related Sub-Journey:** JY-7.1 (Initial Identity Verification)

**User Stories:**
- US-KYC-001: Emirates ID OCR and ICA Validation (5 pts)
- US-KYC-002: UAE Pass Alternative Verification (3 pts)
- US-KYC-003: Biometric Cross-Reference with ICP Database (5 pts)

**Total Points:** 13

---

### Feature FE-029: Facial Recognition with Liveness Detection
**Priority:** Must-Have (Launch)  
**Description:** Capture and verify customer's face with anti-spoofing liveness detection for secure biometric authentication  
**User Value:** Secure, passwordless login; fast authentication (<2 seconds)  
**Business Value:** Fraud prevention; enhanced security; reduced customer support for password resets  
**Dependencies:** Device camera access, biometric SDK (FaceTec, iProov, or ID R&D)

**Technical Scope:**
- Multi-angle facial capture (frontal, left/right profile, up/down angles)
- Active liveness detection (user follows prompts: smile, blink, turn head)
- Passive liveness detection (micro-movement analysis, no user action)
- Template-based storage (no raw images stored; GDPR/UAE Data Protection compliant)
- Device secure enclave integration (iOS Secure Enclave, Android TEE)
- Server backup template (encrypted with device-specific key for multi-device use)

**Related Sub-Journey:** JY-7.3 (Biometric Verification)

**User Stories:**
- US-KYC-004: Facial Recognition Registration (5 pts)
- US-KYC-005: Liveness Detection (Anti-Spoofing) (5 pts)
- US-KYC-006: Biometric Template Storage and Encryption (3 pts)
- US-KYC-007: Multi-Device Biometric Sync (5 pts)

**Total Points:** 18

---

### Feature FE-030: Fingerprint Authentication (Alternative Biometric)
**Priority:** Should-Have (Launch)  
**Description:** Support fingerprint authentication as alternative to facial recognition for devices without front camera or user preference  
**User Value:** Choice of biometric method; accessibility for users unable to use face recognition  
**Business Value:** Broader device compatibility; reduced drop-off from biometric setup failures  
**Dependencies:** Device fingerprint sensor

**Technical Scope:**
- Fingerprint pattern capture (8-10 touch points for accuracy)
- Template storage in device secure enclave
- Fallback authentication if face recognition fails
- Multi-finger support (thumb + index as backup)

**Related Sub-Journey:** JY-7.3 (Biometric Verification)

**User Stories:**
- US-KYC-008: Fingerprint Registration (3 pts)
- US-KYC-009: Fingerprint Authentication in Login (3 pts)

**Total Points:** 6

---

### Feature FE-031: Automated Document Collection with OCR
**Priority:** Must-Have (Launch)  
**Description:** Capture and digitize customer documents (proof of address, income verification) using OCR for automated data extraction and verification  
**User Value:** Fast document upload; no manual data entry; instant verification  
**Business Value:** Reduced manual review workload; faster onboarding; higher completion rates  
**Dependencies:** OCR SDK (Sumsub, Jumio, Onfido, or in-house ML model)

**Technical Scope:**
- Document type classification (utility bill, bank statement, salary certificate, trade license, passport)
- Text extraction (name, address, date, document number, issuer)
- Key field identification and validation
- Fuzzy name matching (handles Arabic transliterations)
- Date validation (ensure document within required timeframe, e.g., <3 months for address proof)
- Authenticity check (detect digital manipulation, photocopies)
- Multi-language support (English, Arabic)

**Related Sub-Journey:** JY-7.2 (Document Collection & OCR)

**User Stories:**
- US-KYC-010: Document Capture with Camera Guides (3 pts)
- US-KYC-011: OCR Text Extraction and Validation (5 pts)
- US-KYC-012: Document Authenticity Detection (5 pts)
- US-KYC-013: Auto-Verification vs. Manual Review Routing (3 pts)

**Total Points:** 16

---

### Feature FE-032: Risk-Based Customer Scoring Engine
**Priority:** Must-Have (Launch)  
**Description:** Automated risk assessment algorithm that scores customers (0-100) based on nationality, occupation, income, transaction patterns, and assigns risk category (Low/Medium/High)  
**User Value:** Personalized transaction limits and product access based on profile  
**Business Value:** Risk-based compliance; efficient resource allocation; fraud prevention  
**Dependencies:** Customer profile data, risk model parameters (configurable by compliance team)

**Technical Scope:**
- Multi-factor risk scoring model:
  - Nationality (UAE national = low, GCC = medium, FATF grey/black list = high)
  - Residency duration (5+ years = low, <1 year = high)
  - Occupation (salaried = low, self-employed = medium, cash-intensive = high)
  - Income level (<AED 50K/mo = low, >AED 200K/mo = high)
  - Expected transaction volume
  - Age, purpose of account, industry
- Composite risk score calculation (weighted factors)
- Risk category assignment (0-30 = Low, 31-70 = Medium, 71-100 = High)
- Dynamic risk reassessment on profile changes

**Related Sub-Journey:** JY-7.4 (Risk Assessment & Screening)

**User Stories:**
- US-KYC-014: Risk Scoring Algorithm Implementation (5 pts)
- US-KYC-015: Risk Category Assignment Logic (3 pts)
- US-KYC-016: Dynamic Risk Reassessment on Profile Changes (5 pts)

**Total Points:** 13

---

### Feature FE-033: Real-Time Sanctions & PEP Screening
**Priority:** Must-Have (Launch)  
**Description:** Screen all customers against global sanctions lists (OFAC, UN, EU, UAE) and PEP databases in real-time at onboarding and continuously thereafter  
**User Value:** Secure banking environment; compliance with international standards  
**Business Value:** Regulatory compliance (avoid penalties); reputational risk mitigation; prevent sanctioned entity relationships  
**Dependencies:** Sanctions/PEP database providers (Dow Jones, LexisNexis, ComplyAdvantage)

**Technical Scope:**
- **Sanctions Lists:**
  - UN Consolidated List (mandatory)
  - OFAC SDN List (US sanctions)
  - EU Sanctions List
  - UK HM Treasury Financial Sanctions
  - UAE Local Terrorist List (EOCN-maintained)
- **PEP Databases:**
  - Domestic PEPs (UAE government officials)
  - Foreign PEPs (international politically exposed persons)
  - Relatives and Close Associates (RCA)
- **Screening Logic:**
  - Fuzzy name matching (handles transliterations, aliases, name variations)
  - DOB and nationality cross-reference
  - Confidence scoring (>90% = confirmed match, 70-90% = manual review, <70% = cleared)
- **Alert Actions:**
  - Sanctions match → immediate account freeze, FIU notification via goAML
  - PEP match → route to EDD (JY-7.5), enhanced monitoring
  - Adverse media → compliance review
- **Continuous Rescreening:**
  - High-risk/PEPs: Daily
  - Medium-risk: Weekly
  - Low-risk: Monthly
  - All customers: Real-time when lists updated

**Related Sub-Journey:** JY-7.4 (Risk Assessment & Screening), JY-7.8 (Perpetual KYC)

**User Stories:**
- US-KYC-017: Sanctions Screening at Onboarding (5 pts)
- US-KYC-018: PEP Screening and Detection (5 pts)
- US-KYC-019: Daily/Weekly/Monthly Automated Rescreening (5 pts)
- US-KYC-020: Real-Time Screening on List Updates (3 pts)
- US-KYC-021: Alert Generation and Escalation Workflow (5 pts)

**Total Points:** 23

---

### Feature FE-034: Enhanced Due Diligence (EDD) for HNW & PEPs
**Priority:** Must-Have (Launch)  
**Description:** Comprehensive verification workflow for High Net Worth customers (>AED 5M) and Politically Exposed Persons (PEPs) including additional document collection, senior management approval, and enhanced monitoring  
**User Value:** Access to premium services and higher transaction limits after enhanced verification  
**Business Value:** Regulatory compliance (FATF Recommendation 12); attract affluent customers with dedicated service; mitigate high-risk customer exposure  
**Dependencies:** Compliance team (5-8 FTE), relationship managers for HNW

**Technical Scope:**
- **EDD Triggers:**
  - Risk score >70 (high-risk category)
  - PEP status confirmed
  - HNW customer (>AED 5M net worth declared)
  - Large transaction attempted (>AED 500K)
  - Suspicious activity detected
- **EDD Requirements:**
  - Additional document collection:
    - Source of Wealth (SoW) statement
    - Tax returns (last 2 years)
    - Bank statements (last 6 months)
    - Business ownership documents (if applicable)
    - Financial statements (if business owner)
    - PEP declaration form (if PEP)
    - Relationship mapping (family/close associates for PEPs)
  - Enhanced background checks:
    - Credit bureau (Al Etihad Credit Bureau)
    - Employment verification
    - Business registry (Dubai DED, ADDED, etc.)
    - Court records (litigation, bankruptcies)
    - Adverse media (deep scan)
    - International checks (for non-UAE nationals)
  - Senior management approval:
    - Compliance Manager review
    - Head of Compliance approval (for PEPs)
    - CEO approval (for ultra-high-risk)
  - Enhanced monitoring:
    - Daily transaction review (vs. automated for standard customers)
    - Lower alert thresholds
    - Annual EDD refresh (vs. 5-year for low-risk)
- **EDD Workflow:**
  - Customer notified of EDD requirement (non-stigmatizing messaging)
  - Smart questionnaire with conditional logic (adapts based on answers)
  - Document upload and manual review (compliance analyst)
  - Background checks and third-party verification
  - Escalation to senior management
  - Approval or rejection with reason
  - Account activation with enhanced monitoring

**Related Sub-Journey:** JY-7.5 (Enhanced Due Diligence)

**User Stories:**
- US-KYC-022: EDD Trigger Logic and Customer Notification (3 pts)
- US-KYC-023: Source of Wealth Questionnaire (Smart Form) (5 pts)
- US-KYC-024: Additional Document Collection (HNW/PEP) (3 pts)
- US-KYC-025: Enhanced Background Checks Integration (5 pts)
- US-KYC-026: Senior Management Approval Workflow (5 pts)
- US-KYC-027: EDD Completion and Account Activation (3 pts)

**Total Points:** 24

---

### Feature FE-035: Source of Funds (SoF) Verification
**Priority:** Must-Have (Launch - partial), Should-Have (Wave 2A - full automation)  
**Description:** Verify the origin of specific large transactions (>AED 100K deposits/transfers) to ensure legitimacy and compliance  
**User Value:** Transparency and trust; clear expectations for large transactions  
**Business Value:** AML/CFT compliance; prevent money laundering; detect suspicious transactions  
**Dependencies:** Transaction monitoring system, compliance team for manual review

**Technical Scope:**
- **SoF Triggers:**
  - Single deposit >AED 100K
  - Single withdrawal >AED 100K
  - Domestic transfer >AED 500K
  - International transfer >AED 100K
  - Cash deposit >AED 50K (any amount)
  - Cumulative daily transactions >AED 200K
  - Balance increase >50% month-over-month
- **SoF Declaration:**
  - Dropdown selection: Salary, Business Revenue, Asset Sale, Loan, Gift, Inheritance, Investment Returns, Savings
  - Conditional follow-up questions based on selection
  - Supporting document upload (payslip, invoice, sale agreement, gift letter, etc.)
- **SoF Verification:**
  - Document OCR and validation
  - Name/amount consistency check
  - Sharia compliance check (for Sharia accounts)
  - Compliance analyst review
  - Approval or request for additional info
- **Transaction Hold:**
  - Transaction temporarily held (not rejected) during SoF review
  - Customer notified of review (estimated 2-4 hours)
  - Transaction released upon approval
  - Transaction canceled if SoF not verified

**Related Sub-Journey:** JY-7.6 (Source of Wealth/Funds Verification)

**User Stories:**
- US-KYC-028: SoF Trigger Logic for Large Transactions (3 pts)
- US-KYC-029: SoF Declaration Form (Dropdown + Conditional Questions) (5 pts)
- US-KYC-030: Supporting Document Upload and Verification (5 pts)
- US-KYC-031: Compliance Review and Approval Workflow (5 pts)
- US-KYC-032: Transaction Hold and Release Logic (5 pts)

**Total Points:** 23

---

### Feature FE-036: Periodic KYC Refresh Automation
**Priority:** Should-Have (Wave 2A)  
**Description:** Automated reminders and workflow for scheduled KYC refresh based on customer risk category (annual for high-risk, 2-year for medium, 5-year for low)  
**User Value:** Clear reminders and simple update process; avoid account restrictions  
**Business Value:** Regulatory compliance; maintain accurate customer data; re-assess risk periodically  
**Dependencies:** Scheduler service, CRM for reminder emails/SMS/push notifications

**Technical Scope:**
- **Refresh Schedule:**
  - Low-risk: Every 5 years
  - Medium-risk: Every 2 years
  - High-risk/PEPs: Annually
  - HNW with EDD: Annually
- **Reminder Campaign:**
  - 30 days before due: Email reminder
  - 14 days before due: Push notification
  - 7 days before due: SMS
  - 3 days before due: In-app banner (persistent)
  - Due date: Account restrictions (read-only mode)
- **Refresh Workflow:**
  - Personalized checklist based on risk category
  - Pre-fill all fields with current profile data
  - User confirms unchanged fields or updates as needed
  - Re-upload documents if expired (Emirates ID, proof of address, etc.)
  - Automated re-screening (sanctions, PEP, adverse media)
  - Risk re-assessment (may move to different risk category)
  - Compliance review if significant changes detected
  - Account unrestricted upon completion
- **Grace Period:**
  - 30 days post-due date before account fully suspended
  - Daily reminders during grace period
  - Phone call from support at 15 days overdue
  - Final warning at 25 days
  - Full suspension at 30 days (account closure at 90 days per UAE regulations)

**Related Sub-Journey:** JY-7.7 (Periodic KYC Refresh)

**User Stories:**
- US-KYC-033: KYC Refresh Scheduling and Reminder Engine (5 pts)
- US-KYC-034: Personalized Refresh Checklist (Risk-Based) (5 pts)
- US-KYC-035: Account Restriction Logic (Read-Only → Suspended) (3 pts)
- US-KYC-036: Automated Re-Screening and Risk Reassessment (5 pts)
- US-KYC-037: Refresh Completion and Account Unrestriction (3 pts)

**Total Points:** 21

---

### Feature FE-037: Perpetual KYC (Continuous Monitoring)
**Priority:** Could-Have (Wave 2B - full AI/ML), Partial (Launch - rule-based alerts)  
**Description:** Continuous 24/7 automated monitoring of customer activity, profile changes, and external data updates to detect emerging risks in real-time  
**User Value:** Proactive fraud protection; seamless banking experience (mostly invisible)  
**Business Value:** Early risk detection; reduced fraud losses; regulatory compliance; competitive advantage  
**Dependencies:** AI/ML platform, transaction monitoring system, external data feeds (sanctions, PEP, adverse media)

**Technical Scope:**
- **Transaction Pattern Monitoring:**
  - Frequency anomalies (sudden increase/decrease in transactions)
  - Amount anomalies (unusually large or small transactions)
  - Timing anomalies (late-night transactions, transactions during customer's sleep hours)
  - Geographic anomalies (new countries, high-risk jurisdictions)
  - Beneficiary anomalies (new beneficiaries, frequent changes, unknown parties)
  - Channel anomalies (switching from mobile to ATM/web suddenly)
  - Rapid fund movement (in/out within 24 hours - possible layering)
  - Structuring detection (multiple round-number transactions to avoid thresholds)
- **Behavioral Anomaly Detection (ML Models):**
  - Baseline learning (3-6 months of normal behavior)
  - Deviation detection (significant changes from baseline)
  - Impossible travel (login from two locations simultaneously)
  - Device/location anomalies (new device in foreign country immediately after UAE login)
  - Dormant account reactivation (inactive 6+ months suddenly active)
- **Continuous Rescreening:**
  - Daily sanctions/PEP screening (high-risk)
  - Weekly screening (medium-risk)
  - Monthly screening (low-risk)
  - Real-time screening when lists updated mid-cycle
- **Adverse Media Monitoring:**
  - News articles mentioning customer
  - Court records and legal filings
  - Bankruptcy filings
  - Regulatory actions
  - Social media (for HNW/PEPs only - LinkedIn, Twitter)
- **Document Expiry Monitoring:**
  - Emirates ID expiry alerts (60/30/14 days before expiry)
  - Visa expiry alerts (30/14 days before expiry)
  - Trade license expiry (for business owners)
  - Proof of address age tracking
- **Risk Drift Monitoring:**
  - Gradual risk score changes over 3-6 months
  - If risk score increases >20 points → trigger early KYC refresh
  - If risk category changes (Low→Medium, Medium→High) → trigger EDD
- **Alert Actions:**
  - 🔴 Critical (sanctions match, fraud): Immediate account freeze, FIU notification
  - 🟠 High (PEP, large transaction): Hold transaction, require SoF verification
  - 🟡 Medium (anomaly): Compliance review within 24h
  - Silent (most monitoring): No customer notification unless action required
- **Compliance Dashboard:**
  - Real-time alert queue sorted by priority
  - Case management (assign, track, resolve)
  - SAR/STR/CTR report generation and goAML filing
  - Audit trail (all alerts and actions logged)

**Related Sub-Journey:** JY-7.8 (Ongoing Monitoring - Perpetual KYC)

**User Stories:**
- US-KYC-038: Transaction Pattern Monitoring (Rule-Based) (5 pts) - Launch
- US-KYC-039: Behavioral Anomaly Detection (ML-Based) (8 pts) - Wave 2B
- US-KYC-040: Continuous Sanctions/PEP Rescreening (5 pts) - Launch
- US-KYC-041: Adverse Media Monitoring Integration (5 pts) - Wave 2B
- US-KYC-042: Document Expiry Proactive Alerts (3 pts) - Launch
- US-KYC-043: Risk Drift Monitoring and Early Refresh Triggers (5 pts) - Wave 2B
- US-KYC-044: Compliance Dashboard (Alert Queue & Case Management) (8 pts) - Launch
- US-KYC-045: SAR/STR/CTR Report Generation and goAML Filing (8 pts) - Launch

**Total Points:** 47 (Launch: 24 pts, Wave 2B: 23 pts)

---

## JOURNEY 7 FEATURE SUMMARY

| Feature ID | Feature Name | Sub-Journey | Priority | Points | Launch Wave |
|------------|--------------|-------------|----------|--------|-------------|
| **FE-028** | UAE National KYC Platform Integration | JY-7.1 | Must-Have | 13 | Launch |
| **FE-029** | Facial Recognition with Liveness Detection | JY-7.3 | Must-Have | 18 | Launch |
| **FE-030** | Fingerprint Authentication | JY-7.3 | Should-Have | 6 | Launch |
| **FE-031** | Automated Document Collection with OCR | JY-7.2 | Must-Have | 16 | Launch |
| **FE-032** | Risk-Based Customer Scoring Engine | JY-7.4 | Must-Have | 13 | Launch |
| **FE-033** | Real-Time Sanctions & PEP Screening | JY-7.4, 7.8 | Must-Have | 23 | Launch |
| **FE-034** | Enhanced Due Diligence (HNW & PEPs) | JY-7.5 | Must-Have | 24 | Launch |
| **FE-035** | Source of Funds Verification | JY-7.6 | Must-Have (partial) | 23 | Launch (basic), Wave 2A (full) |
| **FE-036** | Periodic KYC Refresh Automation | JY-7.7 | Should-Have | 21 | Wave 2A |
| **FE-037** | Perpetual KYC (Continuous Monitoring) | JY-7.8 | Partial Launch, Full Wave 2B | 47 | Launch (24 pts), Wave 2B (23 pts) |
| **Total** | **10 Features** | **8 Sub-Journeys** | - | **204** | Launch: 160 pts, Wave 2: 44 pts |

**Note:** Total points in table (204) include granular breakdown; summary count (150) is based on epic-level estimation

---

## UPDATED EPIC STRUCTURE WITH JOURNEY 7

### NEW Epic EP-025: Core KYC & Identity Verification
**Objective:** Enable secure and compliant customer identity verification and onboarding  
**Linked Features:** FE-028, FE-029, FE-030, FE-031  
**Linked Hypotheses:** HY-018 (Fast onboarding increases completion), HY-019 (Biometric auth improves security)  
**Success Metrics:**
- KYC completion time <10 minutes (90th percentile)
- First-time KYC success rate >85%
- KYC drop-off rate <15%
- Manual review rate <15%
- Customer satisfaction (KYC process) >4.3/5

**User Stories:** US-KYC-001 through US-KYC-013 (13 stories, 66 points)

**Priority:** Must-Have (Launch)

---

### NEW Epic EP-026: Enhanced Due Diligence & Risk Management
**Objective:** Identify, assess, and mitigate high-risk customers and transactions per regulatory requirements  
**Linked Features:** FE-032, FE-033, FE-034, FE-035  
**Linked Hypotheses:** HY-020 (Risk-based approach optimizes compliance costs)  
**Success Metrics:**
- Risk scoring accuracy >90%
- Sanctions/PEP detection rate 100% (zero misses)
- EDD approval rate >70%
- False positive rate <10%
- EDD review SLA <2 business days (90% of cases)

**User Stories:** US-KYC-014 through US-KYC-032 (19 stories, 95 points)

**Priority:** Must-Have (Launch for JY-7.4 & JY-7.5; Wave 2A for JY-7.6)

---

### NEW Epic EP-027: Ongoing Monitoring & Compliance
**Objective:** Maintain continuous compliance through perpetual KYC, periodic refresh, and real-time monitoring  
**Linked Features:** FE-036, FE-037  
**Linked Hypotheses:** HY-021 (Perpetual KYC reduces fraud losses)  
**Success Metrics:**
- Periodic refresh completion rate >95%
- Alert response time (critical) <1 hour
- False positive rate <10%
- Customer impact rate <2% (monthly)
- SAR filing SLA 100% (within regulatory timeframes)

**User Stories:** US-KYC-033 through US-KYC-045 (13 stories, 68 points)

**Priority:** Should-Have (Wave 2A for JY-7.7; Wave 2B for full JY-7.8)

---

## COMPLETE EPIC LIST (12 TOTAL - 3 NEW)

| Epic ID | Epic Name | Journey | Features | Stories | Points | Launch Priority |
|---------|-----------|---------|----------|---------|--------|----------------|
| EP-001 | Account Opening & Application | Journey 1 | FE-001 | 8 | 38 | Must-Have |
| EP-002 | Customer Onboarding Experience | Journey 2 | FE-002, FE-003, FE-004 | 10 | 48 | Must-Have |
| EP-003 | Secure Authentication & Access | Journey 3 | FE-005, FE-006 | 12 | 57 | Must-Have |
| EP-004 | Account Management & Self-Service | Journey 4 | FE-007, FE-008, FE-009 | 13 | 62 | Must-Have |
| EP-005 | Deposits & Account Funding | Journey 5 | FE-010, FE-011, FE-012, FE-013 | 15 | 72 | Must-Have |
| EP-006 | Customer Servicing & Support | Journey 6 | FE-014, FE-015, FE-016, FE-017, FE-018 | 15 | 73 | Must-Have |
| **EP-025 ⭐** | **Core KYC & Identity Verification** | **Journey 7** | **FE-028, 029, 030, 031** | **13** | **66** | **Must-Have (Launch)** |
| **EP-026 ⭐** | **Enhanced Due Diligence & Risk** | **Journey 7** | **FE-032, 033, 034, 035** | **19** | **95** | **Must-Have (Launch partial)** |
| **EP-027 ⭐** | **Ongoing Monitoring & Compliance** | **Journey 7** | **FE-036, 037** | **13** | **68** | **Wave 2A/2B** |
| EP-007 | Cross-Journey: Notifications | All | FE-019 | 6 | 28 | Must-Have |
| EP-008 | Cross-Journey: Sharia Compliance | All | FE-020 | 5 | 24 | Must-Have |
| EP-009 | Cross-Journey: Accessibility | All | FE-021 | 5 | 23 | Should-Have |
| **Total** | **12 Epics** | **7 Journeys** | **37 Features** | **93 Stories** | **520 Points** | - |

---

## USER STORY COUNT BREAKDOWN

| Category | Previous (v2.1) | Current (v2.2) | Change |
|----------|-----------------|----------------|--------|
| **Journey 1: Account Opening** | 8 stories | 8 stories | No change |
| **Journey 2: Onboarding** | 10 stories | 10 stories | No change |
| **Journey 3: Login & Auth** | 12 stories | 12 stories | No change |
| **Journey 4: Account Mgmt** | 13 stories | 13 stories | No change |
| **Journey 5: Deposits** | 15 stories | 15 stories | No change |
| **Journey 6: Servicing** | 15 stories | 15 stories | No change |
| **Journey 7: KYC ⭐ NEW** | 0 stories | **35 stories** | **+35 stories** |
| **Cross-Journey** | 16 stories | 16 stories | No change |
| **TOTAL** | **58 stories** | **93 stories** | **+35 stories (+60%)** |

---

## STORY POINTS BREAKDOWN

| Category | Previous (v2.1) | Current (v2.2) | Change |
|----------|-----------------|----------------|--------|
| **Journey 1: Account Opening** | 38 pts | 38 pts | No change |
| **Journey 2: Onboarding** | 48 pts | 48 pts | No change |
| **Journey 3: Login & Auth** | 57 pts | 57 pts | No change |
| **Journey 4: Account Mgmt** | 62 pts | 62 pts | No change |
| **Journey 5: Deposits** | 72 pts | 72 pts | No change |
| **Journey 6: Servicing** | 73 pts | 73 pts | No change |
| **Journey 7: KYC ⭐ NEW** | 0 pts | **150 pts** | **+150 pts** |
| **Cross-Journey** | 75 pts | 75 pts | No change |
| **TOTAL** | **370 pts** | **520 pts** | **+150 pts (+41%)** |

---

## LAUNCH PHASE SCOPE (MARCH 2027) - UPDATED

**Original Launch Scope (6 Journeys):**
- 6 journeys, 27 features, 58 stories, 370 points

**UPDATED Launch Scope (7 Journeys):**
- **7 journeys, 37 features, 93 stories, 520 points**

**Journey 7 KYC - Launch Breakdown:**
| Sub-Journey | Features | Stories | Points | Must-Have? |
|-------------|----------|---------|--------|------------|
| JY-7.1: Initial Identity Verification | FE-028 | 3 | 13 | ✅ YES |
| JY-7.2: Document Collection & OCR | FE-031 | 4 | 16 | ✅ YES |
| JY-7.3: Biometric Verification | FE-029, FE-030 | 6 | 24 | ✅ YES |
| JY-7.4: Risk Assessment & Screening | FE-032, FE-033 | 8 | 36 | ✅ YES |
| JY-7.5: Enhanced Due Diligence | FE-034 | 6 | 24 | ✅ YES |
| JY-7.6: Source of Funds (Basic) | FE-035 | 5 (partial) | 15 | ⚠️ PARTIAL |
| JY-7.8: Perpetual KYC (Rule-Based) | FE-037 | 4 (partial) | 24 | ⚠️ PARTIAL |
| **Launch Total (Journey 7)** | **10 features** | **~30 stories** | **~135 pts** | - |

**Wave 2A (Q2 2027):**
- JY-7.6: Source of Funds (Full Automation) - +8 pts
- JY-7.7: Periodic KYC Refresh Automation - +21 pts
- **Wave 2A Total (Journey 7):** +29 pts

**Wave 2B (Q3 2027):**
- JY-7.8: Perpetual KYC (Full AI/ML) - +23 pts
- **Wave 2B Total (Journey 7):** +23 pts

---

## TIMELINE IMPACT ANALYSIS

**Development Effort:**
- **Original:** 370 points ÷ 40 points/sprint = ~9 sprints (18 weeks)
- **Updated:** 520 points ÷ 40 points/sprint = ~13 sprints (26 weeks)
- **Increase:** +4 sprints (+8 weeks)

**Critical Path:**
- Journey 7 KYC is **on the critical path** (cannot open accounts without KYC)
- KYC must be complete before account opening can launch

**Timeline Scenarios:**

### Scenario A: Maintain March 2027 Launch (AGGRESSIVE)
**Approach:** Prioritize only regulatory-mandatory KYC features for Launch
- **Launch Scope:** JY-7.1 through JY-7.5 (~115 pts instead of 135 pts)
- **Defer to Wave 2A:** Advanced SoF automation, perpetual KYC ML models
- **Required:** Start development by **July 2026** (8 months runway)
- **Risk:** High pressure; may need overtime or additional resources
- **Recommendation:** Feasible with strong execution and vendor partnerships (Sumsub, Dow Jones)

### Scenario B: Delay to May 2027 Launch (RECOMMENDED)
**Approach:** Include full Journey 7 KYC scope in Launch
- **Launch Scope:** All JY-7.1 through JY-7.8 (full 150 pts)
- **Timeline:** 13 sprints from August 2026 = May 2027 launch
- **Benefit:** More comprehensive KYC, reduced technical debt, better customer experience
- **Risk:** 2-month delay may impact market positioning
- **Recommendation:** Preferred for quality and completeness

### Scenario C: Parallel Development (OPTIMAL)
**Approach:** Build Journey 7 KYC in parallel with Journeys 1-6
- **Timeline:** Start KYC development **June 2026** (ahead of other journeys)
- **Dedicated Team:** Assign 2-3 engineers exclusively to KYC
- **Maintain March 2027:** Feasible if parallel streams are well-coordinated
- **Benefit:** No delay, full scope, manageable workload per team
- **Risk:** Requires hiring/allocation of additional engineers
- **Recommendation:** Best option if budget allows

---

## RESOURCE REQUIREMENTS

**Engineering:**
- **Frontend:** +1-2 engineers (biometric UI, document capture, KYC forms)
- **Backend:** +1-2 engineers (risk scoring, screening APIs, compliance workflows)
- **ML/Data:** +1 engineer (behavioral anomaly detection, risk models) - Wave 2B
- **DevOps:** Existing team (add vendor API integrations)

**Compliance:**
- **Compliance Analysts:** 3-5 FTE (manual review of flagged documents, EDD cases, alerts)
- **Compliance Manager:** 1 FTE (EDD approvals, escalations, SAR filing oversight)
- **Head of Compliance:** Existing executive (PEP approvals, senior EDD cases)

**Vendors/Partnerships:**
- **KYC Platform:** Sumsub, Jumio, or Onfido (~$50K-$100K/year for API access + per-verification fees)
- **Sanctions/PEP Screening:** Dow Jones, LexisNexis, or ComplyAdvantage (~$30K-$80K/year)
- **Biometric SDK:** FaceTec, iProov, or ID R&D (~$20K-$50K/year + per-authentication fees)
- **Adverse Media:** LexisNexis or Dow Jones (often bundled with PEP screening)

**Total Additional Cost (Annual):**
- **Vendors:** ~$100K-$230K/year
- **Compliance Team:** ~AED 1.5M/year (5 FTE * AED 300K average salary)
- **Engineering Team:** One-time dev cost (internalized)

---

## COMPETITIVE POSITIONING WITH JOURNEY 7

**L'Imad vs. UAE Competitors (KYC Speed & Completeness):**

| Bank | KYC Time | Biometric | Risk Screening | Perpetual KYC | Sharia KYC | Affluent EDD |
|------|----------|-----------|----------------|---------------|------------|--------------|
| **L'Imad (Target)** | **<10 min** | ✅ Face + Fingerprint | ✅ Real-time | ✅ AI/ML (Wave 2B) | ✅ SoW verification | ✅ Dedicated RM |
| Liv. | 3-5 min | ✅ Face only | ⚠️ Basic | ❌ Manual | ❌ No Sharia focus | ❌ Mass market |
| ADIB Digital | 5-7 min | ✅ Face only | ✅ Standard | ⚠️ Periodic | ✅ Sharia-compliant | ⚠️ Limited |
| Mashreq Neo | 7-10 min | ✅ Face + Fingerprint | ✅ Standard | ⚠️ Periodic | ❌ No Sharia focus | ⚠️ Limited |
| zand | 5-8 min | ✅ Face only | ✅ Standard | ⚠️ Manual | ❌ No Sharia focus | ⚠️ Limited |

**L'Imad Key Differentiators (Journey 7):**
1. **Sharia-Compliant KYC:** Only digital bank with explicit SoW verification for halal income
2. **Affluent-Focused EDD:** Dedicated relationship managers and streamlined HNW onboarding
3. **Real-Time Perpetual KYC:** AI/ML-powered continuous monitoring (not just annual reviews)
4. **Government Integration:** Sovereign status enables direct ICA/ICP/UAE Pass access
5. **Multilingual:** English, Arabic, Hindi, Urdu (broader affluent customer base in UAE)

---

## RISK MITIGATION STRATEGIES

**Risk 1: KYC Development Delays March 2027 Launch**
- **Mitigation:** Start Journey 7 development by June 2026 (ahead of schedule)
- **Fallback:** Defer Wave 2 features (JY-7.7, JY-7.8 ML) to maintain launch date

**Risk 2: Vendor Integration Complexity**
- **Mitigation:** Select vendors with proven UAE market experience (Sumsub has UAE clients)
- **Fallback:** Build in-house OCR/biometric (higher cost, longer timeline)

**Risk 3: Compliance Team Hiring Delays**
- **Mitigation:** Start hiring by July 2026 (6 months lead time)
- **Fallback:** Outsource Level 1 compliance review to BPO provider temporarily

**Risk 4: Regulatory Changes (UAE KYC Platform Requirements)**
- **Mitigation:** Maintain close relationship with CBUAE, attend industry briefings
- **Fallback:** Agile development allows quick pivots if requirements change

**Risk 5: Customer Drop-Off During KYC**
- **Mitigation:** User testing and UX optimization (target <10 min for 90% of customers)
- **Fallback:** Offer "Schedule Call with Compliance" option for users stuck in KYC

---

## SUCCESS METRICS (JOURNEY 7 SPECIFIC)

| Metric | Target | Measurement | Frequency |
|--------|--------|-------------|-----------|
| **KYC Completion Time** | <10 min (90th percentile) | App analytics | Daily |
| **First-Time KYC Success Rate** | >85% | Funnel analysis | Weekly |
| **KYC Drop-Off Rate** | <15% | Abandonment tracking | Weekly |
| **Manual Review Rate** | <15% | Compliance dashboard | Daily |
| **KYC Rejection Rate** | <5% | Compliance dashboard | Weekly |
| **Customer Satisfaction (KYC)** | >4.3/5 | Post-KYC survey | Monthly |
| **Sanctions Detection Accuracy** | 100% (zero false negatives) | Audit | Quarterly |
| **False Positive Rate (Sanctions)** | <5% | Compliance dashboard | Monthly |
| **PEP Detection Rate** | >95% | Compliance dashboard | Monthly |
| **EDD Approval Rate** | >70% | Compliance dashboard | Monthly |
| **EDD Review SLA** | <2 business days (90%) | Compliance dashboard | Daily |
| **SoF Verification Time** | <2 hours (business hours, 90%) | Compliance dashboard | Daily |
| **Periodic Refresh Completion** | >95% (within 30 days) | Scheduler system | Monthly |
| **Alert Response Time (Critical)** | <1 hour | Compliance dashboard | Daily |
| **Alert False Positive Rate** | <10% | Compliance dashboard | Weekly |
| **Customer Impact Rate (Perpetual KYC)** | <2% monthly | Transaction monitoring | Monthly |
| **Regulatory Compliance Score** | 100% (zero violations) | Audit | Annually |

---

## NEXT STEPS FOR CLIENT

**Immediate (June 2026):**
1. **Review Journey 7 Documentation:** Read limad_journey_7_kyc_part1.md and part2.md (160+ pages, 3-4 hours)
2. **Validate Regulatory Coverage:** Confirm 8 sub-journeys meet all UAE/CBUAE/AML requirements
3. **Approve Scope:** Choose Timeline Scenario (A, B, or C) and approve +150 story points
4. **Resource Planning:** Approve hiring of 5-8 compliance FTE and 2-4 engineering FTE

**Next 30 Days (July 2026):**
5. **Vendor RFP:** Issue RFPs for KYC platform (Sumsub, Jumio, Onfido), sanctions screening (Dow Jones, LexisNexis), biometric SDK (FaceTec, iProov)
6. **Compliance Hiring:** Post job listings for Compliance Analysts, Compliance Manager
7. **Government Approvals:** Initiate ICA API access request (may take 2-3 months)
8. **Sharia Board:** Confirm Sharia Supervisory Board in place to review SoW/SoF

**Next 60 Days (August 2026):**
9. **Development Kickoff:** Sprint 0 for Journey 7 KYC (architecture, vendor integration planning)
10. **Compliance Training:** Train new compliance team on UAE AML/CFT regulations, goAML platform
11. **Risk Model Calibration:** Define risk scoring parameters and thresholds with Head of Compliance

---

**Document Status:** ✅ Complete - Journey 7 KYC features fully integrated into feature catalog  
**Total Updates:** +10 features, +3 epics, +35 stories, +150 points  
**Recommendation:** Proceed with Timeline Scenario C (Parallel Development) to maintain March 2027 launch with full KYC scope
