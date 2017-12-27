---
layout: post
title: Diameter protocol replacing SS7
categories: 
  - blog
  - telcosec
published: true
---

Newer standards such as 4G are moving towards ‘all IP’ connections and the IP-based Diameter protocol [1] based signaling protocols by default use IPsec to authenticate connections, they have higher chances of providing sufficient security than SS7, which has no such protection. However, there is also the possibility that the IP-based attacks from the Internet could be replicated in the telecommunication networks.

Diameter addresses a broader range of emerging technologies than just cellular access, such as Mobile IP and the Internet of Things (IoT). The diameter was designed to resolve the issues with its predecessor, Radius, by improving the authentication, authorization, and accounting (AAA) functionality. Since any node within the Diameter system can initiate a request, Diameter is considered to be a peer-to-peer (P2P) communication protocol. The AAA functionality is incorporated with the help of a Network Authentication Server (NAS) and a shared authentication server. Being a P2P network, every node within the Diameter system can act as a client or a server depending on the network deployment. Every peer within the system uses dynamic peer discovery strategies including peer tables [2], which removes the need for the manual configuration of the NAS. Diameter can use the SCTP or Transmission Control Protocol (TCP) as the transport layer protocol.

One of the key measures to protect the core telecommunications network against network breaches is by hiding the critical elements from outside exposure. In SS7, the Global Title Translation (GTT) functionality [3] helps to achieve network exposure by reducing the need of disclosing the entire network’s element addresses in the routing tables of each and every node of the network. GTT hides the critical infrastructure such as HLR and EIR, as STPs can resolve the actual addresses of these elements using internal routing tables. This concept in Diameter protocol is implemented by default in the Home Subscriber Service (HSS) which takes care of GTT as well as mutual network terminal authentication. GTT and mutual terminal authentication jointly can protect the system against SCTP port scanning and impersonation attacks.

Another concern of the GSM/UMTS core networks is mapping the boundaries of the core network by an attacker by penetrating deeper into the network using vulnerable ports exploiting the interconnection gateways. The Diameter protocol prevents such penetration by topology hiding [4] in terms of critical infrastructure as well as routing paths. When an internetwork message is sent outside the HPLMN, the STP router replaces the internal (actual) address of the network entity with a generic address which can only be resolved by that STP. This helps hide global IP addresses from the view of an attacker who is trying to gain access to mobile core network. This not only prevents the attacker from accessing internal elements but also prevents man-in-the-middle (MitM) attacks. As part of backward compatibility, mobile operators have to support interconnection of GSM/UMTS to LTE systems. Address resolution during roaming between the 2G/3G MAP protocol and LTE Diameter is handled by the Interworking Function (IWF) interfaces [5].

Contrary to SS7, the Diameter protocol ensures a secure connection between the entities of the core network by IP Security (IPSec) or Transport Layer Security (TLS) that authenticate and encrypt the internal traffic. Diameter uses the TLS handshake protocol [6] , which utilizes X.509 [7] certificates and asymmetric cryptography to authenticate the peers which are part of communication. Since the traffic is encrypted, an attacker who has already gained access to the core network cannot intercept the transmission between network entities [8] . Authentication between the peers in the Diameter protocol makes it comparatively more secure than SS7. Diameter uses Network Access Identifier (NAI), Challenge Handshake Authentication Protocol (CHAP), Extensible Authentication Protocol (EAP ) and Password Authentication Protocol (PAP) for authentication [9]. The option of specifying Hop-by-Hop and End-to-End identifiers [10] in the message packets ensures a secure routing path as well as end-to-end security.

With the AAA mechanism in place, Diameter appears to be more secure than SS7 whose purpose was communication within trusted network. One of the key issues with the Diameter specifications is that, though it standardizes the use of IPSec and TLS in mobile communication, using them is not mandatory [1]. Also, there is no procedure to verify whether IPSec or TLS have been used underneath the Diameter implementation [12] of VPLMN. Moreover, being a P2P protocol, Diameter is application based. The rate at which Diameter can send or handle messages and the disclosure of interconnected peers or routes are dependent on the application. The packets that a Diameter system can send depend on the application that generates them rather than network settings. In such application-driven environments, if there is insufficient traffic to piggyback the acknowledgment messages ; the underlying TCP or SCTP protocols may cause more traffic with encrypted data. Furthermore, the application decides the penetration or reachability of the signaling messages. The attacker can impersonate at the application level and penetrate deeper into the core network. Hence Diameter cannot completely ensure the core network security against spoofing and interception during interconnection.

Additionally, Diameter uses the X.509 certificate and Public Key Infrastructure (PKI) for authentication; the common the problems of PKI such as the distribution of public keys, management of certificates and verification of certificate revocation continue to create the security administration overhead in core networks. Yet another issue with Diameter protocol is that it does not secure the system against DoS attacks. Though the peers can recognize the malicious flooding messages, the failover algorithms within Diameter implementation try to respond to the attacker with error messages. The attacker can exploit this vulnerability to submerge the target peer with flooding messages and hence execute a successful DoS attack.

Many of SS7 design features including some flaws have been replicated in the Diameter protocol. GSM /UMTS systems take most of the market share (in terms of inter-operator roaming) compared to hardly a handful of LTE roaming implementations. Since GSM/UMTS along with SS7 will continue to rule the core network domain for probably the next couple of decades, the positive changes that Diameter could affect to the core network are not huge.

---

1. V. Fajardo, J. Arkko, J. Loughney and G. Zorn, "Diameter Base Protocol," RFC Editor, 2012.
2. J. Liu, S. Jiang and H. Lin, "introduction to Diameter," IBM Developerworks, [Online].  
3. M.  Mimoso, "Cellular Privacy, SS7 Security Shattered at 31C3.," Threatpost, 30 December 2014. [Online]. 
4. 3GPP, "3GPP TR 23.840: Study into routing of MT-SMs via the HPLMN,"  3rd Generation Partnership Project. 
5. PP,  "3GPP TS 29.305:  InterWorking Function (IWF) between MAP based and Diameter based interfaces," 3rd Generation partnership Project.
6. T. Dierks and E. Rescorla, "The Transport Layer Security (TLS) Protocol Version 1.2," RFC Editor, 2008. 
7. M. Cooper, Y. Dzambasow, P. Hesse, S. Joseph and R. Nicholas, "Internet X.509 Public Key Infrastructure: Certification Path Building," RFC Editor, 2005.
8. Oracle Communications, "The Value of Diameter Signaling in Security and Interworking Between 3G and LTE Networks," Oracle Communications, [Online].  
9. A. Hoisa, "Comparision between RADIUS and Diameter," [Online].  
10. P. Calhoun, J. Loughney, E. Guttman, G. Zorn and J. Arkko, "Diameter Base Protocol," RFC Editor, 2003.
11. L. Philippe, "Diameter vs SS7 from a security perspective,"  P1 Labs,  13 July 2013. [Online].








