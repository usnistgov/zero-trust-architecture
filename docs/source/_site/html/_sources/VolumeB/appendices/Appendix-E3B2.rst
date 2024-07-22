Enterprise 3 Build 2 (E3B2) - EIG Run - Microsoft Azure AD Conditional Access (later renamed *Entra Conditional Access*), Microsoft Intune, Forescout eyeControl, and Forescout eyeExtend as PEs
====================================================================================================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E3B2 uses products from F5, Forescout, Mandiant, Microsoft, Palo Alto Networks, PC Matic, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E3B2 components consist of F5 BIG-IP, Microsoft AD, Microsoft Azure AD, Microsoft Azure AD (Conditional Access), Microsoft Intune, Microsoft Defender for Endpoint, Microsoft Defender for Cloud Apps, PC Matic Pro, Microsoft Sentinel, Microsoft Azure AD Identity Protection, Tenable.io, Tenable.ad, Tenable NNM, Mandiant Security Validation, Forescout eyeControl, Forescout eyeExtend, Forescout eyeSight, Forescout eyeSegment, Palo Alto Networks NGFW, Microsoft Defender for Cloud, Microsoft Azure (IaaS), Microsoft 365 (SaaS), and DigiCert CertCentral. (Note that after this build was completed, the name *Azure AD* was changed to *Entra ID*. Also, the name Defender for Cloud Apps was changed to Defender for Apps. This appendix uses the original name of *Microsoft Azure AD* and *Microsoft Defender for Cloud Apps*.)

*Table 1* lists all of the technologies used in E3B2 ZTA. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 E3B2 Products and Technologies**

.. csv-table:: E3B2 Products and Technologies
    :file: csv/AppendixH-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E3B2. We also describe E3B2's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E3B2. *Figure 1* uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E3B2. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E3B2 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E3B2 was designed with Microsoft Azure AD (Conditional Access), Microsoft Defender for Cloud Apps, Microsoft Intune, Forescout eyesight, and Forescout eyeExtend as the ZTA PEs and PAs, and Microsoft AD and Azure AD providing ICAM support. It includes six PEPs: Microsoft Azure AD (Conditional Access), Microsoft Defender for Cloud Apps, Microsoft Defender for Endpoint, Microsoft Intune, F5 BIG-IP, and Palo Alto Networks NGFW. A more detailed depiction of the messages that flow among components to support user access requests in the case in which a new endpoint is detected on the network and checked for compliance can be found in :ref:`Message Flows for a Successful Resource Access Request`.

**Figure 1 - Logical Architecture of E3B2**

