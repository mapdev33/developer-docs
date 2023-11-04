This document will introduce the complete process of voting.

## Create an account

If you have already created an account, please skip this step.

In this step, your identity information will be stored in the corresponding management contract, which will manage your
account, keys, and metadata.
You need to use the `createAccount` command to perform the above operations. For more details about the `createAccount`
command, please refer to [here](/docs/base/mapo-relay-chain/marker/common_en.md#createaccount).

```shell
./marker createAccount --rpcaddr http://127.0.0.1:7445 --name "validator" --keystore ./UTC--2022-07-01T04-02-22.985282926Z--078f684c7d3bf78bdbe8bef93e56998442dc8099 

INFO [07-01|05:54:37.048] Create account                           func=createAccount address=0x078F684c7d3bf78BDbe8bEf93E56998442dc8099 name=validator
INFO [07-01|05:54:37.048] === create Account ===
INFO [07-01|05:54:37.056] TxInfo                                   func=sendContractTransaction TX data nonce =0  gasLimit =4,500,000  gasPrice =101,000,000,000  chainID =29088
INFO [07-01|05:54:37.057] Please waiting                           func=getResult                txHash =0xbd9603b438fa5b98b894431111c6298605d47a12c8b508458482aa865f2d707c
INFO [07-01|05:54:42.082] Transaction Success                      func=queryTx                 block Number=360,085
INFO [07-01|05:54:42.083] === setName name ===
INFO [07-01|05:54:42.090] TxInfo                                   func=sendContractTransaction TX data nonce =1  gasLimit =4,500,000  gasPrice =101,000,000,000  chainID =29088
INFO [07-01|05:54:42.091] Please waiting                           func=getResult                txHash =0x8c68f99e1c7216a12d3e2ea12d293d150d94c2e0d0136504860e0f86c87cf77c
INFO [07-01|05:54:47.117] Transaction Success                      func=queryTx                 block Number=360,086
INFO [07-01|05:54:47.117] === setAccountDataEncryptionKey ===
INFO [07-01|05:54:47.125] TxInfo                                   func=sendContractTransaction TX data nonce =2  gasLimit =4,500,000  gasPrice =101,000,000,000  chainID =29088
INFO [07-01|05:54:47.126] Please waiting                           func=getResult                txHash =0xed401e84bf7759f2559ba8d97bcee09bb2128cbfb798f3751a427a640944f60d
INFO [07-01|05:54:52.152] Transaction Success                      func=queryTx                 block Number=360,087
```

## Locking

If you have already locked enough MAP to vote, please skip this step.

You need to use the `lockedMAP` command to perform the above operation. For more details about the `lockedMAP` command,
please refer to [here](/docs/base/mapo-relay-chain/marker/common_en.md#lockedmap).

```shell
./marker lockedMAP --rpcaddr http://127.0.0.1:7445 --keystore ./UTC--2022-07-01T04-02-22.985282926Z--078f684c7d3bf78bdbe8bef93e56998442dc8099 --lockedNum 1000000

INFO [07-01|06:12:45.068] === Lock  gold ===
INFO [07-01|06:12:45.069] Lock  gold                               amount=1000000000000000000000000
INFO [07-01|06:12:45.084] TxInfo                                   func=sendContractTransaction TX data nonce =3  gasLimit =4,500,000  gasPrice =101,000,000,000  chainID =29088
INFO [07-01|06:12:45.085] Please waiting                           func=getResult                txHash =0x6f8c9ea1d4481ba26af144d4cf04b5275750f51b899a898e6c57a798fdbcceab
INFO [07-01|06:12:47.095] Transaction Success                      func=queryTx                 block Number=360,302
```

## Voting

When you reach this step, you can vote for your favorite validators. You can use
the [getTotalVotesForEligibleValidators](/docs/base/mapo-relay-chain/marker/common_en.md#gettotalvotesforeligiblevalidators)
command to view all current validators and their votes.

```shell
./marker getTotalVotesForEligibleValidators --rpcaddr http://127.0.0.1:7445 --keystore ./UTC--2022-07-01T04-02-22.985282926Z--078f684c7d3bf78bdbe8bef93e56998442dc8099 

INFO [07-06|06:04:01.431] === getTotalVotesForEligibleValidators === admin=0x078F684c7d3bf78BDbe8bEf93E56998442dc8099
INFO [07-06|06:04:01.434] Validator:                               addr=0x36b77597430cc2C0DD090c67f77f67Fc28195b5D vote amount=1,056,438,467,567,624,843,076,833
INFO [07-06|06:04:01.434] Validator:                               addr=0x7cC3e34C2075D96ef69bF6445a234F6C5E244073 vote amount=1,056,438,467,567,624,843,076,833
INFO [07-06|06:04:01.434] Validator:                               addr=0x3B778BB4F460956E313Ba92484Eb84603A86a625 vote amount=1,046,438,467,567,624,843,076,833
INFO [07-06|06:04:01.434] Validator:                               addr=0x19b375EBB9eE1B21A592A933c6383Df49380046D vote amount=1,046,425,233,310,919,400,227,838
INFO [07-06|06:04:01.434] Validator:                               addr=0x19C560de95c222Ac4B0ad3093D66EF1Fe75640f4 vote amount=134,664,371,097,943,842,325,525
INFO [07-06|06:04:01.434] Validator:                               addr=0x078F684c7d3bf78BDbe8bEf93E56998442dc8099 vote amount=103,060,000,000,004,450,909,077
```

Let's proceed to vote for the validator (0x078F684c7d3bf78BDbe8bEf93E56998442dc8099).

```shell
./marker vote --rpcaddr http://127.0.0.1:7445 --keystore ./UTC--2022-07-01T04-02-22.985282926Z--078f684c7d3bf78bdbe8bef93e56998442dc8099 --target "0x078F684c7d3bf78BDbe8bEf93E56998442dc8099" --voteNum 100000

INFO [07-06|06:05:31.454] === vote Validator ===                   admin=0x078F684c7d3bf78BDbe8bEf93E56998442dc8099 voteTargetValidator=0x078F684c7d3bf78BDbe8bEf93E56998442dc8099 vote MAP Num=100000
INFO [07-06|06:05:31.478] TxInfo                                   func=sendContractTransaction TX data nonce =10  gasLimit =4,500,000  gasPrice =101,000,000,000  chainID =29088
INFO [07-06|06:05:31.479] Please waiting                           func=getResult                txHash =0x8f8724be7e7eb2ffb0034dee92dbe57fbd2534b057ba43adcc7c6be5b20b9ffa
INFO [07-06|06:05:32.083] Transaction Success                      func=queryTx                 block Number=446,614
```

Once you have voted, your vote will be in a pending state. At the end of the current epoch, the selected validator will
be automatically activated along with their associated pending votes.
