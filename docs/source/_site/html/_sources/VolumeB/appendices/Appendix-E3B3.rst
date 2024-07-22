Enterprise 3 Build 3 (E3B3) - SDP and Microsegmentation - Microsoft Azure AD Conditional Access (later renamed *Entra Conditional Access*), Microsoft Intune, Microsoft Sentinel, Forescout eyeControl, and Forescout eyeExtend as PEs
===========================================================================================================================================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E3B3 uses products from F5, Forescout, Mandiant, Microsoft, Palo Alto Networks, PC Matic, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E3B3 components consist of F5 BIG-IP, Microsoft AD, Microsoft Azure AD, Microsoft Azure AD (Conditional Access), Microsoft Azure AD Identity Governance, Microsoft Intune, Microsoft Sentinel, Microsoft Azure App Proxy, Microsoft Defender for Endpoint, Microsoft Azure AD Identity Protection, Microsoft Azure Application Gateway, Microsoft Defender for Identity, Microsoft Defender for Office, Microsoft Entra Permissions Management, Microsoft Defender for Cloud Apps, PC Matic Pro, Tenable.io, Tenable.ad, Tenable NNM, Mandiant Security Validation, Forescout eyeControl, Forescout eyeExtend, Forescout eyeSight, Forescout eyeSegment, Palo Alto Networks NGFW, Microsoft Purview - DLP, Microsoft Purview Information Protection, Microsoft Purview Information Protection Scanner, Microsoft Intune VPN Tunnel, Microsoft Azure Arc, Microsoft Azure Automanage, Microsoft Intune Privilege Access Workstation, Microsoft Azure Virtual Desktop, Microsoft Defender for Cloud, Microsoft Azure (IaaS), Microsoft 365 (SaaS), and DigiCert CertCentral. (Note that after this build was completed, the name *Azure AD* was changed to *Entra ID*. Also, the name *Defender for Cloud Apps* was changed to *Defender for Apps* and the name *Azure Application Proxy* was changed to *Entra Application Proxy*. This appendix uses the original name of *Microsoft Azure AD*, *Microsoft Defender for Cloud Apps* and *Microsoft Azure App Proxy*.)

*Table 1* lists all of the technologies used in E3B3 ZTA. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E3B3 Products and Technologies**

.. csv-table:: E3B3 Products and Technologies
    :file: csv/AppendixK-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E3B3. We also describe E3B3's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E3B3. *Figure 1* uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E3B3. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E3B3 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E3B3 was designed with Microsoft Azure AD (Conditional Access), Microsoft Defender for Cloud, Microsoft Defender for Cloud Apps, Microsoft Defender for Office, Microsoft Intune, Microsoft Sentinel, Forescout eyeControl, and Forescout eyeExtend as the ZTA PEs and PAs, and Microsoft AD and Azure AD providing ICAM support. It includes nine PEPs: Microsoft Azure AD (Conditional Access), Microsoft Azure App Gateway, Microsoft Azure App Proxy, Microsoft Defender for Cloud Apps, Microsoft Defender for Endpoint, Microsoft Defender for Office,Microsoft Intune, F5 BIG-IP, and Palo Alto Networks NGFW. A more detailed depiction of the messages that flow among components to support user access requests in the case in which a new endpoint is detected on the network and checked for compliance can be found in :ref:`E3B2 - Message Flows for a Successful Resource Access Request <AppendixHMessageFlows>`.

**Figure 1 - Logical Architecture of E3B3**

|Figure1|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 3` describes the physical architecture of the E3B3 network.

Message Flows for a Successful Resource Access Request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The two message flows for E3B1 that are described in :ref:`E3B1 - Message Flows for a Successful Resource Access Request <AppendixFMessageFlows>` both still apply to E3B3 for cases in which the resource being accessed is located on-premises. Those message flows depict the use cases in which an on-premises resource being accessed is protected by Azure AD alone (see :ref:`Use Case in which Resource Access Is Enforced by Azure AD`), and in which an on-premises resource being accessed is protected by Azure AD in conjunction with the F5 BIG-IP PEP (see :ref:`Use Case in which Resource Access Is Enforced by an F5 BIG-IP PEP`).

In addition, three additional high-level message flows that are described in :ref:`E3B2 - Message Flows for a Successful Resource Access Request <AppendixHMessageFlows>` also still apply to E3B3. These message flows describe the cases in which a private resource being accessed is located in the cloud (see :ref:`Use Case in which Access to a Private Cloud Resource is Enforced by Azure AD and Azure AD's Application Proxy`); an externally-facing resource being accessed is in the cloud (see :ref:`Use Case in which Access to an Externally Facing Cloud Resource is Enforced by Azure AD and Monitored by Microsoft Defender for Cloud Apps`); and a new endpoint is discovered on the network, found to be non-compliant with enterprise policy, and blocked from accessing all resources (see :ref:`Use Case in which a Non-Compliant Endpoint is Discovered on the Network and Blocked from Accessing Resources`).

This section presents high-level message flows, each of which supports the use case in which an authenticated, authorized user who has already been granted access to a resource is engaged in an active access session when events occur that cause the user's access to be revoked.

In the first flow, many Microsoft Defender components are running to monitor and protect access to the resource (Defender for Endpoint, Defender for Cloud, Defender for Cloud Apps, Defender for Identity). The Defender security portal enables a network administrator to see all of the information produced by these Defender components in a single pane of glass. These Defender components all send suspicious or anomalous event information to Microsoft Sentinel. Sentinel uses configured automation rules to determine that the detected event is a dangerous enough activity that it warrants revoking the user's existing access. Sentinel directs Azure AD to restrict user access and take other policy-based action based on the event information.

