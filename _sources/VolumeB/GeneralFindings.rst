General Findings
================

.. include:: /_publication_note.rst

When deploying ZTA using the EIG approach, the following capabilities are considered to be fundamental to determining whether a request to access a resource should be granted and, once granted, whether the access session should be permitted to persist:

-  Authentication and periodic reauthentication of the requesting user's identity

-  Authentication and periodic reauthentication of the requesting endpoint

-  Authentication and periodic reauthentication of the endpoint that is hosting the resource being accessed

In addition, the following capabilities are also considered highly desirable:

-  Verification and periodic reverification of the requesting endpoint's health

-  Verification and periodic reverification of the health of the endpoint that is hosting the resource being accessed

EIG Crawl Phase Findings
------------------------

In the EIG crawl phase, we followed two patterns. First, we leveraged our ICAM solutions to also act as PDPs. We discovered that many of the vendor solutions used in the EIG crawl phase do not integrate with each other out-of-the-box in ways that are needed to enable the ICAM solutions to function as PDPs. Typically, network-level PEPs, such as routers, switches, and firewalls, do not integrate directly with ICAM solutions. However, network-level PEPs that are identity-aware may integrate with ICAM solutions. Also, endpoint protection solutions in general do not typically integrate directly with ICAM solutions. However, some of the endpoint protection solutions considered for use in the builds have out-of-the-box integrations with the MDM/UEM solutions used, which provide the endpoint protection solutions with an indirect integration with the ICAM solutions.

Second, we used out-of-the-box integrations offered by the solution providers rather than performing custom integrations. These two patterns combined do not support all the desired zero trust capabilities.

Both builds E1B1 and E3B1 were capable of authenticating and reauthenticating requesting users and requesting endpoints, and of verifying and periodically reverifying the health of requesting endpoints, and both builds were able to base their access decisions on the results of these actions. Access requests were not granted unless the identities of the requesting user and the requesting endpoint could be authenticated and the health of the requesting endpoint could be validated; however, no check was performed to authenticate the identity or verify the health of the endpoint hosting the resource.

Access sessions that are in progress in both builds are periodically reevaluated by reauthenticating the identities of the requesting user and the requesting endpoint and by verifying the health of the requesting endpoint. If these periodic reauthentications and verifications cannot be performed successfully, the access session will eventually be terminated; however, neither the identity nor the health of the endpoint hosting the resource is verified on an ongoing basis, nor does its identity or health determine whether it is permitted to be accessed.

Neither build E1B1 nor build E3B1 was able to support resource management as envisioned in the ZTA logical architecture depicted in *Figure 4-1*. These builds do not include any ZTA technologies that perform authentication and reauthentication of resources that host endpoints, nor are these builds capable of verifying or periodically reverifying the health of the endpoints that host resources. In addition, when using both builds E1B1 and E3B1, devices (requesting endpoints and endpoints hosting resources) were initially joined to the network manually. Neither of the two EIG crawl phase builds includes any technologies that provide network-level enforcement of an endpoint's ability to access the network. That is, there is no tool in either build that can keep any endpoint (either one that is hosting a resource or one that is used by a user) from initially joining the network based on its authentication status. The goal is to try to support resource management in future builds as allowed by the technologies used.

EIG Run Phase Findings
----------------------

The EIG run phase enabled us to demonstrate additional capabilities over the EIG crawl phase, such as:

-  establishment of secure, direct access tunnels from requesting endpoints to private enterprise resources, regardless of whether the resources are located on-premises or in the cloud, driven by policy and enforced by PEPs

-  use of connectors that act as proxies for internal, private enterprise resources, enabling resources to be accessed by authenticated, authorized users while ensuring that they are not discoverable by or visible to others

-  protection for private enterprise resources hosted in the cloud that enables authenticated, authorized remote users to access those resources directly rather than having to hairpin through the enterprise network

-  ability to monitor, inspect, and enforce policy controls on traffic being sent to and from resources in the cloud or on the internet

-  discovery of new endpoints on the network and the ability to block newly discovered endpoints that are not compliant with policy

