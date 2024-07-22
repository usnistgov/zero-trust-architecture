Enterprise 2 Build 4 (E2B4) - SDP and SASE - Symantec Cloud Secure Web Gateway, Symantec ZTNA, and Symantec Cloud Access Security Broker as PEs
===============================================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E2B4 uses products from Google Cloud, IBM, Mandiant, Okta, Radiant Logic, SailPoint, Symantec by Broadcom, Tenable, and VMware. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E2B4 components consist of Symantec Cloud Secure Web Gateway (Cloud SWG), Symantec Zero Trust Network Access (ZTNA), Symantec Cloud Access Security Broker (CASB), Symantec Endpoint Security Agent, VMware Workspace ONE UEM, Symantec DLP Cloud Detection Service, Symantec ZTNA Connector, Okta Identity Cloud, Okta Verify App, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable Nessus Network Monitor (NNM), Mandiant Security Validation (MSV), Google Cloud, and DigiCert CertCentral.

*Table 1* lists all of the technologies used in Build E2B4. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E2B4 Products and Technologies**

.. csv-table:: E2B4 Products and Technologies
    :file: csv/AppendixN-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E2B4. We also describe E2B4's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E2B4. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E2B4. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E2B4 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E2B4 was designed with Symantec by Broadcom components that serve as PEs, PAs, and PEPs. Okta Identity Cloud serves as the identity, access, and credential manager. Radiant Logic acts as a PIP for the PDP as it responds to inquiries and provides identity information on demand in order for Okta Identity Cloud to make near-real-time access decisions. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flows for Successful Resource Access Requests<Appendix-E2B4-MessageFlows>`.

**Figure 1 - Logical Architecture of E2B4**

|Figure1|

ICAM Information Architecture
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How ICAM information is provisioned, distributed, updated, shared, correlated, governed, and used among ZTA components is fundamental to the operation of the ZTA. The ICAM information architecture ensures that when a subject requests access to a resource, the aggregated set of identity information and attributes necessary to identify, authenticate, and authorize the subject is available to be used as a basis on which to make the access decision.

