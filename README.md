# Project Name
ClusterCast (working title)
![image](https://github.com/user-attachments/assets/bfb38761-60d7-4228-b94d-0dbe9730cf3b)


## Project Description
A fully-on-chain, peer-to-peer live-video delivery network.  
Viewers pay independent relay nodes in **USDC on a high-throughput L2 (Base or MegaETH)**—with gas abstracted via account-abstraction paymasters—for every cryptographically-verified megabyte they receive.  
Merkle-chunk proofs and probabilistic micropayments (PMs) enforce honest delivery and fair compensation; no traditional CDN edge is required.  
Target end-to-end latency: **< 5 s**.

## Target Audience
- Independent streamers / e-sports casters  
- Event producers (webinars, conferences, concerts)  
- Viewers who want low-latency, censorship-resistant video  
- Home users or data-centres eager to earn by relaying  

## Desired Features
### Core P2P Protocol
- [ ] Live HLS/DASH segmentation (2 s default chunks)  
    - [ ] **Single 480p rendition** (~1.5 Mb/s H.264 + AAC)  
- [ ] WebRTC or QUIC transport between peers  
- [ ] DHT for chunk advertisement & peer discovery  
- [ ] Broadcaster-signed rolling Merkle roots (per 2 s window)  

### Smart-Contract Suite (Immutable, Apache-2.0)
- [ ] Deployed on Base or MegaETH (benchmark & choose)  
- [ ] `TicketBroker`-style PM contract (USDC)  
    - [ ] Deposit / withdrawal flows  
    - [ ] Configurable win probability & face value  
    - [ ] **Hard cap on viewer balances: US $50**  
- [ ] Relayer staking & slashing logic  
    - [ ] Fraud-proof submission window  
    - [ ] Penalty distribution / burn rules  
- [ ] **Account-abstraction paymaster**  
    - [ ] Users pay gas in USDC (not subsidised)  
- [ ] **Protocol treasury & paymaster wallets** secured by a **multi-sig
      (owner + core team)**  
- [ ] No upgrade proxy—code & state immutable at launch  

### Stream-Key NFTs
- [ ] Unlimited ERC-721 keys (one per broadcast slot)  
    - [ ] Transferable / rentable  
    - [ ] Metadata: title, category, max concurrent viewers  
    - [ ] On-chain royalty split → protocol treasury  

### Relayer Node Software
- [ ] Ingest, cache, and forward 480p chunks  
- [ ] Validate incoming PM tickets; batch winners  
- [ ] Automatic redemption batching (< $0.01 gas per call)  
- [ ] QoS reporting & reputation publishing (on-chain or via indexer)  
- [ ] **Minimum network spec**: uplink ≥ 5 Mb/s, downlink ≥ 10 Mb/s (TBD)  

### Viewer Player
- [ ] HTML5/JS player  
    - [ ] Merkle proof verification (WASM) per chunk  
    - [ ] Auto-blacklist misbehaving relayers  
- [ ] Wallet integration (MetaMask, WalletConnect, etc.) with paymaster flow  
- [ ] Real-time spend & bandwidth stats overlay  

### Broadcaster Tools
- [ ] OBS/FFmpeg plug-in for 480p encoding + chunk signing  
- [ ] Dashboard for Stream-Key NFT management & per-MB pricing  
- [ ] Stream health analytics (latency, peer count)  

### Incentive & Economics
- [ ] Baseline price per MB with optional surge pricing  
- [ ] Viewer tips to broadcaster  
- [ ] **Fee split between broadcaster & relayers — TBD**  
- [ ] Deposits & tips in USDC; gas abstracted  

### Security & Compliance
- [ ] Sybil-resistant staking minimum for relayers  
- [ ] DDoS / spam mitigation on contract calls  
- [ ] Balance caps per wallet to reduce regulatory exposure  
- [ ] GDPR alignment for any off-chain logs  

### Metrics & Monitoring
- [ ] On-chain stats explorer (TheGraph or equivalent)  
- [ ] Relayer performance leaderboard  

### DevOps & Deployment
- [ ] Target chain benchmarking: gas & throughput on Base vs MegaETH  
- [ ] CI/CD for contracts & node builds  
- [ ] Testnet and staging environments  

## Design Requests
- [ ] Visual identity (logo, colour palette)  
    - [ ] Should evoke decentralised broadcasting  
- [ ] Web dashboard UX mock-ups (dark & light modes)  
- [ ] Architecture & sequence diagrams for white-paper  

## Other Notes
- NAT traversal in hostile networks is a known risk  
- Mobile browsers may throttle WebRTC data-channels  
- Balance cap ($50) could interrupt long viewing sessions; need auto top-up prompts  