|Figure1|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 3` describes the physical architecture of the E3B2 network.

.. _AppendixHMessageFlows:

Message Flows for a Successful Resource Access Request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The two message flows for E3B1 that are described in :ref:`E3B1 - Message Flows for a Successful Resource Access Request <AppendixFMessageFlows>` both still apply to E3B2 for cases in which the resource being accessed is located on-premises. Those message flows depict the use cases in which an on-premises resource being accessed is protected by Azure AD alone (see :ref:`Use Case in which Resource Access Is Enforced by Azure AD`), and in which an on-premises resource being accessed is protected by Azure AD in conjunction with the F5 BIG-IP PEP (see :ref:`Use Case in which Resource Access Is Enforced by an F5 BIG-IP PEP`).

This section depicts three additional high-level message flows. The first two new message flows support the use case in which a user who has an enterprise ID and who is authorized to access a cloud-based resource requests and receives access to that resource. The user may be located on-premises or at a remote location, such as a coffee shop. In the first of these two new use cases, the resource accessed is an internal resource. In the second of these new use cases, the resource is externally facing. The third new message flow presented in this section depicts the use case in which a new endpoint is discovered on the network, found to be non-compliant with enterprise policy, and blocked from accessing all resources.

In both of the cloud-based resource access use cases depicted below, all endpoints are enrolled into Microsoft Intune, which is an MDM that can configure and manage devices, and it can also retrieve and report on device security settings that can be used to determine compliance, such as whether the device is running a firewall or anti-malware. Non-Windows devices have an MDM Agent installed on them to enable them to report compliance information to Microsoft Intune, but Windows devices do not require a separate agent because Windows has built-in agents that are designed to communicate with Intune. Intune-enrolled devices check in with Intune periodically, allowing Intune to authenticate the requesting endpoint, determine how the endpoint is configured, modify certain configurations, and collect much of the information it needs to determine whether or not the endpoint is compliant. Intune reports the device compliance information that it collects to Azure AD, which will not permit a device to access any resources unless it meets configured access policies.

One of the criteria that devices must meet to be considered compliant is that they must have anti-virus software updated and running. Some requesting endpoints have Microsoft Defender Antivirus running on them and other requesting endpoints have PC Matic Pro (also antivirus software) running; no endpoints have both turned on. If a device is running Microsoft Defender Antivirus, the Intune MDM can sense this and report it to Azure AD. If a device is running PC Matic Pro, however, the device is configured to notify Windows Security Center that the endpoint has anti-virus software installed, and the Security Center provides this information to Azure AD.

The authentication message flows depicted below show only the messages that are sent in response to the access request. However, the authentication process also relies on the following additional background communications that occur among components on an ongoing basis:

-  Microsoft AD periodically synchronizes with Azure AD to provide it with the most up-to-date identity information.

-  Intune-enrolled devices check in with Intune periodically. Checking in allows Intune to determine how the endpoint is configured and modify certain configurations that have been previously specified. It also allows Intune to report the compliance of the device to Azure AD.

-  Microsoft Defender for Endpoint has both a cloud component and built-in sensors that detect threats on Windows endpoints. So not only can it tell that a firewall is off or antivirus is off, but it can tell when certain malicious signals seen elsewhere have also been observed on the endpoint. It periodically reports this information to its cloud/management component, which uses it for risk determination. This information can be passed off to Intune to include in its compliance determination of an endpoint.

-  Microsoft Defender Antivirus (an endpoint agent) periodically syncs with Microsoft Intune MDM and Microsoft Defender for Endpoint.

-  Microsoft Intune periodically sends device health information to Azure AD so that it can be sure that the device is managed and compliant.

-  PC Matic periodically syncs with Windows Security Center to inform it that the endpoint has anti-virus installed and active.

-  Windows Security Center periodically syncs with Azure AD to provide it with endpoint status information, i.e., that endpoints have anti-virus installed.

Use Case in which Access to a Private Cloud Resource is Enforced by Azure AD and Azure AD's Application Proxy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 2* depicts the message flow for the use case in which Azure AD's Application Proxy acts as the PEP and Azure AD serves as identity manager. In this use case, the resource being accessed is an internal, private resource that does not have a publicly facing IP address and may be located either on-premises at the owning organization or in a private portion of Azure IaaS or another public cloud that the organization controls. Application Proxy includes both the Application Proxy service, which runs in the cloud as part of Azure AD, and the Application Proxy connector, which is a software agent that runs on a server inside the enterprise's network (either on-premises or in the enterprise's private portion of the cloud) and sits in front of the application being protected to manage communication between the Application Proxy service and the application. The Application Proxy connector uses only outbound HTTPS connections, so there is no need for the enterprise to open inbound ports. The connector can also perform “\ `Kerberos Constrained Delegation <https://learn.microsoft.com/en-us/windows-server/security/kerberos/kerberos-constrained-delegation-overview>`__ (KCD)” in the case of enterprise Kerberos apps, which means that the user authenticating to the cloud can get SSO to Kerberos apps on-premises without re-authentication. For KCD to work, the Application Proxy connector would also need to have a path to an enterprise domain controller.

**Figure 2 - Use Case E3B2 - Access to an Internal Resource is Enforced by Azure AD and Azure AD's Application Proxy**

|Figure2|

Prior to the flow above, the administrator configures both the Application Proxy connector and the application. This provides the administrator with an internet-facing URL they can give users who are coming off the internet (by default it would be something like app-contoso.msappprox.net, but they can customize the DNS URL with a SSL certificate). The message flow depicted in *Figure 2* consists of the following steps:

