import DocCardList from '@theme/DocCardList';

# cheqd

The cheqd module provides an integration with the cheqd network.

[cheqd](https://github.com/cheqd/sdk) is a blockchain network, built in the Cosmos ecosystem for Self-Sovereign Identity (SSI). The cheqd Network leverages the [cheqd DID method](https://docs.cheqd.io/identity/architecture/adr-list/adr-001-cheqd-did-method) and enables [DID-Linked Resources](https://docs.cheqd.io/identity/architecture/adr-list/adr-002-did-linked-resources) to be written to the network, associated with a DID and controlled using the verification methods in the DID Document.

Through this approach, the cheqd Network is able to natively support the [Ledger Agnostic AnonCreds Specification (v1.0)](https://hyperledger.github.io/anoncreds-spec/) through its [AnonCreds Object Method](https://docs.cheqd.io/identity/guides/anoncreds) (as well as VC-JWT and JSON-LD).

cheqd also has a dedicated token, $CHEQ, used for identity writes to the network, voting in a decentralized governance framework as well as for various payment flows between verifiers, holders and issuers of Verifiable Credentials.

## Module Installation

The cheqd module can be installed from the `@aries-framework/cheqd` package.

<!--tabs-->

# NPM

```bash
npm install @aries-framework/cheqd@^0.4.0
```

# Yarn

```bash
yarn add @aries-framework/cheqd@^0.4.0
```

<!--/tabs-->

### React Native

To enable React Native support we need to follow the steps below.

In the `package.json` file add the below code snippet, which replaces the `cosmjs` dependencies with the `cosmjs-rn` packages

<!--tabs-->

# NPM

Using [NPM `overrides`](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#overrides) we can point the `cosmjs` packages to `cosmjs-rn`.

```json
{
  "overrides": {
    "@cosmjs/amino": "npm:@cosmjs-rn/amino@^0.27.1",
    "@cosmjs/encoding": "npm:@cosmjs-rn/encoding@^0.27.1",
    "@cosmjs/math": "npm:@cosmjs-rn/math@^0.27.1",
    "@cosmjs/stargate": "npm:@cosmjs-rn/stargate@^0.27.1",
    "@cosmjs/tendermint-rpc": "npm:@cosmjs-rn/tendermint-rpc@^0.27.1",
    "@cosmjs/utils": "npm:@cosmjs-rn/utils@^0.27.1",
    "@cosmjs/proto-signing": "npm:@cosmjs-rn/proto-signing@^0.27.1",
    "@cosmjs/crypto": "npm:@cosmjs-rn/crypto@^0.27.1"
  }
}
```

# Yarn

Using [Yarn `resolutions`](https://classic.yarnpkg.com/lang/en/docs/selective-version-resolutions/) we can point the `cosmjs` packages to `cosmjs-rn`.

```json
{
  "resolutions": {
    "@cosmjs/amino": "npm:@cosmjs-rn/amino@^0.27.1",
    "@cosmjs/encoding": "npm:@cosmjs-rn/encoding@^0.27.1",
    "@cosmjs/math": "npm:@cosmjs-rn/math@^0.27.1",
    "@cosmjs/stargate": "npm:@cosmjs-rn/stargate@^0.27.1",
    "@cosmjs/tendermint-rpc": "npm:@cosmjs-rn/tendermint-rpc@^0.27.1",
    "@cosmjs/utils": "npm:@cosmjs-rn/utils@^0.27.1",
    "@cosmjs/proto-signing": "npm:@cosmjs-rn/proto-signing@^0.27.1",
    "@cosmjs/crypto": "npm:@cosmjs-rn/crypto@^0.27.1"
  }
}
```

<!--/tabs-->

create a `shim.js` file with the below code snippet

```typescript
import { Buffer } from '@aries-framework/core'
global.Buffer = Buffer
```

`import shim.js` at the top of your file where the React Native App is imported.

## Module Setup

After installing the dependencies, we can register the `CheqdModule` on the agent by adding the below code snippet to the agent constructor. The `CheqdModule` MUST always be registered if you're using any of the other services provided by the `@aries-framework/cheqd` package.

The following modules and services are exposed:

- `CheqdModule` - Registers the needed services to interact with the cheqd network.
- `CheqdDidResolver` - for resolving cheqd DIDs
- `CheqdDidRegistrar` - for creating, updating and deactivating cheqd DIDs
- `CheqdAnonCredsRegistry` - for resolving and registering AnonCreds schemas and credential definitions on the cheqd network.

```typescript showLineNumbers set-up-cheqd.ts section-1

```

### Configuration

#### `networks`

**Type**: `NetworkConfig[]`

An array of cheqd networks to connect to.

##### `networks[].network`

**Type**: `string`

The network to connect to. Either `mainnet` or `testnet`.

##### `networks[].cosmosPayerSeed`

**Type**: `string`

The32-bit seed value or a mnemonic. The payer seed can be managed outside of the agent using e.g. the Keplr wallet. To setup Keplr wallet for cheqd follow [this tutorial](https://learn.cheqd.io/getting-set-up-on-cheqd/cheqd-supported-wallets/keplr-wallet).

##### `networks[].rpcUrl`

**Type**: `string`

The RPC URL to use to connect to the cheqd network. Uses `https://rpc.cheqd.net` for `mainnet` and `https://rpc.cheqd.network` for `testnet` by default.

## Tutorials

- [Cheqd DID Module](../tutorials/chqed.md)
- [Register Schema and Credential Definition](../tutorials/registering-schema-and-credential-definition.md)
- [Issue a Credential](../tutorials/issue-a-credential.md)
