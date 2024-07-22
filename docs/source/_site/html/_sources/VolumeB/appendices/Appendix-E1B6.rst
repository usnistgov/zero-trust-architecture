Enterprise 1 Build 6 (E1B6) - SDP and Microsegmentation - Ivanti Neurons for Zero Trust Access as PE
=====================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E1B6 uses products from Amazon Web Services, IBM, Ivanti, Mandiant, Okta, Radiant Logic, SailPoint, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`collaborators and their contributions`.

E1B6 components consist of Ivanti Neurons for Zero Trust Access (nZTA), Ivanti nZTA Gateway, Okta Identity Cloud, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Okta Verify App, Ivanti Secure Access Client, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable NNM, Mandiant Security Validation (MSV), DigiCert CertCentral, and AWS IaaS.

Table 1 lists all of the technologies used in Build E1B6. It lists the products used to instantiate each ZTA component and the security function that each component provides. The technologies in this table are used to support zero trust access for non-mobile devices. For the technologies used to support zero trust access for mobile devices, refer to :ref:`Enterprise 1 Build 1 (E1B1) <Enterprise 1 Build 1 (E1B1) - EIG Crawl - Okta Identity Cloud and Ivanti Access ZSO as PEs>`.

**Table 1 - E1B6 Products and Technologies**

.. csv-table:: E1B6 Products and Technologies
    :file: csv/AppendixT-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E1B6. We also describe E1B6's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

Figure 1 depicts the logical architecture of E1B6. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user, the requesting endpoint, and the resource; and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in Figure 1 have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, Figure 1 includes the specific products that instantiate the architecture of E1B6.

E1B6 was designed with Ivanti components that serve as PEs, PAs, and PEPs, and Okta Identity Cloud that serves as the identity, access, and credential manager. Radiant Logic acts as a PIP for the PDP as it responds to inquiries and provides identity information on demand in order for Okta to make near-real-time access decisions. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flow for a Successful Resource Access Request<message-flow-e1b6>`.

**Figure 1 - Logical Architecture of E1B6**

|Figure1|

ICAM Information Architecture
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How ICAM information is provisioned, distributed, updated, shared, correlated, governed, and used among ZTA components is fundamental to the operation of the ZTA. The ICAM information architecture ensures that when a subject requests access to a resource, the aggregated set of identity information and attributes necessary to identify, authenticate, and authorize the subject is available to be used as a basis on which to make the access decision.

In E1B6, Okta, Radiant Logic, and SailPoint integrate with each other as well as with other components of the ZTA to support the ICAM information architecture. The ways that these components work together to correlate identity information and to support actions such as users joining, changing roles, and leaving the enterprise are the same in E1B6 as they are in E1B1, E1B2, E1B3, E1B4, and E1B5. These interactions are described in :ref:`E1B1 ICAM Information Architecture<e1b1icam>`.

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 1` and :ref:`Enterprise 1 Branch Office` describe and depict the physical architecture of the E1B6 headquarters network and the E1B6 branch office network, respectively.

Message Flow for a Successful Resource Access Request 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _message-flow-e1b6:

This section depicts the authentication message flow supported by E1B6. In this flow, a subject who is authorized to access a resource requests and receives access to that resource. Access to the resource is authenticated and authorized by Ivanti nZTA. Ivanti nZTA is integrated with Okta, which acts as the IdP. The authentication message flow is the same regardless of whether the resource is located on-premises, in a private SaaS cloud, in a private IaaS cloud, or in a public cloud. The user is accessing the resource from a non-mobile device that has the Ivanti Secure Access Client running on it.

To access a resource, the user must first log into the Ivanti Secure Access Client that is running on the user's endpoint. This results in the establishment of secure tunnels from the user's Secure Access Client to all authorized Gateways guarding access to protected resources. Figure 2 depicts the steps that are performed when the user logs into the Ivanti Secure Access Client.

**Figure 2 - Use Case E1B6 - User Logs into the Ivanti Secure Access Client**

|Figure2|

When the user logs into the client, the following steps, as shown in Figure 2, are performed to initiate operations:

1. The user connects to the Ivanti Secure Access Client. The client and the nZTA Controller mutually authenticate using mTLS.

2. The user is redirected to Okta, the organization's SAML identity provider, for authentication.

3. Okta challenges the user for their first- and second-factor authentication credentials.

4. The user provides their first- and second-factor authentication credentials to Okta.

