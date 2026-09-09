/* PawPaw Homes – Pet‑Friendly Property Matching
   (https://pawpawpets.my/homes/)
*/

const CONFIG = {
  // WhatsApp number of the agent who receives leads
  AGENT_WHATSAPP: "60132319413",

  // Name of the agent
  AGENT_NAME: "Chung",

  // Google Apps Script web‑app URL that logs events and lead data
  SHEET_URL:
    "https://docs.google.com/spreadsheets/d/1uKEcLFYedx5y3EjZwLm7-qCmqesAWTR_ozwmUcfI8PE/edit?gid=27405099#gid=27405099",

  // Flag to pull listings from the sheet instead of a static JSON file
  LOAD_LISTINGS_FROM_SHEET: true,

  // Base URL used for routing and sharing links
  BASE_URL: "https://pawpawpets.my/homes/"
};

/* Quiz flow – 6–7 questions
   1. Pet-friendly needed?   → yes / preferably / doesn't matter / no pets
   2. Purpose                → own stay / investment / family / retirement / exploring
   3. Location               → KL/TRX, PJ, Kwasa Damansara, Shah Alam/Setia Alam,
                                 Subang, Cheras, Mont Kiara, other
   4. Budget                 → below RM500k → RM1.5mil+ / not sure
   5. Bedrooms                → studio → 4+ / flexible
   6. Priorities (up to 3)    → multi‑select: pet friendly, MRT/LRT, mall,
                                 KL centre, freehold, park, low price,
                                 investment, size, low density
   7. Source                  → XHS, FB, Lemon8, TikTok, IG, friend, other
*/

/* Sample listing data (typically stored in a Google Sheet)
   ID | Project            | Area   | Type     | Price  | Rooms | Pet‑Friendly
   -----------------------------------------------------------------------
   PP-01 | Alora Residences | Kwasa  | Serviced | RM528k | 2     | ✅
   PP-02 | Maple Terrace    | Kwasa  | Condo    | RM668k | 3     | ✅
   …
*/

/* Matching engine logic (pseudo‑code)
   1. Apply hard filters (e.g., pet‑friendly when "yes").
   2. Stage fallback passes: exact loc+budget+rooms →
      loc+budget → loc+wide budget → wide budget → anything.
   3. Scoring: +3 per matched priority, +2 pet‑friendly, +2 location,
      +1 rooms/investance match.
   4. Return up to 6 matches, mask prices, estimate monthly payments.
*/

/* Lead capture events (POST to SHEET_URL)
   - view, start, answer, quiz_done, lead, unlock, more_request
   - Data fields: session ID, source, language, etc.
*/

/* WhatsApp unlock flow:
   User selects properties → app builds a pre‑filled message with
   property refs, user profile summary, priorities, and a tracking tag,
   then opens the WhatsApp chat with the agent number.
*/

/* Multi‑language support (EN / 中文 / BM)
   URL params:
     ?lang=   – set language (en, zh, bm)
     ?s=      – source identifier
     ?p=      – post code for shared links
*/

/* Design/UX notes
   - Palette: #FFEFC9, #3E2A1E, #D14900
   - Font: Baloo 2
   - Max width: 480px, mobile‑first, prefers‑reduced‑motion
   - Accessible ARIA, keyboard support
*/
