# Product Vision

## Purpose

PC Diagnostic Assistant is a Windows desktop application designed to simplify and streamline the PC troubleshooting process by bringing together system information, diagnostic data, and guided investigations into a single application.

Rather than acting as another system information viewer, the application aims to reduce the manual effort involved in diagnosing hardware and software issues. It gathers evidence from multiple Windows diagnostic sources, interprets that evidence, and helps users work through structured investigations to identify likely causes.

The application does **not** attempt to repair problems automatically. Instead, it assists users in reaching well-informed conclusions while leaving all repair decisions in the hands of the user.

---

## Problem Statement

Diagnosing Windows PCs often requires switching between numerous built-in tools and third-party utilities, including Task Manager, Event Viewer, Device Manager, Resource Monitor, Settings, Command Prompt, and hardware monitoring software.

This fragmented workflow creates several challenges:

* Diagnostic information is scattered across multiple applications.
* Important evidence is easy to overlook.
* Users often lose track of what has already been investigated.
* Troubleshooting becomes increasingly difficult when multiple possible causes exist.
* Existing tools focus on presenting information rather than guiding the troubleshooting process.

PC Diagnostic Assistant aims to reduce this complexity by centralising evidence collection, organising investigations, and guiding users towards the most likely causes of an issue through structured, evidence-based workflows.

---

## Target Users

PC Diagnostic Assistant is intended for anyone who wants to troubleshoot Windows PCs more efficiently, including:

* Intermediate PC users.
* PC builders and enthusiasts.
* Computer Science and IT students.
* IT technicians and support engineers.
* Experienced users who already understand diagnostic workflows but want a more streamlined process.

The goal is not to replace technical knowledge, but to reduce the time, effort, and cognitive load required to apply it.

---

## Product Philosophy

The application is built around the following principles.

### Evidence before conclusions

Recommendations should always be supported by observable evidence collected from the system. The application should never make assumptions without supporting information.

### Confidence, not certainty

Computer diagnostics rarely produce absolute answers. Findings should communicate confidence levels while explaining why a particular hypothesis has been suggested.

### Guide, don't repair

The application assists users in identifying likely causes of issues but never performs repairs or makes irreversible changes to the operating system or hardware.

### Reduce cognitive load

The application should minimise context switching between Windows diagnostic tools by collecting, organising, and presenting relevant information in a single workflow.

### Transparency

Users should always be able to understand how a recommendation was reached by reviewing the findings, evidence, and hypotheses generated during an investigation.

---

## Project Boundaries

PC Diagnostic Assistant will:

* Collect diagnostic information from Windows and supported hardware.
* Organise investigations into structured diagnostic workflows.
* Present findings, supporting evidence, confidence levels, and recommendations.
* Allow users to record diagnostic progress and re-test after making changes.
* Export investigation reports for future reference or sharing.

PC Diagnostic Assistant will **not**:

* Perform automatic repairs.
* Execute repair commands on behalf of the user.
* Modify Windows configuration.
* Make irreversible system changes.
* Present hypotheses as confirmed facts.
* Encourage users to perform repairs beyond their level of confidence.

---

## Long-Term Vision

The long-term vision of PC Diagnostic Assistant is to become a practical troubleshooting companion for Windows users by reducing the friction involved in diagnosing hardware and software issues.

Rather than replacing technical expertise, the application aims to organise diagnostic thinking, reduce uncertainty, and provide users with a structured, transparent workflow that supports better troubleshooting decisions.
