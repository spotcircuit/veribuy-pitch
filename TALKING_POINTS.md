# VeriBuy Pitch — Talking Points (Brian Pyatt)

Use these as your guide while presenting. Each slide has **what to say**, **key points to hit**, and **transition** to the next slide.

---

## Slide 1: Title — Brian Pyatt

**Open with confidence. This is your first impression.**

> "Hi, I'm Brian Pyatt. I put together this presentation to show you not just that I understand what VeriBuy needs — but exactly how I'd build it. I want to walk you through my approach to taking VeriBuy from where it is today to a true production decision engine."

**Key points:**
- Full-stack means you own the problem end to end — no handoffs
- Systems thinker means you design for how pieces connect, not just individual parts
- Ship fast means working software in production, not slides about architecture

**Transition:** *"Let me start with what I understand about VeriBuy's mission."*

---

## Slide 2: I Understand the Mission

**This is the most important slide. You're proving you actually read and understood their docs — not just skimmed them.**

> "What stood out to me about VeriBuy is this line from your docs: the moat isn't the model — it's the proprietary dataset, scoring logic, and workflow integration that improve over time. That tells me this isn't an ML research problem. This is a production data pipeline problem. You need a system that turns noisy inspection photos into structured, explainable scores that insurers and lenders can make real decisions on. And critically — every inspection that flows through the system should make the next score more accurate."

**Key points:**
- **Quote their own words back.** This shows you didn't just skim — you internalized it.
- Emphasize "production data pipeline" not "ML research" — this is what they said in the job description
- The compounding intelligence is the product, not the model itself

**If asked "what do you mean by compounding intelligence?":**
> "Every inspection adds labeled data. Every outcome — loan approved, claim denied — becomes ground truth. Over time, your internal model gets better than any external API because it's trained on YOUR data, YOUR use cases, YOUR outcome signals. That's the moat."

**Transition:** *"Before I get into the how, let me talk about who this system actually serves."*

---

## Slide 3: Stakeholder Ecosystem

**This shows you're thinking beyond code — you understand the business.**

> "VeriBuy isn't a single-user product. There's a whole ecosystem of stakeholders, and each one needs something different. Insurers need explainable scores they can defend to regulators. Lenders need confidence that the collateral condition matches the loan value. Marketplaces need trusted condition reports that reduce buyer disputes. But the stakeholder most teams overlook is the inspector — the person in the field actually taking the photos. Their capture quality determines everything downstream. If the app is clunky or doesn't guide them, you get blurry photos, missing angles, and noisy data. Then you've got dealers and auction houses — high volume, fast turnaround. They need scores in minutes, not days. And fleet managers — they're not doing one-off inspections, they're tracking condition over time across hundreds of assets. That's where the asset graph really shines. And all of this works across four asset classes: vehicles, property, equipment, and collateral. Same pipeline, different scoring configs per asset type."

**Key points:**
- **Top row (cyan) = paying customers** — insurers, lenders, marketplaces. They buy the scores.
- **Bottom row (magenta) = critical users** — inspectors, dealers, fleet. They generate the data.
- **Inspectors are the most overlooked** — if their experience is bad, data quality suffers and the whole pipeline degrades
- **Four asset classes** — shows the system is designed to scale horizontally, not just for cars
- **Dealers & auctions = high volume** — this is where VeriBuy could scale fastest
- **Fleet = recurring revenue** — periodic inspections, not one-time transactions

**If asked "which vertical would you prioritize?":**
> "I'd start with vehicles — it's the most mature use case and you already have prototype data. But I'd design the pipeline to be asset-type agnostic from day one. Scoring configs and label taxonomies are per asset type, but ingestion, inference, and reporting are shared."

**Transition:** *"So with that ecosystem in mind, let me show you where you are today versus where this needs to go."*

---

## Slide 4: Prototype → Decision Engine

**You're showing them you understand the gap — not criticizing what they built.**

