**2022-05-05 Internal Training**

- [Topic 3: Substrate Runtime](#topic-3-substrate-runtime)
- [Topic 4: Running Node Template / Alt-producer together](#topic-4-running-node-template--alt-producer-together)
- [Topic 5: Polkadot JS API](#topic-5-polkadot-js-api)
- [Topic 6: Basic Code Walkthrough for Node Template / Alt Producer](#topic-6-basic-code-walkthrough-for-node-template--alt-producer)

<details>
  <summary>Table of Content</summary>

<!-- MarkdownTOC autolink="true" -->

- [Substrate Knowledge Map](#substrate-knowledge-map)
  - [Topic 0: Navigating Substrate Documentation](#topic-0-navigating-substrate-documentation)
    - [Additional resources](#additional-resources)
    - [Quiz #1](#quiz-1)
  - [Topic 1: Run & Interact with Substrate](#topic-1-run--interact-with-substrate)
    - [Set up your local development environment](#set-up-your-local-development-environment)
    - [Lab #1](#lab-1)
    - [Interact with a Substrate network using Polkadot-JS apps](#interact-with-a-substrate-network-using-polkadot-js-apps)
    - [Quiz #2](#quiz-2)
    - [Lab #2](#lab-2)
    - [Lab #3](#lab-3)
  - [Topic 2: Substrate Development Preliminaries](#topic-2-substrate-development-preliminaries)
    - [Rust](#rust)
    - [How blockchains work](#how-blockchains-work)
    - [Quiz #3](#quiz-3)
  - [Topic 3: Substrate Runtime](#topic-3-substrate-runtime)
    - [High level architecture](#high-level-architecture)
    - [Quiz #4](#quiz-4)
    - [Runtime development topics](#runtime-development-topics)
    - [Lab #4](#lab-4)
    - [Lab #5](#lab-5)
    - [Lab #6](#lab-6)
    - [Quiz #5](#quiz-5)
  - [Topic 4: Running Node Template / Alt Producer together](#topic-4-running-node-template--alt-producer-together)
  - [Topic 5: Polkadot JS API](#topic-5-polkadot-js-api)
    - [Quiz #6](#quiz-6)
    - [Lab #7](#lab-7)
    - [Interacting with Node Template / Alt-producer using Polkadot JS-API](#interacting-with-node-template--alt-producer-using-polkadot-js-api)
  - [Topic 6: Basic Code Walkthrough for Node Template / Alt Producer](#topic-6-basic-code-walkthrough-for-node-template--alt-producer)
  - [Topic 7: Smart contracts](#topic-7-smart-contracts)
    - [Quiz #7](#quiz-7)
  - [What we do not cover](#what-we-do-not-cover)
  - [Others](#others)
  - [Appendix](#appendix)
    - [Appendix 1: Terms clarification](#appendix-1-terms-clarification)
    - [Appendix 2: Smart Contract vs Runtime Development](#appendix-2-smart-contract-vs-runtime-development)

<!-- /MarkdownTOC -->

</details>

# Substrate Knowledge Map

The _Substrate Knowledge Map_ provides information for you to develop a non-trivial application in Substrate.

Each section contains basic information on each topic, with links to additional documentation for you to dig deeper.
Within each section, you'll find a mix of **quizzes** and **labs** to test your knowledge as your progress through the map.
The goal of the labs and quizzes is to help you consolidate what you've learned and put it to practice with some hands-on activities.

## Topic 0: Navigating Substrate Documentation

If you need any community support, please look for support on [Stack Overflow questions tagged with "substrate"](https://stackoverflow.com/questions/tagged/substrate) or [Substrate & Polkadot Stack Exchange](https://substrate.stackexchange.com/).

Use the following links to explore the sites and resources available on each:

[**Substrate Developer Hub**](https://docs.substrate.io/) has the most comprehensive
all-round coverage about Substrate, from a "big picture" explanation of architecture to specific technical concepts.
The site also provides tutorials to guide you as your learn the Substrate framework and the API reference documentation.
Check this site first if you want to look up information about Substrate runtime development.

The site consists of:

- [Knowledge Base](https://docs.substrate.io/v3): Explaining the foundational concepts of building blockchain runtimes using Substrate.

- [Tutorials](https://docs.substrate.io/tutorials/v3): Hand-on tutorials for developers to follow.
    **The first SIX tutorials show the fundamentals in Substrate and are recommended for every Substrate learner to go through.**

- [How-to Guides](https://docs.substrate.io/how-to-guides/v3): These resources are like the O'Reilly cookbook series written in a task-oriented way for readers to get the job done.
  Some examples of the topics overed include:

    - Setting up proper weight functions for extrinsic calls.
    - Using off-chain workers to fetch HTTP requests.
    - Writing tests for your pallets

- API docs

    - [latest stable version](https://paritytech.github.io/substrate/latest/sc_service/index.html)
    - [`master` branch](https://paritytech.github.io/substrate/master/sc_service/index.html)

- [Substrate Node Template](https://github.com/substrate-developer-hub/substrate-node-template) provides a light weight, minimal Substrate blockchain node that you can set up as a local development environment.

- [Substrate Front-end template](https://github.com/substrate-developer-hub/substrate-front-end-template) provides a front-end interface built with React using [Polkadot-JS API](https://polkadot.js.org/docs/api/) to connect to any Substrate node.

**Developers are encouraged to start new Substrate projects based on these templates**.

### Additional resources

- [**Polkadot Wiki**](https://wiki.polkadot.network/) documents the specific behavior and
mechanisms of the Polkadot network.
The Polkadot network allows multiple blockchains to connect and pass messages to each other.
On the wiki, you can learn about how Polkadot—built using Substrate—is customized to support inter-blockchain message passing.

- [**Polkadot JS API doc**](https://polkadot.js.org/docs/api/): documents how to use the Polkadot-JS API.
This JavaScript-based API allows developers to build custom front-ends for their blockchains and applications.
Polkadot JS API provides a way to connect to Substrate-based blockchains to query runtime metadata and send transactions.

### Quiz #1

👉 **Submit your answers to [Quiz #1](quizzes/01-overview.md)**

## Topic 1: Run & Interact with Substrate

### Set up your local development environment

Here you will set up your local machine to install the Rust compiler&mdash;ensuring that you have both stable and nightly versions installed.
Both stable and nightly versions are required because currently a Substrate runtime is compiled to a native binary using the stable Rust compiler, **then** compiled to a WebAssembly (WASM) binary, which only the nightly Rust compiler can do.

Also refer to:

- [Set up Substrate for Unix-based machines](https://docs.substrate.io/v3/getting-started/installation)
- [Set up Substrate for Windows](https://docs.substrate.io/v3/getting-started/windows-users)

### Lab #1

👉 **Complete [Lab #1: Run a Substrate node](labs/01-run-a-substrate-node.md)**

### Interact with a Substrate network using Polkadot-JS apps

[Polkadot JS Apps](http://polkadot.js.org/apps) is the canonical front-end to interact with any Substrate-based chain.

You can configure whichever endpoint you want it to connected to, even to your `localhost`
running node. Refer to the following two diagrams.

1. Click on the top left side showing your currently connected network:

![assets/01-polkadot-app-endpoint.png](./assets/01-polkadot-app-top-left.png)

2. Scroll to the bottom of the menu, open **DEVELOPMENT**, and choose either **Local Node** or **Custom** to specify your own endpoint.

![assets/02-polkadot-app-select-endpoint.png](./assets/02-polkadot-app-select-endpoint.png)

### Quiz #2

👉 **Complete [Quiz #2](quizzes/02-basics.md)**

### Lab #2

👉 **Complete [Lab #2: Using Polkadot-JS Apps](labs/02-polkadot-js-interaction.md)**

> **Notes**: If you are connecting Apps to a custom chain (or your locally-running node), you may
> need to specify your chain's custom data types in JSON under **Settings** > **Developer**.
>
> Polkadot-JS Apps only receives a series of bytes from the blockchain. It is up to the developer to
> tell it how to decode and interpret these custom data type. To learn more on this, refer to:
>
> - [Polkadot JS doc: Type basics](https://polkadot.js.org/docs/api/start/types.basics)
> - [Polkadot JS doc: Extending types](https://polkadot.js.org/docs/api/start/types.extend)

You will also need to create an account. To do so, follow these
[steps on account generation](https://wiki.polkadot.network/docs/en/learn-account-generation).
You'll learn that you can also use the [Polkadot-JS Browser Plugin](https://polkadot.js.org/extension/)
(a Metamask-like browser extension to manage your Substrate accounts) and it will automatically be
imported into Polkadot-JS Apps.

> **Notes**: When you run a Substrate chain in development mode (with the `--dev` flag), well-known
> accounts (`Alice`, `Bob`, `Charlie`, etc.) are always created for you.

### Lab #3

👉 **Complete [Lab #3: Create an Account](labs/03-create-account.md)**

## Topic 2: Substrate Development Preliminaries

You need to know some Rust programming concepts and have a good understanding on how blockchain technology works in order to make the most of developing with Substrate. The following resources will help you brush up in these areas.

### Rust

You will need to familiarize yourself with Rust to understand how Substrate is built and how to make the most of its capabilities.

If you are new to Rust, or need a brush up on your Rust knowledge, please refer to
[The Rust Book](https://doc.rust-lang.org/book/). You could still continue learning about
Substrate without knowing Rust, but we recommend you come back to this section whenever in doubt about what any of the
Rust syntax you're looking at means. Here are the parts of the Rust book we recommend you
familiarize yourself with:

- **ch 1 - 10**: These chapters cover the foundational knowledge of programming in Rust
- **ch 13**: On iterators and closures
- **ch 18 - 19**: On advanced traits and advanced types. Learn a bit about macros as well. You will not
  necessarily be writing your own macros, but you'll be using a lot of Substrate and FRAME's built-in macros to write
  your blockchain runtime.

### How blockchains work

Given that you'll be writing a blockchain runtime, you need to know what a blockchain is, and how it works.
The [**Web3 Blockchain Fundamental MOOC**](https://www.youtube.com/playlist?list=PLxVihxZC42nF_MCN9PTvZMIifRjx9cZ2J) Youtube video
series provides a good basis for understanding key blockchain concepts and how blockchains work.

The lectures we recommend you watch are: lectures 1 - 7 and lecture 10. That's 8 lectures, or about 4 hours of video.

### Quiz #3

👉 **Complete [Quiz #3](quizzes/03-rust.md)**

## Topic 3: Substrate Runtime

### High level architecture

To know more about the high level architecture of Substrate, please go through the Knowledge Base articles on
**[Getting Started: Overview](https://docs.substrate.io/v3/getting-started/overview)** and **[Getting Started: Architecture](https://docs.substrate.io/v3/getting-started/architecture)**.

In this document, you will develop a Substrate runtime with [FRAME](https://docs.substrate.io/v3/runtime/frame) (v2). This is what a Substrate node consists of.

![assets/03-substrate-architecture.png](./assets/03-substrate-architecture.png)

Each node has many components that manage things like:

- the transaction queue,
- communicating over a P2P network,
- reaching consensus on the state of the blockchain, and
- the chain's actual runtime logic (aka the blockchain runtime)

The runtime is particularly interesting because it contains the business logic (aka "state transition function") that codifies the chain's functionality. The runtime contains a collection of [pallets](https://docs.substrate.io/v3/runtime/frame) that are configured to work together.

On the node level, Substrate leverages [**libp2p**](https://libp2p.io/) for the p2p networking layer and puts the transaction pool, consensus mechanism, and underlying data storage (a key-value database) on the node level.
These components all work "under the hood", and in this knowledge map we won't cover them in detail except for mentioning their existence.

### Quiz #4

👉 **Complete [Quiz #4](quizzes/04-architecture.md)**

### Runtime development topics

In our [Developer Hub](https://docs.substrate.io/), we have a thorough coverage on various subjects you need to know to develop with Substrate.
So here we just list out the key topics and reference back to Developer Hub.
Please go through the following key concepts and the directed resources to know the fundamentals of runtime development.

- [**Key Concept: Runtime**](https://docs.substrate.io/v3/concepts/runtime), this is where the blockchain state transition function (the blockchain application-specific logic) is defined.
  It is about composing multiple pallets (can be understood as Rust modules) together in the runtimeand hooking them up together.

    - Developers can pick different pallets (modules) and composed them together to form your own runtimes. In this way you can extra functionalities easily to your runtime.
    - [code example](https://github.com/substrate-developer-hub/substrate-node-template/blob/596285acac52c9be4e6b575a15d13b455647e270/runtime/src/lib.rs#L261-L289) in node-template on how the pallet-sudo (with sudo functionality) is added to the runtime. Same for the Grandpa (block finalization logic)
    - So out from all Substrate pallets, you can pick the required pallets/logics and write your pallet and configure your own runtime.
        ![frame-runtimes](assets/04-frame-runtime.png)

- [**Runtime Development: Execution**](https://docs.substrate.io/v3/concepts/execution),
  this article describes how a block is produced, and how transactions are selected and executed
  to reach the next "stage" in the blockchain.

    How a block is born:

    1. Validate transactions
    2. Initializing a block (`on_initialize` hook is called)
    3. Executing extrinsics (where the pallet extrinsics are executed and event emitted)
    4. Finalizing a block (`on_finalize` hook is called)

- [**Runtime Develpment: Pallets**](https://docs.substrate.io/v3/runtime/frame),
  this article describes what the basic structure of a Substrate pallet is consists of.

    Basic stucture of a pallet

    ![Pallet Skeleton](./assets/05-pallet-skeleton.png)

    - the Configuration Trait (the interface that the runtime need to implement in order to include this pallet)
    - the Storage (data structure of the pallet)
    - the Event (events emitted by this pallet)
    - the Errors (errors that can be returned from this pallet)
    - Calls (external extrinsics (function calls) that users can call)

    Examples:

    - The simplest pallet: [Node template Template pallet](https://github.com/substrate-developer-hub/substrate-node-template/blob/main/pallets/template/src/lib.rs)
    - A production pallet: [Substrate Balances pallet](https://github.com/paritytech/substrate/blob/master/frame/balances/src/lib.rs)

### Lab #4

👉 **Complete [Lab #4: Adding a Pallet into a Runtime](labs/04-tutorial-add-a-pallet.md)**

- [**Runtime Development: Storage**](https://docs.substrate.io/v3/runtime/storage),
  this article describes how data is stored on-chain and how you could access them.

- [**Runtime Development: Events & Errors**](https://docs.substrate.io/v3/runtime/events-and-errors),
  this page describe how external parties know what has happened in the blockchain, via the emitted
  events and errors when executing transactions.

> **Notes**: All of the above concepts we leverage on the `#[pallet::*]` macro to define them in the
> code. If you are interested to learn more about what other types of pallet macros exist
> go to [the FRAME macro API documentation](https://docs.substrate.io/rustdocs/latest/frame_support/attr.pallet.html)
> and
> [this doc on some frequently used Substrate macros](https://docs.substrate.io/v3/runtime/macros).

### Lab #5

👉 **Complete [Lab #5: Building a Proof-of-Existence dApp](labs/05-poe.md)**

- [Writing Tests for Your Pallet](https://docs.substrate.io/v3/runtime/testing):
  learn to build up a mock runtime and write test cases for your pallet logics.

### Lab #6

👉 **Complete [Lab #6: Building a Substrate Kitties dApp](labs/06-substrate-kitties.md)**

### Quiz #5

👉 **Complete [Quiz #5](quizzes/05-runtime-development.md)**

## Topic 4: Running Node Template / Alt Producer together

Some usual commands:

- Compile and run substrate: `cargo build` (faster at build, slower at execution), `cargo build --release` (slower at build, faster at execution).

- Getting help: `./target/debug/node-template --help`.

- Running a single node:
    - temporarily (dev mode - chain data is removed upon termination): `./target/debug/node-template --dev`
    - as a single node: `./target/debug/node-template --alice --force-authoring`

    by default, chain data saved at: `~/.local/share/node-template/chains/local_testnet/db/full`

- Purge chain data: `./target/debug/node-template purge-chain`

- Running on 3-node network locally:

    ```bash
    ./target/debug/node-template --alice --tmp & \
    ./target/debug/node-template --bob --tmp & \
    ./target/debug/node-template --charlie --tmp

    # when you are done
    pkill <binary-name>
    ```

    or run each command at three terminals.

- Generating your own chainspec (chain configuration) and run the chain (this is how chain run in production):

    See reference of the tutorial [**Start a Private Network**](https://docs.substrate.io/tutorials/v3/private-network/).

    Let's use alt-producer at the following:

    ```bash
    # Build the chain spec file (chain configuration)
    ./target/debug/alt-producer build-spec --disable-default-bootnode --chain local > mySpec.json

    # Customized the `mySpec.json` as you see fit.

    # Generate the raw version of the chain spec
    ./target/debug/alt-producer build-spec --chain=mySpec.json --raw --disable-default-bootnode > mySpecRaw.json
    ```

    Now we pass the raw chainSpec to node validators. This file is also checked in to GitHub and is [publicly available](https://github.com/paritytech/polkadot/tree/master/node/service/res).

    Each node is run as follows:

    - node01

        ```bash
        ./target/debug/alt-producer \
          --base-path /tmp/node01 \
          --chain ./mySpecRaw.json \
          --port 30333 \
          --ws-port 9833 \
          --rpc-port 9933 \
          --validator \
          --rpc-methods Unsafe \
          --name node01
        ```

    - node02

        ```bash
        ./target/debug/alt-producer \
          --base-path /tmp/node02 \
          --chain ./mySpecRaw.json \
          --port 30344 \
          --ws-port 9844 \
          --rpc-port 9944 \
          --validator \
          --rpc-methods Unsafe \
          --name node02
        ```

    - node03

        ```bash
        ./target/debug/alt-producer \
          --base-path /tmp/node03 \
          --chain ./mySpecRaw.json \
          --port 30355 \
          --ws-port 9955 \
          --rpc-port 9955 \
          --validator \
          --rpc-methods Unsafe \
          --name node03
        ```

    We should see 2 peers are connected for each node console, and block should start getting generated and finalized.

- Generate a new account / keypair:

    It is in the sub-command: `./target/debug/node-template key`. See [reference at this docs](https://docs.substrate.io/v3/tools/subkey)

    - Generate a randomized account: `./target/debug/node-template key generate`

        You will see

        ```
        Secret phrase:       ocean still shine slice drop ship lecture member lion enroll try abstract
          Network ID:        substrate
          Secret seed:       0x803793e2cd71da0418553d842ccce81b5c0f6640ebcd78cdea6af7136db5da7e
          Public key (hex):  0x4c80c01961140284f84d057968f5c80d4ee5fd5ee27113964d0ea465149aa062
          Account ID:        0x4c80c01961140284f84d057968f5c80d4ee5fd5ee27113964d0ea465149aa062
          Public key (SS58): 5Do1k4Z1oHqELaGM6sYeeeVZ7HYUKnmFaLMRjEcRcnTGJWFt
          SS58 Address:      5Do1k4Z1oHqELaGM6sYeeeVZ7HYUKnmFaLMRjEcRcnTGJWFt
        ```

        **SS58 Address** is what we usually referred as the user account. Note even the public key is the same, there is a different SS58 address for different network.

    - Inspect for the same mnemonic/secret seed at Polkadot network:

      `./target/debug/node-template key inspect "ocean still shine slice drop ship lecture member lion enroll try abstract" --network polkadot`

    - Key generation supporting multiple scheme, the two usual ones are `ed25519`, and `sr25519`.

    - supports hard and soft hierarchical deterministic (HD) key derivation.

        - hard HD derivation for Alice: `./target/debug/node-template key inspect "ocean still shine slice drop ship lecture member lion enroll try abstract//alice"`
        - soft HD derivation for Alice: `./target/debug/node-template key inspect "ocean still shine slice drop ship lecture member lion enroll try abstract/alice"`

    - Use `--password` to generate password protected key

All the commands are (mostly) the same for both node-template and alt-producer.

## Topic 5: Polkadot JS API

[Polkadot JS API](https://polkadot.js.org/docs/api/) is the javascript API for Substrate. By using it you can
build a javascript front end or utility and interact with any Substrate-based blockchain.

The [Substrate Front-end Template](https://github.com/substrate-developer-hub/substrate-front-end-template)
is an example of using Polkadot JS API in a React front-end.

- [Runtime Development: Metadata](https://docs.substrate.io/v3/runtime/metadata),
  this article describes the API allowing external parties to query what API is
  open for the chain. Polkadot JS API makes use of a chain's metadata to know what queries and
  functions are available from a chain to call.

### Quiz #6

👉 **Complete [Quiz #6: Using Polkadot-JS API](quizzes/06-polkadot-js-api.md)**

### Lab #7

👉 **Complete [Lab #7: Using Polkadot-JS API](labs/07-polkadot-js-api.md)**

### Interacting with Node Template / Alt-producer using Polkadot JS-API

- Goto [Polkadot-JS Apps](https://polkadot.js.org/apps)
- Change the network on the top left to the local dev node
- Go through **Accounts** tab for accounts related feature
- Go through **Network** tab.
- Go through **Developer** tab.
    - **Chain State** to check the on-chain storage
    - **Extrinsics** to send transaction on-chain
    - **RPC Call** to make remote RPC call
    - **Sign and Verify** to sign and verify message by a certain user
    - **Sudo** make a certain transaction with sudo account (need to have `pallet-sudo` integrated)
    - **Javascript** run javascript

- Note that currently Polkadot-JS Apps doesn't

## Topic 6: Basic Code Walkthrough for Node Template / Alt Producer

[Substrate Node Template](https://github.com/substrate-developer-hub/substrate-node-template)

- on [node](https://github.com/substrate-developer-hub/substrate-node-template/blob/main/node/src/main.rs)
    - `cli.rs`
    - `command.rs`
    - `service.rs`
    - `rpc.rs`

- on [runtime](https://github.com/substrate-developer-hub/substrate-node-template/blob/main/runtime/src/lib.rs)
    - all `impl pallet_xxx::Config for Runtime` structure.
    - `construct_runtime!()` macro block

- on [`pallets/template`](https://github.com/substrate-developer-hub/substrate-node-template/blob/main/pallets/template/src/lib.rs)
    - notice the structure of `trait Config`, storage, events, errors, public extrinsics

[Alt Producer](https://github.com/alt-research/alt-producer)

- on [node](https://github.com/alt-research/alt-producer/tree/master/node)
    - the node will include components from `client`. Refer to [the node `Cargo.toml`](https://github.com/alt-research/alt-producer/blob/master/node/rpc/Cargo.toml)
- on [runtime](https://github.com/alt-research/alt-producer/tree/master/runtime)
- on pallets, an example is [`pallets/aggregator`](https://github.com/alt-research/alt-producer/tree/master/pallets/aggregator)
- on [primitives](https://github.com/alt-research/alt-producer/tree/master/primitives). These are the data structure frequently used within the chain, across pallets.

## Topic 7: Smart contracts

Learn about the difference between smart contract development vs Substrate runtime development, and
when to use each [here](https://docs.substrate.io/v3/runtime/smart-contracts#smart-contracts-vs-runtime-development).

In Substrate, you can program smart contracts using [ink!](https://paritytech.github.io/ink-docs).

- Learn about
  [smart contract development in Substrate](https://docs.substrate.io/v3/runtime/smart-contracts)
- Learn about
  [Smart contract development using ink!](https://docs.substrate.io/v3/runtime/smart-contracts#contracts-pallet)

### Quiz #7

👉 **Complete [Quiz #7: Using ink!](quizzes/07-using-ink!.md)**

## What we do not cover

A lot 😄

- On-chain runtime upgrades. We have a tutorial on
  [On-chain (forkless) Runtime Upgrade](https://docs.substrate.io/v3/runtime/upgrades).
  This tutorial introduces how to perform and schedule a runtime upgrade as an on-chain
  transaction.

- About [transaction weight and fee](https://docs.substrate.io/v3/runtime/weights-and-fees), and
  [benchmarking your runtime to determine the proper transaction cost](https://docs.substrate.io/v3/runtime/benchmarking).

- [Off-chain Features](https://docs.substrate.io/v3/concepts/off-chain-features)

  There are certain limits to on-chain logic. For instance, computation cannot be too
  intensive that it affects the block output time, and computation must be deterministic. This
  means that computation that relies on external data fetching cannot be done on-chain. In Substrate,
  developers can run these types of computation off-chain and have the result sent back on-chain via
  extrinsics.

- [Tightly- and Loosely-coupled pallets](https://docs.substrate.io/v3/runtime/pallet-coupling),
  calling one pallet's functions from another pallet via trait specification.

- [Blockchain Consensus Mechansim](https://wiki.polkadot.network/docs/en/learn-consensus), and a
  guide on customizing it to proof-of-work [here](https://docs.substrate.io/how-to-guides/v3/consensus/pow).

- [Parachains](https://wiki.polkadot.network/docs/en/learn-parachains): one key feature of
  Substrate is the capability of becoming a parachain for relay chains like Polkadot. You can develop your own
  application-specific logic in your chain and rely on the validator community of the relay chain
  to secure your network, instead of building another validator community yourself. Learn more
  with the following resources:

  - [Cross-chain Message Passing (XCMP)](https://wiki.polkadot.network/docs/en/learn-crosschain),
    how parachain and relay-chain communicate to each others
  - [Workshop: Using cumulus to build your parachain](https://docs.substrate.io/tutorials/v3/cumulus/start-relay)

## Others

- [Answers to quizzes and labs](https://github.com/substrate-developer-hub/hackathon-knowledge-map-ans)

## Appendix

### Appendix 1: Terms clarification

- **Substrate**: the blockchain development **framework** built for writing highly customized, domain-specific
  blockchains.
- **Polkadot**: Polkadot is the relay chain blockchain, built with Substrate.
- **Kusama**: Kusama is Polkadot's canary network, used to launch
  features before these features are launched on Polkadot. You could view it as a beta-network
  with real economic value where the state of the blockchain is never reset.
- **Web 3.0**: is the decentralized internet ecosystem that, instead of apps being centrally
  stored in a few servers and managed by a sovereign party, it is an open, trustless, and
  permissionless network when apps are not controlled by a centralized entity.
- **Web3 Foundation**: A foundation setup to support the development of decentralized web software
  protocols. Learn more about what they do [on thier website](https://web3.foundation/about/).

### Appendix 2: Smart Contract vs Runtime Development

**Smart Contract Development**

Traditional smart contract platforms allow users to publish additional logic on top of some core blockchain logic.
Since smart contract logic can be published by anyone, including malicious actors
and inexperienced developers, there are a number of intentional safeguards and restrictions built around these public smart contract platforms.
For example:

- **Fees**: Smart contract developers must ensure that contract users are charged for the computation and storage they impose on the computers running their contract.
With fees, block creators are protected from abuse of the network.

- **Sandboxed**: A contract is not able to modify core blockchain storage or storage items of other contracts directly.
Its power is limited to only modifying its own state, and the ability to make outside calls to other contracts or runtime functions.

- **Reversion**: Contracts can be prone to undesirable situations that lead to logical errors when wanting to revert or upgrade them.
Developers need to learn additional patterns such as splitting their contract's logic and data to ensure seamless upgrades.

These safeguards and restrictions make running smart contracts slower and more costly. However, it's important to consider the different developer audiences for contract development versus Substrate runtime development.

Building decentralized applications with smart contracts allows your community to extend and develop on top of your runtime logic without worrying about proposals, runtime upgrades, and so on.
You can also use smart contracts as a testing ground for future runtime changes, but done in an isolated way that protects your network from any errors the changes might introduce.

In summary, smart contract development:

- Is inherently safer to the network.
- Provides economic incentives and transaction fee mechanisms that can't be directly
  controlled by the smart contract author.
- Provides computational overhead to support graceful logical failures.
- Has a low barrier to entry for developers and enables a faster pace of community interaction.

**Substrate Runtime Development**

Unlike traditional smart contract development, Substrate runtime development offers none of the network protections or safeguards.
Instead, as a runtime developer, you have total control over how the blockchain behaves.
However, this level of control also means that there is a higher barrier to entry.

Substrate is a _framework_ for building blockchains, which almost makes comparing it to smart contract development like comparing apples and oranges.
With the Substrate framework, developers _can_ build smart contracts but that is only a fraction of using Substrate to its full potential.

With Substrate, you have full control over the underlying logic that your network's nodes will run.
You also have full access for modifying and controlling each and every storage item across your runtime modules.
As you progress through this map, you'll discover concepts and techniques that will help you to unlock the potential of the Substrate framework, giving you the freedom to build the blockchain that best suits the needs of your application.

You'll also discover how you can upgrade the Substrate runtime with a single transaction instead of having to organize a community hard-fork.
Upgradeability is one of the primary design features of the Substrate framework.

In summary, runtime development:

- Provides low level access to your entire blockchain.
- Removes the overhead of built-in safety for performance.
- Has a higher barrier of entry for developers.
- Provides flexibility to customize full-stack application logic.

> To learn more about using smart contracts within Substrate, refer to the
> [**Smart Contract - Overview**](https://docs.substrate.io/v3/smart-contracts/overview)
> page as well as the
> [Polkadot Builders Guide](https://wiki.polkadot.network/docs/build-build-with-polkadot#what-is-the-difference-between-building-a-parachain-a-parathread-or-a-smart-contract).
