Enterprise 2 Build 1 (E2B1) - EIG Crawl - Ping Identity Ping Federate as PE
===========================================================================

.. include:: /_publication_note.rst

Technologies
------------

E2B1 uses products from Cisco Systems, IBM, Mandiant, Palo Alto Networks, Ping Identity, Radiant Logic, SailPoint, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`.

E2B1 components consist of PingFederate, which is connected to the Ping Identity SaaS offering of PingOne, Radiant Logic RadiantOne Intelligent Identity Data Platform, SailPoint IdentityIQ, Cisco Duo, Palo Alto Networks Next Generation Firewall, IBM Security QRadar XDR, Tenable.io, Tenable.ad, Tenable Nessus Network Monitor (NNM), Mandiant Security Validation (MSV), and DigiCert CertCentral.

Table 1 lists all of the technologies used in E2B1. It lists the products used to instantiate each ZTA component and the security function that each component provides.

**Table 1 - E2B1 Products and Technologies**

.. csv-table:: E2B1 Products and Technologies
    :file: csv/AppendixE-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E2B1 relative to how it instantiates the EIG crawl phase reference architecture depicted in :ref:`Architecture - Figure 2<ArchitectureFigure2>`. We also describe E2B1's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

:ref:`Figure 1<e2b1icam>` depicts the logical architecture of E2B1. The figure uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in :ref:`Figure 1<e2b1icam>` have the same meanings as they do in :ref:`Architecture - Figure 1<ArchitectureFigure1>` and :ref:`Architecture - Figure 2<ArchitectureFigure2>`. However, :ref:`Figure 1<e2b1icam>` includes the specific products that instantiate the architecture of E2B1. :ref:`Figure 1<e2b1icam>` also does not depict any of the resource management steps found in :ref:`Architecture - Figure 1<ArchitectureFigure1>` and :ref:`Architecture - Figure 2<ArchitectureFigure2>` because the ZTA technologies deployed in E2B1 do not support the ability to perform authentication and reauthentication of the resource or periodic verification of resource health.

E2B1 was designed with a single ICAM system (Ping Identity PingFederate) that serves as the identity, access, and credential manager as well as the ZTA PE and PA. PingFederate also serves as its PEP. Radiant Logic acts as a PIP for the PDP as it responds to inquiries and provides user identity and authentication information on demand in order for Ping Identity PingFederate to make near-real-time access decisions. Cisco Duo provides endpoint protection by monitoring the status and configuration of the endpoint to ensure that its health posture continues to conform with enterprise policy. Duo also provides second-factor user authentication. Note that both multifactor authentication and directory services are also available through Ping, but for purposes of this collaborative build, Ping is demonstrating standards-based interoperability by integrating with Cisco Duo for MFA and Radiant Logic RadiantOne for federated identity services. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flow for a Successful Resource Access Request<message-flow-e2b1>`.

**Figure 1 - Logical Architecture of E2B1**

|Figure1|

.. _E2B1ICAM:

ICAM Information Architecture
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

How ICAM information is provisioned, distributed, updated, shared, correlated, governed, and used among ZTA components is fundamental to the operation of the ZTA. The ICAM information architecture ensures that when a subject requests access to a resource, the aggregated set of identity information and attributes necessary to identify, authenticate, and authorize the subject is available to be used as a basis on which to make the access decision.

In E2B1, Ping, Radiant Logic, and SailPoint integrate with each other as well as with other components of the ZTA to support the ICAM information architecture. Ping Identity PingFederate uses authentication and authorization to manage access to enterprise resources. SailPoint governs and RadiantOne aggregates identity information that is available from many sources within the enterprise. RadiantOne stores, normalizes, and correlates this aggregation of information and extended attributes and provides appropriate views of the information in response to queries. RadiantOne monitors each source of identity truth and updates changes in near real-time to ensure that Ping is able to enforce access based on accurate data. SailPoint is responsible for governance of the identity data. It executes automated, policy-based workflows to manage the lifecycle of user identity information and manage user accounts and permissions, ensuring compliance with requirements and regulations. To perform its identity aggregation and correlation functions, Radiant Logic connects to all locations within the enterprise where identity data exists to create a virtualized central identity data repository. SailPoint may also connect directly to sources of identity data or receive additional normalized identity data from Radiant Logic in order to perform its governance functions.

