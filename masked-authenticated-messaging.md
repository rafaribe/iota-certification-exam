# Masked Authenticated Messaging (MAM)

Is a layer 2 data communication protocol which allows the ability to emit and access encrypted data streams, over the tangle.
IOTA's consensus protocol adds integrity to these message streams.
Good for industries that need privacy and integrity of data.

Very Important: Channel ID == `address`

## How it works:

MAM uses a Merkle tree based signature scheme to sign the [cipher digest](https://stackoverflow.com/a/3332741/2298776)  of an encrypted message.
![MAM](https://miro.medium.com/max/2000/1*D5cI3pV3JBR5FqxwoKJs2w.jpeg "Masked authenticated messaging")

The root of the Merkle Tree is used as the ID of the channel. Since the tree only lasts for a short period of time, 
each message contains the root of the **next** Merkle tree.
Since previous trees are not referenced, this might be used to add a element of forward secrecy
to a channel.

Each message is encrypted with a [one time pad](https://www.wikiwand.com/en/One-time_pad#/Perfect_secrecy) that consists of the channel ID
and the index of the key used to sign the message.
The resulting cipher hash is signed using the PK bellonging to one of the leaves. 
The encrypted payload, the signature and the leaf's siblings are then published to the tangle where anyone knowing the symmetric key can find and decrypt it.

When consuming a MAM stream the message is first authenticated by validating the signature and verifying that the signature belongs to one of the tree's leaves, and then unmasked.
If the signature verification fails, the entire message is invalid.

## Privacy and Encryption modes:

- Public: everyone can view 
- Private: only you (i.e. seed owner) can view
- Restricted: you can specify your viewers by telling them a key. This key is named as sideKey in source code.
