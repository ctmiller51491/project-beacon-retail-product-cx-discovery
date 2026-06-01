# L'IMAD DIGITAL BANK - JOURNEY 7: KYC (PART 2)
## Enhanced Due Diligence, Source of Wealth, Refresh & Perpetual KYC

**Document Version:** 2.1  
**Date:** June 1, 2026  
**Continuation:** Part 2 of 2 (Sub-Journeys JY-7.5 through JY-7.8)

---

## JY-7.5: ENHANCED DUE DILIGENCE (EDD)

**Purpose:** Perform additional verification for high-risk customers, PEPs, and HNW individuals

**Entry Points:**
- High risk score (71-100) from JY-7.4 risk assessment
- PEP confirmation from sanctions/PEP screening
- Large transaction attempted (>AED 500K)
- Suspicious activity detected by monitoring system
- Customer requests premium services (private banking, investment advisory)

**User Type:** 
- HNW customers (>AED 5M net worth)
- Politically Exposed Persons (PEPs)
- High-risk occupation (cash-intensive business, crypto, forex)
- High-risk nationality (FATF grey/black list countries)
- Complex ownership structures (multiple entities, offshore companies)

**Prerequisites:**
- Standard KYC complete (JY-7.1 through JY-7.4)
- Customer consent for enhanced verification
- Senior management approval initiated

**EDD Requirements:**
- Additional document collection (comprehensive SoW/SoF)
- Enhanced background checks
- Senior management approval (Head of Compliance or above)
- Ongoing enhanced monitoring (daily transaction review)
- Annual refresh (vs. 5-year for low-risk)

---

### USER FLOW: JY-7.5 Enhanced Due Diligence

#### Step 1: EDD Notification
**User Action:** Customer sees notification that additional verification is required  
**System Response:**
- Displays message: "Additional Verification Required"
- Explanation: "To complete your account setup, we need additional information. This is a standard process for [premium accounts / certain customer profiles]"
- Reason provided (non-stigmatizing):
  - For HNW: "As a premium customer, we need additional details to serve you better"
  - For PEPs: "We're required by law to perform enhanced verification for public officials"
  - For High-Risk: "Additional verification required to activate all features"
- Estimated time: "10-15 minutes to complete, plus 1-2 business days for review"
- CTA: "Start Enhanced Verification"
- Option to schedule call: "Prefer to speak with us? Schedule a call with our compliance team"

**Customer Support:**
- Dedicated EDD support line provided (English + Arabic)
- Relationship manager assigned for HNW customers
- Compliance specialist assigned for PEPs

---

#### Step 2: Enhanced Document Collection
**User Action:** Uploads additional documents beyond standard KYC  
**System Response:**
- Displays comprehensive checklist based on customer category:

**For HNW Customers:**
```
✓ Emirates ID - Verified (from JY-7.1)
✓ Proof of Address - Verified (from JY-7.2)
○ Source of Wealth Statement - Required
○ Tax Returns (Last 2 Years) - Required
○ Bank Statements (Last 6 Months) - Required
○ Investment Portfolio Statement - Optional
○ Business Ownership Documents - If applicable
○ Audited Financial Statements - If business owner
```

**For PEPs:**
```
All HNW documents PLUS:
○ PEP Declaration Form - Required
○ Position/Role Description - Required
○ Family Tree (RCA Mapping) - Required
○ Government Transparency Report - If available
```

**Document Guidance:**
- **Source of Wealth Statement:** "Detailed explanation of how you accumulated your wealth over time"
- **Tax Returns:** "Last 2 years accepted (PDF from tax authority preferred)"
- **Bank Statements:** "Full statements from primary bank(s) showing transaction history"
- **Business Documents:** "Trade license, ownership structure, MOA if applicable"
- **PEP Declaration:** "List current and past government positions, including dates"

**Document Upload Process:**
- Same as JY-7.2 (photo capture, OCR, auto-verification)
- Additional manual review required for all EDD documents (auto-verification disabled)
- Compliance team review SLA: 1-2 business days

**Edge Cases:**
- **Documents in Foreign Language:** "Please provide English or Arabic translation (certified translation accepted)"
- **Complex Ownership Structure:** "Please upload organizational chart showing all entities and ownership percentages"
- **Multiple Income Sources:** "Please provide documentation for each source separately"
- **Cryptocurrency Holdings:** "Please provide exchange statements showing source of funds"

**SLA Target:** 15-20 minutes for document upload (customer side)

---

#### Step 3: Source of Wealth Questionnaire
**User Action:** Completes detailed SoW questionnaire  
**System Response:**
- Displays smart form with conditional logic (questions adapt based on answers)

**Sample Questions:**
1. **Primary Source of Wealth:** (Dropdown)
   - Employment/Salary
   - Business Ownership
   - Inheritance
   - Investment Returns
   - Real Estate
   - Sale of Business
   - Other (specify)

2. **Wealth Accumulation Timeline:** (Structured input)
   - "How many years did it take to accumulate current wealth?" (slider: 1-50 years)
   - "Approximate current net worth?" (dropdown: <AED 5M, 5-20M, 20-50M, 50M+)

3. **Employment Details:** (If "Employment" selected)
   - "Current employer name"
   - "Position title"
   - "Years with current employer"
   - "Annual salary range"
   - "Bonuses/stock options?" (Yes/No → If Yes, provide details)

4. **Business Ownership:** (If "Business" selected)
   - "Business name and industry"
   - "Ownership percentage"
   - "Annual revenue range"
   - "Number of employees"
   - "Years in operation"
   - "How was business funded initially?" (Loan, personal savings, investors, etc.)

5. **Inheritance Details:** (If "Inheritance" selected)
   - "Relationship to benefactor"
   - "Year received"
   - "Approximate value at time of receipt"
   - "Documentation available?" (Yes/No)

6. **Investment Portfolio:** (If "Investments" selected)
   - "Primary investment types" (Stocks, bonds, real estate, private equity, crypto, etc.)
   - "Investment account location(s)" (UAE banks, international brokers, etc.)
   - "Source of initial investment capital" (Savings, loan, inheritance, etc.)

7. **Real Estate Holdings:**
   - "Number of properties owned"
   - "Property locations" (UAE emirates, international)
   - "Primary residence value"
   - "Investment properties value"
   - "Mortgage status" (Paid off, mortgaged)

8. **Expected Account Activity:**
   - "Expected monthly deposits" (Range)
   - "Expected monthly withdrawals" (Range)
   - "Expected international transfers" (Yes/No → If Yes, countries and purpose)
   - "Expected cash deposits" (Yes/No → If Yes, frequency and source)

**Smart Form Logic:**
- If "Business Owner" → automatically asks for trade license upload
- If "Inheritance" → asks for probate/will documentation
- If "Cryptocurrency" → asks for exchange statements and blockchain addresses
- If "International Transfers" → asks for countries and purpose (triggers FATCA/CRS checks)

**Sharia Compliance Check:**
- For each income source, asks: "Is this income Sharia-compliant?" (Yes/No)
- If "No" → triggers Sharia review by Sharia Supervisory Board
- Examples of non-compliant sources: Interest income, alcohol/tobacco business, gambling, pork products

**Edge Cases:**
- **Multiple Sources:** Form supports multiple selections with percentage allocation
- **Complex Structures:** Free-text field for detailed explanations
- **Privacy Concerns:** Optional "I prefer to discuss this with compliance team" checkbox

**SLA Target:** 10-15 minutes for questionnaire completion

---

