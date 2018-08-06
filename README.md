# How to Build Your Own Cryptocurrency Exchange with python like binance

Bu eğitimde python ile bir bitcoin veya ethereum cüzdanı nasıl yaratacağınızı ardından yarattığınız bu cüzdanlardan nasıl transfer yapacağınızı öğreneceksiniz.

Aşağıda tüm bunları yaparken kullanacağımız kütüphaneleri ve eğtimde kullandığım komut satırlarını göreceksiniz.

# <img src="https://github.com/omgbbqhaxx/PythonCrtyptoExchange/blob/master/images/UdemyBanner2.png">


## Contact

[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/cloudbank-github/)
[![GitHub Issues](https://img.shields.io/badge/open%20issues-0-yellow.svg)](https://github.com/omgbbqhaxx/CloudBank/issues)

- Chat in
- Report bugs, issues or feature requests using [GitHub issues](issues/new).



## Getting Started

Öncelikle ubuntu sistemimizi güncelleyelim ve sistemimizi hazır hale getirelim.

```shell
sudo apt-get update -y && sudo apt-get upgrade -y && sudo apt-get install vim -y && sudo apt-get install python-dev -y && sudo apt-get install libevent-dev -y &&  sudo apt-get install python-virtualenv -y && apt-get install git -y
```



## Install python last version..

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

## Other configurations..

We are using [pyethereum](https://github.com/ethereum/pyethereum)  and   [web3py](http://web3py.readthedocs.io/en/stable/) libraries for ethereum.

```shell
virtualenv -p python3 venv
cd venv
. bin/activate
git clone https://github.com/omgbbqhaxx/PythonCrtyptoExchange.git

sudo apt-get install libssl-dev build-essential automake pkg-config libtool libffi-dev libgmp-dev libyaml-cpp-dev
git clone https://github.com/ethereum/pyethereum/
cd pyethereum
python setup.py install


pip install -r requirements.txt
pipenv install requests
```





## Donations
  * My ethereum wallet : `0xFBd6f9704478104f0EF3F4f9834c3621210fE598`


## License

[![License](https://img.shields.io/github/license/ethereum/cpp-ethereum.svg)](LICENSE)

All contributions are made under the [GNU General Public License v3](https://www.gnu.org/licenses/gpl-3.0.en.html). See [LICENSE](LICENSE).
