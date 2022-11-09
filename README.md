# pysui

Python SUI client SDK for Sui - WIP and expect significant refactoring

## Known issues or missing capability
* No batch transaction coverage yet
* Doesn't use mnemonics yet (see [Issue](https://github.com/FrankC01/pysui/issues/9))
* Partial coverage for `sui_getTransaction...` RPC API
* Doesn't support `sui_getEvents` added in SUI 0.15.0

## Ready to run
Requires:
 * Linux or macos (x86_64 or M1)
 * python 3.10 or greater
 * pkg-config

## Run with devnet
By default, `pysui` will use the `client.yaml` configuration found in `.sui/sui_config/`. See [below](#run-local) for running
with different configuration (e.g. Local)

### Setup environment
`python3 -m venv pysuienv`

If, instead, you want to work with repo source code then read DEVELOP.md from repo

### Activate
`source pysuienv/bin/activate`

### Install `pysui`
`pip install pysui`

### Run sample wallet app for help
`wallet`

#### Output
```bash
usage: wallet [options] command [--command_options]

options:
  -h, --help            show this help message and exit

commands:
  {active-address,addresses,new-address,gas,object,objects,rpcapi,committee,merge-coin,split-coin,transfer-object,transfer-sui,pay,paysui,payallsui,package-object,package,publish,call,txns}
    active-address      Shows active address
    addresses           Shows all addresses
    new-address         Generate new address and keypair
    gas                 Shows gas objects and total mist
    object              Show object by id
    objects             Show all objects
    rpcapi              Show Sui RPC API information
    committee           Show committee info for epoch
    merge-coin          Merge two coins together
    split-coin          Split coin into one or more coins
    transfer-object     Transfer an object from one address to another
    transfer-sui        Transfer SUI 'mist(s)' to a Sui address
    pay                 Send coin of any type to recipient(s)
    paysui              Send SUI coins to a list of addresses.
    payallsui           Send all SUI coin(s) to recipient(s)
    package-object      Show raw package object with Move disassembly
    package             Show normalized package information
    publish             Publish a SUI package
    call                Call a move contract function
    txns                Show transaction information
```

### Run sample wallet app for transaction query help
`wallet txns -h`

### Output
```bash
usage: txns subcommand [--subcommand_options]

options:
  -h, --help   show this help message and exit

subcommand:
  {count,txn}
    count      Return total transaction count from server
    txn        Return transaction information
```

## Run Local
To run locally, especially useful when devnet is down, below are the steps to follow:

### Setup local (example from home directory)
1. `mkdir sui_local` from your home directory
2. `sui genesis --working-dir sui_local/`
3. `sui start --network.config sui_local/network.yaml`
4. Open another terminal
5. If you haven't already, setup your `pysui` environment as shown [above](#setup-environment)
6. Prefix `pysui` commands with `--cfg ~/sui_local/client.yaml`

Example:
```bash
wallet --cfg ~/sui_local/client.yaml gas
```