> "Your current prototype works. It proves the workflow and the value prop — photos go in, AI analyzes them, clients can see what a condition report looks like. That's exactly what a prototype should do. But right now, every inspection is a one-time transaction. The intelligence stays with the API vendor, not with VeriBuy. The True MVP flips that. Every photo captured structured and training-ready. Scores broken down with evidence clients can actually audit. Your own model learning alongside the external API — not replacing it overnight, but growing next to it. Real business outcomes feeding back to improve accuracy. And the bottom line — a data asset that grows more valuable every day. The prototype proves the value. The MVP captures the intelligence that makes it defensible."

**Key points:**
- **"Works for demos" vs "Works for decisions"** — this framing respects what they built while showing the gap
- **"Intelligence stays with the API vendor"** — this is the pain point. The CEO hears "we're paying someone else to get smarter on our data."
- **"Evidence clients can audit"** — outcome-focused, not architecture-focused
- **The insight line** — "The prototype proves the value. The MVP captures the intelligence." Pause after this. It's the thesis of the whole presentation.
- Don't say "hybrid inference" — say "your own model learning alongside the external API." Same concept, accessible language.

**Transition:** *"Here's what that system actually does day to day."*

---

## Slide 5: What the System Actually Does

**This is the slide that lands for everyone in the room. The CEO sees the value. Isaac sees you understand the pieces.**

> "Let me walk through what this system actually does day to day. An inspector uploads 10 photos of a vehicle. The system instantly validates the quality — flags blurry shots, extracts GPS and timestamp data, and stores everything structured and analysis-ready. No manual cleanup. Then it scores and explains. Not a black-box number — a full breakdown. 'Body panels: 6.2 — moderate dent detected on rear quarter panel.' Every score is backed by visual evidence the client can audit. But here's where it gets powerful. When a lender makes a decision based on that score — say they deny a loan — that outcome flows back into VeriBuy. Now the system knows what a 'bad score' actually looks like in the real world. Accuracy compounds with every decision. And because we're tracking assets over time, if the same car was scored 87 in January and comes back at 62 in July, VeriBuy sees that delta. It can flag deterioration, catch fraud, detect inconsistencies. No single-inspection tool can do that."

**Key points:**
- **Capture & Structure** — the "no manual cleanup" line resonates with ops-minded people
- **Score & Explain** — use the concrete example (body panels: 6.2, rear quarter panel dent). Makes it tangible.
- **Learn & Improve** — the loan denial example is the killer line. It makes the feedback loop real and concrete for the CEO.
- **Track Over Time** — the 87→62 example is your moat story. Say "no single-inspection tool can do this" — that's the competitive differentiation.
- The flow diagram at the bottom (Capture → Process → Analyze → Score → Report → Learn) gives Isaac the architecture at a glance

**Transition:** *"Now, every one of these capabilities is a deliberate architecture decision. Let me show you why it's built this way."*

---

## Slide 6: Why This Architecture Matters

**This is the bridge between business value and technical depth. Each card has a business line (for CEO) and a technical line (for Isaac).**

> "Every technical decision in this system maps to a business outcome. Structured from day one — when you're ready to train your own model, every past inspection is already usable. You don't have to go back and re-collect data or clean up messy records. That's months of time saved. Quality-aware scoring — an inspector takes a blurry photo in bad lighting. Instead of producing a bad score, the system down-weights that image. Clients trust the output even when field conditions aren't perfect. Gradual AI independence — this is a big one. You keep using OpenAI today, zero disruption to clients. But behind the scenes, your own model is running in shadow mode, proving itself. When it's ready, you switch. Your API costs drop and you own your intelligence. And asset history — a competitor can copy your model. They can reverse-engineer your scoring. But they cannot copy two years of condition history on 50,000 vehicles. That data advantage is permanent and it grows every day."

**Key points:**
- **Lead with the business line on each card.** If someone asks for technical detail, the muted text is your answer.
- **"Structured from day one"** — the CEO hears "no wasted work." Isaac hears "normalized storage, embeddings at ingest."
- **"Quality-aware"** — the CEO hears "reliable outputs." Isaac hears "blur/brightness/contrast weighting."
- **"Gradual AI independence"** — the CEO hears "lower costs, own our IP." Isaac hears "shadow → canary → graduated routing."
- **"Asset history = moat"** — this is the line the CEO takes to investors. "They can copy our model, they can't copy our data." Pause after this one.

