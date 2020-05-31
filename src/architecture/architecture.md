# Architecture
[Architecture]: #architecture

## Table of Contents
[Table of Contents]: #table-of-contents

  - [Opening](#architecture)
  - [Table of Contents]
  - [Glossary]
  - [Clean Architecture]
    - [Service (Daemon)](/architecture/components/service-daemon.md)
    - [GUI-Flutter](/architecture/components/gui.md)
    - [Command Line Interface](/architecture/components/cli.md)

## Glossary
[Glossary]: #glossary

| Keyword      | Definition |
| ----------- | ----------- |
| Owner      | Owner represent a physical person that can have the same vault installed on many devices      |
| Vault   | Represet the PeerVault software installed on a device        |
| Relay | The relay are a server that will proxy the connection between two devices to avoid NAT issue |
| Seed | Represent the root key of an owner, used for rebuild any Owner master key. **use bitcoin BIP39** |
| Mnemonic or Paper Key| 12 words ASCII representation of a seed |
| Master Key | Key generate from a seed **use bitcoin BIP32** |
| Child Key | Key generate from a master key **use bitcoin BIP32** |
| LibP2P | It is the p2p library used to secure the exchange between peer |
| Peer | A Peer is a Vault connected to the network, listening through relay |
| QmPeerId | Represent unique ID of a Peer calculated from child key, used to announced peer on libp2p network |
| Key | Key as capital word represent a pair of private/public keys, like Master Key and Child Key |

## Clean Architecture
[Clean Architecture]: #clean-architecture

Clean Architecture is a well-known design that promotes loosely coupled application components to have better 
control and flexibility over time on each part.

First, we have two main components:

1. Human Interface (GUI or CLI)
2. Business Logic (SERVICE)

It can be kind of obvious for web developers but in the world of desktop applications it is not so much popular.
Split these two components gave us flexibility to choose different programming languages as well as ease the development 
of many Client UI without having to cope with all the complexity of business logic.

![PeerVault Daemon Architecture](/architecture-rfcs/images/peervault-soft-archi.png)
