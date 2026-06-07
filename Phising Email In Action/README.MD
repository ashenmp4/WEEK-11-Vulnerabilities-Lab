# TryHackMe: Phishing Emails in Action - Walkthrough & Write-up

## 📌 Room Overview
* **Room Name:** Phishing Emails in Action
* **Difficulty:** Easy
* **Category:** Security Operations (SOC Level 1) / Phishing Analysis
* **Objective:** Learn to identify common indicators of phishing attempts, analysis techniques, social engineering tactics, and payload distribution mechanisms by inspecting real-world malicious email samples.

---

## 🔍 Task 1: Introduction
This room transitions core phishing theory into practical hands-on analysis using actual phishing, spam, and malicious email samples. 

### Key Objectives:
* Analyze raw email body structures and headers.
* Spot visual brand impersonation tactics.
* Detect tracking mechanisms (tracking pixels) and malicious attachment styles (.dot, macro-enabled .xls).

> ⚠️ **Warning:** The artifacts studied in this lab are derived from real phishing campaigns. Avoid interacting with active links or opening external files outside the secure sandbox environment.

*No questions are required for this task.*



---

## 💳 Task 2: Cancel Your PayPal Order
This sample models a classic transaction-based scare tactic attempting to trick the victim into reacting out of panic regarding a fake checkout or purchase order.

### 🛠️ Phishing Techniques Observed
* **Spoofed From Address:** The visual display name mimics a trusted brand (`service@paypal.com`), but the actual underlying sender address belongs to an unrelated, potentially compromised domain.
* **URL Shortening:** The attacker uses URL shorteners to obscure the destination landing page, preventing standard users from verifying the final link destination via standard hovering.
* **Branded HTML:** Copies look-alike corporate styling, transactional banners, and legitimate logos to foster an environment of trust.

### ❓ Questions & Answers
#### 1. What phrase does the gibberish sender email start with?
* **Answer:** `noreply`
* **Analysis:** When evaluating the raw `From:` header metadata, the address string presents a structure similar to `noreply[gibberish]@sultanbogor.com`, utilizing an automated system moniker to blend in.

---

## 📦 Task 3: Track Your Package
Attackers routinely exploit the high volume of global logistics deliveries by sending look-alike distribution and parcel tracking notifications.

### 🛠️ Phishing Techniques Observed
* **Display Name Impersonation:** Sets the outer mailbox name to `Distribution Center` or `DHL Tracking` while using an external rogue sender string like `contact@beginpro.club`.
* **Pixel Tracking:** Embeds a microscopic or transparent image element ($1 \times 1$ pixel GIF). When the client parses the HTML and pulls the source from the remote attacker-controlled infrastructure, the attacker logs that the message was opened along with the victim’s IP address.
* **Link Manipulation:** Employs hyperlink anchoring where the text explicitly displays a valid tracking string, but the underlying destination path points somewhere else entirely.

### ❓ Questions & Answers
#### 1. What is the root domain for each URL? Defang the URL.
* **Answer:** `devret[.]xyz`
* **Analysis:** Inspecting the underlying hyperlinked redirect chain reveals that the fake tracking buttons route traffic out to the root domain infrastructure managed by the adversary (`devret.xyz`). 

---

## 📄 Task 4: Select Your Email Provider to View Document
This scenario evaluates a multi-stage corporate credential harvesting strategy mimicking an automated document portal alert.

### 🛠️ Phishing Techniques Observed
* **Document Expiration Urgency:** Imposes a strict time constraint (e.g., "Link expires today") to suppress critical thinking.
* **Multi-Brand Impersonation:** Combines recognized cloud environments (OneDrive, Adobe Sign, SharePoint) within the same template flow to validate why a login prompt is occurring.
* **Credential Harvesting Portal:** The interface does not authenticating accounts; it maps the text form fields directly to backend collection scripts.

### ❓ Questions & Answers
#### 1. This email sample used the names of a few major companies, their products, and logos such as OneDrive and Adobe. What other company name was used in this phishing email?
* **Answer:** `Citrix`
* **Analysis:** Reviewing the explicit text fields, brand layouts, or interface signatures (such as the document portal header title) reveals references to Citrix ShareFile technologies mixed into the lure.

---

## 🍿 Task 5: Please Update Your Payment Details
A consumer-focused phishing methodology targeting streaming subscriptions, designed to cause instant friction via account suspension warnings.

### 🛠️ Phishing Techniques Observed
* **Urgency & Account Restrictions:** Relies entirely on the threat of immediate service termination.
* **External Forms/PDF Lures:** Instead of direct links inside the text body, this strategy embeds structural call-to-actions within an attached document template, minimizing detection rules triggered by typical text link crawlers.

### ❓ Questions & Answers
#### 1. What should users do if they receive a suspicious email or text message claiming to be from Netflix?
* **Answer:** `forward the message to phishing@netflix.com`
* **Analysis:** Official organizations maintain specialized intake reporting boxes to aggregate threat telemetry and coordinate active takedowns of fraudulent portals.

---

## 🍏 Task 6: Your Recent Purchase
This attack sample presents a counterfeit electronic invoice or store receipt layout targeting Apple customers, leveraging large dollar amounts to trigger an immediate dispute reaction.

### 🛠️ Phishing Techniques Observed
* **BCC (Blind Carbon Copy) Distribution:** The primary threat actor drops victim addresses into the hidden distribution field. The target only sees their address in isolation or structured look-alike labels, hiding the fact that it's an automated mass-spam campaign.
* **Atypical Templates:** Delivers the payload via unusual file types like `.dot` (Microsoft Word Document Template) instead of conventional standard extensions.

### ❓ Questions & Answers
#### 1. What does BCC mean?
* **Answer:** `Blind Carbon Copy`

#### 2. What technique was used to persuade the victim to not ignore the email and act swiftly?
* **Answer:** `Urgency`
* **Analysis:** The invoice frames a substantial transaction that demands immediate cancellation if unauthorized, weaponizing psychological panic.

---

## 🚛 Task 7: DHL Express Courier Shipping Notice
This vector represents a highly technical corporate malware dropper flow masquerading as automated shipping manifests or inventory schedules.

### 🛠️ Phishing Techniques Observed
* **Macro-Enabled Droppers:** The email features an attached spreadsheet workbook. The visual layer employs social engineering text prompting users to bypass built-in security protections by clicking "Enable Content" or "Enable Editing."
* **Malicious Execution Chain:** Activating macros fires embedded VBA scripts, leveraging tools like PowerShell or CMD to reach out to remote staging systems and download secondary stage binaries.

### ❓ Questions & Answers
#### 1. What is the name of the executable that the Excel attachment attempts to run?
* **Answer:** `regasms.exe`
* **Analysis:** Looking into the macro parameters or analyzing the process execution alerts reveals that the document attempts to fetch and execute a remote access payload disguised as `regasms.exe`.

---

## 🏁 Task 8: Conclusion
Defending environments against active phishing relies heavily on proactive technical visibility and user indicators:
* Mismatched header parameters (`From:` vs `Reply-To:` vs `Return-Path`).
* Misaligned domains and missing authentication controls (SPF, DKIM, DMARC failures).
* Suspicious or uncommon attachments (.xlsm, .dot, double-extensions).

---
🏁 *Great job completing the Phishing Emails in Action lab! Keep analyzing, stay vigilant, and clear those alerts!*
