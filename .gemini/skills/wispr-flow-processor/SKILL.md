---
name: wispr-flow-processor
description: Standardizes the ingestion of raw Wispr Flow monologues. Use when the user provides a raw text dump or transcript that needs to be archived, triaged, and distributed across the Obsidian vault.
---

# Wispr Flow Processor

## 1. Overview
The `wispr-flow-processor` automates the transformation of raw, unstructured transcripts (Wispr Flow) into structured, interlinked notes. It follows a strict "Append -> Triage -> Distribute" pipeline to maintain vault integrity and ensure no context is lost.

## 2. Global Architecture (DRY)
This skill adheres to the centralized vault structure and standards. Before processing, the agent SHOULD reference the following local files for the current project's schema:
- **Vault Schema & Standards**: `/Users/reut/Code/assistant/GEMINI.md` and `/Users/reut/Code/assistant/meta/ENGINEERING_STANDARDS.md`.
- **System Architecture**: `/Users/reut/Code/assistant/meta/SYSTEM_ARCHITECTURE_v1.md`.
- **Core Templates**: `/Users/reut/Code/assistant/data_vault/_utils/_templates/`.

## 3. Workflow: The Ingestion Loop

### Step 1: Append Verbatim (Archive)
1.  **Target**: Locate the daily raw log at `assistant/data_vault/04/YYYY-MM-DD_raw_stream_log.md`. (Create it if missing).
2.  **Action**: Append the raw transcript under a header: `## 📅 YYYY-MM-DD HH:MM (Context)`. 
3.  **Format**: Wrap the input in a `> [!QUOTE] Raw Input` callout to distinguish it from structured notes.

### Step 2: Entity Extraction & Triage
Analyze the raw input for the following entities and perform the corresponding updates:

- **Personnel (05)**:
  - **Context**: Mention of names, family, friends, or coworkers.
  - **Action**: Check `assistant/data_vault/05/Personnel/`. If a note exists, update its "Recent Interactions" section. If not, create a new profile note.
- **Atlas (03)**:
  - **Context**: Mention of specific projects, areas of interest, or long-term goals.
  - **Action**: Update or create project notes in `assistant/data_vault/03/` using the `03_Atlas_Project_Area.md` template.
- **Journal (04)**:
  - **Context**: Specific events, locations, or time-bound reflections.
  - **Action**: Update the primary daily note `assistant/data_vault/04/YYYY-MM-DD.md` (e.g., "Where was I today?", "Who did I meet?").
- **Logs (06)**:
  - **Context**: Decisions, communications, or formal meetings.
  - **Action**: Extract to a standalone note in `assistant/data_vault/06/` using the `06_Logs_Comms_Decision.md` template.

### Step 3: Task Distribution
Extract actionable items and distribute them based on scope:
- **Work/Project Tasks**: Add to `assistant/meta/PROJECT_TODO.md`.
- **Personal/Chore Tasks**: Add to the `## 🎯 Tasks for Today` section of the daily journal (`04/YYYY-MM-DD.md`).

## 4. Extraction Rules & Style
- **Linking**: Always use double brackets `[[Entity Name]]` for extracted names and projects.
- **Provenance**: When summarizing, include a breadcrumb back to the raw log source.
- **Standard Format**: Standalone logs MUST follow the `YYYY-MM-DD_HHMMSS-description.md` naming convention.
- **Style**: Maintain a neutral, senior-software-engineer tone while capturing the user's intent accurately.
