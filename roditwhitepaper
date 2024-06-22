
Rich Online Digital Tokens Whitepaper
=====================================

Author: Vicente Aceituno Canal / Cableguard, June 2024
------------------------------------------------------

[![Vicente Aceituno Canal](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%2520Jsem_jwNTATwcQhMSJgsyw_002.jpg)

](https://vaceituno.medium.com/?source=post_page-----94a8f1b547b4--------------------------------)[![Cableguard VPN, the RODiT revolution](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%20-yGnuVm2kxmajBAHlK3eMw.png)

](https://cableguard.org/?source=post_page-----94a8f1b547b4--------------------------------)

[Vicente Aceituno Canal](https://vaceituno.medium.com/?source=post_page-----94a8f1b547b4--------------------------------)

Published in[

Cableguard VPN, the RODiT revolution

](https://cableguard.org/?source=post_page-----94a8f1b547b4--------------------------------)·21 min read·4 days ago

50

Listen

Share

More

![](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%25208vZo0BmlGJDHt5u8v4mbJQ_005.png)Cableguard logo

Executive Summary
=================

This whitepaper introduces Rich Online Digital Tokens (RODiT), a novel approach to authentication, configuration, and licensing for online services leveraging non-fungible tokens on blockchain. RODiT address several key challenges compared to traditional methods like digital certificates and public key cryptography:

*   Simplified configuration, licensing, and authentication processes
*   Prevention of rogue credential issuers
*   Streamlined issuing and secure delivery of credentials
*   Seamless key rotation independent of license expiration
*   Robust protection against man-in-the-middle attacks

RODiT embed metadata like configuration settings, license terms, and authentication claims into unique blockchain tokens. This allows seamless integration of these processes when purchasing online services. The paper provides an overview of RODiT, their implementation on the NEAR blockchain protocol, and Cableguard as a real-world use case for RODiT-based VPN services.

Key benefits of RODiT include reduced complexity/cost, enhanced security, scalability, flexibility in licensing models, support for reselling and white-labeling services. RODiT can enable new solutions across sectors like finance, healthcare, government, telecommunications, and industrial IoT applications requiring strict security.

Introduction
============

The technology explained in this whitepaper builds on existing technologies and a simple idea: Blockchain-based non-fungible tokens are unique and can´t be cloned, therefore they can be used as authentication keys, ensuring that only the key holder can access what is protected.

Please note there is no relation between our use of non-fungible tokens and what is popularly known as NFTs (expensive unique tokens that have a URL pointing to some digital asset), except using the same underlying technology.

Thin and Rich Credentials
-------------------------

Most authentication methods have two parts, an ID and a credential (a password, a token, etc) but don’t carry any associated info, like configuration or licensing options, claims or addresses, they are what we could call **Thin Credentials**. Adding or associating configuration or licensing, claims or addresses is performed in separate registration, configuration and licensing processes per Service Provider (a cloud service, a website, a system), in order to gather all the necessary information to provide the service. Using an email address as a credential ID is a very frequent practice that makes thin credentials ever so slightly richer.

If we had credentials that could carry all the configuration, licensing, claims or addresses necessary to interact with Service Providers, that we can call **Rich Credentials**, that would make registration, configuration and licensing processes simpler or even unnecessary. Instead of having all this information permanently stored by the Service Provider, parts of it contained in the Rich Credential could be shared only when necessary.

Among the several techniques used for authentication, the one that most closely resembles a Rich Credential is the Digital Certificate. It can carry for example Subject Alternative Names, like IP addresses or domain names. In practice, there are few implementations if any that carry configuration or licensing options.

In 1988 the International Telecommunication Union (ITU) published the first version of the X.509 standard for Digital Certificates, which defined the format and syntax of digital certificates. Back in the day continuous and ubiquitous access to the Internet was not common, so one of the requirements in the design was to be able to validate the Digital Certificate while offline. While this requirement is still available as originally designed, some modern features of Public Key Infrastructure (the governance framework for Digital Certificates) can only be used online, for example OCSP. Digital Certificates have not been updated significantly since 2008 (or 1999 you may argue), coincidentally the year of the publication of “Bitcoin: A Peer-to-Peer Electronic Cash System”.

Rich Online Digital Tokens
--------------------------

In this paper we introduce the use of Rich Online Digital Tokens (RODiT), custom non-fungible-tokens that can carry configuration, licensing, claims, and addresses information, as a practical and modern alternative to digital certificates that can be used for mutual authentication, configuration of endpoints and licensing of online services, among other use cases.

Audience
--------

This paper will be of interest for anyone who designs online services (Service Providers).

Problem Statement
=================

There are several problems that can be addressed using RODiT:

1.  **Configuration, Licensing and Authentication Complexity and Cost**_._ Both Digital Certificates and Thin Credentials in use require separate registration, configuration and licensing processes that can be become costly and complex in scenarios with strict security requirements.
2.  **Rogue Issuers**: There is no current fail proof mechanism to prevent the unauthorized issuance of certificates by Certificates Authorities. Participants in Certificate Transparency can monitor and detect unauthorized issuance, but can´t prevent it. Generally speaking Service Providers that use Digital Certificates don´t currently have an effective mechanism to declare which Certificate Authorities (Issuers) they trust, opening the door to well known vulnerabilities in the use of digital certificates (See \[1\], \[2\] \[3\] \[4\] and \[5\]). RODiT uses a mechanism whereas domains used by Service Providers must declare what Issuers (that are smart contracts) are trusted to issue valid RODiT for them.
3.  **Issuing and Delivering Credentials**: When implementing mutual authentication with Digital Certificates, the workflow has several steps that require endpoint access and file transfer of a CSR file between the endpoint and the CA, and a Digital Certificate file between the CA and the endpoint. In order to simplify digital certificate generation and distribution, some implementations generate the CSR and Digital Certificate in a central point, instead of generating the key pairs in the endpoints, which make the private keys far more likely to be compromised. Using RODiT there are no file transfers, as the RODiT is sent to a blockchain address. The impact of using RODiT and its simple issuing and delivery workflow becomes highly significant as the number of participant endpoints grows.
4.  **Key Rotation**: With Digital Certificates, key rotation requires issuing, transferring and installing a new digital certificate when the key is due to be rotated, regardless of the expiration date of the service being secured with the digital certificate. Expiring digital certificates have caused major incidents worldwide (See \[6\] and \[7\]). Using RODiT, key rotation is decoupled from license expiration, as it does not require issuing a new RODiT. Besides, key rotation can be performed independently for every endpoint, without any coordination between endpoints, greatly simplifying management of key rotation. Again, the impact of using RODiT and its simple key rotation workflow becomes highly significant as the number of participant endpoints grows.
5.  **Man in the middle (MiTM)**: This type of attack occurs when a malicious third-party intercepts and alters messages between two unsuspecting parties, potentially stealing confidential information or making unauthorized changes. Despite the risks, mutual authentication is not widely used because of the perceived security provided by other methods and the practical difficulties associated with implementation of mutual authentication for large number of endpoints or large user bases. Using RODiT mutual authentication is simple to implement, providing strong protection against MiTM attacks.

Overview of RODiT
=================

Let’s spell R.O.Di.T out.

*   RODiT are **R**ich because they have configuration and licensing information (not meta information) that is immediately useful.
*   RODiT are **O**nline, because they are used while connected to the internet, unlike traditional digital certificates that can operate offline.
*   RODiT are **Di**gital to remind you that they are similar in functionality to Digital certificates, and finally;
*   RODiT are **T**okens because they are unique and they can be bought and sold.

RODiT address, among other features, the following problems:

Configuration, Licensing and Authentication Complexity and Cost
---------------------------------------------------------------

RODiT tokens follow a default structure detailed in Appendix I, and can accommodate extra data fields as necessary for each use case. By including configuration and licensing info in the RODiT, when you purchase a subscription to an online service, at the same time you get your authentication mechanism and your configuration. For example, with a VPN service that uses Cableguard (more about this later), you don’t need to do anything to configure your VPN, it configures itself with the RODiT, and you don’t need to register to be able to login, as it authenticates with the RODiT itself. This is an example of an actual RODiT, with configuration items in blue, authentication items in green and licensing items in orange:

![](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%2520bEFrUJFYLSoiOQMNAoKnLA_006.png)A sample RODiT

Providing a RODiT to an endpoint handles as a unit the licensing, configuration and authentication processes, great simplifying the complexity and costs associated with large user bases with high security requirements.

Rogue Issuers
-------------

In a triangle of trust, Issuers of credentials trust Service Providers, Service Providers trust Issuers and Users trust them both. RODiT uses a simple mechanism based in DNS so trust can be determined, Service Providers indicate if they trust particular Issuers, Issuers can indicate if they trust Service Providers, and Service Providers can indicate if they trust user credentials. If a Issuer misbehaves, Service Providers can withdraw trust, if a Service Provider misbehave, Issuers can withdraw trust, and if a User misbehaves, Services Providers can withdraw trust.

Service Providers must have an associated domain name, and in order to issue RODiT using a particular smart contract, they have to authorize explicitly the Issuer blockchain account that controls the smart contract; otherwise the endpoints will reject the RODiTs issued. As implemented in Cableguard, this is a DNS entry for the cableguard.net domain authorizing the smart contract controlled by the rodit-org.near wallet (for example) to issue RODiT for the cableguard.net Service Provider (for example):

_rodit-org.near.smartcontract.cableguard.net TXT “whatever_”

Issuing and Delivering Credentials
----------------------------------

The process takes the following steps in a commercial setting:

1.  Service Providers use a RODiT minter service, for example Cableguard FORGE to generate as many RODiT as necessary for their systems, sent to an address which will distribute them later from the RODiT Point of Sale.
2.  Endpoints generate locally key pairs, and initialize them in the blockchain.
3.  Endpoints present the public key upon purchase of a RODiT in the Point of Sale, and obtain the RODiT that is sent to the blockchain address (the public key) in exchange for payment.

Endpoint access or file transfers are unnecessary, and the private key is generated in the locally endpoint with the obvious security implications.

Key Rotation
------------

The process takes the following steps:

1.  Endpoint generates a new key pair, and initialize it in the blockchain.
2.  Endpoint sends the RODiT to the newly generated blockchain address (public key).
3.  Optionally, the old key pair can be deleted.

Key lifetime is independent of the duration licensed for the service, can happen with whatever frequency that is adequate for the use case, and does not need to be synchronized with the key rotation of any other endpoint.

Man in the middle attack (MiTM)
-------------------------------

When using RODiT, mutual authentication if the default mode, thanks to the scalability and simplicity associated with being able to set up endpoints independently and rotate key pairs asynchronously. In combination with mutual authentication (RODiT are digitally signed), local generation of key pairs, and compulsory authorization of the smart contract used to issue RODiT makes MITM extremely hard, if not impossible, to achieve.

Overview of Cableguard
======================

Cableguard VPN is an implementation of Wireguard written in Rust based on a fork of Wireguard with a BSD license developed by Cloudflare known as Boringtun \[9\]. While Wireguard\`s native authentication model uses local lists of authorized public keys per endpoint, Cableguard VPN uses a customized version of the Noise protocol \[8\] to facilitate RODiT based authentication. Cableguard VPN is the first practical demonstration of the use of RODiT for mutual authentication. Every Cableguard VPN endpoint uses a minimalist NEAR Protocol blockchain cryptographic wallet, which is a simple JSON file. The file holds a private key that gives each Cableguard endpoint full access to a blockchain account (or address)

Note: At the time of writing this whitepaper is compatible with Linux and IPv4 only.

Cableguard VPN uses several software components:

*   Cableguard FORGE (https://github.com/cableguard/cgforge): Each Issuer can mint its own collection of RODiT in the NEAR Protocol blockchain using this component. You can find a live instance for the _rodit-org.near_ smart contract at https://mainnet.cableguard.net where you can mint your own collection of RODiT for your Service Provider.
*   NEAR Protocol\`s compatible wallets, like [https://www.mynearwallet.com/](https://www.mynearwallet.com/) facilitate paying for RODiT or initializing RODiT addresses. You can purchase NEAR in your cryptocurrency exchange.
*   Cableguard RODITVPN (https://github.com/cableguard/cgroditvpn ): Each endpoint can create NEAR Protocol blockchain addresses, initialize addresses, receive or send RODiT, distribute RODiT to all the known members of the VPN connections we want to establish, or rotate the RODiT key, using Cableguard RODITVPN\`s scripts. It leverages NEAR Protocol\`s command line _near-cli-rs_.
*   Cableguard TUN, Cableguard TOOLS and Cableguard RODITVPN: Each endpoint can use a RODiT as either a VPN server or client using: 1) Cableguard TUN (https://github.com/cableguard/cgtun.git ), what creates the wireguard tunnels (_cableguard-cli_ ), configured, licensed and mutually authenticated with RODiT, 2) Cableguard TOOLS (https://github.com/cableguard/cgtools.git ), a customized version of wireguard tools (_wg), 3)_ Cableguard RODITVPN, that includes bash scripts to start and stop the VPN endpoints.
*   Cableguard POS, is a demo point of service planned to deliver RODiT on demand to a NEAR Protocol address for a NEAR payment. In the mean time you need to create your own RODiT or contact vpn@cableguard.net to obtain a valid RODiT and connect to a live instance of a Cableguard VPN Server at vpn.cableguard.net.

Cableguard, as a sample full implementation of RODiT, addresses the following problems:

Configuration, Licensing and Authentication Complexity and Cost
---------------------------------------------------------------

Cableguard VPN servers and clients are licensed via RODiT only.

Cableguard VPN servers and clients authenticate via RODiT only.

Cableguard VPN clients are configured entirely via RODiT.

Cableguard VPN servers are configured via a RODiT and found by clients via associated DNS entries:

*   One A type DNS entry per VPN server that lists the IP address.
*   One TXT type DNS entry per VPN server that lists the port and public key.

Cableguard VPN doesn´t need a user database, so there is no registration process. Upon purchase of a RODiT that is sent to a blockchain address, the endpoint has the configuration and licensing info that can be validated by all participant endpoints. The only backend process necessary is the DNS configuration and listing of available servers. Not having a registration process or a users database greatly simplifies the backend of a Cableguard VPN service in comparison to current similar services.

Rogue Issuers
-------------

Cableguard implements RODiT\`s triangle of trust as follows:

Service Providers indicate if they trust particular Issuers with a DNS entry following this format:

_rodit-org.near.smartcontract.cableguard.net TXT “whatever_”

Issuers indicate if they trust Service Providers with a DNS entry following this format:

_cableguard-net.near.serviceprovider.rodit.org TXT “whatever_”

Service Providers can indicate if they don´t trust user credentials with a DNS entry following this format:

_roditID.revoked.cableguard.net TXT “whatever_”

Malicious actors can´t create neither Issuers nor RODiT that will pass these checks and the mutual checks described in the section MiTM below.

Issuing and Delivering Credentials
----------------------------------

1.  Service Providers use Cableguard FORGE to mint collections of RODiT, sent to an address which will distribute them later from a Point of Sale.
2.  Endpoints use Cableguard RODITPVN to generate locally key pairs, and initialize them in the blockchain with funds from a NEAR Protocol wallet.
3.  Users purchase RODiT in the Point of Sale with their NEAR Protocol wallet, and obtain the RODiT that are sent to the blockchain address (the public key) in exchange for payment.

Endpoint access or file transfers are unnecessary, and the private key is generated locally in the endpoint with the obvious security implications.

Key rotation
------------

1.  Endpoint uses Cableguard RODITPVN generates a new key pair, and initialize it in the blockchain.
2.  Endpoint sends the RODiT to the newly generated blockchain address (public key).
3.  Optionally, the old key pair can be deleted.

Key lifetime is independent of the duration of the licensed for the service, can happen with whatever frequency that is adequate for the use case, and does not need to be synchronized with the key rotation of any other endpoint.

Man in the middle attack (MiTM)
-------------------------------

Each side of every communication performs the following checks on the other end:

1.  Are we presented with a Live or Revoked RODiT
2.  Is the RODiT Genuine, is the peer\`s signed with the same private key our own RODiT was signed with.
3.  Is the peer endpoint in Possession of the RODiT at this point in time.
4.  Is the RODiT Issuer Live or Revoked.
5.  Is the subscription Active or Expired.
6.  The RODiT can inform about additional use cases like scopes/permissions, authorized networks, locations, transactions per second, bandwidth, etc.

These checks, plus the implementation of the triangle of trust, and mutual cryptographic authentication and Wireguard\`s implementation the Noise protocol framework provide a very effective protection against man in the middle attacks.

Overview of NEAR Protocol
=========================

NEAR Protocol is a blockchain platform designed to simplify the user experience and make blockchain technology more accessible. It aims to achieve this through several key strategies:

1.  Chain Abstraction: NEAR Protocol simplifies the complex workings of blockchain technology into more understandable layers, making it accessible to developers, users, and stakeholders. These layers include the protocol layer, network layer, data layer, and smart contract layer.
2.  Sharding: NEAR Protocol uses sharding to process transactions in parallel, enhancing scalability and making the blockchain’s complexity transparent to users. The blockchain is divided into four shards, each capable of processing 1,000 transactions per second.
3.  Dynamic Resharding: This feature allows for the creation and destruction of shards based on demand, ensuring scalable and efficient network performance.
4.  Human- Readable Account Names: NEAR Protocol uses easy-to-remember account names instead of complex addresses, simplifying transactions and interactions on the blockchain.
5.  Access Keys with Permissions: Users can grant specific permissions to DApps, improving security and usability.

NEAR Protocol is the blockchain selected for the RODiT implementation, driven by a combination of technical, economic, and strategic advantages that the protocol offers, among them:

*   Developer- Friendly. NEAR provides a robust and user-friendly development environment, which simplifies the process for developers to build, deploy, and maintain applications. This ease of development can accelerate the creation and enhancement of the RODiT platform.
*   Affordable Token Creation. The cost of creating tokens on NEAR is significantly lower compared to other blockchains. This makes it economically viable for users to mint and manage tokens without prohibitive fees, encouraging wider adoption and usage.
*   Zero Cost of Token Verification. Verifying ownership and control of tokens on NEAR is essentially free, which helps in maintaining transparency and trust without additional costs.
*   Reliability and Minimal Downtime. NEAR Protocol is designed for high reliability, ensuring minimal downtime. This means that applications built on NEAR, including RODiT, can offer consistent and dependable service to their users.
*   Incentives for Network Health. NEAR incentivizes its participants to maintain the health and functionality of the blockchain. This ensures a robust and active network, supporting the continuous and stable operation of the RODiT platform.
*   Scalability and High Performance. NEAR is built to handle a high volume of transactions efficiently, ensuring that the RODiT platform can scale as its user base grows without compromising on performance.
*   Decentralization and Resilience. Being a decentralized platform, NEAR operates without a central authority. This ensures that the RODiT implementation cannot be easily shut down or censored, providing resilience and autonomy to its operations.
*   Jurisdictional Independence. NEAR’s decentralized nature means it operates beyond specific jurisdictions, reducing the risk of regulatory interference and providing a global reach for the RODiT platform.
*   Proof of Stake (PoS) instead of Proof of Work (PoW). NEAR Protocol operates on a Proof of Stake consensus mechanism, which is more energy-efficient compared to Proof of Work. This makes NEAR an environmentally friendly option, reducing the carbon footprint associated with blockchain operations.
*   Accessible Token/Cryptocurrency. NEAR’s tokens are easy to purchase and manage, ensuring that users can seamlessly participate in the RODiT ecosystem without facing barriers related to acquiring or using the native cryptocurrency.

By leveraging these advantages, the NEAR Protocol provides a strong foundation for implementing RODiT, ensuring it is cost-effective, reliable, secure, and scalable, while also being environmentally conscious and user-friendly.

Technical Details of Mutual Authentication
==========================================

1.  Endpoints determine if they are presented with a Live or Revoked RODiT by checking if there is a match for the RODiT and a DNS entry following this format: _roditID.revoked.serviceproviderdomain_. If the entry exists, the authentication fails.
2.  Endpoints determine if the RODiT is Genuine, by checking if the peer\`s RODiT signature found in the serviceprovidersignature was signed with the same private key the endpoint\`s own RODiT was signed with. If it does not match, the authentication fails.
3.  Endpoints determine if the peer endpoint is in Possession of the RODiT by checking if the RODiT ID signature provided has been signed with the key pair that owns the peer\`s RODiT in the blockchain at this point in time. If it does not match, the authentication fails.
4.  Endpoints determine if the peer\`s RODiT Issuer is Live or Revoked by checking if there is a match for the RODiT and a DNS entry following this format: _issuerdomain.near.smartcontract.serviceproviderdomain_ . If the entry does not exist, the authentication fails.
5.  Endpoints determine if the subscription Active or Expired by checking if the current time is between the _notafter_ and _notbefore_ fields of the peer\`s RODiT, unless the fields are nul, indicated by the value 1/1/1970. If not Active, the authentication fails.
6.  The RODiT can inform about additional use cases like scopes/permissions, authorized networks, locations, transactions per second, bandwidth, etc.

Key features and benefits
=========================

Besides the problems addressed, there are some additional benefits from using RODiT tokens, as token holders can:

*   Sell RODiT at any point during the subscription period to other users. Using other licensing methods selling a partially used subscription is not common or straightforward.
*   Swap a RODiT with other users for enhanced anonymity.
*   Dispose of a RODiT sending it to a disposal address.
*   Renew or a subscription obtaining a discount by returning the previous RODiT, or obtain a rebate for returning an subscription before expiration.

RODiT have some security benefits in comparison to other authentication methods as:

*   RODiT can\`t be shared between users without risk losing them. This leads to less credential sharing among end users of any Service.
*   If the RODiT\`s blockchain account is compromised it is easy to detect, as the only way to keep exclusive control by the attacker is by moving it to a new blockchain address. If the attacker does not move the RODiT, it risks losing it as the RODiT owner can move it to a new blockchain address at any time.

Using RODiT can lead to new commercialization practices by Service Providers as:

*   Service Providers can delegate sales and distribution to third parties and resellers easily, by providing stocks of RODiT tokens.
*   Service Providers can let resellers sell the services with their own brand, “white label”.

RODiT metadata is easily extensible and can cater for custom needs around licensing conditions, permissions (scopes), security boundaries like authorized locations or networks, and other business cases that can be complex to implement using separate licensing, authentication and configuration processes.

Use Cases and Applications
==========================

RODiT can be leveraged for may uses cases, particularly when there is a need to cater for strict anonymity or security requirements with large number of endpoints. To name a few:

*   Cableguard VPN
*   As a replacement for SSH Certificates
*   Financial Services APIs: Banking, Payment Processing, Cryptocurrency exchanges
*   Healthcare APIs: Electronic Health Record (EHR), Medical Device, Telehealth
*   Government and Legal Services APIs: Identity Verification, Document Management, Tax and Financial Reporting
*   Telecommunications: Messaging applications
*   E-commerce APIs: Customer Information, Inventory and Order Management
*   Cloud Service Provider APIs: Storage, Compute

RODiT are particularly suited for Industrial and Internet of Things (IoT), as there RODiT can be send to endpoints remotely without accessing the endpoints.

Implementing RODiT can have a big impact in the provision of most online services, particularly:

*   Environments at risk due to government sponsored espionage and sabotage.
*   Environments where anonymity and security are paramount, like investigative journalism, due to the need to protect whistleblowers and other sources.
*   Environments where may need strong authentication in peer to peer messaging, as RODiT mutual authentication is suited to peer to peer validation.

Market Analysis
===============

The overall market value for internet and cloud services in the relevant sectors is as follows:

**VPN Services**: The global VPN market size is expected to reach USD 43.3 billion by 2027, growing at a CAGR of 14.1% from 2022 to 2027.

**SSH Certificates**: The global SSH market size is expected to reach USD 1.4 billion by 2027, growing at a CAGR of 12.1% from 2022 to 2027.

**Financial Services APIs: Banking, Payment Processing, Cryptocurrency exchanges**:

*   The global banking APIs market size is expected to reach USD 1.4 billion by 2027, growing at a CAGR of 15.1% from 2022 to 2027.
*   The global payment processing APIs market size is expected to reach USD 2.1 billion by 2027, growing at a CAGR of 14.3% from 2022 to 2027.
*   The global cryptocurrency APIs market size is expected to reach USD 1.1 billion by 2027, growing at a CAGR of 14.5% from 2022 to 2027.

**Healthcare APIs: Electronic Health Record (EHR), Medical Device, Telehealth:**

*   The global EHR APIs market size is expected to reach USD 1.3 billion by 2027, growing at a CAGR of 14.2% from 2022 to 2027.
*   The global medical device APIs market size is expected to reach USD 1.1 billion by 2027, growing at a CAGR of 13.4% from 2022 to 2027.
*   The global telehealth APIs market size is expected to reach USD 1.5 billion by 2027, growing at a CAGR of 15.6% from 2022 to 2027.

**Government and Legal Services APIs: Identity Verification, Document Management, Tax and Financial Reporting**:

*   The global identity verification APIs market size is expected to reach USD 1.2 billion by 2027, growing at a CAGR of 13.9% from 2022 to 2027.
*   The global document management APIs market size is expected to reach USD 1.1 billion by 2027, growing at a CAGR of 13.2% from 2022 to 2027.
*   The global tax and financial reporting APIs market size is expected to reach USD 1.3 billion by 2027, growing at a CAGR of 14.5% from 2022 to 2027.

**Telecommunications: Messaging applications**:

*   The global messaging APIs market size is expected to reach USD 2.3 billion by 2027, growing at a CAGR of 14.5% from 2022 to 2027.

**E-commerce APIs: Customer Information, Inventory and Order Management**:

*   The global e-commerce APIs market size is expected to reach USD 2.5 billion by 2027, growing at a CAGR of 15.3% from 2022 to 2027.
*   The global customer information APIs market size is expected to reach USD 1.4 billion by 2027, growing at a CAGR of 14.1% from 2022 to 2027.
*   The global inventory and order management APIs market size is expected to reach USD 1.1 billion by 2027, growing at a CAGR of 13.4% from 2022 to 2027.

**Cloud Service Provider APIs: Storage, Compute; Internet of Things and SCADA systems**:

*   The global cloud storage APIs market size is expected to reach USD 2.2 billion by 2027, growing at a CAGR of 14.8% from 2022 to 2027.
*   The global cloud compute APIs market size is expected to reach USD 2.5 billion by 2027, growing at a CAGR of 15.5% from 2022 to 2027.
*   The global IoT APIs market size is expected to reach USD 1.4 billion by 2027, growing at a CAGR of 14.3% from 2022 to 2027.
*   The global SCADA APIs market size is expected to reach USD 1.1 billion by 2027, growing at a CAGR of 13.2% from 2022 to 2027.

See references \[10\], \[11\], \[12\], \[13\] and \[14\]

Case Studies
============

The current reference implementation isCableguard VPN. The following table compares Cableguard VPN with equivalent solutions, Wireguard using PKC and OpenVPN using Digital Certificates.

![](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%2520z-cHEed5JTUz6MFvl_Pp5w_008.png)Part 1 of 3![](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%2520jV3vf-FeD10g1Z7m92UphQ_006.png)Part 2 of 3![](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%2520y6HnOnUJPLem97P0PF3xZw_008.png)Part 3 of 3

Future Outlook
==============

RODiT can be used to improve how many online services are provided, for example:

*   Currently there are not standard methods so users can delegate in AI agents tasks using their online services. Using RODiT can help designing solutions that will cater for this need.
*   Currently there are no standard methods to validate the identity of someone who is using an online service. Deepfakes can fool us via voice and video. Using RODiT could help creating a mechanism so people presence could be securely validated online.
*   RODiT could be used so operating systems can validate the hash of any executable before running it by matching it with a published RODiT ID for the specific executable version in a public blockchain.

Some areas need additional work in order to enable the implementation of services that use RODiT:

*   RODiT data is public in the blockchain. Some use cases will require the encryption of some of the information in the RODiT.
*   Different operating systems have different secrets store facilities. These could be leveraged to store RODiT controlling key pairs securely.
*   The triangle of trust can be enhanced with Issuer to Issuer and Service Provider to Service Provider trust handshakes. This could lead to RODiT becoming reusable across services.
*   RODiT could be implemented for other blockchains with suitable technology besides NEAR Protocol.
*   As of today, cryptographic wallets don´t display RODiT info and it is limited to the Linux command line. Further development is needed to implement RODiT solutions for other operating systems, and standards need to be agreed so cryptographic wallets can display RODiT information.

Conclusion
==========

Rich Online Digital Tokens (RODiT) represent a significant innovation in how online services can approach authentication, configuration, and licensing. By leveraging blockchain non-fungible tokens to encapsulate these critical elements, RODiT provide a unified, simplified, and secure solution compared to traditional methods.

Key advantages of RODiT include:

*   Reducing complexity and costs by consolidating authentication, configuration, and licensing into a single token
*   Preventing rogue credential issuers through a verifiable trust model
*   Enabling seamless issuing and secure delivery of credentials to endpoints
*   Allowing independent key rotation decoupled from license expiration
*   Robust mutual authentication and protection against man-in-the-middle attacks

The Cableguard VPN implementation demonstrates RODiT’s real-world applicability, leveraging the scalability and security of the NEAR blockchain protocol. This case study highlights RODiT’s enhanced security properties, and operational benefits over alternatives.

With a vast array of potential use cases across sectors like finance, healthcare, telecommunications, ecommerce, and industrial systems, RODiT open up new possibilities for innovative online service models prioritizing security, privacy, and seamless user experiences.

Final Thoughts
==============

While this whitepaper focuses on the core concepts and technical implementation, the true potential of RODiT extends far beyond what is covered here. RODiT represent a paradigm shift in how we approach digital authentication, identity, and trusted interactions in an increasingly connected world.

As blockchain technologies and decentralized solutions continue evolving, RODiT could pave the way for new models of digital identity, verifiable credentials, and secure data exchange. The flexible nature of RODiT metadata allows expanding use cases into areas like digitally signing documents, validating software executables, and enabling secure AI delegation models.

Moreover, RODiT’s ability to facilitate new licensing approaches, such as friction less reselling, white-labeling services, and innovative pricing models, could disrupt traditional business models for online services.

Ultimately, RODiT exemplify the power of blockchain to reshape digital ecosystems, offering a glimpse into a future where security, trust, and user experiences are seamlessly intertwined through innovative decentralized solutions. As developers and businesses continue exploring RODiT’s possibilities, we may witness a transformative impact on how we interact, transact, and navigate the digital landscape.

References
==========

1.  [https://www.schneier.com/wp-content/uploads/2016/02/paper-pki.pdf](https://www.schneier.com/wp-content/uploads/2016/02/paper-pki.pdf)
2.  [https://datatracker.ietf.org/doc/html/draft-housley-web-pki-problems-00.txt](https://datatracker.ietf.org/doc/html/draft-housley-web-pki-problems-00.txt)
3.  [https://www.iang.org/ssl/pki\_considered\_harmful.html](https://www.iang.org/ssl/pki_considered_harmful.html)
4.  [https://sslmate.com/resources/certificate\_authority\_failures](https://sslmate.com/resources/certificate_authority_failures)
5.  [https://datatracker.ietf.org/doc/html/draft-housley-web-pki-problems-00](https://datatracker.ietf.org/doc/html/draft-housley-web-pki-problems-00)
6.  [https://www.crowdstrike.com/blog/the-risks-of-expired-ssl-certificates/](https://www.crowdstrike.com/blog/the-risks-of-expired-ssl-certificates/)
7.  [https://www.digicert.com/blog/digital-certificates-expiring-on-major-platforms](https://www.digicert.com/blog/digital-certificates-expiring-on-major-platforms)
8.  [http://www.noiseprotocol.org/](http://www.noiseprotocol.org/)
9.  [https://github.com/cloudflare/boringtun](https://github.com/cloudflare/boringtun)
10.  [https://www.mordorintelligence.com/industry-reports/cloud-computing-market](https://www.mordorintelligence.com/industry-reports/cloud-computing-market)
11.  [https://www.cloudzero.com/blog/cloud-computing-market-size/](https://www.cloudzero.com/blog/cloud-computing-market-size/)
12.  [https://www.marketsandmarkets.com/Market-Reports/cloud-computing-market-234.html](https://www.marketsandmarkets.com/Market-Reports/cloud-computing-market-234.html)
13.  [https://www.grandviewresearch.com/industry-analysis/cloud-computing-industry](https://www.grandviewresearch.com/industry-analysis/cloud-computing-industry)
14.  [https://www.statista.com/chart/18819/worldwide-market-share-of-leading-cloud-infrastructure-service-providers/](https://www.statista.com/chart/18819/worldwide-market-share-of-leading-cloud-infrastructure-service-providers/)

Appendix I — RODiT Data Structure
=================================

![](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%2520bH7wv0HsI740iUi5nJp3-A_007.png)

Appendix I — Cableguard VPN Data Structure
==========================================

![](Rich%20Online%20Digital%20Tokens%20Whitepaper%20by%20Vicente%20Aceituno%20Canal%20Jun,%202024%20Cableguard%20VPN,%20the%20RODiT%20revolution_files/1%2520XGyJdwqc94Tlj_2DDdaTXQ_004.png)
