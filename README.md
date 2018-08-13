# How to Build Your Own Cryptocurrency Exchange with python like binance

In this tutorial you will learn how to create a bitcoin and ethereum wallet with python and then transfer from those wallets you created.


# <img src="https://github.com/omgbbqhaxx/PythonCrtyptoExchange/blob/master/images/UdemyBanner2.png">

### Getting Started

First of all, we will update our ubuntu system and make our system ready.

```shell
sudo apt-get update -y && sudo apt-get upgrade -y && sudo apt-get install vim -y && sudo apt-get install python-dev -y && sudo apt-get install libevent-dev -y &&  sudo apt-get install python-virtualenv -y && apt-get install git -y
```



### First of all install python version 3.0+

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



### How to create an ethereum wallet using python.


```python
from ethereum import utils
from eth_utils import address
import os

private_key = utils.sha3(os.urandom(4096))
raw_address = utils.privtoaddr(private_key)
addressif = address.to_normalized_address(raw_address)
keyether = utils.encode_hex(private_key)
```


### How to send ether using python.
```python
from web3 import Web3, HTTPProvider, IPCProvider
from ethereum.transactions import Transaction
web3 = Web3(HTTPProvider('https://api.myetherapi.com/eth'))

amountexample = Web3.toWei(0.001, 'ether')
tx = Transaction(0, 60000000000, 21000, targetwallet, amountexample, "").sign('yourprivatekey')
print(tx.to_dict())
raw_tx = rlp.encode(tx)
raw_tx_hex = web3.toHex(raw_tx)
web3.eth.sendRawTransaction(raw_tx_hex)
```




### How to deposit ether using etherscan.io API.
```shell
http://api.etherscan.io/api?module=account&action=txlist&address=0xeb02fed51228b842fb00fb18c26fe84707cd28d7&startblock=0&endblock=99999999&sort=asc&apikey=GKQMITFG5YPAG1MA2B4P6KAXGVKMQHVVWV
```

```python
r = "http://api.etherscan.io/api?module=account&action=txlist&address=0xeb02fed51228b842fb00fb18c26fe84707cd28d7&startblock=0&endblock=99999999&sort=asc&apikey=GKQMITFG5YPAG1MA2B4P6KAXGVKMQHVVWV"
r = requests.get(r)
r = r.json()
for i in r["result"]:
    try:
        UserHistory.objects.get(txhash=str(i["blockHash"])) #  blockhash is important for avoid double deposit. you need save and check  #blockhash#
    except UserHistory.DoesNotExist: #if blockhash is not registered on your database.
        if(i["to"] == "0xeb02fed51228b842fb00fb18c26fe84707cd28d7"):
            ethval = web3.fromWei(int(i["value"]), 'ether') #Convert ethers from WEİ.
            acc.ethbalance = acc.ethbalance + ethval #increase user's ethereum balance.
            acc.save()
            uh = UserHistory(king=acc,txhash=str(i["blockHash"]),value=ethval,currencyname="ethereum") #save blockhash on your database! that important.
            uh.save()
        else:
            pass
```





## Bitcoin configurations..
We are using [bit](https://github.com/ofek/bit) libraty for bitcoin.

```shell
pip install bit
```

### How to create a bitcoin wallet using python.

```python
from bit import Key

btc = Key()
btc.address #Your bitcoin address.
btc.to_wif() #Your [secret] private KEY!
```


### How to import btc wallet from key.

```python
from bit import Key
from bit import wif_to_key
btc = Key('btcWİFkeyHere')
key = wif_to_key('btcWİFkeyHere') #alternative usagement.
btc.address #Your bitcoin address.
#get user ethbalance
btc.get_balance('usd') # Get accoun's usd balance.
btc.get_balance('btc') #Get account's btc balance.
```


### How to send btc using python.

[Bit developer docs.](https://github.com/ofek/bit)
```python
from bit import Key

key = Key('btcWİFkeyHere')
key.get_unspents()
x = key.send([(targetwallet, amountasbtc, 'btc')],fee=100)
print(x)
```



### Satoshi to Currency & btc

[Satoshi to Currency docs.](https://ofek.github.io/bit/guide/rates.html)
```python
from bit import Key
from bit.network import satoshi_to_currency_cached


key = Key('btcWİFkeyHere')
key.get_unspents()
satoshi_to_currency_cached(1500, 'usd')
satoshi_to_currency_cached(1500, 'btc')
```


### How to deposit bitcoin using bitcoin.info API.

[blockchain.info API docs.](https://blockchain.info/q)

txresult/TxHash/Address - Calculate the result of a transaction sent or received to Address. Multiple addresses separated by |

```python
from bit import Key
from bit.network import satoshi_to_currency_cached


transactions = key.get_transactions()
if(len(transactions) == 0):
    pass
try:
    UserHistory.objects.get(txhash=str(transactions[0])) #
except UserHistory.DoesNotExist:
    for i in transactions:
        r = 'https://blockchain.info/q/txresult/{0}/{1}'.format(TxHash,Address)
        r = requests.get(r)
        num = int(r.text)
        if num > 0:
            try:
                UserHistory.objects.get(txhash=str(i))
            except UserHistory.DoesNotExist:
                #if dont have an any transaction
                btcbal = Decimal(satoshi_to_currency_cached(num, 'btc'))
                acc.btcbalance = acc.btcbalance + btcbal
                acc.save()
                uh = UserHistory(king=acc,txhash=str(i),value=num,currencyname="bitcoin")
                uh.save()
        else:
           print("Negative number")
    return render(request, "x.html", locals())
print("nothing changed")
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