Build E1B2, which uses Zscaler as its PE, PA, and PEP, does not have an EPP because this build does not include any collaborators with EPP solutions that integrate with Zscaler. Zscaler (e.g., the Zscaler client connector) has capabilities to enforce policies based on a defined set of endpoint compliance checks to allow or deny user/endpoint access to a resource. However, it does not perform the functions of an EPP solution to protect an endpoint. Zscaler integrates with EPP solutions to receive a more robust set of information about the endpoints in order to make a decision to allow or deny access to a resource. However, in build E1B2, we do not have a collaborator with an EPP solution that can integrate with Zscaler.

Because there is no EPP in E1B2, there is no automatic solution to remediate an issue on the endpoint either.

Build E1B2 also does not have a collaborator with a solution that supports determination of confidence level/trust scores that can integrate with Zscaler. Due to the absence of a collaborator with this capability, Build E1B2 does not support the calculation of confidence levels/trust scores.

Build E2B1, which uses Ping Identity as its PE and PA and Ping Identity and Cisco Duo as its PEP, does not have an EPP. Cisco Duo provides limited device health information, but not the full spectrum that an EPP would provide. Because there is no official EPP in this build, there is no automatic solution to remediate an issue on the endpoint. An EPP for Enterprise 2 was included in a later build phase (E2B3).

Build E3B2 currently supports one-way integration between Microsoft Intune and Forescout eyeExtend. If Intune detects an endpoint out of compliance, eyeExtend can become informed of this problem by pulling information from Intune. However, if one of Forescout's discovery tools detects a problem with an endpoint, there is currently no mechanism for this information to be passed from Forescout eyeExtend to Microsoft Intune. Ideally, future integration of these products would allow Forescout eyeExtend to inform Microsoft Intune when it detects a non-Azure AD-connected endpoint that is non-compliant, as this would enable Intune to direct Azure AD to block sign-in from the non-compliant endpoint. Without a mechanism for enabling Forescout eyeExtend to send endpoint compliance information to Microsoft Intune, Azure AD does not have a way of knowing that a non-Azure AD-connected endpoint is not compliant.

SDP, Microsegmentation, and SASE Phase Findings
-----------------------------------------------

More integration of zero trust products from different vendors is needed to support the implementation of ZTAs that are built using components from a variety of vendors. For the most effective zero trust solutions, PDPs should integrate with a variety of security tools and other supporting components that enable the PDP to assess the real-time risk of any given access request.

It is not unusual for a ZTA to have multiple PDPs, each of which may be integrated with one or more different supporting component and/or PEPs. As a result, the policies that the ZTA enforces are not centrally located. Rather, they are configured and managed in association with each of the various PDPs. This makes it challenging to understand, articulate, and manage the ZTA's policies as a comprehensive whole.

In addition, the multiple PDPs that comprise a ZTA do not typically integrate with each other to share information and so do not have a shared understanding of what users, endpoints, or other subjects may pose risks. For example, one PDP may be aware that an endpoint is non-compliant, whereas this same endpoint compliance information is not available to another PDP. On the other hand, the second PDP may be aware that the endpoint's user may have exhibited suspicious behavior, whereas the first PDP is not. Ideally, when a ZTA has multiple PDPs, it is desirable to have an integrated approach that enables the PDPs to share information so that they can each be more fully informed, share a common, consolidated understanding of risks, and make a decision based on all information available.

The SIEM and/or SOAR components contain a wealth of information that could prove useful to a PDP as it tries to determine whether any given access request should be allowed or not. Ideally, the SIEM and SOAR should send this information to the PDP in real-time, if possible, to ensure that the PDP's access decisions are fully informed.

Ideally, data security tools should be integrated with the PDP so that the PDP can be made aware of instances in which access requests are denied by the tools that are designed to protect data.

Additionally, risk information and user behavior analytics should be shared with the PDP to potentially improve ZTA security.

Some zero trust SDP solutions for managing endpoints can also manage resources by installing clients onto those resources. However, solutions that are specifically designed to manage resources should be leveraged rather than the zero trust solutions that have the primary purpose of managing endpoints. In some cases, the solutions that manage resources do not have out-of-the-box integration with the PDPs. PDP integration capability should be available in these resource management solutions.

Endpoint compliance is essential for security. It is important to have tools that are capable of detecting when an endpoint is not compliant and ensuring that the endpoint is not permitted to access resources as a result. Furthermore, automatic solutions to remediate noncompliance issues on the endpoint should be deployed when possible, and these should be integrated with the organization's configuration and patch management systems.