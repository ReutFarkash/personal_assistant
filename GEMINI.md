# Gemini Assistant Infrastructure (Core)

## 🎯 Vision
A reusable AI assistant engine for Obsidian vaults.

## 🏗️ Architecture (Hub & Spoke)
This project consists of three distinct repositories:
1.  **Infrastructure (This Repo):** Reusable logic and configuration.
2.  **Assistant Data (`assistant/`):** Private Obsidian vault (User data).
3.  **Dev Process (`meta/`):** Private session history and planning.

### 🔗 Directory Structure
- `/` (Infrastructure Root)
- `/assistant/` (Vault - Separately versioned)
- `/meta/` (Dev Process - Separately versioned, symlinked into vault)
- `/assistant/_utils/` (Core scripts and templates)
    - `_dataview_scripts/`: Specialized DataviewJS for unified content views.
    - `_templates/`: Core note templates (Journal, Atlas, Logs).

## 🛡️ Privacy & Access Mandates
**CRITICAL:** These rules must be strictly followed by the AI agent.

### 🚫 Forbidden Zone (`#off-limits` or `secret/`)
- The agent **MUST NOT** read, remember, or edit any file tagged with `#off-limits` or located in a `secret/` folder.
- If encountered, discard context immediately.

### 📖 Read-Only Zone (`#read-only`)
- The agent **MAY** read and use this data for context.
- The agent **MUST NOT** edit, delete, or modify these files.

### 🛠️ Dev Context (`meta/`)
- Files in `meta/` are for development tracking.
- The agent **MAY** read and edit these files to manage the project's evolution.

## 🔄 Development Workflow
Follow the **"Zooming" Workflow**:
1.  **Zoom Out:** Update `meta/PLANNING.md` and `meta/PROJECT_TODO.md`.
2.  **Zoom In:** Execute technical tasks.
3.  **Validate:** Ensure compliance with `ENGINEERING_STANDARDS.md`.

## 📜 Documentation
- **`meta/PROJECT_STATUS.md`**: Current state.
- **`meta/PROJECT_TODO.md`**: Tasks and ideas.
- **`meta/PLANNING.md`**: Idea dump.
- **`meta/SESSION_FLIGHT_RECORDER.md`**: Turn-by-turn log.
