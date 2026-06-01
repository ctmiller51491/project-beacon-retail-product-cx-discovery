# L'IMAD DIGITAL BANK - USER FLOW MAPPING DOCUMENT (PART 2)
## Journeys 5-6: Deposits & Servicing

**Continued from Part 1**

---

# JOURNEY 5: DEPOSITS

## Overview
**Purpose:** Enable customers to add funds to their accounts through various channels  
**Primary Users:** All customers  
**Success Criteria:** Funds successfully credited to account with clear confirmation  
**Average Duration:** 2-5 minutes (instant for internal transfers, 1-2 business days for external)  
**Launch Phase:** Must-Have

---

## Sub-Journey 5.1: External Bank Transfer (Incoming)

### User Flow JY-5.1: Receive Transfer from Another UAE Bank

**Entry Point:** Customer wants to transfer funds from external bank account

**Flow Steps:**

1. **Access IBAN Details**
   - User: Taps "Add Money" on home screen
   - System: Displays funding options:
     - Transfer from another bank
     - Cash deposit
     - Debit card transfer
     - Cheque deposit
   - User: Selects "Transfer from another bank"

2. **IBAN Display and Instructions**
   - System: Displays L'Imad account IBAN prominently
   - System: Shows copy button and share options
   - System: Displays instructions:
     - "Use this IBAN to transfer from your other bank"
     - "Domestic transfers usually arrive within 1 hour"
     - "International transfers may take 1-3 business days"
     - "Add your name as beneficiary for faster processing"
   - User: Copies IBAN or shares via SMS/Email/WhatsApp
   - System: Provides "Done - I've initiated the transfer" button
   - User: Taps "Done"

3. **Transfer Initiation Confirmation**
   - System: Shows "We'll notify you when funds arrive"
   - System: Offers to set up reminders (optional):
     - "Remind me in 1 hour if not received"
     - "Remind me tomorrow if not received"
   - User: Sets reminder or skips
   - System: Monitors incoming UAEFTS for matching IBAN

4. **Transfer Received Notification**
   - System: Detects incoming transfer via UAEFTS
   - System: Credits account in real-time
   - System: Sends push notification: "AED [amount] received from [Sender Bank]"
   - System: Updates account balance on home screen
   - User: Opens app to view updated balance

**Success Outcome:** Funds transferred from external bank and credited to L'Imad account

**Edge Cases:**
- Transfer delayed >1 hour → Proactive notification: "Your transfer is taking longer than usual. This can happen with some banks. We'll credit funds as soon as we receive them."
- Sender name mismatch → Manual review required, customer notified
- Large amount (>AED 100,000) → Automatic AML screening, may cause 1-2 hour delay

---

## Sub-Journey 5.2: Cash Deposit at Partner Locations

### User Flow JY-5.2: Deposit Cash at Exchange or Retail Partner

**Entry Point:** User selects "Cash deposit" from Add Money screen

**Flow Steps:**

1. **Partner Location Finder**
   - System: Displays "Deposit cash at 500+ locations across UAE"
   - System: Shows map with nearest partner locations:
     - UAE Exchange branches
     - Al Ansari Exchange branches
     - Select Carrefour locations
     - Select ENOC/EPPCO stations
   - System: Shows list view with:
     - Partner name and branch
     - Distance from current location
     - Operating hours
     - "Get Directions" button
   - User: Selects location
   - User: Taps "Get Directions"
   - System: Opens Google Maps / Apple Maps with directions

2. **Deposit Code Generation**
   - System: Generates unique 8-digit deposit code valid for 24 hours
   - System: Displays code prominently: "Show this code at the partner location"
   - System: Shows QR code (alternative to typing code)
   - System: Lists deposit limits:
     - Minimum: AED 100
     - Maximum per transaction: AED 10,000
     - Maximum per day: AED 20,000
   - User: Notes deposit code or screenshots
   - User: Travels to partner location

3. **At Partner Location**
   - User: Arrives at partner location
   - User: Provides deposit code (verbal or QR scan) and cash to agent
   - Agent: Enters code into partner system
   - Partner System: Validates code with L'Imad backend
   - **Decision Point:** Code valid?
     - ✓ Valid: Agent accepts cash
     - ✗ Invalid/Expired: Agent cannot proceed, customer must regenerate code in app
   - Agent: Counts cash and confirms amount
   - Agent: Provides receipt to customer
   - Partner System: Sends deposit confirmation to L'Imad

4. **Deposit Confirmation**
   - System: Receives deposit notification from partner (real-time API)
   - System: Credits account within 5 minutes
   - System: Sends push notification "AED [amount] cash deposited at [Partner Name]"
   - System: Updates account balance
   - User: Receives confirmation SMS and email with transaction ID

**Success Outcome:** Cash deposited and credited to account within 5 minutes

