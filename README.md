# DeVault

Decentralized Vault to Secure Digital Assets

---

## Overview

DeVault is a decentralized document storage and verification platform built on the Internet Computer Protocol (ICP). It provides a secure, tamper-proof, and censorship-resistant solution for storing, managing, and verifying critical documents. By leveraging ICP, IPFS, and Web3.Storage, DeVault ensures data integrity, availability, and user control.

---

## Key Features

- **Decentralized Storage:** Files are stored off-chain on IPFS, with metadata managed on the ICP canister.
- **Cryptographic Proof:** Each file is hashed client-side (SHA-256) for integrity and verification.
- **Decentralized Authentication:** Uses Internet Identity for secure, passwordless login.
- **Public Verification:** Anyone can verify a document's authenticity using its hash.
- **User Control:** Only file owners can access or delete their files.

---

## System Architecture

- **Frontend:** React SPA (Single Page Application) for user interaction, authentication, and file management.
- **Backend:** Motoko canister on ICP for business logic, metadata storage, and access control.
- **Storage:** IPFS/Web3.Storage for decentralized file storage.
- **Authentication:** Internet Identity for secure, device-based login.

**High-Level Flow:**
1. User authenticates via Internet Identity.
2. User uploads a file; the frontend hashes it and uploads it to IPFS.
3. The canister stores file metadata and the IPFS CID.
4. Users can verify files by hash or manage their own files.

---

## User Flow

1. **Login:** Authenticate with Internet Identity.
2. **Upload:** Select a file, which is hashed and uploaded to IPFS. Metadata is stored on-chain.
3. **Verify:** Enter a file hash to check its authenticity and metadata.
4. **Manage:** View, download, or delete your files from the dashboard.

---

## Project Structure

- `backend/src/devault_backend/main.mo` — Motoko canister logic
- `backend/src/devault_backend/types.mo` — Type definitions for the canister
- `frontend/src/main.jsx` — React frontend entry point
- `dfx.json` — DFINITY Canister SDK configuration
- `ARCHITECTURE.md` — Detailed architecture and system design
- `Excalidraw.md` — Visual diagrams of system flows

---

## Getting Started

1. **Clone the repository:**
   ```sh
   git clone https://github.com/DeVault-dev/DeVault.git
   cd DeVault
   ```
2. **Install DFINITY SDK:**
   - Follow instructions at https://internetcomputer.org/docs/current/developer-docs/cli-reference/dfx-tool/
3. **Install dependencies:**
   - For backend: (from project root)
     ```sh
     dfx deps install
     ```
   - For frontend:
     ```sh
     cd frontend
     npm install
     ```
4. **Start local development environment:**
   ```sh
   dfx start --background
   dfx deploy
   cd frontend
   npm start
   ```

---

## Documentation

- See `ARCHITECTURE.md` for a deep dive into system design and user flows.
- See `Excalidraw.md` for visual diagrams of the infrastructure and user journey.

---
