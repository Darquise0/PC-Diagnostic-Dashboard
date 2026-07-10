# Design Principles

## Purpose

This document defines the product and engineering principles that guide the development of PC Diagnostic Assistant.

These principles are intended to help maintain consistency as the application grows. They should be used when evaluating new features, designing diagnostic workflows, reviewing contributions, and resolving uncertainty during development.

The goal is not to prevent change. The goal is to ensure that changes continue to support the original purpose of the application.

---

# Core Product Principles

## Assist With Diagnosis, Do Not Perform Repairs

PC Diagnostic Assistant is a diagnostic tool, not an automated repair utility.

The application may:

* Collect diagnostic information.
* Identify unusual or concerning behaviour.
* Suggest possible causes.
* Recommend areas for further investigation.
* Record the results of user-performed tests.
* Direct users towards appropriate external resources.

The application must not:

* Automatically alter system configuration.
* Execute repair commands.
* Modify the registry.
* Install or remove drivers.
* Change firmware or BIOS settings.
* Perform destructive storage operations.
* Make physical hardware changes on behalf of the user.

Repair decisions and actions remain the responsibility of the user.

---

## Evidence Before Conclusions

Every diagnostic conclusion should be supported by observable evidence.

The application should clearly separate:

* What was checked.
* What data was collected.
* What was observed.
* What the application believes that observation may mean.

A hypothesis should never be created solely because a symptom is commonly associated with a particular issue.

For example, a black screen may be associated with graphics hardware, but the application should not automatically conclude that the GPU is faulty without supporting evidence.

---

## Confidence, Not Certainty

PC diagnostics frequently involve incomplete information, intermittent behaviour, hardware limitations, and several possible causes.

The application should use language such as:

* Possible.
* Likely.
* May indicate.
* Consistent with.
* Worth investigating.

It should avoid language such as:

* Definitely.
* Guaranteed.
* Proven.
* This component has failed.

Confidence levels should communicate the strength of the current evidence without implying mathematical certainty.

---

## Transparency Over Hidden Reasoning

Users should be able to understand why the application produced a finding or hypothesis.

Each diagnosis should expose:

* The relevant findings.
* The evidence supporting them.
* The checks that produced the evidence.
* The confidence level.
* Any important limitations or unavailable data.
* The reasons behind suggested next steps.

The application should not behave like an unexplained scoring system.

A technically experienced user should be able to inspect the evidence independently and form their own conclusion.

---

## Reduce Diagnostic Friction

The application should reduce the need to repeatedly move between separate diagnostic tools.

Where practical, it should centralise:

* System information.
* Event information.
* Hardware observations.
* Diagnostic notes.
* Test results.
* Investigation history.
* Recommendations.
* Exportable reports.

The goal is not to reproduce every Windows utility. The goal is to gather the information that is relevant to the current investigation and present it in a useful workflow.

---

## Preserve User Control

Users should remain in control of the investigation.

The application may propose checks and recommendations, but users should be able to:

* Skip a check.
* Mark a check as unavailable.
* Record their own result.
* Add notes.
* Disagree with a hypothesis.
* Re-run a check.
* End an investigation.
* Continue an investigation later.

The application should support the user’s judgement rather than attempt to replace it.

---

## Prioritise Safety

User safety, hardware safety, and data safety take priority over completing a diagnostic workflow.

Recommendations should include appropriate warnings when an action could involve:

* Data loss.
* Electrical risk.
* High temperatures.
* Opening a computer.
* Removing components.
* Changing firmware settings.
* Working with storage devices.
* Voiding a warranty.
* Interrupting important system processes.

Where appropriate, recommendations should advise users to:

* Back up important data.
* Shut down and disconnect power.
* Stop if they are uncertain.
* Consult official documentation.
* Seek assistance from a qualified technician.

A recommendation should not pressure the user into performing an action beyond their confidence or experience.

---

## Escalate Urgent Risks

Critical risks should take priority over unrelated informational findings.

Examples include:

* Unsafe component temperatures.
* Evidence of possible storage failure.
* Repeated signs of data corruption.
* Serious battery health concerns.
* Conditions that may cause immediate hardware damage.

A critical warning should remain visible even when it is not the most likely cause of the reported symptom.

For example, an available Windows update should not distract from a CPU running at an unsafe idle temperature.

