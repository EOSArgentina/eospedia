# Oracles

{% hint style="info" %}
Sources:   
[https://blockchainhub.net/blockchain-oracles/](https://blockchainhub.net/blockchain-oracles/)  
[https://cointelegraph.com/explained/blockchain-oracles-explained](https://cointelegraph.com/explained/blockchain-oracles-explained)
{% endhint %}

### Introduction

An oracle, in the context of blockchains and smart contracts, is an agent that finds and verifies real-world occurrences and submits this information to a blockchain to be used by smart contracts.

Smart contracts contain value and only unlock that value if certain pre-defined conditions are met. When a particular value is reached, the smart contract changes its state and executes the programmatically predefined algorithms, automatically triggering an event on the blockchain.

Blockchains cannot access data outside their network. An oracle is a data feed – provided by third party service – designed for use in smart contracts on the blockchain.  The primary task of oracles is to provide these values or conditions to the smart contract in a secure and trusted manner. Such condition could be any data like weather temperature, successful payment, price fluctuations, etc.

Oracles are part of multi-signature contracts where for example the original trustees sign a contract for future release of funds only if certain conditions are met. Before any funds get released an oracle has to sign the smart contract as well.

### The Need for Oracles

There is a fundamental difference of formats. [Blockchain](https://cointelegraph.com/tags/blockchain) is deterministic, meaning that is a reflection of a specific series of events which take place one after another in sequential order - series of transactions. Accessing information outside of the chain would require data points that are not sequential, and would therefore be impossible for Blockchain to use or make sense of. This aspect of Blockchain gives it immutability, but reduces flexibility.

The off-chain world, however, is non-deterministic, meaning that there is no recording of the events in the specific sequence that they have taken place, which creates problems with transparency. Data points can be generated from and understood at any point, providing increased flexibility, but difficulty in communicating with the Blockchain.

This foundational distinction makes the two worlds incompatible with each other by default, and only the presence of an oracle can make two-way communication between them possible.

### **Types of oracles**

There are different types of oracles based on the type of use. We differentiate between software oracles, hardware oracles, consensus oracles and inbound and outbound oracles.

* **Software Oracles** Software oracles handle information available online. An example could be the temperature, prices of commodities and goods, flight or train delays, etc. The data originates from online sources, like company websites. The software oracle extracts the needed information and pushes it into the smart contract.
* **Hardware Oracles** Some smart contracts need information directly from the physical world, for example, a car crossing a barrier where movement sensors must detect the vehicle and send the data to a smart contract. Another use case is RFID sensors in the supply chain industry. The biggest challenge for hardware oracles is the ability to report readings without sacrificing data security. [Oraclize](http://www.oraclize.it/) proposes a two-step solution to the risks, by providing cryptographic evidence of the sensor’s readings and anti-tampering mechanisms rendering the device inoperable in the case of a breach.
* **Inbound Oracles** These provide the smart contract with data from the external world. Example use case will be an automatic buy order if the USD hits a certain price.
* **Outbound Oracles** These provide smart contracts with the ability to send data to the outside world. An example would be a smart lock in the physical world which receives a payment on its blockchain address and needs to unlock automatically.
* **Consensus Based Oracles** Prediction markets like Augur and Gnosis rely heavily on oracles to confirm future outcomes. Using only one source of information could be risky and unreliable. To avoid market manipulation prediction markets implement a rating system for oracles. For further security, a combination of different oracles may be used, where for example 3 out of 5 oracles could determine the outcome of an event.

### **Security Challenges**

Oracles are third party services which are not part of the blockchain consensus mechanism. The main challenge with oracles is that people need to trust these sources of information. Whether a website or a sensor, the source of information needs to be trustworthy. Different trusted computing techniques can be used as a way of solving these issues. Companies like [Oracalize](http://www.oraclize.it/), for example, have been leveraging Amazon with the [TLSNotary](https://tlsnotary.org/)-based proofs. Town Crier, another company, is focusing on the utilization of the Intel [Software Guard Extensions](https://software.intel.com/en-us/blogs/2013/09/26/protecting-application-secrets-with-intel-sgx) \(SGX\). Providing smart contracts with trusted information sources is crucial for the users because in case of mistakes there are no rollbacks.

