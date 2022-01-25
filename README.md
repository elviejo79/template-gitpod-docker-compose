# Setup a plutus development environment and connection to the testnet.

Using the docker virtual machines provided by input-output

We setup a devolpment environment with the following components

- Passive Cardano Node that is downloadnig a copy of the blockchain
- Cardano-node that is only used to query
- Plutus virtual machine

![Architecture](https://www.planttext.com/api/plantuml/png/JL7BJWCn3BpdAwozvmVsi2g52Y4k87f374nYTQscpYfnUa7yEqbs2vnYpup7Z-ooOj9o2SOeQo2uIsvc9QSbaJ4BkZEU28P7rYLwECYLKvGBYGxmPG3Uxp5vb6WbUle0pD22HhYDS84xNjy6luIY9SDRQqi9dbaxky9Di7LwUZXqWgjRXPkhdQe7ZE1HiK8jiLDdAlXQA35bGF5mJ2WPdNAKggiEOCjIfRLYX3qBTYKBa5mfn6KLsSIdMUsqZZA2MnTPKpjnRtEhDkRR61TYyJ3iGtHdDoDBkydlHOwKLMXTRujRaTdYVxD_DeDiUbRHcs04_LkaTZGx4b-_wWS0)


When you turn on this development environment.
You will see the cardano node updating with messages like this:

```sh
cardano-node_1        | [05bb8e0e:cardano.node.ChainDB:Info:5] [2022-01-25 03:53:01.79 UTC]Replayed block: slot 36525599 out of 48632936. Progress: 75.10%
cardano-node_1        | [05bb8e0e:cardano.node.ChainDB:Info:5] [2022-01-25 03:53:01.98 UTC] Replayed block: slot 36547116 out of 48632936. Progress: 75.15%
```

You just need to *wait until the node* has caught up with the tip of the blokchain.
And then use `cardano-cli` to query the node.

In order to run queries to the node you will use `caradano-cli` whichi is configured in the `cardano` container.

While the node is updating: `cardano-cli` would show an error `Socket.connect..: does not exist`
```sh
docker-compose run cardano cli query tip --testnet-magic 1097911063
--------
Creating template-gitpod-docker-compose_node_run ... done

cardano-cli: Network.Socket.connect: <socket: 11>: does not exist (No such file or directory)ERROR: 1
```

Once the `caradano-node` has caught up with the blockchain executing that same command will give you:

```sh

```

Now you can follow Plutus Transaction tutorial to know what you can execute.
