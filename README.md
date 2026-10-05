# 🍔 QuickBite App - PRD Analysis & Test Design Portfolio

Welcome to the **QuickBite Test Case Design & PRD Analysis** repository! This project showcases my methodology for analyzing Product Requirement Documents (PRDs), identifying requirement gaps and ambiguities, and designing comprehensive end-to-end test suites **prior to code execution**.

> 📌 **Disclaimer:** The PRD (`QuickBite PRD.pdf`) used in this repository is a **demo/mock Product Requirement Document** created purely for portfolio, educational, and testing demonstration purposes.

## 📌 Table of Contents

* [Project Overview](#-project-overview)

* [Repository Structure](#-repository-structure)

* [Application Under Test (AUT)](#-application-under-test-aut)

* [PRD Analysis & Requirement Ambiguities Identified](#-prd-analysis--requirement-ambiguities-identified)

* [Test Case Design & Coverage](#-test-case-design--coverage)

* [Test Case Template Structure](#-test-case-template-structure)

* [Tools Used](#-tools-used)

* [How to Access the Artifacts](#-how-to-access-the-artifacts)

* [Author & Contact](#-author--contact)

## 🧠 Project Overview

In real-world software development, QA involvement begins long before code execution. This portfolio project demonstrates **Static Testing / Requirement Analysis** and proactive QA practices:

1. **Requirements Review:** Analyzing the sample PRD for clarity, edge cases, business rules, and non-functional requirements.

2. **Ambiguity Analysis:** Spotting contradictory thresholds, edge-case loopholes, and undefined system behaviors.

3. **Test Suite Authoring:** Designing structured test scenarios and manual test cases covering positive, negative, boundary, and edge-case behaviors.

## 📁 Repository Structure

```
├── QuickBite PRD.pdf                       # Demo Product Requirement Document
├── QuickBite Manual Testing Test Cases.xlsx # Complete Test Suite & Analysis Spreadsheet
└── README.md                               # Project documentation & overview

```

## 🌐 Application Under Test (AUT)

* **Application Name:** QuickBite (Food Ordering & Delivery App)

* **Target Platforms:** Mobile (iOS & Android)

* **Modules Covered:** Cart Management, Coupons & Discount Engine, Checkout & Delivery Fees, Payment Gateways (Card, UPI, Wallet, COD), Order Tracking, Cancellation/Refunds, and Post-Delivery Reviews.

* **Test Status:** **Unexecuted (Design Phase)** — Designed directly from the PRD requirements to ensure full coverage prior to deployment/execution.

## 🔍 PRD Analysis & Requirement Ambiguities Identified

During static analysis of `QuickBite PRD.pdf`, several ambiguous rules, conflicting thresholds, and edge cases were identified. These gaps were documented to show how QA provides value early in the STLC by raising inquiries before development begins:

| Feature Area | PRD Rule | Ambiguity / Edge Case Identified | QA Impact / Question | 
| ----- | ----- | ----- | ----- | 
| **Delivery Threshold** | `FR-12` (Min order = 100) vs `FR-13` (Free delivery > 99) | Conflicting phrasing on boundary value ($100$). | Is $100$ considered free delivery, or is delivery fee charged exactly at $99.01$? | 
| **Order Tracking** | `FR-20` (Status sequence) vs `FR-25` (Cancellation lockout) | "Preparing" state ambiguity relative to restaurant acceptance. | Can a user cancel for free if status is "Preparing" but restaurant hasn't explicitly clicked "Accept"? | 
| **Wallet + Payments** | `BR-3` & `FR-16` | Partial payments using QuickBite Wallet combined with other payment gateways. | Can a user split payment between Wallet + Cash on Delivery or Card? | 
| **Guest Checkout** | Scope mentions "Guest User can browse" | Behavior on clicking "Checkout" as a guest user. | Does the app enforce login at Cart creation or at the Checkout step? | 

## 🎯 Test Case Design & Coverage

The test suite in `QuickBite Manual Testing Test Cases.xlsx` covers both standard user flows and critical business logic edge cases:

```
                  ┌─────────────────────────────────────────┐
                  │     QuickBite Requirements Coverage     │
                  └────────────────────┬────────────────────┘
                                       │
      ┌────────────────┬───────────────┼───────────────┬────────────────┐
      ▼                ▼               ▼               ▼                ▼
Cart Management    Coupons &     Checkout & Fees    Payments &     Cancellation &
 (FR-1 - FR-5)    Discounts     (FR-12 - FR-15)    COD Rules         Refunds
               (FR-6 - FR-11)                     (FR-16 - FR-19)  (FR-23 - FR-26)

```

### Coverage Highlights:

* **Cart Logic:** Adding/modifying item quantities (1–10), max item limit (20 items), real-time total updates, cross-restaurant cart clearing dialogs.

* **Coupon Engine:** Minimum cart thresholds (`FLAT20` min $149$), automatic coupon removal on cart item deletion, first-time user restrictions (`WELCOME50`), server-side validation.

* **Checkout & Fees:** Boundary Value Analysis (BVA) on Minimum Order Value ($100$) and Free Delivery thresholds ($99$ vs $100$), tax/GST calculation accuracy ($5\%$).

* **Payment Restrictions:** Fraud control logic blocking Cash on Delivery (COD) for orders $> 2,000$, auto-refund triggers for deduction failures.

* **Cancellation Timers:** Free cancellation window ($\le 2$ minutes) vs post- acceptance lockout.

## 📝 Test Case Template Structure

Each test case designed in the Excel sheet follows a standard IEEE-aligned format:

* **Test Case ID:** Unique reference (e.g., `TC_CART_001`, `TC_CPN_005`, `TC_PAY_012`)

* **PRD Mapping:** Traced directly to requirement ID (e.g., `FR-3`, `FR-17`, `BR-2`)

* **Test Type:** Functional, Boundary Value Analysis (BVA), Equivalence Partitioning (EP), Negative Testing, Business Rule

* **Pre-conditions & Test Steps:** Clear execution instructions

* **Test Data:** Exact inputs and mock parameters

* **Expected Result:** Clear statement of expected system behavior based on PRD and resolved ambiguities

## 🛠 Tools Used

* **Requirement Analysis & Documentation:** PDF Reader, Mind Mapping

* **Test Design & Management:** Microsoft Excel / Google Sheets

* **Version Control:** Git, GitHub

## 📥 How to Access the Artifacts

1. **Clone the repository:**

   ```
   git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
   
   ```

2. **View PRD:** Open `QuickBite PRD.pdf` to review the original requirement document.

3. **View Test Cases:** Open `QuickBite Manual Testing Test Cases.xlsx` in Microsoft Excel, Google Sheets, or directly inside GitHub to review the test suite and requirement traceability matrix.

## 👤 Author & Contact

* **Name:** Md Mashrur Ahmed

* **LinkedIn:** https://www.linkedin.com/in/mashrur-ahmed/

* **Email:** mashrur789@gmail.com

*If you find this requirement analysis and test design portfolio helpful, feel free to give it a 🌟 star!*