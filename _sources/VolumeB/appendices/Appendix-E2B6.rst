Enterprise 2 Build 6 (E2B6) - SASE - Google Chrome Enterprise Premium (CEP) - Access Context Manager as PE
===========================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E2B6 uses products from Google Cloud, IBM, Mandiant, Okta, Omnissa, Radiant Logic, SailPoint, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies they contributed to this project overall, see :ref:`collaborators and their contributions`.

E2B6 components consist of Google Chrome Enterprise Premium (CEP), Google Application Connector, Omnissa Workspace ONE UEM, Okta Identity Cloud, Okta Verify App, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable Nessus Network Monitor (NNM), Mandiant Security Validation (MSV), Google Cloud (IaaS), Google Workspace (SaaS), and DigiCert CertCentral.

Note that after Tenable products were implemented at NCCoE, the name Tenable.ad was changed to Tenable Identity Exposure.

Table 1 lists all of the technologies used in Build E2B6. It lists the products used to instantiate each ZTA component and the security function that each component provides.

Note that after the VMware End User Computing Division products were implemented at NCCoE, VMware was acquired by Broadcom, and then the VMware End User Computing Division was divested and reformed under a new entity, Omnissa LLC.

**Table 1 - E2B6 Products and Technologies**

.. csv-table:: E2B6 Products and Technologies
    :file: csv/E2B6-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E2B6. We also describe E2B6's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

Figure 1 depicts the logical architecture of E2B6. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in Figure 1 have the same meanings as they do in :ref:`General ZTA Reference Architecture<ArchitectureFigure1>`. However, Figure 1 includes the specific products that instantiate the architecture of E2B6. Figure 1 also does not depict any of the resource management steps found in :ref:`General ZTA Reference Architecture<ArchitectureFigure1>` because the ZTA technologies deployed in E2B6 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E2B6 was designed with Google CEP - Access Context Manager serving as PE, PA, and Google CEP - Identity Aware Proxy and Google CEP - Chrome Browser serving as PEPs. Okta Identity Cloud serves as the identity, access, and credential manager. Radiant Logic acts as a PIP for the PDP as it responds to inquiries and provides identity information on demand in order for Okta Identity Cloud to make near-real-time access decisions. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flows for Successful Resource Access Requests<message-flow-E2B6>`.

**Figure 1 - Logical Architecture of E2B6**

|Figure1|

ICAM Information Architecture
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How ICAM information is provisioned, distributed, updated, shared, correlated, governed, and used among ZTA components is fundamental to the operation of the ZTA. The ICAM information architecture ensures that when a subject requests access to a resource, the aggregated set of identity information and attributes necessary to identify, authenticate, and authorize the subject is available to be used as a basis on which to make the access decision.

In E2B6, Okta Identity Cloud, Radiant Logic, and SailPoint integrate with each other as well as with other components of the ZTA to support the ICAM information architecture. The ways that these components work together to correlate identity information and to support actions such as users joining, changing roles, and leaving the enterprise are the same in E2B6 as they are in E1B1, E1B2, E1B3, E1B4, and E2B4. These interactions are described in :ref:`E1B1 ICAM Architecture<e1b1icam>`.

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 2` describes the physical architecture of the E2B6 network. :ref:`IaaS - Google` describes the cloud architecture of E2B6.

Message Flows for Successful Resource Access Requests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _message-flow-E2B6:

This section depicts three authentication message flows supported by E2B6. In each flow, a subject who is authorized to access a resource requests and receives access to that resource. In the first flow, we show a user signing into Google Chrome Enterprise Premium - Chrome Browser. In the second flow, the resource is located either on-premises or in an IaaS cloud. In the third flow, the resource is located in Google Workspace, a SaaS cloud. Before a user can access a resource in either of these locations, the user must be onboarded to Google Chrome Enterprise Premium - Chrome Browser. Figure 2 depicts the steps that must be performed to onboard the user to Google Chrome Enterprise Premium - Chrome Browser.

**Figure 2 - Use Case E2B6 - User Signs into Google Chrome Enterprise Premium**

|Figure2|

The message flow depicted in Figure 2 consists of the following steps:

