Enterprise 3 Build 5 (E3B5) - SDP and SASE - Microsoft Entra Conditional Access (formerly called Azure AD Conditional Access) and Microsoft Security Service Edge as PEs
========================================================================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E3B5 uses products from Mandiant, Microsoft, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`collaborators and their contributions`.

E3B5 components consist of Microsoft Entra Conditional Access, Microsoft Security Service Edge (SSE) (which includes Entra Private Access, Entra Internet Access, and Microsoft 365 Access), Microsoft Entra Private Access Connector, Microsoft Entra ID, Microsoft Entra ID Governance, Microsoft Intune, Microsoft Defender for Endpoint, Microsoft Global Secure Access Client, Microsoft Purview DLP, Microsoft Purview Information Protection, Microsoft Purview Information Protection Scanner, Microsoft Entra ID Identity Protection, Microsoft Defender for Identity, Microsoft Defender for Cloud, Microsoft Sentinel, Tenable.io, Tenable.ad, Mandiant Security Validation, Microsoft Azure (IaaS), Microsoft 365 (SaaS), and DigiCert CertCentral. (Note that Microsoft Entra ID was formerly named *Microsoft Azure AD*.)

Table 1 lists all of the technologies used in E3B5 ZTA. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E3B5 Products and Technologies**

.. csv-table:: E3B5 Products and Technologies
    :file: csv/AppendixS-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E3B5. We also describe E3B5's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

Figure 1 depicts the logical architecture of E3B5. Figure 1 uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in Figure 1 have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, Figure 1 includes the specific products that instantiate the architecture of E3B5. Figure 1 also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E3B5 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E3B5 was designed with Microsoft Entra Conditional Access, Microsoft Defender for Cloud, Microsoft Intune, Microsoft SSE, and Microsoft Sentinel as the ZTA PEs and PAs and Microsoft Entra ID providing ICAM support. It includes four PEPs: Microsoft Entra Conditional Access, Microsoft Defender for Endpoint, Microsoft Intune, and Microsoft SSE. A more detailed depiction of the messages that flow among components to support user access requests in the case in which a new endpoint is detected on the network and checked for compliance can be found in :ref:`Message Flows for a Successful Resource Access Request`.

**Figure 1 - Logical Architecture of E3B5**

