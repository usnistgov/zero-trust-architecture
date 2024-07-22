Enterprise 3 Build 1 (E3B1) - EIG Crawl - Azure AD Conditional Access (later renamed *Entra Conditional Access*) as PE
=========================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E3B1 uses products from F5, Forescout, Lookout, Mandiant, Microsoft, Palo Alto Networks, PC Matic, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E3B1 components consist of Microsoft Azure AD, Microsoft AD, F5 BIG-IP, Microsoft Intune, Microsoft Defender for Endpoint, Lookout MES, PC Matic Pro, Microsoft Sentinel, Tenable.io, Tenable.ad, Mandiant Security Validation, Forescout eyeSight, Palo Alto Networks NGFW, and DigiCert CertCentral. (Note that after this build was completed, the name *Azure AD* was changed to *Entra ID*. This appendix uses the original name of *Microsoft Azure AD*.)

Table 1 lists all of the technologies used in E3B1 ZTA. It lists the products used to instantiate each ZTA component and the security function that the component provides.

*Table 1 - E3B1 Products and Technologies*

.. csv-table:: E3B1 Products and Technologies
    :file: csv/AppendixF-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E3B1 relative to how it instantiates the crawl phase EIG reference architecture depicted in :ref:`Architecture - Figure 2<ArchitectureFigure2>`. We also describe E3B1's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

:ref:`Figure 1<Appendix-E3B1-Figure1>` depicts the logical architecture of E3B1. :ref:`Figure 1<Appendix-E3B1-Figure1>` uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>` and :ref:`Architecture - Figure 2<ArchitectureFigure2>`. However, while :ref:`Architecture - Figure 2<ArchitectureFigure2>` depicts generic crawl phase ZTA components, *Figure 1* includes the specific products that instantiate the architecture of E3B1. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` and :ref:`Architecture - Figure 2<ArchitectureFigure2>` because the ZTA technologies deployed in E3B1 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E3B1 was designed with a single ICAM system (Microsoft Azure AD) that serves as identity, access, and credential manager and also serves as the ZTA PE and PA. Microsoft Intune also serves as the ZTA PE and PA. It includes five PEPs: Microsoft Azure AD, Microsoft Defender for Endpoint, Microsoft Intune, F5 BIG-IP, and Lookout MES. A more detailed depiction of the messages that flow among components to support user access requests in the two different cases when the resource is being protected by the Azure AD PEP versus the F5 BIG-IP PEP can be found in :ref:`Use Case in which Resource Access Is Enforced by Azure AD` and :ref:`Use Case in which Resource Access Is Enforced by an F5 BIG-IP PEP`.

**Figure 1 - Logical Architecture of E3B1**

|Figure1|