#### Step 4: Background Checks & Third-Party Verification
**User Action:** Consents to enhanced background checks  
**System Response:**
- Displays consent form: "We may contact third parties to verify information provided"
- Checkboxes:
  - ☑ "I consent to credit bureau checks"
  - ☑ "I consent to employment verification (if applicable)"
  - ☑ "I consent to business registry searches"
  - ☑ "I consent to adverse media screening"
- Privacy notice: "Information collected will only be used for compliance purposes"
- CTA: "I Consent"

**Backend Verification Process (Compliance Team):**
1. **Credit Bureau Check:** Al Etihad Credit Bureau (UAE) for credit history
2. **Employment Verification:** If salaried, contact HR department for confirmation
3. **Business Registry:** Check Dubai DED/ADDED/other emirate authorities for trade license validity
4. **Property Registry:** Dubai Land Department / Abu Dhabi Municipality for real estate ownership
5. **Court Records:** Check for any litigation, bankruptcies, criminal records
6. **Adverse Media:** Deep scan for negative news articles, scandals, investigations
7. **Enhanced PEP Screening:** Family tree verification, relationship mapping to other PEPs
8. **International Checks:** For non-UAE nationals, check home country databases (if accessible)

**Verification Timeline:** 1-2 business days (may extend to 5 days for complex cases)

**Edge Cases:**
- **Verification Fails:** Compliance team contacts customer for clarification
- **Conflicting Information:** Customer interview scheduled to resolve discrepancies
- **Negative Media Found:** Customer given opportunity to explain/provide context

---

#### Step 5: Senior Management Approval
**User Action:** Waits while compliance team reviews and escalates for approval  
**System Response:**
- Displays: "Your application is under review by our compliance team"
- Estimated timeline: "We'll update you within 1-2 business days"
- Progress tracker shown:
  ```
  ✓ Documents Received
  ⏳ Compliance Review (In Progress)
  ○ Senior Approval (Pending)
  ○ Final Decision
  ```
- Customer can track status in app

**Backend Approval Workflow:**
1. **Compliance Analyst Review:** Junior analyst reviews all documents, scores risk (0-100)
2. **Compliance Manager Review:** Manager validates analysis, adds notes
3. **Head of Compliance Approval:** Final decision for high-risk/PEP customers
4. **CEO Approval:** Required for ultra-high-risk (sanctioned countries, adverse media, etc.)

**Approval Criteria:**
- All documents authentic and complete
- SoW/SoF plausible and verifiable
- No unresolved adverse media
- No sanctions/watchlist matches
- Sharia compliance confirmed (for Sharia accounts)
- Risk appetite within L'Imad's policy limits

**Decision Point:**
- **Approved:** Proceeds to Step 6 (Success)
- **Approved with Conditions:** E.g., lower transaction limits, enhanced monitoring, restricted products
- **Rejected:** Customer notified with reason, right to appeal provided

**Approval Timeline SLA:**
- **Standard EDD:** 1-2 business days
- **Complex Cases:** Up to 5 business days
- **Appeals:** Up to 10 business days

---

#### Step 6: EDD Completion & Account Activation
**User Action:** Receives notification that EDD is approved  
**System Response:**
- Push notification: "Great news! Your account is approved"
- Email with details:
  ```
  Dear [Customer Name],

  Your Enhanced Verification is complete. Your L'Imad account is now fully activated.

  ✓ All features unlocked
  ✓ Premium services available
  ✓ Dedicated relationship manager: [Name, Phone, Email]

  Transaction Limits:
  - Daily transfer limit: AED 500,000
  - Monthly limit: AED 5,000,000
  - International transfer: Enabled

  Next Steps:
  - Fund your account to start banking
  - Schedule onboarding call with your relationship manager
  - Explore investment opportunities

  Welcome to L'Imad Premium Banking!
  ```
- In-app welcome screen with premium features highlighted
- Relationship manager contact details prominently displayed

**Backend Actions:**
- Account fully activated (no restrictions)
- Premium features enabled (investment advisory, concierge, etc.)
- Enhanced monitoring enabled (daily transaction review by compliance)
- Annual refresh scheduled (vs. 5-year for standard customers)
- Customer tagged as "EDD Complete" in CRM
- Relationship manager assigned and notified

**Data Stored:**
- EDD completion date
- Approved risk category (high-risk-approved)
- Senior approver name and timestamp
- SoW/SoF summary (for ongoing reference)
- Next EDD refresh due date (1 year)
- Monitoring thresholds and alerts configured

---

### SUCCESS OUTCOME
- EDD complete and approved
- Account fully activated with premium features
- Dedicated relationship manager assigned
- Enhanced monitoring in place
- Annual refresh scheduled

---

### REJECTION OUTCOME
- EDD rejected with specific reason
- Customer notified via email/phone call
- Right to appeal explained (10-day window)
- Alternative options offered:
  - Lower-tier account (standard retail) if partial approval possible
  - Refund of any deposits made
  - Assistance with account closure

**Rejection Reasons:**
- Unverifiable Source of Wealth
- Conflicting information not resolved
- Adverse media indicating criminal activity
- Sanctions/watchlist match confirmed
- Non-compliant with Sharia (for Sharia accounts)
- Outside L'Imad's risk appetite

---

### EXIT POINTS

1. **EDD Approved:** Account activated → proceeds to initial funding (Journey 5)
2. **EDD Approved with Conditions:** Account activated with restrictions → monitoring enhanced
3. **EDD Rejected:** Account creation blocked → customer offered appeal or refund
4. **Customer Abandons EDD:** Progress saved → follow-up call from compliance team after 48 hours

---

### EDGE CASES & ERROR HANDLING

| Scenario | System Response | User Action | Outcome |
|----------|-----------------|-------------|---------|
| **PEP Status Disputed** | "Please provide evidence you're not a PEP" | Uploads proof | If proven, downgraded to standard KYC |
| **Complex Offshore Structure** | "Please provide full ownership chart" | Uploads detailed structure | Additional review time (5-10 days) |
| **Cryptocurrency Wealth** | "Provide blockchain transaction history" | Uploads exchange statements + addresses | Sharia review + enhanced monitoring |
| **Inherited Wealth (Decades Ago)** | "Documentation unavailable due to age?" | Explains via free-text | Compliance makes judgment call |
| **Multiple Citizenships** | "Which passport will you use for account?" | Selects primary | Risk assessed on all citizenships |
| **Recent Bankruptcy** | "Please explain circumstances and current financial status" | Provides explanation + current statements | Case-by-case decision |
| **Adverse Media (False)** | "This article isn't about you?" | Provides clarification | If proven false, cleared |
| **Family Member of Sanctioned Person** | "Are you connected to [sanctioned person]?" | Denies or explains | Enhanced scrutiny; may be rejected |

---

### SECURITY MEASURES

- **Enhanced Monitoring:** All transactions reviewed by compliance team (not just automated)
- **Daily Screening:** Customer rescreened daily against sanctions/PEP lists
- **Relationship Manager Oversight:** RM required to have quarterly review calls
- **Annual Refresh:** Full EDD repeated annually (vs. 5-year for standard)
- **Transaction Alerts:** Lower thresholds for alerts (e.g., >AED 100K instead of >AED 500K)
- **Audit Trail:** Every EDD decision logged with approver name and rationale

---

### REGULATORY COMPLIANCE