Use of these three components to support the ICAM information architecture in Enterprise 2 is intended to demonstrate how a large enterprise with a complex identity environment might operate—for example, an enterprise with two ADs and multiple sources of identity information, such as HR platforms, the back-end database of a risk-scoring application, a credential management application, a learning management application, on-premises LDAP and databases, etc. Mimicking a large, complex enterprise enables the project to demonstrate the ability to aggregate identity data from many sources and provide identity managers with a rich set of attributes on which to base access policy. By aggregating risk-scoring and training data with more standard identity profile information found in AD, rich user profiles can be created, enabling enterprise managers to formulate and enforce highly granular access policies. Information from any number of the identity and attribute sources can be used to make authentication and authorization decisions. In addition, such aggregation allows identities for users in a partner organization whose identity information is not in the enterprise AD to be made available to the enterprise identity manager so it has the information required to grant or deny partner user access requests. Policy-based access enforcement is also possible, in which access groups can be dynamically generated based on attribute values.

Although federated identity and identity governance technologies provide automation to ease the burden of aggregating identity information and enforcement of identity governance, they are not required supporting components for implementing a ZTA in situations in which there may only be one or a few sources of identity data.

The subsections below explain the operations of the ICAM information architecture for E2B1 when correlating identity information and when a user joins, changes roles, or leaves the enterprise. The operations depicted support identity correlation, identity management, identity authentication and authorization, and SIEM notification. It is worth noting that both Ping Identity and SailPoint also support additional features that we have not deployed at this time, such as the ability to perform just-in-time provisioning of user accounts and permissions and the ability to remove access permissions or temporarily disable access authorizations from user accounts in response to alerts triggered by suspicious user activity.

Identity Correlation
''''''''''''''''''''

:ref:`Figure 2<Appendix-E2B1-Figure2>` depicts the ICAM information architecture for E2B1, showing the steps involved in correlating identity information to build a rich global profile that includes not just identity profiles found in AD, but additional profiles and attributes from other platforms as well. The steps are as follows:

1. RadiantOne aggregates, correlates, and normalizes identity information from all sources of identity information in the enterprise. In complex architectures, a ZTA requires an identity data foundation that bridges legacy systems and cloud technologies, and that extends beyond legacy AD domains. In our builds, the identity source used is an example HR database that is augmented by extended user profile and attribute information that is representative of information that could come from a variety of identity sources in a large enterprise. A credential management database, an LDAP database, and a learning management application are some examples of such identity sources. These are depicted in the lower left-hand corner of :ref:`Figure 2<Appendix-E2B1-Figure2>` in the box labeled “Enhanced Identity Data Sources.”

2. The correlated identity profiles in RadiantOne are consumed by SailPoint.

3. SailPoint provisions identities into AD. Multiple AD instances may be present in the enterprise, as depicted. However, each of our builds includes only one AD instance.

4. RadiantOne correlates endpoint identities from AD.

5. SailPoint provisions identities into appropriate enterprise resources—e.g., SaaS, IaaS, enterprise applications, and endpoint protection platforms. (This provisioning may occur directly or via Ping.)

6. As the new identities appear in the SaaS, IaaS, enterprise application, endpoint protection, and other components, Radiant Logic is notified. Radiant Logic collects, correlates, and virtualizes this new identity information and adds it back into the global identity profile that it is maintaining. It also updates its HR, authentication, and authorization views to reflect the recent changes. Ping will eventually query these authentication and authorization information views in Radiant Logic to determine whether to grant future user access requests.

   Note that in this architecture, persistent storage of personally identifiable information (PII) is not required within any SaaS service. RadiantOne stores all user identity information, and RadiantOne has been installed on-premises. Ping does not store any user data. When Ping needs user identity data, it looks up this information directly from RadiantOne.

The identity correlation lifecycle is an ongoing process that occurs continuously as events that affect user identity information, accounts, and permissions occur, ensuring that the global identity profile is up to date. Examples of such events are depicted in the subsections below.