**Edge Cases:**
- Code expired (>24 hours) → Customer must generate new code in app
- Amount exceeds daily limit → Agent rejects, customer notified of limit
- Partner system offline → Agent manually records, credited within 2 hours after reconciliation
- Discrepancy in amount → Partner agent contacts support, resolution within 24 hours

---

## Sub-Journey 5.3: Debit Card Transfer

### User Flow JY-5.3: Transfer from Another Bank's Debit Card

**Entry Point:** User selects "Debit card transfer" from Add Money screen

**Flow Steps:**

1. **Card Link Introduction**
   - System: Displays "Add funds using your debit card from another bank"
   - System: Shows benefits:
     - "Instant transfer (funds available in minutes)"
     - "Securely save card for future use"
     - "No L'Imad fees (your bank may charge)"
   - System: Shows supported card types: Visa, Mastercard
   - User: Taps "Continue"

2. **Card Details Entry**
   - System: Displays card entry form:
     - Card Number (16 digits with spacing)
     - Cardholder Name (as on card)
     - Expiry Date (MM/YY)
     - CVV (3 digits)
   - System: Option to scan card using camera (OCR)
   - User: Enters card details manually or scans
   - System: Validates card format in real-time
   - System: Checkbox: "Save this card for future deposits"
   - User: Completes form and taps "Continue"

3. **3D Secure Authentication**
   - System: Forwards to issuing bank's 3D Secure page
   - System: Displays "Authenticating with [Bank Name]..."
   - Issuing Bank: Prompts customer authentication (OTP, biometric, or password)
   - User: Completes authentication on bank's page
   - System: Receives authentication result
   - **Decision Point:** Authentication successful?
     - ✓ Success: Continue to amount entry
     - ✗ Failure: Show error "Authentication failed. Please check your details or try another card"

4. **Transfer Amount Entry**
   - System: Displays "How much would you like to transfer?"
   - System: Shows limits:
     - Minimum: AED 100
     - Maximum: AED 10,000 per transaction
   - User: Enters amount
   - System: Shows fee breakdown:
     - Amount: AED [entered amount]
     - L'Imad Fee: AED 0 (free)
     - Card Issuer Fee: May apply (check with your bank)
     - Total to be charged: AED [amount]
   - User: Taps "Transfer Now"

5. **Payment Processing**
   - System: Displays "Processing payment..." with loading indicator
   - System: Charges card via payment gateway
   - System: Waits for authorization (5-30 seconds)
   - **Decision Point:** Payment result?
     - ✓ **Approved:** Continue to confirmation
     - ✗ **Declined:** Show decline reason and alternative options
     - ⚠ **Pending:** Show "Your transfer is being processed. We'll notify you once complete"

6. **Transfer Confirmation**
   - System: Credits account instantly upon approval
   - System: Displays success screen:
     - "Transfer successful!"
     - Amount: AED [amount]
     - From: [Card ending in XXXX]
     - New Balance: AED [balance]
   - System: Sends push notification and email confirmation
   - **If card saved:** System shows "Card ending in XXXX saved for future use"

**Success Outcome:** Funds transferred from debit card and credited instantly

**Edge Cases:**
- Card declined (insufficient funds) → Suggest trying lower amount or alternative method
- Card declined (fraud concern) → Suggest contacting issuing bank, offer alternative deposit methods
- 3D Secure timeout → Allow retry, session valid for 10 minutes
- Saved card expired → Prompt to update card details

---

## Sub-Journey 5.4: Cheque Deposit (Mobile)

### User Flow JY-5.4: Deposit Cheque via Mobile App

**Entry Point:** User selects "Cheque deposit" from Add Money screen

**Flow Steps:**

1. **Cheque Deposit Introduction**
   - System: Displays "Deposit cheques using your phone"
   - System: Shows requirements:
     - Cheque must be drawn on a UAE bank
     - Payable to account holder name
     - Not post-dated
     - Amount under AED 50,000 (mobile deposit limit)
   - System: Shows processing time: "Funds available in 2-3 business days after clearance"
   - User: Taps "Start Deposit"

2. **Cheque Details Entry**
   - System: Displays form:
     - Cheque Amount (manual entry for validation)
     - Cheque Number (optional, for tracking)
     - Issuing Bank (dropdown of UAE banks)
     - Cheque Date (date picker)
   - User: Fills in cheque details
   - User: Taps "Continue to Photo Capture"

3. **Cheque Photo Capture - Front**
   - System: Opens camera with cheque frame overlay
   - System: Displays instructions:
     - "Place cheque on flat surface"
     - "Ensure good lighting, no shadows"
     - "All 4 corners must be visible"
   - User: Positions cheque within frame
   - System: Provides real-time feedback: "Move closer", "Reduce glare", "Hold steady"
   - System: Auto-captures when positioned correctly
   - System: Displays captured image with "Retake" or "Use Photo" options
   - User: Reviews and confirms or retakes

