Enterprise 2 Build 5 (E2B5) - SDP and SASE - Lookout SSE and Okta Identity Cloud as PEs
=======================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E2B5 uses products from Google Cloud, IBM, Lookout, Mandiant, Okta, Radiant Logic, SailPoint, Tenable, and VMware. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`collaborators and their contributions`.

E2B5 components consist of Lookout Security Service Edge (SSE) (includes Secure Private Access [SPA], Secure Cloud Access [SCA], and Secure Internet Access [SIA]), Lookout Secure Private Access Connector, VMware Workspace ONE UEM, Lookout MES, Lookout Client, Okta Identity Cloud, Okta Verify App, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable Nessus Network Monitor (NNM), Mandiant Security Validation (MSV), Google Cloud, Google Workspace, and DigiCert CertCentral.

Table 1 lists all of the technologies used in Build E2B5. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E2B5 Products and Technologies**

.. csv-table:: E2B5 Products and Technologies
    :file: csv/AppendixR-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E2B5. We also describe E2B5's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

Figure 1 depicts the logical architecture of E2B5. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in Figure 1 have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>`. However, Figure 1 includes the specific products that instantiate the architecture of E2B5. Figure 1 also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` because the ZTA technologies deployed in E2B5 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E2B5 was designed with Lookout components that serve as PEs, PAs, and PEPs. Okta Identity Cloud also serves as a PE and PA, as well as the build's identity, access, and credential manager. Radiant Logic acts as a PIP for the PDP as it responds to inquiries and provides identity information on demand in order for Okta Identity Cloud to make near-real-time access decisions. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flows for Successful Resource Access Requests<message-flow-e2b5>`.

**Figure 1 - Logical Architecture of E2B5**

|Figure1|

ICAM Information Architecture
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How ICAM information is provisioned, distributed, updated, shared, correlated, governed, and used among ZTA components is fundamental to the operation of the ZTA. The ICAM information architecture ensures that when a subject requests access to a resource, the aggregated set of identity information and attributes necessary to identify, authenticate, and authorize the subject is available to be used as a basis on which to make the access decision.

