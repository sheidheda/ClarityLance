# ClarityLance

ClarityLance is a decentralized freelance payment escrow system built with Clarity smart contracts on the Stacks blockchain. This system facilitates milestone-based payments for freelance projects, ensuring secure transactions between clients and freelancers with a built-in dispute resolution mechanism. ClarityLance offers transparency, automation, and trust by locking funds until project milestones are completed and approved.

## Features

- **Project Creation**: Clients can create projects by defining total payment amounts, the number of milestones, and a dispute resolver.
- **Milestone Management**: Supports milestone-based payments, where clients fund each stage and approve payments upon completion.
- **Freelancer Acceptance**: Freelancers can accept projects to initiate work.
- **Dispute Resolution**: In case of a dispute, both parties can initiate dispute resolution, involving a pre-designated resolver for fair fund distribution.
- **Secure Escrow System**: Funds are locked until milestones are completed and approved, ensuring payment security for both parties.

## Smart Contract Overview

ClarityLance uses the following key components:

### Constants
- **`contract-owner`**: Owner of the contract, typically used for administration.
- **Error Codes**: Constants defining error codes, such as `err-owner-only`, `err-not-found`, and `err-insufficient-funds`, for smooth error handling.

### Data Structures
- **`projects` Map**: Stores details for each project, including the client, freelancer, total amount, milestone count, and status.
- **`milestones` Map**: Tracks milestone details for each project, such as the amount, description, status, and proof of completion.
- **`project-funds` Map**: Holds the balance and released amounts for each project.
- **`disputes` Map**: Stores dispute information, including the initiating party, reason, resolver fee, and resolution status.

### Key Functions

- **`create-project`**: Initializes a project with the total amount, milestone count, and dispute resolver.
- **`accept-project`**: Allows freelancers to accept projects, transitioning them to "in-progress."
- **`set-milestone`**: Enables clients to set milestones with specific amounts and descriptions.
- **`submit-milestone`**: Freelancers submit completion proof for each milestone.
- **`approve-milestone`**: Clients approve milestones, releasing funds to the freelancer.
- **`initiate-dispute`**: Clients or freelancers can initiate a dispute with a reason.
- **`resolve-dispute`**: Dispute resolvers manage the fund distribution based on agreed percentages.

## Getting Started

1. Clone the repository.
2. Install dependencies and set up the environment (e.g., Clarity, Clarinet).
3. Deploy the contract on the Stacks blockchain.
4. Use a compatible wallet to interact with the contract for testing.

### Prerequisites

- **Clarity Development Kit**: To compile and deploy Clarity smart contracts.
- **Clarinet**: For local testing and simulation.
- **Stacks Wallet**: For interacting with deployed contracts.

## Usage

1. **Project Creation**: A client creates a project by calling `create-project`, specifying the total project amount, milestone count, and dispute resolver.
2. **Freelancer Acceptance**: The freelancer accepts the project by calling `accept-project`.
3. **Milestone Submission and Approval**: For each milestone, the freelancer submits completion proof using `submit-milestone`, and the client approves it with `approve-milestone`.
4. **Dispute Initiation**: In case of a disagreement, either party can call `initiate-dispute`, providing the reason for dispute.
5. **Dispute Resolution**: The dispute resolver calls `resolve-dispute`, splitting funds according to the specified percentages.

## Example

Here’s an example flow:

1. **Create Project**:
   ```clarity
   (create-project "Website Development" u1000000 u3 tx-sender)
   ```

2. **Set Milestones**:
   ```clarity
   (set-milestone u1 u1 u300000 "Design Completion")
   ```

3. **Submit Milestone**:
   ```clarity
   (submit-milestone u1 u1 "Design Proof Link")
   ```

4. **Approve Milestone**:
   ```clarity
   (approve-milestone u1 u1)
   ```

5. **Initiate Dispute**:
   ```clarity
   (initiate-dispute u1 "Freelancer missed milestone deadline")
   ```

6. **Resolve Dispute**:
   ```clarity
   (resolve-dispute u1 u70 u30)
   ```

## Contributing

Contributions are welcome! Please fork the repository and submit pull requests for any enhancements or bug fixes.

## License

This project is licensed under the MIT License.

---