|Figure1|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 3` describes the physical architecture of the E3B5 network.

Message Flows for a Successful Resource Access Request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This section presents three high-level message flows in which Microsoft Entra ID and Microsoft Entra SSE determine and enforce whether a user will be granted access to a requested resource. The user's endpoint is running Microsoft Global Secure Access (GSA) Client. The first flow depicts the case in which an authenticated, authorized user requests access to a private resource. The second case depicts a user requesting access to an internet resource that they are permitted by policy to access, and the third case depicts a user requesting access to a Microsoft SaaS services resource that they are permitted by policy to access.

Use Case in which Access to a Private Resource is Requested 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 2 depicts the message flow for the use case in which a user requests and receives access to a private resource.

**Figure 2 - Use Case E3B5 - User Requests and Receives Access to a Private Resource**

|Figure2|

The message flow depicted in Figure 2 consists of the following steps:

1. A user attempts to navigate to a private resource. The GSA Client on the user's endpoint intercepts the first IP packet, consults its traffic acquisition policy, and determines that the packet should be acquired. The GSA Client queues the packet until it determines that a tunnel has been established.

   The GSA Client checks if there is already an outer tunnel instance. If not, it reaches out to the Tunneling Client to create the outer tunnel instance. Entra SSE forces Entra ID user authentication to create an authenticated tunnel.

2. The GSA Client forces the user to authenticate to Entra ID. The user authenticates with Entra ID, providing both first and second authentication factors. Assuming the authentication is successful, Entra ID sends an access token for Entra Private Access to the GSA Client.

3. The user attempts to navigate to the private resource, but the GSA Client recognizes that this is part of the traffic profile to be captured and sends this request to the Entra SSE instead, inside the tunnel created earlier.

4. The GSA Client validates with Entra ID that the user has been assigned to the private resource and enforces any conditional access policies that apply to the private resource.

5. Entra ID sends the GSA Client an access token for the user to access the private resource.

6. The GSA Client sends this access token to Entra SSE.

7. Entra SSE forwards the access token to the private resource via the connector.

8. The private resource responds via the connector, and the response is forwarded to Entra SSE.

9. Entra SSE forwards the response to the GSA Client. Subsequent traffic on the access session continues to flow on the authenticated tunnel between the GSA Client and Entra SSE and then to the private resource via the Entra Private Access Connector. Throughout this communication session, Entra SSE Private Access Service enforces any conditional access policies that apply to this private resource access session.

Use Case in which Access to an Internet Resource is Requested 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 3 depicts the message flow for the use case in which a user requests and receives access to an internet resource.

**Figure 3 - Use Case E3B5 - User Requests and Receives Access to an Internet Resource**

|Figure3|

The message flow depicted in Figure 3 consists of the following steps:

1.  A user attempts to navigate to an internet resource. The GSA Client on the user's endpoint intercepts the first IP packet, consults its traffic acquisition policy, and determines that the packet should be acquired. The GSA Client queues the packet until it determines that a tunnel has been established. The GSA Client checks if there is already an outer tunnel instance. If not, it reaches out to the Tunneling Client to create the outer tunnel instance. 

2. The GSA client forces the user to authenticate to Entra ID. The user authenticates with Entra ID, providing both first and second authentication factors. Assuming the authentication is successful, Entra ID sends an access token for internet Access to the GSA client.

3. The queued packet is now sent inside the tunnel that was created earlier to the Microsoft Entra SSE Internet Access Service.

4. Microsoft Entra SSE Internet Access Service determines with Entra ID the user (or group) and enforces any conditional access policies that apply to the conditional access security profile.

5. Entra ID sends the GSA client an access token with an identifier that indicates the conditional access policy and security profile to be applied to the access session.

6. GSA Client sends encapsulated data destined for the Internet location with the access token for the matching security profile(s) to Entra SSE.

7. If the traffic is matched to a policy rule (first match wins), traffic is forwarded to the internet destination.

8. The internet destination responds to Entra SSE.

9. Entra SSE forwards the response to the GSA Client. Subsequent traffic on the access session continues to flow on the tunnel between the GSA Client and Entra SSE and then to the internet destination. Throughout this communication session, Entra SSE Internet Access Service enforces any conditional access policies that apply to this internet access session.

Use Case in which Access to a Microsoft SaaS Service Resource is Requested 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 4 depicts the message flow for the use case in which a user requests and receives access to a Microsoft SaaS Service resource.

**Figure 4 - Use Case E3B5 - User Requests and Receives Access to a Microsoft SaaS Service Resource**

|Figure4|

The message flow depicted in Figure 4 consists of the following steps:

1. An M365 client app or an Entra ID aware native client app is requesting a new token using the Microsoft Authentication Library. 

2. The GSA Client intercepts the first IP packet for the M365 destination and determines if the packet is to be acquired based on its traffic acquisition policy, which in this case is the Microsoft 365 traffic profile, and queues the packet until the tunnel is established.

    a. The GSA Client checks if any outer tunnel instance is present. If not, it reaches out to the Tunneling Client to create the outer tunnel instance.

    b. The Entra SSE service forces Entra ID user authentication to create an authenticated tunnel.

    c. The GSA Client initiates an Entra ID authentication, and Entra ID provides the access token to the GSA Client. The GSA Client stores it locally.

3. The queued packet is now sent inside the tunnel that was created earlier to the Microsoft SSE Internet Access service.

    a. Entra ID enforces any Conditional Access policies that apply to the Conditional Access Control targeting the Microsoft 365 traffic profile under Target resource or other Conditional Access policy controls such as Compliant Network with Microsoft's SSE Internet Access Service.

4. Entra ID returns an M365 access token or rejects the request to the M365 app, depending on policy. In this case, Entra ID returns an M365 access token via Microsoft SSE Internet Access and the GSA Client.

5. The M365 app sends the request to the M365 service, such as SharePoint online, via the GSA Client and the Microsoft SSE Internet Access service.

6. The respective M365 service endpoint (e.g., SharePoint Online) will respond to the M365 app via the Microsoft SSE Internet Access service and the GSA Client.

.. |Figure1| image:: images/AppendixS-Figure1.png
   :alt: This figure depicts the logical architecture of E3B5. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. 
.. |Figure2| image:: images/AppendixS-Figure2.png
   :alt: This figure depicts the message flow for the use case in which a user requests and receives access to a private resource.
.. |Figure3| image:: images/AppendixS-Figure3.png
   :alt: This figure depicts the message flow for the use case in which a user requests and receives access to an internet resource.
.. |Figure4| image:: images/AppendixS-Figure4.png
   :alt: This figure depicts the message flow for the use case in which a user requests and receives access to a Microsoft SaaS Service resource.