**UAE EDD Requirements:**
- Senior management approval mandatory for PEPs (CBUAE requirement)
- Source of Wealth verification for high-risk customers (AML/CFT Law)
- Annual refresh for PEPs (FATF recommendation implemented by UAE)
- goAML reporting for any suspicious findings during EDD

**International Standards:**
- FATF Recommendation 12: PEPs must undergo EDD
- FATF Recommendation 10: EDD for high-risk customers
- Wolfsberg Group: Enhanced verification for private banking clients

---

### ACCESSIBILITY CONSIDERATIONS

- **Language Support:** EDD questionnaire available in English, Arabic
- **Personal Assistance:** Relationship manager can help complete complex SoW questionnaires
- **Alternative Formats:** Paper forms accepted if customer prefers (scanned and uploaded)
- **Extended Deadlines:** Customers can request deadline extensions for document gathering
- **Privacy:** EDD conducted with highest confidentiality standards

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **EDD completion time (customer side)** | <30 minutes | Industry: 45-90 min |
| **Compliance review SLA** | 1-2 business days | Industry: 5-10 days |
| **Senior approval SLA** | Same day (if submitted by 2 PM) | Industry: 2-5 days |
| **Appeal resolution SLA** | 10 business days | Industry: 30 days |
| **EDD approval rate** | >70% | Industry: 60-70% |
| **Customer satisfaction (EDD process)** | >4.0/5 | Industry: 3.5/5 |

---

## JY-7.6: SOURCE OF WEALTH / FUNDS VERIFICATION

**Purpose:** Verify the origin of specific large transactions or accumulated wealth for ongoing compliance

**Entry Points:**
- Large deposit (>AED 100K) from new source
- Large withdrawal (>AED 100K)
- Large transfer (>AED 500K)
- Significant balance increase (>50% month-over-month)
- Customer requests investment product (>AED 250K)
- Annual EDD refresh for HNW customers
- Transaction inconsistent with customer profile

**User Type:**
- All customers (for large transactions)
- HNW customers (periodic verification)
- Customers with significant wealth changes

**Prerequisites:**
- Account active and verified
- Transaction initiated or wealth change detected

**Verification Scope:**
- **Source of Funds (SoF):** Origin of specific transaction money
- **Source of Wealth (SoW):** Total accumulated wealth verification

---

### USER FLOW: JY-7.6 Source of Wealth/Funds Verification

#### Step 1: Verification Trigger
**User Action:** Attempts large transaction or system detects wealth change  
**System Response:**
- Transaction temporarily held (not rejected)
- Displays: "Additional Verification Needed"
- Message: "To proceed with this [deposit/transfer], please verify the source of funds"
- Reason: "This is a standard compliance requirement for transactions over AED 100,000"
- Estimated time: "5-10 minutes to provide information"
- Options:
  - "Provide Information Now" (preferred)
  - "Schedule Call with Compliance" (alternative)
  - "Cancel Transaction" (exit)

**Trigger Thresholds:**
| Transaction Type | Threshold (SoF Required) |
|------------------|--------------------------|
| Deposit (single) | >AED 100,000 |
| Withdrawal (single) | >AED 100,000 |
| Domestic transfer | >AED 500,000 |
| International transfer | >AED 100,000 |
| Cash deposit | >AED 50,000 |
| Cumulative daily | >AED 200,000 |
| Balance increase (% change) | >50% month-over-month |

---

#### Step 2: Source of Funds Declaration
**User Action:** Selects source of funds from dropdown or free-text  
**System Response:**
- Displays SoF form with pre-populated transaction details:
  ```
  Transaction: Deposit AED 150,000
  From: [Bank name, account holder]
  Date: [Today's date]
  ```
- Dropdown menu: "What is the source of this AED 150,000?"
  - ○ Salary/Employment Income
  - ○ Business Revenue/Profit
  - ○ Sale of Asset (property, car, investment)
  - ○ Loan from Bank
  - ○ Gift from Family Member
  - ○ Inheritance
  - ○ Investment Returns/Dividends
  - ○ Savings Accumulated Over Time
  - ○ Other (please specify)

**Conditional Follow-Up Questions:**

**If "Salary":**
- "Employer name?" (Auto-populated from profile if already provided)
- "Is this a bonus or regular salary?" (Bonus, Salary, Both)
- "Please upload: Recent payslip showing this amount"

**If "Business Revenue":**
- "Business name?" (Auto-populated if known)
- "Please upload: Invoice/receipt or bank statement showing business income"
- "Is this revenue Sharia-compliant?" (Yes/No) → If No, Sharia review triggered

**If "Sale of Asset":**
- "What asset did you sell?" (Property, Vehicle, Stocks, Jewelry, Other)
- "Approximate sale value?"
- "Please upload: Sale agreement or confirmation from buyer"

**If "Loan":**
- "Lender name?" (Bank name)
- "Loan purpose?" (Business, Personal, Mortgage refinance, etc.)
- "Please upload: Loan agreement or disbursement confirmation"
- Sharia check: "Is this a Sharia-compliant financing arrangement?" (Murabaha, Ijara, Musharaka, etc.)

**If "Gift":**
- "Relationship to donor?" (Parent, Spouse, Sibling, Other family, Friend)
- "Donor's full name?"
- "Please upload: Gift letter signed by donor OR bank transfer showing donor's account"
- Trigger: If gift >AED 200K, donor's SoW may be requested

**If "Inheritance":**
- "Relationship to deceased?"
- "Approximate date of inheritance?"
- "Please upload: Probate document, will, or inheritance distribution certificate"

**If "Investment Returns":**
- "Investment type?" (Stocks, Mutual Funds, Real Estate, Crypto, Other)
- "Investment account/platform?"
- "Please upload: Account statement showing gain/dividend"

**If "Savings":**
- "Time period over which savings accumulated?" (Months/Years)
- "Primary source of savings?" (Salary, Business, etc.)
- "Please upload: Bank statements showing accumulation pattern"

**Edge Cases:**
- **Multiple Sources:** "This AED 150K comes from multiple sources?" → allows adding multiple entries with amounts
- **Cannot Provide Docs:** "I don't have documentation" → routes to compliance call
- **Privacy Concerns:** "I prefer not to disclose" → informs that transaction will be blocked until verified

**SLA Target:** 5-10 minutes for SoF declaration

---

#### Step 3: Document Upload (Supporting Evidence)
**User Action:** Uploads requested supporting document  
**System Response:**
- Uses same document capture UI as JY-7.2 (OCR, auto-verification)
- Validates document matches declared source:
  - **Payslip:** OCR extracts employer name, amount → compares to declaration
  - **Bank Statement:** OCR extracts account holder, transaction amount → validates
  - **Sale Agreement:** OCR extracts parties, amount, date → validates
  - **Gift Letter:** Manual review required (no auto-verification)

**Document Requirements by Source:**

| Source | Acceptable Documents |
|--------|----------------------|
| Salary | Payslip, Employment Contract, Bank Statement showing salary credit |
| Business | Invoice, Receipt, Business Bank Statement, Audited Accounts |
| Asset Sale | Sale Agreement, Title Transfer, Broker Confirmation, Payment Receipt |
| Loan | Loan Agreement, Disbursement Confirmation, Bank Transfer Record |
| Gift | Gift Letter (signed by donor), Donor's Bank Statement, Transfer Confirmation |
| Inheritance | Probate Document, Will, Court Order, Inheritance Distribution Certificate |
| Investment | Brokerage Statement, Dividend Notice, Capital Gains Statement |
| Savings | Bank Statements (6-12 months showing accumulation pattern) |

