# Bitcoin Nexus Gaming Protocol

> A comprehensive Layer-2 gaming ecosystem built on Stacks, enabling Bitcoin-native NFT assets, competitive gaming, and decentralized rewards.

## Overview

Bitcoin Nexus creates an immersive gaming metaverse where players can mint unique NFT assets, build avatars, compete across virtual worlds, and earn Bitcoin rewards. The protocol leverages Stacks' smart contract capabilities to bring true ownership and value to gaming experiences while maintaining Bitcoin's security guarantees.

## Key Features

- **NFT Gaming Assets**: Mint unique assets with rarity tiers, power levels, and customizable attributes
- **Avatar Progression**: Level-based character development with experience points and achievements
- **Multi-World Gaming**: Create and explore virtual worlds with custom entry requirements
- **Competitive Leaderboards**: Skill-based rankings with Bitcoin reward distribution
- **Decentralized Ownership**: True asset ownership with peer-to-peer trading capabilities
- **Bitcoin Security**: Inherit Bitcoin's security through Stacks Layer-2 integration

## System Architecture

### Core Components

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   NFT Assets    │    │     Avatars     │    │  Game Worlds    │
│                 │    │                 │    │                 │
│ • Rarity System │    │ • Experience    │    │ • Entry Reqs    │
│ • Power Levels  │    │ • Leveling      │    │ • Active Players│
│ • Attributes    │    │ • Achievements  │    │ • Reward Pools  │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │  Leaderboard    │
                    │                 │
                    │ • Player Stats  │
                    │ • Rankings      │
                    │ • Rewards       │
                    └─────────────────┘
```

### Contract Architecture

The Bitcoin Nexus protocol is built as a single, comprehensive smart contract with modular functionality:

#### Data Layer

- **NFT Collections**: Two distinct NFT types (`nexus-asset`, `nexus-avatar`)
- **Metadata Storage**: Structured maps for assets, avatars, worlds, and leaderboards
- **Configuration Variables**: Protocol settings and counters

#### Business Logic Layer

- **Validation Functions**: Input sanitization and business rule enforcement
- **Experience System**: Level progression and experience calculation
- **Reward Distribution**: Bitcoin reward calculation and distribution logic

#### Access Control Layer

- **Admin Whitelist**: Protocol administrator management
- **Ownership Verification**: NFT ownership and transfer authorization
- **Safety Checks**: Principal validation and security measures

## Data Flow

### Asset Creation Flow

```
Admin → Validation → NFT Mint → Metadata Storage → Asset Counter Update
```

### Avatar Creation Flow

```
Player → Validation → Avatar NFT Mint → Leaderboard Entry → World Access Setup
```

### Experience Progression Flow

```
Admin → Experience Validation → Avatar Update → Level Check → Metadata Update
```

### Reward Distribution Flow

```
Admin → Player Validation → Score Calculation → Reward Distribution → Leaderboard Update
```

## Core Functions

### Asset Management

- `mint-nexus-asset`: Create new gaming assets with custom properties
- `transfer-game-asset`: Secure asset transfers between players

### Avatar System

- `create-avatar`: Initialize player avatar with world access
- `update-avatar-experience`: Progress avatar through experience gains

### World Management

- `create-game-world`: Deploy new gaming environments
- `get-world-details`: Retrieve world information and stats

### Competitive Features

- `update-player-score`: Record competitive gaming results
- `distribute-bitcoin-rewards`: Automated reward distribution to top players

## Technical Specifications

### NFT Standards

- **Asset NFTs**: Unique gaming items with metadata
- **Avatar NFTs**: Player identity tokens with progression data

### Experience System

- **Max Level**: 100 levels per avatar
- **Experience Cap**: 1,000 XP per level
- **Base Requirement**: 100 XP for first level

### Validation Rules

- **Names**: 1-50 ASCII characters
- **Descriptions**: 1-200 ASCII characters
- **Rarity Tiers**: common, uncommon, rare, epic, legendary
- **Power Levels**: 1-1,000 range
- **Attributes**: 1-10 custom attributes per asset

### Security Features

- **Admin Controls**: Whitelist-based administration
- **Input Validation**: Comprehensive parameter checking
- **Ownership Guards**: NFT ownership verification
- **Safe Transfers**: Protected asset movement

## Deployment

### Prerequisites

- Stacks blockchain access
- Clarity smart contract deployment capability
- Protocol administrator wallet

### Initialization

1. Deploy the contract to Stacks blockchain
2. Call `initialize-protocol` with desired fee and entry settings
3. Create initial game worlds using `create-game-world`
4. Begin asset minting and player onboarding

### Configuration

- **Protocol Fee**: 1-1,000 range (default: 10)
- **Max Leaderboard Entries**: 1-500 range (default: 50)
- **Admin Whitelist**: Configurable administrator access

## Integration

### Frontend Integration

Connect to the protocol using Stacks.js library:

```javascript
// Example integration
import { StacksMainnet } from '@stacks/network';
import { callReadOnlyFunction } from '@stacks/transactions';

// Read avatar details
const avatarDetails = await callReadOnlyFunction({
  contractAddress: 'CONTRACT_ADDRESS',
  contractName: 'bitcoin-nexus',
  functionName: 'get-avatar-details',
  functionArgs: [uintCV(avatarId)],
  network: new StacksMainnet()
});
```

### Game Engine Integration

- Connect game events to experience updates
- Implement score reporting for competitive modes
- Handle asset ownership verification
- Manage world access controls

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contributing

Contributions are welcome! Please read our contributing guidelines and submit pull requests for any improvements.