In the second flow, Intune MDM monitors the endpoint for compliance and sends logs to Sentinel. When Intune detects that the device posture is no longer compliant, it notifies Azure AD, which prevents the user from accessing the resource until the endpoint can be remediated and brought back into compliance.

In the third flow, as the user is accessing the resource, Microsoft Purview DLP detects that the user is attempting to send PII to the resource, which is prohibited by policy. Purview DLP blocks this data from being transferred and sends logs to Sentinel.

Use Case in which Azure AD takes action based on log information forwarded by Sentinel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 2* depicts the message flow for the use case in which Azure AD blocks user access based on information forwarded by Sentinel.

**Figure 2 - Use Case E3B3 - Azure Decisions Are Based on Sentinel Log Information**

|Figure2|

The message flow depicted in *Figure 2* consists of the following steps:

1.	An authenticated, authorized user is securely accessing a resource.
2.	Throughout this ongoing access session, all Microsoft defender components (e.g., Defender for Endpoint, Defender for Cloud, Defender for Cloud Apps, Defender for Identity) send in-formation regarding events that are considered suspicious or anomalous to Microsoft Sentinel.
3.	Sentinel, which has been configured with rule-based analytics and automation workflows, de-tects a suspicious user based on observed anomalous activities in conjunction with its config-ured analytics rules. Sentinel acts as the PE and initiates an automated response based on its automation rules. As part of its automated response, Sentinel decides to terminate the user's access and invokes Azure AD to revoke current sessions and terminate further access.
4.	Azure AD executes the decisions made by Sentinel by directing Defender for Cloud Apps to terminate the user's access session, and Azure AD also disables the user's access to resources.

Use Case in which Intune determines that an endpoint is non-compliant and blocks its access to the resource until device posture can be remediated
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the message flow for the case in which Azure AD blocks user access based on device non-compliance information provided by Intune.

**Figure 3 - Use Case E3B3 - A Device that Intune Determines to be Non-Compliant is Temporarily Blocked from Accessing the Resource until It is Remediated and Brought Back Into Compliance**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1.	An authenticated, authorized user is securely accessing a resource.
2.	Throughout this ongoing access session, Intune monitors the endpoint for compliance and sends logs to Microsoft Sentinel. 
3.	Intune detects that the device's posture is no longer compliant, so it alerts Azure AD.
4.	Azure AD directs Defender for Cloud Apps to prevent the user from accessing the resource.
5.	Intune remediates the device posture to bring it into compliance with enterprise policy.
6.	Intune notifies Azure AD that the device is compliant.
7.	Azure AD directs Defender for Cloud Apps to permit the user to access the resource.

Use Case in which Purview DLP blocks the transfer of data that is prohibited from being sent from the enterprise
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 4* depicts a high-level message flow that supports the use case in which Purview DLP blocks a user's attempt to retrieve PII from the resource.

**Figure 4 - Use Case E3B3 - Purview DLP Blocks an Attempt to Retrieve PII from the Resource**

|Figure4|

The message flow depicted in *Figure 4* consists of the following steps:

1.	An authenticated, authorized user is securely accessing a resource.
2.	Throughout this ongoing access session, Purview DLP and Purview Information Protection monitor the information transferred between the endpoint and the resource to provide data security, document protection, and data loss prevention.
3.	Purview DLP detects that the user is attempting to retrieve PII from the resource, which is for-bidden according to enterprise policy.
4.	Purview DLP blocks the data transfer, preventing the user from retrieving the PII from the re-source.
5.	Purview DLP sends a log to Sentinel regarding the DLP action.
6.	Sentinel informs Azure AD regarding the DLP action.


Use Case in which a service/application requests access to a Microsoft Application
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This subsection discusses the steps needed to enable one application/service to access a Microsoft application. Prior to such a service-to-service request, the application or service that will request access to the Microsoft service, also referred to as the *client*, must be registered in the Authorization Server/IdP (which, in this case, is Microsoft Azure AD) and issued a client ID and a client secret. The client's permissions must also be configured.

*Figure 5* depicts the message flow for the use case in which an application/service requests access to a Microsoft Application. Microsoft Azure AD issues access tokens to authenticated users or applications seeking to make API calls to various Microsoft services and applications. In this example Microsoft Graph is the example application to which access is being requested.

*Figure 5 - Use Case E3B3 - Service-to-Microsoft Service Access*

|Figure5|

The message flow depicted in *Figure 5* consists of the following steps:

1.	The client authenticates to Microsoft Azure AD (Conditional Access) and requests an access token to Microsoft Graph with specific scopes (for example: User.Read.All or Files.Read.AsUser).
2.	Microsoft Azure AD (Conditional Access) verifies the client credentials, and that the client is authorized (coarse-grained authorization) to request such scopes from Graph. Azure AD then issues a time-bound access token to the client.
3.	The client calls the Graph API with the access token bearing the specified scopes. 
4.	The Graph API service responds with the appropriate content requested by the client or de-nies the access request if the scopes requested are not permitted.


.. |Figure1| image:: images/AppendixK-Figure1.png
   :alt: This figure depicts the logical architecture of E3B3. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health.
.. |Figure2| image:: images/AppendixK-Figure2.png
   :alt: This figure depicts the message flow for the use case in which Azure AD blocks user access based on information forwarded by Sentinel.
.. |Figure3| image:: images/AppendixK-Figure3.png
   :alt: This figure depicts the message flow for the case in which Azure AD blocks user access based on device non-compliance information provided by Intune.
.. |Figure4| image:: images/AppendixK-Figure4.png
   :alt: This figure depicts a high-level message flow that supports the use case in which Purview DLP blocks a user's attempt to retrieve PII from the resource.
.. |Figure5| image:: images/AppendixK-Figure5.png
   :alt: This is a ladder diagram depicting the message flow for the use case in which an application/service requests access to a Microsoft Application.
