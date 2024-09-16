#### starkli

## 0 - Criando Pasta

mkdir ~/.starkli-wallets
mkdir ~/.starkli-wallets/erc20test

## 1.1 - Criando nova pvt key

starkli signer keystore new ~/.starkli-wallets/erc20test/user0_keystore.json

export STARKNET_KEYSTORE="~/.starkli-wallets/erc20test/user0_keystore.json"

## 1.2 - Conectando com private key local

starkli signer keystore from-key ~/.starkli-wallets/erc20test/user0_keystore.json

## 2.1 - Criando conta

starkli account oz init ~/.starkli-wallets/erc20test/account0_account.json

starkli account deploy ~/.starkli-wallets/erc20test/account0_account.json

## 2.2 - Conectando com conta local

cat ~/.starkli-wallets/erc20test/account0_account.json

starkli account fetch 0x5d1b7079c98b6160bea639a01852a199474de01ee8932ec6008387332dbbce4 --rpc https://starknet-sepolia.public.blastapi.io/rpc/v0_7 --output ~/.starkli-wallets/erc20test/account0_account.json

## 3 Declarando Mock ERC20 Token

starkli declare target/dev/token_sender_MockERC20.contract_class.json --rpc https://starknet-sepolia.public.blastapi.io/rpc/v0_7 --account ~/.starkli-wallets/erc20test/account0_account.json --keystore ~/.starkli-wallets/erc20test/user0_keystore.json

## 4 Deployand Mock ERC20 Token

starkli deploy 0x0631029fa51675ac4e0271911f1d5075154e663576010785b01f924bf9368401 u256:1000000000 0x01121c686b331F5b9D19dAF25E56F023bee7F6AC129518154a05f3Dd2b1dC0Ba --rpc https://starknet-sepolia.public.blastapi.io/rpc/v0_7 --account ~/.starkli-wallets/erc20test/account0_account.json --keystore ~/.starkli-wallets/erc20test/user0_keystore.json

## 5 Checando Supply do Token

starkli call 0x01f6ce3402f17f360b253fe0d9a94aa1fb832aacfcba099813657565a271c449 total_supply --rpc https://starknet-sepolia.public.blastapi.io/rpc/v0_7
