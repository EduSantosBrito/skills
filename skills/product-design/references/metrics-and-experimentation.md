# Metrics, Experimentation & Business Math

## Measure traction through return and activation
**Use when** — A rising signup curve on the dashboard feels like proof of traction, particularly under a freemium model.

**Decision** — Signups are the cheapest action a user takes, so they measure curiosity, not value — especially in freemium. Real growth is whether people come back and do the action that delivers value.

**Action** — Treat signups as top-of-funnel only — never stop reading there. Track who returns on day 2 and day 7 (D1/D7 retention) and how many complete the value-delivering action (activation). Paid media can inflate signups while real retention stays flat.

**Source language** — "The signup curve climbs with paid traffic, but usage and activation only climb with a good product."

**Source** — [@richardrx · 2026-06-11](https://x.com/richardrx/status/2065082771987394651)

## Read each product metric as one diagnosis, then read the whole panel
**Use when** — A founder fixates on one number or conflates what each metric diagnoses.

**Decision** — The post maps each metric to the question it mainly hints at: ARR to size (not necessarily health); burn rate to risk (time until death); CAC to efficiency (pushing it down can bring a less-qualified cohort); DAU/MAU to engagement; LTV to whether customers see value; churn to fit; NRR to real growth; gross margin to the model; runway to survival. Like a blood panel, the readings are complementary clues, not a causal diagnosis: one bad reading can be critical, and only the whole panel suggests health.

**Action** — Use each metric as a lead for its layer, then read the full panel and the local evidence behind it before prescribing a fix: ARR alone cannot prove health, low CAC can hide a weak cohort, and strong growth without margin or runway can still be fatal.

**Evidence** — The post's warning thresholds are practitioner rules of thumb, not universal benchmarks: DAU/MAU under 20% is a bad sign; NRR above 100% is good; SaaS gross margin under 70% is a problem (AI wrappers excepted); runway under 12 months is danger. Calibrate them to your business model and stage.

**Source** — [@richardrx · 2026-01-12](https://x.com/richardrx/status/2010675817483817384)

## Model the retention metric before choosing a game mechanic
**Use when** — You are adding gamification by copying a mechanic instead of finding the metric that compounds engagement.

**Decision** — Model the retention metric before borrowing a mechanic. In Duolingo's case — a product meant for daily use — that meant optimizing the number that moved daily active users (DAU). Duolingo copied game mechanics twice and failed: a Gardenscapes-style moves counter was neutral, and a referral program copied from Uber gained only 3% because its reward excluded the best users. It then modelled which number to move — bucketing users by engagement and simulating +2% a quarter for three years — and current-user retention rate (CURR) had about five times the impact of the next-best metric. Gamification worked once aimed at CURR.

**Action** — Start from how often the user's task naturally recurs — daily, weekly, or yearly — and the useful result each return delivers; choose the retention metric at that cadence and set guardrails, such as task success, complaints, and opt-outs, so the work never chases opens that deliver no value. Gamification is optional. If you use it, points, badges, and leaderboards are only the free sample of a much larger set of gamification mechanics. Three useful ones: competition with a defined start, middle, and end; progress bars as trajectory achievement, not just onboarding; and content unlocked by engagement (a forecast panel that opens after 30 real entries — a ladder, not a paywall). Design each mechanic for the user's own progress, with opt-out and without punishing absence.

**Evidence** — Duolingo's results as reported in the post, specific to one consumer-learning product: CURR +21% over four years, daily churn of best users down 40%+, DAU ×4.5. Leaderboards alone added 17% total learning time and tripled highly engaged learners after users competed with others of similar prior-week engagement (automatic opt-in, a default effect, with no extra tasks).

**Visual** — Duolingo's DAU curve from mid-2018 to mid-2022, marked "Started working on CURR" at the inflection, with a 4.5× arrow from there to the top right — [source media](https://raw.githubusercontent.com/heliocosta-dev/revenue-centric-design/1942760c2242f609bf63ce2c97204f5a1791bd68/assets/2081714430811730162__1.jpg)

**Source** — [@richardrx · 2026-07-27](https://x.com/richardrx/status/2081714430811730162)

## Require sufficient power before an A/B test
**Use when** — You're in traction or survival stage, ran a test for a week, saw "variant B won by 12%," and want to ship it everywhere.

**Decision** — Most A/B tests in small SaaS lack the volume to prove anything, yet founders swap the whole product on the result. Testing without enough sample to conclude is the trap.

**Action** — Before running, declare the primary metric and guardrail metrics, then compute the minimum sample size (free calculators exist); if you can't hit that floor in reasonable time, don't start. Test big things (headline, offer, pricing structure, onboarding) since large effects need less sample. Never stop a test because the number looked pretty mid-way. With no volume, decide by qualitative research — five good interviews beat an underpowered A/B test. Beware the law of small numbers and confirmation bias.

**Evidence** — ProfitWell is categorical: don't A/B test price — you'll never have the volume or context for it to mean anything.

**Source** — [@richardrx · 2026-06-01](https://x.com/richardrx/status/2061463480868229189)

## Celebrate conversion-weighted signal quality
**Use when** — You launch a waitlist and feel tempted to celebrate raw headcount.

**Decision** — A waitlist exists to validate that a pain is one people pay to solve — not to sell. Absolute size is a vanity metric; conversion-weighted quality is the real signal.

**Action** — Convert size to expected customers before reacting: a good waitlist converts 15–20% to paying, above 30% is excellent. 53 people at 20% = 10 customers; 1,000 people at 1% = 10 customers — same result, different perception. Until there's a transaction, there's no validated hypothesis.

**Source language** — "Founders celebrate the size of the list when they should celebrate the quality of the signal."

**Source** — [@richardrx · 2026-04-17](https://x.com/richardrx/status/2045094511106220220)

## Translate churn points into LTV
**Use when** — You're staring at a churn percentage and treating it as a vanity number rather than money.

**Decision** — Most people watch churn %, but few compute what each point costs in accumulated LTV over 12 months. Cutting churn is a cash lever that needs no price hike or new acquisition.

**Action** — Do the churn→LTV math: at 25% monthly churn on 1,000 users you must add 250 new users/month just to break even — kill paid traffic and the product dies in ~4 months. Then improve retention without Figma: define the Aha Moment, measure time-to-value (TTV) from signup to it, ask "how do I deliver this faster?", break it into micro-wins if you can't, then test, measure, repeat.

**Evidence** — Finance SaaS, ARPU R$120: cutting churn 5 points (25%→20%) is +R$72,000/year in cash, with no price change and no extra acquisition.

**Source** — [@richardrx · 2026-04-06](https://x.com/richardrx/status/2041184077106004289)
