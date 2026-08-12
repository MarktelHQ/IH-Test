# Investing Hero — Advisory Platform Concept

*Written 12 August 2026 from the design session with the owner, and updated the same day after the pricing,
packaging and go-to-market decisions. Companion artefacts: `investinghero-dashboard-mockup.html`, a working
mockup of nine screens, and `investinghero-advisory-upsell.html`, the sales page for the advisory upsell.*

**Status:** concept agreed, not yet built. Gated on FinSA registration and on the course being produced.

---

## 1. What this is

A private, login-protected platform for people living in Switzerland that combines two things which are
normally sold separately:

1. **A self-paced course** teaching Swiss personal finance, and
2. **A personal advisory service** in which a registered client adviser reviews the member's actual
   accounts every quarter and issues written recommendations.

One application, one login, two entitlements. Everyone who buys the course gets the course and a view of
their own numbers. Only members who take the paid upgrade receive personal advice.

### The one-line promise

> A registered adviser looks at your actual accounts every quarter and tells you, in writing, what to
> change and what it is worth.

### Why it is defensible

Not the software. Providers can and will build fee calculators. The moat is that the platform is
independent of every provider it compares, a named registered person stands behind each recommendation,
and the service will tell a member to leave a provider that pays Investing Hero a commission. That is a
positioning moat, so it must be stated everywhere rather than implied.

---

## 2. Regulatory frame

The advisory layer is **regulated investment advice under FinSA**, not education, and the platform must
be designed around that from the first line of code.

### Qualification and registration

- Course: VisionCompliance "Asset Management and Investment Advice", CHF 1,290, roughly 22 hours,
  online, English. Confirmed by regservices.ch as satisfying both the Art. 6 professional knowledge
  requirement and the Rules of Conduct requirement.
- Registration as an individual **client adviser** on the BX Swiss / regservices.ch register. This is
  registration, not a FINMA licence.
- Also required before registration completes: Swiss debt-register and criminal-record extracts;
  professional indemnity insurance of CHF 500,000 or more held under the GmbH (quoted at approximately
  CHF 1,500 a year); affiliation with a FINMA-recognised ombudsman such as FINSOM; amendment of the
  GmbH *Statuten* to include investment advisory as a purpose; application on regservices.ch, roughly
  30 days to registration.

### In scope

- Transaction-related advice, meaning single product recommendations.
- Portfolio-related advice, meaning ongoing advice considering the whole portfolio. This is what the
  quarterly review actually is, and it triggers full suitability plus ongoing update duties.
- Fund-based pillar 3a advice, which is a financial instrument in the same regulatory bucket as ETFs.

### Explicitly out of scope

| Excluded | Why |
|---|---|
| Discretionary management, power of attorney, execution authority | FinIA portfolio management licence, a different and much larger authorisation |
| Pillar 2 / BVG decisions, insurance-wrapped pension products | Separate track under the Insurance Supervision Act |
| Mortgages and insurance advice | Deliberate commercial scope decision; a Tools and Resources calculator is acceptable, advice is not |
| Crypto | Generally not a financial instrument under FinSA and almost certainly outside PI cover |
| Tax filing | Handled by referral to Ynoves |

The platform must never hold execution authority, discretion or power of attorney over a member's
accounts. Advice plus execution by the member themselves is the entire model.

### Duties that shape the design

Every personal recommendation must be able to evidence: which advisory service type was given and that
this was disclosed; the client information relied on; that an appropriateness or suitability assessment
was performed; documentation of the advice and the data behind it; and disclosure of conflicts of
interest including affiliate relationships.

This is why the platform has an immutable record rather than an editable one.

---

## 3. The offer and pricing

| Product | Price | Type | Entitlement |
|---|---|---|---|
| Course | CHF 599 | one-off | `learn` |
| Opening Review (onboarding) | CHF 199 | one-off, charged with the first subscription | `advised` |
| Personal advisory dashboard | CHF 349 | per year, auto-renewing | `advised` |

**Year one for an advised member is CHF 548. Renewal is CHF 349.**

The split onboarding fee was added after a market check on 12 August 2026. Rationale:

- The Opening Review is a focused advice engagement, and the Swiss market price for exactly that piece
  of work as a one-off is CHF 390 to 690. Including it inside a CHF 349 subscription underprices it.
- It matches revenue to where the work actually is. Year one is far heavier than year two.
- It removes the incentive to take the expensive deliverable in week one and cancel, which is also what
  unlocks quarterly billing as an option later.

