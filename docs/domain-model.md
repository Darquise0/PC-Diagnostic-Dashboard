# Domain Model

## Purpose

This document defines the core concepts that make up the PC Diagnostic Assistant domain.

Rather than describing implementation details, it establishes a common vocabulary for the project. These concepts represent how the application understands the diagnostic process and should remain consistent regardless of how the software evolves.

The goal is to ensure that developers, contributors, and future maintainers share the same understanding of the application's terminology.

---

# Diagnostic Workflow

At a high level, every investigation follows the same process:

```text
Diagnostic Check
        ↓
     Evidence
        ↓
      Finding
        ↓
    Hypothesis
        ↓
  Recommendation
        ↓
     User Test
        ↓
 Re-evaluate Investigation
```

This workflow represents the core diagnostic pipeline used throughout the application.

---

# Core Concepts

## Investigation

An Investigation represents a complete diagnostic case.

It begins when a user starts investigating a problem, either through a guided investigation or as the result of a Quick Health Check or Full Diagnostic.

An Investigation manages the overall troubleshooting process and tracks its progress from start to finish.

An Investigation contains:

* The reported symptom or reason for the investigation.
* One or more hypotheses.
* Diagnostic history.
* User notes.
* System snapshots.
* Investigation status.
* Final outcome.

Only one problem should be investigated per Investigation.

---

## Hypothesis

A Hypothesis represents one possible explanation for the reported problem.

An Investigation may contain multiple hypotheses simultaneously.

Each hypothesis develops independently as new evidence is collected and user feedback is received.

A hypothesis contains:

* Findings.
* Supporting evidence.
* Diagnostic checks.
* Recommendations.
* Confidence level.
* Current status.

Hypotheses are never presented as confirmed facts. They represent the application's current understanding based on the available evidence.

---

## Diagnostic Check

A Diagnostic Check is an automated or manual action used to gather information.

Checks may:

* Read system information.
* Analyse Windows diagnostics.
* Ask the user to perform a manual test.
* Validate previous recommendations.

Examples include:

* Checking Event Viewer.
* Reading storage health.
* Measuring CPU usage.
* Asking whether moving an NVMe drive resolved an issue.

Diagnostic Checks do not produce conclusions. They collect information.

---

## Evidence

Evidence is the factual information collected by Diagnostic Checks.

Evidence should be objective and reproducible.

Examples include:

* Event ID 153 detected.
* SMART reports healthy.
* CPU temperature reached 95°C.
* Network packet loss measured at 8%.

Evidence should never contain interpretation.

---

## Finding

A Finding is a simplified description of evidence intended to make technical information easier to understand.

Examples include:

* Repeated storage warnings detected.
* High CPU temperatures detected.
* Frequent unexpected shutdowns detected.

Findings communicate what the application observed without suggesting a cause.

---

## Recommendation

A Recommendation suggests a safe next step based on the current hypothesis.

Recommendations should:

* Be evidence-based.
* Avoid irreversible actions.
* Encourage safe troubleshooting.
* Suggest official documentation or trusted resources where appropriate.

Recommendations assist the user but never perform repairs.

---

## System Snapshot

A System Snapshot represents the state of the system at a specific point in time.

Snapshots allow investigations to compare system state before and after testing or attempted repairs.

A snapshot may include:

* Operating system information.
* CPU.
* Memory.
* Storage.
* Network.
* Running processes.
* Recent system events.
* Hardware information.

Snapshots provide context for investigations but do not contain diagnostic conclusions.

---

# Supporting Concepts

## Confidence Level

Confidence represents how strongly the available evidence supports a hypothesis.

The MVP defines three confidence levels:

* Low
* Medium
* High

Confidence levels should change as additional evidence and user feedback are collected.

---

## Priority Level

Priority communicates the urgency of a finding or recommendation.

The MVP defines five priority levels:

* Critical
* High
* Medium
* Low
* Information

Priority helps users focus on the most important issues first.

---

## Investigation Status

An Investigation progresses through a series of states.

Possible states include:

* Created
* Scanning
* Analysing
* Awaiting User Action
* Re-testing
* Resolved
* Exhausted
* Archived

These states describe the progress of the investigation rather than the health of the system.

---

## Diagnostic Check Status

Each Diagnostic Check has its own lifecycle.

Possible states include:

* Pending
* Running
* Completed
* Failed
* Skipped
* Requires User Input

---

# Relationships

The following relationships describe how the core concepts interact.

* An Investigation contains one or more Hypotheses.
* A Hypothesis contains Findings.
* Findings are supported by one or more pieces of Evidence.
* Evidence is produced by Diagnostic Checks.
* Recommendations are generated from Hypotheses.
* System Snapshots provide context throughout an Investigation.
* User feedback may update confidence levels and influence the status of hypotheses.

---

# MVP Scope

The initial implementation will focus on the following domain concepts:

* Investigation
* Hypothesis
* Diagnostic Check
* Evidence
* Finding
* Recommendation
* System Snapshot

Additional concepts may be introduced as the diagnostic engine evolves. The domain model should grow incrementally alongside the application while maintaining clear responsibilities and consistent terminology.
