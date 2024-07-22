Enterprise 3 Build 4 (E3B4) - SDP - F5 BIG-IP, F5 NGINX Plus, Forescout eyeControl, and Forescout eyeExtend as PEs 
===================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E3B4 uses products from F5, Forescout, Mandiant, Microsoft, Palo Alto Networks, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E3B4 components consist of F5 BIG-IP, F5 NGINX Plus, F5 Access App, F5 Edge Client, Microsoft AD, Microsoft Azure AD, Microsoft Azure AD Identity Governance, Microsoft Intune, Microsoft Sentinel, Tenable.io, Tenable.ad, Tenable NNM, Mandiant Security Validation, Forescout eyeControl, Forescout eyeExtend, Forescout eyeSight, Forescout eyeSegment, Microsoft Azure (IaaS), and DigiCert CertCentral. (Note that after this build was completed, the name *Azure AD* was changed to *Entra ID*. This appendix uses the original name of *Microsoft Azure AD*.)

*Table 1* lists all of the technologies used in Build E3B4. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E3B4 Products and Technologies**

.. csv-table:: E3B4 Products and Technologies
    :file: csv/AppendixO-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E3B4. We also describe E3B4's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E3B4. *Figure 1* uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E3B4. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E3B4 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E3B4 was designed with F5 BIG-IP, F5 NGINX Plus, Forescout eyeControl, and Forescout eyeExtend as its PEs and PAs. F5 BIG-IP, F5 NGINX Plus, and PAN NGFW serve as PEPs, and Microsoft AD and Azure AD provide ICAM support. To manage service-to-service access for containers, NGINX Plus enforces access to microservices. A more detailed depiction of the messages that flow among components to support user access requests can be found in :ref:`Message Flows for Successful Resource Access Requests<Appendix-E3B4-MessageFlows>`.

**Figure 1 - Logical Architecture of E3B4**