### Where this sits in the market

| Comparable | Price |
|---|---|
| PVVS Finanz-Abo Basic / Plus, the closest subscription comparable | CHF 160 / CHF 290 a year |
| Independent Swiss advice, hourly | CHF 150 to 400 an hour |
| Focused advice engagement, one-off | CHF 390 to 690 |
| Comprehensive financial planning, one-off | CHF 840 to 2,000 |
| Robo-adviser on CHF 191,000 at 0.4 to 0.5%, with no personal advice at all | CHF 760 to 955 a year |
| Prospert live cohort investing course | CHF 2,486 |
| Self-paced Swiss personal finance courses | CHF 250 to 2,000 |

CHF 599 for the course sits in the upper-middle of self-paced and well below anything with live contact,
which is the right place. It is also already published on the course page, so it is effectively committed.
CHF 548 in year one and CHF 349 thereafter puts the advisory layer just above the only real subscription
comparable and far below hourly or planning engagements, which is defensible for a service that includes
a named registered adviser reviewing actual holdings.

Do not go below CHF 349. For regulated personal advice, cheap reads as low value, and this audience is
buying trust rather than shopping on price.

- The course is sold standalone at CHF 599 and remains the primary product.
- The dashboard is an upsell to course buyers, not a bundle. This is deliberate: bundling the advice
  layer into every course sale would make every course buyer a FinSA advisory client with a suitability
  file, a documentation record and a slot in the quarterly batch, whether they wanted advice or not.
- Annual only in year one. Quarterly billing is deferred because the Opening Review, the most expensive
  deliverable, happens in week one and a quarterly plan lets someone take it and cancel.
- Two-year prepay is deferred until the process is proven, because it concentrates the delivery
  obligation.
- **Swiss residents only.** Enforced by self-declaration at checkout plus the residency field in the
  profile, and stated in the terms.

### What the fee buys

- An **Opening Review** on joining: a dated written report, delivered in-app and as a PDF, stating current
  total annual cost, the recommended moves in order of impact, projected before and after, conflicts
  disclosed, and the adviser's name and register number.
- **Four quarterly reviews a year**, on fixed calendar quarters, including quarters where the answer is
  "nothing needs changing" and the deliverable is the list of what was checked and found correct.
- **A monthly note** on what changed in Swiss investing, sent to every member.
- **Two personal letters a year**, written to everyone but containing a section written for the
  individual member which does constitute advice.
- **Tax date prompts** tied to the member's canton, and the handoff to Ynoves.
- **One written question per quarter**, answered inside the review rather than by email.

### What it explicitly does not buy

No calls in year one. No ad-hoc advice between reviews. No access to the member's accounts. These are
stated on the pricing page, because people buying financial advice assume a call is included unless
told otherwise.

---

## 4. The member experience

Nine screens exist in the mockup. Each is listed with what it does and what compliance artefact it
produces.

### 4.1 Sign in

Password plus mandatory TOTP. Positioning line stating regulated advice for Swiss residents,
registered and insured. Four trust lines leading with the FinSA registration and the ombudsman and PI
cover, and closing with security. No marketing pitch: this page is for people who have already bought.

### 4.2 Dashboard

Opens "Hey, Sophie". The hero figure is **what the member's setup costs them this year in francs**, not
net worth. Net worth moves for reasons nobody controls and implies responsibility for markets; cost is
controllable and every recommendation reduces it. This choice should be tested rather than assumed.

Contains: three stat tiles (total tracked, identified saving, last confirmed); a fee comparison of the
member's 3a against the cheapest alternatives; an allocation bar coloured by account type, matching the
accounts page exactly; a projection of the recommended change to retirement; a tax card; and the three
most recent updates.

### 4.3 Recommendations

A list, not a single item. Open recommendations, completed ones with the date the member acted and what
they saved, and declined ones marked closed and not actioned. The list footer states the ratio, for
example "three of four acted on", because a recommendation that was not taken changes what is said next
quarter.

Each recommendation opens to a detail page carrying: the saving, the one-off cost, and the break-even in
years; the reasoning in plain language; a step-by-step execution guide including a generated prefilled
transfer letter the member signs and sends themselves; the source and read-date of every figure; and a
fixed disclosure block covering the affiliate relationship and what the advice was based on.

**Compliance artefact:** the recommendation record, immutable, with the adviser's name, register number,
advisory service type, issue date and the data version relied on.

### 4.4 Accounts and balances

