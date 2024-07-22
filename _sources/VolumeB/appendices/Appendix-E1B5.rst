Enterprise 1 Build 5 (E1B5) - SASE and Microsegmentation - PAN NGFW and PAN Prisma Access as PEs
================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E1B5 uses products from AWS, IBM, Mandiant, Okta, Palo Alto Networks (PAN), Radiant Logic, SailPoint, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E1B5 components consist of PAN Panorama, PAN Next Generation Firewall (NGFW), PAN Prisma Access, PAN Prisma SASE (Prisma Access & Prisma SD-WAN), PAN Cloud-Delivered Security Services (CDSS), PAN Cloud Identity Engine (CIE), PAN Global Protect, PAN Strata Cloud Manager, Okta Identity Cloud, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Okta Verify App, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable NNM, Mandiant Security Validation, DigiCert CertCentral, and AWS IaaS.

*Table 1* lists all of the technologies used in Build E1B5. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E1B5 Products and Technologies**

.. csv-table:: E1B5 Products and Technologies
    :file: csv/AppendixQ-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E1B5. We also describe E1B5's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E1B5. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E1B5. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E1B5 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E1B5 was designed with Palo Alto Networks components that serve as PEs, PAs, and PEPs, and Okta Identity Cloud that serves as identity, access, and credential manager. PAN Cloud Identity Engine is used to connect and integrate Okta Identity Cloud with PAN products such as the NGFW and Panorama. Radiant Logic acts as a PIP for the PDP as it responds to inquiries and provides identity information on demand in order for Okta and PAN to make near-real-time access decisions. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flows for Successful Resource Access Requests<Appendix-E1B5-MessageFlows>`.

**Figure 1 - Logical Architecture of E1B5**

|Figure1|

ICAM Information Architecture
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How ICAM information is provisioned, distributed, updated, shared, correlated, governed, and used among ZTA components is fundamental to the operation of the ZTA. The ICAM information architecture ensures that when a subject requests access to a resource, the aggregated set of identity information and attributes necessary to identify, authenticate, and authorize the subject is available to be used as a basis on which to make the access decision.

