Enterprise 1 Build 4 (E1B4) - SDP - Appgate SDP Controller as PE
================================================================

.. include:: /_publication_note.rst

Technologies
------------

E1B4 uses products from Amazon Web Services, Appgate, IBM, Ivanti, Mandiant, Okta, Radiant Logic, SailPoint, Tenable, and Zimperium. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E1B4 components consist of Appgate SDP Controller, Appgate SDP Gateway, Appgate SDP client, Appgate Portal, Appgate Injector (Appgate for Kubernetes), Okta Identity Cloud, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Okta Verify App, Ivanti Neurons for Unified Endpoint Management (UEM) Platform, Zimperium Mobile Threat Defense, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable NNM, IBM Cloud Pak for Security, Mandiant Security Validation (MSV), DigiCert CertCentral, and AWS IaaS.

*Table 1* lists all of the technologies used in Build E1B4. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E1B4 Products and Technologies**

.. csv-table:: E1B4 Products and Technologies
    :file: csv/AppendixM-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E1B4. We also describe E1B4's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E1B4. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user, the requesting endpoint, and the resource; and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E1B4.

E1B4 was designed with Appgate components that serve as PEs, PAs, and PEPs, and Okta Identity Cloud that serves as the identity, access, and credential manager. Radiant Logic acts as a PIP for the PDP as it responds to inquiries and provides identity information on demand in order for Okta to make near-real-time access decisions. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flows for Successful Resource Access Requests<Appendix-E1B4-MessageFlows>`.

**Figure 1 - Logical Architecture of E1B4**

|Figure1|

ICAM Information Architecture
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How ICAM information is provisioned, distributed, updated, shared, correlated, governed, and used among ZTA components is fundamental to the operation of the ZTA. The ICAM information architecture ensures that when a subject requests access to a resource, the aggregated set of identity information and attributes necessary to identify, authenticate, and authorize the subject is available to be used as a basis on which to make the access decision.

In E1B4, Okta, Radiant Logic, and SailPoint integrate with each other as well as with other components of the ZTA to support the ICAM information architecture. The ways that these components work together to correlate identity information and to support actions such as users joining, changing roles, and leaving the enterprise are the same in E1B4 as they are in E1B1, E1B2, and E1B3. These interactions are described in :ref:`E1B1 - ICAM Information Architecture <E1B1ICAM>`.

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 1` and :ref:`Enterprise 1 Branch Office` describe and depict the physical architecture of E1B4 headquarters network and E1B4 branch office network, respectively.

Message Flows for Successful Resource Access Requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _Appendix-E1B4-MessageFlows:

This section presents the high-level message flows supporting the use cases in which a subject who has an enterprise ID and who is authorized to access an enterprise resource requests and receives access to that resource. In the cases depicted here, access to the resource is protected by the Appgate SDP System, which is comprised of Controllers that act as PDPs; Gateways that acts as PEPs; and the Appgate SDP Client, which supports endpoint compliance. The Appgate system integrates with Okta, which acts as identity provider (IdP); Ivanti Neurons for UEM, which acts as endpoint manager; and Zimperium Mobile Threat Defense. Two message flows are depicted: one in which the resource being accessed is located on-premises and another in which the resource is in the AWS cloud. For the on-premises case, the Appgate SDP Controller and Gateway are located on-premises. For the AWS case, the Appgate SDP Controller and Gateway are located in the cloud.

Both use cases that are depicted show only the messages that are sent in response to the access request. However, the authentication process also relies on the following additional background communications that occur among components:

-  The Ivanti Neurons for UEM agent that is running on the user's endpoint (mobile devices only) periodically syncs with the Ivanti Neurons for UEM Platform in the cloud to reauthenticate the requesting endpoint device using a unique certificate that has been provisioned specifically for that device, and sends the cloud component information about device posture and health (e.g., risk score, threat defense status, iOS version).

-  Zimperium Mobile Threat Defense is integrated with Ivanti Neurons for UEM, and Zimperium periodically sends threat information to it. When Zimperium detects a threat, it can also block the threat as well as send Ivanti information about the threat.