5. Assuming the user is authenticated successfully, Okta provides a SAML assertion and attributes to the client.

6. The Ivanti nZTA controller defines dynamic application policies to govern this user's access based on the SAML assertion attributes and the endpoint's compliance status and sends these policies to the client.

7. The Ivanti nZTA controller also sends these dynamic application policies governing this user's access to the Ivanti nZTA Gateway.

8. The client and the gateway mutually authenticate via mTLS and set up a secure tunnel.

Once an authorized user has logged into the Ivanti Secure Access Client, they may access any resource, either on-premises or in the cloud, that they are authorized to access, with the Gateway in each location acting as the PEP.

The Ivanti Secure Access Client is monitoring the device's posture. The Ivanti Secure Access Client is continually sending device compliance information to the Ivanti nZTA Controller. This ensures that the Ivanti nZTA Controller has up-to-date information about device posture. Communications between the Ivanti Secure Access Client and the nZTA Controller are occurring in the background on an ongoing basis and are not shown explicitly in the authentication flow.

Message Flow for a Request to Access a Resource that May Be On-Premises, in a Public Cloud, or in a Private Cloud
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Figure 3 depicts the high-level message flow supporting a user who requests access to a resource. The message flow begins after the user has already successfully logged into the Ivanti Secure Access Client and thereby established tunnels to all authorized Gateways guarding access to protected resources. In the figure, one Ivanti nZTA Gateway is shown.

**Figure 3 - Use Case E1B6 - User Requests Access to a Resource**

|Figure3|

The message flow depicted in Figure 3 consists of the following steps:

1. A user initiates access to an on-premises resource, e.g., GitLab.

2.  The endpoint sends a request packet to the resource via the tunnel that was set up between the Ivanti Secure Access Client and the Ivanti nZTA Gateway when the user logged into the Ivanti Secure Access Client. The request is sent in the tunnel from the client to the Gateway, and then the Gateway forwards the message to the resource.

3.  The resource, which in this case is GitLab, displays the option for the user to sign in with SAML. When the user clicks on the sign-on with SAML icon on the GitLab screen, the resource creates a SAML request and sends the SAML request to the user's endpoint via the Ivanti nZTA Gateway and the tunnel.

4.  The user's endpoint sends the SAML request to the Okta Identity Cloud, which is located on the internet.

5.  Okta prompts for username and password.

6.  The user responds with username and password.

7.  Okta authenticates the user and verifies the device certificate.

8.  Okta challenges the user to perform second-factor authentication using the Okta Verify App.

9.  The user provides the second authentication factor (e.g., biometrics).

10.  Okta generates a SAML assertion and sends it to the user's endpoint.

11. The user's endpoint sends the SAML assertion to the resource (GitLab) via the tunnel between the Ivanti Secure Access Client and the Ivanti nZTA Gateway. The resource accepts the assertion and grants the access request.

12. Throughout the access session, user traffic to and from the resource is transmitted back and forth through the tunnel, ensuring it is secured according to policy. The user is able to access applications via the gateway as permitted by the dynamic application policies.

13. 
   (a) The Ivanti Secure Access Client performs continuous compliance checks and communicates compliance changes to the Ivanti nZTA Controller. 
   (b) The nZTA Controller updates policies and sends the updates to the client and gateway. These updates are sent on an ongoing basis for the life of the secure access tunnel to ensure that the user, endpoint, and access requests continue to be permitted according to the dynamic application policies that were established.

.. |Figure1| image:: images/AppendixT-Figure1.png
   :alt: This figure depicts the logical architecture of E1B6. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user, the requesting endpoint, and the resource; and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access.
.. |Figure2| image:: images/AppendixT-Figure2.png
   :alt: This figure depicts the authentication message flow supported by E1B6. In this flow, a subject who is authorized to access a resource requests and receives access to that resource. Access to the resource is authenticated and authorized by Ivanti nZTA. Ivanti nZTA is integrated with Okta, which acts as the IdP. The authentication message flow is the same regardless of whether the resource is located on-premises, in a private SaaS cloud, in a private IaaS cloud, or in a public cloud. The user is accessing the resource from a non-mobile device that has the Ivanti Secure Access Client running on it.
.. |Figure3| image:: images/AppendixT-Figure3.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to a resource. The message flow begins after the user has already successfully logged into the Ivanti Secure Access Client and thereby established tunnels to all authorized Gateways guarding access to protected resources. In the figure, one Ivanti nZTA Gateway is shown.
