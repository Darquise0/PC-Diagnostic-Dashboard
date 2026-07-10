# Roadmap

## Purpose

This roadmap outlines the planned evolution of PC Diagnostic Assistant from an initial proof of concept into a practical Windows diagnostic assistant.

The roadmap is intended to communicate the project's direction rather than define every implementation detail. It should evolve alongside the project as requirements change, new ideas emerge, and lessons are learned during development.

Features may move between milestones where appropriate, but the overall philosophy of incremental, well-tested development should remain unchanged.

---

# Development Philosophy

Development will follow several guiding principles:

* Build vertically rather than horizontally.
* Complete one workflow before starting the next.
* Validate architectural decisions early.
* Deliver working software at the end of every milestone.
* Prefer small, well-tested improvements over large unfinished features.
* Avoid introducing complexity before it provides value.

The project should grow by extending a stable foundation rather than repeatedly restructuring unfinished systems.

---

# Phase 1 — Planning & Design

## Objective

Define the vision, architecture, and development strategy before implementation begins.

### Milestone 1 — Project Planning

**Status:** Complete

Deliverables:

* Public GitHub repository.
* README.
* Product Vision.
* Domain Model.
* Architecture.
* Design Principles.
* MVP Scope.
* Technology Stack.
* Roadmap.

Success Criteria:

* The project's goals, architecture, and technology choices are clearly documented.
* The implementation strategy is agreed before development begins.

---

# Phase 2 — Foundation

## Objective

Build the application's technical foundation while validating the architecture.

### Milestone 2 — Solution Foundation

Deliverables:

* Visual Studio solution.
* Project structure.
* Layered architecture.
* Dependency injection.
* MVVM infrastructure.
* Logging.
* Configuration.
* Initial navigation.
* Basic application shell.

Learning Goals:

* Solution structure.
* Dependency Injection.
* MVVM.
* Application startup.
* Logging.

Success Criteria:

* The application launches successfully.
* The architectural boundaries are established.
* Every project compiles and communicates correctly.

---

### Milestone 3 — First Vertical Slice

Deliverables:

* Quick Health Check.
* System Snapshot.
* First diagnostic check.
* Evidence generation.
* Finding generation.
* Hypothesis generation.
* Recommendation generation.
* Investigation creation.
* Investigation persistence.
* Basic results screen.

Learning Goals:

* End-to-end application flow.
* Async programming.
* Entity Framework Core.
* SQLite.
* Application workflows.

Success Criteria:

* A complete investigation can be created, saved, reopened, and viewed.

This milestone proves the overall architecture before expanding functionality.

---

# Phase 3 — Core Investigation System

## Objective

Transform the proof of concept into a usable diagnostic application.

### Milestone 4 — Investigation Management

Deliverables:

* Investigation list.
* Investigation history.
* User notes.
* Investigation status.
* Basic searching.
* Basic filtering.
* Improved persistence.

Success Criteria:

* Users can manage multiple investigations without losing diagnostic context.

---

### Milestone 5 — Expand Diagnostic Coverage

Deliverables:

* Additional storage diagnostics.
* Memory diagnostics.
* Event Viewer integration.
* System health observations.
* Improved recommendations.
* Confidence evaluation improvements.

Success Criteria:

* Multiple independent diagnostic checks contribute to investigations.

---

# Phase 4 — Guided Diagnostics

## Objective

Shift the application from collecting information to actively guiding investigations.

### Milestone 6 — Guided Investigation

Deliverables:

* Symptom selection.
* Investigation workflow.
* User test recording.
* Confidence updates.
* Re-evaluation after user feedback.

Success Criteria:

* Users can work through structured troubleshooting sessions rather than relying solely on scan results.

---

### Milestone 7 — Investigation Intelligence

Deliverables:

* Multiple hypotheses.
* Improved confidence calculations.
* Better recommendation prioritisation.
* Investigation progression.
* Investigation completion.
* Investigation exhaustion handling.

Success Criteria:

* Investigations evolve as evidence changes rather than remaining static reports.

---

# Phase 5 — Advanced Diagnostics

## Objective

Expand the application's diagnostic capabilities while preserving usability.

Potential additions include:

* Hardware temperatures.
* SMART and NVMe health.
* Driver analysis.
* Startup applications.
* Services.
* Running processes.
* Network diagnostics.
* Internet connectivity testing.
* Windows activation.
* Installed software.
* Hardware inventory.
* Additional diagnostic workflows.

The exact implementation order will be determined after the MVP has been validated.

---

# Phase 6 — Reporting & User Experience

## Objective

Improve usability and prepare the application for public release.

Potential additions include:

* Exportable reports.
* Improved visual design.
* Better navigation.
* Accessibility improvements.
* Search improvements.
* Performance optimisation.
* Additional settings.
* Documentation improvements.

Success Criteria:

* The application is suitable for everyday use by its target audience.

---

# Phase 7 — Version 1.0

## Objective

Prepare the first stable public release.

Deliverables include:

* Feature freeze.
* Bug fixing.
* Performance review.
* Documentation review.
* Testing across supported Windows versions.
* Installer creation.
* Release packaging.
* Public release.

Success Criteria:

* The application satisfies the MVP goals.
* Documentation is complete.
* The application is stable enough for general public use.

---

# Beyond Version 1.0

Future development may include:

* Additional guided diagnostic workflows.
* Expanded hardware support.
* Investigation comparison.
* Diagnostic trend analysis.
* Community-requested features.
* Improved reporting.
* Additional export formats.
* Further workflow automation that remains consistent with the project's design principles.

These features should be considered only after the core investigation workflow has matured.

---

# Measuring Progress

Progress should not be measured by lines of code or the number of completed features.

Instead, each milestone should deliver:

* A working application.
* A validated architectural improvement.
* A better user experience.
* Improved diagnostic capability.
* New learning opportunities.

The project succeeds by growing into a reliable diagnostic assistant through incremental, well-engineered improvements rather than attempting to deliver every planned feature immediately.