-  When a user initiates login with the Appgate Mobile Client, the Appgate SDP Controller queries the Ivanti Neurons for UEM Platform to obtain real-time information regarding device health for the user's device. The Appgate SDP Client running on the user's endpoint periodically syncs with the Appgate SDP System to provide information regarding device compliance and dynamically adjusts user and device attributes and authorizations.

To access a resource in both use cases depicted here, the user must log into the Appgate SDP Client that is running on the user's endpoint. When the user logs into the client, the following steps are performed to initiate operations:

1. The Appgate SDP Client sends an encrypted Single Packet Authorization (SPA) UDP packet to the Controller to pre-authorize the subsequent TLS connection.

2. The Appgate SDP Client establishes a TLS connection and authenticates to the Appgate SDP Controller. During this process, the user is redirected to Okta and the SAML assertion is sent to the Controller.

3. The Appgate SDP Controller issues a signed and encrypted entitlement token to the client that contains user and device attributes, protected resource authorizations, and the hostnames and SPA keys for authorized Appgate Gateways.

4. The Appgate SDP Client creates a TLS tunnel and passes the signed Entitlement token to an Appgate Gateway that is guarding resources the client is authorized to access. (Note: When there are multiple gateways guarding the same resource, the client chooses one of the gateways based on load balancing information contained in the entitlement token.)

5. The Appgate Gateway validates the token and creates a session-based microfirewall for the user/device to enforce policies created on the Appgate SDP Controller.

Once an authorized user has logged into the Appgate SDP Client, they may access any resource, either on-premises or in the cloud, that they are authorized to access, with the Gateway in each location acting as the PEP.

Use Case in which Access to a Resource that Is On-Premises Is Enforced by Appgate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 2* depicts the message flow for the user's request to access the resource located on-premises. The message flow begins after the user has already successfully logged into the Appgate SDP Client and established tunnels to all authorized Gateways guarding access to protected resources, which, in this case, is the Appgate SDP Gateway that is located on-premises.

**Figure 2 - Use Case E1B4 - Access to an On-Premises Resource Is Enforced by Appgate**

|Figure2|

The message flow depicted in **Figure 2** consists of the following steps:

1.  A user initiates access to an on-premises resource, e.g., GitLab.

2.  The endpoint sends a request packet to the resource via this tunnel. The request is sent in the tunnel from the client to the Gateway, and then the Gateway forwards the message to the resource.

3.  The resource, which in this case is GitLab, displays the option for the user to sign in with SAML. When the user clicks on the sign-on with SAML icon on the GitLab screen, the resource creates a SAML request and sends the SAML request to the user's endpoint via the Appgate Gateway and the tunnel.

4.  The user's endpoint sends the SAML request to the Okta Identity Cloud, which is located on the internet.

5.  Okta prompts for username and password.

6.  The user responds with username and password.

7.  Okta authenticates the user and verifies the device certificate.

8.  Okta challenges the user to perform second-factor authentication using the Okta Verify App.

9.  The user provides the second authentication factor (i.e., biometrics).

10. Okta generates a SAML assertion and sends it to the user's endpoint.

11. The user's endpoint sends the SAML assertion to the resource (GitLab) via the tunnel between the Appgate SDP Client and the Appgate SDP Gateway. The resource accepts the assertion and grants the access request.

12. User traffic to and from the resource is transmitted back and forth through the Appgate tunnel, ensuring it is secured according to policy.

The Appgate SDP Client collects system attributes every five minutes and updates the Appgate SDP Controller to ensure the client conforms with policy.

Note that the message flow depicted in Figure 2 is the same regardless of whether the employee is located on-premises at headquarters, on-premises at a branch office, or off-premises at a remote location.

Use Case in which Access to a Resource in the AWS Cloud is Enforced by Appgate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the message flow for the user's request to access the resource located in the AWS cloud. The message flow begins after the user has already successfully logged into the Appgate SDP Client and established tunnels to all authorized Gateways guarding access to protected resources, which, in this case, is the Appgate SDP Gateway that is located in AWS.

