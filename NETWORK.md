# Online rooms

Apex Kart is a static browser game and can run on GitHub Pages without a game server. The host creates a six-character room code; friends enter the code and join a private, eight-racer room. The host chooses the track and starts the race. New racers cannot join a race that has already begun. To race again, create a new room.

The game uses the open-source PeerJS client with its public signaling service. Signaling introduces browsers to one another; race positions and power-up messages travel over WebRTC data channels. The host relays messages between guests. A small ping/pong exchange estimates each guest's clock offset before the synchronized countdown. The host must keep the browser tab open. Leaving or losing the host ends the room; host migration is not implemented.

There are no hosting or account keys in the build. The public signaling service and Google STUN servers are external services, with no availability guarantee. There is no TURN relay: restrictive office/school networks, symmetric NATs, VPNs, firewalls, or blocked WebRTC may prevent a connection. The lobby reports a connection error in that case. Try a different network or use single-player. A production deployment that must connect on every network needs a separately operated signaling service and an authenticated TURN service.

This is casual peer-to-peer multiplayer. A host relays the roster, track, synchronized start, position updates, and item events. The client simulates its own kart; the game does not provide server-authoritative anti-cheat, accounts, public matchmaking, or global rankings. Unlocks are local browser progression. Display names and message sizes are bounded, but rooms should be shared with friends.

Run the site over HTTPS (GitHub Pages provides it) or localhost. WebRTC support is required; current desktop Chrome, Edge, and Firefox are recommended. Browser background throttling can disrupt a race, so all racers should keep the game visible.