**Figure 2 - E2B1 ICAM Information Architecture - Identity Correlation**

|Figure2|

.. _Appendix-E2B1-Figure2:

User Joins the Enterprise
'''''''''''''''''''''''''

:ref:`Figure 3<Appendix-E2B1-Figure3>` depicts the ICAM information architecture for E2B1, showing the steps required to provision a new identity and associated access privileges when a new user is onboarded to the enterprise. The steps are as follows:

1. When a new user joins the enterprise, an authorized HR staff member is assumed to input information into some sort of enterprise employee onboarding and management HR application that will ultimately result in a new, active HR record for the employee appearing in the Radiant Logic human resources record view. In practice, the application that the HR staff member uses will typically store identity records in backend databases like the ones depicted in the lower left-hand corner of *Figure 3* that are in the box labeled “Enhanced Identity Data Sources.” As these databases get updated, Radiant Logic is notified, and it responds by collecting the new information and using it to dynamically update its HR view.

2.  In the course of performing its governance activities, SailPoint detects the new HR record in Radiant Logic. SailPoint evaluates this new HR record, which triggers a *Joiner* lifecycle event, causing SailPoint to execute a policy-driven workflow that includes steps 3, 4, and 5.

3.  SailPoint provisions access permissions to specific enterprise resources for this new user. These access permissions, known as the user's *Birthright Role Access*, are automatically determined according to policy based on factors such as the user's role, type, group memberships, and status. These permissions comprise the access entitlements that the employee has on day 1. SailPoint creates an account for the new user in AD, thereby provisioning appropriate enterprise resource access for the new user. Also (not labeled in the diagram), Radiant Logic then collects and correlates this user information from AD into the global identity profile that it is maintaining.

4.  Assuming there are resources for which access is not managed by AD that the new user is authorized to access according to their Birthright Role, SailPoint also provisions access to these resources for the new user by creating new accounts for the user, as appropriate, on SaaS, IaaS, enterprise application, MDM, EPP, and other components. (This provisioning may occur directly or via Ping.)

5.  Once the new identity and its access privileges have been provisioned, SailPoint audits the identity and provisioning actions that were just performed.

6. As the new enterprise accounts appear in the SaaS, IaaS, enterprise application, endpoint protection, and other components, Radiant Logic is notified. Radiant Logic collects, correlates, and virtualizes this new identity information and adds it back into the global identity profile that it is maintaining. It also updates its HR, authentication, and authorization (AuthN/AuthZ) views to reflect the recent changes. Ping will eventually query these authentication and authorization information views in Radiant Logic to determine whether or not to grant future user access requests. (Note that Ping will only query these views in Radiant Logic when a user tries to access a resource; it will not query if there is no action from the user. Also, RadiantOne stores all user identity information; Ping does not store any user data. When Ping needs user identity data, it looks up this information directly from RadiantOne.)

**Figure 3 - E2B1 ICAM Information Architecture - New User Onboarding**

|Figure3|

.. _Appendix-E2B1-Figure3:

User Changes Roles
''''''''''''''''''

:ref:`Figure 4<Appendix-E2B1-Figure4>` depicts the ICAM information architecture for E2B1, showing the steps required to remove some access privileges and add other access privileges for a user in response to that user changing roles within the enterprise. The steps are as follows:

1. When a user changes roles within the enterprise, an authorized HR staff member is assumed to input information into some sort of enterprise employee management application that will result in the Radiant Logic HR record for that user indicating that the user has changed roles.

2. SailPoint detects this updated HR record in Radiant Logic. SailPoint evaluates this updated HR record, which triggers a *Mover* lifecycle event, causing SailPoint to execute a policy-driven workflow that includes steps 3, 4, 5, and 6.

3. SailPoint removes access permissions associated with the user's prior role (but not with the user's new role) from the user's AD account and removes access from other enterprise resources (e.g., SaaS, IaaS, enterprise applications, MDM) that the user had been authorized to access as a result of their prior role but is not authorized to access as a result of their new role. Also (not labeled in the diagram), Radiant Logic then collects and correlates any changes that were made to the user's account from AD into the global identity profile that it is maintaining.

