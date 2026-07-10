# Technology Stack

## Purpose

This document records the technologies selected for PC Diagnostic Assistant and the reasoning behind each decision.

Technology choices should support the project's goals of maintainability, readability, long-term support, and professional software engineering practices.

The stack has been intentionally selected to favour mature, well-supported technologies over newer alternatives where they provide a clear advantage for this Windows desktop application.

Technology decisions should be reviewed when project requirements change, but should not be changed without a clear technical justification.

---

# Core Platform

## Runtime

**.NET 10 (LTS)**

### Why?

* Current Long-Term Support (LTS) release.
* Stable foundation for a multi-year project.
* Modern C# language support.
* Excellent performance.
* Broad package compatibility.
* Industry-standard choice for new .NET desktop applications.

---

# User Interface

## Framework

**Windows Presentation Foundation (WPF)**

### Why?

* Native Windows desktop framework.
* Mature and well documented.
* Excellent support for data-heavy desktop applications.
* Strong integration with MVVM.
* Large community and extensive learning resources.
* Ideal for a Windows-specific diagnostic application.

Cross-platform frameworks were considered but rejected because the application's functionality depends heavily on Windows-specific APIs and diagnostic services.

---

# Application Pattern

## MVVM

**Model-View-ViewModel**

### Why?

* Clear separation between presentation and application behaviour.
* Encourages maintainable UI code.
* Highly testable.
* Well established within the WPF ecosystem.

---

## MVVM Toolkit

**CommunityToolkit.Mvvm**

### Why?

* Microsoft-supported.
* Removes repetitive MVVM boilerplate.
* Provides reliable implementations of observable properties and commands.
* Excellent support for asynchronous commands.
* Allows development effort to remain focused on diagnostic functionality rather than UI infrastructure.

The underlying MVVM concepts will still be learned and understood rather than treated as a black box.

---

# Dependency Injection

**Microsoft.Extensions.DependencyInjection**

### Why?

* Standard dependency injection container for modern .NET.
* Integrates naturally with logging and configuration.
* Supports constructor injection.
* Encourages loose coupling.
* Improves testability.

The application will use constructor injection and a single composition root during application startup.

---

# Configuration

**Microsoft.Extensions.Configuration**

### Why?

* Standard .NET configuration system.
* Supports strongly typed configuration.
* Easy integration with dependency injection.
* Appropriate for application-level configuration.

Application configuration and user preferences will remain separate concerns.

---

# Logging

## Logging Abstraction

**Microsoft.Extensions.Logging**

## Logging Provider

**Serilog**

### Why?

* Standard Microsoft logging abstraction.
* Structured logging support.
* Reliable rolling log files.
* Flexible output providers.
* Suitable for desktop applications.
* Keeps application code independent of a specific logging implementation.

Application logs are intended for diagnosing PC Diagnostic Assistant itself and are separate from exported diagnostic reports.

---

# Data Persistence

## Database

**SQLite**

### Why?

* Lightweight embedded database.
* No external database server required.
* Excellent support for searching, filtering, and historical investigations.
* Easy deployment.
* Reliable local storage.

SQLite was selected because investigations are a core feature of the application and require efficient querying and long-term storage.

---

## Object Relational Mapper (ORM)

**Entity Framework Core**

### Why?

* Industry-standard ORM for .NET.
* Strong integration with SQLite.
* Simplifies data access.
* Supports migrations.
* Improves maintainability.
* Valuable professional experience.

The persistence layer should remain an implementation detail behind application interfaces.

---

# Architectural Foundation

The project will follow a layered architecture consisting of:

* Presentation
* Application
* Domain
* Infrastructure

This structure separates user interface concerns from business logic and Windows-specific integrations.

The architecture is intentionally lightweight and inspired by Clean Architecture rather than implementing every possible architectural pattern.

---

# Testing

The project will include automated testing from the beginning.

The planned testing stack is:

* xUnit
* FluentAssertions
* Moq

These technologies support unit testing, expressive assertions, and test doubles while remaining common within the .NET ecosystem.

---

# Source Control

The project will be hosted publicly on GitHub.

Development practices include:

* Feature-focused commits.
* Meaningful commit messages.
* Documentation-first development where appropriate.
* Milestone-based implementation.
* Public issue tracking for major features and enhancements.

---

# Future Technology Decisions

The following technologies will be selected when their implementation milestone is reached:

* Windows diagnostic APIs.
* Hardware monitoring library.
* Report export formats.
* Installer and deployment strategy.
* Packaging format.
* Telemetry (if ever introduced).

These decisions have been intentionally deferred to avoid unnecessary complexity during the planning stage.

---

# Technology Selection Philosophy

The technologies used by PC Diagnostic Assistant have been chosen according to the following principles:

* Prefer mature, stable technologies over newer alternatives without a clear benefit.
* Avoid reinventing well-established infrastructure.
* Focus development effort on the application's diagnostic capabilities.
* Follow common practices within the modern .NET ecosystem.
* Prioritise maintainability, readability, and long-term support.

The project's innovation lies in its diagnostic workflow and reasoning engine rather than in the supporting technology stack. Supporting technologies should therefore minimise friction and allow development effort to remain focused on solving the core problem.
