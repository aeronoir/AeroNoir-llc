# Lambert Mobile Notary Services — business context

Persistent notes for this sub-project. Keep this updated as facts change; don't let the landing page or marketing drift from what's true here.

## Business facts
- Brand: Lambert Mobile Notary Services
- Service area: Richmond, VA metro (Richmond, Henrico, Chesterfield, Hanover County)
- Contact: annfranceslambert@gmail.com (phone still TBD — see landing page TODO flag)
- Credentials: VA Commissioned Notary, bonded & E&O insured (voluntary — VA does not require notary bonding), 4+ years experience, background screened
- Availability: by appointment, evenings & weekends

## Services & pricing (as of Oct 2026)
- General Notarizations — travel fee ($50 base/0-25mi, +$10/5mi beyond, example rate) + $10/act traditional notarial fee (VA law cap)
- Apostille & Document Authentication (flagship/lead-gen focus) — $25 service fee (concierge/prep/filing), separate from the $10 notarial act fee and the separate VA Secretary of the Commonwealth authentication fee (paid at cost, not yet confirmed — see below)
- Loan Signings (purchase/refinance/HELOC)
- Real Estate & Title Documents
- Estate & Healthcare Documents (POA, wills, trusts, healthcare directives)
- Remote Online Notarization (RON) — not yet active, "Coming Soon" on site. Reminder scheduled (trig_01FZ4Gzbo4ecMCBEdjpkBMFL, fires ~Oct 14 2026) to apply: buy e-seal from approved provider, submit Electronic Notary application + $45 fee to Secretary of the Commonwealth. Electronic act fee cap once active: $25/act (VA law).

## Strategic note: proximity to VA Secretary of the Commonwealth
Lambert Mobile Notary's building/office location is around the corner from the Secretary of the Commonwealth's Authentications office (1111 East Broad Street, Richmond, VA 23219 — phone 804-692-0114), which is the office that actually issues VA apostilles/authentications. This is a genuine competitive edge worth leading with in apostille marketing: same-day or next-day in-person drop-off/pickup is realistic for this business in a way it isn't for notaries farther from Richmond, cutting the usual multi-week mail turnaround down significantly for walk-in-eligible cases.

## Apostille process (Virginia) — verify before publishing
Sourced from third-party guides, not a direct fetch of the state's own page (DNS to commonwealth.virginia.gov failed in this environment) — confirm against https://www.commonwealth.virginia.gov/official-documents/authentications/ before putting exact figures in client-facing material:
1. Document must first be notarized (or already be a certified public record).
2. Submit to the Secretary of the Commonwealth's Authentications office — by mail, or in person by appointment.
3. State fee: reported as $10 per authentication by one source; another (older, university-sourced) says $10 for the first + $5 for each additional — needs confirmation of current rate.
4. Apostille (Hague Convention countries) vs. Certification/Great Seal (non-Hague countries) — different output, same office.
5. Not available for federal documents (e.g. FBI background checks) — those go through the U.S. Department of State instead.
6. Typical turnaround by mail: ~3-5 weeks per third-party sources; in-person by appointment is same-day for the state processing step once at the counter.

## Marketing & funnel architecture (decided Oct 2026)
- Flagship lead-gen angle: Apostille (per earlier REFINE strategy work)
- **Canonical site = the Lovable app** (project `edbb186e-c0cc-40be-95df-c553b4d48a3f`, preview_url `https://id-preview--edbb186e-c0cc-40be-95df-c553b4d48a3f.lovable.app`). This is the ONE link every marketing access point (GBP, social bios, QR codes, business cards, directory listings, referral partners) should point to.
- `lambert-mobile-notary/index.html` (this repo, static HTML) is a **retired/backup copy only** — it was never merged to `main` or deployed live, and should NOT be promoted or linked anywhere going forward, to avoid the exact two-front-doors fragmentation problem this decision fixed. Keep it as a static fallback, not an active funnel entry point.
- Booking data source of truth: the Jotform intake (`https://form.jotform.com/262985862427068`), now embedded directly on the Lovable app's `/book` page (merged Oct 2026). The app's own Supabase `bookings` table stopped receiving new submissions at that point — admin dashboard now shows a note pointing to Jotform/Mailchimp for current leads. The `lead_capture` table (checklist email signups) is unaffected and still live.
- **Published Oct 2026** to `https://lambert-mobile-notary.lovable.app` (deployment_id cee2e7c4-6dee-494e-879e-13ed2940317f) — this replaces the preview_url as the canonical link for all marketing access points. Still worth connecting a real custom domain (e.g. lambertmobilenotaryservices.com) before committing to physical/print marketing (business cards, signage) — see Lovable's Project → Settings → Domains panel for the exact DNS records to add, since those are generated per-domain and must come from that panel, not guessed.
- Funnel shape: Awareness (GBP, content, referral partners, directories, physical signage — all one URL) → Capture (apostille-led landing + checklist email capture → Mailchimp) → Conversion (Jotform intake on `/book`) → Retention (Mailchimp nurture, GBP review ask, referral incentive for title companies/attorneys).
