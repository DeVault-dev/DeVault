# DeVault - Visualized Flows (Excalidraw)

This document provides a visual representation of DeVault's infrastructure and user flows using Mermaid diagrams, corrected for syntax and improved for readability.

## 1. Infrastructure & Implementation Diagram

This diagram illustrates the technical components of the DeVault application and how they interact.

```mermaid
graph TD
    subgraph "User's Device"
        A["Browser: React Frontend"]
    end

    subgraph "Internet Computer"
        B["DeVault Canister (Motoko Logic)"]
        C["Internet Identity Service"]
        D["Canister Stable Memory (State)"]
    end

    subgraph "Decentralized Web"
        E["IPFS / Web3.Storage"]
    end

    A -- "1. Authenticates via" --> C
    C -- "2. Returns Principal" --> A
    A -- "3. Calls Canister Functions (store, get, verify)" --> B
    B -- "4. Reads/Writes State" --> D
    B -- "5. Manages Metadata (Hash, CID)" --> D
    A -- "6. Uploads/Downloads File Content" --> E
    B -.-> E
```

**Subtext:** The user interacts with the React frontend in their browser. Authentication is handled by Internet Identity. The frontend calls the main DeVault canister for business logic, which persists metadata in stable memory. The actual file content is stored on IPFS to ensure the canister remains lightweight and cost-effective.

---

## 2. User Flow: File Upload & Verification

This sequence diagram details the step-by-step process a user follows to upload a new file and how it can be verified. It has been expanded for clarity.

```mermaid
sequenceDiagram
    participant User
    participant Frontend as "React App"
    participant II as "Internet Identity"
    participant Canister as "DeVault Canister"
    participant IPFS as "IPFS/Web3.Storage"

    rect rgb(240, 248, 255)
        note over User, II: Authentication Flow
        User->>Frontend: 1. Clicks "Login"
        Frontend->>II: 2. Initiates auth flow
        II-->>User: 3. Prompts for authentication
        User-->>II: 4. Authenticates (e.g., biometrics)
        II-->>Frontend: 5. Returns authenticated Principal
    end

    %% Spacer
    User->>User: <br/>

    rect rgb(230, 255, 230)
        note over User, IPFS: File Upload Flow
        User->>Frontend: 6. Selects a file to upload
        Frontend->>Frontend: 7. Computes file's SHA-256 hash client-side
        note right of Frontend: Ensures data integrity before upload
        Frontend->>IPFS: 8. Uploads raw file content
        IPFS-->>Frontend: 9. Returns IPFS Content ID (CID)
        Frontend->>Canister: 10. storeFile(name, hash, size, CID)
        Canister->>Canister: 11. Validates user & stores metadata
        Canister-->>Frontend: 12. Returns success confirmation
    end

    %% Spacer
    User->>User: <br/>

    rect rgb(255, 250, 230)
        note over User, Canister: Verification Flow
        participant Verifier
        Verifier->>Frontend: 13. Enters file hash on Verify page
        Frontend->>Canister: 14. verifyFile(hash) (as a public query call)
        note left of Canister: Fast, read-only, and does not require consensus.
        Canister-->>Frontend: 15. Returns stored FileInfo if hash is found
        Frontend-->>Verifier: 16. Displays document's on-chain details
    end
```

**Subtext:** The flow begins with secure authentication. For uploads, the file is first hashed and stored on IPFS by the client, and only the resulting metadata (hash and CID) is sent to the canister. This makes the process efficient. Verification is a simple, fast, and public query using the file's hash.