The member enters balances only. **Fees are never entered by the member**, they are looked up from the
product database. This keeps entry to about two minutes per account, keeps fee data current without the
member doing anything, and means a provider repricing automatically flags every affected member.

Account types supported: cash, pillar 3a, brokerage, crypto (recorded, never advised on), and vested
benefits for members who are leaving Switzerland. Household data is recorded; advice is given to one
named client on one login.

A product not yet in the database is held in net worth, excluded from fee analysis, queued for pricing,
and said so plainly in the review.

The page carries a standing prompt before each review: the platform will not review numbers it knows are
out of date. This is framed as the adviser's constraint rather than as nagging, and it is the strongest
possible reason to log in quarterly.

### 4.5 Updates

Everything ever sent, categorised, never deleted. Categories: recommendation, quarterly review, tax,
monthly note, letter. Items expand in place to full content rather than linking away. Every item ends
with a dated provenance footer stating who it went to and whether it is general information or personal
advice.

### 4.6 My profile

- **Details** that decide which tax rates and allowances apply: date of birth, municipality and canton,
  residency, employment, marital status, dependants, monthly outgoings, expected retirement.
- **Risk and suitability assessment**, presented as locked question-and-answer pairs each timestamped.
  The lock is explained rather than merely imposed: every recommendation issued since that date was
  assessed against exactly these answers, so editing them retrospectively would break the record.
- **What the answers produced**: risk profile, capacity for loss, investment horizon, and a note on
  whether current holdings sit inside the range.
- **On-demand reassessment**, roughly eight minutes, logged with date, time and device, superseding the
  previous version rather than overwriting it.
- **Assessment history** with versions marked Current and Archived, and an explanation of what changed
  between them.
- **Record and data**: download the full advice file, download assessment history, change password
  and 2FA, and a statement of the ten-year retention obligation.
- **Support**, see section 6.

### 4.7 Knowledge base

The course, the workbook and the reference library, built on the existing six-part curriculum of roughly
40 lessons. Pill tabs for Start here, Parts 1 to 6, Templates, and Sources. Each lesson shows its ID,
title, duration, the workbook section or exercise it belongs to, and a completion state. A progress bar
shows lessons complete and time remaining.

Above the tabs sits a contextual prompt linking the two halves of the product, for example surfacing
"M5L3 Pillar 3a: the decision framework" because the member has an open 3a recommendation. **This link
between advice and education is the single strongest argument for one platform rather than two.**

### 4.8 Review console (adviser only)

The most important screen in the product, and the one that decides whether the business works.

At CHF 349 a year across four reviews, the budget is roughly CHF 87 per review, which means **a quarterly
review must take under 15 minutes**. The console is built to that number:

- A queue of clients for the quarter with status: ready, no change, blocked on a stale profile.
- A diff of what changed since last quarter, balance by balance.
- Which rules fired, with francs attached, including rules carried over and not actioned.
- A drafted note with selectable boilerplate scenarios.
- Approve and publish, save, or record no change this quarter.
- Approval logged with name, time and the data version used.

Nothing reaches a member until it is approved.

---

## 5. The recommendation engine

**Deterministic rules decide what to advise. AI only writes the explanation.** This is the central
design principle and it is a liability decision as much as a quality one. An AI that decides what to
recommend cannot be audited, reproduced or defended; a rule that fires on a threshold can.

### Rule structure

Each rule has: a trigger condition, a materiality threshold, a franc value, a severity, and a boilerplate
narrative the adviser edits.

### Materiality

No recommendation is raised where the annual saving is below **CHF 100 or 0.1% of the balance, whichever
is higher**. Without a floor the engine nags members about CHF 15 a year and the service loses
credibility.

### Payback

Every recommendation carries a cost, a saving and a **break-even in years**. Some recommendations must
resolve to "do not switch, you are past the point where it pays". The finpension exit-fee case is the
worked example: a CHF 3,000 exit charge against a CHF 400 annual saving is a seven and a half year
payback, which is a different answer for a 60-year-old and a 30-year-old.

### The rule set itself

To be authored by the owner. The estimate is fifteen to twenty-five rules covering the entire useful
universe, for example: 3a total cost above the cheapest available by more than a set margin; equity quota
below profile; cash above the agreed months of outgoings; savings rate materially below best available;
dormant accounts to consolidate; insurance-wrapped 3a to exit; home-bias fund to replace; currency-hedged
share class in the wrong place; contribution below annual allowance; withdrawal staggering not set up;
new asset class outside advisory scope.

