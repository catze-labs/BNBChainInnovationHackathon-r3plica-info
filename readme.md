# BNB Chain Innovation Hackathon
# r3plica: Mirror Your Gaming Soul

![image](https://user-images.githubusercontent.com/104552234/208289569-840536df-dcac-4caa-a580-058f5667a20a.png)

## Table of Contents
0. [Links](#links)
1. [Abstract](#abstract)
2. [Key Concept](#keyconcept)
3. [Account Abstraction](#aa)
4. [fSBT](#fsbt)
5. [References](#references)
6. [Glossaries](#glossaries)
7. [Expectations and differences from existing solutions](#expectdiffer)
8. [References](#references)
9. [Methodology and Functionality](#methodfunction)
10. [Architecture](#architecture) 

## Links <a name="links"></a>

![](https://lh5.googleusercontent.com/jCWqRkskqIszwUw1JAeo95xNsE8kq7t3Gkg-hQgh5v6ZSSSI221kP0m-vwyYEjEmWVDnKlBIHwQiah_0esrebsRE6zUuzwWzkq2oyrjymfSXc4J44M9tyEq7ttUsugphy9bV09Nu4F7c13zVlvmtGEkMopfR3C7Dflycaf8FC-N1L3gygTj4--61AXQ)

Our BEP-179 is live! : https://github.com/bnb-chain/BEPs/pull/179

Website : https://r3plica-web.vercel.app

Game Client: https://github.com/catze-labs/r3plica-unity-public

Game Server: PlayFab

Front-end: https://github.com/catze-labs/r3plica-web

Back-end: https://github.com/catze-labs/r3plica-server

Blockchain: bnb-chain/BEPs#179

Protocol: https://github.com/catze-labs/futureSBT

## Abstract <a name="abstract"></a>
r3plica is an SDK that uses fSBT to enable transactions to be used as n times as specified in the Smart Contract. The primary goal of the r3plica SDK is to provide users with complete data ownership over their assets and experiences. One of the biggest obstacles preventing gamers from trying blockchain games is Web3 accounts and their lack of understanding of the Web3 ecosystem.

An important feature of blockchain games is that players can fully record their experiences and assets on the blockchain. In order to address these issues, r3plica has introduced a token called fSBT, which limits the number of executable transactions. Games that utilize the r3plica SDK can offer the following characteristics

### SBT vs fSBT
|  | SBT | fSBT |
|--|--|--|
| Trasnfer-able? | Not available | Limited number of times available |
| Token Owner Account | User | Can be delegated at first |
| User's point of mint | Not free | Free |
| User's wallet address | Needed | Not needed at first |
| Storage of Assets | Not available | Available |
| Community Recovery | Available | Available |
  

## Key Concept <a name="keyconcept"></a>

### SBT

Weyl, Ohlhaver & Buterin (2022) proposed the concept of SBT (Soul Bound Token). The term "Soul Bound" is derived from the MMORPG game World of Warcraft and means that it is affiliated with a specific user. Here, affiliation means that ownership cannot be transferred. The first usage example presented in Weyl, Ohlhaver & Buterin's (2022) proposal involves cases where the anonymity of the blockchain is a hindrance to the blockchain community. The aim was to solve this problem through SBT and to further strengthen the decentralized community. However, this can be seen as a concept that conflicts with the anonymity of the blockchain. As a result, there is ongoing discussion within the blockchain community about SBT and its uses. In other words, SBT is a relatively new concept that has not yet become a widely used standard. The discussion that r3plica focuses on in relation to SBT is as follows.

### SBT of stolen accounts

The discussion on how to handle SBT in a wallet that has been compromised and is no longer safe due to some reason. POAP, which has a similar concept to SBT, has chosen to make token transferability possible (Turley, 2020).

### Community recovery wallet

The community recovery wallet is a concept that starts from the premise that a third party guarantees the identity of the user. The traditional key authentication method has inconveniences due to loss, theft, hacking, etc. Loopring is an example of an implemented idea that aims to improve this inconvenience. The concept is that the user can recover another wallet with a third party or another wallet of their own (Loopring, 2022; Buterin, 2022).
    
### Transferability of SBT
  
There are opinions that SBT should be accepted as an NFT concept that is not transferable after issuance, in line with the initial design (Buzzcai 2022), and there are also opinions that it should be supplemented to solve various problems after accepting the conceptual proposal of SBT (Tim Daub, Ethereum Magicians community 2021). This is due to the characteristic of being untransferable, which can lead to various problems such as hacking, user convenience, etc.
    
The problems mentioned above are the problems that r3plica focuses on, and r3plica has come up with fSBT as an alternative solution. Additionally, r3plica presents an example of using fSBT to implement the functional implementation of Account Abstraction through an SDK.

## Account Abstraction <a name="aa"></a>

Account Abstraction (called AA) is an attempt to abstract the account in order to break free from the constraints of traditional wallets. Many networks based on the EVM use two types of accounts: external owned accounts (EOA) and contract accounts (CA). CA can execute contracts, but to issue contracts or generate transactions, it must be used with EOA. While this structure is superior in terms of security, it imposes constraints when implementing functions with contracts. AA is a concept that allows the functions of EOA and CA to be available in a single account. While there have been discussions on this in the past, significant progress has been made in the EIP-4337 proposal ([Buterin](https://github.com/vbuterin), et, al., 2021). The expected effects of implementing AA are as follows:

### Wallet

Through AA, users can change their security key without changing their wallet. They can also benefit from security features such as multi-sig and smart recovery.

### Transaction sponsorship

Through AA, the contract issuer, corporation, or third party can pay for the gas fee on behalf of the user who initiated the transaction. This will be a great help in various parts, including the initial entry of Web2 users into Web3.

### Meta transaction (gasless)

Through AA, users can accept meta transactions (gasless) without trusting relayers. That is, users can initiate transactions without paying the gas fee. This is different from transaction sponsorship in that there is no gas fee.

r3plica is an SDK that focuses on reducing or eliminating barriers to web3 entry for web2 users, in addition to functional implementation of Account Abstraction. Through r3plica, web2 users can enjoy content without barriers to entry in web3.

## fSBT <a name="fsbt"></a>

### General functionality of fSBT

fSBT is one of the various proposals that can be presented in the absence of SBT standards. fSBT stands for Future Soul Bound Token, meaning that there is a point at which it will be converted to SBT. The first major functional difference between fSBT and SBT is the "limit on the number of transfers." With fSBT, it is possible to have wider uses and applications by limiting the number of transfers to 1 or n in the SBT model. In addition, like SBT, the issuer or owner can restrict the functions of the fSBT or burn the token itself.  
  
SBT cannot be transferred, so the account that mints the token must be a user. However, fSBT can be issued in advance because it is possible to transfer within the number of times specified in the contract. Depending on the intention of the issuer, it is possible to obtain different effects by issuing in advance or allowing the user to issue fSBT. The owner can use the limited number of transfers to strengthen the SBT-like characteristics by actually receiving the fSBT, or use the fSBT to fluidize the number of transfers to strengthen the NFT-like characteristics by minting the fSBT. If the fSBT is issued by a user's account, the rarity will be further emphasized because the number of transfers is limited.

The fact that fSBT can be issued in advance also means that the minting point is flexible from the user's perspective. It is very important to consider when a personal account connection is needed in a service situation. Personal account connection is the first step towards Web3 onboarding, and it is the biggest hurdle. The fact that the minting point is flexible means that both the business and the user are free in terms of personal account connection, which provides a very high degree of freedom in the service environment.

### SBT vs fSBT
|  | SBT | fSBT |
|--|--|--|
| Trasnfer-able? | Not available | Limited number of times available |
| Token Owner Account | User | Can be delegated at first |
| User's point of mint | Not free | Free |
| User's wallet address | Needed | Not needed at first |
| Storage of Assets | Not available | Available |
| Community Recovery | Available | Available |

### fSBT and Mass Adoption

r3plica is a project that focuses on Web3 onboarding for Web2 users, enabling mass adoption and implementing the conceptual and functional implementation of Account Abstraction (AA). AA aims to implement features such as gas fee support and meta transactions. In actual service situations, this function is emphasized because content providers can act on behalf of users. In addition to the functional implementation of gas fee support and meta transactions pursued by AA, r3plica removes the time constraints of Web3 onboarding. fSBT allows users to benefit from the transparency, decentralization, and security benefits of Web3 without a Web3 account.  
  
The r3plica fSBT SDK allows users to create their fSBT when they join the service. Until the actual owner of the generated fSBT connects to a Web3 account, the ownership of this fSBT exists in the issued contract. This is called PAfSBT (Profiles by Assetized fSBT). When the user connects and owns a Web3 account and the issued PAfSBT, the PAfSBT consumes the limit on the number of transfers and becomes the fully owned property of the real owner.  
  
When users use the Web3 service through r3plica, they have a similar experience to using Web2 games and services. However, the items, achievements, and experience points that users actually obtain in the game are all stored in this PAfSBT and are transferred to the user when they want to enter Web3. This is significant in that it reduces the amount of information that users need to know in order to enjoy the content, compared to the traditional Web3 content that required users to connect a wallet first.

## References<a name="references"></a>

Weyl, E. G., Ohlhaver, P., & Buterin, V. (2022). Decentralized Society: Finding Web3's Soul. Available at SSRN 4105763.

[Vitalik Buterin](https://github.com/vbuterin), [Yoav Weiss](https://github.com/yoavw), [Kristof Gazso](https://github.com/kristofgazso), [Namra Patel](https://github.com/namrapatel), [Dror Tirosh](https://github.com/drortirosh), [Shahaf Nacson](https://github.com/shahafn), [Tjaden Hess](https://github.com/tjade273), "EIP-4337: Account Abstraction using alt mempool [DRAFT]," Ethereum Improvement Proposals, no. 4337, September 2021. [Online serial]. Available: [https://eips.ethereum.org/EIPS/eip-4337](https://eips.ethereum.org/EIPS/eip-4337).

[Cooper Turley](https://medium.com/@coopahtroopa-eth?source=post_page-----d7e8fdfc207d--------------------------------), “What is POAP?“, Medium, Mar 2020. Available: [https://medium.com/poap/what-is-poap-d7e8fdfc207d](https://medium.com/poap/what-is-poap-d7e8fdfc207d)

Loopring, “What is a wallet Recovery?“, May 2022. Available : [https://loopring.zohodesk.com/portal/en/kb/articles/what-is-a-wallet-recovery](https://loopring.zohodesk.com/portal/en/kb/articles/what-is-a-wallet-recovery)

Vitalik Buterin, “Why we need wide adoption of social recovery wallets”, Blog, Jan 2022. Available : [https://vitalik.ca/general/2021/01/11/recovery.html](https://vitalik.ca/general/2021/01/11/recovery.html)

Tim Daub, Ethereum Magicians Community, “EIP-4973 - Account-bound Tokens“, Community Discussion, Apr 2022. Available : [https://ethereum-magicians.org/t/eip-4973-account-bound-tokens/8825](https://ethereum-magicians.org/t/eip-4973-account-bound-tokens/8825)

[Buzz Cai](https://github.com/buzzcai), "EIP-5484: Consensual Soulbound Tokens," Ethereum Improvement Proposals, no. 5484, August 2022. [Online serial]. Available: https://eips.ethereum.org/EIPS/eip-5484.

## Glossaries<a name="glossaries"></a>

SBT : Soul Bounded Token

fSBT : future SBT

PAfSBT : Profile Assetized fSBT

AA: Account Abstraction

PlayFab : A backend platform for games with game manage services, real-time analytics, etc

## Expectations and differences from existing solutions <a name="expectdiffer"></a>
### Outside of the game

#### Why blockchain gaming?

The expectation effect of blockchain games is the ability for users to fully own and control their gameplay experiences, including accounts, items, and achievements, through the use of fSBT (r3plica SDK). This is a significant shift from traditional games, where users do not typically have ownership over their in-game assets. Game companies, being profit-seeking organizations, may be motivated to adopt blockchain technology in order to offer more advanced services and increase profits. The decentralization, community, and ownership aspects of blockchain technology allow for the creation of games with higher levels of autonomy for users, which can lead to more active user participation. By owning fSBT related to their experiences in their Web3 account, users can assetize their gameplay experiences, potentially allowing them to be utilized by third parties.


#### User's Web3 Onboarding Procedure

Existing game companies often require users to connect their Web3 accounts in order to access certain in-game assets or to play the game smoothly. However, this process can be optional for users with r3plica, as they can choose to onboard with Web3 only when necessary or when they are ready to leave the game. This allows users to feel less obligated to onboard with Web3 and allows game companies to continue using their existing Web2 business models without interference. With r3plica, user information and Web3 assets are stored in PAFSBT and a virtual Web3 wallet is created upon subscription. This means that the game server and PAFSBT work together, allowing for real-time data processing and handling of user promises and security requirements through the blockchain. The flexible Web3 onboarding process allows for the continuation of familiar services and the potential for more diverse Web3 content. Additionally, the transparency provided by the disclosure of all Web3 data ensures user trust.

![](https://lh6.googleusercontent.com/vo-gYrbkDpFkeR-ihUkUmuN8lvQ00vVRni_8g8iFEkxo48033Xoe_SW1bhnmWkfuZzkmp0-UwpHTBE6D__0JGnn5dOJZheWQK5Re_FgYadWYC2BSGiiM8O6VJcTPcxIHRvrqmwGieGV2qLCrOhyLLJiONPGmSugzQHmN5kNfTB1RWlsMGKy9nAhltk0)

 
### Web3 Percentage of Services

#### Web3 weight of existing game companies  
  
Both in-game assets and Web3 assets using the server storage method are used in the game. When the user wants to play, the server storage asset is replaced with a Web3 asset and paid. This is a method of converting in-game money and items that are not blockchain into NFT and deleting existing data. In order to process both off-chain -> on-chain and on-chain -> off-chain, a user's wallet is essential. That is, there is no public information that the user can know until the user connects the wallet and receives the on-body asset.  
  
Team r3plica expect that transparency and security are emphasized through r3plica to provide transparent game data such as probability, explicit matters, items, and currency. Blockchain games can increase the proportion of on-chain data.  
  
#### Web3 weight of r3plica  
  
Using r3plica, all assets designated as NFT or FT by game companies exist as NFT or FT, and the game server can output NFT and FT, which have the entire record in the blockchain, as well as NFT and FT. Therefore, game companies can record the fact that the promised model is being kept and gain security and user trust. For example, in the existing web3 onboarding method, if the in-game assets were controlled by the algorithm of the game server, in a game using r3plica, the in-game assets were recorded by the blockchain and the user could check it transparently.  
  
#### Utilize fSBT with features such as vouchers  
  
Team r3plica expect that Use fSBT's limited number of transmission functions for use such as vouchers and specific authorization.  
  
Implementing a voucher in Web3 exists with NFT, and it was common for service providers that utilize it to determine the function of the NFT. However, it can be designed to act like a real voucher by taking advantage of the fSBT's limited number of transmission functions, unavailable after a certain period of time, and so on. In this case, the user may check the information in advance at a stage where the user is interested in assets having characteristics such as vouchers.

#### whitelist and blacklist user registration

The use of white and blacklists for users can be improved through the use of fSBT. While existing methods may include wallets on these lists, there is no way to check them on the whole chain. With fSBT, everyone can easily check if a wallet has been sent an fSBT.
  

#### Transfer of user accounts using PAfSBT

PAfSBT can also be used to transfer user accounts, depending on the design. By emphasizing the characteristics of NFT, PAfSBT can be designed to allow for multiple transfers. This means that in-game empirical elements, such as levels, achievements, attributed items, and skills, can potentially be traded using PAfSBT, even if the information of existing services is linked to a wallet and cannot be moved.

#### Using fSBT to build a sustainable community building

Furthermore, fSBT can be used to build sustainable communities. While current NFT communities may have a form and property that can be easily moved, fSBT can be used to emphasize communities that are more persistent and meaningful over time. Examples of this include middle school alumni associations and staff meetings at Binance.

  

### In the game

#### Tangible and intangible assets of user experience

One of the major benefits of using fSBT in blockchain games is the ability for users to claim and own their gameplay experiences. In traditional Web2 games, a user's experience is lost once they leave the game. However, in Web3 games with fSBT, a user's experience can be recorded and shared as an fSBT. This adds intangible value to the fSBT, as it serves as evidence of the time and effort a user has put into the game, similar to how professional certificates serve as evidence of expertise in a particular field. As certain game services become more well-known, the achievements of users who played them may be highly valued, leading to additional value creation.

#### Item on-chain


Existing solutions for on-chain items involve the use of data on the game server that is NFTized to enable transactions. However, this method limits the additional functions that can be expressed in NFT beyond the existing items, as the actual items and server must act within the server. Possible functions may include NFTization of generated items, movement of assets in the game when trading on-chain, and item destruction, all of which require payment by the user. Account abstraction is an attempt to solve this issue through the use of contracts.

R3plica's solution for in-game assets on-chain involves the issuance of assets on the online chain, where they exist on the game server and all functions linked to the game can be recorded on the chain. While an on-chain record is created, the user is not required to pay for it as the transaction is executed by the service provider. This is because in-game assets are issued from the game's Web3 account before the user applies for receipt, pursuing the functional implementation of account abstraction through fSBT.

#### Function as a tool to limit user behavior

Additionally, fSBT can function as a device to limit user behavior, similar to a yellow or red card in a soccer game. It can be used to limit the number of content a user can access or to limit the behavior of a user who has caused cheating.


## Methodology and Functionality<a name="methodfunction"></a>

### Features with user scenario

-   The user signs up/logs in, and the system mints a PAfSBT.
    
-   The user downloads the game and plays it.
    
-   While playing the game, the user obtains an item or achieves an achievement. At this point, the system binds the already minted AfSBTs to the user's PAfSBT on the on-chain.
    
-   The user connects their wallet. At this point, the system transfers the PAfSBT to the user's connected wallet.
    
-   The user goes to their My page and transfers the desired fSBT to their own wallet.
  

## Architecture<a name="architecture"></a>

  

![](https://lh6.googleusercontent.com/jAKmuHailDii35mvHOfcTbiGsJXIFGEMxxdO-Mahpd_VXuF9gxbHsoIXVmCG5KcMpVljp50772BJ3bNBTVeJBR0HRtNV9mT3THnIE1PHvDHn_y5aIj51fHQuQ4P3BUV9s9g1nuBf6dNV4ekNdrpDL9S3zvQjpYMzyMjODyNG4C5mIOzXoj5ey1cAR44)

The implementation of the r3plica SDK can be largely divided into six areas.

-   Game Client: [https://github.com/catze-labs/r3plica-unity-public](https://github.com/catze-labs/r3plica-unity-public)
    
-   Game Server: PlayFab
    
-   Front-end: [https://github.com/catze-labs/r3plica-web](https://github.com/catze-labs/r3plica-web)  
    
-   Back-end: [https://github.com/catze-labs/r3plica-server](https://github.com/catze-labs/r3plica-server)  
    
-   Blockchain: [bnb-chain/BEPs#179](https://github.com/bnb-chain/BEPs/pull/179)  
    
-  Protocol: [https://github.com/catze-labs/futureSBT](https://github.com/catze-labs/futureSBT)  

Each specific implementation method is described in each repo.
