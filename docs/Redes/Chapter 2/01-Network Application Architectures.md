> [!IMPORTANT] Application Architecture
> Is designed by the application developer and dictates how the application is structured over the various end systems.

## Client-Server Architecture
- There is an always-on host, called the server, which services requests from many other hosts, called clients.
- Clients do not directly communicate with each other.
- The server has a fixed, well-known address, called an IP address. The clients can always contact the server by sending a packet to the server's IP address.

---

## P2P Architecture
- The application exploits direct communication between pairs of intermittenly connected hosts, called peers.
- Because the peers communicate without passing through a dedicated server, the architecture is called peer-to-peer.
- **Self-scalability**: Each peer also adds service capacity to the system by distributing files to other peers.

