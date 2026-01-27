### Revolutionizing the Rules of Social Networking: The Decent Network Thesis

In an era of centralized social platforms that harvest data, manipulate feeds, censor content, and lock users into corporate clouds, **Decent Network** offers a foundational shift: a device-centric, peer-to-peer (P2P) protocol that makes social feel like real life—direct, unmediated, and user-controlled.

Visit https://decent.network for the protocol overview and https://beagle.chat for a live example app (native Web3 messenger with P2P E2EE messaging, audio/video calls, offline support, wallet identity, omni-chain assets, token-gated meetings, Nostr Moments, and growing community: 16K+ members, 2K+ downloads).

#### The Core Problem
Web2 social relies on client-server clouds → privacy erosion, algorithmic addiction, fragility, and over-reliance on intermediaries that deviate from natural human interaction.

SocialFi (Farcaster, Lens, etc.) layers features on existing chains but often falls into over-financialization, misaligned incentives (speculation > utility), poor UX, and the same **network effects trap** Vitalik Buterin highlighted: entrenched platforms win because everyone’s already there. He urges starting from genuine social primitives, not crypto bolt-ons. Suji Yan pushes gradual hybrid migration with wallet/AI/governance integrations.

The fix isn’t better apps on chains—it’s a **base-layer protocol revolution** for social coordination, parallel to how blockchain disrupted finance.

#### Decent Network: The Friend Network as Foundational Primitive
Decent Network builds one unified **Friend Network** using DHT (Distributed Hash Table) for decentralized discovery and routing—proven, permissionless, and device-native.

- **Identity** = public key (self-generated, portable; no usernames tied to platforms).
- **Relationships** = explicit, mutual friendships forming network-native ACLs (access control lists). Strangers can’t message by default → anti-spam built-in.
- **P2P Connectivity** = direct device-to-device via multiple transports (WebRTC, QUIC, etc.), NAT traversal (ICE), and a decentralized pubkey directory. No central servers needed for core ops.
- **Messages** = end-to-end encrypted, permissioned peer-to-peer (one-to-one or group via friends).
- **Events** = ephemeral multicast/broadcast primitives native to the Friend Network:
  - When online, users broadcast mutable presence info (configurable visibility): online/offline status, display name, avatar, self-introduction, optional location/IP (limited to close friends for privacy).
  - Events propagate via gossip to authorized viewers (friends via multicast; optionally broadcast to everyone/strangers per user settings).
  - Updates anytime by the user.
  - **Crucially ephemeral**: Only broadcast while online. Offline → no events/presence visible in the network. Mirrors real-life: you’re “there” only when participating.

This makes the network “alive” with real-time visibility and coordination—without persistent cloud storage or intermediaries. Layers add storage (offline files), data access (indexing/queries), and intelligence (AI inference/hooks).

Beagle Chat demonstrates this in production: P2P messaging/calls, wallet-based sovereign identity (SOL/EVM), offline queuing, token incentives, and more—all powered by the Friend Network primitives.

#### Why This Matters for SocialFi
Current SocialFi builds houses on financial concrete. Decent Network invents the right “concrete” for social: device-first P2P substrate where:
- Privacy is default (local/encrypted data, user-controlled sharing).
- Resilience scales naturally (P2P load distribution, no single-point failures).
- Incentives align with utility (e.g., micro-rewards for trusted relaying, not speculation).
- Network effects can compound: portable pubkey identity + friend graphs migrate across apps.

#### Overcoming Network Effects (The Hard Part)
Vitalik’s #1 barrier is real. Decent counters it:
- **Developer-first bootstrapping**: Simple TypeScript SDK → embed P2P social into wallets, DeFi, AI agents, or Web2 apps as “Trojan horses.”
- **Gradual/hybrid paths**: Start in niches (privacy/crypto communities, censored regions); bridge to X/Telegram; viral QR/NFC friend invites leveraging real-world proximity.
- **Utility flywheel**: Tangible wins (own your graph, no surveillance, direct comms) drive organic growth over hype.
- **Open collaboration**: Hackathons, grants, pilots to educate and onboard.

#### Call to Action
Decent Network isn’t another app—it’s the missing base layer SocialFi needs: permissionless, pubkey-addressed, friend-bound P2P communication where events and messages flow directly between devices.

Explore → https://decent.network  
Try Beagle Chat → https://beagle.chat  
Code/docs → https://github.com/0xli/0xli  
Follow @0xWLi for updates.

Builders & users: join the revolution. Let’s make social decentralized, authentic, and truly ours. 🚀
