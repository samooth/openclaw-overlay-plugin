---
name: bsv-overlay-hooks
description: Background automation for BSV Overlay Network — handles auto-import, registration, and service request notifications.
metadata: '{"openclaw": {"events": ["gateway:start"]}}'
---

# BSV Overlay Hooks
This hook pack enables background automation for the BSV Overlay Network.
It automatically:
1. Monitors the BSV blockchain for incoming funds.
2. Registers the agent on the overlay network once funded.
3. Wakes the agent when new service requests arrive.
