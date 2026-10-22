# Security and privacy status

Implemented safeguards: salted scrypt password hashing, HMAC session signatures, HttpOnly/SameSite cookies, production Secure cookie, account ownership checks, safe JSON parsing, request body limit, CSP, MIME sniffing/referrer headers, server-side financial arithmetic, external calls disabled by default, and no secrets in frontend assets.

Known gaps: no rate limiting, CSRF token, account recovery/deletion, formal retention policy, encrypted-at-rest datastore, structured security audit log, automated penetration testing, or database transaction layer. The file-backed store is for local use only. Before production, migrate to PostgreSQL/Prisma and complete the controls listed above; use HTTPS, managed secrets, access-restricted backups and a documented deletion schedule.

No private invoice data is sent to an AI provider in the current application. Reminder generation is a deterministic local template. No research content or citations are fabricated when TinyFish is unavailable.
