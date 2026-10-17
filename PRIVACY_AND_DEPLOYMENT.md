# NOVA WORLD LIVE — Privacy + Deployment

## Data design
- Passwords are never stored in plain text; only scrypt password hashes are stored.
- The browser receives a signed session token but the token secret stays on the server.
- Player persistence is stored in PostgreSQL: character appearance, position/location, NOVA Cash, properties, vehicles, inventory and progression.
- Private messages are stored only for the messaging feature and are linked to account IDs.
- No microphone audio is stored by the database in this backend. Voice relay remains ephemeral between connected players.
- HTTPS/WSS should be used in production.
- Account deletion is supported through the WebSocket `delete_account` message and cascades stored messages.

## Production deployment
1. Deploy the `server/` service with a PostgreSQL database. `render.yaml` is included for Render Blueprint deployment.
2. The host supplies `DATABASE_URL` and generates `TOKEN_SECRET`.
3. Copy the resulting secure WebSocket endpoint (for Render this is `wss://<service>.onrender.com`).
4. Put that endpoint in `config.js` as `window.NOVA_SERVER_URL = "wss://...";`.
5. Upload the browser ZIP to itch.io as the HTML5 build. The database/server is NOT uploaded to itch.io; itch.io only serves the game client.
6. Test with two separate accounts on two devices/browser sessions before publishing the live build.

## Important
A static itch.io page cannot itself host the Node/WebSocket server or PostgreSQL database. The game client and backend are separate services.