**Writing that list down is the highest-value unbuilt asset in this project.**

### Projections

- 7% gross return, contributions rising 1.5% a year as the 3a allowance is raised.
- Assumptions published and dated on a methodology page, versioned like every other figure.
- Fee savings drawn as the certain part; market return as a range, never a single confident line.

### Benchmarking

Against **the best available product in Switzerland**, not against other members. Peer benchmarking needs
a population that will not exist for years and would need consent anyway. Benchmarking against optimal is
more useful, more honest, and available on day one.

---

## 6. Support model

Bounded by design, because an open inbox is what kills solo advisory products. A single long email thread
erases the margin on a CHF 349 member.

| The member wants | Route | Promise |
|---|---|---|
| App, login or billing help | Email support | One working day |
| A question about their money | Written into the next quarterly review | Answered in the review, one per quarter included |
| To report a life change | **Start a new assessment on demand, not an email** | Profile updates immediately, everything afterwards measured against the new answers |
| To complain | One sentence in the grey footnote, naming FINSOM as the free ombudsman route | Present because it must be, deliberately not promoted |

The reasoning is given to the member rather than hidden: answering in the review keeps every answer
documented, assessed against their profile and part of their record.

---

## 7. Product data

**The fee database is the actual product.** The login and the graphs are a few weeks of work; the
database of every provider, product, strategy, constituent fund, TER, admin fee, exit charge and minimum,
kept current and dated, is forever, and it is what is really being sold.

Rules:

- Every figure carries a source link and an "as of" date, visible in the interface.
- Being out of date on a blog post is an embarrassment. Being out of date inside a personalised
  "switch and save CHF 412 a year" projection that someone acts on is a different class of risk.
- A repricing updates the database once and flags every affected member automatically.

Long term this database could also power public comparison tools on investinghero.ch, turning a
maintenance cost into an asset that earns on the free side. Deferred for now.

---

## 7b. Positioning and messaging

The single most important message is that this is **personal, regulated advice, not more content**. Every
competitor in the education space stops at generic material; the qualification is what lets Investing Hero
cross that line, so the language has to keep saying so.

### The lines that carry it

- Headline: **"You've learnt the basics. Now get your personal advice."**
- Opening: *"Online content has to speak to everyone. So it can never tell you exactly what to do with your
  own money. This is different. A qualified investment adviser, registered under Swiss law, gives you
  personal recommendations and real insight into your own plan. Without the hefty fees and the hidden
  costs."*
- Section heading: **"Courses & blogs can't give personal investment advice. This can."**
- Pricing heading: **"One clear flat fee. Never a percentage of your assets."**

### Rules for all customer-facing copy

1. Say **personal**, **qualified**, **registered**, **regulated**. Those four words are the product.
2. Informal register. Contractions throughout. No press-release phrasing, no em-dashes.
3. Never claim what has not been decided. The referral-fee rebate was written and then removed because it
   was not true. Disclosure of the relationship is what the copy claims, and nothing more.
4. Lead with what the reader gets, not with what the business is.
5. The honest exclusions stay visible. "When you should not buy this" earns more trust than any claim.

### The positioning against the traditional industry

The sales page frames price as **what you are not paying for**: commission-driven product selling, an
insurance policy dressed as an investment, a percentage of your assets, half a day off work for a meeting,
a 60-page plan read once, a relationship manager who calls you, and the Porsche in the car park. Fully
digital delivery is presented as a benefit rather than a compromise.

The comparison section opens on the unfairness that the people who would benefit most from advice are the
ones who cannot afford it, because advice in Switzerland is priced for people who already have money.

### Design standards applied

Palette sampled from investinghero.ch and never invented. Stat tiles, indigo numbered chips, 42px icon
tiles and a dated sources footer, all from the house style. Line length capped at 46 to 58 characters in
multi-column blocks. Text contrast at or above 4.5:1 on dark surfaces. Visible focus rings on every
interactive element, because the theme strips outlines sitewide. Skip link, `main` landmark, decorative
icons hidden from screen readers, reduced-motion honoured, and the comparison table collapses to stacked
cards below 820px.

---

## 8. Technical decisions