4. **Cheque Photo Capture - Back**
   - System: Prompts "Now photo the back of the cheque"
   - System: Shows endorsement instruction: "Please sign the back of the cheque before photographing"
   - User: Signs back of cheque (endorsement)
   - User: Positions back of cheque within frame
   - System: Auto-captures
   - System: Displays back image for review
   - User: Confirms

5. **OCR Extraction and Validation**
   - System: Displays "Analyzing cheque..." with loading indicator
   - System: Performs OCR on front image to extract:
     - MICR code (bank routing and cheque number)
     - Amount (numeric and written)
     - Date
     - Payee name
   - System: Validates extracted data against manually entered amount
   - **Decision Point:** OCR extraction successful and matches?
     - ✓ Match: Continue to submission
     - ⚠ Mismatch: Show warning "Extracted amount (AED X) doesn't match entered amount (AED Y). Please verify."
     - ✗ Extraction failed: Prompt manual entry of all fields

6. **Cheque Submission**
   - System: Displays deposit summary:
     - Cheque Amount: AED [amount]
     - Issuing Bank: [Bank Name]
     - Cheque Number: [Number]
     - Expected Clearance: [Date] (2-3 business days)
   - System: Shows disclaimer: "Funds will be available after cheque clearance. Returned cheques may incur fees."
   - User: Taps "Submit Deposit"
   - System: Uploads cheque images to backend
   - System: Creates deposit ticket
   - System: Displays "Cheque deposit submitted!" with tracking number

7. **Cheque Processing and Clearance**
   - System: Routes cheque to clearing house
   - System: Tracks clearance status (2-3 business days)
   - **Day 1-2:** Status: "Cheque submitted for clearance"
   - **Day 2-3:** Status: "Cheque clearing in progress"
   - **Decision Point:** Clearance result?
     - ✓ **Cleared:** Credits account, sends notification "Cheque cleared! AED [amount] added to your account"
     - ✗ **Returned:** Sends notification "Cheque returned by issuing bank. Reason: [Insufficient funds / Stop payment / Other]"

**Success Outcome:** Cheque deposited and cleared, funds available in account

**Edge Cases:**
- Cheque returned (insufficient funds) → Customer notified, AED 50 return fee charged
- Cheque returned (signature mismatch) → Customer notified, return fee charged
- Amount over AED 50,000 → Must visit branch or use alternative deposit method
- Post-dated cheque → Rejected at OCR stage, customer notified
- Poor image quality → Prompt retake with better lighting/positioning

---

## Sub-Journey 5.5: Salary Transfer Setup

### User Flow JY-5.5: Set Up Direct Salary Deposit

**Entry Point:** User taps "Set up salary transfer" from home screen or account settings

**Flow Steps:**

1. **Salary Transfer Introduction**
   - System: Displays "Get your salary paid directly into your L'Imad account"
   - System: Shows benefits:
     - "Higher profit-sharing rate (up to 6.25% p.a. with salary transfer)"
     - "Automatic savings with Salary Sorter feature"
     - "Exclusive salary transfer offers"
   - System: Shows required information:
     - Account IBAN
     - Account certificate (generated in-app)
     - Employer name and HR contact
   - User: Taps "Get Started"

2. **Salary Transfer Letter Generation**
   - System: Displays "We'll create a salary transfer letter for your employer"
   - System: Requests information:
     - Current employer name (pre-filled from KYC if available)
     - HR department contact (name, email)
     - Monthly salary amount (optional, for letter)
   - User: Fills in details
   - User: Taps "Generate Letter"
   - System: Generates PDF salary transfer letter containing:
     - L'Imad bank letterhead
     - Account holder name
     - Account IBAN (highlighted)
     - Bank SWIFT code
     - Bank address
     - Salary transfer request statement
   - System: Downloads letter and sends to user's email

3. **Account Certificate Generation**
   - System: Also generates account certificate (as per Sub-Journey 4.6)
   - System: Downloads certificate containing:
     - Account holder name
     - Account number (IBAN)
     - Account opening date
     - Bank seal and signature
   - System: Bundles salary letter + certificate into one PDF

4. **Submission Instructions**
   - System: Displays "Next steps:"
     - "1. Download the salary transfer letter and certificate"
     - "2. Submit to your HR department"
     - "3. HR will update your salary payment details"
     - "4. Your next salary will be paid to L'Imad account"
   - System: Shows option "Share via email directly with HR"
   - User: Chooses to download or email HR directly
   - **If email HR:**
     - User: Enters HR email address
     - System: Sends email with subject "Salary Transfer Request - [Customer Name]" and attachments
     - System: CCs customer on email