---

## Treat Missing Data Honestly

Unavailable diagnostic information must not be interpreted as a healthy result.

A failed check may mean:

* The information is unsupported.
* The application lacks permission.
* The hardware does not expose the data.
* A dependency is unavailable.
* The check timed out.
* An unexpected error occurred.

The application should clearly distinguish between:

```text
No issue detected
```

and:

```text
The application could not complete this check
```

This distinction is essential for trustworthy diagnostics.

---

# Diagnostic Workflow Principles

## Begin With the User’s Problem

The primary guided workflow should begin with the question:

> What are you trying to solve?

The application should organise checks around the reported symptom rather than forcing the user to search through unrelated system information.

General system scans should also be available for users who:

* Do not know where to begin.
* Want a basic health check.
* Want a detailed system review.
* Want reassurance that no obvious issues were detected.

---

## Support Both Broad and Targeted Diagnostics

PC Diagnostic Assistant should support three main entry points.

### Quick Health Check

A lightweight scan of common and important system health indicators.

Its purpose is to identify obvious concerns without requiring a reported symptom.

### Full Diagnostic

A broader scan that gathers as much supported information as practical and produces a detailed report.

It may identify issues that require dedicated investigations.

### Guided Investigation

A symptom-focused workflow that selects relevant checks, creates hypotheses, records user feedback, and guides the user through repeated testing.

These modes should share diagnostic components rather than becoming three independent systems.

---

## Keep Investigations Focused

An Investigation should represent one primary problem or symptom.

Examples include:

* Random crashes.
* Loss of display output.
* Slow startup.
* Network disconnections.
* Storage performance problems.

An Investigation may contain several hypotheses, but they should all relate to the same reported problem.

This prevents reports and checklists from becoming overwhelming or unrelated.

---

## Treat Hypotheses as Working Theories

A Hypothesis is a possible explanation, not a confirmed diagnosis.

Each hypothesis should have:

* Supporting findings.
* Supporting or conflicting evidence.
* Relevant checks.
* A confidence level.
* Recommendations.
* A history of changes.

Hypotheses may be:

* Strengthened.
* Weakened.
* Ruled out.
* Reopened.
* Marked as resolved by the user.

The application should preserve previous hypotheses and their reasoning instead of deleting them when confidence changes.

---

## Use Testing to Reduce Uncertainty

The purpose of a suggested test is to gather new evidence.

A test result may:

* Support a hypothesis.
* Weaken a hypothesis.
* Rule out a hypothesis.
* Produce a new hypothesis.
* Reveal that the original symptom has changed.
* Leave the investigation unchanged.

Tests should not be included merely to make a checklist longer.

Every test should have a clear diagnostic purpose.

---

## Re-evaluate After User Feedback

User-provided test results should influence the investigation.

For example, the user may report:

* The issue was resolved.
* The issue remains unchanged.
* The issue became worse.
* The test could not be completed.
* The result was unclear.

The application should record this feedback and re-evaluate relevant hypotheses where possible.

It should not treat a user-entered result as infallible. User input is evidence, but it may be incomplete or uncertain.

---

## Avoid Endless Diagnostic Loops

The application should not repeatedly suggest the same failed action without new evidence.

When the available checks have been exhausted, it should say so clearly.

An exhausted investigation may recommend:

* Performing one final complete re-test.
* Reviewing the exported report.
* Researching suggested search phrases.
* Consulting official documentation.
* Seeking professional assistance.

The application should fail honestly rather than manufacture another recommendation.

---

## Preserve Investigation History

Diagnostic progress should not rely on memory.

The application should record:

* Checks performed.
* Evidence collected.
* Findings produced.
* Hypothesis changes.
* Recommendations shown.
* User actions.
* User test results.
* Re-test outcomes.
* Notes.
* Investigation status changes.

This history should allow users to continue an investigation later and explain what has already been attempted.

---

# Recommendation Principles

## Explain the Issue in Accessible Language

Recommendations should be understandable without hiding technical detail.

Where useful, a recommendation should include:

* A plain-language explanation.
* The relevant technical term.
* A suggested search phrase.
* The evidence that led to it.
* Any safety warning.
* An indication of when professional assistance may be appropriate.

This supports both less-experienced users and advanced users who want the exact diagnostic context.

---

