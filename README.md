![Proof of Phone logo](https://raw.githubusercontent.com/blocknotary/proofofphone/master/logo_proof_of_phone.png)

Proof of phone is a smart oracle developed for the Ethereum blockchain to serve as a simple form of KYC (Know-Your-Customer).

[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/hyperium/hyper/master/LICENSE)

## Installation

1. Download zip archive
2. Unpack it
3. Go to the /web folder in terminal and install the dependencies `npm install`
4. Set **environment** in web/config.json (see config.json with placeholders below): `test` or `live`
5. Set smart contract key points in web/config.json (see config.json with placeholders below):
    * `wallet.test`, `wallet.live`
    * `rpc.test`, `rpc.live`
6. Go to the root in terminal `/` and run `node deployContract.js` to deploy your smart contract into Ethereum.
7. After creation you will get the message in terminal like this:
    *Contract mined! address:* **0xb713e9195f44a10383015f38774f31869053750c** *transactionHash: 0x85e85f78a4e1b40f26e491eb88b9a231b31085db11799734edc54d0285edc190*
8. Copy created smart contract address from this message and paste it to the config.json to `contractAddress.test` or `contractAddress.live` depending on your environment.
9. Set `twilio` params for sending SMS, path to mongo DB (`mongodbConnectionString`) for two-factor verification and `salt` for transaction message.
10. Go to `/web` folder in terminal and start proofofphone web application `node app.js`

### 
config.json with placeholders
```
{
    "environment": "live/test",
    "globalToken": "cba2c691-47df-41e7-bc97-a0818103ed14",
    "salt": "salt_for_message_with_hash_creating",
    "mongodbConnectionString": "mongodb://user:password@path_to_database",
    "sendSMS": {
        "twilio": {
            "phoneNumberTest": "+12345678900",
            "phoneNumberLive": "+12345678900",
            "accountSIDTest": "twilio_account_SID_test",
            "accountSIDLive": "twilio_account_SID_live",
            "authTokenTest": "twilio_auth_token_test",
            "authTokenLive": "twilio_auth_token_live"
        }
    },
    "smartContract": {
        "bin": "0x60606040525b33600060006101000a81548173ffffffffffffffffffffffffffffffffffffffff021916908302179055505b6109438061003f6000396000f36060604052361561008a576000357c0100000000000000000000000000000000000000000000000000000000900480631f83f440146101ef57806341c0e1b51461021b5780634636a1591461022a578063a02b9aac1461024b578063b958a5e1146102cf578063e3ffc9a3146102fb578063f37306531461030a578063fe97ee881461034c5761008a565b6101ed5b6060604051908101604052806000815260200167016345785d8a0000340481526020016000368080601f016020809104026020016040519081016040528093929190818152602001838380828437820191505050505050815260200150600260005060003373ffffffffffffffffffffffffffffffffffffffff16815260200190815260200160002060005060008201518160000160005055602082015181600101600050556040820151816002016000509080519060200190828054600181600116156101000203166002900490600052602060002090601f016020900481019282601f1061018957805160ff19168380011785556101ba565b828001600101855582156101ba579182015b828111156101b957825182600050559160200191906001019061019b565b5b5090506101e591906101c7565b808211156101e157600081815060009055506001016101c7565b5090565b50509050505b565b005b6102056004808035906020019091905050610378565b6040518082815260200191505060405180910390f35b61022860048050506103bc565b005b6102496004808035906020019091908035906020019091905050610455565b005b61026160048080359060200190919050506106b1565b60405180806020018281038252838181518152602001915080519060200190808383829060006004602084601f0104600f02600301f150905090810190601f1680156102c15780820380516001836020036101000a031916815260200191505b509250505060405180910390f35b6102e5600480803590602001909190505061079f565b6040518082815260200191505060405180910390f35b61030860048050506107e3565b005b61032060048080359060200190919050506108ae565b604051808273ffffffffffffffffffffffffffffffffffffffff16815260200191505060405180910390f35b61036260048080359060200190919050506108e6565b6040518082815260200191505060405180910390f35b6000600260005060008373ffffffffffffffffffffffffffffffffffffffff1681526020019081526020016000206000506001016000505490506103b7565b919050565b600060009054906101000a900473ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff163373ffffffffffffffffffffffffffffffffffffffff1614151561041857610453565b600060009054906101000a900473ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff16ff5b565b600060009054906101000a900473ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff163373ffffffffffffffffffffffffffffffffffffffff161415156104b1576106ad565b6060604051908101604052808281526020016000815260200160016000508054600181600116156101000203166002900480601f0160208091040260200160405190810160405280929190818152602001828054600181600116156101000203166002900480156105635780601f1061053857610100808354040283529160200191610563565b820191906000526020600020905b81548152906001019060200180831161054657829003601f168201915b5050505050815260200150600260005060008473ffffffffffffffffffffffffffffffffffffffff16815260200190815260200160002060005060008201518160000160005055602082015181600101600050556040820151816002016000509080519060200190828054600181600116156101000203166002900490600052602060002090601f016020900481019282601f1061060c57805160ff191683800117855561063d565b8280016001018555821561063d579182015b8281111561063c57825182600050559160200191906001019061061e565b5b509050610668919061064a565b80821115610664576000818150600090555060010161064a565b5090565b5050905050816003600050600083815260200190815260200160002060006101000a81548173ffffffffffffffffffffffffffffffffffffffff021916908302179055505b5050565b6020604051908101604052806000815260200150600260005060008373ffffffffffffffffffffffffffffffffffffffff1681526020019081526020016000206000506002016000508054600181600116156101000203166002900480601f01602080910402602001604051908101604052809291908181526020018280546001816001161561010002031660029004801561078e5780601f106107635761010080835404028352916020019161078e565b820191906000526020600020905b81548152906001019060200180831161077157829003601f168201915b5050505050905061079a565b919050565b6000600260005060008373ffffffffffffffffffffffffffffffffffffffff1681526020019081526020016000206000506000016000505490506107de565b919050565b600060009054906101000a900473ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff163373ffffffffffffffffffffffffffffffffffffffff1614151561083f576108ac565b600060009054906101000a900473ffffffffffffffffffffffffffffffffffffffff1673ffffffffffffffffffffffffffffffffffffffff1660003073ffffffffffffffffffffffffffffffffffffffff1631604051809050600060405180830381858888f19350505050505b565b600360005060205280600052604060002060009150909054906101000a900473ffffffffffffffffffffffffffffffffffffffff1681565b60006000600260005060008473ffffffffffffffffffffffffffffffffffffffff16815260200190815260200160002060005060000160005054141515610934576001905061093e5661093d565b6000905061093e565b5b91905056",
        "ABI": [{"constant":true,"inputs":[{"name":"addr","type":"address"}],"name":"getPaymentByAddress","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"constant":false,"inputs":[],"name":"kill","outputs":[],"type":"function"},{"constant":false,"inputs":[{"name":"addr","type":"address"},{"name":"phone","type":"uint256"}],"name":"newPhoneToAddr","outputs":[],"type":"function"},{"constant":true,"inputs":[{"name":"addr","type":"address"}],"name":"getPaymentDataByAddress","outputs":[{"name":"","type":"bytes"}],"type":"function"},{"constant":true,"inputs":[{"name":"addr","type":"address"}],"name":"getPhoneByAddress","outputs":[{"name":"","type":"uint256"}],"type":"function"},{"constant":false,"inputs":[],"name":"sendEtherToOwner","outputs":[],"type":"function"},{"constant":true,"inputs":[{"name":"","type":"uint256"}],"name":"phones","outputs":[{"name":"","type":"address"}],"type":"function"},{"constant":true,"inputs":[{"name":"addr","type":"address"}],"name":"hasPhone","outputs":[{"name":"","type":"bool"}],"type":"function"},{"inputs":[],"type":"constructor"}],
        "wallet": {
            "test": "0x0000000000000000000000000000000000000000",
            "live": "0x0000000000000000000000000000000000000000"
        },
        "contractAddress": {
            "test": "0x0000000000000000000000000000000000000000",
            "live": "0x0000000000000000000000000000000000000000"
        },
        "rpc": {
            "test": "http://host:port",
            "live": "http://host:port"
        }
    }
}
```

## Contributors

Viktor Baranov

Pasha Goncharenko

Igor Barinov

Anton Grin


## License

MIT

## Support

Supported by [Wanxiang Blockchain Labs](http://www.blockchainlabs.org/blockgrant-x-en/)
