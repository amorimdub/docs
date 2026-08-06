# Procedures

A CompanyOS Procedure is a Workspace-wide internal instruction record that tells an AI Client how to produce a repeatable output for Members using visible knowledge and the client's own tools.

For the full create → approve → publish → run journey, follow **[Your first Procedure](/first-procedure)**.

## Procedure Content

Procedure Content includes input guidance and output rules. It does not embed a tool script, execute actions, perform writes, or call tools on behalf of the AI Client.

## Required Inputs

A Procedure declares Required Inputs it must have before an AI Client may produce the output. The AI Client refuses to run the Procedure until every Required Input is satisfied. Input Source Hints tell the AI Client where the input might come from.

## Missing Requirements

A draft Procedure with a Missing Requirement cannot be published. Procedure Authoring Tools report Missing Requirements as AI-Actionable Errors, and the web UI shows the same gaps with repair guidance.

## Publishing

Only a Workspace Owner can publish a CompanyOS Procedure for the first time. Procedure Authoring Tools return an Approval Link so the Owner can review the draft in the web UI before that first publish. After publish, Owner edits can go live directly. Members can run published Procedures through their AI Clients.

## System Procedures

CompanyOS seeds protected System Procedures into every Workspace, such as Create a Procedure and Create a Template. Members and Owners cannot archive, delete, or edit System Procedures. Use Create a Procedure as the starting point for [your first Procedure](/first-procedure).