**Edge Cases:**
- **Document in Foreign Language:** "Please provide English or Arabic translation"
- **Document Not Available:** "Alternative: Schedule call with compliance to explain verbally"
- **Document Incomplete:** "This document is missing [X]. Please upload complete version"
- **Document Expired/Old:** "Please provide recent document (within 3 months for statements)"

**SLA Target:** 10 minutes for document upload and validation

---

#### Step 4: Compliance Review
**User Action:** Waits while compliance team reviews SoF declaration  
**System Response:**
- Displays: "Your information is being reviewed"
- Estimated time: "Most reviews complete within 2 hours (business hours)"
- Transaction status: "Your [deposit/transfer] is pending review"
- Customer can continue using app (transaction just held temporarily)

**Backend Review Process:**
1. **Automated Checks:**
   - Document authenticity (AI detection)
   - Amount consistency (declared vs. documented)
   - Name matching (customer vs. document names)
   - Date validation (document recent enough)
   - Sharia compliance (if applicable)

2. **Compliance Analyst Review:**
   - Reviews declaration and documents
   - Cross-references with customer profile and history
   - Checks for red flags:
     - Inconsistent with customer's known income
     - Source doesn't match customer profile (e.g., salary but customer is self-employed)
     - Suspicious patterns (frequent large gifts from unrelated persons)
     - High-risk sources (crypto, forex, cash-intensive business)
   - Makes recommendation: Approve, Request More Info, or Escalate

3. **Escalation (If Needed):**
   - Manager review for amounts >AED 500K or red flags
   - Head of Compliance for suspicious cases
   - SAR (Suspicious Activity Report) filed if warranted

**Decision Point:**
- **Approved:** Proceeds to Step 5 (Transaction Released)
- **More Info Needed:** Customer receives request for clarification or additional docs
- **Rejected/Blocked:** Transaction canceled, customer notified, account may be reviewed

**Review SLA:**
- **Auto-Approved (70% of cases):** <5 minutes
- **Standard Manual Review:** 2-4 hours (business hours)
- **Complex Cases:** 24-48 hours
- **After-Hours/Weekends:** Next business day

---

#### Step 5: Verification Complete & Transaction Released
**User Action:** Receives notification that SoF is verified  
**System Response:**
- Push notification: "Your transaction is approved and processing"
- In-app message: "Source of funds verified ✓"
- Transaction proceeds:
  - **Deposit:** Funds credited to account
  - **Transfer:** Payment sent to beneficiary
  - **Withdrawal:** Cash prepared for collection
- Confirmation details shown:
  ```
  ✓ Transaction Approved
  Amount: AED 150,000
  Source: Salary (Verified)
  Status: Processing
  Expected completion: [Date/Time]
  ```

**Backend Actions:**
- Transaction released from hold
- SoF record stored in customer profile (for future reference)
- If same source used again within 6 months, auto-approved without re-verification
- Risk profile updated (if SoF changes understanding of customer wealth)
- Audit trail logged (compliance)

**Future Optimization:**
- If customer frequently receives salary deposits, those are auto-approved after first verification
- If customer has verified SoW statement on file, SoF verification may be waived for amounts within expected range

---

### SUCCESS OUTCOME
- Source of funds verified and documented
- Transaction approved and processed
- Compliance requirement fulfilled
- Customer can continue banking without interruption

---

### BLOCKED OUTCOME
- SoF verification failed (suspicious, inconsistent, or undocumented)
- Transaction canceled and funds returned (if deposit)
- Account may be flagged for enhanced monitoring
- Customer notified of reason and next steps
- Possible outcomes:
  - Provide alternative documentation
  - Explain discrepancies via compliance call
  - Accept transaction cancellation
  - Close account if unwilling to verify

---

### EXIT POINTS

1. **SoF Verified:** Transaction released → customer continues banking
2. **SoF Auto-Approved (Repeat Source):** Instant approval for subsequent similar transactions
3. **SoF Rejected:** Transaction canceled → customer can appeal or provide alternative docs
4. **Customer Cancels:** Transaction canceled → no further action
5. **SAR Filed:** Account under investigation → customer notified if required by law

---

### EDGE CASES & ERROR HANDLING

| Scenario | System Response | User Action | Outcome |
|----------|-----------------|-------------|---------|
| **Gift from Unknown Person** | "Please explain relationship to donor" | Provides explanation | Enhanced review; may be rejected if suspicious |
| **Cryptocurrency Sale** | "Please provide blockchain transaction history" | Uploads exchange statement | Sharia review + enhanced scrutiny |
| **Offshore Source** | "Please provide foreign tax documentation" | Uploads foreign bank statement | FATCA/CRS checks triggered |
| **Round Number (e.g., AED 100K exact)** | "Is this a partial payment or full amount?" | Clarifies | Validates against documentation |
| **Frequent Large Gifts** | "Receiving multiple gifts may require donor verification" | Cooperates or explains | May require donor's SoW |
| **Business Revenue (Cash-Heavy)** | "Cash revenue requires additional verification" | Provides business records | Enhanced monitoring activated |
| **No Documentation Available** | "Without documentation, we cannot approve this transaction" | Accepts or schedules compliance call | Transaction blocked unless explained |
| **Conflicting Info** | "Your payslip shows AED 80K but you declared AED 150K" | Explains (e.g., bonus + salary) | Clarification resolves; must match docs |

---

### SECURITY MEASURES

- **Historical Pattern Analysis:** System compares SoF to customer's previous transactions and profile
- **Velocity Checks:** Flags if customer submits multiple SoF verifications in short time (structuring detection)
- **Cross-Customer Analysis:** Detects if multiple customers declare gifts from same donor (possible money mule network)
- **Sharia Compliance:** All SoF/SoW checked against Sharia principles (interest income flagged)
- **Audit Trail:** Every SoF declaration and approval logged with timestamp and reviewer ID

---

### REGULATORY COMPLIANCE