In E2B4, Okta Identity Cloud, Radiant Logic, and SailPoint integrate with each other as well as with other components of the ZTA to support the ICAM information architecture. The ways that these components work together to correlate identity information and to support actions such as users joining, changing roles, and leaving the enterprise are the same in E2B4 as they are in E1B1, E1B2, E1B3, and E1B4. These interactions are described in :ref:`E1B1 - ICAM Information Architecture <E1B1ICAM>`.

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 2` describes the physical architecture of the E2B4 network.

Message Flows for Successful Resource Access Requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _Appendix-E2B4-MessageFlows:

This section depicts several authentication message flows supported by E2B4. In each flow, a subject who is authorized to access a resource requests and receives access to that resource. Access to the resource is authenticated and authorized by various Symantec by Broadcom components that act as PDPs and PEPs. The scenarios differ according to whether or not the requesting user's device has a Symantec Endpoint Security Agent running on it, and whether the resource is an enterprise resource (i.e., located on-premises or in a private IaaS cloud) or on the public internet.

Message Flow for Symantec Endpoint Security Agent Initialization and an Identity Aware Tunnel Establishment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If the requesting user's device has the Symantec Endpoint Security Agent running on it, then the agent must be initialized and the user must log into it. Once successfully logged in, an identity-aware tunnel will be established between the agent and the Symantec Cloud SWG that secures all of their subsequent communications. In addition, the Symantec Endpoint Security Agent will continually evaluate the compliance of the endpoint and provide ongoing updates to the SWG via the tunnel, thereby keeping the SWG informed of the device's compliance status.

*Figure 2* depicts the high-level message flow supporting Symantec Endpoint Security Agent initialization and establishment of the identity-aware tunnel. In all scenarios in which the requesting user's device has a Symantec Endpoint Security Agent installed, initialization of the agent and establishment of the tunnel are the first things that happen.

**Figure 2 - Use Case E2B4 - Symantec Endpoint Security Agent Initialization and Identity Aware Tunnel Establishment**

|Figure2|

The message flow depicted in *Figure 2* consists of the following steps:

1. The Symantec Endpoint Security Agent sends a message to the Symantec Cloud SWG requesting the organizational configuration.

2. The Symantec Cloud SWG provides the agent with the configuration.

3. The Symantec Endpoint Security Agent sends a SAML request to Okta, the IdP for this build.

4. Okta challenges the user for authentication credentials (i.e., username and password).

5. The user responds with their credentials.

6. Assuming the user was able to be authenticated, Okta provides the Symantec Endpoint Security Agent with a SAML assertion.

7. The identity-aware tunnel is established between the Symantec Endpoint Security Agent and the Symantec Cloud SWG.

8. On an ongoing basis, the Symantec Endpoint Security Agent evaluates the compliance of the user's device.

9. The Symantec Endpoint Security Agent periodically sends updates on the device's compliance status to the Symantec Cloud SWG via the tunnel.

Message Flow for a User with a Symantec Endpoint Security Agent-Equipped Endpoint Requesting Access to an Enterprise Resource
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the high-level message flow supporting a user who has a Symantec Endpoint Security Agent-equipped endpoint and requests access to an enterprise resource. The enterprise resource may be located either on-premises or in a private IaaS cloud.

**Figure 3 - Use Case E2B4 - User with a Symantec Endpoint Security Agent-Equipped Device Accesses an Enterprise Resource**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1. As explained earlier, before the user can access the resource, the Symantec Endpoint Security Agent on the user's device must be initialized, and it must establish an identity-aware tunnel with the Symantec Cloud SWG. The message flow that accomplishes this is described in :ref:`Message Flow for Symantec Endpoint Security Agent Initialization and an Identity Aware Tunnel Establishment`.

2.  The user requests access to an enterprise resource. This request is sent over the secure identity-aware tunnel to the Symantec Cloud SWG.

3.  The Symantec Cloud SWG forwards the user's access request to the Symantec ZTNA Controller.

4.  The Symantec ZTNA Controller forwards the request to the site-specific ZTNA connector, i.e., the connector for the resource to which access is being requested. The choice of connector will depend on the location of the resource—e.g., whether it is on-premises or in the cloud, and what subnetwork it is on.

5.  The ZTNA connector queries the private DNS for the resource's IP address.

6.  DNS provides the IP address of the resource to the user's device.

7.  The user's device sends the Symantec ZTNA Controller a request to establish an access tunnel to the resource.

8.  The ZTNA Controller evaluates this access tunnel request against organizational policy to determine if it is authorized.

9. Assuming the access tunnel request is permissible by policy, the Symantec ZTNA Controller sends the approved access tunnel request to the ZTNA Connector for the resource (again, the ZTNA Connector selected will depend on where the resource is located—on-premises or in a private IaaS cloud, and what subnetwork the resource is on if there are multiple connectors at that location).

10. The ZTNA Connector establishes a tunnel to the resource.

11. Access is established from the user's endpoint to the resource.

12. The user attempts to log into the resource (e.g., the GitLab application).

13. The resource redirects the user's access request to the organization's IdP, Okta, via SSO. Okta challenges the user for their first- and second-factor authentication credentials.

14. The user provides their first- and second-factor authentication credentials to Okta.

15. Assuming the user is authenticated successfully, Okta provides a SAML assertion to the user.

16. The user sends the SAML assertion to the resource. The resource accepts the assertion and grants the access request.

17. A session between the user and the resource is established. User traffic to and from the resource is secured according to policy.

Message Flow for a User Requesting Access to an Enterprise Resource from a Web Browser
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 4* depicts the high-level message flow supporting a user who requests access to an enterprise resource from a web browser. The enterprise resource may be located either on-premises or in a private IaaS cloud.

**Figure 4 - Use Case E2B4 - User Requesting Access to an Enterprise Resource from a Web Browser**

|Figure4|

The message flow depicted in *Figure 4* consists of the following steps:

1. The user requests access to an enterprise resource. The user makes this request by typing the URL for the enterprise resource into their browser.

2. The user's browser sends a request to the Global DNS to get the IP address of the enterprise resource.

3. The DNS resolves the address request to the Symantec ZTNA Controller.

4. The Symantec ZTNA Controller redirects the user to Okta, the organization's IdP, which challenges the user for their first- and second-factor authentication credentials.

5. The user provides their first- and second-factor authentication credentials to Okta.

6. Assuming the user is authenticated successfully, Okta provides a SAML assertion to the user.

7. The user sends the SAML assertion to the Symantec ZTNA Controller.

8. The ZTNA Controller evaluates the SAML assertion in light of the organization's access policy and the device's compliance status.

9. Assuming the access request is permissible by policy, the Symantec ZTNA Controller forwards the approved request to the site-specific ZTNA Connector. (The ZTNA Connector selected will depend on where the resource is located—on-premises or in a private IaaS cloud, and what subnetwork the resource is on if there are multiple connectors at that location.)

10. The ZTNA Connector establishes a tunnel to the resource.

11. A session between the user and the resource is established. User traffic to and from the resource is secured according to policy, and the session is evaluated on an ongoing basis to ensure that it continues to be permitted according to organizational policy.

Message Flow for a User with a Symantec Endpoint Security Agent-equipped Endpoint Requesting Access to a Public Internet Resource
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 5* depicts the high-level message flow supporting a user who has a Symantec Endpoint Security Agent-equipped endpoint and requests access to a public internet resource.

**Figure 5 - Use Case E2B4 - User with a Symantec Endpoint Security Agent-Equipped Device Accesses a Public Internet Resource**

|Figure5|

The message flow depicted in *Figure 5* consists of the following steps:

1. As explained earlier, before the user can access the resource, the Symantec Endpoint Security Agent on the user's device must be initialized, and it must establish an identity-aware tunnel with the Symantec Cloud SWG. The message flow that accomplishes this is described in :ref:`Message Flow for Symantec Endpoint Security Agent Initialization and an Identity Aware Tunnel Establishment`.

2. The user requests access to a public internet resource by providing the resource's URL. This request is sent over the secure identity-aware tunnel to the Symantec Cloud SWG.

3. The Symantec Cloud SWG's policy engine evaluates this access request against organizational policy and risk protection engines.

4. Assuming the requested access has been determined to be permissible, the request is forwarded onto the internet.

5. A web session between the user and the public internet resource is established, with all communications flowing to and from the user's device via the tunnel that was established between the device and the Symantec Cloud SWG. Throughout the web session, the Symantec Cloud SWG performs ongoing policy-based evaluation of the session to ensure that it continues to be permissible.

.. |Figure1| image:: images/AppendixN-Figure1.png
   :alt: This figure depicts the logical architecture of E2B4. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health.
.. |Figure2| image:: images/AppendixN-Figure2.png
   :alt: This figure depicts the high-level message flow supporting Symantec Endpoint Security Agent initialization and establishment of the identity-aware tunnel.
.. |Figure3| image:: images/AppendixN-Figure3.png
   :alt: This figure depicts the high-level message flow supporting a user who has a Symantec Endpoint Security Agent-equipped endpoint and requests access to an enterprise resource.
.. |Figure4| image:: images/AppendixN-Figure4.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to an enterprise resource from a web browser.
.. |Figure5| image:: images/AppendixN-Figure5.png
   :alt: This figure depicts the high-level message flow supporting a user who has a Symantec Endpoint Security Agent-equipped endpoint and requests access to a public internet resource.