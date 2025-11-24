# Pumpfun Smart Contract (Meteora Integration)

A Solana smart contract forked and customized from pumpfun (pump.fun), featuring bonding curve mechanics and integration with Meteora DEX for seamless token launches and liquidity migration.

## Overview

This project implements a complete token launch platform on Solana with:
- **Bonding Curve System**: Create and trade tokens through a bonding curve mechanism
- **Meteora Integration**: Automatic migration to Meteora DEX pools when bonding curve completes
- **Token 2022 Support**: Full compatibility with SPL Token 2022 standard
- **Metadata Support**: Integrated with Metaplex Token Metadata

## Features

### Core Functionality

- **Create Bonding Curve**: Launch new tokens with customizable parameters
- **Swap**: Buy and sell tokens through the bonding curve
- **Pool Migration**: Automatically create Meteora pools when bonding curve completes
- **Pool Locking**: Secure and finalize migrated pools
- **Admin Configuration**: Flexible configuration system for contract parameters

### Key Components

- Bonding curve mechanics for price discovery
- Automatic liquidity migration to Meteora DEX
- Team wallet management
- Global vault for token management
- Comprehensive error handling and events

## Program ID

```
B9kCGKJsUjFP3ej2JQY6bsLEaMNHpcF5TNVLrfZZbEqa
```

## Tech Stack

- **Framework**: Anchor (Solana)
- **Language**: Rust
- **Testing**: TypeScript/JavaScript with Mocha
- **Dependencies**:
  - Meteora SDK
  - Raydium SDK
  - Metaplex UMI
  - Solana Web3.js

## Prerequisites

- [Rust](https://www.rust-lang.org/tools/install) (latest stable version)
- [Solana CLI](https://docs.solana.com/cli/install-solana-cli-tools) (v1.18+)
- [Anchor](https://www.anchor-lang.com/docs/installation) (v0.30.1+)
- [Node.js](https://nodejs.org/) (v16+) and [Yarn](https://yarnpkg.com/)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/vladmeer/Pumpfun-Smart-Contract-All.git
cd pumpfun
```

2. Install dependencies:
```bash
yarn install
```

3. Build the program:
```bash
anchor build
```

## Development

### Build

```bash
anchor build
```

### Test

```bash
anchor test
# or
yarn test
```

### Lint

```bash
yarn lint
```

### Fix Linting Issues

```bash
yarn lint:fix
```

## Project Structure

```
pumpfun/
├── programs/
│   └── pump-all/
│       └── src/
│           ├── lib.rs                 # Main program entry point
│           ├── constants.rs           # Program constants
│           ├── errors.rs              # Custom error types
│           ├── events.rs              # Event definitions
│           ├── utils.rs               # Utility functions
│           ├── instructions/          # Instruction handlers
│           │   ├── admin/
│           │   │   └── configure.rs   # Admin configuration
│           │   ├── curve/
│           │   │   ├── create_bonding_curve.rs
│           │   │   └── swap.rs
│           │   └── migration/
│           │       ├── create_pool.rs
│           │       └── lock_pool.rs
│           └── state/                 # State accounts
│               ├── config.rs
│               ├── bondingcurve.rs
│               └── meteora.rs
├── Anchor.toml                        # Anchor configuration
├── Cargo.toml                         # Rust workspace config
├── package.json                       # Node.js dependencies
└── tsconfig.json                      # TypeScript config
```

## Usage

### Creating a Bonding Curve

```rust
pub fn create_bonding_curve(
    ctx: Context<CreateBondingCurve>,
    decimals: u8,
    token_supply: u64,
    virtual_lamport_reserves: u64,
    name: String,
    symbol: String,
    uri: String,
) -> Result<()>
```

### Swapping Tokens

```rust
pub fn swap(
    ctx: Context<Swap>,
    amount: u64,
    direction: u8,  // 0 = buy, 1 = sell
    minimum_receive_amount: u64,
) -> Result<u64>
```

### Migrating to Meteora Pool

```rust
pub fn create_pool(ctx: Context<InitializePoolWithConfig>) -> Result<()>
```

### Locking Pool

```rust
pub fn lock_pool(ctx: Context<LockPool>) -> Result<()>
```

## Configuration

The contract can be configured through the `configure` instruction, allowing updates to:
- Team wallet
- Fee structure
- Pool parameters
- Migration settings

## Networks

The program is configured for:
- **Mainnet**: `B9kCGKJsUjFP3ej2JQY6bsLEaMNHpcF5TNVLrfZZbEqa`
- **Devnet**: `B9kCGKJsUjFP3ej2JQY6bsLEaMNHpcF5TNVLrfZZbEqa`
- **Localnet**: `B9kCGKJsUjFP3ej2JQY6bsLEaMNHpcF5TNVLrfZZbEqa`

## Security

- Comprehensive input validation
- Access control for admin functions
- Secure account constraints
- Overflow protection enabled in release builds

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

- **GitHub**: [@vladmeer](https://github.com/vladmeer)
- **Telegram**: [@vladmeer67](https://t.me/vladmeer67)
- **Twitter**: [@vladmeer67](https://x.com/vladmeer67)

## Disclaimer

This software is provided "as is" without warranty. Use at your own risk. Always audit smart contracts before deploying to mainnet.

---

**Note**: This is a forked and customized version of the pumpfun smart contract with Meteora DEX integration for enhanced functionality.

