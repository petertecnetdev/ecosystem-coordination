# CLAIM — W06 Event Flyer Assistant

- worker: W06 / MediaForge
- priority: P1
- status: CLAIMED
- scope: `src/components/EventFlyerAssistant.js` and its dedicated media/editor behavior only
- points: W06-005, W06-006
- intent: remove hardcoded Brazilian locale/location assumptions from flyer rendering and replace visible Bootstrap Spinner loading with the Cutinapp Processing Indicator without touching W01 Event view files or W04 shared primitives.
- exclusions: EventViewPage/EventArtwork (W01 overlap), shared OptimizedImage primitives (W04 request), API/payment/auth.
- app head observed before claim: e5b9436de271c8594afdff715978947a2d211059
