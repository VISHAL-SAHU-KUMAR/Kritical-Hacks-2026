# API reference

Base path: `/api/v1`. JSON errors are `{ "error": "message" }`. Authenticated routes require the `dueshield_session` HttpOnly cookie.

| Method and path | Access | Behavior |
|---|---|---|
| POST `/auth/register` | Public | `{name,email,password}`; 201 and session cookie; 409 duplicate |
| POST `/auth/login` | Public | `{email,password}`; generic 401 on failure |
| POST `/auth/logout` | Public | Clears session cookie |
| GET `/auth/me` | Auth | Current account identity |
| GET/POST `/invoices` | Auth | List supports `q`, `status`, `page`, `limit`; create validates dates/amount and account-unique invoice number |
| GET/PATCH/DELETE `/invoices/:id` | Auth | Ownership-scoped detail/update/delete |
| GET/POST `/invoices/:id/payments` | Auth | Payment list and positive payment record; overpayment rejected |
| GET `/dashboard/summary` | Auth | Account-derived totals and recent/upcoming invoices |
| GET `/dashboard/analytics` | Auth | Aging, top customers and monthly invoice totals |
| POST `/reminders/generate` | Auth | `{invoiceId,tone,language,channel}`; creates clearly labelled deterministic template draft |
| GET `/reminders` and GET/PATCH `/reminders/:id` | Auth | History and edit draft content |
| POST `/reminders/:id/mark-sent` | Auth | Records manual user claim; no delivery is asserted |
| POST/GET `/research` | Auth | Saves question/status; POST returns 503 until real integration is configured |
| GET/POST `/invoices/:id/checklist` | Auth | List/add checklist item |
| PATCH/DELETE `/checklist/:id` | Auth | Update/delete owned item |
| GET/PATCH `/settings` | Auth | Read/update profile preferences |
| GET `/reports/receivables`, `/reports/export.csv` | Auth | Account-only report and escaped CSV |

Validation failures return 400, unauthenticated access 401, absent/foreign resources 404, duplicate registration/invoice numbers 409, oversized body 413 and unavailable live research 503.
