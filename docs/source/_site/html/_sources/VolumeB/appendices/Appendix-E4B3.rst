Enterprise 4 Build 3 (E4B3) - EIG Run - IBM Security Verify as PE
=================================================================

.. include:: /_publication_note.rst

Technologies
------------

E4B3 uses products from IBM, Mandiant, Palo Alto Networks, Tenable, and VMware. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E4B3 components consist of IBM Security Verify, IBM Security MaaS360 (for both laptops and mobile devices), IBM Cloud Pak for Security, IBM QRadar XDR, Mandiant Security Validation, Palo Alto Networks GlobalProtect VPN, Tenable.io, Tenable.ad, Tenable NNM, IBM Security Guardium Data Encryption, IBM Security Guardium Data Protection, VMware infrastructure, and DigiCert ONE.

*Table 1* lists all of the technologies used in E4B3 ZTA. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E4B3 Products and Technologies**

.. csv-table:: E4B3 Products and Technologies
    :file: csv/AppendixL-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E4B3. We also describe E4B3's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E4B3. *Figure 1* uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E4B3. *Figure 1* also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E4B3 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E4B3 was designed with IBM Security Verify as the ZTA PE, PA, and PEP, and IBM Security Verify providing ICAM support. Other components that support endpoint security, security analytics, and data security are also listed in *Figure 1*.

**Figure 1 - Logical Architecture of E4B3**

|Figure1|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 4` describes the physical architecture of the E4B3 network.

Message Flows for Successful Resource Access Requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This section depicts some high-level message flows for E4B3 supporting the use case in which a subject who has an enterprise ID and who is authorized to access an enterprise resource requests and receives access to that resource. In both use cases depicted here, access to the resource is protected by IBM Security Verify/Trusteer, which acts as a PDP and an identity provider. In the first use case, the access request is coming from a managed device, and in the second use case, the access request is coming from an unmanaged device.

Use Case in which the Requesting Endpoint is Managed, so Access Is Enforced by IBM Security Verify/Trusteer and Authentication Is Performed by IBM MaaS360
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In this use case, the requesting endpoint is managed by IBM MaaS360. MaaS360 is a UEM that consists of an agent on the endpoint and a cloud component that work together to perform device authentication and first and second-factor user authentication, and also to gather device posture information to ensure device compliance.

The message flow depicted in *Figure 2* shows only the messages that are sent in response to the access request. However, the authentication process also relies on the following additional background communications that occur among components on an ongoing basis:

-  The IBM MaaS360 endpoint agent periodically syncs with the IBM MaaS360 cloud component to reauthenticate the requesting endpoint device using a unique certificate that has been provisioned specifically for that device and sends the cloud component information about device health (e.g., firewall running, anti-malware software, iOS version).

-  IBM MaaS360 is integrated with IBM Security Verify/Trusteer and periodically sends Verify/Trusteer assurance that, based on the device health information collected by IBM MaaS360, the device is compliant with configured policy.

*Figure 2* depicts the message flow for the user's request to access the resource when the requesting endpoint is managed.

**Figure 2 - Use Case E4B3 - The Requesting Endpoint Is Managed, so Access Is Enforced by IBM Security Verify/Trusteer and IBM MaaS360**

|Figure2|

The message flow depicted in Figure L-2 consists of the following steps:

1.	A user requests to access a resource from a managed endpoint.
2.	The resource receives the access request and sends a user authentication request to IBM Se-curity Verify/Trusteer.
3.	Certificate authentication is initiated with the MaaS360 agent.
4.	IBM Security Verify/Trusteer authenticates the requesting device's certificate.
5.	Verify/Trusteer checks the endpoint's compliance status based on information shared by MaaS360.
6.	Verify/Trusteer evaluates the access policy rules to determine if the access request is author-ized.
7.	Assuming the request is authorized and the endpoint has passed the authentication and au-thorization checks, IBM Security Verify/Trusteer creates a SAML assertion token and sends it to the resource. The resource accepts the assertion and grants the access request.
8.	User traffic to and from the resource is secured according to policy (e.g., using TLS or HTTPS).


Use Case in which the Requesting Endpoint Is Unmanaged, so Access Is Enforced by IBM Security Verify/Trusteer, which Also Performs User Authentication
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In this use case, the requesting endpoint is unmanaged. There is no endpoint agent running on the device, so device compliance cannot be enforced.

*Figure 3* depicts the message flow for the user's request to access the resource when the requesting endpoint is unmanaged.

**Figure 3 - Use Case E4B3 - The Requesting Endpoint Is Unmanaged, so Access Is Enforced by IBM Security Verify/Trusteer**

|Figure3|

The message flow depicted in *Figure 3* consists of the following steps:

1.	A user requests to access a resource from an unmanaged endpoint.
2.	The resource receives the access request and sends a user authentication request to IBM Se-curity Verify/Trusteer.
3.	The user is prompted to provide username and password.
4.	IBM Security Verify/Trusteer verifies the username and password.
5.	Verify/Trusteer evaluates the access policy rules to determine if the access request is author-ized.
6.	Assuming the request is authorized and the endpoint has passed the authentication and authorization checks, IBM Security Verify/Trusteer creates a SAML assertion token and sends it to the resource. The resource accepts the assertion and grants the access request.
7.	User traffic to and from the resource is secured according to policy (e.g., using TLS or HTTPS).

Note that the message flows depicted in both of these use cases applies to several of the other use cases we are considering. It applies to all cases in which a user with an enterprise ID who can successfully authenticate themselves requests and receives access to an enterprise resource that they are authorized to access. The message flow is the same regardless of whether the user is located on-premises at headquarters, on-premises at a branch office, or off-premises at home or elsewhere. It is also the same regardless of whether the resource is located on-premises or in the cloud.


.. |Figure1| image:: images/AppendixL-Figure1.png
   :alt: This figure depicts the logical architecture of E4B3. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health.
.. |Figure2| image:: images/AppendixL-Figure2.png
   :alt: This figure depicts the message flow for the user's request to access the resource when the requesting endpoint is managed.
.. |Figure3| image:: images/AppendixL-Figure3.png
   :alt: This figure depicts the message flow for the user's request to access the resource when the requesting endpoint is unmanaged.