**If Isaac asks for more technical depth:**
> "Happy to go deeper — the ingestion pipeline runs quality signals at ingest, we store CLIP embeddings in pgvector inside the existing Postgres, and the inference router logs both internal and external outputs during shadow mode. I can walk through the service topology if you'd like."

**If the CEO asks "how long until we own our own model?":**
> "The internal model enters shadow mode around week 5. By week 9, if we have enough labeled data, it's handling 10% of live traffic. Full graduation depends on data volume, but the architecture is designed so you're building toward it from day one — not starting from scratch later."

**Transition:** *"Let me show you how this system actually gets smarter over time."*

---

## Slide 7: How the System Gets Smarter

**This is what separates VeriBuy from every competitor. The compounding intelligence story.**

> "Most platforms score and forget. VeriBuy captures three signals that compound over time. First — expert labels. Domain experts review inspections and score six dimensions: paint, panels, glass, wheels, interior, mechanical. This teaches the model what 'good' and 'bad' actually look like in your domain. Second — real-world outcomes. A lender approves a loan. Six months later, the borrower defaults. That outcome flows back and tells VeriBuy: your score was too high. This is the signal competitors don't have. You can't get this from any API — it's unique to your pipeline. Third — corrections. When a human reviewer disagrees with a score, that correction gets captured and fed back. And here's the key metric: the rate of corrections decreasing over time is how you measure the model improving."

**Key points:**
- **Expert labels** — six-dimension taxonomy, locked before first annotation. Under the hood: Label Studio with inter-rater agreement tracking.
- **Real-world outcomes** — the killer differentiator. "This is the signal competitors don't have" — pause after this line.
- **Corrections** — the self-improving loop. Correction rate is a health metric the CEO can track.
- All three signals feed training — this is why the system gets better with every inspection.

**If asked "why not just use the API outputs as labels?":**
> "API outputs are predictions, not ground truth. You'd be training your model to replicate another model's mistakes. Human labels grounded in domain expertise, combined with real-world outcomes, give you a training signal that's actually tied to reality."

**Transition:** *"So the system is learning — but how do you actually move from paying for an external API to owning your own intelligence?"*

---

## Slide 8: Owning Your Intelligence Without Risk

**The three-stage rollout shows you think about risk management, not just building.**

> "You don't flip a switch from external API to internal model overnight. You earn it in three stages. Shadow — nothing changes for clients. Same API, same results. But behind the scenes, your internal model runs on every request silently. You compare its answers to the external API and measure the gap. Zero risk. Canary — still nothing visible to clients. But now 10% of requests use the internal model when it's confident enough. If anything looks off, you pull back instantly. Graduate — the internal model handles most traffic. The external API stays as a safety net. Your API costs drop, and you own the intelligence. The model itself is fine-tuned CLIP ViT-L/14 — we're not training from scratch, we're adapting a proven vision model to your domain."

**Key points:**
- **Frame it from the client's perspective** — "What clients see: nothing changes." This is about risk elimination.
- **Shadow = zero risk** — you get comparison data without affecting any client
- **Canary = controlled risk** — 10% with a confidence threshold, instant rollback
- **Graduate = earned trust** — the model proves itself before it takes over
- **CEO line:** "API costs drop and you own the intelligence" — that's an investor-ready line

**If asked "how long before the internal model replaces the API?":**
> "It depends on data volume. At 500 labels you get a baseline. At 2,000 you should be within 15% of the API. At 15,000, you should outperform it on in-domain asset types. The shadow mode data tells you exactly when you're ready — no guessing."

**Transition:** *"Once the system is scoring, here's what the client actually sees."*

---

## Slide 9: What the Client Actually Receives

**This is the client-facing surface. What insurers and lenders actually see and use.**

> "Not a black-box number. A full condition report they can defend to regulators, underwriters, and buyers. The condition breakdown gives a composite score — 1 to 100 — broken into dimensions. 'Body panels: 6.2 — dent on rear quarter panel.' Each dimension is weighted by how much it affects value. Structural issues tank the score; cosmetic ones don't. Every finding links to the actual photo with the problem area highlighted. The client can see exactly what the AI saw and why it scored that way. No guessing. The coverage report shows what was photographed and what wasn't — 'Front, rear, both sides captured. Engine bay and underbody: missing.' The client knows the gaps before making a decision. And everything has an audit trail — which model version scored it, what confidence level, whether it was routed internally or externally. Full traceability for regulated industries."

