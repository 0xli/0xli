
# Whitepaper: Decent Network × App/Web × Agents — System Architecture

Wei Li — [@0xWLi](https://x.com/0xWLi)  
[Decent Network](https://decent.network) · [Beagle Chat](https://beagle.chat)

> Audience: Founders / Technical Leaders / Investors  
> This paper focuses on needs, abstractions, and architecture—no implementation details.

---

## Abstract

In the AI + blockchain era, product delivery surfaces are primarily **App / Web / Agents**.  
The real moat comes from **reachability + unified identity/permissions + accessible storage/compute + agent interoperability interfaces**.

**[Decent Network](https://decent.network)** is communication-first. It builds an identity-driven reachable overlay on top of today’s internet, and on top of that enables storage and compute participation—supporting scalable collaboration across App/Web and Agents.

---

## 1. Problem: Why today’s internet is hostile to personal devices and the Agent ecosystem

### 1.1 The default worldview: C/S + IP/DNS
The mainstream internet relies on IP/DNS for addressing and is dominated by the client/server model. Most personal devices sit behind NATs/firewalls and are not reachable by default.

### 1.2 A one-way resource structure: “cloud-only”
When endpoints are not reachable, storage and compute are forced into the cloud:
- cost boundaries are dictated by cloud pricing  
- privacy and data boundaries are hard to define clearly  
- devices controlled by individuals/organizations cannot become usable resource nodes  

### 1.3 New hard requirements in the Agent era
As Agents become execution units for organizations, they need:
- independent identities and permission boundaries  
- access to data and compute (not only cloud, but also private/personal devices)  
- interoperability with external systems and other Agents (IM / API / CLI / Streams)  

Without a unified network layer, ecosystems fragment and devolve into piles of connectors/plugins.

---

## 2. Three-Layer Overview

### 2.1 Mermaid diagrams (GitHub-renderable: topology + node structure)

#### 2.1.0 Topology (Overlay = a DHT/P2P mesh formed by many L2 nodes)

```mermaid
flowchart LR
  %% Topology-style overlay. Many nodes, many links (DHT/P2P mesh).
  %% Keep labels short to avoid truncation in GitHub.

  subgraph L2NET["Decent Network Overlay (L2 mesh)"]
    direction LR
    N1(("L2-1"))
    N2(("L2-2"))
    N3(("L2-3"))
    N4(("L2-4"))
    N5(("L2-5"))
    N6(("L2-6"))
    N7(("L2-7"))
    N8(("L2-8"))

    %% mesh-ish links (conceptual)
    N1 --- N2
    N2 --- N3
    N3 --- N4
    N4 --- N5
    N5 --- N6
    N6 --- N7
    N7 --- N8
    N8 --- N1
    N2 --- N5
    N3 --- N6
    N1 --- N4
    N5 --- N8
  end

  %% Node types attach to some L2 instances (conceptual)
  A1["App Node"] --- N1
  A2["App Node"] --- N6
  W1["Web Node"] --- N2
  W2["Web Node"] --- N5
  G1["Agent Node"] --- N4
  G2["Agent Node"] --- N8

  %% Example traffic (conceptual)
  A1 -. "msg/call" .- G1
  G2 -. "event" .- W1
```

#### 2.1.1 Message/call path through the overlay (conceptual)

```mermaid
sequenceDiagram
  participant App as App Node
  participant L2A as L2 (local)
  participant Mesh as Overlay (DHT/P2P)
  participant L2B as L2 (remote)
  participant Agent as Agent Node

  App->>L2A: msg/call (identity-signed)
  L2A->>Mesh: discover + route (DHT)
  Mesh->>L2B: route/relay (as needed)
  L2B->>Agent: deliver to session
  Agent-->>App: response/event
```

#### 2.1.2 “Three layers = the structure of a node” (surface-to-carrier mapping)

```mermaid
flowchart TB
  subgraph NODE["Node = L3 (Surface) + L2 (Decent Network) + L1 (Carrier)"]
    direction TB
    L3["L3: App / Web / Agent"]
    L2["L2: SDK/Protocol<br/>(DHT • P2P • Identity)"]
    L1["L1: Carrier<br/>(Phone • PC • Server • VM)"]
    L3 --> L2 --> L1
  end

  MAP1["App Node = App + L2 + Phone"]
  MAP2["Web Node = Web + L2 + Server/VM"]
  MAP3["Agent Node = Agent + L2 + PC/Server/VM"]

  NODE --> MAP1
  NODE --> MAP2
  NODE --> MAP3
```

---

## 3. Glossary

- **Node**: a network participant—personal devices, private servers, or cloud nodes  
- **Identity**: a node’s unique identifier for discovery, connection, authorization, and audit  
- **Friend Network**: identity-based relationships and reachable paths  
- **Agent**: an identity-bearing digital executor (assistant/sales/support/dev) primarily operating in natural language  
- **Resource Node**: an accessible provider of storage/compute (personal devices / private servers / cloud)  
- **Streams / Events**: I/O channels for systems and Agents (IM/API/CLI/Webhook)

---

## 4. Layer 3: App / Web / Agents (user-facing surfaces)

### 4.1 App
Apps provide experience and reachability (sessions, messaging, notifications, media, and permission interactions).  
Example: [Beagle Chat](https://beagle.chat)

### 4.2 Web
Web provides distribution, operations, and ecosystem integration—fast iteration, external service integrations, and developer/admin workspaces.

### 4.3 Agents
Agents are GUI-less digital workers (assistant/sales/support/dev) with natural-language as the primary interface.  
Agents collaborate via **IM / API / CLI** and require unified identity, permissions, and resource-access boundaries.

---

## 5. Layer 2: Decent Network (communication-first)

[Decent Network](https://decent.network) is built to establish an **identity-reachable communication network**:
- discover/connect by identity, not by IP/DNS  
- make personal devices and private servers reachable nodes  
- provide unified semantics for communication, identity/permissions, and event streams for App/Web/Agents  

Architecturally it answers a core question:  
**“How can personal devices be reachable?”**  
Through identity-driven discovery, routing, and necessary relays, nodes become reachable on top of today’s internet and can participate in communication and collaboration.

---

## 6. Layer 1: Accessible Storage & Compute (Resource Nodes)

Once communication reachability is established, storage and compute no longer have to be cloud-only.  
Resource nodes can come from:
- **personal devices** (phones/PCs): participate in data and compute collaboration  
- **private servers/VMs**: host long-running Agents and services  
- **cloud nodes**: still useful, but no longer the only option  

Under unified identity/permissions semantics, App/Web/Agents can access these resource nodes—forming a mixed resource structure: **cloud + private + personal devices**.

---

## 7. Typical Workflow (Agent collaboration loop)

### 7.1 Mermaid workflow
```mermaid
sequenceDiagram
  participant A as Agent A
  participant N as Decent Network
  participant R as Resource Nodes
  participant B as Agent B / External Channel

  A->>N: Discover & connect by identity
  A->>N: Request permission / access scope
  N-->>A: Grant / deny + policies
  A->>R: Read data / invoke compute (via network reachability)
  R-->>A: Results / artifacts
  A->>B: Deliver outcome (IM / API / CLI)
  B-->>A: Feedback / next task
```

### 7.2 Text workflow (diagram-independent)
1) An Agent discovers and connects by identity  
2) It obtains data/compute access scope under unified permission semantics  
3) It accesses reachable storage/compute nodes (personal/private/cloud)  
4) It delivers outputs via IM/API/CLI and iterates with other Agents or external systems  

---

## 8. Use Cases

### 8.1 Founders: ship first, then scale the system
- surfaces: App / Web / Agents (pick one or combine)  
- needs: faster launch, lower long-term cost, easier multi-platform scaling  
- Decent Network provides: reachability + unified identity/permissions + accessible resource nodes  

### 8.2 Enterprises: make Agents “manageable digital employees”
- surfaces: sales/support/ops/dev Agents working over IM/API/CLI  
- needs: identity isolation, permission boundaries, auditability, controllable data/resources  
- Decent Network provides: unified identity/permissions semantics + event streams + accessible resources  

### 8.3 Developer ecosystem: interoperability for third-party Agents and apps
- surfaces: third-party Agents/tools integrating via IM/API/CLI  
- needs: interoperability, composability, orchestration, extensibility  
- Decent Network provides: communication + event streams as the ecosystem coupling layer  

---

## 9. Security & Governance (principles)

This paper states principles only (no implementation details):

- **Identity-first**: all access and collaboration is identity-scoped  
- **Permissioned access**: data/compute/asset access must be explicit and revocable  
- **Auditability by design**: critical actions can be logged and audited  
- **Least privilege**: minimal permissions by default; grant only what is needed  
- **Composable trust**: personal/private/cloud resources can be composed under unified semantics  

---

## 10. Conclusion

Decent Network makes **communication reachability** the foundation and turns storage/compute into accessible resources. This enables Apps/Web/Agents to collaborate under unified identity and network semantics—forming a rational architecture for the AI + blockchain era.

It supports:
- traditional App/Web delivery and long-term scaling  
- agent-native digital employee collaboration and ecosystem interoperability  
- a shift from cloud-only to **cloud + private + personal device** resource structures
