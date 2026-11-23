# API design (planned)

Flask REST API, JSON over HTTPS. Role required is shown for each route.

| Method | Route | Role | Purpose |
|---|---|---|---|
| POST | `/api/auth/register` | Public | Create an account with a role |
| POST | `/api/auth/login` | Public | Log in |
| GET / PUT | `/api/me` | Any | Read or update own profile |
| GET | `/api/skills?trade=` | Any | Skills and checklists for a trade |
| POST | `/api/assessments` | Worker | Upload a demo video for a skill (stored in S3) |
| GET | `/api/assessments/mine` | Worker | Own assessments and their status |
| GET | `/api/assessments?status=pending` | Assessor | Review queue with signed video URLs |
| POST | `/api/assessments/<id>/ai-check` | Assessor | Run Gemini checklist check + Rekognition face match |
| POST | `/api/assessments/<id>/decision` | Assessor | Approve or reject with remarks; approval issues a credential |
| GET | `/api/workers?trade=&location=&skill=` | Employer | Search workers with approved credentials |
| GET | `/api/verify/<credential_id>` | Public | Live status: valid, revoked or not found |
| GET | `/api/credentials/<id>/qr` | Worker | QR code image for a credential |
| GET | `/api/voice?text=&lang=` | Worker | Spoken instructions via ElevenLabs |

## AI check response (example shape)

```json
{
  "criteria": [
    { "item": "Required tools visible", "status": "appears_demonstrated", "note": "Tester and screwdriver seen" },
    { "item": "Power isolated before work", "status": "needs_review", "note": "Switch not clearly shown" }
  ],
  "face_match": { "similarity": 97.4 },
  "summary": "Most steps visible; safety step needs assessor review.",
  "advisory_only": true
}
```
