<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [以太坊私有链搭建手册](#%E4%BB%A5%E5%A4%AA%E5%9D%8A%E7%A7%81%E6%9C%89%E9%93%BE%E6%90%AD%E5%BB%BA%E6%89%8B%E5%86%8C)
  - [1、安装go 语言开发环境，这个请自行安装](#1%E5%AE%89%E8%A3%85go-%E8%AF%AD%E8%A8%80%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E8%BF%99%E4%B8%AA%E8%AF%B7%E8%87%AA%E8%A1%8C%E5%AE%89%E8%A3%85)
  - [2、下载 https://github.com/ethereum/go-ethereum 源码，并编译源码，会得到以太坊客户端 geth;](#2%E4%B8%8B%E8%BD%BD-httpsgithubcomethereumgo-ethereum-%E6%BA%90%E7%A0%81%E5%B9%B6%E7%BC%96%E8%AF%91%E6%BA%90%E7%A0%81%E4%BC%9A%E5%BE%97%E5%88%B0%E4%BB%A5%E5%A4%AA%E5%9D%8A%E5%AE%A2%E6%88%B7%E7%AB%AF-geth)
  - [3、配置初始化状态](#3%E9%85%8D%E7%BD%AE%E5%88%9D%E5%A7%8B%E5%8C%96%E7%8A%B6%E6%80%81)
  - [4、初始化，写入创世区块](#4%E5%88%9D%E5%A7%8B%E5%8C%96%E5%86%99%E5%85%A5%E5%88%9B%E4%B8%96%E5%8C%BA%E5%9D%97)
  - [5、启动私有节点](#5%E5%90%AF%E5%8A%A8%E7%A7%81%E6%9C%89%E8%8A%82%E7%82%B9)
    - [控制台操作](#%E6%8E%A7%E5%88%B6%E5%8F%B0%E6%93%8D%E4%BD%9C)
    - [一、创建用户](#%E4%B8%80%E5%88%9B%E5%BB%BA%E7%94%A8%E6%88%B7)
    - [二、查看账户余额](#%E4%BA%8C%E6%9F%A5%E7%9C%8B%E8%B4%A6%E6%88%B7%E4%BD%99%E9%A2%9D)
    - [三、启动&停止挖矿](#%E4%B8%89%E5%90%AF%E5%8A%A8%E5%81%9C%E6%AD%A2%E6%8C%96%E7%9F%BF)
    - [四、发送交易](#%E5%9B%9B%E5%8F%91%E9%80%81%E4%BA%A4%E6%98%93)
    - [五、查看交易区块](#%E4%BA%94%E6%9F%A5%E7%9C%8B%E4%BA%A4%E6%98%93%E5%8C%BA%E5%9D%97)
    - [六、连接到其他节点](#%E5%85%AD%E8%BF%9E%E6%8E%A5%E5%88%B0%E5%85%B6%E4%BB%96%E8%8A%82%E7%82%B9)
  - [七、合约的应用与创建使用](#%E4%B8%83%E5%90%88%E7%BA%A6%E7%9A%84%E5%BA%94%E7%94%A8%E4%B8%8E%E5%88%9B%E5%BB%BA%E4%BD%BF%E7%94%A8)
    - [1、编写合约](#1%E7%BC%96%E5%86%99%E5%90%88%E7%BA%A6)
    - [2、编译合约](#2%E7%BC%96%E8%AF%91%E5%90%88%E7%BA%A6)
    - [3、部署合约](#3%E9%83%A8%E7%BD%B2%E5%90%88%E7%BA%A6)
  - [4、合约交互](#4%E5%90%88%E7%BA%A6%E4%BA%A4%E4%BA%92)
    - [第一步： 获取合约组件](#%E7%AC%AC%E4%B8%80%E6%AD%A5-%E8%8E%B7%E5%8F%96%E5%90%88%E7%BA%A6%E7%BB%84%E4%BB%B6)
    - [第二步： 实例化合约](#%E7%AC%AC%E4%BA%8C%E6%AD%A5-%E5%AE%9E%E4%BE%8B%E5%8C%96%E5%90%88%E7%BA%A6)
    - [第三步： 调用合约](#%E7%AC%AC%E4%B8%89%E6%AD%A5-%E8%B0%83%E7%94%A8%E5%90%88%E7%BA%A6)
  - [5、在电脑B 调用合约](#5%E5%9C%A8%E7%94%B5%E8%84%91b-%E8%B0%83%E7%94%A8%E5%90%88%E7%BA%A6)
  - [6、通过web3 调用](#6%E9%80%9A%E8%BF%87web3-%E8%B0%83%E7%94%A8)
    - [第一步](#%E7%AC%AC%E4%B8%80%E6%AD%A5)
    - [第二步](#%E7%AC%AC%E4%BA%8C%E6%AD%A5)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 以太坊私有链搭建手册
### 1、安装go 语言开发环境，这个请自行安装
### 2、下载 https://github.com/ethereum/go-ethereum 源码，并编译源码，会得到以太坊客户端 geth;
### 3、配置初始化状态
要运行以太坊私有链，需要定义自己的创世区块，创世区块信息写在一个 JSON 格式的配置文件中。首先将下面的内容保存到一个 JSON 文件中，例如 genesis.json；

```
{
  "config": {
        "chainId": 1024,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    },
    "coinbase" : "0x0000000000000000000000000000000000000000",
    "difficulty" : "0x40000",
    "extraData" : "",
    "gasLimit" : "0xffffffff",
    "nonce" : "0x0000000000000042",
    "mixhash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
    "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
    "timestamp" : "0x00",
    "alloc": { }
}
```
其中，chainID 指定了独立的区块链网络 ID。网络 ID 在连接到其他节点的时候会用到，以太坊公网的网络 ID 是 1，为了不与公有链网络冲突，运行私有链节点的时候要指定自己的网络 ID。不同 ID 网络的节点无法相互连接。

* difficulty： 设置当前区块的难度，如果难度过大，cpu挖矿就很难，这里设置较小难度；
* extraData：附加信息，随便填，可以填你的个性信息；
* gasLimit：该值设置对GAS的消耗总量限制，用来限制区块能包含的交易信息总和；
* coinbase： 矿工的账号，随便填；
* parentHash：上一个区块的hash值，因为是创世块，所以这个值是0；
* alloc：用来预置账号以及账号的以太币数量，因为私有链挖矿比较容易，所以我们不需要预置有币的账号，需要的时候自己创建即可以；
* nonce：nonce就是一个64位随机数，用于挖矿；

### 4、初始化，写入创世区块
准备好创世区块配置文件后，需要初始化区块链，将上面的创世区块信息写入到区块链中。首先要新建一个目录用来存放区块链数据，假设新建的数据目录为 ~/coin/data0，genesis.json 保存在 ~/coin 中，此时目录结构应该是这样的：

```
coin
├── data0
└── genesis.json
```
接下来进入 coin 中，执行初始化命令：

```
cd privatechain
geth --datadir data0 init genesis.json
```

运行上面的命令，会读取 genesis.json 文件，根据其中的内容，将创世区块写入到区块链中。

初始化成功后，会在数据目录 data0 中生成 geth 和 keystore 两个文件夹，此时目录结构如下：

```
./coin/
├── data0
│   ├── geth
│   │   ├── chaindata
│   │   │   ├── 000040.ldb
│   │   │   ├── 000041.ldb
│   │   │   ├── 000044.ldb
│   │   │   ├── 000045.log
│   │   │   ├── CURRENT
│   │   │   ├── LOCK
│   │   │   ├── LOG
│   │   │   └── MANIFEST-000046
│   │   ├── ethash
│   │   │   ├── cache-R23-0000000000000000
│   │   │   └── cache-R23-290decd9548b62a8
│   │   ├── lightchaindata
│   │   │   ├── 000001.log
│   │   │   ├── CURRENT
│   │   │   ├── LOCK
│   │   │   ├── LOG
│   │   │   └── MANIFEST-000000
│   │   ├── LOCK
│   │   ├── nodekey
│   │   └── transactions.rlp
│   ├── geth.ipc
│   ├── history
│   └── keystore
│       ├── UTC--2018-07-06T08-47-57.705247784Z--fd5c2fab3069aacce339425c1168ed961cb82dcd
│       └── UTC--2018-07-06T10-47-22.680691612Z--79c385060f0e4798cc43520b2e60fb2c67154ffb
└── genesis.json
```

其中 geth/chaindata 中存放的是区块数据，keystore 中存放的是账户数据。

### 5、启动私有节点
初始化完成后，就有了一条自己的私有链，之后就可以启动自己的私有链节点并做一些操作，在终端中输入以下命令即可启动节点：

```
geth --identity "node1" --rpc --rpcport "8545" --datadir data0 --port "30303" --nodiscover console
```
上面命令的主体是 geth console，表示启动节点并进入交互式控制台。
各选项含义如下：

identity：指定节点 ID；<br>
rpc：表示开启 HTTP-RPC 服务；<br>
rpcport：指定 HTTP-RPC 服务监听端口号（默认为 8545）；<br>
datadir：指定区块链数据的存储位置；<br>
port：指定和其他节点连接所用的端口号（默认为 30303）；<br>
nodiscover：关闭节点发现机制，防止加入有同样初始配置的陌生节点。<br>

运行上面的命令后，就启动了区块链节点并进入了该节点的控制台：

```
Welcome to the Geth JavaScript console!

instance: Geth/TestNode/v1.6.7-stable-ab5646c5/linux-amd64/go1.8.1
 modules: admin:1.0 debug:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 txpool:1.0 web3:1.0

```
这是一个交互式的 JavaScript 执行环境，在这里面可以执行 JavaScript 代码，其中 > 是命令提示符。在这个环境里也内置了一些用来操作以太坊的 JavaScript 对象，可以直接使用这些对象。这些对象主要包括：

* eth：包含一些跟操作区块链相关的方法；
* net：包含一些查看p2p网络状态的方法；
* admin：包含一些与管理节点相关的方法；
* miner：包含启动&停止挖矿的一些方法；
* personal：主要包含一些管理账户的方法；
* txpool：包含一些查看交易内存池的方法；
* web3：包含了以上对象，还包含一些单位换算的方法。

#### 控制台操作

入以太坊 Javascript Console 后，就可以使用里面的内置对象做一些操作，这些内置对象提供的功能很丰富，比如查看区块和交易、创建账户、挖矿、发送交易、部署智能合约等。

常用命令有：

* personal.newAccount()：创建账户；
* personal.unlockAccount()：解锁账户；
* eth.accounts：枚举系统中的账户；
* eth.getBalance()：查看账户余额，返回值的单位是 Wei（Wei 是以太坊中最小货币面额单位，类似比特币中的聪，1 ether = 10^18 Wei）；
* eth.blockNumber：列出区块总数；
* eth.getTransaction()：获取交易；
* eth.getBlock()：获取区块；
* miner.start()：开始挖矿；
* miner.stop()：停止挖矿；
* web3.fromWei()：Wei 换算成以太币；
* web3.toWei()：以太币换算成 Wei；
* txpool.status：交易池中的状态；
* admin.addPeer()：连接到其他节点；

这些命令支持 Tab 键自动补全，具体用法如下。

#### 一、创建用户

```
> personal.newAccount()
Passphrase:
Repeat passphrase:
"0x3443ffb2a5ce3f4b80080791e0fde16a3fac2802"
> INFO [09-12|05:55:44] New wallet appeared                     url=keystore:///root/work/privatech… status=Locked
```
输入两遍密码后，会生成账户地址。

再创建一个账户：

```
> personal.newAccount()
Passphrase:
Repeat passphrase:
"0x02bee2a1582bbf58c42bbdfe7b8db4685d4d4c62"
> INFO [09-12|06:10:45] New wallet appeared                     url=keystore:///root/work/privatech… status=Locked

```

查看刚刚创建的两个账户：

```
> eth.accounts
["0x3443ffb2a5ce3f4b80080791e0fde16a3fac2802", "0x02bee2a1582bbf58c42bbdfe7b8db4685d4d4c62"]
```

注意 这条命令当前只能看到 当前链上 的account信息

#### 二、查看账户余额

```
> eth.getBalance(eth.accounts[0])
0
> eth.getBalance(eth.accounts[1])
0
```

注意，这里eth.accounts[0]是账户ID，是一个字符串；

#### 三、启动&停止挖矿

```
> miner.start(1)
```
其中 start 的参数表示挖矿使用的线程数。第一次启动挖矿会先生成挖矿所需的 DAG 文件，这个过程有点慢，等进度达到 100% 后，就会开始挖矿，此时屏幕会被挖矿信息刷屏。

停止挖矿，在 console 中输入：

```
> miner.stop()
```

挖到一个区块会奖励5个以太币，挖矿所得的奖励会进入矿工的账户，这个账户叫做 coinbase，默认情况下 coinbase 是本地账户中的第一个账户，可以通过 miner.setEtherbase() 将其他账户设置成 coinbase。

#### 四、发送交易

目前，账户 0 已经挖到了 3 个块的奖励，账户 1 的余额还是0：

```
> eth.getBalance(eth.accounts[0])
15000000000000000000
> eth.getBalance(eth.accounts[1])
0
```


我们要从账户 0 向账户 1 转账，所以要先解锁账户 0，才能发起交易：

```
> personal.unlockAccount(eth.accounts[0])
Unlock account 0x3443ffb2a5ce3f4b80080791e0fde16a3fac2802
Passphrase: 
true
```

发送交易，账户 0 -> 账户 1：

```
> amount = web3.toWei(5,'ether')
"5000000000000000000"
> eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[1],value:amount})
INFO [09-12|07:38:12] Submitted transaction                    fullhash=0x9f5e61f3d686f793e2df6378d1633d7a9d1df8ec8c597441e1355112d102a6ce recipient=0x02bee2a1582bbf58c42bbdfe7b8db4685d4d4c62
"0x9f5e61f3d686f793e2df6378d1633d7a9d1df8ec8c597441e1355112d102a6ce"

```
此时如果没有挖矿，用 txpool.status 命令可以看到本地交易池中有一个待确认的交易，可以使用 eth.getBlock("pending", true).transactions 查看当前待确认交易。

使用 miner.start() 命令开始挖矿：

```
> miner.start(1);admin.sleepBlocks(1);miner.stop();
```

新区块挖出后，挖矿结束，查看账户 1 的余额，已经收到了账户 0 的以太币：

```
> web3.fromWei(eth.getBalance(eth.accounts[1]),'ether')
5
```

#### 五、查看交易区块
查看当前区块总数：

```
> eth.blockNumber
4
```

#### 六、连接到其他节点

可以通过 admin.addPeer() 方法连接到其他节点，两个节点要要指定相同的 chainID。

假设有两个节点：节点一和节点二，chainID 都是 1024，通过下面的步骤就可以从节点一连接到节点二。

首先要知道节点二的 enode 信息，在节点二的 JavaScript console 中执行下面的命令查看 enode 信息：

```
> admin.nodeInfo.enode
"enode://d465bcbd5c34da7f4b8e00cbf9dd18e7e2c38fbd6642b7435f340c7d5168947ff2b822146e1dc1b07e02f7c15d5ca09249a92f1d0caa34587c9b2743172259ee@[::]:30303"

```

然后在节点一的 JavaScript console 中执行 admin.addPeer()，就可以连接到节点二：

```
> admin.addPeer("enode://d465bcbd5c34da7f4b8e00cbf9dd18e7e2c38fbd6642b7435f340c7d5168947ff2b822146e1dc1b07e02f7c15d5ca09249a92f1d0caa34587c9b2743172259ee@127.0.0.1:30304")

```

addPeer() 的参数就是节点二的 enode 信息，注意要把 enode 中的 [::] 替换成节点二的 IP 地址。连接成功后，节点二就会开始同步节点一的区块，同步完成后，任意一个节点开始挖矿，另一个节点会自动同步区块，向任意一个节点发送交易，另一个节点也会收到该笔交易。

通过 admin.peers 可以查看连接到的其他节点信息，通过 net.peerCount 可以查看已连接到的节点数量。

除了上面的方法，也可以在启动节点的时候指定 --bootnodes 选项连接到其他节点。

geth --dev console 进入控制台

### 七、合约的应用与创建使用
#### 1、编写合约

```
pragma solidity ^0.4.0;

contract SimpleStorage {
    uint storedData;

    function set(uint x) public returns (uint){
        storedData = x;
        return 10 * x;
    }

    function get() public  returns (uint) {
        return storedData;
    }
}
```

#### 2、编译合约

推荐网站： https://ethereum.github.io/browser-solidity/#version=soljson-v0.4.16+commit.d7661dd9.js&optimize=false

得到 web3deploy

```
var simplestorageContract = web3.eth.contract([{"constant":false,"inputs":[{"name":"x","type":"uint256"}],"name":"set","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[],"name":"get","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"nonpayable","type":"function"}]);
var simplestorage = simplestorageContract.new(
   {
     from: web3.eth.accounts[0], 
     data: '0x6060604052341561000f57600080fd5b5b60ec8061001e6000396000f30060606040526000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff16806360fe47b11460475780636d4ce63c14607b575b600080fd5b3415605157600080fd5b6065600480803590602001909190505060a1565b6040518082815260200191505060405180910390f35b3415608557600080fd5b608b60b6565b6040518082815260200191505060405180910390f35b60008160008190555081600a0290505b919050565b6000805490505b905600a165627a7a7230582026dec0f4d79b9f9ab28541921bdf54151e1aafa40e81612989b9ebfa27c06dd60029', 
     gas: '4700000'
   }, function (e, contract){
    console.log(e, contract);
    if (typeof contract.address !== 'undefined') {
         console.log('Contract mined! address: ' + contract.address + ' transactionHash: ' + contract.transactionHash);
    }
 })
```

#### 3、部署合约

第一步： 获取abi信息

```
abi = [
	{
		"constant": false,
		"inputs": [
			{
				"name": "x",
				"type": "uint256"
			}
		],
		"name": "set",
		"outputs": [
			{
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [],
		"name": "get",
		"outputs": [
			{
				"name": "",
				"type": "uint256"
			}
		],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	}
]
```

第二步：myContract = web3.eth.contract(abi)

得到结果：

```
{
  abi: [{
      constant: false,
      inputs: [{...}],
      name: "set",
      outputs: [{...}],
      payable: false,
      stateMutability: "nonpayable",
      type: "function"
  }, {
      constant: false,
      inputs: [],
      name: "get",
      outputs: [{...}],
      payable: false,
      stateMutability: "nonpayable",
      type: "function"
  }],
  eth: {
    accounts: ["0xe81b6c3c341ddb3aa878125a7f5c02c31b385f9b", "0x13031a7529c0f6e64d72df709f484ba4c1816a55"],
    blockNumber: 16,
    coinbase: "0xe81b6c3c341ddb3aa878125a7f5c02c31b385f9b",
    compile: {
      lll: function(),
      serpent: function(),
      solidity: function()
    },
    defaultAccount: undefined,
    defaultBlock: "latest",
    gasPrice: 18000000000,
    hashrate: 0,
    mining: false,
    pendingTransactions: [],
    protocolVersion: "0x3f",
    syncing: false,
    call: function(),
    contract: function(abi),
    estimateGas: function(),
    filter: function(options, callback, filterCreationErrorCallback),
    getAccounts: function(callback),
    getBalance: function(),
    getBlock: function(),
    getBlockNumber: function(callback),
    getBlockTransactionCount: function(),
    getBlockUncleCount: function(),
    getCode: function(),
    getCoinbase: function(callback),
    getCompilers: function(),
    getGasPrice: function(callback),
    getHashrate: function(callback),
    getMining: function(callback),
    getPendingTransactions: function(callback),
    getProtocolVersion: function(callback),
    getRawTransaction: function(),
    getRawTransactionFromBlock: function(),
    getStorageAt: function(),
    getSyncing: function(callback),
    getTransaction: function(),
    getTransactionCount: function(),
    getTransactionFromBlock: function(),
    getTransactionReceipt: function(),
    getUncle: function(),
    getWork: function(),
    iban: function(iban),
    icapNamereg: function(),
    isSyncing: function(callback),
    namereg: function(),
    resend: function(),
    sendIBANTransaction: function(),
    sendRawTransaction: function(),
    sendTransaction: function(),
    sign: function(),
    signTransaction: function(),
    submitTransaction: function(),
    submitWork: function()
  },
  at: function(address, callback),
  getData: function(),
  new: function()
}

```

第三步： 复制Web3 deploy 到命令行

在这之前 请先登录 ```personal.unlockAccount(eth.accounts[0])```


```
simplestorage = simplestorageContract.new(
   {
     from: web3.eth.accounts[0], 
     data: '0x6060604052341561000f57600080fd5b5b60ec8061001e6000396000f30060606040526000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff16806360fe47b11460475780636d4ce63c14607b575b600080fd5b3415605157600080fd5b6065600480803590602001909190505060a1565b6040518082815260200191505060405180910390f35b3415608557600080fd5b608b60b6565b6040518082815260200191505060405180910390f35b60008160008190555081600a0290505b919050565b6000805490505b905600a165627a7a7230582026dec0f4d79b9f9ab28541921bdf54151e1aafa40e81612989b9ebfa27c06dd60029', 
     gas: '4700000'
   }, function (e, contract){
    console.log(e, contract);
    if (typeof contract.address !== 'undefined') {
         console.log('Contract mined! address: ' + contract.address + ' transactionHash: ' + contract.transactionHash);
    }
 })
```

得到结果

```
{
  abi: [{
      constant: false,
      inputs: [{...}],
      name: "set",
      outputs: [{...}],
      payable: false,
      stateMutability: "nonpayable",
      type: "function"
  }, {
      constant: false,
      inputs: [],
      name: "get",
      outputs: [{...}],
      payable: false,
      stateMutability: "nonpayable",
      type: "function"
  }],
  address: undefined,
  transactionHash: "0x13452c18ca799b216b715d397cae615bbbb0489908c25f878d2fb45bd783b08d"
}

```

第四步： 然后我们需要确认挖矿

```
miner.start()

等待一会，你会得到一条信息：
Contract mined! address: 0xdb385bc97ed9fbac62920102d5edc7c4bf993c79 transactionHash: 0x87400471a0e32edcfa9e1ca621d08a318e9abb85299d280deb8bc199e118427f
==> 就代表部署成功啦。

miner.stop()
```

### 4、合约交互

#### 第一步： 获取合约组件

```
MyContract = eth.contract(abi)
```

#### 第二步： 实例化合约

```testContract = MyContract.at(myContract.address)```

#### 第三步： 调用合约

```testContract.get.call(5)```

### 5、在电脑B 调用合约

确定两台电脑已连接成功。电脑B上新建用户，并解锁。

```
1. abi = [{constant:false,inputs:[{name:'a',type:'uint256'}],name:'multiply',outputs:[{name:'d',type:'uint256'}],type:'function'}]  //合约的abi
2. address = 0xdb385bc97ed9fbac62920102d5edc7c4bf993c79  // 合约地址
3. myContract = web3.eth.contract(abi).at(address)

```

### 6、通过web3 调用

#### 第一步 
使用npm 安装web3,执行 ```npm install web3```

#### 第二步
在当前目录下创建 ```connect.js``` 文件，内容如下：

```
var Web3 = require('web3');
var web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
web3.eth.getAccounts().then(console.log);
web3.eth.getBlockNumber().then(console.log);

```

可得到如下现实：

```
[ '0xe81b6C3C341Ddb3aA878125a7f5C02c31B385f9B',
  '0x13031a7529c0f6e64D72dF709f484BA4c1816A55' ]
10

```