In E1B5, Okta, Radiant Logic, and SailPoint integrate with each other as well as with other components of the ZTA to support the ICAM information architecture. The ways that these components work together to correlate identity information and to support actions such as users joining, changing roles, and leaving the enterprise are the same in E1B5 as they are in E1B1, E1B2, E1B3, and E1B4. These interactions are described in :ref:`E1B1 - ICAM Information Architecture <E1B1ICAM>`.

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 1` and :ref:`Enterprise 1 Branch Office` describe and depict the physical architecture of the E1B5 headquarters network and E1B5 branch office network, respectively.

Message Flows for Successful Resource Access Requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _Appendix-E1B5-MessageFlows:

This section depicts several authentication message flows supported by E1B5. Resource access is protected by PAN components, which act as PDPs and PEPs. Okta acts as the identity provider for this build, and PAN Prisma Access and PAN NGFWs integrate with Okta via the PAN Cloud Identity Engine, which acts like an ICAM proxy for Prisma Access and NGFW. Five flows are depicted.

Message Flow for Remote User Access to Enterprise Resources that Are Either On-Premises or In the Cloud (PAN Prisma Access, PAN Global Protect, PAN Cloud Identity Engine, PAN NGFW) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 2* depicts the high-level message flow supporting the use case in which a remote user (i.e., a user who is not located on-premises or at a branch office) who has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource, requests and receives access to that resource. The resource may be located either on-premises or in the cloud. Access to the resource is authenticated and authorized by the following components working together:

-  PAN Global Protect Agent running on the user's endpoint, which collects cybersecurity and other information about the endpoint such as firewall status, OS, antivirus, etc. and submits it as a host information profile (HIP) to a PAN PDP such as Prisma Access or NGFW. The PDP uses the PDP to perform endpoint compliance checks. The Global Protect Agent connects to a Global Protect Gateway that is running on a PAN PEP and submits access requests to it.

-  Okta, which acts as IdP and has a directory and SAML integration with PAN Cloud Identity Engine.

-  PAN Prisma Access, which acts as both PDP and PEP, and includes a mobile user security processing node (MU SPN), a service connection security processing node (SC SPN), and a Global Protect Gateway.

-  PAN NGFW, which acts as both PDP and PEP. If the resource is located on-premises, the NGFW controlling access is the enterprise NGFW that is on-premises guarding the resource; if the resource is located in the cloud, the NGFW controlling access is a VM-series NGFW in the cloud. The NGFW includes a Global Protect Gateway (not shown).

**Figure 2 - Use Case E1B5 - Remote User Authentication and Access Enforcement Using PAN Prisma Access, PAN Global Protect, and PAN NGFW**

|Figure2|

The message flow depicted in *Figure 2* consists of the following steps:

1.	The PAN Global Protect Agent on the user's device tries to connect to the portal. Because the user is remote (i.e., not located on-premises or at a branch office), this connection attempt is received at the MU SPN component of PAN Prisma Access.
2.	The MU SPN component of Prisma Access redirects the Global Protect Agent to the PAN Cloud Identity Engine (CIE) for authentication. 
3.	The Global Protect Agent directs the user's endpoint to contact PAN CIE for authentication in a web browser.
4.	PAN CIE determines that Okta is the IdP based on the authentication profile and redirects the user to Okta.
5.	Okta challenges the user for both first- and second-factor authentication and the user re-sponds by providing their first- and second-factor credentials.
6.	Assuming the user provided the correct credentials, Okta sends an authentication token to the endpoint. The MU SPN component of PAN Prisma Access learns the user's IP address as traffic passes through it.
7.	The Global Protect Agent connects to the best/closest Global Protect Gateway, based on user location and latency. The Global Protect Agent authenticates to this gateway by providing the authentication token. 
8.	The Global Protect Agent also submits the HIP to the Prisma Access PEP. 
9.	The user sends a request to access the enterprise resource on the connection to the Prisma Access PEP. (The resource may be located either on-premises or in an enterprise data center that is hosted in the cloud.) 
10.	Prisma Access looks up the security policy and the device HIP profile, inspects the traffic, and forwards the traffic, assuming the endpoint is compliant and access is permitted by policy.
11.	The SC SPN component of Prisma Access forwards the traffic using an IPsec tunnel that termi-nates at the PAN NGFW that is guarding the resource. If the resource is on-premises, the ser-vice connection IPsec tunnel will terminate at an on-premises enterprise NGFW. If the re-source is in the cloud, the service connection IPsec tunnel will terminate at a VM-series NGFW that is deployed in the cloud.
12.	The NGFW looks up security policy, inspects the traffic, and forwards the traffic to the re-source, if allowed.


Message Flow for A User Who Is Located at a Branch Office to Access an Enterprise Resource On-Premises at Another Enterprise Site or In the Cloud (PAN Prisma Access, PAN Global Protect, PAN Cloud Identity Engine, PAN NGFW) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the high-level message flow supporting the use case in which a user who is located at a branch office, who has an enterprise ID, is using a compliant device, and is authorized to access an on-premises enterprise resource, requests and receives access to that resource. The resource may be located either on-premises at another enterprise site or in the cloud. Access to the resource is authenticated and authorized by the following components working together:

-  PAN Global Protect Agent running on the user's endpoint, which collects cybersecurity and other information about the endpoint such as firewall status, OS, antivirus, etc. and submits it as a host information profile (HIP) to a PAN PDP such as Prisma Access or NGFW. The PDP uses the PDP to perform endpoint compliance checks. The Global Protect Agent connects to a Global Protect Gateway that is running on a PAN PEP and submits access requests to it.

-  Okta, which acts as IdP and has a directory and SAML integration with PAN Cloud Identity Engine.

-  PAN Prisma Access, which acts as both PDP and PEP, and includes a remote network security processing node (RN SPN), a service connection security processing node (SC SPN), and a Global Protect Gateway.

-  Two PAN NGFWs, which act as both PDPs and PEPs: an NGFW located at the branch office where the user is located, and an NGFW that is guarding the resource. If the resource is located on premises, the NGFW controlling access is the enterprise NGFW that is on-premises guarding the resource; if the resource is located in the cloud, the NGFW controlling access is a VM-series NGFW in the cloud. Each NGFW includes a Global Protect Gateway (not shown).

**Figure 3 - Use Case E1B5 - User Located in a Branch Office Authentication and Access Enforcement to an On-Premises Enterprise Resource Using PAN Prisma Access, PAN Global Protect, and PAN NGFW**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1.	The PAN Global Protect Agent on the user's device tries to connect to the portal. Because the user is located at a Branch Office, this connection attempt is received at the Branch NGFW.
2.	The Branch NGFW redirects the Global Protect Agent to the PAN Cloud Identity Engine (CIE) for authentication. 
3.	The Global Protect Agent directs the user's endpoint to contact PAN CIE for authentication in a web browser.
4.	PAN CIE determines that Okta is the IdP based on the authentication profile and redirects the user to Okta.
5.	Okta challenges the user for both first- and second-factor authentication. and the user re-sponds by providing their first- and second-factor credentials.
6.	Assuming the user provided the correct credentials, Okta sends an authentication token to the endpoint. The Branch NGFW learns the user's IP address as traffic passes through it.
7.	The Global Protect Agent connects to the internal Global Protect Gateway within the Branch NGFW once internal host detection is resolved, demonstrating that the endpoint is physically present at the site. The Global Protect Agent authenticates to the internal gateway by provid-ing the authentication token.
8.	The Global Protect Agent also submits the HIP to the Global Protect Gateway that is on the Branch NGFW PEP. 
9.	The user sends a request to access the enterprise resource that is located on-premises at an-other site (headquarters or another branch office) on the connection to the Branch NGFW. 
10.	The Branch NGFW looks up the security policy and the device HIP profile, inspects the traffic, and forwards the traffic to the RN SPN component of Prisma Access, assuming the endpoint is compliant and access is permitted by policy.
11.	The RN SPN component of Prisma Access performs policy enforcement, traffic inspection, and routing of the request as it forwards the request to the SC SPN component of Prisma Access.
12.	The SC SPN component of Prisma Access forwards the traffic using an IPsec tunnel that termi-nates at the enterprise PAN NGFW guarding the resource. If the resource is on-premises, the service connection IPsec tunnel will terminate at an on-premises enterprise NGFW. If the re-source is in the cloud, the service connection IPsec tunnel will terminate at a VM-series NGFW that is deployed in the cloud.
13.	The NGFW that is guarding the resource looks up security policy, inspects the traffic, and for-wards the traffic to the resource, if allowed.

Message Flow for A User Who Is On-Premises at Enterprise Headquarters to Access an Enterprise Resource Located at a Data Center Hosted in the Cloud (PAN Prisma Access, PAN Global Protect, PAN Cloud Identity Engine, PAN on premise and cloud NGFWs) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 4* depicts the high-level message flow supporting the use case in which a user who is located on-premises at headquarters, has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource that is in a data center hosted in the cloud, requests and receives access to that resource. Access to the resource is authenticated and authorized by the following components working together:

-  PAN Global Protect Agent running on the user's endpoint, which collects cybersecurity and other information about the endpoint such as firewall status, OS, antivirus, etc. and submits it as a host information profile (HIP) to a PAN PDP such as Prisma Access or NGFW. The PDP uses the PDP to perform endpoint compliance checks. The Global Protect Agent connects to a Global Protect Gateway that is running on a PAN PEP and submits access requests to it.

-  Okta, which acts as IdP and has a directory and SAML integration with PAN Cloud Identity Engine.

-  PAN Prisma Access, which acts as both PDP and PEP, and includes multiple instantiations of service connection security processing nodes (SC SPNs) and a Global Protect Gateway.

-  Two PAN NGFWs, which act as both PDPs and PEPs: a NGFW located on-premises at headquarters where the user is located, and a VM-series NGFW in the cloud where the resource is located. Each NGFW includes a Global Protect Gateway (not shown).

**Figure 4 - Use Case E1B5 - User Located On-Premises at Headquarters Authentication and Access Enforcement to a Resource in the Cloud Using PAN Prisma Access, PAN Global Protect, and PAN NGFW**

|Figure4|

The message flow depicted in *Figure 4* consists of the following steps:

1.	The PAN Global Protect Agent on the user's device tries to connect to the portal. Because the user is located at the enterprise headquarters, this connection attempt is received at the on-premises Enterprise NGFW.
2.	The Enterprise NGFW redirects the Global Protect Agent to the PAN Cloud Identity Engine (CIE) for authentication. 
3.	The Global Protect Agent directs the user's endpoint to contact PAN CIE for authentication in a web browser.
4.	PAN CIE determines that Okta is the IdP based on the authentication profile and redirects the user to Okta.
5.	Okta challenges the user for both first- and second-factor authentication, and the user re-sponds by providing their first- and second-factor credentials.
6.	Assuming the user provided the correct credentials, Okta sends an authentication token to the endpoint. The Enterprise NGFW learns the user's IP address as traffic passes through it.
7.	The Global Protect Agent connects to the internal Global Protect Gateway within the Enter-prise NGFW once internal host detection is resolved, demonstrating that the endpoint is phys-ically present at the site. The Global Protect Agent authenticates to the internal gateway by providing the authentication token.
8.	The Global Protect Agent also submits the HIP profile to the Global Protect Gateway that is on the on-premises PAN NGFW PEP. 
9.	The user sends a request to access the enterprise resource that is located in the cloud on the connection to the Enterprise NGFW. 
10.	The Enterprise NGFW looks up the security policy and the device HIP profile, inspects the traf-fic, and forwards the traffic to the SC SPN component of Prisma Access, assuming the endpoint is compliant and access is permitted by policy.
11.	Traffic is routed from between service connections set up by the SC SPN component of Prisma Access.
12.	An SC SPN component of Prisma Access forwards the traffic using an IPsec tunnel that termi-nates at an NGFW NVF that is in the cloud guarding the resource.
13.	The NGFW looks up security policy, inspects the traffic, and forwards the traffic to the re-source, if allowed.

Message Flow for A User Located On-Premises to Access an Enterprise Resource Also Located On-Premises (PAN Prisma Access, PAN Global Protect, PAN Cloud Identity Engine, PAN NGFW) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 5* depicts the high-level message flow supporting the use case in which a user who is located on-premises at headquarters, has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource that is also located on-premises at headquarters, requests and receives access to that resource. Access to the resource is authenticated and authorized by the following components working together:

-  PAN Global Protect Agent running on the user's endpoint, which collects cybersecurity and other information about the endpoint such as firewall status, OS, antivirus, etc. and submits it as a host information profile (HIP) to a PAN PDP such as Prisma Access or NGFW. The PDP uses the PDP to perform endpoint compliance checks. The Global Protect Agent connects to a Global Protect Gateway that is running on a PAN PEP and submits access requests to it.

-  Okta, which acts as IdP and has a directory and SAML integration with PAN Cloud Identity Engine.

-  PAN NGFW, which acts as both PDP and PEP, and is located on-premises at enterprise headquarters where both the user and the resource are located. The NGFW includes a Global Protect Gateway (not shown).

**Figure 5 - Use Case—E1B5 - User Located On-Premises at Enterprise Authentication and Access Enforcement to a Resource Located Internally On-Premises Using PAN Global Protect and PAN NGFW**

|Figure5|

The message flow depicted in *Figure 5* consists of the following steps:

1.	The PAN Global Protect Agent on the user's device tries to connect to the portal. Because the user is located on-premises at the enterprise, this connection attempt is received at the inter-nal, on-premises Enterprise NGFW.
2.	The Enterprise NGFW redirects the Global Protect Agent to the PAN Cloud Identity Engine (CIE) for authentication. 
3.	The Global Protect Agent directs the user's endpoint to contact PAN CIE for authentication in a web browser.
4.	PAN CIE determines that Okta is the IdP based on the authentication profile and redirects the user to Okta.
5.	Okta challenges the user for both first- and second-factor authentication, and the user re-sponds by providing their first- and second-factor credentials.
6.	Assuming the user provided the correct credentials, Okta sends an authentication token to the endpoint. The Enterprise NGFW learns the user's IP address as traffic passes through it.
7.	The Global Protect Agent connects to the internal Global Protect Gateway within the internal Enterprise NGFW once internal host detection is resolved, demonstrating that the endpoint is physically present at the site. The Global Protect Agent authenticates to the internal gateway by providing the authentication token.
8.	The Global Protect Agent also submits the HIP profile to the Global Protect Gateway that is on the Enterprise NGFW. 
9.	The user sends a request to access the internal, on-premises enterprise resource on the con-nection to the Enterprise NGFW. 
10.	The Enterprise NGFW looks up the security policy and the device HIP profile, inspects the traf-fic, and forwards the traffic to the resource, assuming the endpoint is compliant and access is permitted by policy.

Message Flow for A Branch Office User to Access an Enterprise Resource Located On-Premises at the Enterprise Headquarters Using SD-WAN (PAN Prisma Access, PAN Prisma SD-WAN, PAN Global Protect, PAN Cloud Identity Engine, PAN NGFW) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 6* depicts the high-level message flow supporting the use case in which a user who is located at a branch office, has an enterprise ID, is using a compliant device, and is authorized to access a resource on the on-premises enterprise network at headquarters, requests and receives access to that resource over a path selected using SD-WAN. Access to the resource is authenticated and authorized by the following components working together:

-  PAN Global Protect Agent running on the user's endpoint, which collects cybersecurity and other information about the endpoint such as firewall status, OS, antivirus, etc. and submits it as a host information profile (HIP) to a PAN PDP such as Prisma Access or NGFW. The PDP uses the PDP to perform endpoint compliance checks. The Global Protect Agent connects to a Global Protect Gateway that is running on a PAN PEP and submits access requests to it.

-  Okta, which acts as IdP and has a directory and SAML integration with PAN Cloud Identity Engine.

-  PAN Prisma Access, which acts as both PDP and PEP, and includes a remote network security processing node (RN SPN), a Mobile User Portal, a service connection security processing node (SC SPN), and a Global Protect Gateway.

-  A PAN NGFW, which acts as both PDP and PEP, located on-premises on the enterprise network at the headquarters where the resource is located. The NGFW includes a Global Protect Gateway (not shown).

-  PAN Prisma Access SD-WAN, which acts as a router and supports efficient transport of traffic between the branch office and the main headquarters.

**Figure 6 - Use Case E1B5 - User Located in a Branch Office Authentication and Access Enforcement to an On-Premises Enterprise Resource Using PAN Prisma SD-WAN, as well as PAN Prisma Access, PAN Global Protect, and PAN NGFW**

|Figure6|

The message flow depicted in *Figure 6* consists of the following steps:

1.	The PAN Global Protect Agent on the user's device tries to connect to the portal. Because the user is located at a Branch Office, this connection attempt is received at Prisma Access.
2.	Prisma Access redirects the Global Protect Agent to the PAN Cloud Identity Engine (CIE) for authentication. 
3.	The Global Protect Agent directs the user's endpoint to contact PAN CIE for authentication in a web browser.
4.	PAN CIE determines that Okta is the IdP based on the authentication profile and redirects the user to Okta.
5.	Okta challenges the user for both first- and second-factor authentication, and the user re-sponds by providing their first- and second-factor credentials.
6.	Assuming the user provided the correct credentials, Okta sends an authentication token to the endpoint. The MU SPN component of Prisma Access learns the user's IP address as traffic passes through it.
7.	The Global Protect Agent connects to the internal Global Protect gateway within Prisma Access once internal host detection is resolved, demonstrating that the endpoint is physically present at the Branch Office site. The Global Protect Agent authenticates to the internal gateway by providing the authentication token.
8.	The Global Protect Agent also submits the HIP profile to the Prisma Access PEP.
9.	The user, who is located in the Branch Office, sends the Prisma SD-WAN a request to access a resource that is on the enterprise network. 
10.	Prisma SD-WAN looks up the security policy and the device HIP profile, inspects the traffic, chooses the best path (based on link quality) and forwards the traffic to Prisma Access via an IPsec tunnel, assuming the endpoint is compliant and access is permitted by policy.
11.	The RN SPN component of Prisma Access performs policy enforcement, traffic inspection, and routing of the request as it forwards the request to the SC SPN component of Prisma Access.
12.	The SC SPN component of Prisma Access forwards the traffic using an IPsec tunnel that termi-nates at the enterprise PAN NGFW that is on-premises, local to, and guarding the resource.
13.	The Enterprise NGFW looks up security policy, inspects the traffic, and forwards the traffic to the resource, if allowed.


.. |Figure1| image:: images/AppendixQ-Figure1.png
   :alt: This figure depicts the logical architecture of E1B5. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health.
.. |Figure2| image:: images/AppendixQ-Figure2.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a remote user (i.e., a user who is not located on-premises or at a branch office) who has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource, requests and receives access to that resource.
.. |Figure3| image:: images/AppendixQ-Figure3.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a user who is located at a branch office, who has an enterprise ID, is using a compliant device, and is authorized to access an on-premises enterprise resource, requests and receives access to that resource.
.. |Figure4| image:: images/AppendixQ-Figure4.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a user who is located on-premises at headquarters, has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource that is in a data center hosted in the cloud, requests and receives access to that resource.
.. |Figure5| image:: images/AppendixQ-Figure5.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a user who is located on-premises at headquarters, has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource that is also located on-premises at headquarters, requests and receives access to that resource.
.. |Figure6| image:: images/AppendixQ-Figure6.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a user who is located at a branch office, has an enterprise ID, is using a compliant device, and is authorized to access a resource on the on-premises enterprise network at headquarters, requests and receives access to that resource over a path selected using SD-WAN.
