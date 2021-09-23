<div align="center">

## Best Practices

![matic-1536x1106](https://user-images.githubusercontent.com/55017307/134569376-bf5f054a-5c5d-4488-8767-c887812cc124.png)

**12-factor applications:** best practices to follow in modern web application, widely respected in industry

this is not enough for dapps

</div>

---

## 1 - You should NOT take control of your user's private key

the whole point of the blockchain security is to not have any centralized vulnerability.

if you store the private keys of your user to sign transactions on their behalf this creates a honey pot for hacker and eliminates the security guaranteed of the blockchain for your users

---

## 2 - You should NOT sign transactions on behalf of your users from a central server

in order to minimize gas cost and improve usability it can be tempting to move the signing of ethereum transactions from user browsers to a central server. In this case the application authenticates users with a traditional username password mechanism and sends ethereum transaction on behalf of the users on a central server using the private key controlled by the application.

there are two problems with this: first you need to trust that the application will not maliciously assign transactions that were not approved by the user, and second, the private key control by the application creates a honeypot fo hackers they only need to hack one server to hack all user.

There is an exception to this rule if you user signed messages with their private keys and the server only acts as a proxy who broadcast transaction with the signed messages of users. (example DEXs)

there isn't much at risk on the server. At worst hackers can stop the broadcasting of transaction to the blockchain but they cannot modify the signature of users and falsify their intent.

---

## 3 - you should put all your critical data & code on the blockchain

because storing and manipulating data on the blockchain is expensive you don't want to put all your data on a smart contract actually must up only put a small fraction of the data on the blockchain. However even if you don't put everything on the blockchain you still need to make sure that both the critical code and the data are indeed on chain.

it's up to you to know what is critical or not for your application but usually everything related to the economy or the governance of your data is critical on the contrary files user settings and metadata have less importance

---

## 4 - You should always run security tools on your contracts

security is a really big deal when developing smart contracts.

they can manipulate real money and they are immutable which means they cannot be updated, so if a hacker finds a bug in your code he or she could drain your smart contract of all its funds.

security tools like mythrl can catch the low-hanging fruits for you, still once your project reaches a certain scale you should hire a professional team to do a full audit of your code.

---

## 5 - You should always deploy your dapp on a public testnet before mainnet

testnets are safe-boxes.

you can use fake ether without any real-world consequences, compared to a local development environment it is closer to production which is the main-net.

it is quite common to find bugs on test net that did not happen on your local development environment.

deploying your Dapp on a public testnet does not guarantee you that you won't have bugs, but at least you users won't accuse you of having skipped the public tested phase

---

## 6 - You should use ETH addresses to identify users

in Dapps like in most applications you will probably need to identify your users to enforce access control, on most web applications users are identified using either a username or email however in the case of dabs we want to avoid dealing with data generated from outside the blockchain.

users can generate as many addresses as they want using their wallet, the dresses are often represented with their exo-decimal form, they can not only be used for signing transactions but also just for signing messages which can be verified outside the blockchain.

when your smart contract receives a transaction, it guarantees you that the value of msg.sender will be the signer
of the transaction. You should use this to implement access control.

You can still associate an Ethereum address to an off chain generated user ID on a central server, but you should not use this user ID to do any critical computation. It should just be used for convenience

---

## 7 - You should explain the update mechanism of your contract

the code of a smart contract is immutable, however developers often need to update the code of the application to fix bugs and add new features.

How can they do this with a smart contract? the solution to this is to make your contract updatable.

there are different solution to this but the cleanest way to do it is to use the proxy pattern with two smart contracts: a proxy smart contract and an implementation smart contract.

users send a transaction to the proxy smart contract which itself forwards everything to the implementation smart contract. This is the smart contract that implements the logic of manipulating data.

when you need to update your smart contract logic you will first deploy a new implementation smart contract and then call a function on a proxy contract that updates the address of the implementation smart contract.

future calls to the proxy contract will forward to the new implementation smart contract and ignore the old implementation contract.

the problem with the above pattern is that it breaks the promise of immutability of code.

on a blockchain in order to mitigate this you can implement a governance system to establish clear rules on who or what can trigger a smart contract update on a proxy smart contract. In any case you should be very explicit about this
mechanism.

Don't fool your user into thinking that your smart contract code will never change even though you put in place an update mechanism principle

---

## 8 - You should explain how external data is collected

often time our Dapp need to use data that is external to the blockchain like stock prices results from external API etc.

this poses a problem because the blockchain does not know how to fetch data from the outside world.

The solution to this is to feed a smart contract with outside data, once the data is inside smart contract, it can be used inside the blockchain that is what we call the oracle.

however the oracle poses a problem because a hacker could hack the external entity that fits data to the blockchain to change the result of a computation.

mechanisms needs to be disclosed clearly to users so that they understand clearly what can influence the computation of the smart contract and what are the security risk of your Dapp.

---

## 9 - You should verify your smart contract on etherscan

the code of a smart contract is always public and anybody can read it to make sure that they agree with what is inside, however when users interact with a smart contract all they have at their disposal is an ethereum address and the vague promise that the code of this address is what the Dapp developers claim it to be.

Etherscan has a feature to verify that a smart contract has the source code it claims to have.

that is not a foolproof solution because Etherscan could be hacked or become malicious but it's still better than nothing

---

## 10 - You should show feedback to users while a transaction is mining

blockchain loading times are not only worse but also have a different nature: first on ethereum a transaction takes about a 15 second to be mined or added to the blockchain.

in ethereum there is no finality after a data change, which means we cannot say that now the blockchain has acknowledged my transaction forever.

blockchain is vulnerable to what we call 'block reorganizations' which means you are never sure that the chain that contains you transaction will be the chain that win in the long, run maybe another part of the network was mining faster than on new part of the network and your transaction will be discarded by the alternative chain.

in reality these block reorganizations happen rarely and when they do they only happen for the latest one or two blocks, that means that you need to wait a few blocks to be sure that your transactions won't be cancelled and the more blocks you wait the more certain you will be that there won't be any adverse block reorganization that will cancel your transaction.

what does this mean in terms of UI?

you need 2 kind of UI confirmations: first after you send a transaction you need to show to the user that the transaction was sent, then after the first few confirmations you need to show the user that there was an extra confirmation. After each confirmation you should show a link to etherscan for the transaction.

This makes the user feel safe that the transaction has been sent.
