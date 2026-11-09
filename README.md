# Offer Track

A private job search tracker that runs inside [Claude](https://claude.ai) as an artifact. It keeps every target company, application, tailored resume, cover letter and conversation in one place, and has Claude built in to help at each step: finding leads, tailoring documents, drafting outreach, prepping for interviews and following up.

Use it two ways: on the web at **https://gitcich.github.io/offer-track/**, or inside Claude. Each person gets their own copy with their own data. The app file in this repo contains no personal information.

---

## Features

### Dashboard
- Greeting with today's date and count of active opportunities
- Key numbers: active pipeline, applications in the last 30 days, response rate, interviews, offers
- **Next actions** list with due dates, flagged when due today or overdue
- **Needs follow-up** list of applications that have gone quiet for over a week
- Pipeline funnel showing how many jobs reached each stage
- Applications-per-week chart (last 8 weeks)
- Fresh leads panel and recent activity feed
- **Plan my day** button: Claude reviews the whole pipeline and names the three most important things to do today
- Lead scan status bar with next and last run, a **Run now** button and a link to the scheduled task

### Kanban board
- Stages: Target → Applied → Screening → Interviewing → Offer → Closed (with outcome)
- Drag and drop between stages; moving to Applied records the date and sets the first follow-up step
- Cards show priority, next-step due date, whether a resume and cover letter exist, checklist progress and how many messages are logged

### All jobs list
- Searchable, filterable table of every job with stage, applied date, next step, last activity and document status

### Lead queue (hidden job market)
- Leads from three sources:
  - **Web scan** (optional scheduled task): recent funding, newly appointed leaders, new partner or expansion programs, and open roles matching your targets
  - **Gmail scan**: reads recent job alerts and recruiter emails and pulls out roles that fit
  - **Your other Claude chats**: imports target companies you've discussed elsewhere, when memory is available
- Each lead has a fit score (0–100), the signal and its date, why it fits, a suggested angle and a source link
- **Add to board**, **Draft outreach** (LinkedIn note plus email) or **Dismiss**
- Tiles or list view, with sorting by fit, newest signal, recently added, company or signal type

### Job detail
- **Overview**: details, contact, job description, notes, next step with due date, and a "Suggest next step" button
- **Post-application checklist** (default "Beyond the application"):
  - DM the hiring manager
  - Multithread leadership
  - Show speed and follow-through

  Each step has notes, a done tick and a Claude button that drafts the message. The steps are fully editable.
- **Resume tab**
  - **Tailor with Claude** from your base resume and the job description, keeping every fact truthful
  - **Drag and drop a resume** (PDF, Word or text) to optimize it for the job, or save it as your new base resume
  - **Fit check**: score, strengths, gaps and missing keywords
  - Restore previous version, copy, and .docx or .txt download
- **Cover letter tab**: Claude drafts a letter in your chosen tone and instructions, with the same editing and export tools
- **Communications tab**
  - Pull matching Gmail threads into the job's history
  - Log calls, notes and meetings
  - Import a phone call log CSV, matched to the contact's number
  - Claude summarizes the history or drafts a reply to any email

### Review and PDF export
- Full-page preview before download, plus **Proofread with Claude** that lists typos and slips without rewriting
- A "ready to send" check before the PDF unlocks; the job remembers when it was reviewed and flags later edits
- Three PDF styles:
  - **Classic**: clean single-column US Letter
  - **Navy & blue**: two-tone A4 design with contact icons, two-column job headers (title and company left; location and dates right) and dashed dividers
  - **AI-optimized**: Claude picks the font, colors, margins, heading style, section order, competency columns and page limit using resume best practice. It stays readable by applicant tracking systems, enforces readable color contrast and shrinks text to fit the page limit.
- Core competencies in 2 or 3 columns, each item kept on one line
- Cover letters share the same header and style as the resume

### Claude assistant
- Side panel that knows the job you're viewing (description, resume, letter, history, checklist) or your whole pipeline
- Stage-aware suggestions: research angles, recruiter-screen prep, mock interviews, thank-you notes, offer negotiation
- With your OK it can set next steps, move stages, add notes and save drafts
- Save any answer as a note or as the cover letter

### Multiple profiles
- Profile switcher at the top of every page; each profile has its own jobs, leads, resume, settings, checklist and Claude chats
- Create a profile from scratch or start from a copy of the current profile's resume and settings
- Use one per person (share one tracker with family or job-club members) or one per search track
- Each profile can have its own scheduled lead scan

### Profile and settings
- Name, title, contact details, location, headline and target roles
- Base resume used for every tailored version
- Lead scan focus: the industries, company types and hiring signals to watch
- Editable post-application checklist (name, intro, steps, button labels and Claude prompts)

---

## Use it on the web (no Claude account needed)

**Open: https://gitcich.github.io/offer-track/**

- Works in any modern browser. Your data is saved in that browser only; use **Profile → Backup** to export and import.
- **Bring the AI of your choice.** On the **Profile** page, pick a provider and paste your API key to turn on the AI features (tailoring, cover letters, coach, fit check, proofreading, AI PDF layout, web lead scan):
  - **Anthropic** (Claude)
  - **OpenAI** (GPT models)
  - **Google Gemini**
  - **OpenRouter** (hundreds of models from one key)
  - **Custom OpenAI-compatible endpoint**, such as Ollama or LM Studio on your own computer, Groq or Together

  You can set the main and quick model names. Usage is billed by your provider. Your key stays in your browser and is sent only to the provider you choose.
- Gmail import and the scheduled morning scan are only available in the Claude version below. The web version has a **Scan web for leads** button instead, which uses your provider's web search (Anthropic, OpenAI, Gemini and OpenRouter; not custom endpoints).

## Requirements (Claude version)
- A Claude account (claude.ai or the Claude desktop app)
- Optional: the **Gmail** connector, for email import and the Gmail lead scan
- Optional: scheduled tasks, for the automatic daily lead scan

Claude features in the app run on the viewer's own Claude usage, and the app asks permission the first time it uses Claude or Gmail.

---

## Install

### Option A: skill (recommended)
1. Download [`dist/offer-track-setup.zip`](dist/offer-track-setup.zip).
2. In Claude, open **Settings** and find **Skills** (under Capabilities on most plans), then upload the zip.
3. Start a new chat and say: **"Set up my job tracker"**.
4. Answer a few questions (name, target roles, location, what to watch for). Attaching your resume is optional.

Claude publishes your private copy, fills in your profile and offers to schedule a lead scan. If you schedule one, open that task's settings and turn on **Automatically approve**, so morning runs can save leads without waiting for you.

### Option B: manual
1. Download [`app/offer-track.html`](app/offer-track.html) and attach it to a Claude chat.
2. Ask Claude: *"Publish this as an artifact with the db, sample and downloads capabilities, plus Gmail `search_threads` if I have Gmail connected."*
3. Open the app and fill in **Profile & resume**.

---

## Privacy
- Your jobs, leads, resume and chats are stored in your own artifact's database, not in this repo or the app file.
- The web version counts anonymous page visits with [GoatCounter](https://www.goatcounter.com/) (no cookies, no personal data). Your jobs, resumes and API keys never leave your browser, except that AI requests go directly to the provider you chose.
- Your copy is private to you. Sharing its link gives others access to your data, so share with care.
- To give the app to someone else, send them this repo or the skill zip, not your artifact link.

---

## Repo layout
```
index.html                           Web version (served by GitHub Pages)
app/offer-track.html                 The app (single self-contained file)
skill/offer-track-setup/SKILL.md     Setup skill instructions
skill/offer-track-setup/assets/      Copy of the app used by the skill
dist/offer-track-setup.zip           Ready-to-upload skill package
```

## License
MIT. See [LICENSE](LICENSE).
