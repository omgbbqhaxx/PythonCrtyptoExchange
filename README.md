# How to Build Your Own Cryptocurrency Exchange with python like binance

In this tutorial you will learn how to create a bitcoin and ethereum wallet with python and then transfer from those wallets you created.


# <img src="https://github.com/omgbbqhaxx/PythonCrtyptoExchange/blob/master/images/UdemyBanner2.png">

## Getting Started

First of all, we will update our ubuntu system and make our system ready.

```shell
sudo apt-get update -y && sudo apt-get upgrade -y && sudo apt-get install vim -y && sudo apt-get install python-dev -y && sudo apt-get install libevent-dev -y &&  sudo apt-get install python-virtualenv -y && apt-get install git -y
```



## First of all install python version 3.0+

```shell
sudo apt-get install --reinstall language-pack-en -y
export LC_ALL="en_US.UTF-8"
export LC_CTYPE="en_US.UTF-8"
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.3
sudo apt-get install python3-pip
apt install python-pip
pip install --upgrade virtualenv
```

## Ethereum configurations..

We are using [pyethereum](https://github.com/ethereum/pyethereum), [web3py](http://web3py.readthedocs.io/en/stable/),
 [eth-utils](https://github.com/ethereum/eth-utils) libraries for ethereum.

```shell
virtualenv -p python3 venv
cd venv
. bin/activate
sudo apt-get install libssl-dev build-essential automake pkg-config libtool libffi-dev libgmp-dev libyaml-cpp-dev
git clone https://github.com/ethereum/pyethereum/
cd pyethereum
python setup.py install
git clone https://github.com/omgbbqhaxx/PythonCrtyptoExchange.git
pip install -r requirements.txt
pipenv install requests
```



## How to create an ethereum wallet using python.


```shell
from ethereum import utils
from eth_utils import address
import os

private_key = utils.sha3(os.urandom(4096))
raw_address = utils.privtoaddr(private_key)
addressif = address.to_normalized_address(raw_address)
keyether = utils.encode_hex(private_key)
```


## How to send ethereum using python.
```shell
from web3 import Web3, HTTPProvider, IPCProvider
from ethereum.transactions import Transaction
web3 = Web3(HTTPProvider('https://api.myetherapi.com/eth'))

tx = Transaction(0, 60000000000, 21000, targetwallet, 0.01, "").sign('yourprivatekey')
print(tx.to_dict())
raw_tx = rlp.encode(tx)
print("raw_tx", raw_tx)
raw_tx_hex = web3.toHex(raw_tx)
print("raw_tx_hex", raw_tx_hex)
web3.eth.sendRawTransaction(raw_tx_hex)
```

## Bitcoin configurations..

We are using [bit](https://github.com/ofek/bit) libraty for bitcoin.

```shell
pip install bit
```





## Donations
  * My ethereum wallet : `0xFBd6f9704478104f0EF3F4f9834c3621210fE598`


  ## Contact

  [![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/cloudbank-github/)
  [![GitHub Issues](https://img.shields.io/badge/open%20issues-0-yellow.svg)](https://github.com/omgbbqhaxx/CloudBank/issues)

  - Report bugs, issues or feature requests using [GitHub issues](issues/new).



## License

[![License](https://img.shields.io/github/license/ethereum/cpp-ethereum.svg)](LICENSE)

All contributions are made under the [GNU General Public License v3](https://www.gnu.org/licenses/gpl-3.0.en.html). See [LICENSE](LICENSE).