| Decision | Choice | Note |
|---|---|---|
| Architecture | One application, single login, two entitlements: `learn` and `advised` | Looks like one product to the buyer, behaves like two to the business |
| LMS | Self-hosted shell: lesson list, progress, gating, workbook downloads | Owning the shell is what makes the advice-to-lesson links possible |
| Video | **Not** self-hosted. Third-party streaming with signed, expiring URLs | Bunny Stream, Cloudflare Stream or Vimeo. Self-hosting video is where this goes wrong |
| Platform | Separate application, not WordPress | Built with Claude Code |
| Database | Supabase, region to be decided | Frankfurt is fastest to ship and adequate under the FADP; Swiss hosting at Infomaniak or Exoscale is slower to set up but supports a stronger claim. Hostpoint cannot run this |
| Language | English only at launch | German is a maintained second version later, from one master |
| Devices | Responsive web. Reading designed mobile-first, editing designed desktop-first | Editing balances is a quarterly desktop job; reading the inbox is a two-minute phone job |
| Security | Mandatory TOTP two-factor, no SMS; session timeout; password reset that never reveals balances; no developer access to production client data | |
| AI | Never sees names, emails or identifying details. Pseudonymous client ID with balances, product codes and profile answers only | A genuine selling point, cheap now and expensive to retrofit |
| Payments | Stripe direct, in CHF | Swiss-residents-only removes EU VAT, OSS and any need for a merchant of record, and takes processing from about 5% to about 2.9% |
| Tax | Swiss VAT only, a threshold question for the Treuhänder | The CHF 100,000 threshold applies to the GmbH's total worldwide turnover including affiliate and advertising income, not to this product line |
| Design | Palette sampled from investinghero.ch, never invented. Ink `#1F0E45`, blue `#0073AA`, green `#00DF56`, Inter with Maven Pro, 16px cards, pill inputs | Chart series colours validated for colourblind separation |

---

## 9. Calendar and rhythm

- **Fixed calendar quarters** for every member, not anniversary dates. One batch, four times a year.
  This makes the workload schedulable, allows the news wrap to be genuinely shared, and creates a rhythm.
- **Opening Review on joining**, independent of the cycle.
- **Monthly note**, sent to everyone.
- **Two personal letters a year**, general content plus a personal section that forms part of the
  advice record.
- **Tax prompts** on the member's canton dates.

The renewal decision arrives after only three or four touchpoints, one of which was the big one at
onboarding. The monthly note and the mid-year letter exist specifically to fill months nine to eleven.

---

## 10. Economics

| Line | Assumption | Year one |
|---|---|---|
| Course | 2 to 3 sales a month at CHF 599 | CHF 14,000 to 21,000 |
| Dashboard | 1 to 2 members a month at CHF 548 in year one | CHF 6,600 to 9,900 |
| **Total** | | **roughly CHF 21,000 to 31,000** |

From year two, each retained member contributes CHF 349 rather than CHF 548, so growth has to come from
new members and from retention rather than from the onboarding fee repeating.

Fixed compliance stack: PI insurance approximately CHF 1,500, plus ombudsman affiliation, register fees,
the FinSA course at CHF 1,290 and the *Statuten* amendment. Budget CHF 2,500 to 3,500 a year, covered by
roughly ten subscribers.

The dashboard is not the revenue engine. It is the recurring layer and the credibility engine, and it
should be scoped accordingly. Its second job is making the course and the whole site more trustworthy,
which is worth more than its own revenue line.

### The metric that matters

Not renewals. **Recommendations acted on.** If eight of ten opening recommendations get executed, the
product is real and renewals follow. If two of ten do, the advice is correct and useless, and the fix is
in the execution guides rather than the advice. Instrument this from launch; it is also the number that
would sell the course.

---

## 11. Build sequence

1. Confirm the FinSA registration path and get real quotes for PI cover and ombudsman affiliation.
2. Amend the GmbH *Statuten*; have the VAT conversation with the Treuhänder in the same sitting.
3. **Author the rule set.** Fifteen to twenty-five rules, written down, with thresholds and franc values.
4. Build the application shell: auth, entitlements, profile, accounts, product database.
5. Ship the **course** inside it first. It is unregulated, it is faster revenue, and it does not wait on
   registration.
6. Complete FinSA registration.
7. Switch on the **advice layer**: assessment, rules engine, recommendations, review console, updates.
8. Onboard the first members. Deliver Opening Reviews by hand against the rule set to prove the timings
   before automating the drafting.
9. Add the German version from the maintained master.
10. Only then consider: quarterly billing, two-year prepay, a call upsell, public comparison tools sharing
    the product database.

### The funnel

