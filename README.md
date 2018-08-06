# How to Build Your Own Cryptocurrency Exchange with python like binance

In this tutorial you will learn how to create a bitcoin and ethereum wallet with python and then transfer from those wallets you created.

Below we'll use the libraries and the command lines that I use for training when we do all of this.

# <img src="https://github.com/omgbbqhaxx/PythonCrtyptoExchange/blob/master/images/UdemyBanner2.png">

## Getting Started

First, we will update our ubuntu system and make our system ready.

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
