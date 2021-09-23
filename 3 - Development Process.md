<div align="center">

# Development Process

![7f3b38ca460748e19cc501b700ba864e](https://user-images.githubusercontent.com/55017307/134577520-59bdb983-d365-45b8-be67-1608e5616032.jpg)

<br>

a decentralized application (Dapp) has some similarities with a web application but at the same time it's a little bit different so we'll be able to reuse some of the development technique of web development but we'll need to adapt them a little bit

in general in the world of software there are two ways to approach application design the first way is to start from the data layer and progressively build up to the UI, and the other way, where you start from the UI and progressively go down to the data layer.

well if your application is really data-intensive with the complex data models you probably want to start from the data layer otherwise you can start from the UI. it also depends if you have a background of back-end developer or front-end developer

understand your data model you main task will be to decide what you put on a smart construct and what you put outside
of the blockchain, so anything which is really critical to your application should be on th blockchain.

for example if you have any economy part and the payment system then should be at the blockchain also if you have any content that you want to protect against any censorship it should be on the blockchain either for things like user settings you can put them outside (AW3 server of IPFS)

If you use a centralized storage service (AW3) you can calculate the data fingerprint of these contents so you're gonna use some hashing function and you're going to store these hashes inside your smart contract. These hashes allow you to compare the data that is retrieved from the outside to what you have in the smart contracts, so if anybody tried to
tamper with this content outside the blockchain then you will be able to figure it out.

<br>

## list:

- write smart contracts

- deploy on local network

- test smart contracts on local network

- deploy on public testnet using infura

- test smart contracts on public testnet

- create front-end

- deploy on testnet

- manage your smart application

- monitor errors

- manage evolution of smart contract protocol

- governance, allow community to ote for the future of your protocol

</div>
