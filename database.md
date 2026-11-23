# Database design (planned)

PostgreSQL on Supabase. Videos live in Amazon S3; the database stores only their keys.

## Tables

### users
| Column | Type | Notes |
|---|---|---|
| id | uuid, PK | Supabase Auth user id |
| name | text | |
| role | text | `worker`, `assessor` or `employer` |
| phone | text | |
| location | text | e.g. Bengaluru |
| trade | text | Workers only |
| years_experience | int | Workers only |
| id_photo_key | text | S3 key, used for face match |
| preferred_language | text | `en`, `kn` or `hi` |
| created_at | timestamptz | |

### skills
| Column | Type | Notes |
|---|---|---|
| id | serial, PK | |
| trade | text | e.g. Electrician |
| name | text | e.g. Electrical installation |
| description | text | |
| checklist | jsonb | List of task items the video should show |

### assessments
| Column | Type | Notes |
|---|---|---|
| id | uuid, PK | |
| worker_id | uuid, FK → users | |
| skill_id | int, FK → skills | |
| video_key | text | S3 key |
| task_prompt | text | Random prompt shown during recording |
| ai_report | jsonb | Per-item status from Gemini |
| face_match_score | numeric | From Rekognition |
| status | text | `pending`, `approved` or `rejected` |
| assessor_id | uuid, FK → users | |
| remarks | text | |
| created_at, decided_at | timestamptz | |

### credentials
| Column | Type | Notes |
|---|---|---|
| id | text, PK | Short public code, e.g. `KP-7F3K9Q` |
| assessment_id | uuid, FK → assessments | |
| worker_id | uuid, FK → users | |
| skill_id | int, FK → skills | |
| assessor_id | uuid, FK → users | |
| issued_at | timestamptz | |
| revoked | boolean | Default false |

## Seed data for the demo

- Trade: Electrician, with four skills: basic electrical wiring, electrical installation, electrical maintenance, electrical safety knowledge (4–5 checklist items each).
- Demo users: one worker (Ramesh Kumar, Electrician, Bengaluru, 6 years), one assessor, one employer.