**Figure 3 - Use Case E1B4 - Access to an AWS Cloud Resource Is Enforced by Appgate**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1.  A user initiates access to an AWS cloud resource, e.g., GitLab.

2.  The endpoint sends a request packet to the resource via this tunnel. The request is sent in the tunnel from the client to the Gateway, and then the Gateway forwards the message to the resource.

3.  The resource, which in this case is GitLab, displays the option for the user to sign in with SAML. When the user clicks on the sign-on with SAML icon on the GitLab screen, the resource creates a SAML request and sends the SAML request to the user's endpoint via the Appgate Gateway and the tunnel.

4.  The user's endpoint sends the SAML request to the Okta Identity Cloud, which is located on the internet.

5.  Okta prompts for username and password.

6.  The user responds with username and password.

7.  Okta authenticates the user and verifies the device certificate.

8.  Okta challenges the user to perform second-factor authentication using the Okta Verify App.

9.  The user provides the second authentication factor (i.e., biometrics).

10. Okta generates a SAML assertion and sends it to the user's endpoint.

11. The user's endpoint sends the SAML assertion to the resource (GitLab) via the tunnel between the Appgate SDP Client and the Appgate SDP Gateway. The resource accepts the assertion and grants the access request.

12. User traffic to and from the resource is transmitted back and forth through the Appgate tunnel, ensuring it is secured according to policy.

The Appgate SDP Client collects system attributes every five minutes and updates the Appgate SDP Controller to ensure the client conforms with policy.

Note that the message flow depicted in *Figure 3* is the same regardless of whether the employee is located on-premises at headquarters, on-premises at a branch office, or off-premises at home or elsewhere.

Service-to-Service Use Case in which a request by one service to access another service is controlled by Appgate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For this use case, the requesting service has an embedded headless client, i.e., a client that does not have a user interface. This headless client must be pre-configured with an identity profile and credentials. Upon boot-up, the headless client immediately tries to sign in to the Appgate SDP Controller (and it will continue retrying if it fails). The steps in the process are depicted in Figure 4 and described below.

**Figure 4 - Use Case E1B4 - Server-to-Server Access Enforced by Appgate**

|Figure4|

The message flow depicted in *Figure 4* consists of the following steps:

1. The headless client sends an encrypted SPA UDP packet to the Controller to pre-authorize the subsequent TLS connection.

2. The headless client establishes a TLS connection and authenticates to the Appgate SDP Controller.

3. The Appgate SDP Controller issues a signed entitlement token to the headless client that enables it to access the resources protected by Appgate SDP that it has been authorized to access according to policy created on the Controller.

4. The headless client will automatically try to establish a secure connection with an Appgate Gateway that is guarding resources that the headless client is authorized to access by passing the signed entitlement token to the Gateway.

5. The Gateway validates the token and creates a session-based micro-firewall for the headless client to enforce policies created on the Appgate SDP Controller.

Once a session-based micro-firewall for the headless client has been created on an Appgate SDP Gateway at each site (e.g., on-premises and in AWS), the headless client may access any authorized resource, with the Gateway(s) in each location acting as the PEP. If the headless client initiates access to a protected resource it is authorized to access, the Gateway will route the request to the resource. If the headless client initiates access to a protected resource it is not authorized to access, the Gateway's session-based micro-firewall will drop the network packets.

The headless client is not re-authenticated every time it initiates access to a protected resource. However, the Appgate SDP Headless Client collects system attributes every five minutes and updates the Appgate SDP Controller to ensure the client conforms with policy.

.. |Figure1| image:: images/AppendixM-Figure1.png
   :alt: This figure depicts the logical architecture of E1B4. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health.
.. |Figure2| image:: images/AppendixM-Figure2.png
   :alt: This figure depicts the message flow for the user's request to access the resource located on-premises.
.. |Figure3| image:: images/AppendixM-Figure3.png
   :alt: This figure depicts the message flow for the user's request to access the resource located in the AWS cloud.
.. |Figure4| image:: images/AppendixM-Figure4.png
   :alt: This figure shows the steps in the process for the service-to-service use case in which a request by one service to access another service is controlled by Appgate.