Blog and free guides → lead-magnet webinar (which replaced the planned free demo tier) → course at
CHF 599 → advisory upsell at CHF 199 plus CHF 349 a year, sold on the course completion page and through
email nurture. The upsell page carries a demo link into the dashboard, because the product is much easier
to sell once seen.

---

## 12. Open decisions

| # | Decision | Owner | Notes |
|---|---|---|---|
| 1 | The rule set | Owner | The highest-value item on this list |
| 2 | Database region: Frankfurt versus Swiss-hosted | Owner | Decides what claim can honestly be made on the sales page |
| 3 | Video host | Owner | Bunny, Cloudflare Stream or Vimeo |
| 4 | Real tax figures for the dashboard | Owner | Zug wealth tax allowance, deduction values, staggering estimates are placeholders in the mockup |
| 5 | Hero metric on the dashboard | Test | Annual cost is the current proposal, unresolved |
| 6 | Course-to-dashboard access window and what happens at expiry | Owner | Proposal: 90 days, profile preserved permanently and locked behind the paywall rather than deleted |
| 7 | Lesson titles | Owner | The 40 in the mockup are placeholders except M2L2 and M5L4 |
| 8 | Leaver product shape | Owner | Swiss resident at signup; departure during a subscription becomes a defined event and a one-off Leaving Switzerland review |
| 9 | PI cover wording | Owner | Confirm it covers investment advice as registered, and check what it says about crypto held in the same file |
| 10 | **How referral income is handled inside paid advice** | Owner + regservices | The sales page currently claims disclosure only. A rebate or advance waiver was drafted and removed because it is not yet true. This must be settled before the first paying client |
| 11 | Opening review turnaround | Owner | The sales page promises 10 working days. That is an assumption, not a commitment |
| 12 | FinSA register number | Owner | Placeholder `00000` appears on both the mockup and the sales page |
| 13 | Course-to-advisory attach rate | Measure | The whole model assumes roughly a third of course buyers upgrade. Instrument it from the first cohort |

---

## 13. Risks

**Liability is asymmetric to revenue.** One bad recommendation and one ombudsman case costs more hours
than the entire subscriber base pays for in a year. This is not an argument against the business; it is
the argument for a finite, rules-driven, conservative and documented recommendation set.

**The affiliate conflict is sharper inside paid advice than on a public page.** A disclosed affiliate link
on a blog post is normal practice. Inside a paid personal recommendation it is a conflict both a regulator
and a member would read as material. The design answer is settled: the ranking rule sorts on total cost
alone and cannot see which providers pay, and the relationship is disclosed in a fixed position on every
recommendation. **The commercial answer is not settled.** Whether the referral income is retained,
rebated or waived in advance needs confirming with regservices, and until it is, no customer-facing copy
may promise a rebate. Copy claiming one was written and removed on 12 August 2026 for exactly this reason.

**Free-tier wording drifts.** Nobody designs over the advice line deliberately; it happens in month eight
when someone tunes conversion copy. The rule to write into the spec and test in the build: **no product
name may appear alongside a member-specific franc figure outside a paid, documented recommendation.**

**Data goes stale.** Members will not update quarterly by default. The mitigation is regulatory rather
than motivational: the platform cannot issue advice on numbers known to be out of date, and says so.

**Single point of failure.** A sole registered adviser with ongoing update duties toward paying members
needs a stated position on what happens during illness or absence, written into the terms before it is
needed rather than during.

**Scope creep against price.** Across this design session the scope grew to cash, 3a, brokerage, crypto,
households and leavers while the price came down from CHF 800 to CHF 349. Those move in opposite
directions. Watch it.

---

## 14. Artefacts

- `investinghero-dashboard-mockup.html` — nine-screen working mockup: sign in, dashboard, recommendations
  list and detail, accounts and balances, updates, my profile, knowledge base, and the adviser review
  console. Mock login, brand palette sampled from the live site, validated chart colours, sample data
  throughout. Every figure in it is invented and needs replacing with real numbers before it is shown to
  anyone as anything other than a design.
- `investinghero-advisory-upsell.html` — the sales page for the advisory upsell, aimed at course
  completers and reachable from the course and from email nurture. Carries a "View the demo" secondary
  CTA linking to the dashboard mockup, so the two files should be kept in the same folder when shared.
- `finsaqualificationbrief.md` — the owner's FinSA qualification and registration brief.
- `Investing-Hero-Course---Revised-Working-Curriculum-v2.md` — the six-part, 40-lesson curriculum the
  knowledge base is built on.