## Recommend Areas of Investigation, Not Detailed Repairs

Recommendations should tell users what to investigate without becoming a repair manual.

For example:

```text
Consider investigating the storage connection, motherboard slot,
storage driver, or device firmware.
```

is appropriate.

A detailed sequence of commands or physical repair instructions may not be appropriate, especially where mistakes could cause damage or data loss.

Where external instructions are useful, the application should prefer official documentation or reputable resources.

---

## Provide Search-Friendly Language

When appropriate, the application should produce search terms based on the actual evidence.

For example:

```text
Windows Event ID 153 repeated disk reset NVMe
```

is more useful than:

```text
My computer keeps crashing
```

Search phrases should help users independently verify findings and locate current repair guidance.

They should not imply that a hypothesis has been confirmed.

---

## Avoid Unnecessary Alarm

Warnings should be proportional to the evidence and risk.

The application should not label ordinary behaviour as dangerous merely because a value is unusual.

Thresholds should consider context where possible, including:

* Idle versus load conditions.
* Component type.
* Duration.
* Repetition.
* Manufacturer guidance.
* Availability of supporting evidence.

Critical language should be reserved for conditions that genuinely warrant immediate attention.

---

# Engineering Principles

## Prefer Clear Code Over Clever Code

The project should favour straightforward, understandable implementations.

Complex abstractions should only be introduced when they solve a demonstrated problem.

Code should be understandable to contributors who were not involved in the original design discussions.

---

## Build Vertically and Incrementally

Features should be developed as small vertical slices that pass through the necessary layers.

For example, the first storage-capacity check should include:

* Data collection.
* Evidence creation.
* Finding generation.
* Display.
* Testing.
* Basic persistence where required.

This provides working value early and validates the architecture before more complex diagnostic capabilities are added.

---

## Avoid Premature Generalisation

The project should not create a universal diagnostic rule engine before several real diagnostic workflows have been implemented.

Reusable abstractions should emerge from repeated needs.

One working implementation should not automatically become a framework.

---

## Protect Architectural Boundaries

New features should preserve the responsibilities defined in the architecture document.

In particular:

* UI code should not collect diagnostic data.
* Infrastructure should not make unsupported diagnostic conclusions.
* Domain concepts should not depend on Windows APIs.
* Application workflows should not depend on WPF controls.
* Persistence details should not leak into diagnostic reasoning.

---

## Make Partial Failure a First-Class Outcome

A diagnostic scan may succeed partially.

One failed collector should not automatically invalidate all other results.

The application should preserve successful results while clearly reporting:

* What failed.
* Why it failed when known.
* Whether the check can be retried.
* How the missing information affects confidence.

This is especially important because hardware and Windows diagnostic sources are not consistently available.

---

## Test Reasoning More Heavily Than Wrappers

The highest-value tests are those that validate:

* Diagnostic rules.
* Investigation state changes.
* Confidence updates.
* Priority handling.
* Workflow decisions.
* Partial-failure behaviour.

Thin wrappers around Windows APIs may be better tested through integration tests and manual verification than through excessive mocking.

---

## Document Important Decisions

Significant technical decisions should be recorded using architecture documentation or Architectural Decision Records.

Examples include:

* Selecting WPF.
* Choosing the persistence technology.
* Selecting a hardware sensor library.
* Defining confidence levels.
* Requiring elevated permissions.

A future contributor should be able to understand why a decision was made, not only what the final decision was.

---

# Feature Evaluation Checklist

Before accepting a new feature, the project should ask:

1. Does this reduce friction in the diagnostic workflow?
2. Does it collect, organise, interpret, or preserve useful diagnostic information?
3. Is it safe?
4. Is it supported by evidence?
5. Does it preserve user control?
6. Does it fit the current milestone?
7. Can it be introduced without breaking architectural boundaries?
8. Does it add genuine value, or is it mainly visual or technically interesting?
9. Can the application explain the result transparently?
10. What should happen when the feature fails or is unsupported?

A useful feature may still be postponed if adding it at the current stage would disrupt the core workflow.

---

# Living Principles

These principles are expected to evolve as the application is developed and tested.

Changes should be made deliberately and documented.

When the implementation reveals that a principle is incomplete or impractical, the principle should be reviewed rather than silently ignored.

The purpose of this document is to guide development, not to prevent the project from learning.
