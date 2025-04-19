
# STX-DataForge - Data Marketplace Smart Contract

A decentralized, secure, and user-friendly smart contract for listing, purchasing, and managing digital data assets on the **Stacks blockchain**. This Clarity smart contract provides a complete ecosystem for data exchange with support for access control, reputation management, platform fees, and secure key delivery.

---

## ✨ Features

- **List Data Assets**: Users can create listings for data with detailed metadata and pricing.
- **Buy Assets**: Buyers can securely purchase data assets using STX tokens.
- **Access Control**: Purchased data can only be accessed by the rightful buyer.
- **Secure Key Storage**: Asset access credentials are stored in an encrypted off-chain-friendly format.
- **Marketplace Fees**: Admins can adjust a platform fee deducted from every transaction.
- **Reputation Tracking**: Sellers build their profile with every transaction.
- **Comprehensive Validation**: Extensive input checks to ensure contract stability and prevent misuse.

---

## 🚀 Getting Started

### Prerequisites

- [Clarity Language](https://docs.stacks.co/write-smart-contracts/clarity-smart-contracts)
- [Stacks Blockchain](https://www.stacks.co/)
- [Clarinet](https://docs.stacks.co/clarity-cli/clarinet-cli) (for testing and development)

### Deployment

1. Clone this repository.
2. Use Clarinet or your preferred tool to deploy the contract.
3. Ensure `marketplace-owner` is set as the deployer of the contract (`tx-sender` at deployment time).

---

## 📖 Contract Overview

### Constants

| Name                        | Description                                |
|----------------------------|--------------------------------------------|
| `marketplace-owner`        | The deployer/admin of the contract         |
| `marketplace-fee-percentage` | Fee % (e.g., 2% is represented by `u2`)     |

### Maps

- `data-asset-listings`: Stores all listed assets with metadata.
- `marketplace-user-profiles`: Tracks sales and reputation of users.
- `marketplace-transactions`: Logs purchases made by buyers.
- `data-access-credentials`: Links asset IDs to encrypted access keys.

### Variables

- `asset-id-counter`: Auto-increments asset ID for uniqueness.
- `total-marketplace-transactions`: Total purchases made.
- `marketplace-fee-percentage`: Percentage fee for each transaction.

---

## ⚙️ Public Functions

| Function | Description |
|---------|-------------|
| `create-data-asset-listing` | Lists a new data asset for sale |
| `purchase-data-asset` | Purchases an asset and transfers STX |
| `retrieve-asset-access-key` | Allows buyers to retrieve the key |
| `update-asset-price` | Allows the asset owner to update price |
| `deactivate-asset-listing` | Deactivates an asset listing |
| `update-marketplace-fee` | Admin-only: Updates the marketplace fee |

---

## 🔒 Access Control

- **Only sellers** can update or deactivate their listings.
- **Only buyers** can retrieve the encrypted access key.
- **Only the marketplace owner** can update the platform fee.

---

## 🧪 Read-Only Functions

| Function | Description |
|---------|-------------|
| `get-asset-listing-details` | View metadata for a specific asset |
| `get-user-profile` | View seller's reputation and stats |
| `get-total-marketplace-transactions` | View the number of successful transactions |
| `get-current-marketplace-fee` | View current marketplace fee percentage |

---

## 📌 Error Codes

| Error Code | Description |
|------------|-------------|
| `u100` | Unauthorized owner access |
| `u101` | Listing not found |
| `u102` | Asset already listed |
| `u103` | Insufficient STX balance |
| `u104` | Unauthorized transaction attempt |
| `u105` | Invalid asset price |
| `u106` | Invalid input parameters |

---

## 🔐 Security & Validation

- All user inputs are strictly validated:
  - Description, category, and access keys are non-empty and length-bound.
  - Asset prices must be greater than 0.
- Funds are transferred securely using `stx-transfer?`.
- Access keys are only revealed to verified buyers.

---
