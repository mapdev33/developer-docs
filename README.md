# MAPO Protocol开发文档

本文档旨在帮助你认识MAPO，或使用它构建你想构建的去中心化应用，或将一条区块链接入MAPO实现与其他区块链的互通。该文档介绍了MAPO的概念，解释了MAPO技术堆栈，以及MAPO应用的使用案例。

基于开源的社区准则，你可以随时提出新的主题，添加新的内容，并在认为可能有用的地方提供示例。所有文档都可以通过github编辑，并会存储到去中心化存储设施`Arweave`。如果不确定如何操作，请遵循[说明进行](docs/editing-markdown.md)。

如果这是你第一次尝试MAPO开发，建议你从头开始阅读，这不仅可以让你更好的熟悉MAPO，其中涉及区块链底层的技术以及ZK等内容，也会让你对点对点的代码信任有一个全新的认识。


## 基础主題

+ [MAPO简介](docs/base/intro-to-mapo/index.md)-----MAPO简要介绍
+ [MAPO币](docs/base/intro-to-mapo/mapo-coin.md)-----MAPO币简要介绍
+ [全链去中心化应用](docs/base/omnichain-dapp/index.md)------覆盖各种区块链的去中心化应用介绍
+ [全链应用与单链或多链应用的区别](docs/base/omnichain-dapp/different.md)----基于跨链技术带来的差异
+ [第三方信任跨链与点对点跨链方案区别](docs/base/omnichain-dapp/the-other.md)----基于技术方案带来的差异
+ [帐户](docs/base/accounts/index.md) – 网络中能够持有余额和发送交易的实体
+ [交易](docs/base/transactions/index.md) – 转账和其他导致MAPO状态变化的行为
+ [区块](docs/base/block/index.md) – 交易分批进行，以确保状态在所有行为者之间同步
+ [MPT树](docs/base/mpt/index.md) - MAPO使用的基础数据结构
+ [RLP编码](docs/base/rlp/index.md) - 递归长度前缀编码
+ [Gas费用](docs/base/gas/index.md) – 交易处理所需的算力，由交易汇款人使用 MAPO 支付
+ [消息跨链](docs/base/cross-chain-message/index.md) - 介绍跨链消息的基本原理
    + 资产跨链 - 介绍资产跨链的流程
+ [轻客户端](docs/base/light-client/index.md) - 轻客户端的功能介绍及在MAPO跨链中的作用
  + 什么是轻客户端  -- spv
  + 典型的轻客户端 -- 一些链的轻客户端(eth,btc)
  + MAPO轻客户端   -- 状态同步，交易验证等
+ [全链开发组件层MOS](docs/base/mos/index.md) - MOS层处理MAPO跨链网络上的所有计算操作
    + Vault - Vault合约基本功能
    + Messenger - 跨链消息的监控与路由
+ [中继链(atlas)](docs/base/mapo-relay-chain/index.md) - 基于POS共识的EVM兼容区块链网络
    + 节点即服务
    + 节点架构
        + 中继链（atlas）架构 - 区块和交易结构
        + 创世配置 - 介绍创世配置文件
        + 共识机制 - 中继链各节点如何就当前状态达成共识
        + 预编译合约 - 支持的预编译合约
        + Marker工具 - atlas的简易客户端工具
    + 部署节点  - 包括公共RPC节点
      + 归档节点（中继链）
      + 引导节点（中继链）
      + 验证节点 （中继链）
      + RPC节点（中继链）
    + [公共网络](docs/base/mapo-relay-chain/public-service.md) - 公共网络服务信息，包括主网，测试网，测试网水龙头,区块浏览器，公共RPC服务地址
    + 搭建私有网络 
+ [Compass(maintainer，messenger)](docs/base/Compass/index.md) - 消息跨链的重要组件，用于更新轻客户端状态及消息路由
    + Compass - 架构及模块说明
    + Compass配置参数
    + Compass环境与部署
    + Compass二次开发 - 基于compass定义自己的路由服务

## MAPO技術堆棧

+ [堆栈](docs/mapo-stack/stack/index.md) - mapo/全链web3堆栈介绍
+ [EVM兼容](docs/mapo-stack/compatible-evm/index.md) - mapo跨链验证智能合约
  + [智能合约语言](docs/mapo-stack/compatible-evm/solidity.md)
  + [智能合约结构](docs/mapo-stack/compatible-evm/anatomy.md)
  + [智能合约库](docs/mapo-stack/compatible-evm/libraries.md)
  + [编译智能合约](docs/mapo-stack/compatible-evm/compile.md)
  + [测试智能合约](docs/mapo-stack/compatible-evm/testing.md)
  + [部署智能合约](docs/mapo-stack/compatible-evm/deploying.md)
  + [可组合性](docs/mapo-stack/compatible-evm/composability.md)
  + [智能合约安全性](docs/mapo-stack/compatible-evm/security.md)
  + [智能合约形式化验证](docs/mapo-stack/compatible-evm/formal-verification.md)
  + 开发架构 - 支持mapo智能合约开发的工具
  + 开发网络 - 用于智能合约部署前测试互操作性的本地区块链环境
+ 实现跨链互通 - 一个第三方区块链网络如何实现接入mapo的跨链网络
  + EVM兼容链的跨链互通 - 两条链互通的基本架构及流程
    + 轻客户端验证 - 基于solidity智能合约的轻客户端部署，升级及验证,
    + 轻客户端状态更新 - 使用maintainer来维护轻客户端的状态
      + maintainer增加对新区块链支持 - 二次开发增加对新链支持
      + 部署maintainer 
    + MOS层 - 支持全链应用开发的基础服务层
      + MOS结构与接口
      + 全链应用调用过程 - 一个消息跨链(资产跨链)调用的完整流程
      + MOS层的部署与升级
  + 非EVM兼容链的跨链互通
    + mapo端轻客户端验证 - 根据目标链共识机制实现一个轻客户端并部署到mapo中继链
    + 目标链端轻客户端验证 - 根据mapo中继链的共识机制实现基于目标链的轻客户端
    + MOS层 
      + 目标链端MOS结构与接口 - 定义及实现基于目标链平台的MOS结构与接口
      + mapo端的MOS层  - mapo端的mos层的部署与升级
+ 如何开发跨链应用 - 如何开发一个基于mapo跨链网络的全链dapp
+ SDK/API - mapo支持的API
  +  [MOS接口](docs/sdk/mos/index.md)
  +  轻客户端接口
  +  中继链RPC
     +  json-rpc
     +  [javaScript sdk](docs/sdk/mapo-relay-chain/javaScript.md)
     +  go-sdk
     +  公共RPC服务
  + 后端API
    + 浏览器API
    + 数据统计与分析API


## 零知识证明(zk)


## 入门开发教程

+ 全链dapp开发视频及例子
+ 开发者入门例子 - 包括环境配置，开发工具选择，合约代码示例




