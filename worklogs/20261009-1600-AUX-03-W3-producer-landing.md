# AUX-03 W3 Producer Conversion — Worklog

agent: AUX-03-W3
objective: Remove outdated commercial promises from the public producer landing and preserve the shortest route to first production.

## Confirmed
- `/for-producers` routes to `ProducerLandingPage`.
- Producer CTAs route to `/register` with `/production/create` as the destination and source attribution.
- Registration preserves that destination through email verification and records signup view/completion when a source is present.
- The current landing advertised a 30-day trial and producer subscription, but the central application configuration does not list Cutinapp subscription plans.

## Delivered
- Branch: `fix/producer-landing-monetization-truth`
- Commit: `2a973b85bd0de3180d9ff243b4e3dd394e5f8ded`
- Removed trial/30-day copy and changed CTAs to producer-action wording.
- Clarified the current model at a high level without inventing a fee amount.
- Preserved signup route and source keys.

## Validation
- Source check: no remaining `trial` or `30 dias` text in `ProducerLandingPage.js`.
- Source check: producer signup destination and acquisition source keys remain present.
- Build/runtime: not verified; commit has no CI checks yet.
- PR creation was blocked by the connected tool safety gate, so the change is committed on a feature branch but not merged.

## Metric
Primary: `producer_signup_completed` from `/for-producers`; activation outcome: `first_event_published`.

## Next action
W00/main account should open/review the feature PR, run CI/build, and only then arrange runtime validation. Do not treat the landing as published until the served SHA is confirmed.
