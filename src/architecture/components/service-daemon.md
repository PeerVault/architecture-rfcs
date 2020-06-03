## PeerVault-Service (Daemon)

All the business logic reside in the Service.

The daemon has been write with __GoLang__. Mainly because the underlying library __libp2p__ have the most advanced 
support with Go and was the only way to make it work the relay communication securely the for passing through NAT.

![PeerVault Daemon Architecture](/architecture-rfcs/images/peervault-soft-archi.png)

### Layers

The service are build on top of 3 layers:

#### 1. Communication
The Blue layer represent the communication, internal with the GUI or external with other Peer.

- Local API: Expose HTTP API to manipulate the Vault create or restore Owner, create or share Secret
- WebSocket Event: Instant notification to GUI when a new secret is shared by another Vault same or different Owner
- Peer LibP2P: Enable secure p2p channel with other Vault through libp2p2 Relay to pass through NAT


#### 2. Domain
The Yellow layer represent the internal Domain abstraction

- Owner: Identity of the Vault Owner, contain Master Key, Device Key, QmPeerId.
- Secret: Secret information, can have many format, Password, Document, Certificate, Private key...
- Exposure: Expose secret publicly on the computer, when mounting SSH Private key
- Backup: Able to export Vault DB encrypted, can only be restored by holding the Owner Master Key

#### 3. Persistence
The Red layer represent the persistent abstraction, we are using the bbolt key/value database