1.  A user requests to access an internal resource in the cloud by typing in the external URL provided by the App Proxy service for that resource. This access request is directed to the Microsoft AD sign-in page.

2.  Azure AD prompts the user for credentials (e.g., username + password, certificate auth, FIDO2 keys).

3.  The user responds with credentials.

4.  If required by policy, Azure AD also prompts the user for second-factor authentication. Azure AD Conditional Access can enforce these additional controls (e.g., MFA, device trust, user risk). Azure AD consults the information about the device that it has received in the background from Microsoft Intune and Defender for Endpoint to authenticate the device and verify that it is managed and meets compliance requirements. If the device has PC Matic running on it, Azure AD also consults information about the device that it has received in the background from Windows Security Center to verify that the device is running anti-virus software.

5.  Azure AD sends an Oauth token to the user's browser to return to the App Proxy service (SAML can also be configured) and redirects the user access request to Azure AD Application Proxy Service.

6.  The endpoint sends the access request and Oauth token to Azure AD Application Proxy Service.

7.  The Application Proxy service retrieves the user principal name and security principal name from the token and sends the request to the Application Proxy connector. If KCD was configured (see above), the Proxy Connector reaches out to the domain controller to acquire a Kerberos ticket on behalf of the user identified in the Oauth token for the intended on-premises resource. Alternatively, the Proxy Connector can be configured to inject authentication headers if the application on-premises requests headers. (This KCD-related step is not depicted in the figure because it was not configured in the NCCoE demonstration.)

8.  The Application Proxy connector sends the request to the resource (optionally with a Kerberos ticket or headers) and the resource grants the user access.

9.  The resource returns content to the Application Proxy connector.

10. The Application Proxy connector tunnels the content to the App Proxy service.

11. The Application Proxy Service serves the content back to the user's end point and browser.

Once the access session is established, all traffic exchanged between the user and the resource flows through the Application Proxy connector.

Use Case in which Access to an Externally Facing Cloud Resource is Enforced by Azure AD and Monitored by Microsoft Defender for Cloud Apps
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the message flow for the case in which access to the resource is protected by Azure AD (with the Conditional Access feature), which acts as a PDP; Microsoft AD, which provides identity information, and Microsoft Defender for Cloud Apps, which monitors cloud resource access sessions for conformance to policy. In this use case, the resource being accessed is externally facing, meaning that it has a publicly reachable IP address. Even though the application is externally facing, because the application is in the part of the cloud that is under the organization's control (i.e., configured for SSO with the organization's Identity Provider through SAML or Oauth), it is still protected by the organization's identity provider, Azure AD, which requires the user to authenticate and then verifies that the user is authorized to access the resource and that the resource is compliant before granting access. Once the access session has been established, Microsoft Defender for Cloud Apps monitors all traffic that is exchanged between the user and the resource (see `here <https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-intro-aad>`__ for a detailed flow explanation). Microsoft Defender for Cloud Apps is therefore able to provide `user behavior analytics <https://en.wikipedia.org/wiki/User_behavior_analytics>`__ functionality and prevent harmful or malicious actions within the resource. For example, it can block download of corporate data onto unmanaged devices, or block upload of data onto cloud storage services that contains PII or credit card numbers.

**Figure 3 - Use Case E3B2 - Access to an Externally-Facing Resource is Enforced by Azure AD and Microsoft Defender for Cloud Apps**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1.  A user requests to access an externally facing, cloud-hosted resource, e.g., a SaaS application that has a publicly reachable IP address. For example, app.saas.com.

2.  The resource sends the authentication request to Azure AD.

3.  Azure AD prompts for credentials.

4.  The user responds with credentials.

5.  Azure AD authenticates the user. Azure AD consults the information about the device that it has received in the background from Microsoft Intune and Defender for Endpoint to authenticate the device and verify that it is managed and meets compliance requirements. If the device has PC Matic running on it, Azure AD also consults information about the device that it has received in the background from Windows Security Center to verify that the device is running anti-virus software.

