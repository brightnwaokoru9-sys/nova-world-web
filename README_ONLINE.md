NOVA WORLD — ONLINE DEVELOPMENT NOTES
Creator: Chidera Bright Nwaokoru

The browser client includes a WebSocket client and the package includes a Node/WebSocket server foundation. This connected build is configured for the deployed NOVA WORLD realtime backend at wss://nova-world-server-3.onrender.com. Keep server secrets out of the browser client.

The online foundation supports registration/login, presence, player positions, chat, NOVA Cash transfers, voice-note relay and travel state. The deployed server uses PostgreSQL for persistent player/account data.

For a public multiplayer launch, deploy the server, use HTTPS/WSS, add persistent storage, validate all economy operations server-side, add moderation/rate limits, and then set window.NOVA_SERVER_URL in config.js.
