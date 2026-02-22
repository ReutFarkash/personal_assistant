# Gemini Assistant Project

## 🎯 Vision
A personalized AI assistant using an Obsidian vault for persistent memory, data storage, and task management.

## 🏗️ Architecture
- **Memory Store:** Obsidian vault at `/Users/reut/Code/assistent/assistent/`
- **Skill Engine:** Gemini CLI with custom skills from `/Users/reut/Code/coffeeproject/skills/`
- **Shared Settings:** `/Users/reut/Code/_shared-gemini/`
- **Meta/Planning:** `/Users/reut/Code/assistent/assistent/meta/` (Development-only)

## 🔄 Development Workflow
Follow the **"Zooming" Workflow** from `coffeeproject`:
1.  **Zoom Out:** Update `meta/PLANNING.md` and `meta/PROJECT_TODO.md` with new ideas and tasks.
2.  **Zoom In:** Execute specific tasks using technical precision.
3.  **Validate:** Verify every change against `meta/ENGINEERING_STANDARDS.md`.

## 📜 Documentation
- **`meta/PROJECT_STATUS.md`**: Current state of the project.
- **`meta/PROJECT_TODO.md`**: Active and upcoming tasks.
- **`meta/PLANNING.md`**: The "Idea Dump" for brainstorming.
- **`meta/SESSION_FLIGHT_RECORDER.md`**: Turn-by-turn session tracking.
- **`meta/ENGINEERING_STANDARDS.md`**: Technical rules and patterns.

## 🛠️ Tools & Skills
- Use `coffeeproject` to create and package new skills.
- Use `project-maintainer` to help update status and todo files.
- Use `session-checkpoint` for session overviews.