6.  Azure AD challenges the user to provide the second authentication factor or any other controls.

7.  The user responds with the second authentication factor.

8.  Azure AD sends a SAML assertion token back to the user's browser/endpoint but does not redirect the user to the resource's original redirect URL configured in the SAML setup (e.g., app.saas.com/saml) and instead redirects the user to a uniquely generated URL that is run by Microsoft Defender for Cloud Apps inline proxy (e.g., app.saml.com.cas.com).

9.  The endpoint sends the access request and SAML assertion to Microsoft Defender for Cloud Apps' generated URL.

10. The Microsoft Defender for Cloud Apps inline proxy forwards the request and SAML assertion to the resource's original URL.

11. Microsoft Defender for Cloud Apps receives and parses the response.

12. Before streaming the content back to the user's endpoint, Microsoft Defender for Cloud Apps rewrites any saas.com URLs to be saas.com.cas.com URLs.

The user receives the resulting content from the SaaS app and as they click on any link in the page, they submit their requests back to the Defender for Cloud Apps-generated URL. Defender for Cloud Apps inspects the action and the payload and enforces any DLP or other policies configured. If the action is allowed, Defender for Cloud Apps passes the request on to app.saas.com and, once again, rewrites the URLs of the response before delivery back to the user.

In this manner, for the remainder of the access session, Microsoft Defender for Cloud Apps inline proxy monitors all traffic that is exchanged between the requesting endpoint and the resource endpoint to ensure that is permitted according to enterprise policy. For example, it can inspect the traffic that is sent to and from the cloud for PII or other prohibited content. Microsoft Defender for Cloud Apps inline proxy is integrated with Azure AD Conditional Access, enabling Azure AD to apply its controls to Microsoft Defender for Cloud Apps-governed applications. Furthermore, Defender for Cloud Apps can discover users and endpoints accessing resources, understand and report the risk posture of resources, and identify malicious activity either targeting or sourced from resources, as well as apply DLP policies that mitigate the risk of malicious data exfiltration.

Use Case in which a Non-Compliant Endpoint is Discovered on the Network and Blocked from Accessing Resources
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 4* depicts a high-level message flow that supports the use case in which Forescout discovers a non-compliant endpoint on the network and directs the Palo Alto Networks NGFW to block traffic to and from that device.

**Figure 4 - Use Case E3B2 - Forescout Discovers a Non-Compliant Endpoint on the Network and Directs the Palo Alto Networks Firewall to Block it**

|Figure4|

The message flow depicted in *Figure 4* depicts a high-level message flow that supports the use case in which Forescout discovers a non-compliant endpoint on the network and directs the Palo Alto Networks NGFW to block traffic to and from that device.

*Figure 4* consists of the following steps:

1. Forescout discovers a new endpoint on the network.

2. Forescout determines what other resources the endpoint is communicating with and then determines whether or not the endpoint is conformant with policy. (In this use case example, the endpoint is found to be non-conformant.)

3. Forescout direct the Palo Alto Networks NGFW to block traffic to and from this device.

4. When the endpoint attempts to access a resource that is beyond the NGFW, the NGFW blocks the endpoint's traffic.

.. |Figure1| image:: images/AppendixH-Figure1.png
   :alt: This figure depicts the logical architecture of E3B2. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity, authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health. 
.. |Figure2| image:: images/AppendixH-Figure2.png
   :alt: This figure depicts the message flow for the use case in which Azure AD's Application Proxy acts as the PEP and Azure AD serves as identity manager. 
.. |Figure3| image:: images/AppendixH-Figure3.png
   :alt: This figure depicts the message flow for the case in which access to the resource is protected by Azure AD, which acts as a PDP; Microsoft AD, which provides identity information, and Microsoft Defender for Cloud Apps, which monitors cloud resource access sessions for conformance to policy. 
.. |Figure4| image:: images/AppendixH-Figure4.png
   :alt: This figure depicts a high-level message flow that supports the use case in which Forescout discovers a non-compliant endpoint on the network and directs the Palo Alto NGFW to block traffic to and from that device. 
