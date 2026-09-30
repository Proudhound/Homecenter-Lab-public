# Cameras and safety

## Principles
- camera footage and snapshots are never committed to Git
- existing vendor apps may remain as fallback
- battery-powered cameras should not be polled or streamed continuously without need
- access and alarm decisions are not delegated solely to an LLM
- physical camera placement and detailed security coverage remain private

## Integration goal
HomeCenter may expose high-level camera status, events or deliberately selected snapshots while retaining the underlying security system as an independent fallback.