5. **Salary Transfer Confirmation**
   - System: Tracks incoming salary payments
   - System: Detects first salary credit (recognized by amount pattern and employer reference)
   - System: Sends congratulatory notification: "Your salary has arrived! Enjoy your enhanced profit-sharing rate 🎉"
   - System: Automatically applies enhanced profit-sharing rate (e.g., 6.25% p.a. instead of 5.5%)
   - System: Offers to set up Salary Sorter: "Automatically distribute your salary to savings, bills, and spending accounts"

6. **Salary Sorter Setup (Optional)**
   - User: Taps "Set up Salary Sorter"
   - System: Displays distribution wizard:
     - "How would you like to split your salary?"
     - Savings: [slider] % or fixed AED amount → "Emergency Fund" sub-account
     - Bills: [slider] % or fixed AED amount → "Bills" sub-account
     - Spending: Remaining balance → "Main Account"
   - System: Shows preview based on estimated salary:
     - "Next month, AED X will go to Savings, AED Y to Bills, AED Z to Spending"
   - User: Adjusts distribution
   - User: Taps "Activate Salary Sorter"
   - System: Saves automation rule
   - System: Confirmation "Salary Sorter activated! Your next salary will be distributed automatically"

**Success Outcome:** Salary transfer set up, enhanced profit rate applied, optional auto-distribution configured

**Edge Cases:**
- Employer requires specific bank forms → Provide contact for L'Imad corporate banking team
- Salary delayed → Customer receives proactive notification if expected salary doesn't arrive on usual date
- Partial salary received → Salary Sorter uses actual amount received, not estimated
- Employer cancels salary transfer → Enhanced rate remains for 3 months grace period

---

## Journey 5 Success Metrics

**Target Metrics:**
- External transfer completion rate: 95%+ (funds received within 24 hours)
- Cash deposit success rate: 98%+ (at partner locations)
- Debit card transfer success rate: 85%+ (3D Secure and payment authorization)
- Cheque clearance rate: 90%+ (not returned)
- Cheque photo capture success (first attempt): 70%+
- Salary transfer setup completion: 60%+ of employed customers
- Average funding time (external transfer): <2 hours for domestic
- Customer satisfaction with deposit experience: 4.5★+ average

---

# JOURNEY 6: SERVICING

## Overview
**Purpose:** Provide customer support, troubleshooting, and issue resolution  
**Primary Users:** All customers with questions or problems  
**Success Criteria:** Issue resolved with minimal effort, high CSAT  
**Average Duration:** 2 minutes (FAQ) to 48 hours (escalated issues)  
**Launch Phase:** Must-Have

---

## Sub-Journey 6.1: Self-Service Help Center

### User Flow JY-6.1: Browse FAQ and Help Articles

**Entry Point:** User taps "Help" or "Support" icon in app

**Flow Steps:**

1. **Help Center Landing Page**
   - System: Displays help center with search bar and popular topics:
     - **Popular Articles:**
       - How to transfer money?
       - How to activate my card?
       - What are the fees and charges?
       - How to update my phone number?
       - How do I earn profit-sharing?
     - **Categories:**
       - 🏦 Accounts & Balances
       - 💳 Cards
       - 💸 Transfers & Payments
       - 📈 Investments
       - 🔒 Security & Privacy
       - 📄 Documents & Statements
       - ⚙️ Settings
   - System: Shows "Still need help? Chat with us" button at bottom
   - User: Can search or browse categories

2. **Search Help Articles**
   - User: Types query in search bar (e.g., "How to change PIN?")
   - System: Provides instant search suggestions as user types
   - System: Displays search results ranked by relevance:
     - Article title
     - Snippet with highlighted keywords
     - Category tag
     - "Was this helpful?" rating
   - User: Taps on article

3. **View Help Article**
   - System: Displays full article with:
     - Clear title
     - Step-by-step instructions with screenshots
     - Related articles at bottom
     - "Was this helpful? Yes / No" feedback buttons
     - "Contact Support" button if article doesn't solve issue
   - User: Reads article
   - User: Taps "Yes, this helped" or "No, I need more help"
   - **If "Yes":** System thanks user and suggests related articles
   - **If "No":** System offers "Chat with agent" or "Request callback"

4. **Video Tutorials**
   - System: For complex topics, shows video tutorial option
   - User: Taps "Watch Video Tutorial"
   - System: Opens in-app video player with tutorial (30-90 seconds)
   - System: Provides video controls (pause, rewind, captions)
   - User: Watches tutorial
   - System: After video, asks "Did this help?"

**Success Outcome:** Customer finds answer in self-service resources, issue resolved

**Edge Cases:**
- No search results → Suggest alternative keywords, offer to contact support
- Multiple articles match query → Rank by helpfulness ratings and view count
- User exits without feedback → Track article views but no confirmation of usefulness

