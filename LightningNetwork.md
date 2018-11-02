# Lightning Network and BTCPay

After deploying BTCPay Server, as a merchant, you may want to experiment with an innovative second-layer payment system built on top of Bitcoin protocol - the [Lightning Network](https://en.bitcoin.it/wiki/Lightning_Network).

This guide will show you how to set up your Lightning Network node in BTCPay and guide you through some basics.

<strong>Before you proceed, please understand that Lightning Network is still in the experimental stage. Do not put the money you can't afford to lose. There is a high risk of you losing the money. </strong>

Take time to familiarize yourself with the risk. <strong>There's no backup for LND or c-lightning keys in BTCPay. Your keys are in a hot-wallet</strong>. This means :

1. If you erase your BTCPay Server or your machine crashes - you lose all the funds.
2. If your server gets hacked - a hacker can take all of your funds by accessing your keys.

While the keys from your Lightning Network don't have a backup and someone can steal them theoretically, your on-chain Bitcoin funds are safe and are never uploaded on the server.

As the technology matures and develops, things like a proper backup will be easier to implement in BTCPay.

BTCPay currently offers two implementations of the Lightning Network:

* [LND](https://github.com/lightningnetwork/lnd)
* [c-lightning](https://github.com/ElementsProject/lightning)

## Choosing the Lightning Network implementation

On the installation, you'll have the option to choose the implementation. For [web-interface installations](https://medium.com/@BtcpayServer/launch-btcpay-server-via-web-interface-and-deploy-full-bitcoin-node-lnd-in-less-than-a-minute-dc8bc6f06a3), you can simply select the implementation from the drop-down menu. For [docker](https://github.com/btcpayserver/btcpayserver-docker) you need to :

```
sudo su -
cd btcpayserver-docker
export BTCPAYGEN_LIGHTNING="implementationgoeshere"
. ./btcpay-setup.sh -i
```

For c-lightning use `export BTCPAYGEN_LIGHTNING="clightning"`
For LND use `export BTCPAYGEN_LIGHTNING="lnd"`

To begin using Lightning, your blockchain needs to be fully synced.

## Connecting your internal Lightning Node in BTCPay

Regardless of the implementation (c-lightning or LND) you've decided to use, the process of connecting your internal Lightning Node in BTCPay Server is the same.

1. If you do not have a store, create one. 
2. Store Settings > General Settings > Lightning Network Experimental (located at the bottom of the page, scroll)
3. Under Crypto tab, select cryptocurrency > Modify.
4. At the next page, at the bottom under "connection string", click on the "click here" link. Your node information will be automatically added.
5. Enable. Submit.
6. Test Connection.

<strong> Your blockchain needs to be fully synced before you try to connect your Lightning Node, otherwise the connection will fail.</strong>

![LightningNetworkSettup1](img/LightningNetworkNodeSetup1.jpg)

![LightningNetworkSettup2](img/LightningNetworkNodeSetup2.jpg)

![LightningNetworkSettup3](img/LightningNetworkNodeSetup3.jpg)

![LightningNetworkSettup4](img/LightningNetworkNodeSetup4.jpg)


## Getting Started with BTCPay and LND

The easiest way to use LND implementation with BTCPay is to use [Zap wallet integration](https://github.com/LN-Zap/zap-tutorials/blob/master/zap-desktop-btcpay-server.md).

[![LNDBTCPay](https://img.youtube.com/vi/CWhTOunTb2Q/mqdefault.jpg)](https://www.youtube.com/watch?v=CWhTOunTb2Q "BTCPay - LND and Zap")

### LND Commands lncli

You can use lncli commands like described in their [API docs](https://api.lightning.community/) but instead of using lncli you use the shell script in of the btcpayserver-docker repository calles bitcoin-lncli.sh.

If you're on Docker make sure you're in docker directory.
```
sudo su -
cd btcpayserver-docker
./bitcoin-lncli.sh
```
So instead of running lncli getinfo you would run `./bitcoin-lncli.sh getinfo`

Run `./bitcoin-lncli.sh --help` to see a full list of commands or check above mentioned API docs.

## Getting Started with BTCPay and c-lightning

### c-lightning Commands lightning-cli

To use clightning CLI it is the same like above for `lncli` but instead you use the shell script `bitcoin-lightning-cli.sh`

If you're on Docker make sure you're in docker directory.

```
sudo su -
cd btcpayserver-docker
./bitcoin-lightning-cli.sh
```
E.g. to list all commands: `./bitcoin-lightning-cli.sh help`
or show info about the node `./bitcoin-lightning-cli.sh getinfo`
