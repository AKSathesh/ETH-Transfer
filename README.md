const Web3 = require('web3');
const web3 = new Web3('https://ropsten.infura.io/https://ropsten.infura.io/v3/74cec7a90abd442c91783d5f0bb74aa5/333f366f10234837b754099fea8c23ae')

const privateKey = '8b276c3a0df86d34555f8821b70f67521eff00c34ed816b3eedf35fd20386229'
const fromAdress = '0x64503DCe20840c0A94210D829b715321370c1A19'
const toAddress = '0x5b6ca2FAb0C42696F107879b59b471c068F477c7'

async function eth_transaction() {
    var value = web3.utils.toWei('0.1', 'ether')

    var SignedTransaction = await web3.eth.accounts.signTransaction({
        to: toAddress,
        value: value,
        gas: 2000000
    }, privateKey);

    web3.eth.sendSignedTransaction(SignedTransaction.rawTransaction) .then((reciept)=>{
        console.log(reciept);
    });
}

eth_transaction()
