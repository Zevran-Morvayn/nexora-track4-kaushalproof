# Tech stack

| Layer | Tool | Job in KaushalProof |
|---|---|---|
| Frontend | React, Vite, Tailwind CSS, React Router | Worker, assessor and employer dashboards; public verify page |
| Languages | i18next | English, Kannada and Hindi interface text |
| Backend | Python Flask | REST API, role checks, assessment workflow, credential issue |
| Database & auth | Supabase (PostgreSQL) | All records; email/phone login |
| Video storage | Amazon S3 | Private storage for demo videos |
| Processing | AWS Lambda + FFmpeg | Extracts key frames when a video is uploaded |
| AI pre-check | Google Gemini API | Compares frames with the skill checklist |
| Identity | Amazon Rekognition | Matches the face in the video with the worker's ID photo |
| Voice | ElevenLabs Text to Speech | Reads steps and checklists aloud in Kannada and Hindi |
| Credentials | Python `qrcode` | QR code linking to the live verify page |
| Hardware | Any smartphone camera | No special devices needed |

## Sponsor integrations

**AWS:** S3 holds the videos, Lambda prepares them for AI review, and Rekognition answers our biggest risk, someone submitting another person's video.

**ElevenLabs:** many target workers are more comfortable listening than reading. Voice guidance in their own language makes sign-up and recording possible without help.
