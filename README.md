# Which Vans Go Electric?

## About today

- **The focus of today is your process, not the app.** Present your process first, then give a short demo. Presentations are about 15 minutes per team.
- **Use whatever you normally use:** any tools, agents and languages. There is nothing to install from us; anything that reads CSV works.
- **Your team's thread on Slack:** start it with a one-line intro post, `Team name | tools | setup`. Everything else from your team goes as replies in that thread.
- **Questions for the client** go in your thread, any time. Ewa (the client) answers all teams together, in one public post, in the morning and again at lunch. Questions posted before we leave for the first workshop are answered in the morning; later ones at lunch. If you ask one of us something in person, we'll ask you to post it on Slack, so every team gets the same answers.
- **Everything you deliver goes into your thread.** Sharing your code or repository is voluntary.
- Everything here is fictional: the company, the people, the grant and the vehicle models.

## What's in the pack

| File | What it is |
|------|------------|
| `vans.csv` | The van register |
| `trips.csv` | Telematics export, 15 Jun-13 Sep 2026: one row per route driven by one van on one day |
| `ev_offers.md` | The dealer's offer for two EV van models |
| `costs.md` | Running costs, charging at the depots, a summary of the grant |
| `emails.txt` | An email thread between our CFO, our head of operations and the drivers' representative |

## Letter from Ewa

Hi,

Thanks for taking this on. The short version, because I'm on the road all day.

We're Pyrlandia Dostawy. We supply bakeries and restaurants across Poznań from two depots, North (Suchy Las side) and South (Luboń side), with 38 diesel vans. Next week the board decides which of them we replace with electric vans first. There's a grant for up to ten EVs and applications close on 16 Oct, so it can't wait.

Everything I have is in this repository: the telematics export, the van register, the dealer's EV offer, our running costs, and an email thread between our CFO and our head of operations, who don't agree. That thread is how this started.

**What I need from you**

1. A recommendation I can defend at the board: which vans, how many, and what it saves.
2. Something I can rerun next quarter on a fresh export. My analyst will rerun this next quarter without you. Leave what they need.
3. The assumptions you made while I was away: what you decided, roughly when, and what you'd ask me next.

**Questions.** Post them in your Slack thread. I answer everyone together, once in the morning and once at lunch. I'm on the road: send me your top 5. If I can't answer in time, choose, write it down and carry on. A clear assumption helps me more than a gap.

**At lunch** I'll ask for a quick preview for the CFO: your current shortlist and at least the three check figures. Your `shortlist.csv` and `summary.csv` as they are at that point are perfect. Partial is fine.

**Before the presentations**, please post in your thread:

- `shortlist.csv` and `summary.csv` in my import format below. The CFO always checks the three check figures first: vans assessed, trips counted, total km.
- A one-page note for the board with your reasoning.
- Your tool: show me it rerunning, and post the instructions to run it. A script is enough.
- Whatever my analyst needs to rerun it without you.
- Your assumptions list.

Thanks. I'll read everything tonight.

Ewa, fleet manager

## My import format

All files: UTF-8 CSV, comma separator, header row, dot decimals, no thousands separators, amounts in PLN, distances in km. XLSX next to the CSV is welcome, but the CSV is what counts.

**`shortlist.csv`**: one row per recommended van, in rank order.

| Column | Type | Meaning |
|--------|------|---------|
| `rank` | integer, 1..n | 1 = replace first |
| `van_id` | text | exactly as in the van register |
| `ev_model` | text | EV model name as in `ev_offers.md` |
| `ev_depot` | `North` / `South` | where the EV will be based |
| `range_check_km` | number, 1 decimal | the distance you compared with the EV's range for this van (say how you got it in your assumptions) |
| `annual_km` | integer | the yearly distance you assumed for this van |
| `annual_fuel_saving_pln` | integer | yearly diesel fuel cost minus yearly charging cost for this van |
| `saving_pln` | integer | your saving figure for this van, on your own basis |
| `reason` | text | one short sentence |

**`summary.csv`**: two columns `figure,value`, one row per figure, in this order.

| `figure` | Meaning |
|----------|---------|
| `vans_assessed` | how many vans your analysis evaluated, shortlisted or not |
| `trips_counted` | how many rows of trip data your analysis used (one row = one route driven by one van on one day) |
| `total_km` | the sum of the distance of those rows, in whole km |
| `recommended_count` | the number of vans in `shortlist.csv` |
| `annual_fuel_saving_pln` | the sum over the shortlist |
| `saving_pln` | the sum over the shortlist |
| `saving_basis` | one line: what your saving figure includes and over how many years |