---

## Sub-Journey 6.2: Live Chat Support

### User Flow JY-6.2: Chat with Customer Support Agent

**Entry Point:** User taps "Chat with us" from help center or home screen

**Flow Steps:**

1. **Chat Initiation**
   - System: Opens chat interface
   - System: Displays chat history (if previous conversations exist)
   - System: Auto-populated message: "Hi [Name], how can we help you today?"
   - System: Shows suggested quick actions:
     - 💳 Card Issues
     - 💸 Transfer Help
     - 🔒 Security Concerns
     - 📄 Document Request
     - 💬 Other
   - User: Taps quick action or types custom message

2. **AI Chatbot First Response**
   - System: AI chatbot analyzes user query
   - **Decision Point:** Can AI resolve?
     - **Simple Query (account balance, transaction status):** AI provides instant answer with relevant data
     - **FAQ-type (how-to questions):** AI suggests relevant help articles with "Was this helpful?" prompt
     - **Complex / Requires Agent:** AI says "Let me connect you with a specialist" and transfers to human agent
   - User: Interacts with AI or waits for human agent

3. **Transfer to Human Agent**
   - System: AI transfers chat to human agent queue
   - System: Displays "Connecting you to an agent..." with estimated wait time
   - System: Provides context to agent (customer name, account status, query topic)
   - System: Agent receives notification and picks up chat
   - Agent: Sends greeting "Hi [Name], I'm [Agent Name]. I can help you with [issue]. Can you provide more details?"

4. **Chat Conversation**
   - User: Explains issue in detail
   - Agent: Asks clarifying questions
   - Agent: Accesses customer account (with permission) to investigate
   - Agent: Provides solution or troubleshooting steps
   - **If Requires Verification:**
     - Agent: "For security, please verify your Emirates ID number"
     - User: Provides last 4 digits of Emirates ID
     - Agent: Validates and proceeds
   - **If Requires Escalation:**
     - Agent: "I need to escalate this to our specialist team. You'll receive a response within 24 hours via email"
     - Agent: Creates ticket and provides ticket number

5. **Issue Resolution**
   - Agent: Confirms "Is there anything else I can help with?"
   - User: "No, thanks" or asks follow-up
   - Agent: Closes chat with "Glad I could help! You'll receive a transcript via email. Have a great day!"
   - System: Sends chat transcript to user's email
   - System: Displays CSAT survey: "How was your experience? ⭐⭐⭐⭐⭐"
   - User: Rates experience (1-5 stars) and optionally leaves comment
   - System: Thanks user for feedback

**Success Outcome:** Issue resolved via live chat, customer satisfied

**Chat Features:**
- File attachment support (screenshots, documents)
- Agent can send links to help articles or app screens
- Agent can initiate screen sharing for troubleshooting
- Chat history saved and accessible
- 24/7 availability (English and Arabic support)

**SLA Targets:**
- AI first response: <5 seconds
- Human agent pickup: <2 minutes (average)
- Simple issue resolution: <5 minutes
- Complex issue resolution: <15 minutes or escalation

---

## Sub-Journey 6.3: Phone Support

### User Flow JY-6.3: Call Customer Support

**Entry Point:** User taps "Call Support" or dials support number from website/app

**Flow Steps:**

1. **Call Initiation**
   - User: Dials +971 X XXXX XXXX (24/7 support line)
   - System (IVR): "Welcome to L'Imad Digital Bank. For English, press 1. للعربية، اضغط 2"
   - User: Selects language

2. **IVR Menu Navigation**
   - System (IVR): "Please choose from the following options:
     - Press 1 for Account and Balance inquiries
     - Press 2 for Card services (lost/stolen, activation)
     - Press 3 for Transfers and Payments
     - Press 4 for Technical support
     - Press 5 to speak with an agent
     - Press 0 to repeat this menu"
   - User: Selects option or presses 5 for agent

3. **Authentication (If Necessary)**
   - System (IVR): "For security, please enter your Emirates ID number followed by hash"
   - User: Enters Emirates ID using phone keypad
   - System: Validates Emirates ID
   - System (IVR): "Please enter the last 4 digits of your account number followed by hash"
   - User: Enters last 4 digits
   - System: Authenticates customer
   - **Decision Point:** Authentication successful?
     - ✓ Success: Continue to agent or self-service options
     - ✗ Failure: Offer to try again or transfer to agent for manual verification

4. **Self-Service Options (IVR)**
   - **For simple queries, IVR offers self-service:**
     - "Press 1 to hear your account balance"
     - "Press 2 to hear your last 5 transactions"
     - "Press 3 to block your card"
     - "Press 4 to request a mini statement via SMS"
   - User: Selects option
   - System: Provides information or executes action
   - System: "Is there anything else? Press 1 for main menu, or stay on the line to speak with an agent"

