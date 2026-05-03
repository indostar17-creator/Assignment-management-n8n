# GuruGuru: The Proactive LMS Assistant 🤖📚

Most Learning Management Systems (LMS) are passive—they wait for you to log in and check them. I was tired of missing deadlines hidden under overlapping assignments. So, I built GuruGuru: an automated system that brings the LMS to my Telegram via n8n, Gemini AI, Google Calendar, and Notion.

## 🛠️ How It Works (The Workflows)

This system is built on two primary workflows managed via n8n:

### 1. Assignment Management (The Main Hub)
A Telegram bot integrated with Gemini AI and Notion to handle day-to-day interactions.
*   **Save Assignment:** I send a screenshot of my LMS to the bot. Gemini analyzes the image, extracts the assignment name, course, and deadline, and automatically logs it into my Notion database.
*   **Deadline Tracker:** I can ask the bot for upcoming deadlines. It queries Notion and returns only tasks with the status "Not Started" or "In Progress."
*   **Status Updates:** I can update a task's status directly via chat (e.g., changing it from "In Progress" to "Done").

### 2. Assignment Auto-Sync (The Background Worker)
An automated pipeline linking the LMS to Notion.
*   It grabs the Moodle LMS calendar feed URL and syncs it with Google Calendar.
*   When a new assignment triggers an event in Google Calendar, it automatically creates a new page in the Notion database.
*   *(Note: This sync relies on the LMS feed refresh rate, which currently has a delay of 2-3 weeks. For urgent new tasks, I use the screenshot method in Workflow 1 as a quick fallback).*

## 📸 Interface Context (Translation Guide)
The bot interface is in Indonesian, as it's designed for my daily use. Here is what the screenshots are demonstrating:

*   **Image 1 (Adding via Screenshot):** I upload a screenshot of my LMS. I say, *"bro tolong isi jadwal matkul ini dong"* (bro, please input these course schedules). The bot correctly extracts the specific course names, task details, and exact deadlines from the image and saves them to Notion.
deadline.png

*   **Image 2 (Notion Database):** The central command. Columns include *Judul Tugas* (Task Name), *Mata Kuliah* (Course), and *Status*. The statuses are *Selesai* (Done), *Dikerjakan* (In Progress), and *Belum Selesai* (Not Started).
[DRAG DAN DROP FOTO DATABASE NOTION DI SINI]

*   **Image 3 (Deadline Checking):** I ask, *"tugas yang masih ongoing dengan deadline terdekat apa aja?"* (what are the nearest ongoing deadlines?). The bot filters out completed tasks and lists exactly what I need to focus on next.
[DRAG DAN DROP FOTO CEK DEADLINE DI SINI]

*   **Image 4 (Updating Status):** I tell the bot I finished specific tasks. The bot updates the Notion database status to *Selesai* (Done) and confirms the change in the chat.
[DRAG DAN DROP FOTO UPDATE STATUS DI SINI]

## 💻 Tech Stack
*   **n8n:** Workflow automation
*   **Telegram API:** Chat interface
*   **Google Gemini AI:** Image analysis & natural language processing
*   **Notion API:** Central database
*   **Google Calendar:** Trigger for auto-syncing LMS events