**Key points:**
- **Condition breakdown** — use the concrete example ("body panels: 6.2"). Makes it tangible.
- **Visual evidence** — clients see exactly what the AI saw. This builds trust.
- **Coverage report** — turns incomplete data into transparent reporting. Unique differentiator.
- **Audit trail** — regulated industries need this. It's not optional — it's what makes VeriBuy adoptable.

**If asked "what if the model is wrong?":**
> "That's exactly why we have human review workflows and the correction pipeline. When a reviewer corrects a score, that correction feeds back into training — that's slide 7's corrections signal. The correction rate decreasing over time is your proof the system is improving."

**Transition:** *"Of course, building this isn't just about architecture — there are real-world challenges."*

---

## Slide 10: Real-World Challenges

**Show you've thought about what actually goes wrong in the field, not just the happy path.**

> "Let me address the hard parts. Inspectors aren't perfect — photos will be blurry, poorly lit, missing angles. You can't control field conditions. So the system detects quality issues automatically and down-weights unreliable images instead of producing unreliable scores. Clients need results fast — dealers and auction houses need turnaround in minutes, not days. The pipeline processes photos as they're uploaded. By the time the last photo lands, the first ones are already scored. Every client integrates differently — insurers want PDF reports, lenders want API calls, marketplaces want embedded widgets. One scoring engine, multiple output formats. JSON, PDF, webhooks — no custom builds per client. And regulation — insurers can't use a tool they can't explain to regulators. So every score is decomposed into weighted dimensions with evidence. The math is visible."

**Key points:**
- **Quality weighting, not rejection** — pragmatic. In the real world you can't always get perfect photos.
- **Streaming pipeline** — first photos scored before last ones arrive. Speed matters for high-volume clients.
- **One engine, multiple outputs** — this is an architecture decision that saves months of custom work per client.
- **Regulation** — circle back to the audit trail from slide 9. It's all connected.

**Transition:** *"And I'd build all of this on the stack you already have."*

---

## Slide 11: Building on What Already Works

**Show you're not going to rewrite everything. You'll extend what exists.**

> "I wouldn't rewrite your stack. I'd extend it. Every addition has a clear reason. Python backend stays — I'd add a FastAPI service for the model. Same language your team already knows. Async, production-grade, easy to deploy alongside what exists. Supabase stays — I'd add the pgvector extension for image embeddings. It lives inside your existing Postgres. No new database, no new vendor, no migration. OpenAI stays — for now. I'd put an inference router in front of it. Today it passes everything through. Tomorrow it starts routing to your own model. Zero disruption. Cloud hosting stays — I'd add structured S3 storage for media and a message queue for the processing pipeline. This is how inspection data becomes training data."

**Key points:**
- **No new languages** — Python + JS, same as what they have
- **Supabase is Postgres** — pgvector is just an extension, not a new database
- **"OpenAI stays, for now"** — the inference router from slide 8 wraps existing calls. It's the same story.
- This slide shows you're pragmatic, not dogmatic about tech choices. The CEO hears "no expensive migration."

**Transition:** *"To get the model learning, we need labeled data. Here's how I'd bootstrap that fast."*

---

## Slide 12: Bootstrapping the Data Advantage

**Show you understand the cold start problem — and that the solution is also a business strategy.**

> "The model needs data before it can learn. Three paths running in parallel. First — label existing data. Every inspection from the current prototype gets run through the labeling tool. Two domain experts, a focused sprint, and you have over a thousand labeled images from data you already own. Second — multiply what you have. Each labeled photo generates multiple training variants: different lighting, angles, compression. The AI sees more diversity without anyone taking more photos. Third — and this is the highest-value path — partner for outcomes. Offer a regional insurer or lender free condition scoring on their historical backlog. In return, they share their decisions. Those real-world outcomes are 10x more valuable than manual labels because they're tied to real business decisions."

**Key points:**
- **Label existing data** — this is fast, not months of work. Use what you already have.
- **Synthetic augmentation** — standard ML technique, multiplies your dataset without additional collection.
- **Partner for outcomes** — this is a business strategy, not just engineering. The partner path is also a sales pipeline — you're demonstrating VeriBuy's value while building the dataset. Hit this with the CEO.

