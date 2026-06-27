# Gmail Compose Function - Manual Test Cases

> **Assessment:** Test the Compose function in Gmail to send an email with the body `"QA test for Incubyte"` and the subject `"Incubyte"`.
>
> **Author:** Senior Manual Test Engineer
> **Date:** 2026-06-26

---

## Table of Contents

1. [Overview](#overview)
2. [Deliverables](#deliverables)
3. [Workbook Structure](#workbook-structure)
4. [Test Case Summary](#test-case-summary)
5. [Coverage Areas](#coverage-areas)
6. [Priority Distribution](#priority-distribution)
7. [How to Use This Document](#how-to-use-this-document)
8. [Test Data Requirements](#test-data-requirements)
9. [Execution Guidelines](#execution-guidelines)
10. [Defect Reporting Template](#defect-reporting-template)
11. [Risk & Assumptions](#risk--assumptions)

---

## Overview

This document contains a comprehensive suite of **60 manual test cases** designed to validate the **Gmail Compose function**. The primary objective is to verify that a user can successfully compose and send an email with:

- **Subject:** `Incubyte`
- **Body:** `QA test for Incubyte`

The test suite covers functional, non-functional, security, and usability aspects of the compose feature using both **Traditional** and **BDD (Behavior-Driven Development)** test case formats.

---

## Deliverables

| # | Deliverable | Description | Status |
|---|-------------|-------------|--------|
| 1 | Traditional Style Test Cases | Step-by-step test cases with preconditions, steps, test data, and expected results | Included |
| 2 | BDD-Style Test Cases | Gherkin syntax (Given-When-Then) scenarios for stakeholder communication | Included |
| 3 | Positive Test Cases | Happy path scenarios verifying expected functionality | 30 cases |
| 4 | Negative Test Cases | Error handling, validation, security, and edge cases | 30 cases |
| 5 | Summary & Traceability | Coverage matrix, priority distribution, and execution notes | Included |

---

## Workbook Structure

The Excel file contains **5 sheets**:

| Sheet Name | Format | Type | Count | Purpose |
|------------|--------|------|-------|---------|
| `Traditional_Positive` | Traditional | Positive | 15 | Functional verification of compose feature working as expected |
| `Traditional_Negative` | Traditional | Negative | 15 | Error handling, validation, and security tests |
| `BDD_Positive` | BDD (Gherkin) | Positive | 15 | Behavior-driven tests for happy path scenarios |
| `BDD_Negative` | BDD (Gherkin) | Negative | 15 | Behavior-driven tests for error conditions and edge cases |
| `Summary` | Matrix | — | — | Traceability, coverage analysis, and execution guidelines |

### Color Coding

- **Green rows** — Positive test cases (expected to pass under normal conditions)
- **Red rows** — Negative test cases (expected to trigger error handling or validation)
- **Dark blue headers** — Column titles

---

## Test Case Summary

### Total Count: 60 Test Cases

```
Traditional Style
├── Positive: 15
└── Negative: 15

BDD Style
├── Positive: 15
└── Negative: 15
```

### Core Requirement Coverage

The specific requirement — **Subject: "Incubyte"** and **Body: "QA test for Incubyte"** — is directly validated across **multiple test cases** in all four sheets:

| TC ID | Sheet | Scenario |
|-------|-------|----------|
| TC_TP_002 | Traditional_Positive | Verify email can be composed with subject and body |
| TC_TP_005 | Traditional_Positive | Verify subject field accepts exact text "Incubyte" |
| TC_TP_006 | Traditional_Positive | Verify body field accepts exact text "QA test for Incubyte" |
| TC_BP_002 | BDD_Positive | Enter subject "Incubyte" in compose window |
| TC_BP_003 | BDD_Positive | Enter body "QA test for Incubyte" in compose window |
| TC_BP_004 | BDD_Positive | Send email with subject and body (end-to-end) |
| TC_TN_003 | Traditional_Negative | Verify email cannot be sent with empty subject |
| TC_TN_004 | Traditional_Negative | Verify email cannot be sent with empty body |
| TC_BN_003 | BDD_Negative | Warn when sending email with empty subject |
| TC_BN_004 | BDD_Negative | Warn when sending email with empty body |

---

## Coverage Areas

| # | Coverage Area | Traditional TCs | BDD TCs | Total | Description |
|---|---------------|-----------------|---------|-------|-------------|
| 1 | Basic Compose Functionality | 5 | 5 | 10 | Opening compose window, UI elements, keyboard shortcuts |
| 2 | Subject Field ("Incubyte") | 3 | 3 | 6 | Exact text entry, validation, character limits |
| 3 | Body Field ("QA test for Incubyte") | 3 | 3 | 6 | Exact text entry, formatting, content limits |
| 4 | Sending & Delivery | 3 | 3 | 6 | Send button, confirmation toast, delivery tracking |
| 5 | Draft & Auto-save | 1 | 1 | 2 | Closing without sending, draft recovery |
| 6 | Recipients & Addressing | 3 | 3 | 6 | Single/multiple recipients, CC, BCC, autocomplete |
| 7 | Formatting & Rich Text | 2 | 2 | 4 | Bold, italic, underline, hyperlinks |
| 8 | Attachments | 2 | 2 | 4 | Valid files, size limits (>25MB), blocked file types |
| 9 | Keyboard Shortcuts | 1 | 1 | 2 | 'C' key, Ctrl+Z (undo), Ctrl+Y (redo) |
| 10 | Scheduling | 1 | 1 | 2 | Future delivery, time zone handling |
| 11 | Security (XSS, SQL Injection) | 3 | 3 | 6 | Script sanitization, injection prevention, input sanitization |
| 12 | Error Handling & Validation | 3 | 3 | 6 | Empty fields, invalid formats, domain validation |
| 13 | Network/Performance Edge Cases | 3 | 3 | 6 | Offline mode, large content, recipient limits (500+) |

---

## Priority Distribution

| Priority | Count | Rationale |
|----------|-------|-----------|
| **High** | 16 | Core functionality, security, and critical validation tests |
| **Medium** | 24 | Important feature validation, usability, and integration tests |
| **Low** | 20 | Edge cases, performance boundaries, and nice-to-have features |

### High Priority Test Cases Include:
- Opening compose window (TC_TP_001, TC_BP_001)
- Entering exact subject "Incubyte" (TC_TP_005, TC_BP_002)
- Entering exact body "QA test for Incubyte" (TC_TP_006, TC_BP_003)
- Sending email end-to-end (TC_TP_003, TC_BP_004)
- XSS injection prevention (TC_TN_008, TC_TN_009, TC_BN_005, TC_BN_006)
- Invalid recipient validation (TC_TN_001, TC_TN_002, TC_BN_001, TC_BN_002)
- Blocked file type rejection (TC_TN_011, TC_BN_008)

---

## How to Use This Document

### For Manual Testers
1. Open the `Gmail_Compose_Test_Cases.xlsx` file
2. Start with **High** priority test cases in `Traditional_Positive` sheet
3. Execute each test case step-by-step
4. Mark execution status: **Pass / Fail / Blocked / Not Executed**
5. For failed cases, log defects using the template below
6. Move to `Traditional_Negative`, then BDD sheets

### For Automation Engineers
- BDD scenarios can be directly translated into Cucumber/Gherkin feature files
- Traditional test cases provide detailed step sequences for script development
- Security test cases (XSS, SQL Injection) can be automated using Selenium + security tools

### For Product Owners / Stakeholders
- Review `BDD_Positive` and `BDD_Negative` sheets for business-readable scenarios
- Use `Summary` sheet for high-level coverage overview
- Priority levels help in sprint planning and risk assessment

### For Regression Testing
- Run all **High** and **Medium** priority cases for every release
- Include **Low** priority cases for major releases or compose-related changes

---

## Test Data Requirements

### Accounts & Access
| Item | Requirement |
|------|-------------|
| Gmail Account | Valid Google account with Gmail access |
| Test Recipients | Minimum 3 valid email addresses for multi-recipient tests |
| Known Contacts | At least 1 contact in address book for autocomplete tests |

### Files for Attachment Tests
| File Name | Size | Type | Purpose |
|-----------|------|------|---------|
| `test_document.pdf` | < 25MB | PDF | Valid attachment test |
| `test_image.jpg` | < 25MB | JPG | Valid attachment test |
| `test_doc.docx` | < 25MB | DOCX | Valid attachment test |
| `large_video.mp4` | > 25MB | MP4 | Oversized attachment rejection |
| `malware.exe` | Any | EXE | Blocked file type test |
| `suspicious.zip` | Any | ZIP | Blocked file type test |

### Network Requirements
- Stable internet connection for positive tests
- Ability to disconnect/reconnect network for offline tests
- Browser: Chrome, Firefox, Safari, or Edge (latest versions)

---

## Execution Guidelines

### Pre-Execution Checklist
- [ ] Gmail account is active and accessible
- [ ] Browser cache is cleared (for clean state tests)
- [ ] Test recipient email addresses are verified and accessible
- [ ] Test files are prepared and accessible in local directory
- [ ] Network connectivity is confirmed

### During Execution
- [ ] Follow test steps exactly as documented
- [ ] Use exact test data provided (especially "Incubyte" and "QA test for Incubyte")
- [ ] Document actual results with screenshots for failures
- [ ] Note any deviations from expected behavior
- [ ] Record execution time for performance-sensitive tests

### Post-Execution
- [ ] Clean up sent emails from Sent folder (if applicable)
- [ ] Delete test drafts from Drafts folder
- [ ] Remove test contacts (if added during testing)
- [ ] Update execution status in the Excel tracker

### Environment Details to Record
```
Browser: _____________ (e.g., Chrome 126.0)
OS: __________________ (e.g., Windows 11 / macOS 14)
Screen Resolution: _____ (e.g., 1920x1080)
Gmail Version: _________ (e.g., Standard / HTML Basic)
Network: _____________ (e.g., Wi-Fi / Ethernet)
```

---

## Defect Reporting Template

When a test case fails, use this template to log defects:

```
Defect ID: [Auto-generated / BUG-001]
Title: [Brief description of the issue]
Severity: [Critical / High / Medium / Low]
Priority: [P1 / P2 / P3 / P4]

Related Test Case: [e.g., TC_TP_002]
Environment: [Browser, OS, Gmail version]

Steps to Reproduce:
1. [Step 1]
2. [Step 2]
3. [Step 3]

Expected Result:
[What should have happened]

Actual Result:
[What actually happened]

Evidence:
- Screenshot: [Attach screenshot]
- Video: [Attach screen recording if applicable]
- Console Logs: [Browser console errors if any]

Additional Notes:
[Any other relevant information]
```

---

## Risk & Assumptions

### Assumptions
1. Gmail web interface (mail.google.com) is the target platform
2. User has a valid, active Google account
3. Gmail is not in "HTML Basic" view (unless specifically tested)
4. Browser supports modern JavaScript and HTML5 features
5. No browser extensions interfere with Gmail functionality

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Gmail UI updates may invalidate locators/steps | High | Update test cases when UI changes are detected |
| Security tests may trigger account suspension | Medium | Use dedicated test accounts; avoid production accounts |
| Large file tests may consume significant bandwidth | Low | Use controlled network environment; schedule off-peak |
| Recipient limit tests require many email addresses | Low | Use distribution lists or programmatic generation |

---

## Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-06-26 | Senior Manual Test Engineer | Initial creation with 60 test cases |

---

## Contact

For questions or clarifications regarding these test cases, contact the Test Engineering team.

---

*End of Document*
