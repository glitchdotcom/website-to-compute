# Scholar Desk — Cloudflare migration

This branch contains the first rebuild scaffold. The existing main branch is not changed.

## Included
- React public course catalogue and course detail
- Student registration/login/logout
- Admin-only course creation and video upload API
- Cloudflare D1 schema for users, courses, lessons, payments, enrollments, progress and certificates
- Cloudflare R2 video storage binding
- Razorpay order creation and server-side signature plus captured-payment verification foundation
- Responsive student/admin starter interface

## Cloudflare setup
1. Create a Cloudflare account.
2. Create a D1 database named scholar-desk and execute database/schema.sql.
3. Create an R2 bucket named scholar-desk-videos.
4. Replace REPLACE_WITH_D1_DATABASE_ID in wrangler.toml with the D1 database ID.
5. Set Worker secret SESSION_SECRET to a long random value.
6. Set RAZORPAY_KEY_ID and RAZORPAY_KEY_SECRET as Worker secrets only when ready. Never commit secrets.
7. Install dependencies, build, and deploy with Wrangler.

## Production work still required
- Secure one-time first-admin bootstrap; public signups are always students.
- Protected video playback/streaming endpoint; never expose R2 object keys directly.
- Razorpay webhook signature validation, idempotent event handling and refund handling.
- Checkout UI, printable receipts, certificates PDF, student course/enrollment profile and progress chart.
- Admin dashboard with payment/enrollment reporting.
- Upload quotas, rate limits, backups, monitoring and security tests.
- End-to-end testing in Razorpay test mode before any live payment activation.

Cloudflare free usage is limited rather than unlimited. R2 storage/operations and Worker/D1 usage must be monitored. Razorpay processing fees still apply.
