# Hack-day plan (24 hours)

Goal: one electrician goes register → upload → assessor approves → credential + QR → employer verifies.

## Roles

| Member | Owns |
|---|---|
| 1 (Lead) | Flask API, auth roles, assessment workflow, credential + QR, repo |
| 2 | Worker screens, employer search, public verify page |
| 3 | Assessor dashboard, credential card, Kannada/Hindi text |
| 4 | Supabase schema, S3 + Lambda, Gemini, Rekognition, ElevenLabs, demo data |

## Timeline

| Hours | Milestone |
|---|---|
| 0–1 | Agree schema and API routes; set up repo, Supabase, AWS |
| 1–6 | Auth and core routes; worker and assessor screens; S3 upload |
| 6–12 | Approve → credential + QR; public verify page; first full run |
| 12–16 | Gemini checklist check; Rekognition face match; Lambda frames |
| 16–19 | ElevenLabs voice guidance; employer search; languages |
| 19–22 | Deploy, bug fixes, demo data |
| 22–24 | Rehearse demo, final push |

If time runs short, cut in this order: languages, voice, face match, AI check. Never cut QR verification.