4. Assuming there are enterprise resources that the user's new role entitles them to access that are not managed by AD, SailPoint provisions access to these resources for the user by creating new accounts for the user, as appropriate, in SaaS, IaaS, enterprise application, endpoint protection, MDM, and other components. (This provisioning may occur directly or via Ping.)

5. SailPoint generates an access review for management to confirm or revoke the changes that have been made. Such an access review is not strictly necessary. The permission changes could be executed in a fully automated manner, if desired, and specified by policy. However, having an access review provides management with the opportunity to exercise some supervisory discretion to permit the user to temporarily continue to have access to some resources associated with their former role that may still be needed.

6. Once the access review has been completed and any access privilege changes deemed necessary have been performed, SailPoint audits the changes.

7. As the new enterprise accounts appear in the SaaS, IaaS, enterprise application, endpoint protection, and other components, and as existing account access is removed, Radiant Logic is notified. Radiant Logic collects, correlates, and virtualizes this new identity information and adds it back into the global identity profile that it is maintaining. It also updates its HR, authentication, and authorization views to reflect the recent changes. Ping will eventually query these authentication and authorization information views in Radiant Logic to determine whether to grant future user access requests. (RadiantOne stores all user identity information; Ping does not store any user data. When Ping needs user identity data, it looks up this information directly from RadiantOne.)

**Figure 4 - E2B1 ICAM Information Architecture - User Changes Roles**

|Figure4|

.. _Appendix-E2B1-Figure4:

User Leaves the Enterprise
''''''''''''''''''''''''''

*Figure 5* depicts the ICAM information architecture for E2B1, showing the steps required to disable or delete an identity and remove access privileges in response to a user leaving the enterprise. The steps are as follows:

1. When a user's employment is terminated, an authorized HR staff member is assumed to input information into some sort of enterprise employee management application that will result in the Radiant Logic HR record for that user indicating that the user has changed from active to inactive status.

2. SailPoint detects this updated HR record in Radiant Logic. SailPoint evaluates this updated HR record, which triggers a *Leaver* lifecycle event, causing SailPoint to execute a policy-driven workflow that includes steps 3, 4, 5, and 6.

3. SailPoint removes all access permissions associated with the user identity from AD. Also (not labeled in the diagram), Radiant Logic then collects and correlates this user access authorization change from AD into the global identity profile that it is maintaining.

4. SailPoint either disables or deletes all enterprise resource accounts associated with the user identity, as defined by policy, from components such as SaaS, IaaS, enterprise applications, and endpoint protection platforms. (SailPoint may perform these actions directly or via Ping.)

5. SailPoint removes the user identity from all governance groups the identity is in.

6. SailPoint audits the changes made as a result of this user termination.

7. As the enterprise accounts associated with the user's identity are deleted or disabled, Radiant Logic is notified. Radiant Logic collects, correlates, and virtualizes this new identity information and adds it back into the global identity profile that it is maintaining. It also updates its HR, authentication, and authorization views to reflect the recent changes. Ping will eventually query these authentication and authorization information views in Radiant Logic to determine whether or not to grant future user access requests. (RadiantOne stores all user identity information; Ping does not store any user data. When Ping needs user identity data, it looks up this information directly from RadiantOne.)

**Figure 5 - E2B1 ICAM Information Architecture - User Termination**

|Figure5|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

:ref:`Enterprise 2` describes the physical architecture of the E2B1 network.

Message Flow for a Successful Resource Access Request
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _message-flow-e2b1:

Below is depicted the high-level message flow supporting the use case in which a subject who has an enterprise ID, who is located on-premises, and who is authorized to access an enterprise resource, requests and receives access to that resource. In the case depicted here, access to the resource is protected by PingFederate, which acts as a PDP and an identity provider; Cisco Duo, which consists of an agent on the endpoint and a cloud component that work together to perform second-factor user authentication and also to gather device health information to ensure device compliance; and Radiant Logic, which performs credential validation for authentication and provides granular user-relevant attributes and groups for authorization at the request of PingFederate.

The message flow depicted in *Figure 6* shows only the messages that are sent in response to the access request. However, the authentication process also relies on the following additional background communications that occur among components on an ongoing basis:

-  The Cisco Duo endpoint agent periodically syncs with the Cisco Duo cloud component to reauthenticate the requesting endpoint device using a unique certificate that has been provisioned specifically for that device and sends the cloud component information about device health (e.g., firewall running, anti-malware software, iOS version).

-  Cisco Duo is integrated with PingFederate and periodically sends PingFederate assurance that, based on the device health information collected by Cisco Duo, the device is compliant with configured policy.

*Figure 6* depicts the message flow for the user's request to access the resource.

**Figure 6 - Use Case E2B1 - Access Enforced by PingFederate, Cisco Duo, and Radiant Logic**

|Figure6|

The message flow depicted in *Figure 6* consists of the following steps:

1.  A user requests to access a resource by typing the resource's URL into a browser.

2.  The resource receives the access request and sends a user authentication request to PingFederate.

3.  PingFederate consults the device health information it has received in the background from Cisco Duo verifying that the device has been authenticated and is compliant with policy.

4.  PingFederate prompts for username and password.

5.  The user responds with username and password.

6.  PingFederate sends the user's username and password to the Ping LDAP Gateway to facilitate communication between the cloud-hosted Ping and the on premises Radiant Logic resources.

7.  The LDAP gateway forwards the LDAP authentication request to Radiant Logic.

8.  Radiant Logic authenticates that the username exists in the master user record and the provided password (credential) is valid based on credentials stored in Radiant Logic or in another source of identity credentials federated by Radiant Logic.

9.  Radiant Logic replies to the LDAP gateway with a valid BIND indicating a successful user authentication and all additional user attributes requested by Ping at the time of Authentication

10. The LDAP gateway forwards the response from Radiant Logic to PingFederate with the successful BIND and applicable user's attributes.

11. PingFederate requests Cisco Duo to perform second-factor user authentication.

12. Cisco Duo challenges the user to provide the second authentication factor.

13. The user responds with the second authentication factor.

14. Cisco Duo responds to PingFederate, indicating that the user authenticated successfully.

15. PingFederate sends a SAML assertion token to the resource. The resource accepts the assertion and grants the access request.

16. User traffic to and from the resource is secured according to policy (e.g., using TLS or HTTPS).

Note that the message flow depicted in Figure 6 applies to several of the use cases we are considering. It applies to all cases in which a user with an enterprise ID who can successfully authenticate themselves and who is using an enterprise-owned endpoint requests and receives access to an enterprise resource that they are authorized to access. The message flow is the same regardless of whether the employee is located on-premises at headquarters, on-premises at a branch office, or off-premises at home or elsewhere. It is also the same regardless of whether the resource is located on-premises or in the cloud.

.. |Figure1| image:: images/AppendixE-Figure1.png
   :alt: This figure depicts the logical architecture of E2B1. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity, user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user and the requesting endpoint and periodic verification of requesting endpoint health.
.. |Figure2| image:: images/AppendixE-Figure2.png
   :alt: This figure depicts the ICAM information architecture for E2B1, showing the steps involved in correlating identity information to build a rich global profile that includes not just identity profiles found in AD, but additional profiles and attributes from other platforms as well.
.. |Figure3| image:: images/AppendixE-Figure3.png
   :alt: This figure depicts the ICAM information architecture for E2B1, showing the steps required to provision a new identity and associated access privileges when a new user is onboarded to the enterprise. 
.. |Figure4| image:: images/AppendixE-Figure4.png
   :alt: This figure depicts the ICAM information architecture for E2B1, showing the steps required to remove some access privileges and add other access privileges for a user in response to that user changing roles within the enterprise. 
.. |Figure5| image:: images/AppendixE-Figure5.png
   :alt: This figure depicts the ICAM information architecture for E2B1, showing the steps required to disable or delete an identity and remove access privileges in response to a user leaving the enterprise. 
.. |Figure6| image:: images/AppendixE-Figure6.png
   :alt: This figure depicts the high-level message flow supporting the use case in which a subject who has an enterprise ID, who is located on-premises, and who is authorized to access an enterprise resource, requests and receives access to that resource. 