**Transition:** *"Let me tell you what I specifically bring to this."*

---

## Slide 13: What I Bring

**This is your direct sell. Be specific and confident.**

> "Here's why I think I'm the right person for this. I build end to end. API, database, frontend, deployment — I don't hand off between layers. One person who owns the pipeline from photo upload to PDF report means fewer gaps and faster iteration. I think in systems. Not just 'how does this service work' but 'how do seven services work together.' Data flow, contracts between pieces, what happens when one part fails. That's how you build something reliable. I ship, then improve. Working software in production beats perfect architecture on a whiteboard. Get the pipeline running. Measure real data. Iterate based on what you learn. That's how startups win. And most importantly — I get the real product. VeriBuy's value isn't the model. It's the decision system around it. The ingestion, the labeling, the scoring, the evidence, the feedback loop. I'd build the machine that makes the model useful."

**Key points:**
- **End to end** = you won't be blocked waiting for someone else
- **Systems thinking** = you design for the whole, not just your piece
- **Ship fast** = they're a startup, speed matters
- **"The machine that makes the model useful"** = directly echoes their job description ("think in terms of decision systems, not model accuracy alone")

**Transition:** *"So here's what success actually looks like."*

---

## Slide 14: What Success Looks Like

**Concrete outcomes, not a week-by-week schedule. Measured by results, not time.**

> "I don't want to give you a week-by-week schedule because the exact pace depends on what I find when I dig into the current codebase. But here's what success looks like. Near term — every new inspection is captured structured and training-ready. Quality issues are flagged automatically, not discovered in reports. The first internal model is running in shadow mode, measuring itself against the API. And your existing prototype data is labeled and feeding the pipeline. Medium term — the internal model is handling live traffic for proven asset types. Client-facing reports include full evidence and audit trail. Outcome feedback is flowing back from partner lenders and insurers. And API costs are dropping as the internal model takes over."

**Key points:**
- **Outcomes, not tasks** — "every inspection captured structured" is measurable. "Working on infrastructure" is not.
- **Near term vs medium term** — avoids committing to specific weeks but shows clear progression.
- **The insight line** — "every inspection makes the next one more accurate" — ties back to slide 2's compounding intelligence theme. It's the through-line of the whole presentation.
- **Soften if needed:** "The pace depends on what I find in the current codebase, but the milestones don't change."

**Transition:** *"And that brings me to the closing thought."*

---

## Slide 15: Let's Build This

**End strong. Short and memorable.**

> "The system that learns from every inspection is the product. Not the model. Not the API. The pipeline that captures data, trains intelligence, produces explainable scores, and feeds outcomes back into the loop. That's what compounds over time. That's VeriBuy's moat. And I'd love to be the one who builds it."

**Then pause. Let them respond.**

**Key points:**
- Echo the theme from slide 2 — "compounding intelligence"
- End on "I'd love to be the one who builds it" — direct, confident, not arrogant
- Don't ramble after this. Say it and stop. Silence is powerful.

---

## General Tips

- **If you don't know something, say so honestly.** "I'd need to dig into the current codebase to give you a precise answer, but my approach would be..."
- **Refer back to their docs.** "As you mentioned in the technical overview..." — proves you did your homework.
- **Keep answers concise.** Hit the key point, then stop. Don't over-explain.
- **If they ask about ML specifics you're unsure of**, pivot to the system: "I'd work with the ML engineer on the model architecture specifics, but what I'd own is the pipeline that feeds it data and makes its outputs useful."
- **If they ask "what would you do first?"** — "Day one, I'd get the ingestion API accepting photos and storing them structured. Everything else depends on that foundation."
- **The through-line** — slides 2, 7, 14, and 15 all reference "compounding intelligence." If you're ever unsure what to say, come back to: "every inspection makes the next one more accurate."
- **For Isaac (technical):** lean into the muted technical details on slides 6-8. He'll appreciate the architecture thinking.
- **For the CEO:** lean into the business framing — "API costs drop," "moat that grows," "partner path is a sales pipeline." These are investor-ready lines.