In E2B5, Okta Identity Cloud, Radiant Logic, and SailPoint integrate with each other as well as with other components of the ZTA to support the ICAM information architecture. The ways that these components work together to correlate identity information and to support actions such as users joining, changing roles, and leaving the enterprise are the same in E2B5 as they are in E1B1, E1B2, E1B3, E1B4, and E2B4. These interactions are described in :ref:`E1B1 ICAM Architecture<e1b1icam>`.

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 2` describes the physical architecture of the E2B5 network.

Message Flows for Successful Resource Access Requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _message-flow-E2B5:

This section depicts several authentication message flows supported by E2B5. In each flow, a subject who is authorized to access a resource requests and receives access to that resource. Access to the resource is authenticated and authorized by various Lookout components that act as PDPs and PEPs. The scenarios differ according to whether the resource is located on-premises, in a private SaaS cloud, in a private IaaS cloud, or on the public internet. The user can be using either a mobile or non-mobile device. As indicated in the diagrams, If the device is mobile, it has Lookout MES running on it; if it is non-mobile, it has the Lookout client running on it.

In each flow, either Lookout MES (mobile) or the Lookout client (non-mobile) is monitoring the device's posture. For mobile devices, Lookout MES is continually sending device compliance information to the Lookout MES server, which forwards the information to the Lookout policy engine, SSE (i.e., SPA, SCA, or SIA). For non-mobile devices, the Lookout client is continually sending device compliance information to the Lookout policy engine. This ensures that the Lookout policy engine has up-to-date information about device posture. Communications between the Lookout MES/client, the Lookout MES server, and the Lookout policy engine are occurring in the background on an ongoing basis and are not depicted explicitly in the authentication flows below.

Message Flow for a Request to Access an On-Premises Resource
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 2 depicts the high-level message flow supporting a user who requests access to a resource that is located on-premises.

**Figure 2 - Use Case E2B5 - User Requests Access to an On-Premises Resource**

|Figure2|

The message flow depicted in Figure 2 consists of the following steps:

1. The user requests access to a resource that is located on-premises. The request is received at the Lookout SSE SPA component.

2. Lookout SSE evaluates the access request in light of the organization's access policies, including consideration of the device's compliance status and user authorization. User is allowed access to the on-premises application's login page.

3. The on-premises application redirects the request to Okta, the organization's identity provider.

4. Okta challenges the user for their first- and second-factor authentication credentials.

5. The user provides their first- and second-factor authentication credentials to Okta.

6. Assuming the user is authenticated successfully, Okta provides a SAML assertion to the endpoint.

7. The endpoint sends the approved request to the on-premises application via the Lookout SSE SPA Connector.

8. A session between the endpoint and the resource is established. User traffic to and from the resource is secured according to policy, and Lookout ZTNA evaluates the session on an ongoing basis to ensure that it continues to be permitted according to organizational policy.

Message Flow for a Request to Access a Resource in a Private SaaS Cloud
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 3 depicts the high-level message flow supporting a user who requests access to an enterprise resource that is located in a SaaS cloud.

**Figure 3 - Use Case E2B5 - User Requesting Access to an Enterprise Resource in a SaaS Cloud**

|Figure3|

The message flow depicted in Figure 3 consists of the following steps:

1. The user requests access to a resource in the SaaS cloud. The request is received at the Lookout SSE SCA component.

2.  Lookout SCA redirects the request to the Lookout Single Sign On (SSO) component.

3.  Lookout SSO redirects the request to Okta, the organization's identity provider.

4. Okta challenges the user for their first- and second-factor authentication credentials.

5. The user provides their first- and second-factor authentication credentials to Okta.

6. Assuming the user is authenticated successfully, Okta provides a SAML assertion to the endpoint.

7. The endpoint sends the SAML assertion to Lookout SCA.

8. Lookout SCA evaluates the access request in light of the organization's access policies by considering the device's compliance status and user authorization.

9. Assuming the access request is permissible by policy, Lookout SCA forwards the approved request to the SaaS application via the Lookout proxy.

10. A session between the endpoint and the resource is established. User traffic to and from the resource is secured according to policy, and Lookout SCA evaluates the session on an ongoing basis to ensure that it continues to be permitted according to organizational policy.

Message Flow for a Request to Access a Resource in a Private IaaS Cloud
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 4 depicts the high-level message flow supporting a user who requests access to an enterprise resource that is located in an IaaS Cloud.

**Figure 4 Use Case E2B5 - User Requesting Access to an Enterprise Resource in an IaaS Cloud**

|Figure4|

The message flow depicted in Figure 4 consists of the following steps:

1. The user requests access to a resource in the IaaS cloud. The request is received at the Lookout SSE SPA component.

2. Lookout SSE evaluates the access request in light of the organization's access policies including consideration of the device's compliance status and user authorization. User is allowed access to the IaaS application's login page.

3. The IaaS application redirects the request to Okta, the organization's identity provider.

4. Okta challenges the user for their first- and second-factor authentication credentials.

5. The user provides their first- and second-factor authentication credentials to Okta.

6. Assuming the user is authenticated successfully, Okta provides a SAML assertion to the endpoint.

7. The endpoint sends the approved request to the IaaS application via the Lookout SPA Connector.

8. A session between the endpoint and the resource is established. User traffic to and from the resource is secured according to policy, and Lookout SSE evaluates the session on an ongoing basis to ensure that it continues to be permitted according to organizational policy.

Message Flow for a Request to Access a Resource on the Internet Using a Mobile Device
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 5 depicts the high-level message flow supporting a user who is using a mobile device and requests access to an enterprise resource that is located on the public internet.

**Figure 5 - Use Case E2B5 - Mobile Device User Requesting Access to a Public Resource on the Internet**

|Figure5|

The message flow depicted in Figure 5 consists of the following steps:

1. The mobile device user requests access to a public internet resource by providing the resource's URL. The Lookout MES client on the mobile device routes this web request to the Lookout's MES server.

2. The Lookout MES server evaluates this access request against organizational policy and risk protection information in the MES safe browsing server, including consideration of device posture.

3. Assuming the requested access has been determined to be permissible, the request is forwarded onto the internet.

4. A web session between the endpoint and the public internet resource is established. User traffic to and from the resource is secured according to policy, and the Lookout MES server evaluates the session on an ongoing basis to ensure that it continues to be permitted according to organizational policy.

Message Flow for a Request to Access a Resource on the Internet Using a Non-Mobile Device
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 6 depicts the high-level message flow supporting a user who is using a non-mobile device and requests access to an enterprise resource that is located on the public internet.

Figure 6 **Use Case E2B5 - Non-Mobile Device User Requesting Access to a Public Resource on the Internet**

|Figure6|

The message flow depicted in Figure 6 consists of the following steps:

1. The non-mobile device user requests access to a public internet resource by providing the resource's URL. The Lookout client on the non-mobile device routes this web request to the Lookout SSE SIA component.

2. The Lookout SSE SIA evaluates this access request against organizational policy and risk protection information, including consideration of device posture.

3. Assuming the requested access has been determined to be permissible, the request is forwarded onto the internet.

4. A web session between the endpoint and the public internet resource is established. User traffic to and from the resource is secured according to policy, and the Lookout SSE SIA evaluates the session on an ongoing basis to ensure that it continues to be permitted according to organizational policy.

Message Flow for a Request to Access a Resource in a Private IaaS Cloud or On-Premises Resource Using a Browser (Mobile and Non-Mobile)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 7 depicts the high-level message flow supporting a user who is using a non-mobile device and requests access to an enterprise resource that is located either on-premises or in a private IaaS cloud.

**Figure 7 - Use Case E2B5 - User Requesting Access to an Enterprise Resource in an IaaS Cloud**

|Figure7|

The message flow depicted in Figure 7 consists of the following steps:

1. The user requests access to a resource that is either in a private IaaS cloud or on-premises.

2. The resource redirects the request to Lookout SSE. Lookout SSE evaluates the access request in light of the organization's access policies.

3. Lookout SSE forwards the authentication request to Okta, the organization's identity provider.

4. Okta challenges the user for their first- and second-factor authentication credentials.

5. The user provides their first- and second-factor authentication credentials to Okta.

6. Assuming the user is authenticated successfully, Okta provides a SAML assertion to the endpoint.

7. The endpoint sends the approved request to the application via the Lookout SPA Connector.

8. A session between the endpoint and the resource is established. User traffic to and from the resource is secured according to policy, and Lookout SSE evaluates the session on an ongoing basis to ensure that it continues to be permitted according to organizational policy.

.. |Figure1| image:: images/AppendixR-Figure1.png
   :alt: This figure depicts the logical architecture of E2B5. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health.
.. |Figure2| image:: images/AppendixR-Figure2.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to a resource that is located on-premises.
.. |Figure3| image:: images/AppendixR-Figure3.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to an enterprise resource that is located in a SaaS cloud.
.. |Figure4| image:: images/AppendixR-Figure4.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to an enterprise resource that is located in an IaaS Cloud.
.. |Figure5| image:: images/AppendixR-Figure5.png
   :alt: This figure depicts the high-level message flow supporting a user who is using a mobile device and requests access to an enterprise resource that is located on the public internet.
.. |Figure6| image:: images/AppendixR-Figure6.png
   :alt: This figure depicts the high-level message flow supporting a user who is using a non-mobile device and requests access to an enterprise resource that is located on the public internet.
.. |Figure7| image:: images/AppendixR-Figure7.png
   :alt: This figure depicts the high-level message flow supporting a user who is using a non-mobile device and requests access to an enterprise resource that is located either on-premises or in a private IaaS cloud.