5. **Transfer to Agent**
   - System: Transfers to agent queue
   - System: Plays hold music with estimated wait time
   - System: "Your estimated wait time is 3 minutes. Please stay on the line"
   - Agent: Answers call "Hello, this is [Agent Name] from L'Imad. How may I assist you today?"
   - User: Explains issue
   - Agent: Accesses customer account (pre-authenticated via IVR)
   - Agent: Resolves issue or escalates if necessary

6. **Call Resolution**
   - Agent: Confirms resolution "Is there anything else I can help with today?"
   - User: Confirms issue resolved
   - Agent: Thanks customer and provides reference number for call
   - Agent: Ends call
   - System: Sends SMS with call summary and reference number
   - System: Sends CSAT survey via SMS link

**Success Outcome:** Issue resolved via phone support

**Phone Support Features:**
- 24/7 availability (English and Arabic)
- Call recording for quality and training
- Callback option if wait time is >5 minutes
- Screen sharing capability (agent sends link via SMS)
- Secure call authentication via IVR

**SLA Targets:**
- Average wait time: <3 minutes
- First call resolution rate: 80%+
- Average handle time: <8 minutes
- Abandoned call rate: <5%

---

## Sub-Journey 6.4: Complaint Filing and Resolution

### User Flow JY-6.4: File and Track Formal Complaint

**Entry Point:** User needs to file official complaint

**Flow Steps:**

1. **Complaint Initiation**
   - User: Navigates to "Help" → "File a Complaint"
   - System: Displays complaint form introduction:
     - "We're sorry to hear you're experiencing an issue"
     - "We take complaints seriously and aim to resolve within 5 business days"
     - "You'll receive a complaint reference number for tracking"
   - User: Taps "File Complaint"

2. **Complaint Form Completion**
   - System: Displays complaint form:
     - **Complaint Category:** (dropdown)
       - Transaction dispute
       - Service quality
       - Card issue
       - Account access problem
       - Fee dispute
       - Privacy concern
       - Sharia compliance concern
       - Other
     - **Description:** (text area, 500 char max)
       - "Please describe your complaint in detail"
     - **Date of Incident:** (date picker)
     - **Attachments:** (optional - upload screenshots, documents)
     - **Preferred Resolution:** (text)
     - **Contact Preference:** Email / Phone / Chat
   - User: Fills in all required fields
   - User: Taps "Submit Complaint"

3. **Complaint Submission and Acknowledgment**
   - System: Validates form completion
   - System: Generates unique complaint reference number (e.g., CMP-2026-05-00123)
   - System: Displays confirmation:
     - "Your complaint has been submitted"
     - "Reference Number: CMP-2026-05-00123"
     - "Expected Resolution: [Date] (within 5 business days)"
     - "You'll receive email and SMS updates"
   - System: Sends confirmation email with details and reference number
   - System: Creates ticket in complaint management system

4. **Complaint Assignment and Investigation**
   - System: Routes complaint to appropriate team based on category
   - Assigned Agent: Reviews complaint within 24 hours
   - Agent: Investigates issue (reviews account, transactions, records)
   - **If More Info Needed:**
     - Agent: Sends email/SMS requesting additional details
     - User: Responds via email or chat
   - Agent: Updates complaint status: "Under Investigation"
   - System: Sends status update to customer

5. **Complaint Resolution**
   - Agent: Determines resolution (within 5 business days)
   - Agent: Updates complaint with resolution details
   - System: Sends resolution email to customer:
     - Complaint Reference: CMP-2026-05-00123
     - Resolution Summary: [detailed explanation]
     - Action Taken: [e.g., refund issued, fee waived, process corrected]
     - Compensation (if applicable): [amount or benefit]
     - Next Steps (if any)
   - **Decision Point:** Customer accepts resolution?
     - ✓ Accepted: Case closed
     - ✗ Not Satisfied: Customer can escalate to complaint review committee

6. **Escalation (If Needed)**
   - User: Replies to resolution email with "I'm not satisfied" or requests escalation
   - System: Flags complaint for escalation
   - System: Sends to Complaint Review Committee (senior management)
   - Committee: Reviews within 10 business days
   - Committee: Provides final decision
   - System: Communicates final resolution to customer
   - System: Provides information on external dispute resolution (DFSA Financial Ombudsman if still unresolved)

**Success Outcome:** Complaint filed, investigated, resolved within SLA

**Complaint Handling Standards:**
- Acknowledgment within 24 hours
- Investigation and resolution within 5 business days
- Escalation review within 10 business days (if needed)
- Regular status updates (every 2-3 days)
- Fair and transparent resolution
- Customer always informed of next steps and rights

---

## Sub-Journey 6.5: Transaction Dispute

### User Flow JY-6.5: Dispute Unauthorized or Incorrect Transaction

