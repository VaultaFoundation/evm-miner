# Vaulta EVM Miner

This tool allows you to accept Ethereum transactions and relay them to the Vaulta EVM.

For every transaction that you relay you will receive a reward in the form of Vaulta tokens.

## Environment Variables

| Name | Description                                                                                                       | Default |
| --- |-------------------------------------------------------------------------------------------------------------------|---------|
| `MINER_ACCOUNT` | The name of the miner account on the Vaulta Network. Mining reward will be sent to this account.                                                                  |         |
| `AUTH_ACCOUNT` | [**New Parameter**] account that authorize the transaction, also pay cpu/net, default to miner                              | =`MINER_ACCOUNT`        |
| `MINER_PERMISSION` | permission used for sending transactions | `active` | 
| `PRIVATE_KEY` | The private key that corresponds to the `MINER_PERMISSION` of `AUTH_ACCOUNT`, used for signing transactions   |         |
| `RPC_ENDPOINTS` | A list of Vaulta RPC endpoints to connect to, comma-delimited. The list is a failover list.                                                        |         |
| `PORT` | The port to listen on for incoming EVM transactions.                                                          | `50305` |
| `EVM_ACCOUNT` | | `eosio.evm` |
| `EVM_SCOPE` | |  |
| `MINER_FEE_MODE` | Set how the miner collect fees after Vaulta-EVM upgrading to version 1. Can be `CPU` or `FIXED`.  | `FIXED` |
| `GAS_PER_CPU` | priority_fee = cpu_per_us / GAS_PER_CPU * (1 + MINER_MARKUP_PERCENTAGE/100) * GAS_TOKEN_EXCHANGE_RATE if MINER_FEE_MODE=`CPU` | 74 |
| `MINER_MARKUP_PERCENTAGE` | priority_fee = cpu_per_us / GAS_PER_CPU * (1 + MINER_MARKUP_PERCENTAGE/100) * GAS_TOKEN_EXCHANGE_RATE if MINER_FEE_MODE=`CPU` | 0 |
| `GAS_TOKEN_EXCHANGE_RATE` | priority_fee = cpu_per_us / GAS_PER_CPU * (1 + MINER_MARKUP_PERCENTAGE/100) * GAS_TOKEN_EXCHANGE_RATE if MINER_FEE_MODE=`CPU` | 1 |
| `FIXED_MINER_FEE` | Fixed priority_fee in wei if MINER_FEE_MODE=`FIXED`. | 0 | 
| `EXPIRE_SEC` | Expiration time when broadcasting Vaulta transaction. | 60 |
| `RETRY_TX` | Whether local Spring node should retry when broadcasting failed. | true |
| `PRICING_ENDPOINTS` | Endpoints used for querying CPU price. Mainly for tests. Only ONE url instead of a list should be put here. | null |

## Usage

> ⚠ **You must have registered your miner**
>
> You must have registered your miner account on the Vaulta Network. [Head over to our
> docs](https://docs.eosnetwork.com/evm/miners-and-nodes/transaction-miner) to learn all about
> mining, claiming your rewards, and more.


### Get the code

```bash
git clone https://github.com/VaultaFoundation/evm-miner.git
cd eos-evm-miner
```

### Install dependencies

```bash
yarn
```
OR
```bash
npm install
```

### Environment Variables
Copy the `.env.example` file to `.env` and fill in the environment variables.

### Start mining

This command will build and run the node.

```bash
yarn mine
```
OR
```bash
npm run mine
```

If you want to just run the node without building, you can run:

```bash
yarn start
```
OR
```bash
npm run start
```


## Logging

This project uses [Winston](https://github.com/winstonjs/winston) for logging.

When you run the miner a directory called `logs` will be created in the root of the project. 
Inside you will find two log files, `combined.log` and `error.log`.
