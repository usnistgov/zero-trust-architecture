Enterprise 4 Build 4 (E4B4) - SDP, Microsegmentation, and EIG - VMware Workspace ONE Access, VMware Unified Access Gateway, and VMware NSX-T as PEs
===================================================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E4B4 uses products from IBM, Mandiant, Tenable, and VMware. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`. Note that after this build was completed, VMware was acquired by Broadcom.

E4B4 components consist of VMware Workspace ONE Access, VMware Unified Access Gateway (UAG), VMware NSX-T, VMware Workspace ONE UEM, VMware Workspace ONE MTD, VMware Carbon Black Enterprise EDR, VMware Carbon Black Cloud, VMware vSphere, VMware vCenter, VMware vSAN, IBM QRadar XDR, Mandiant Security Validation, Tenable.io, Tenable.ad, Tenable NNM, and DigiCert ONE.

*Table 1* lists all of the technologies used in Build E4B4. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E4B4 Products and Technologies**

.. csv-table:: E4B4 Products and Technologies
    :file: csv/AppendixP-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E4B4. We also describe E4B4's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E4B4. *Figure 1* uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E4B4. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E4B4 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E4B4 was designed with VMware Workspace ONE Access, VMware UAG, and VMware NSX-T as its PEs and PAs, VMware UAG and VMware NSX-T as its PEPs, and VMware Workspace ONE Access providing ICAM support. Other components that support endpoint security, security analytics, and data security are also listed in *Figure 1*.

**Figure 1 - Logical Architecture of E4B4**

|Figure1|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 4` describes the physical architecture of the E4B4 network.

Message Flows for Successful Resource Access Requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This section depicts some high-level message flows for E4B4. Resource access is protected by VMware technology, which acts as a PDP and PEP. VMware products also serve as the identity provider for the build and provide endpoint protection.

Authentication Message Flow for Access to Both Internal and External Resources (VMware Workspace ONE Access, VMware Workspace ONE UEM) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 2* depicts the high-level message flow supporting the use case in which a subject who has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource, requests and receives access to that resource. In the case depicted here, the request to access the resource and all communication between the user and the resource flows through an authenticated tunnel. Access to the resource is authenticated and authorized by:

-  VMware Workspace ONE Access, which acts as both PDP and IdP

-  VMware Workspace ONE UEM, which has an agent running on the requesting endpoint that assesses device compliance and periodically reports device compliance status to the VMware Workspace ONE UEM controller

The message flow depicted in *Figure 2* shows only the messages that are sent in response to the access request. However, the authentication and access process also relies on additional background communications that occur between the Workspace ONE UEM agent and the Workspace ONE UEM controller that provide the controller with device compliance status on an ongoing basis.

Prior to the message flow depicted in *Figure 2*, the user is assumed to have authenticated to the VMware Workspace ONE UEM agent on the device. After the user authenticates to this agent, if the user requests access to a protected resource, an authenticated tunnel can be established between the Workspace ONE UEM agent on the user's device and the UAG that is protecting the requested resource.

**Figure 2 - Use Case E4B4 - User Authentication and Access Enforcement Using Workspace ONE Access and Workspace ONE UEM**

|Figure2|

The message flow depicted in *Figure 2* consists of the following steps:

1.	A user who has already logged into the UEM agent on an enterprise-managed device requests to access a resource. This request flows through an authenticated tunnel to the VMware Unified Access Gateway (UAG) that is protecting the resource.
2.	The UAG contacts Workspace ONE UEM to verify that the device is compliant. 
3.	Assuming the device is compliant, the UAG forwards the user's request to the resource.
4.	Because the user does not have an access token for the resource, the user's access request is redirected to Workspace ONE Access so the user can be authenticated.
5.	Workspace ONE Access contacts Workspace ONE UEM to verify that the device is compliant.
6.	Assuming the device is compliant, Workspace ONE Access challenges the user for their authentication credentials.
7.	The user responds with their first-factor credentials (i.e., username and password).
8.	Workspace ONE Access challenges the user for their second authentication factor.
9.	The user responds with their second-factor credential. 
10.	Assuming that the user has authenticated successfully, and that policy indicates that the user is authorized to access the resource, Workspace ONE issues the requesting user a SAML asser-tion for access to the resource. 
11.	The user sends the SAML assertion to the resource via the authenticated tunnel to the UAG. The resource accepts the assertion and grants the access request.
12.	User traffic to and from the resource is secured according to policy on the authenticated tunnel.

Note that the message flow described above is the same regardless of whether the employee is located on-premises at headquarters, on-premises at a branch office, or off-premises at home or elsewhere. It is also the same regardless of whether the resource is located on-premises or in the cloud.


Authentication Message Flow for Network Access to a Resource from a VM (VMware NSX-T, VMware VMtool, Microsoft AD) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the high-level message flow supporting the use case in which a subject who has an enterprise ID, is using a VM on an NSX-T managed network segment, and is authorized to have network access to an enterprise resource, requests and receives network access to the resource. In the use case depicted here, network access to the resource is managed by VMware NSX-T, which uses device identity information provided by a VMware VMtool agent running on the requesting VM and relies on Microsoft AD as an identity provider:

-  NSX-T provides network access based on identity, but does not control access to the resource itself.

-  VMtool is a client agent running on the requesting VM that provides identity information to NSX-T.

-  Microsoft AD serves as the IdP to authenticate user identities.

-  NSX AD log scraping is another method that NSX uses to determine who is logged into a VM if the VMtool agent stops working or if the VMtool agent is not installed on a VM. (VMtool is the primary method of determining who is logged in, and log scraping is a secondary backup method.)

**Figure 3 - Use Case E4B4 - User Authentication and Authorization for Network Access to a Resource from a VM Using NSX-T and VMtool client agent**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1.	NSX-T synchronizes select AD groups from Microsoft AD. These groups are then used to create access policies in NSX-T based on identity.
2.	The user enters their Microsoft AD credential (e.g., username and password) on the device to attempt to log into a VM.
3.	The device (VM) passes the user authentication request to Microsoft AD
4.	Microsoft AD verifies the user's credentials to authenticate the user's identity and grants the logon request.
5.	(5a.) The VMtool agent on the requesting VM sends the user's username to NSX-T, or, alternatively, if the VMtool agent is not installed on the VM or if it is not working, then (5b.) NSX uses AD log scraping as a secondary method to identify the user.
6.	The user makes a request to access a resource on the network, which is sent to NSX-T.
7.	Assuming enterprise policy permits, NSX-T grants the user network access to the resource. 

Note that the message flow described above authenticates and authorizes the user to have network access to the resource based on the user's identity. However, it does not control access to the resource itself. That is, the user is permitted to reach the resource, but is not logged into the resource. After a user has performed the message flow described here to gained network access to the resource, they would initiate the call flow described in :ref:`Authentication Message Flow for Access to Both Internal and External Resources (VMware Workspace ONE Access, VMware Workspace ONE UEM)` to be authenticated and authorized for access to the resource itself using VMware Workspace ONE Access and VMware Workspace One UEM.

.. |Figure1| image:: images/AppendixP-Figure1.png
   :alt: This figure depicts the logical architecture of E4B4. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health.
.. |Figure2| image:: images/AppendixP-Figure2.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a subject who has an enterprise ID, is using a compliant device, and is authorized to access an enterprise resource, requests and receives access to that resource.
.. |Figure3| image:: images/AppendixP-Figure3.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a subject who has an enterprise ID, is using a VM on an NSX-T managed network segment, and is authorized to have network access to an enterprise resource, requests and receives network access to the resource.