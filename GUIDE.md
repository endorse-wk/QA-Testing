# Endorse QA Guide: Tester, Reviewer and QA Lead

This guide explains how the three roles work together on the Endorse manual QA run. Find your role below and follow it. For the tests themselves, see the [Issues tab](../../issues) and the pinned **QA Tracker**.

## How the roles fit together

| Role | Main job | Final say on |
|---|---|---|
| **Tester** | Runs the test cases and reports what happened | Nothing. Reports facts only |
| **Reviewer** | Checks the tester's work is correct and complete | Whether a result is accepted or sent back |
| **QA Lead** | Runs the process, triages defects, signs off | Severity, closing issues, final sign-off |

### The flow for every test case

1. **Tester** runs it, comments the result, and adds the label `ready-for-review`.
2. **Reviewer** checks it, then either adds `reviewed`, or adds `needs-info` and comments what is missing.
3. **QA Lead** closes the issue and ticks it in the tracker.

### Labels

| Label | Added by | Meaning |
|---|---|---|
| `ready-for-review` | Tester | Result recorded, waiting for a reviewer |
| `needs-info` | Reviewer | Something is missing, tester should fix it |
| `reviewed` | Reviewer | Checked and accepted |
| `defect` | Tester | A bug was found |
| `sev:S1-blocker`, `sev:S2-critical`, `sev:S3-major`, `sev:S4-minor` | QA Lead | Severity of a defect |

---

## Guide for Testers

**Your job:** follow the steps exactly, record what really happened, and report it clearly.

### Before you start
- Read the README and the pinned QA Tracker.
- Check that the test URL, your accounts and the test files are ready.
- Read the whole test case before clicking anything.

### While testing
1. Follow the steps in order and tick each box as you go.
2. Write what you actually saw in the "Actual Result" column, even when it matches what you expected.
3. Compare with the Expected Result line by line. If one line fails, the whole test fails.
4. Do not skip steps or fix things yourself. If a step is unclear, ask.

### When you finish a test case
Comment on the issue with:
- **Result:** Pass, Fail or Blocked
- **Environment:** which link, browser and version, device and OS
- **Date tested**
- **Evidence:** a screenshot or short screen recording, plus console and network logs when the steps ask for them

Then add the label `ready-for-review`.

### When a test fails
Create a new issue using the **Defect** template. A good defect report has:
- A short, specific title ("Signed PDF missing signature on page 2", not "PDF broken")
- Exact steps anyone could repeat
- What you expected, and what happened instead
- A screenshot or recording, and any error text from the console
- The test case it came from (`#number`)

If you are unsure how serious it is, suggest a severity and let the QA Lead decide.

### What "Blocked" means
You could not run the test because of something outside it (the site was down, or an earlier test failed). Say why in your comment.

### Do not
- Enter a real payment card. Use only the test cards in the issues.
- Share the test link, files or screenshots outside the team.
- Test anything that is not on the list, unless the QA Lead asks.
- Close issues. The reviewer and QA Lead do that.

---

## Guide for Reviewers

**Your job:** make sure every result can be trusted. You are checking the tester's work, not repeating all of it.

### For each issue labelled `ready-for-review`, check
- Every step is ticked and each has an actual result.
- The comment includes result, environment, browser, device and date.
- Evidence is attached, and it really shows what the tester says it shows.
- The Pass or Fail agrees with the Expected Result. A Pass with a missed check is a common mistake.
- For a failure, a defect issue exists, is linked, and is clear enough for a developer to act on.

### Reviewing a defect report
- Can you repeat it from the steps alone? If not, add `needs-info` and say what is missing.
- Is it a real bug, or a setup problem (wrong account, test mode off, expired tunnel link)?
- Is it a duplicate of an existing defect? If so, link it and note it.
- Suggest a severity (S1 to S4) in a comment. The QA Lead makes the final call.

### Spot-check by re-running
- Re-run at least one test from each module yourself.
- Always re-run any S1 or S2 failure.
- If your result differs from the tester's, comment with both results and tell the QA Lead.

### Your outcomes
- **Fine:** add `reviewed`.
- **Something is missing:** add `needs-info` and write exactly what to fix. Be specific and polite, for example: "Please attach a screenshot of the toast message from step 7."

### Do not
- Change the tester's result or edit their comment. If you disagree, say so in a comment.
- Close issues. That is the QA Lead's job.

---

## Guide for the QA Lead

**Your job:** keep testing moving, decide what counts as a pass or a defect, and sign off.

### Setup and kickoff
- Invite everyone to the repo, create the labels, pin the tracker and post the test URL.
- Assign each test case to a tester and each module to a reviewer, so no test is run twice.
- Run a short kickoff call: show the README, walk through one example test, and show how to write a defect.

### Daily (5 to 10 minutes)
- Scan the tracker for new comments, `needs-info` items and new defects.
- Make sure the test link and tunnel are still working.
- Unblock anyone who is stuck. Answer questions in the issue so everyone can see them.

### Triage defects
1. Confirm it is real and not a duplicate.
2. Set the severity label (S1 to S4) using the matrix below.
3. Assign it to a developer.
4. Add it to the tracker's **Defects Found** list.
5. When it is fixed, ask the tester to retest and fill in the Retest section.

| Severity | Description | Resolution SLA |
|---|---|---|
| S1 Blocker | App crash, payment failure, cannot log in, document corruption | Immediate (<4 hours) |
| S2 Critical | PDF flattener misplacement, invites failing, upload broken | <24 hours |
| S3 Major | Visual misalignment, mobile modal overlap, template variable issue | <3 days |
| S4 Minor | Typo, spacing, hover color glitch | Next sprint |

### Closing test cases
- Close an issue only when it has the `reviewed` label and the result is Pass.
- A failed test stays open until its defect is fixed and retested.
- Update the Results Summary table in the tracker at the end of each week.

### Resolve disagreements
- If a tester and reviewer disagree, look at the evidence and decide. Write your reasoning in a comment.
- If the Expected Result in a test case looks wrong or out of date, fix the issue text and tell everyone, since this can change other results.

### Escalate right away
- **An S1 defect** (crash, cannot log in, payment failure, document corruption): message the developer straight away rather than waiting for the daily check.
- **Real customer data seen, or a real card charged:** stop testing and tell the founder.

### Sign-off checklist
- [ ] All 23 test cases are closed
- [ ] All S1 and S2 defects are fixed and retested
- [ ] S3 and S4 defects are triaged, with remaining ones accepted or scheduled
- [ ] The tracker's Results Summary is complete
- [ ] Sign-off boxes in the tracker are ticked and a short summary comment is posted

---

## Quick start by role

| If you are... | Start here |
|---|---|
| A **Tester** | Read your section above, then open the QA Tracker and pick your first test case |
| A **Reviewer** | Read your section above, then filter issues by the `ready-for-review` label |
| The **QA Lead** | Create the labels, assign owners, post the test URL, then run the kickoff call |
