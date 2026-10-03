# Endorse Platform: Manual QA Testing

Welcome! This repo is where we test the Endorse document signing platform (www.e-ndorse.online).

## Start here
1. Open the **[Issues tab](../../issues)** and read the pinned issue **"QA Tracker: Endorse Platform Manual Test Execution"**. It lists the environments, the test files and the full list of tests.
2. Get the **test URL** from the tracker. A developer will post it as a comment. If the tracker doesn't have one yet, ask a developer.
3. Download the **test files** the developer sends you (`sample_contract.pdf`, `nda_template.docx`, `large_video.mp4`, `corrupted.pdf`, `my_signature.png`).
4. Work through the test cases **in the order below**.

## What you need
- A modern browser (Chrome recommended) with DevTools (press `F12`).
- Your own real Google account and email address.
- A **second real email inbox** you can open, for the signer tests.
- For payment tests: use **only** the test cards written in the issues. Never enter a real card.

## Order to test in
Some tests depend on earlier ones, so follow this order:

| Step | Issues | What it covers |
|---|---|---|
| 1 | #2, #4, #3 | Sign up, protected routes, Google sign-in |
| 2 | #5, #6, #7 | Upload PDF, Word conversion, file validation |
| 3 | #8, #9, #10, #11 | Signature creation and field placement |
| 4 | #12, #13 | Signed PDF download and audit trail |
| 5 | #14, #15 | Signer invitation, then guest signing |
| 6 | #16, #17 | Create template, then send from template |
| 7 | #18, #19, #20 | Free-tier cap, Paystack, Stripe |
| 8 | #21, #22 | WhatsApp OTP and rate limit |
| 9 | #23 | Mobile layout and touch signing |
| 10 | #24 | Cross-browser check (do this last) |

## How to run a test
1. Open the test case issue and read the **Preconditions**.
2. Follow the **Test Steps** one by one and tick each box as you go.
3. Compare what you see with **Expected Result**.
4. Comment on the issue with the result (**Pass / Fail / Blocked**), your browser and version, your operating system, and the date.
5. **Pass:** close the issue and tick it in the tracker.
6. **Fail:** attach screenshots, a screen recording, and console or network logs, then create a new issue using the **Defect** template and link it to the test case.

## Severity guide
| Level | Meaning |
|---|---|
| S1 Blocker | App crashes, can't log in, payment failure, document corruption |
| S2 Critical | Signature misplaced in PDF, invites not sending, upload broken |
| S3 Major | Visual misalignment, mobile modal overlap, template variable issue |
| S4 Minor | Typo, small spacing issue, hover color glitch |

## Questions?
Comment on the tracker issue or contact the developer.