1. The user opens Google Enterprise Chrome Enterprise Premium (CEP) - Chrome Browser, clicks on the user icon at the top right, and selects “Turn on sync”.

2. The Google login page opens and requests a username. The user enters their username.

3. The user is redirected to Okta, the organization's SAML identity provider, for authentication.

4. Okta challenges the user for their first- and second-factor authentication credentials.

5. The user provides their first- and second-factor authentication credentials to Okta.

6. Assuming the user is authenticated successfully, Okta provides a SAML assertion and attributes to the client.

7. Once the user is successfully authenticated, the user is signed in to Google Chrome Browser. Google CEP -Access Context Manager validates device compliance.



Message Flow for User Access to an Enterprise Resource that is Located Either On-Premises or In an IaaS Cloud
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 3 depicts the high-level message flow supporting a user who requests access to a resource located either on premises or in an IaaS cloud. Prior to this message flow, the user is assumed to have already signed in to Google Chrome.

**Figure 3 - Use Case E2B6 - User Requests Access to a Resource Located either On Premises or in an IaaS Cloud**

|Figure3|

The message flow depicted in Figure 3 consists of the following steps:

1.  A user initiates access to a resource, e.g., GitLab.

2.  The endpoint sends a request packet to the resource via the Google Application Connector and then the connector forwards the message to the resource.

3.  The resource, which in this case is GitLab, displays the option for the user to sign in with SAML. When the user clicks on the sign-on with SAML icon on the GitLab screen, the resource creates a SAML request and sends the SAML request to the user's endpoint via the Application Connector.

4.  The user's endpoint sends the SAML request to the Okta Identity Cloud, which is SaaS based.

5.  Okta challenges the user for username and password.

6.  The user responds with username and password.

7.  Okta authenticates the user and verifies the device certificate.

8.  Okta challenges the user to perform second-factor authentication using the Okta Verify App.

9.  The user provides the second authentication factor (i.e., biometrics).

10. Okta generates a SAML assertion and sends it to the user's endpoint.

11. The user's endpoint sends the SAML assertion to the resource (GitLab) via the connector. The resource accepts the assertion and grants the access request.

12. The user accesses the resource based on enterprise policies.

Message Flow for User Access to an Enterprise Resource that is Located in Google Workspace
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Figure 4 depicts the high-level message flow supporting a user requesting access to a resource that is located in Google Workspace, which is a SaaS cloud. Prior to this message flow, the user is assumed to have already signed in to Google CEP - Chrome Browser.

**Figure 4 Use Case E2B6 - User Requests Access to a Resource Located in Google Workspace**

|Figure4|

The message flow depicted in Figure 4 consists of the following steps:

1.  A user initiates access to a resource in Google Workspace

2.  Google Identity creates a SAML request and sends the SAML request to the user's endpoint.

3.  The user's endpoint sends the SAML request to the Okta Identity Cloud, which is SaaS based.

4.  Okta challenges the user for username and password.

5.  The user responds with username and password.

6.  Okta authenticates the user and verifies the device certificate.

7.  Okta challenges the user to perform second-factor authentication using the Okta Verify App.

8.  The user provides the second authentication factor (e.g., biometrics).

9.  Okta generates a SAML assertion and sends it to the user's endpoint.

10. The user's endpoint sends the SAML assertion token to Google Identity. Google Identity accepts the assertion and passes it to Google CEP - Access Context Manager.

11. Google CEP - Access Context Manager postures user's endpoint

12. The user accesses the Google Workspace resource based on enterprise policies identified by Google CEP - Access Context Manager.

.. |Figure1| image:: images/E2B6-Figure1.png
   :alt: This figure depicts the logical architecture of E2B6. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health.
.. |Figure2| image:: images/E2B6-Figure2.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to a resource that is located on-premises.
.. |Figure3| image:: images/E2B6-Figure3.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to an enterprise resource that is located either on-premises or in an IaaS cloud.
.. |Figure4| image:: images/E2B6-Figure4.png
   :alt: This figure depicts the high-level message flow supporting a user who requests access to an enterprise resource that is located in Googlel Workspace.