**Entry Point:** User sees unauthorized transaction in account

**Flow Steps:**

1. **Identify Disputed Transaction**
   - User: Views transaction history
   - User: Sees suspicious transaction
   - User: Taps on transaction to view details
   - System: Displays transaction detail screen
   - System: Shows "Report a Problem" or "Dispute Transaction" button
   - User: Taps "Dispute Transaction"

2. **Dispute Reason Selection**
   - System: Displays dispute reason options:
     - "I don't recognize this transaction" (fraud)
     - "Transaction amount is incorrect"
     - "I was charged twice"
     - "Merchant didn't deliver goods/services"
     - "I cancelled the transaction but was still charged"
     - "ATM didn't dispense cash but I was charged"
     - "Other"
   - User: Selects dispute reason
   - User: Taps "Continue"

3. **Dispute Details Entry**
   - System: Displays dispute form:
     - Transaction ID: [pre-filled]
     - Transaction Amount: [pre-filled]
     - Transaction Date: [pre-filled]
     - Merchant Name: [pre-filled]
     - **Your Description:** "Please explain the issue" (text area)
     - **Supporting Documents:** Upload receipts, correspondence, etc. (optional)
   - User: Provides details and uploads evidence
   - User: Taps "Submit Dispute"

4. **Immediate Actions**
   - System: Generates dispute reference number (e.g., DSP-2026-05-00456)
   - **For Fraud Cases (Unrecognized Transaction):**
     - System: Immediately freezes card to prevent further unauthorized charges
     - System: Displays "Your card has been frozen for security. We'll issue a new card."
     - System: Offers to issue replacement virtual card instantly
   - **For Merchant Disputes:**
     - System: Notes dispute but doesn't freeze card
   - System: Sends confirmation email with dispute reference number
   - System: Creates chargeback case with card network (Visa/Mastercard)

5. **Investigation Process**
   - System: Submits dispute to merchant's bank (for merchant disputes)
   - System: Allows merchant 30 days to respond (chargeback process)
   - **Interim Credit (if applicable):**
     - For fraud cases: Provisional credit issued within 5 business days
     - System: Credits disputed amount temporarily
     - System: Sends notification "Provisional credit of AED [amount] has been applied to your account while we investigate"
   - Agent: Reviews all evidence from customer and merchant
   - System: Sends status updates every 7 days

6. **Dispute Resolution**
   - **Decision Point:** Outcome?
     - **✓ Customer Wins:**
       - System: Finalizes credit (makes provisional credit permanent)
       - System: Sends confirmation "Your dispute has been resolved in your favor. The credit of AED [amount] is now permanent."
     - **✗ Merchant Wins:**
       - System: Reverses provisional credit
       - System: Sends explanation "After investigation, the transaction was found to be valid. Here's why: [explanation]"
       - System: Offers customer right to escalate if not satisfied
     - **⚠ Requires More Info:**
       - System: Requests additional documentation from customer
       - User: Provides additional evidence
       - Investigation continues

**Success Outcome:** Dispute investigated and resolved, customer protected from fraudulent charges

**Dispute Resolution Timeline:**
- Fraud cases: Provisional credit within 5 days, final resolution within 30 days
- Merchant disputes: Resolution within 60-90 days (per card network rules)
- ATM disputes: Resolution within 10 business days

---

## Sub-Journey 6.6: Account Security Assistance

### User Flow JY-6.6: Report Compromised Account or Lost/Stolen Card

**Entry Point:** User suspects account compromise or loses card

**Flow Steps:**

1. **Quick Security Actions (Self-Service)**
   - **Lost/Stolen Card:**
     - User: Taps "Cards" → Selects affected card
     - User: Taps "Freeze Card" button (instant action)
     - System: Immediately freezes card (no further transactions authorized)
     - System: Displays "Card frozen. Report as lost/stolen?"
     - User: Taps "Report Lost/Stolen"
   - **Or via Phone Support:**
     - User: Calls 24/7 support line
     - System (IVR): "To block your card immediately, press 3"
     - User: Presses 3
     - System: Freezes card and confirms via IVR

2. **Report Lost/Stolen Card**
   - System: Displays "Report Card" form:
     - **Card Status:** Lost | Stolen | Damaged
     - **When did this happen?** (date/time picker)
     - **Last known location:** (text field)
     - **Did you notice any unauthorized transactions?** Yes/No
   - User: Fills in details
   - User: Taps "Submit Report"
   - System: Marks card as permanently blocked
   - System: Sends confirmation "Your [Card Type] ending in [XXXX] has been blocked and cannot be used"