**UAE Requirements:**
- **CDD Threshold:** Transactions ≥AED 55,000 require source verification (L'Imad uses AED 100K for better UX)
- **Suspicious Transactions:** Any transaction lacking plausible SoF must be reported to FIU
- **Record Retention:** SoF declarations retained for 5 years minimum

**Sharia Requirements:**
- Source of Wealth/Funds must originate from halal (permissible) activities
- Interest income, alcohol, gambling, pork, etc. are haram (forbidden) and must be rejected or purified
- Sharia Supervisory Board reviews flagged SoF declarations

---

### ACCESSIBILITY CONSIDERATIONS

- **Simplified Option:** For customers with limited tech literacy, offer "Call Compliance" button for phone-based SoF declaration
- **Language Support:** SoF form available in English, Arabic, Hindi, Urdu
- **Document Alternatives:** Accept verbal explanation if customer cannot provide written documentation (recorded call)
- **Extended Timeline:** Customers can request 48-hour extension if they need time to gather documents

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **SoF declaration time (customer)** | <10 minutes | Industry: 15-30 min |
| **Auto-approval rate** | >70% | Industry: 30-50% |
| **Manual review SLA** | <2 hours (business hours) | Industry: 24 hours |
| **Repeat source auto-approval** | <1 minute | Industry: manual every time |
| **Customer satisfaction** | >4.2/5 | Industry: 3.8/5 |
| **Transaction drop-off rate** | <10% (customers abandoning due to SoF) | Industry: 20-30% |

---

## JY-7.7: PERIODIC KYC REFRESH

**Purpose:** Re-verify customer information at scheduled intervals to maintain compliance and accurate risk profiles

**Entry Points:**
- Scheduled refresh due date (based on risk category)
- Customer initiates profile update
- Document expiration (e.g., Emirates ID, visa)
- System detects significant profile changes (occupation, address, etc.)
- Regulatory audit trigger

**Refresh Frequency by Risk Category:**
- **Low Risk:** Every 5 years
- **Medium Risk:** Every 2 years
- **High Risk / PEPs:** Annually
- **HNW with EDD:** Annually
- **Exceptional High Risk:** Semi-annually (6 months)

**User Type:** All customers (mandatory)

**Refresh Scope:**
- **Minimal (Low Risk):** Confirm contact details, Emirates ID still valid, update occupation if changed
- **Standard (Medium Risk):** Re-upload documents (address proof, income), confirm transaction patterns still accurate
- **Comprehensive (High Risk):** Full EDD refresh, updated SoW/SoF, enhanced screening, senior approval

---

### USER FLOW: JY-7.7 Periodic KYC Refresh

#### Step 1: Refresh Notification
**User Action:** Receives notification that KYC refresh is due  
**System Response:**
- **30 days before due:** Email reminder: "Your account information needs updating soon"
- **14 days before due:** Push notification: "Please update your details within 2 weeks"
- **7 days before due:** SMS: "Action required: Update your L'Imad account info"
- **3 days before due:** In-app banner (persistent): "Update your details to avoid account restrictions"
- **Due date:** Account restrictions activated (read-only mode):
  - Cannot send transfers
  - Cannot make withdrawals
  - Can still receive deposits
  - Card transactions limited to existing balance

**Message Content:**
```
Time to Update Your Details

UAE regulations require us to refresh your account information every [X years].

What You Need:
- 5-10 minutes of your time
- Updated Emirates ID (if renewed)
- Recent proof of address

Why It's Important:
Your account may be restricted if we don't receive updated information by [date].

[Update Now Button]
```

---

#### Step 2: Refresh Scope Determination
**User Action:** Taps "Update Now" → lands on refresh screen  
**System Response:**
- Displays personalized refresh checklist based on risk category:

**Low-Risk Customer Checklist:**
```
Please Confirm or Update:
✓ Name: [Pre-filled from profile]
✓ Emirates ID: xxxx-xxxx-1234 (Expires: [date])
  ○ Upload New ID if expired
✓ Mobile: +971 50 xxx xxxx
✓ Email: user@example.com
✓ Address: [Pre-filled] - Is this still current? Yes / No
✓ Occupation: [Pre-filled] - Still accurate? Yes / No
✓ Expected Transaction Activity: Still <AED 50K/month? Yes / No
```

**Medium-Risk Customer Checklist:**
```
All Low-Risk items PLUS:
○ Proof of Address (Recent utility bill or bank statement)
○ Income Verification (Salary certificate or 3-month bank statement)
○ Confirm Source of Funds still valid
```

**High-Risk / PEP Checklist:**
```
All Medium-Risk items PLUS:
○ Updated Source of Wealth Statement
○ Tax Returns (Last 2 years)
○ Bank Statements (Last 6 months)
○ PEP Status (Still in office? Retired? New position?)
○ Business Ownership Changes (If applicable)
```

**Estimated Time:**
- Low-Risk: 5 minutes
- Medium-Risk: 10-15 minutes
- High-Risk: 20-30 minutes (plus 1-2 days compliance review)

---

#### Step 3: Information Update
**User Action:** Reviews pre-filled data and updates as needed  
**System Response:**
- Pre-populates all fields with current profile data
- User can:
  - ✓ Confirm unchanged fields (single tap)
  - ✏️ Edit fields that changed
  - 📷 Upload new documents if required

**Common Changes:**
- **Address Changed:** Upload new proof of address (utility bill, tenancy contract, bank statement)
- **Occupation Changed:** Select new occupation → may trigger risk re-assessment
- **Emirates ID Renewed:** Upload new ID → OCR extracts new expiry date
- **Income Changed:** Upload new salary certificate → update expected transaction volumes
- **Business Ownership Changed:** Upload new trade license or ownership docs

**Conditional Logic:**
- If occupation changed from "Employee" to "Business Owner" → system requests business documents
- If address changed to different emirate → system may request additional verification
- If income increased significantly (>50%) → system may request Source of Wealth explanation
- If customer now holds political position → automatically flags for PEP review

**Edge Cases:**
- **Everything Unchanged:** Customer can confirm all details with single "Confirm All" button (fastest path)
- **Major Life Event:** Marriage, divorce, inheritance → customer can add notes to explain significant profile changes
- **Multiple Changes:** System prioritizes critical fields (ID, address) over optional fields (preferences)

**SLA Target:** 5-15 minutes depending on number of changes

---

#### Step 4: Document Re-Upload (If Required)
**User Action:** Uploads updated documents (same flow as JY-7.2)  
**System Response:**
- Uses document capture UI from JY-7.2
- OCR processes new documents
- Auto-verifies where possible
- Flags for manual review if:
  - Document authenticity score low
  - Information conflicts with previous profile
  - Significant changes detected (e.g., income doubled)

**Documents Commonly Refreshed:**
- **Emirates ID:** If expired or expiring within 3 months
- **Proof of Address:** If older than 3 months (medium/high-risk only)
- **Income Proof:** If income changed or >12 months old (medium/high-risk only)
- **Trade License:** If business ownership changed (self-employed/business owners)

---

#### Step 5: Re-Screening (Automated)
**User Action:** Waits while system re-screens against updated databases  
**System Response:**
- Backend process (automatic, no user interaction):
  1. **Sanctions/PEP Screening:** Re-runs against latest watchlists
  2. **Risk Re-Assessment:** Recalculates risk score based on updated profile
  3. **Adverse Media Scan:** Checks for any new negative news
  4. **Credit Bureau Check:** (Optional, for medium/high-risk) updates credit profile

**Decision Point:**
- **No Changes in Risk:** Customer remains in same category → proceeds to Step 6 (Success)
- **Risk Increased:** Customer moved to higher risk category → may require EDD (JY-7.5)
- **Risk Decreased:** Customer moved to lower risk category → fewer restrictions
- **PEP Status Confirmed:** New PEP or existing PEP → triggers EDD
- **Sanctions Match:** Account immediately frozen → compliance team notified

**SLA Target:** 10-15 seconds for automated re-screening

---

#### Step 6: Compliance Review (If Flagged)
**User Action:** Waits for manual review (if changes are significant or documents need verification)  
**System Response:**
- Displays: "Your updated information is being reviewed"
- Estimated time:
  - **Low-Risk:** Auto-approved (<5 minutes)
  - **Medium-Risk with minor changes:** 2-4 hours
  - **High-Risk or significant changes:** 1-2 business days
- Customer can continue using account in read-only mode until approved

**Manual Review Triggers:**
- Occupation changed to high-risk category (crypto, forex, cash business)
- Address changed to high-risk jurisdiction
- Income increased >50%
- New business ownership disclosed
- Emirates ID shows new nationality (naturalization)
- Document authenticity score <85%

---

#### Step 7: Refresh Complete & Account Unrestricted
**User Action:** Receives confirmation that refresh is complete  
**System Response:**
- Push notification: "Your account is updated and unrestricted ✓"
- Email confirmation:
  ```
  KYC Refresh Complete

  Thank you for updating your information.

  ✓ All restrictions removed
  ✓ Full account access restored
  ✓ Next refresh due: [Date in X years]

  Your updated profile:
  - Risk Category: [Low/Medium/High]
  - Transaction Limits: [Details]
  - Features Available: [List]
  ```
- Account restrictions lifted immediately:
  - Transfers enabled
  - Withdrawals enabled
  - Cards unrestricted
  - Investment products accessible (if eligible)

**Backend Actions:**
- Updates customer profile with new data
- Resets refresh due date (1/2/5 years from now)
- Logs refresh completion in audit trail
- Sends summary to compliance dashboard
- Updates risk monitoring thresholds if risk category changed

---

### SUCCESS OUTCOME
- Customer information updated and verified
- Risk profile current and accurate
- Account fully functional (no restrictions)
- Next refresh scheduled

---

### FAILED REFRESH OUTCOME
- Customer did not complete refresh by due date
- Account remains restricted (read-only)
- **Grace Period:** 30 days to complete refresh
- **After Grace Period:** Account fully suspended (cannot receive funds either)
- **After 90 Days:** Account closure initiated per UAE regulations

**Communication During Failed Refresh:**
- **Daily reminders** during grace period
- **Phone call from support** at 15 days overdue
- **Final warning at 25 days:** "Complete refresh within 5 days or account will be suspended"
- **Suspension notice:** "Your account is now suspended. Contact support to reactivate"

---

### EXIT POINTS

1. **Refresh Complete:** Account unrestricted → customer resumes normal banking
2. **Refresh Incomplete:** Account restricted → daily reminders until complete
3. **Customer Unresponsive:** Account suspended after grace period → requires support contact to reactivate
4. **Risk Escalation:** Moved to higher risk tier → triggers EDD (JY-7.5)
5. **Sanctions Match:** Account frozen → compliance investigation → possible closure

---

### EDGE CASES & ERROR HANDLING

| Scenario | System Response | User Action | Outcome |
|----------|-----------------|-------------|---------|
| **Emirates ID Expired** | "Please renew your ID with ICA before continuing" | Renews ID, uploads | Refresh proceeds after renewal |
| **Traveling (Out of Country)** | "Extend your refresh deadline?" button | Requests 30-day extension | Extension granted (once only) |
| **Documents Lost** | "Alternative verification: Schedule call with compliance" | Calls compliance team | Verbal verification accepted temporarily |
| **Major Changes (Multiple)** | "Significant changes detected. Compliance will review" | Waits for review call | Compliance interview scheduled |
| **Conflicting Data** | "Your stated income is [X] but documents show [Y]" | Explains or corrects | Clarification required before approval |
| **Customer Refuses Refresh** | "Without updated info, we must restrict your account per UAE law" | Accepts restriction or completes refresh | Account restricted if refused |
| **Deceased Customer** | Family reports death | Estate documentation required | Account frozen, estate process initiated |
| **Customer Relocated Abroad** | "You're no longer a UAE resident?" | Confirms | Account may need to be closed per license restrictions |

---

### SECURITY MEASURES

- **Automated Reminders:** Multi-channel (email, SMS, push, in-app) to ensure customer sees notification
- **Grace Period:** 30 days post-due date before harsh restrictions (customer-friendly)
- **Graduated Restrictions:** Read-only → full suspension (not immediate closure)
- **Audit Compliance:** All refresh activities logged for regulatory audits
- **Data Validation:** Every field change cross-checked against previous profile for anomalies

---

### REGULATORY COMPLIANCE

**UAE Requirements:**
- **CBUAE Regulation:** Periodic KYC refresh mandatory (frequency based on risk)
- **FATF Recommendation 10:** Ongoing due diligence throughout relationship
- **Record Retention:** All refresh records retained for 5 years

**Refresh Frequency Compliance:**
- Low-Risk: 5 years (UAE standard)
- Medium-Risk: 2 years (CBUAE best practice)
- High-Risk/PEPs: Annual (FATF requirement for PEPs)

---

### ACCESSIBILITY CONSIDERATIONS

- **Simplified Path:** Low-risk customers can confirm all details with one tap if nothing changed
- **Offline Option:** Customers can visit branch (future) or call support to complete refresh over phone
- **Extended Deadlines:** Customers can request extensions for valid reasons (travel, illness, etc.)
- **Language Support:** Refresh forms available in English, Arabic, Hindi, Urdu
- **Customer Support:** Dedicated refresh support line for assistance

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **Refresh completion rate** | >95% (within 30 days of due date) | Industry: 80-85% |
| **Low-risk refresh time** | <5 minutes | Industry: 10-15 min |
| **Medium-risk refresh time** | <15 minutes | Industry: 20-30 min |
| **Auto-approval rate** | >80% (low-risk) | Industry: 60-70% |
| **Compliance review SLA** | <4 hours (medium), <2 days (high) | Industry: 1-5 days |
| **Reminder effectiveness** | >90% complete after 2nd reminder | Industry: 60-70% |

---

## JY-7.8: ONGOING MONITORING (PERPETUAL KYC)

**Purpose:** Continuously monitor customer activity and profile for changes, anomalies, and emerging risks in real-time

**Entry Points:**
- Continuous (24/7 automated monitoring)
- Triggered by specific events (transactions, profile changes, external data updates)
- Scheduled batch processes (daily sanctions screening, weekly pattern analysis)

**User Type:** All customers (automated, mostly invisible to customer)

**Monitoring Scope:**
- **Transaction Monitoring:** Real-time analysis of all transactions for suspicious patterns
- **Behavioral Monitoring:** Changes in customer behavior compared to historical baseline
- **External Data Monitoring:** Sanctions lists, PEP databases, adverse media, credit bureau
- **Document Monitoring:** Emirates ID expiry, visa expiry, trade license expiry
- **Risk Drift Monitoring:** Gradual or sudden changes in customer risk profile

**Technology:**
- AI/ML models for anomaly detection
- Rule-based alerts for regulatory thresholds
- Real-time API integration with external databases
- Predictive analytics for risk forecasting

---

### MONITORING TYPES & TRIGGERS

#### 1. Transaction Pattern Monitoring
**What's Monitored:**
- Transaction frequency (sudden increase/decrease)
- Transaction amounts (unusually large or small)
- Transaction timing (late-night transactions, transactions during customer's known sleep hours)
- Geographic patterns (new countries, high-risk jurisdictions)
- Beneficiary patterns (new beneficiaries, frequent changes, multiple unknown beneficiaries)
- Channel patterns (switching from mobile to web/ATM suddenly)

**Alert Triggers:**
| Pattern | Threshold | Alert Level | Action |
|---------|-----------|-------------|--------|
| Daily transaction count spike | >300% of average | 🟡 Medium | Compliance review within 24h |
| Single large transaction | >AED 500K | 🟠 High | SoF verification required |
| Cumulative daily transactions | >AED 1M | 🟠 High | SoF + compliance review |
| Rapid fund movement (in/out) | >AED 200K within 24h | 🟠 High | Possible layering; SAR review |
| Multiple round-number transactions | 3+ transactions of exact AED 10K, 50K, 100K | 🟡 Medium | Possible structuring; review |
| Late-night transactions (2-5 AM) | 5+ in one week | 🟡 Medium | Behavioral anomaly; review |
| New high-risk country transfer | First-time transfer to FATF grey/black list country | 🔴 Critical | Hold transaction; manual approval required |

**Customer Impact:**
- Most monitoring is **silent** (no customer notification)
- Alerts that require action (SoF verification) trigger in-app prompts
- Transactions may be temporarily held (1-2 hours) during review

---

#### 2. Sanctions & PEP Rescreening
**What's Monitored:**
- Daily rescreening against updated sanctions lists
- Weekly PEP database updates
- Real-time alerts when lists are updated (OFAC SDN, UN, EU, UAE)

**Rescreening Frequency:**
- **High-Risk/PEPs:** Daily (automated batch job at 2 AM UAE time)
- **Medium-Risk:** Weekly (Sunday batch job)
- **Low-Risk:** Monthly (first of each month)
- **All Customers:** Real-time when sanctions lists updated mid-cycle

**Alert Triggers:**
| Event | Impact | Action |
|-------|--------|--------|
| New sanctions match | 🔴 Critical | Immediate account freeze; all transactions blocked; FIU notification within 24h |
| New PEP status | 🟠 High | Account flagged; EDD required within 30 days; enhanced monitoring activated |
| PEP status removed (retired) | 🟡 Medium | Maintain PEP treatment for 2 years; then downgrade to standard |
| Family member of PEP (RCA) | 🟠 High | EDD required; enhanced monitoring |

**Customer Communication:**
- Sanctions match: "Your account is temporarily restricted. Please contact support"
- PEP match: "Additional verification required for your account" (email within 24h)

---

#### 3. Adverse Media Monitoring
**What's Monitored:**
- News articles mentioning customer name
- Court records and legal filings
- Bankruptcy filings
- Regulatory actions (securities violations, license suspensions, etc.)
- Social media (for HNW/PEPs only; LinkedIn, Twitter for business-related posts)

**Data Sources:**
- LexisNexis
- Dow Jones Risk & Compliance
- Local UAE news aggregators (Gulf News, Khaleej Times, etc.)
- International news (Reuters, Bloomberg, Financial Times)
- Court records (UAE federal courts, Dubai courts, Abu Dhabi courts)

**Alert Triggers:**
| Adverse Event | Severity | Action |
|---------------|----------|--------|
| Criminal charges filed | 🔴 Critical | Account flagged; compliance review within 24h; possible account closure |
| Bankruptcy filing | 🟠 High | Enhanced monitoring; credit limit restrictions |
| Lawsuit (plaintiff or defendant) | 🟡 Medium | Compliance review; context-dependent action |
| Negative business press | 🟡 Medium | Review article; assess reputational risk |
| Regulatory action (e.g., trade license suspended) | 🟠 High | Account review; possible restrictions |

**Customer Communication:**
- Customer is **not notified** of adverse media monitoring (compliance only)
- If account action required (restrictions, closure), customer is contacted by relationship manager or compliance

---

#### 4. Behavioral Anomaly Detection
**What's Monitored:**
- Changes in customer behavior compared to historical baseline
- ML models learn "normal" behavior for each customer over first 3-6 months

**Anomalies Detected:**
| Behavioral Change | Example | Alert |
|-------------------|---------|-------|
| Sudden increase in transaction volume | Customer who typically does 5 transactions/month suddenly does 50 | 🟡 Medium |
| Change in transaction type | Customer who only receives salary suddenly starts international transfers | 🟡 Medium |
| Geographic anomaly | Customer who banks only in UAE suddenly has transactions in 5 countries | 🟠 High |
| Device/location anomaly | Login from new device in foreign country immediately after UAE login (impossible travel) | 🔴 Critical (fraud) |
| Dormant account reactivation | Account inactive for 6+ months suddenly active | 🟡 Medium |
| Channel shift | Customer who only uses mobile app suddenly uses ATM/web exclusively | 🟡 Medium |

**Customer Impact:**
- Fraud alerts (impossible travel, new device) trigger **Step-Up Authentication** (Journey 3.5)
- Suspicious behavior alerts may trigger **SoF requests** or **compliance calls**
- Severe anomalies may temporarily **restrict account** until verified

---

#### 5. Document Expiry Monitoring
**What's Monitored:**
- Emirates ID expiry date
- Visa expiry (for expats)
- Trade license expiry (for business owners)
- Proof of address age (>3 months old)

**Proactive Notifications:**
| Document | Reminder Schedule | Action If Expired |
|----------|-------------------|-------------------|
| Emirates ID | 60 days, 30 days, 14 days before expiry | Account restricted 30 days after expiry |
| Visa | 30 days, 14 days before expiry | Account restricted immediately after expiry (non-resident) |
| Trade License | 30 days before expiry | Business account restricted after expiry |
| Proof of Address | 90 days before 6-month mark (medium/high-risk) | Request updated document |

**Customer Communication:**
- Email + SMS + Push notification at each reminder interval
- In-app banner when document expiring <30 days

---

#### 6. Risk Drift Monitoring
**What's Monitored:**
- Gradual changes in customer risk profile that don't trigger single-event alerts
- Composite risk score recalculated weekly

**Risk Drift Indicators:**
- Increasing transaction volumes over 3-6 months
- Adding beneficiaries in high-risk countries
- Increasing international transfer frequency
- Balance growth (wealth accumulation)
- Occupation changes reported
- Address changes to higher-risk emirates/countries

**Action:**
- If risk score increases >20 points over 6 months → trigger **early KYC refresh** (JY-7.7)
- If risk category changes (Low→Medium, Medium→High) → trigger **EDD** (JY-7.5)

---

### CUSTOMER-FACING OUTCOMES

**Perpetual KYC is mostly invisible to customers, except when:**

1. **Transaction Hold:**
   - "Your transfer is being reviewed. This usually takes 1-2 hours"
   - Reason: Triggered alert requires compliance review

2. **SoF Request:**
   - "Please verify the source of this AED 150K deposit"
   - Reason: Transaction exceeded SoF threshold or flagged by anomaly detection

3. **Document Update Request:**
   - "Your Emirates ID is expiring soon. Please update to avoid restrictions"
   - Reason: Proactive document monitoring

4. **Enhanced Monitoring Notification (PEPs only):**
   - "As a politically exposed person, your account is subject to enhanced monitoring per UAE regulations"
   - Reason: Transparency requirement

5. **Account Restriction:**
   - "Your account is temporarily restricted. Please contact support"
   - Reason: Sanctions match, fraud alert, or expired documents

---

### BACKEND COMPLIANCE DASHBOARD

**Compliance Team View:**
- **Real-Time Alerts:** Queue of all triggered alerts sorted by priority
- **Alert Details:** Customer profile, triggering event, historical context, recommended action
- **Case Management:** Assign alerts to analysts, track resolution, document decisions
- **Reporting:** Generate SAR, STR, CTR reports for FIU via goAML integration
- **Audit Trail:** Every alert and action logged for regulatory audits

**Alert Queue Example:**
```
🔴 CRITICAL (Action Required Within 1 Hour):
- Customer ID 12345: Sanctions match (OFAC SDN List) → FREEZE ACCOUNT
- Customer ID 67890: Impossible travel detected → VERIFY DEVICE

🟠 HIGH (Action Required Within 4 Hours):
- Customer ID 11111: New PEP status confirmed → INITIATE EDD
- Customer ID 22222: Large transfer AED 800K to high-risk country → HOLD & VERIFY SoF

🟡 MEDIUM (Action Required Within 24 Hours):
- Customer ID 33333: Transaction pattern anomaly (10x normal volume) → REVIEW
- Customer ID 44444: Adverse media: lawsuit filed → ASSESS RISK
```

---

### SUCCESS OUTCOME
- Risks detected early and mitigated proactively
- Regulatory compliance maintained continuously
- Customer experience minimally impacted (most monitoring silent)
- Fraud prevented through real-time detection

---

### ALERT RESOLUTION OUTCOMES

**Alert Cleared:**
- Compliance team reviews → determines alert is false positive or low risk → clears alert
- Customer unaffected (no notification)
- Transaction proceeds (if held)

**Alert Escalated:**
- Compliance team escalates to manager or Head of Compliance
- Customer may be contacted for clarification
- Additional documentation requested (SoF, SoW, etc.)
- Account may be restricted pending resolution

**SAR Filed:**
- Suspicious activity confirmed → SAR filed with FIU via goAML
- Customer is **not notified** (tipping off is illegal)
- Enhanced monitoring activated permanently
- Account may be closed after SAR filing (at bank's discretion)

**Account Closed:**
- Sanctions match confirmed, criminal activity suspected, or customer uncooperative
- Customer notified: "We are unable to continue banking relationship"
- Funds returned to source (after regulatory clearance)
- Customer blacklisted (cannot reapply)

---

### EDGE CASES & FALSE POSITIVES

| Scenario | System Response | Outcome |
|----------|-----------------|---------|
| **Common Name Alert** | "Ahmed Mohamed Ali" matches 50+ PEPs | Compliance reviews DOB, nationality → clears |
| **Legitimate Business Activity** | Cash-intensive restaurant owner has high cash deposits | Enhanced monitoring but no restrictions |
| **Family Gift (Large)** | AED 500K gift from parent | SoF requested → gift letter clears alert |
| **Vacation Spending Spike** | Customer abroad, many ATM withdrawals | Geo-pattern recognized as travel → cleared |
| **Impossible Travel (VPN User)** | Login from UAE, then login from US 5 min later | System detects VPN → prompts "Are you using VPN?" → customer confirms → cleared |
| **Dormant Reactivation (Legitimate)** | Customer returns to UAE after years abroad | Compliance reviews → confirms legitimate → cleared |
| **Inherited Wealth (Sudden Balance Increase)** | AED 2M inheritance deposited | SoF requested → inheritance docs clear alert |

**False Positive Management:**
- ML models continuously learn from resolved alerts
- Confirmed false positives are whitelisted (same pattern won't trigger again for that customer)
- Feedback loop: Compliance team marks alerts as "False Positive" → model adjusts thresholds

---

### SECURITY MEASURES

- **24/7 Monitoring:** Automated systems never sleep
- **Multi-Layer Defense:** Rule-based + ML models + human review
- **Encrypted Logs:** All monitoring logs encrypted and access-restricted
- **Audit Trail:** Every alert, decision, and action logged for 5+ years
- **Regulatory Reporting:** Automated SAR/STR/CTR generation and filing via goAML

---

### REGULATORY COMPLIANCE

**UAE Requirements:**
- **Ongoing Monitoring:** CBUAE requires continuous transaction monitoring (not just onboarding)
- **Daily Screening:** High-risk customers must be screened daily against sanctions lists
- **SAR Filing:** Suspicious transactions must be reported within 24 hours (expedited) or 15 business days (complex)
- **Record Retention:** All monitoring logs retained for 5 years

**International Standards:**
- **FATF Recommendation 10:** Ongoing due diligence throughout customer relationship
- **FATF Recommendation 20:** Suspicious transaction reporting
- **Basel AML Index:** Risk-based monitoring intensity

---

### ACCESSIBILITY CONSIDERATIONS

- **Transparency:** Customers can request explanation of account restrictions (unless SAR filed)
- **Appeal Process:** Customers can appeal false positives or account closures
- **Customer Support:** Dedicated compliance support line for monitoring-related questions

---

### PERFORMANCE SLA TARGETS

| Metric | Target | Current Benchmark (Competitors) |
|--------|--------|--------------------------------|
| **Alert response time (critical)** | <1 hour | Industry: 4 hours |
| **Alert response time (high)** | <4 hours | Industry: 24 hours |
| **False positive rate** | <10% | Industry: 20-30% |
| **SAR filing SLA** | <24 hours (expedited cases) | Regulatory requirement |
| **Sanctions screening frequency** | Daily (high-risk), weekly (medium), monthly (low) | Industry: weekly/monthly |
| **Transaction hold time (review)** | <2 hours (90% of cases) | Industry: 4-24 hours |
| **Customer impact rate** | <2% (customers who experience holds/restrictions monthly) | Industry: 5-10% |

---

## JOURNEY 7 SUMMARY: KYC METRICS DASHBOARD

**Comprehensive KYC Performance Metrics**

### Overall KYC Journey Metrics

| Metric | Target | Rationale |
|--------|--------|-----------|
| **End-to-End KYC Completion Time** | <10 minutes (low-risk), <20 min (medium), <30 min (high) + compliance review | Competitive advantage; Liv: 5-7 min, ADIB: 10-15 min |
| **First-Time KYC Success Rate** | >85% (no manual review) | Automation efficiency |
| **KYC Drop-Off Rate** | <15% | Customer experience quality |
| **Manual Review Rate** | <15% | Automation effectiveness |
| **KYC Rejection Rate** | <5% | Balanced compliance and growth |
| **Customer Satisfaction (KYC Process)** | >4.3/5 | Process clarity and ease |

### Sub-Journey Metrics

**JY-7.1: Initial Identity Verification**
- Emirates ID capture success (first attempt): >90%
- ICA validation time: <5 seconds
- Facial recognition success: >85%
- Verification drop-off: <10%

**JY-7.2: Document Collection**
- OCR accuracy: >90%
- Auto-approval rate: >75%
- Document rejection rate: <15%
- Average documents per customer: 3-4

**JY-7.3: Biometric Verification**
- Face registration success: >90%
- Fingerprint registration success: >85%
- Liveness detection success: >95%
- Future biometric login success: >98%

**JY-7.4: Risk Assessment & Screening**
- Screening time: <10 seconds
- Auto-clearance rate: >85%
- False positive rate (sanctions): <5%
- PEP detection accuracy: >95%

**JY-7.5: Enhanced Due Diligence**
- EDD approval rate: >70%
- EDD review time: 1-2 business days (standard), 5 days (complex)
- Customer satisfaction (EDD): >4.0/5
- EDD drop-off rate: <20%

**JY-7.6: Source of Wealth/Funds**
- SoF verification time: <2 hours (business hours)
- Auto-approval rate (repeat sources): >80%
- SoF drop-off rate: <10%
- Customer satisfaction: >4.2/5

**JY-7.7: Periodic Refresh**
- Refresh completion rate: >95% (within 30 days)
- Low-risk refresh time: <5 minutes
- Reminder effectiveness: >90% (complete after 2nd reminder)

**JY-7.8: Perpetual KYC**
- Alert response time (critical): <1 hour
- False positive rate: <10%
- Customer impact rate: <2% (monthly)
- Transaction hold time: <2 hours (90% of cases)

---

**END OF JOURNEY 7: KYC DOCUMENTATION**

**Total Journey 7 Content:**
- **Sub-Journeys:** 8 comprehensive flows
- **User Flow Steps:** 100+ detailed steps across all sub-journeys
- **Decision Points:** 50+ documented decision trees
- **Edge Cases:** 80+ edge case scenarios with handling
- **Security Measures:** 60+ specific security controls
- **SLA Targets:** 50+ performance metrics defined
- **Regulatory Requirements:** Full UAE/international compliance coverage

**Journey 7 now fully integrated into L'Imad Digital Bank benchmark documentation.**
