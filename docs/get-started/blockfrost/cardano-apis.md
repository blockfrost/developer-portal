---
id: cardano-api
sidebar_position: 3
title: Cardano API
sidebar_label: Cardano API
description: Cardano API
---

Blockfrost's primary objective is to offer API access to the Cardano ecosystem, encompassing not just the mainnet network, but also various testnet networks like preview and preprod.

## Cardano networks

Each distinct network not only needs its own `project_id` but also has a unique endpoint.

| Network                 | Endpoint                                        |
| ----------------------- | ----------------------------------------------- |
| Cardano mainnet         | `https://cardano-mainnet.blockfrost.io/api/v0/` |
| Cardano preview testnet | `https://cardano-preview.blockfrost.io/api/v0/` |
| Cardano preprod testnet | `https://cardano-preprod.blockfrost.io/api/v0/` |

## Your first request

Blockfrost is using <a href="https://en.wikipedia.org/wiki/Representational_state_transfer">REST</a>, which require you to request a specific endpoint. The API will then return the requested data, allowing you to process it according to your particular use case.

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs
defaultValue="curl"
values={[
{label: 'curl', value: 'curl'},
{label: 'JavaScript', value: 'js'},
{label: 'Other languages', value: 'others'},
]}>

<TabItem value="curl">

```bash
export BLOCKFROST_PROJECT_ID_MAINNET=mainnetdEI_YOUR_PROJECT_ID
curl -H "project_id: $BLOCKFROST_PROJECT_ID_MAINNET" https://cardano-mainnet.blockfrost.io/api/v0/epochs/latest
```

</TabItem>
<TabItem value="js">

```javascript
import { BlockFrostAPI } from "@blockfrost/blockfrost-js";

async function run() {
  const API = new BlockFrostAPI({
    projectId: "YOUR API KEY HERE",
  });

  try {
    const latestBlock = await API.blocksLatest();
    console.log(latestBlock);
  } catch (error) {
    console.error(error);
  }
}

run();
```

</TabItem>
<TabItem value="others">

There are over 15 different SDKs available for a variety of programming languages.

<ul>
<li><a href="https://github.com/blockfrost/blockfrost-js">blockfrost-js</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-haskell">blockfrost-haskell</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-python">blockfrost-python</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-rust">blockfrost-rust</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-go">blockfrost-go</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-ruby">blockfrost-ruby</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-java">blockfrost-java</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-scala">blockfrost-scala</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-swift">blockfrost-swift</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-kotlin">blockfrost-kotlin</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-elixir">blockfrost-elixir</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-dotnet">blockfrost-dotnet</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-arduino">blockfrost-arduino</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-php">blockfrost-php</a></li>
<li><a href="https://github.com/blockfrost/blockfrost-crystal">blockfrost-crystal</a></li>
</ul>
</TabItem>
</Tabs>

When executed correctly, you will receive a response in JSON format, resembling the following:

```json
{
  "time": 1641338934,
  "height": 15243593,
  "hash": "4ea1ba291e8eef538635a53e59fddba7810d1679631cc3aed7c8e6c4091a516a",
  "slot": 412162133,
  "epoch": 425,
  "epoch_slot": 12,
  "slot_leader": "pool1pu5jlj4q9w9jlxeu370a3c9myx47md5j5m2str0naunn2qnikdy",
  "size": 3,
  "tx_count": 1,
  "output": "128314491794",
  "fees": "592661",
  "block_vrf": "vrf_vk1wf2k6lhujezqcfe00l6zetxpnmh9n6mwhpmhm0dvfh3fxgmdnrfqkms8ty",
  "op_cert": "da905277534faf75dae41732650568af545134ee08a3c0392dbefc8096ae177c",
  "op_cert_counter": "18",
  "previous_block": "43ebccb3ac72c7cebd0d9b755a4b08412c9f5dcb81b8a0ad1e3c197d29d47b05",
  "next_block": "8367f026cf4b03e116ff8ee5daf149b55ba5a6ec6dec04803b8dc317721d15fa",
  "confirmations": 4698
}
```

To learn more about different endpoints, have a look at <a href="https://blockfrost.dev/">the official Blockfrost documentation</a>.
