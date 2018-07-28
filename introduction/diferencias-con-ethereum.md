# Differences with Ethereum

{% hint style="info" %}
Source and acknoledgement: [https://steemit.com/eos/@trogdor/eos-vs-ethereum-for-dummies](https://steemit.com/eos/@trogdor/eos-vs-ethereum-for-dummies)
{% endhint %}

### Introduction 

Not long after the launch of Bitcoin, savvy individuals began to recognize that the technology behind Bitcoin has vastly greater potential than simply as the basis for a new electronic currency. In fact, within just a few years of Bitcoin's development, dozens of new decentralized applications have been built upon the same type of public ledger blockchain technology behind Bitcoin. Just a few of these decentralized applications include encrypted messaging \(Bitmessage\), decentralized exchanges \(Bitshares\), trustless gambling/betting \(Peerplays\), cloud computing \(Golem\), and of course social media \(Steem/Steemit\). One challenge for innovators and app developers in this new blockchain economy is the difficulty of actually building a new blockchain application from scratch. On top of that, with traditional Proof-of-Work \(POW\) and Proof-of-Stake consensus mechanisms, the security of the network and application depends on a large amount of hashing power and/or a large distribution of network tokens. For small business owners and startups, these challenges make the barrier to entry impractically high. There is no way a small startup company can independently fund a widely distributed, powerful computer network to secure their application.

Of course, other consensus mechanisms such as Delegated Proof-of-Stake \(DPOS\) can be operated by a relatively small number of processors without the same network security concerns, although other concerns would still be present for those developers, including achieving a large distribution of network tokens, and of course developing all of the cryptography and blockchain technology to interact with their application. For a comparison, imagine if every computer game designer had to both build a computer from scratch specifically to run a given game, and at the same time they had to develop a game specific operating system to communicate instructions between the game and the computer. It is likely that with such a design model, the vast majority of games and applications would never be built.

In order to solve this problem, the idea of smart contract platforms was developed and implemented, by far the most successfully, by the Ethereum network. Ethereum can be thought of as a decentralized platforms for developing and running decentralized applications \(DAPPs\), with the benefit that users can be sure that those DAPPs will run exactly as programmed without interference from third-parties. Currently, the Ethereum network has a market cap of around $30 billion \(USD\), testifying to the demand for smart contract platforms.

Recently, Dan Larimer \(inventor of Bitshares, Graphene, and Steem/Steemit\), along with the eos.io team, announced the development of EOS, a consensus blockchain operating system that provides databases, account permissions, scheduling, authentication, and internet-application communication to app developers. Thus, EOS will provide developers the tools they need so that they can focus on the specific business logic for their application, without worrying about the cryptography implementations or communication with the decentralized computer \(i.e. blockchain\). Furthermore, EOS will use parallelization to make possible blockchain scalability to potentially millions of transactions per second.

In this post I will describe some of the differences in technological capabilities and limitations, as well as differences in design philosophies between the EOS and Ethereum platforms.

### What's contained in this post?

* Chapter 1: What is a smart contract?
* Chapter 2: Design philosophy
* Chapter 3: Consensus mechanism and governance
* Chapter 4: Scalability
* Chapter 5: Denial-of-service attacks
* Chapter 6: Economics of the networks: burning fees vs. owning a stake 

### Chapter 1: What is a smart contract?

  
For those who are very new to the ideas of cryptocurrencies and blockchain technology, it is first of all most important to understand exactly what a blockchain is. Essentially, a blockchain is a decentralized system, at the heart of which is a public ledger. A ledger is basically a way to account for the current state of the system \(e.g. how much cryptocurrency is held in each account\). Along with the public ledger, blockchain technology includes a consensus mechanism which dictates how the decentralized computer \(i.e. the network of computers running the blockchain\) updates the current state of the public ledger.

As a fun piece of history, a cryptographer named Nick Szabo realized in 1994 that a decentralized ledger system could be used to execute smart contracts \(also called self-executing contracts\). Mr. Szabo actually coined the phrase "smart contracts" with the goal of incorporating contract law practices into the design of electronic commerce protocols operating between strangers across the internet.

Smart contracts can facilitate the transfer and exchange of money or property in a transparent way, all while avoiding the services of a middleman.

Smart contracts also define all of the obligations and potential penalties involved in an agreement, much like traditional contracts do, but the smart contract platform also automatically enforces all of these obligations and penalties. These smart contract platforms essentially allow the development of decentralized applications to run on the network. Ethereum is currently by far the largest and most successful platform for decentralized applications, but the new platform EOS will seek to solve several of the challenges faced by the Ethereum network.

### Chapter 2: Design philosophy

![](https://steemitimages.com/0x0/https://steemitimages.com/DQmfQC3Q7NvUxKxwdj93nNZgFJnsAYQMxtCA9cbf88KRTjX/Slide1.PNG)

One of the key differences between EOS and the Ethereum network is in the design philosophy behind the networks. The Ethereum network could almost be described as application-agnostic, i.e. it is specifically designed as a neutral platform for all potential applications. In this way, as stated by the Ethereum Design Rationale document on github: Ethereum has "no features", refusing to build in "even very common high-level use cases as intrinsic parts of the protocol." This rationale reduces bloat among applications, but it also requires many different applications to reuse code, and efficiency gains for app developers could certainly be realized if certain more common functionalities were provided by the platform itself.

In contrast to this approach, EOS recognizes that many different applications require the same types of functionalities and seeks to provide those functions, such as implementations of the cryptography and app/blockchain communication tools needed by many applications. With this philosophy, EOS will feature the introduction of generalized role-based permissions, a web toolkit for interface development, self-describing interfaces, self-describing database schemes, and a declarative permission scheme. It is my understanding that these functionalities, provided by EOS, will be especially powerful for simplifying user account generation and management, as well as security issues like declarative permissions and account recovery.

### Chapter 3: Consensus mechanism and governance

![](https://steemitimages.com/DQmV8BJqXQXVqLAM7VqR6hWt8HdgUY1vzPGG2XGqQWoZ7oT/Slide2.PNG)

Another significant difference between EOS and Ethereum is in the blockchain consensus mechanism and overall blockchain governance approach. Whereas Ethereum uses Proof-of-Work \(and will soon switch to hybrid Proof-of-Work/Proof-of-Stake\), EOS will use Graphene technology that utilizes the Delegated Proof-of-Stake \(DPOS\) consensus mechanism. This choice has significant importance for commercial scalability, which will be addressed in the next chapter.

One issue with the current Proof-of-Work implementation behind the Ethereum network is the difficulty in fixing broken applications. For example, recently the DAO suffered a critical bug/hack/failure. It's important to note, that those with the "code-is-law" mentality consider the DAO hack to be a "feature", not a failure, and that users simply should have been more responsible to understand the code more carefully. In any case, the DAO failure showed that broken applications on Ethereum either result in investors facing potentially substantial losses or in disruptive hard forks. With the current Proof-of-Work consensus mechanism of Ethereum, each hard fork also results in a risk of spawning multiple competing chains, as happened with the Ethereum, Ethereum Classic split following the DAO failure. Furthermore, in order to fix a broken application, a disruptive hard fork is required which disrupts the entire Ethereum network.

In contrast, EOS includes a mechanism to freeze and fix broken or frozen applications. For example, if the DAO had been implemented on EOS, it could have been frozen, fixed, and updated without disrupting the other EOS applications. Furthermore, the DPOS consensus mechanism of EOS has no potential for spawning multiple competing chains during a hard fork. This is evidenced by the 18 successful hard forks experienced by the Steem network, which also runs on Graphene technology. Furthermore, EOS will include a legally binding constitution that establishes a common jurisdiction for dispute resolution, and it will also include self-funded community benefit applications that will be selected by stake-weighted voting.

### Chapter 4: Scalability

![](https://steemitimages.com/0x0/https://steemitimages.com/DQmdrre6WZJLychsHpCsQWo7Uf2sYLrzMGM3E3wbMgc5KAK/Slide3.PNG)

In order to consider a platform as commercially viable, scalability is of utmost importance. This is one key area where EOS and Ethereum will differ. Currently, the Ethereum network is limited by the single threaded performance of a CPU. Early test networks achieved 25 transactions per second \(in somewhat optimized conditions\), which could likely be increased to 50 or 100 tx/s with optimizations. However, under load from real applications, the current transaction limit of the Ethereum network is likely 10 tx/s or less. In the past, the network has been overwhelmed and overloaded with transactions to the point that all but the highest-fee transactions were rejected. This is especially obvious during recent Initial Coin Offerings, such as the Status ICO, in which the network was completely overwhelmed and the ETH tokens suffered a massive flash crash. Note that Vitalik Buterin has laid out a roadmap to "unlimited scalability" which heavily relies on the concept of sharding. As far as I understand \(which is NOT well\), sharding is a technologically challenging concept that certainly increases the complexity and attack surface of the network, and potentially lowers the security of the network. _I am in no way discounting sharding as a viable approach to successfully scale the Ethereum network, and it is likely that it will be successfully implemented to achieve reasonable gains in scalability._

However, in terms of scalability, EOS will have two significant advantages over the Ethereum network, and once implemented, EOS will likely be on the only platform that can handle truly commercial-scale decentralized applications. First, EOS will rely on Graphene technology, which has been shown in stress tests to achieve 10,000-100,000 transactions per second. Secondly, EOS will use parallelization to scale the network, likely up to millions of transactions per second. If these benchmarks are realized, EOS should be able to support thousands of commercial scale DAPPs. EOS will use asynchronous communications and separate authentication from execution to achieve speedups, and because it will have no transaction fees, EOS also does not require counting operations.

### Chapter 5: Denial-of-service attacks

![](https://steemitimages.com/DQmSxgwQmHMcUUATQy4rsARReptRTJ2jxYiZbjFFFe8azpB/Slide4.PNG)

Related to the scalability of the network, it is also important to discuss potential attack vectors to the network. In this chapter, I will briefly discuss the potential for denial-of-service type attacks. This type of attack is when a malicious attacker spams a network with traffic in order to prevent legitimate traffic from getting through. It is my understanding that the Ethereum network has been proven to be vulnerable to such DOS attacks, while EOS should be invulnerable to such attacks.

In the Ethereum network, it is well-known that miners preferentially select high-fee transactions to add to the blockchain. Since there is finite bandwidth and computing power in the network, it is easy to imagine a scenario in which the network is spammed with many high-fee transactions, effectively blocking out many lower-fee legitimate transactions. You might think that typically this would be an expensive attack to execute on the network, but there are situations where there are financial incentives to do so. For example, with the recent Status ICO, it was effectively a race to contribute funds to the ICO smart contract in order to effectively receive the ICO tokens at a huge discount. This created an incentive for wealthy players to spam the network with high-fee transactions in order to ensure that their transactions went through. However, this creates a serious weakness for the Ethereum network, since a single application or smart contract can effectively freeze out the entire network.

In contrast, EOS should not be vulnerable to DOS attacks. The ownership of EOS tokens gives users a proportional stake in the network bandwidth, storage, and computing power. Therefore, spammers can only consume the proportion of the network that their EOS tokens entitle them too. DOS attacks may be possible on a given application, depending on the apps design, but those attacks can never disrupt the entire network. Startups with a very small stake invested in the network will have guaranteed, reliable bandwidth and computational power, even if many other malicious actors try to spam several large network apps.

### Chapter 6: Economics of the networks: burning fees vs. owning a stake

![](https://steemitimages.com/0x0/https://steemitimages.com/DQmSRV6uCBVr9XfS6CyVgkag9TWntUNDu1cUCNDg1WWGThf/Slide5.PNG)

Finally, I want to briefly discuss the different economic models of the EOS and Ethereum networks. Essentially, this is a comparison between and ownership model and a rental model. With Ethereum, gas fees are required in exchange for every calculation, storage operation, and bandwidth utilization. Furthermore, the required fees fluctuate and can spike prohibitively high as miners preferentially select transactions with the largest fees. This was especially obvious during the recent Status ICO, in which $100 gas fees were still too small, even for trivial transactions. Furthermore, as discussed in the previous chapter, this economic model creates a scenario in which rich actors can potentially freeze the entire network by flooding it with high-fee transactions. Furthermore, this model requires developers and startups to continuously burn gas fees throughout development and deployment of their applications.

In contrast, EOS will utilize an ownership model, in which holding EOS tokens gives users a proportional share in the network bandwidth, storage, and processing power. This means that if someone owns 1% of the EOS tokens, they will always have access to 1% of the network bandwidth, regardless of the load on the rest of the network. In this way, small startups and developers can purchase a relatively small part of the network in order to receive reliable, predictable network bandwidth and computing power, and simply purchase more EOS tokens when they need to scale up their application. Furthermore, since the network will have zero transaction fees, there is no network development cost, except for the initial purchase of EOS tokens. However, these can of course always be sold in order to reclaim the initial investment if desire.

### Conclusion

  
Of course, I am a strong believer in Graphene-based technologies, largely because of their impressive scalability and minimal transaction fees. I recognize this post has had an obvious EOS bias, but keep in mind that Ethereum currently has a viable product with a market cap of ~$30 Billion, while EOS is still under development with a current market cap of $0. If you want my honest opinion, I am bullish on both EOS and Ethereum, and I believe once EOS is launched, both platforms will still have tremendous room to grow. Plus do not consider anything in this post to be investment advice, and remember to always do your own due diligence and research!