3. **Review Recent Transactions**
   - System: Displays last 10 transactions on the card
   - System: Asks "Please review and mark any unauthorized transactions"
   - User: Reviews list
   - User: Checkmarks any unauthorized transactions
   - User: Taps "These transactions are unauthorized"
   - System: Automatically creates disputes for selected transactions
   - System: Applies provisional credit for unauthorized transactions (see Sub-Journey 6.5)

4. **Replacement Card Issuance**
   - System: Offers "Would you like a replacement card?"
     - "Virtual card: Available now (instant)"
     - "Physical card: Delivered in 3-5 business days to your registered address"
   - User: Selects virtual and/or physical replacement
   - **Virtual Card:**
     - System: Issues new virtual card instantly with new 16-digit number
     - System: Displays new card details
     - System: Prompts "Add to Apple/Google Pay?"
   - **Physical Card:**
     - System: Confirms delivery address
     - User: Confirms or updates address
     - System: Orders physical card (courier delivery)
     - System: Provides tracking number

5. **Account Compromise (Broader Security Issue)**
   - **If user suspects account breach beyond card:**
     - User: Taps "Help" → "Security Concern" → "My account may be compromised"
     - System: Immediately triggers security protocol:
       - All cards frozen
       - All devices logged out except current device
       - Transaction limits set to zero
       - Email/SMS sent: "Security alert: Your account is under security review"
     - System: Transfers to fraud specialist immediately
     - Fraud Specialist: Conducts security interview:
       - "When did you notice the issue?"
       - "Have you shared your PIN or password?"
       - "Have you received suspicious calls or emails?"
       - "Which transactions appear unauthorized?"
     - Specialist: Reviews account activity for fraud indicators
     - Specialist: Determines action plan:
       - Reset all login credentials
       - Issue new cards
       - Dispute unauthorized transactions
       - Set up enhanced monitoring

6. **Post-Incident Security Measures**
   - System: Forces password/PIN reset
   - System: Sends security alert to registered email and phone
   - System: Enhances monitoring on account for 30 days (flag suspicious activity)
   - System: Sends follow-up email with security tips:
     - "Never share your PIN or OTP"
     - "Enable biometric login"
     - "Review transactions regularly"
     - "Beware of phishing attempts"
   - System: Offers optional consultation with security specialist

**Success Outcome:** Account secured, unauthorized access blocked, customer protected

**Security Response Times:**
- Card freeze: Instant (within seconds)
- Fraud specialist response: <10 minutes (24/7 availability)
- Account lockdown: <2 minutes
- Replacement virtual card: Instant
- Replacement physical card: 3-5 business days

---

## Journey 6 Success Metrics

**Target Metrics:**
- Self-service resolution rate: 60%+ (FAQ/chatbot)
- Live chat first response time: <2 minutes
- Live chat resolution time: <5 minutes (simple), <15 minutes (complex)
- Phone support answer time: <3 minutes (average)
- First call resolution: 80%+
- Complaint resolution within SLA (5 days): 95%+
- Dispute resolution within 30 days (fraud): 100%
- Dispute resolution within 90 days (merchant): 95%+
- Card block time (emergency): <30 seconds
- Customer satisfaction (CSAT): 4.5★+ across all channels
- Net Promoter Score (NPS) for service: 70+

---

## JOURNEY SUMMARY & METRICS DASHBOARD

### Cross-Journey KPIs

**Account Opening → Onboarding:**
- Application-to-active-account conversion: 85%+
- Time to first transaction: <24 hours for 60% of customers

**Login & Authentication:**
- Login success rate (first attempt): 95%+
- Authentication friction score: <2 (on 1-5 scale, lower is better)

**Account Management:**
- Monthly active users engaging with account management: 80%+
- Support tickets for account changes: <5% of customers

**Deposits:**
- First deposit within 7 days of account opening: 80%+
- Average deposits per customer per month: 3-5

**Servicing:**
- Customer effort score (CES): <2 (on 1-5 scale, lower is better)
- Support ticket deflection via self-service: 60%+

---

**End of User Flow Mapping Document**

---

## APPENDIX: Journey Mapping Conventions

**Entry Point:** Where the user begins the journey (specific UI location or trigger)

**Flow Steps:** Numbered sequential steps with user actions and system responses

**Decision Points:** Conditional logic where flow branches based on outcomes

**Success Outcome:** What constitutes successful completion of the journey

**Exit Points:** Ways the user can leave the journey (intentional or error states)

**Edge Cases:** Unusual scenarios or error conditions that must be handled

**Accessibility Considerations:** Special accommodations for users with disabilities

**Security Measures:** Authentication, authorization, and fraud prevention steps

**SLA Targets:** Service level agreements and performance metrics

---

**Document prepared by:** Product Manager Multi-Agent Framework v1.0.0  
**Date:** May 28, 2026  
**Updated:** Per client core journey requirements  
**Status:** ✅ Complete - All 6 core journeys with 30+ sub-journeys mapped
