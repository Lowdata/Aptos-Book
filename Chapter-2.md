# Logical Data Model

The ledger state of the Aptos blockchain represents the state of all accounts and is versioned using an unsigned 64-bit integer indicating the number of executed transactions.

## Transactions

A signed transaction includes:

- **Transaction Authenticator**: One or more digital signatures for authentication.
- **Sender Address**: The sender's account address.
- **Payload**: Refers to an existing entry function or contains inlined bytecode (a script) with input arguments.
- **Gas Price**: The sender's payment per unit of gas for computation, networking, and storage.
- **Maximum Gas Amount**: The maximum gas units allowed for the transaction.
- **Sequence Number**: Transaction sequence matching the sender's account.
- **Expiration Time**: Timestamp for transaction validity.
- **Chain ID**: Identifies the blockchain for transaction validation.

Each version i of the ledger state includes a tuple (Ti, Oi, Si) containing the transaction, transaction output, and resulting ledger state, produced by a deterministic function Apply(Si−1, Ti) → ⟨Oi, Si⟩.

### Events

Events are emitted during transaction execution, defined by Move modules. Events are stored in the ledger and can be queried through an Aptos node. Events have unique keys for querying event details. Multiple events with the same key create event streams, each with a type and data.

Transactions can generate events but cannot read them, ensuring transaction execution depends solely on the current state and inputs.

## Accounts

Each account is identified by a unique 256-bit account address. Accounts are created when a transaction from an existing account invokes the create_account(addr) Move function or through implicit creation when Aptos tokens are transferred to a nonexistent account.

To create an account, a user generates a signature key-pair (vk, sk), deriving the account address addr with the cryptographic hash H(vk, ssid), where ssid is the signature scheme identifier.

Accounts are not linked to real-world identities, and users can create multiple accounts for pseudonymity. Multiple accounts by a single user offer concurrency channels for execution.
Accounts controlled by the same user have no inherent link to each other, providing pseudonymity. However, a user can manage multiple accounts within a single wallet for simplified asset management. This flexibility ensures user privacy while allowing for experimentation with privacy-preserving features in future releases.

Multiple accounts owned by a single user or a set of users also serve as channels to increase execution concurrency
