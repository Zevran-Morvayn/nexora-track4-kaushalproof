# KaushalProof

**Turning practical skills into verifiable digital credentials.**

| | |
|---|---|
| Team | Nexora |
| College | Dayananda Sagar Academy of Technology and Management |
| Event | wHACKiest 2026 Online Ideathon |
| Track | 4 – Localized Vocational Skill Verification |
| Pitch deck | [Google Drive link](PASTE_DRIVE_LINK) |
| Video pitch | [YouTube link](PASTE_YOUTUBE_LINK) |

> **Blueprint phase.** Per wHACKiest rules, this repository currently holds the design and plans only. Code will be added here during the 24-hour hack day.

## The problem

Most of India's electricians, plumbers, masons and carpenters learned their trade on the job. They have no trusted way to prove what they can do, and employers have no reliable way to check.

- Only **4.2%** of people aged 15–59 have formal vocational training (PLFS 2025, MoSPI).
- **30.6%** were trained informally: on the job, self-taught or by family (PLFS 2023–24).
- Today's options fall short: job portals rely on self-declared skills, paper certificates are easy to forge, and RPL camps are batch-based.

## Our solution

A worker records a short video of a real task. A qualified assessor reviews it, helped by an AI pre-check. If approved, the worker gets a digital credential with a unique ID and QR code that any employer can verify in seconds.

**The AI never certifies anyone. Only a human assessor's approval creates a credential.**

### Users

| User | What they do |
|---|---|
| Worker | Registers, picks a skill, uploads a demo video, holds credentials |
| Assessor | Reviews the video and AI notes, approves or rejects with remarks |
| Employer | Searches workers by trade, skill and location; scans a QR to verify |

### User flow

1. Worker registers and adds trade, location and experience (voice-guided in Kannada, Hindi or English).
2. Worker picks a skill, e.g. "electrical installation", and sees its checklist.
3. Worker records or uploads a video of the task.
4. AI checks frames against the checklist and matches the face to the worker's ID; an assessor decides.
5. On approval, a credential with a unique ID and QR code is issued.
6. An employer scans the QR or searches to verify it live.

## Architecture

![Architecture diagram](docs/architecture.png)

Details: [docs/architecture.md](docs/architecture.md)

## Tech stack

| Layer | Choice | Why |
|---|---|---|
| Frontend | React + Vite + Tailwind CSS | Three dashboards built fast from shared components; mobile-friendly |
| Backend | Python Flask (REST API) | Simple role-based endpoints; Python suits the video and AI steps |
| Database | Supabase (PostgreSQL + Auth) | Records and login in one managed service |
| AI | Google Gemini API | Compares video frames with the skill checklist |
| Cloud (AWS) | Amazon S3, AWS Lambda, Amazon Rekognition | Video storage, frame extraction on upload, face match to ID |
| Voice (ElevenLabs) | ElevenLabs Text to Speech | Reads steps and checklists aloud in Kannada and Hindi |
| Libraries | qrcode, FFmpeg, i18next | QR codes, frame extraction, multilingual UI |

More: [docs/tech-stack.md](docs/tech-stack.md)

## Documentation

| Doc | Contents |
|---|---|
| [architecture.md](architecture.md) | Components and how data flows between them |
| [database.md](database.md) | Planned tables and relationships |
| [api-design.md](api-design.md) | Planned REST endpoints |
| [tech-stack.md](docs/tech-stack.md) | Each tool, its job and sponsor integrations |
| [hack-day-plan.md](docs/hack-day-plan.md) | Team roles and the 24-hour build plan |

## Team Nexora

| Member | Role on hack day |
|---|---|
| Mithun A (Lead) | Backend: Flask API, workflow, credentials and QR |
| P Prem Akarsh | Frontend: worker and employer screens, verify page |
| Modini Siri | Frontend: assessor dashboard, design, languages |
| Lahari S | Data, AI and AWS: schema, S3/Lambda, Gemini, Rekognition, ElevenLabs |