.. _Appendix-E3B1-Figure1:

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 3` describes the physical architecture of the E3B1 network.

.. _AppendixFMessageFlows:

Message Flows for a Successful Resource Access Request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This section depicts two high-level message flows, both of which support the use case in which a subject who has an enterprise ID, is located on-premises, and is authorized to access an enterprise resource, requests and receives access to that resource.

The two message flows that are supported by Enterprise 3 for this use case depend on whether the resource being accessed is protected by Azure AD alone (see :ref:`Use Case in which Resource Access Is Enforced by Azure AD`) or by Azure AD in conjunction with the F5 BIG-IP PEP (see :ref:`Use Case in which Resource Access Is Enforced by an F5 BIG-IP PEP`).

Regardless of which components are being used to protect the resource, all endpoints are enrolled into Microsoft Intune, which is an MDM (and a UEM) that can configure and manage devices and can also retrieve and report on device security settings that can be used to determine compliance, such as whether the device is running a firewall or anti-malware. Non-Windows devices have an MDM agent installed on them to enable them to report compliance information to Microsoft Intune, but Windows devices do not require a separate agent because Windows has built-in agents that are designed to communicate with Intune. Intune-enrolled devices check in with Intune periodically, allowing it to authenticate the requesting endpoint, determine how the endpoint is configured, modify certain configurations, and collect much of the information it needs to determine whether the endpoint is compliant. Intune reports the device compliance information that it collects to Azure AD, which will not permit a device to access any resources unless it is compliant.

For demonstration purposes, one of the criteria that devices are expected to meet to be considered compliant in our example implementation is that they must have antivirus software updated and running. In both scenarios below, some requesting endpoints have Microsoft Defender Antivirus running on them and other requesting endpoints have PC Matic Pro (also antivirus software) running; no endpoints have both turned on. If a device is running Microsoft Defender Antivirus, the Intune MDM can sense this and report it to Azure AD. If a device is running PC Matic Pro, however, the device is configured to notify Windows Security Center that the endpoint has antivirus software installed, and the Security Center provides this information to Azure AD.

The authentication message flows depicted below show only the messages that are sent in response to the access request. However, the authentication process also relies on the following additional background communications that occur among components on an ongoing basis:

-  Microsoft AD periodically synchronizes with Azure AD to provide it with the most up-to-date identity information.

-  Intune-enrolled devices check in with Intune periodically. Checking in allows Intune to determine how the endpoint is configured and modify certain configurations that have been previously specified. It also allows Intune to report the compliance of the device to Azure AD.

-  Microsoft Defender for Endpoint has both a cloud component and built-in sensors that detect threat signals from Windows endpoints. So not only can it tell that a firewall is disabled or antivirus is off, but it can tell when certain malicious signals seen elsewhere have also been observed on your endpoint. It periodically reports this information to its cloud/management component, which uses it for risk determination. This information can be passed off to Intune to include in its compliance determination of an endpoint.

-  Microsoft Defender Antivirus (an endpoint agent) periodically syncs with Microsoft Intune and Microsoft Defender for Endpoint.

-  Microsoft Intune periodically sends device health information to Azure AD so that it can be sure that the device is managed and compliant.

-  PC Matic periodically syncs with Windows Security Center to inform it that that the endpoint has antivirus installed and active.

-  Windows Security Center periodically syncs with Azure AD to provide it with endpoint status information, e.g., that endpoints have antivirus installed.

Use Case in which Resource Access Is Enforced by Azure AD
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 2* depicts the message flow for the case in which access to the resource is protected by Azure AD (with the Conditional Access feature), which acts as a PDP; and Microsoft AD, which provides identity information.

**Figure 2 - Use Case E3B1 - Access Enforced by Azure AD**

|Figure2|

The message flow depicted in *Figure 2* consists of the following steps:

1. A user requests access to a resource.

2. The resource sends the authentication request to Azure AD.

3. Azure AD prompts for username and password.

4. The user responds with username and password.

5. Azure AD authenticates the user. Azure AD consults the information about the device that it has received in the background from Microsoft Intune and Defender for Endpoint to authenticate the device and verify that it is managed and meets compliance requirements. If the device has PC Matic running on it, Azure AD also consults information about the device that it has received in the background from Windows Security Center to verify that the device is running antivirus software.

6. Azure AD challenges the user to provide the second authentication factor.

7. The user responds with the second authentication factor.

8. Azure AD sends a SAML assertion to the resource.

9. The resource accepts the assertion and grants the access request. User traffic to and from the resource is secured according to policy (e.g., using TLS or HTTPS).

Use Case in which Resource Access Is Enforced by an F5 BIG-IP PEP
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the message flow for the case in which access to the resource is protected by F5 BIG-IP, which acts as an identity-aware proxy PEP; Microsoft Azure AD, which acts as an ICAM provider and PDP; and Microsoft AD, which provides identity information.

**Figure 3 - Use Case E3B1 - Access Enforced by F5 BIG-IP**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1. A user requests access to a resource.

2.  BIG-IP, which is acting as an identity-aware proxy PEP that sits in front of the resource, intercepts and forwards the request to Azure AD.

3. Azure AD prompts for username and password.

4. The user responds with username and password.

5. Azure AD authenticates the user. Azure AD consults the information about the device that it has received in the background from Microsoft Intune and Defender for Endpoint to authenticate the device and verify that it is managed and meets compliance requirements. If the device has PC Matic running on it, Azure AD also consults information about the device that it has received in the background from Windows Security Center to verify that the device is running antivirus software.

6. Azure AD challenges the user to provide the second authentication factor.

7. The user responds with the second authentication factor.

8. Azure AD sends a SAML assertion to BIG-IP which serves as an identity-aware proxy, service provider, and the PEP protecting the resource.

9. BIG-IP accepts the SAML assertion and permits the access request to proceed to the resource. User traffic to and from the resource is secured according to policy (e.g., using TLS or HTTPS).

.. |Figure1| image:: images/AppendixF-Figure1.png
   :alt: This figure depicts the logical architecture of E3B1. It uses numbered arrows to depict message flows.
.. |Figure2| image:: images/AppendixF-Figure2.png
   :alt: This figure depicts the message flow for the case in which access to the resource is protected by Azure AD, which acts as a PDP; and Microsoft AD, which provides identity information.
.. |Figure3| image:: images/AppendixF-Figure3.png
   :alt: This figure depicts the message flow for the case in which access to the resource is protected by F5 BIG-IP, which acts as an identity-aware proxy PEP; Microsoft Azure AD, which acts as an ICAM provider and PDP; and Microsoft AD, which provides identity information.
