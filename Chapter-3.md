# Resources

Account addresses in the Aptos blockchain can have data values associated with them, each keyed by their types. Only one value of each type can belong to an account. Generic types are allowed, with different instantiations treated as distinct types for extensibility. Mutating, deleting, and publishing values are governed by the module defining the data type. Move's safety rules prevent unauthorized access to data types defined in other modules. Wrapper types can be used to avoid limitations.

## Ledger State

From the perspective of the Move virtual machine (Move VM), each account comprises values and key-value data structures stored in the Binary Canonical Serialization format (BCS). This layout allows smart contracts to operate efficiently on both small and large data sets. Move modules are stored in an independent namespace similar to account data. The genesis ledger state defines the initial accounts and state. Aptos plans to scale up with more shards as adoption grows, maintaining on-chain assets for each shard.

# A Safe User Experience

To ensure widespread adoption, web3 must provide a safe and accessible user experience. The Aptos blockchain introduces innovations aimed at achieving this goal.

## 6.1 Transaction Viability Protection

Aptos safeguards users from unintentional or manipulated transactions with three key protections:
- **Sequence Number**: Each sender's account has a unique sequence number, ensuring a transaction can only be committed once.
- **Expiration Time**: Transactions have an expiration time, preventing their execution after a certain point.
- **Chain Identifier**: A designated chain identifier prevents malicious entities from replaying transactions across different blockchain environments.

## 6.2 Move-Based Key Management

Aptos accounts support key rotation and flexible custody models. Users can delegate key rotation to trusted entities through Move modules, enhancing security and enabling key recovery services.

## 6.3 Pre-signing Transaction Transparency

Aptos offers transparency by providing users with human-readable descriptions of transaction outcomes before signing. This, along with known attack histories and wallet-imposed constraints, enhances user protection against fraud and malicious applications.

## 6.4 Practical Light Client Protocols

Ensuring trust and data integrity between blockchain clients and servers is crucial. Aptos addresses this by offering state proofs and light client verification protocols that allow wallets and clients to verify data validity from untrusted third-party servers.

- **State Proofs**: Aptos provides state proofs that enable verification of data presented by third-party servers, enhancing data authenticity and integrity.
- **Timestamp-Based State Proofs**: Using timestamp-based state proofs, light clients can maintain up-to-date account state with tight bounds on freshness.
- **High-Performance Storage Interfaces**: Aptos nodes offer high-performance storage interfaces that can be tailored for subscriptions to specific data and accounts on-chain. This enables light clients to retain minimal verifiable data without running a full node or processing numerous transactions.

These protocols enhance security and trust in the Aptos blockchain, providing clients with reliable data and protecting against potential attacks.

