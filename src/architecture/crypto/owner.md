## Owner keychain

When a vault is created for the first time, the `Seed` will be generated and owner will be able to 
keep the Mnemonic phrase also known as `Paper key`

Then a Master Key will be derivate from the Seed.
And for each device, a Child Key hardened will be generated using a random Uint32 index

Child Key will be used to create an identity for each Peers announced on the network.
Communication between peer will be encrypted using Child Key derivation.

The Relay will not be able to decrypt any exchange between peers.

* The Owner identification is made using **Master Public Key**
* The Peer Identification is made using **Child Public Key**