|Figure1|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 3` describes the physical architecture of the E3B4 network.

Message Flows for a Successful Resource Access Request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _Appendix-E3B4-MessageFlows:

This section depicts high-level message flows for E3B4. Resource access is protected by F5 technology such as BIG-IP and NGINX Plus, which act as PDPs and PEPs. Microsoft Azure AD serves as the identity provider for the build, and Microsoft Intune and F5 Access App support endpoint protection by providing device compliance information to the F5 PDP.

*Authentication* Message Flow for Access to an Enterprise Resource (F5 BIG-IP, Microsoft Azure AD, Microsoft Intune, and F5 Access App) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 2* depicts the high-level message flow supporting the use case in which a subject who has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource, requests and receives access to that resource. In the case depicted here, access to the resource is authenticated and authorized by F5 BIG-IP, which acts as both PDP and PEP. All endpoints are enrolled into Microsoft Intune, which is an MDM (and a UEM) that can configure and manage devices and can also retrieve and report on device security settings that can be used to determine compliance, such as whether the device is running a firewall or anti-malware. Non-Windows devices have the F5 Access App installed on them as an MDM agent to enable them to report compliance information to Microsoft Intune, but Windows devices do not require a separate agent because Windows has built-in agents that are designed to communicate with Intune. Intune-enrolled devices check in with Intune periodically, allowing Intune to authenticate the requesting endpoint, determine how the endpoint is configured, modify certain configurations, and collect much of the information it needs to determine whether the endpoint is compliant. The F5 Access App provides unique device details to BIG-IP that enables BIG-IP to query Intune for device compliance. In addition, the F5 Access App also provides its own compliance information about each device to BIG-IP. F5 BIG-IP will not permit a device to access any resources unless it is compliant.

**Figure 2 - Use Case E3B4 - User Authentication and Access Enforcement Using F5 BIG-IP, Microsoft Intune, F5 Access App, and Microsoft Azure AD**

|Figure2|

The message flow depicted in *Figure 2* consists of the following steps:

1.	A user requests access to a resource.
2.	F5 BIG-IP intercepts this request and determines whether or not the requesting endpoint is compliant by querying both the F5 Access App and Microsoft Intune. If the requesting end-point is not compliant, its access will be blocked with an “Access Denied” message. 
3.	Assuming the device is compliant, BIG-IP redirects the user to Azure AD for authentication.
4.	Azure AD Access challenges the user for their username and password.
5.	The user responds with username and password.
6.	Azure AD challenges the user for their second authentication factor.
7.	The user responds with their second-factor credential. 
8.	Azure AD authenticates the user, sends a SAML assertion to BIG-IP, which serves as both a policy engine and a policy enforcement point protecting the resource, and redirects the user back to BIG-IP.
9.	BIG-IP accepts the SAML assertion and determines what resources the user is authorized to access. 
10.	BIG-IP redirects the user to the resource via the resource web portal.


Authentication Message Flow for a Client Application Running Outside the Service Mesh to Access an Enterprise Server Application Running within a Pod in the Service Mesh (F5 NGINX) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the high-level message flow supporting the use case in which a client application that is running outside the service mesh and is authorized to access a server application that is running within a pod in the service mesh, requests and receives access to that server application. In the case depicted here, access to the resource is authenticated and authorized by NGINX Plus, which includes NGINX Mesh Controller acting as PDP and NGINX Ingress Controller and a sidecar container acting as PEPs.

**Figure 3 - Use Case E3B4 - Client Authentication and Access Enforcement for Inter-Service Mesh Communication Using F5 NGINX Plus**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1.	A client application that is running outside the service mesh requests access to a server appli-cation that is running within a pod in the service mesh.
2.	The NGINX Plus Ingress Controller, which proxies traffic for the service mesh, checks with the NGINX Plus Mesh Controller to determine if the client application is authorized to access the server application.
3.	Assuming the client app is authorized, the NGINX Plus Ingress Controller initiates a mutual connection with the server application's sidecar and forwards the traffic to the server applica-tion's sidecar.
4.	The server application's sidecar checks with the NGINX Plus Mesh Controller to determine if the client app is authorized to access the server application.
5.	Assuming the client is authorized, the server application's sidecar proxies traffic to the server application. 


Authentication Message Flow for a Client Application Running Within a Pod to Access an Enterprise Server Application Also Running within a Pod in the Service Mesh (F5 NGINX) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 4* depicts the high-level message flow supporting the use case in which a client application that is running within a pod in the service mesh and is authorized to access a server application that is also running within a pod in the service mesh, requests and receives access to that server application. In the case depicted here, access to the resource is authenticated and authorized by NGINX Plus, which includes NGINX Mesh Controller acting as PDP and sidecar containers that proxy traffic for the client and server applications acting as PEPs.

**Figure 4 - Use Case-E3B4 - Client Authentication and Access Enforcement for Intra-Service Mesh Communication Using F5 NGINX Plus**

|Figure4|

The message flow depicted in *Figure 4* consists of the following steps:

1.	A client application that is running within a pod in the service mesh requests access to a server application that is also running within a pod in the service mesh.
2.	The sidecar that proxies client traffic for the rest of the pod checks with the NGINX Plus Mesh Controller to determine if the client is authorized to access the server application.
3.	Assuming the client app is authorized, the client application's sidecar initiates and performs mTLS authentication with the server application's sidecar and forwards traffic to the server ap-plication's sidecar.
4.	The server application's sidecar checks with the NGINX Plus Mesh Controller to determine if the client is authorized to access the server application.
5.	Assuming the client is authorized, the server application's sidecar proxies traffic to the server application. 


.. |Figure1| image:: images/AppendixO-Figure1.png
   :alt: This figure depicts the logical architecture of E3B4. It uses numbered arrows to depict the general flows of messages.
.. |Figure2| image:: images/AppendixO-Figure2.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a subject who has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource, requests and receives access to that resource.
.. |Figure3| image:: images/AppendixO-Figure3.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a client application that is running outside the service mesh and is authorized to access a server application that is running within a pod in the service mesh, requests and receives access to that server application.
.. |Figure4| image:: images/AppendixO-Figure4.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a client application that is running within a pod in the service mesh and is authorized to access a server application that is also running within a pod in the service mesh, requests and receives access to that server application.
