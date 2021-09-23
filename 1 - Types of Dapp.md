<div align="center">

## Building Blocks of All Architectures

**smart contracts** on the blockchain that's really the coe of your decentralized application (Dapp)

**wallet** where users will store the private key that will allow them to send transaction to the smart contract and modify its data

**frontend UI** allows user to interact with the smart contract in an easy way (web or mobile application )

---

## Pure Dapp

![pure](https://user-images.githubusercontent.com/55017307/134560596-86e342eb-cff8-42c4-a271-b9b2636f5e1a.png)

<br>

all decentralized.

front-end is not served from a centralized server but instead is served from a decentralized file system like IPFS

it's not possible to hack into a centralized server or restrict access to the centralized servers so that the
front end is not available. In this case everything is absolutely decentralized: the purest form.

very few dapp works that way.

---

## Common Dapp

![common](https://user-images.githubusercontent.com/55017307/134563927-ca764f01-94a6-42da-a87a-76c7fd1df0f1.png)

<br>

web front-end is not served from IPFS but it's served from a centralized server.

The important component of your Dapp are still decentralized (smart contracts)

sine the front end is serve from a centralized place so you have a vulnerability

---

# Backend + TX broadcast

![3](https://user-images.githubusercontent.com/55017307/134560610-ad81dd69-c451-4556-b451-e45e9a7c0575.png)

<br>

in this architecture you still have your smart contract, you have your front-end, yo have your back-end that serve the front-end.

users sign transaction on the front-end but don't send them directly to the blockchain but instead they send a transaction to the backend the backend is going to make sure that the transaction is correct and is going to broadcast this to the ethereum network.

why don't user directly send transactions themselves?

well it can be that we want to protect users, for example they might do some some transactions that are they are not correct and they
or make a mistake that will cost them lots of money, so by checking & broadcasting their requests on the blockchain we make
sure that everything is correct.

this makes the system less decentralized because if the backend is compromised then the centralized application will
not work.

it's still somewhere acceptable because users can always decide to to send a transaction themselves to the ethereum network so the back end does not have much of power but it is still a bit more more centralized under the previous architecture

---

# back-end + signature

![4](https://user-images.githubusercontent.com/55017307/134563933-24bb3be6-fd0f-4d4e-897d-8566cc78446c.png)

<br>
this architectural clients don't directly create and send transaction from the front end to the blockchain but instead what they will do is that they will create a message that describe the change that they want to make on a smart contract and they will sign this message and they will send everything to the backend.

the backend is gonna make sure that everything is fine and it's going to create an Ethereum transaction embedding the signature of the front-end and send it to to a smart contract.

the smart contract is going to do a few things: first it's going to make sure that the transaction come from the wallet of the back-end and it's going to make sure so that the signature of the end-user is correct, so there is no way for the backend to to fake the user to cheat the system.

this system is very used for example by decentralized exchanges.

you don't send you order directly to the smart contract but in general there is an option order book.

the big advantage of this architecture is that end-users they don't have to pay for transaction costs!

All they have to do is to sign messages and and then the transaction cost is going to be supported by the backend while it of the decentralized
application

the vvulnerability lies in the fact that if the back-end server is a hacked it can change all the data (in server, not blockchain)

is not possible for the hackers to forge user signature so it still remain quite safe and it's like a good compromise between the decentralization and need of the centralized application and also the practicality of that we need in production

---

# back-end + centralized wallet

![5](https://user-images.githubusercontent.com/55017307/134560646-6e22c219-d77e-497f-bb3c-0e2c884fd790.png)

<br>

there is absolutely no wallet on the front end users will interact with the back end like a normal web application and probably that they will send some money to the back end with normal system like like PayPal or bank account or credit card and then after they've been identified they'll be able to take some action on the blockchain.

the backend will create transactions on behalf of the user but it will not use the private key of a future it will use the private key of the of the backend and so the problem of this system is that it's actually not very decentralized.

yes, there is an interaction with a smart contract but the end-user is not capable of controlling that part since it's entirely dedicated to to the backend.

so if you work with a company that designed to shut down your account then then you will lose all your access to you to the Dapp also if this is hacked then it can be a big problem.

however there is a big advantage with an architecture like this: is much easier to onboard users because they don't have to install a wallet on the front-end, they don't have to buy some ether or make transactions on the blockchain

Beginner friendly

example: Coinbase

___

notes from this playlist https://www.youtube.com/playlist?list=PLbbtODcOYIoFAQPcXQ-O84sMkuk780gP_