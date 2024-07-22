Demonstration Terminology
===============================

.. include:: /_publication_note.rst

Definitions
-----------

Network IDs
~~~~~~~~~~~

As defined in NIST SP 800-63, an *identity* is an attribute or set of attributes that uniquely identifies a subject *[2]*. Here, a *network identity* is used simply as an identity that allows the subject to identify itself to all (network) connected enterprise resources. The following definitions are used for network IDs:

-  **Enterprise-ID:** An ID issued and maintained by the enterprise. It is stored in one (or more) identity stores maintained by the enterprise.

-  **Federated-ID:** An ID issued and maintained by another enterprise in a community of interest, and partner enterprises have a trusted means to authenticate the ID. This could include things such as a common PKI, etc.

-  **Other-ID:** An ID issued and maintained by another enterprise but known or registered by the first enterprise. Examples include contractors and customers. The other enterprise can authenticate to the first enterprise, but the first enterprise may have limited visibility to all attributes/roles associated with the identity. For example, the first enterprise may be able to verify only that the Other-ID is still considered valid, but no other information from the other enterprise (employee ID number, other PII, etc.).

-  **No-ID:** An anonymous ID unknown to the enterprise that the enterprise would be unable to authenticate. This may also be referred to as a “guest” to the enterprise. No-ID will also be used to indicate an anonymous subject that does not present any ID.

Subject and Requested Resource Types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In zero trust, all enterprise data, assets, etc. are considered resources. To clarify the actors (subject and requested resource) in the following scenarios, the following more detailed definitions are used:

-  **Enterprise endpoint (EP):** Owned and fully managed by the enterprise. The enterprise can inspect and modify any data on the endpoint. An EP is usually acting as the requesting subject but can be the target of a management utility. An EP could be physical (e.g., a laptop) or virtual (e.g., virtual machine or container). Each EP should be able to be uniquely identified by the enterprise.

-  **Enterprise resource (RSS):** Fully managed by the enterprise. The enterprise can inspect and modify the resource. An RSS is usually acting as the target of a request. Like EP above, each RSS should be uniquely identified by the enterprise.

-  **Bring your own device (BYOD):** Not owned by the enterprise and not managed by the enterprise. The enterprise can inspect the device but cannot directly manage or wipe the device. User agents, certificates, etc. may be pre-installed by the device's owner, but the endpoint is not managed by the enterprise. A BYOD is usually acting on behalf of the requesting subject or as the target of a management utility. A BYOD device may be uniquely identified by the enterprise.

-  **Guest device:** Not owned or managed by the enterprise and is opaque to the enterprise. The enterprise can only see what is emitted and received by its enterprise managed infrastructure. Examples include browser user agents and DNS queries. A guest device is usually acting as the requesting subject or as the target of a management utility. Guest devices are not assumed to be uniquely identified by the enterprise.

Resource and Querying Endpoint Compliance Classification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following definitions are used for endpoint and resource security compliance policies:

-  **(EIG) Endpoint Compliance:** Policy that requires the endpoint device to be uniquely identified and to conform to the enterprise security policy for the device. An endpoint is considered to be in compliance if both of the above are true.

-  **(EIG) Resource Compliance:** Policy that requires the enterprise-managed resource to be identified and to conform to the enterprise security policy for the resource. A resource is considered to be in compliance if both of the above are true.

Desired Outcomes
~~~~~~~~~~~~~~~~

The following definitions are used for desired outcomes:

-  **Access to Network:** Endpoint is allocated an address on enterprise infrastructure and enrolled/updated into any monitoring system in place for the enterprise. This result is only applicable to select on-premises (or branch) demonstrations. This does not grant the endpoint any privileges beyond the ability to send traffic on the network.

-  **Access to Public Network:** Endpoint is allocated an address, but only allowed access to the (public) internet; cannot reach/access non-public enterprise resources. This result is only applicable to select on-premises (or branch) demonstrations. This does not grant the endpoint any privileges beyond the ability to send traffic on the network. Traffic bound for external Internet connected resources may be further screened or monitored.

-  **Limited Access to Network:** Endpoint is allocated an address with strict traffic restrictions. This may include a quarantine state with only access to update/patch management system. This result is only applicable to select on-premises (or branch) demonstrations. This does not grant the endpoint any privileges beyond the ability to send traffic on the network that may be restricted to only provide reachability to a select set of services.

-  **No Access to Network:** Endpoint is not allocated an address and cannot send or receive communication. This result is only applicable to select on-premises (or branch) demonstrations. This means the endpoint cannot send queries to any resource.

-  **Access (to Resource) Successful:** Access to the resources that are specified in the profile is achieved. The subject initiates a session with the authorized privileges.

-  **Access (to Resource) Limited:** Access to a subset, but not all, of the resources that are specified in the profile is achieved. The subject initiates a session with a restricted subset of the authorized privileges.

-  **Access (to Resource) Not Successful:** No access to the requested resource is achieved.

-  **Keep Access (to Resource):** Access remains at the previous state.

-  **Max. Limited Access to Network:** This outcome is specific for device-based assets that will be authenticated. This means that portions of the network or some RSS will not be available to be accessed by this subject. This is similar to Limited Access to Network (above), but may allow the endpoint to access a set of resources beyond enterprise endpoint management/update services.

-  **Terminate Access (to X):** The session is terminated or all access to the network is terminated (i.e., no longer allowed to send/receive communications).

-  **Other Outcome:** Some demonstrations use explicit text that informs of a desired action. Examples: *“Terminate all sessions”* or *“Log API call.”*

Authentication Status
~~~~~~~~~~~~~~~~~~~~~

Table 1 explains the authentication status codes used in the demonstration use case tables below.

**Table 1 - Authentication Status Codes**

+----------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Activity | Description                                                            | Examples                                                                                                                                                                 |
+==========+========================================================================+==========================================================================================================================================================================+
| A+       | Authentication successful                                              | All provided credentials matched and verified                                                                                                                            |
+----------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| A-       | Authentication not successful                                          | One or more credentials were not verified such as password failure, multifactor authentication (MFA) failure, account does not exist, account blocked, suspicions raised |
+----------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RA+      | Successful re-authentication of a previously successful authentication | All provided credentials matched                                                                                                                                         |
+----------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| RA-      | Failed re-authentication of a previously successful authentication     | One or more credentials were not verified such as password failure, MFA failure, account was deleted and is no longer valid, account blocked, suspicious activity        |
+----------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| A        | Actively authenticated                                                 | Previously authenticated and no need for re-authentication yet                                                                                                           |
+----------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ---      | Not authenticated yet                                                  |                                                                                                                                                                          |
+----------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

General Configurations
----------------------

This section focuses on the configurations and specifications used within the demonstration use cases.

Access Level
~~~~~~~~~~~~

Table 2 defines the access levels used in the demonstration scenarios. An *access level* specifies a set of available actions or access allowed to a subject. Downgrading an access level means the access level will be replaced by the new downgraded access level. For example, if a subject with access level “Full Access” gets downgraded to access level “Limited Access,” this means the subject only has access to resources and/or functions that require at least “Limited Access.” Similarly, if a subject with access level “Limited Access” gets downgraded, the subject will have no further access to anything. Downgraded access levels can be reversed to their original state.

**Table 2 - Access Levels**

+----------------+------------------+----------------------------------------------------------------------------------------------+
| Access Level   | Can Downgrade to | Description of Access Level                                                                  |
+================+==================+==============================================================================================+
| Full Access    | Limited Access   | This allows the subject to use **all functions** available on the selected resource.         |
+----------------+------------------+----------------------------------------------------------------------------------------------+
| Limited Access | None             | This allows the subject to use **a subset of functions** available on the selected resource. |
+----------------+------------------+----------------------------------------------------------------------------------------------+
| None           | None             | No access                                                                                    |
+----------------+------------------+----------------------------------------------------------------------------------------------+

Access Profiles
~~~~~~~~~~~~~~~

Table 3 defines the access levels used in the demonstration scenarios. Access profiles provide the configuration and maximum access level that can be used. Access levels within the profile can be downgraded to the next lower level when the demonstration directs the operator to limit the access.

**Table 3 - Access Profiles**

+----------------+------------------------------------------+--------------------------------------------------------------------------------------------------+
| Access Profile | Maximum Access Level                     | Description                                                                                      |
+================+==========================================+==================================================================================================+
| P_FULL         | Full Access                              | This provides the capability to access all capabilities of each available resource.              |
+----------------+------------------------------------------+--------------------------------------------------------------------------------------------------+
| P_LIMITED      | Limited Access                           | This provides the capability to select a limited set of capabilities by the available resources. |
+----------------+------------------------------------------+--------------------------------------------------------------------------------------------------+
| P_NONE         | none                                     | No access                                                                                        |
+----------------+------------------------------------------+--------------------------------------------------------------------------------------------------+

Resources and Capabilities 
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Table 4 defines the resources and capabilities used in the demonstration scenarios. Resources (RSS) and capabilities (CAP) specify items and actions used within the demonstrations. Access to them requires a minimum access level. For convenience, the *Access Profile* column lists the access profiles that will provide access to the given resource or capability. The *Example* column provides suggestions regarding resources and capabilities that the access level could be representing.

**Table 4 - Resources and Capabilities**

+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| Component | Type       | Minimum                         | Access Profile                        | Example                                             |
|           |            | Access Level                    |                                       |                                                     |
+===========+============+=================================+=======================================+=====================================================+
| RSS1      | Resource   | Full Access                     | P_FULL                                | GitLab only accessible by P_FULL                    |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| RSS2      | Resource   | Limited Access                  | P_FULL, P_LIMITED                     | File server                                         |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
|           |            |                                 |                                       |                                                     |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| CAP1-RSS1 | Capability | Full Access                     | P_FULL                                | Create and access repositories                      |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| CAP2-RSS1 | Capability | Full Access                     | P_FULL                                | Access repositories                                 |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
|           |            |                                 |                                       |                                                     |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| CAP1-RSS2 | Capability | Full Access                     | P_FULL                                | Read and write access                               |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| CAP2-RSS2 | Capability | Limited Access                  | P_FULL, P_LIMITED                     | Read-only access to all or limited part of resource |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
|           |            |                                 |                                       |                                                     |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| URL1      | Resource   | Full Access                     | P_FULL                                | https://www.nccoe.nist.gov                          |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+
| URL2      | Resource   | Limited Access                  | P_FULL, P_LIMITED                     | https://www.nist.gov                                |
+-----------+------------+---------------------------------+---------------------------------------+-----------------------------------------------------+

User Profiles
~~~~~~~~~~~~~

Table 5 contains the different user profiles (UP) used with an enterprise-ID (UP-E) or other-ID (UP-O) for the demonstrations. Some profiles might be redundant (e.g., UP-E1 and UP-E4). This is done to help keep the profile configuration simple because the demonstrations that the redundant profiles are used in utilize different resources. The Downgrade Trigger Examples are situations where the access would be restricted from the original Access Profile to remove some of the capabilities. For example, moving UP-E1 from P_FULL to a temporary P_LIMITED for the scenario.

**Table 5 - User Profiles**

+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
| User Profile | Access Profile                        | Resource                                   | Status                 | Downgrade Trigger Examples                                                  |
+==============+=======================================+============================================+========================+=============================================================================+
| UP-E1        | P_FULL                                | RSS1                                       | Active                 | Endpoint falls out of compliance                                            |
|              |                                       |                                            |                        |                                                                             |
| UP-O1        |                                       | RSS2                                       |                        |                                                                             |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
| UP-E2        | P_LIMITED                             | RSS2                                       | Active                 | Endpoint falls out of compliance                                            |
|              |                                       |                                            |                        |                                                                             |
| UP-O2        |                                       |                                            |                        |                                                                             |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
| UP-E3        | none                                  | none                                       | Deactivated or deleted |                                                                             |
|              |                                       |                                            |                        |                                                                             |
| UP-O3        |                                       |                                            |                        |                                                                             |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
|              |                                       |                                            |                        |                                                                             |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
| UP-E4        | P_FULL                                | URL1                                       | Active                 | Endpoint falls out of compliance                                            |
|              |                                       |                                            |                        |                                                                             |
| UP-O4        |                                       | URL2                                       |                        |                                                                             |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
| UP-E5        | P_LIMITED                             | URL1                                       | Active                 | Endpoint falls out of compliance                                            |
|              |                                       |                                            |                        |                                                                             |
| UP-O5        |                                       | URL2                                       |                        | Internet access only during specific times                                  |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
|              |                                       |                                            |                        |                                                                             |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
| UP-E6        | P_FULL                                | RSS1                                       | Active                 | Detection of multiple logins from different locations                       |
|              |                                       |                                            |                        |                                                                             |
| UP-O6        |                                       |                                            |                        | Detection of second login from enterprise-owned device not assigned to user |
|              |                                       |                                            |                        |                                                                             |
|              |                                       |                                            |                        | Detection of login from location outside of the country                     |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+
| UP-E7        | P_FULL                                | RSS1                                       | Active                 | Account reported compromised                                                |
|              |                                       |                                            |                        |                                                                             |
| UP-O7        |                                       |                                            |                        | Using old MFA method (stolen PIV card)                                      |
+--------------+---------------------------------------+--------------------------------------------+------------------------+-----------------------------------------------------------------------------+

Demonstration Methodology
-------------------------

We are leveraging two types of demonstration methodologies: manual and automated. Demonstrations that require human interaction (e.g., user performs MFA) must be performed manually. Demonstrations that do not require human interaction can be performed either manually or automated, or both. It is also possible to perform demonstrations in a hybrid manner in which the early part of a demonstration that requires user authentication is performed manually, followed by an automated portion of the demonstration. This approach can be helpful for demonstrations that are complicated, yet nevertheless require human interaction.

We deployed Mandiant Security Validation (MSV) throughout the project's laboratory environment to enable us to monitor and verify various security characteristics of the builds. MSV automates a testing program that provides visibility and evidence of how security controls are performing by emulating attackers to safely process advanced cyberattack security content within production environments. It is designed so defenses respond to it as if an attack is taking place within the enterprise. Virtual machines (VMs) that are intended to operate as actors are deployed on each of the subnetworks in each of the enterprises. These actors can be used to initiate various actions for the purpose of verifying that security controls are working to support the objectives of zero trust. We also deployed three VMs that operate as directors, two of which function as applications within enterprise 1 and enterprise 3 that are used by those enterprises to monitor and audit their own traffic, and one of which is an overarching director that is located within the management and orchestration domain and used by the project team to demonstrate and audit operations that span multiple enterprises. (See :ref:`ZTA Laboratory Physical Architecture`.)

This setup enabled the following dual-purpose MSV deployment:

1. **A typical MSV deployment, in which each enterprise deploys MSV as an application within its own enterprise and uses it for self-auditing and testing.** Each enterprise deploys a director and multiple actors that function as applications within the enterprise, enabling the enterprise to monitor and test its own enterprise security capabilities, verifying the protections it receives from the ZTA and its ability to operate as expected. In this capacity, MSV is treated just like any other application deployed within that enterprise. The components may be protected by PEPs according to enterprise policies, and directors and actors exchange traffic over the same data communications paths as other enterprise applications. Firewalls and policies within the ZTA must be configured to permit the communications that the MSV components send and receive, including traffic that is sent between actors and the director to control the actions that are performed to test various security controls.

2. **The NCCoE project team, as testers, use MSV to monitor and audit enterprise and inter-enterprise actions.** The project team deploys an overarching director and a management backchannel connecting that director to all actors throughout the laboratory environment. This overarching director is used as a tool to verify the security controls provided by each of the ZTAs in the various enterprises and to monitor and audit inter-enterprise interactions. In this capacity, MSV is not functioning as an application deployed or controlled by the enterprises, but rather as a tool being used to monitor and audit enterprise and inter-enterprise activity. Communications between the actors and this overarching director occur on a management channel that is separate from the data networks in each of the enterprises. Using a separate backchannel ensures that the tool being used to monitor and verify the various ZTA architectures is not itself impacting those architectures. Enabling the overarching MSV director to control the actor VMs via a backchannel requires each of the actor VMs to have two network interface cards (NICs), one for enterprise data and one for MSV tool interoperation. Use of a separate backchannel ensures that enterprise ZTA policies and firewalls don't need to be modified to accommodate the overarching MSV testing by permitting traffic between the overarching director and the actors that would not normally be expected to transit any of the enterprise networks. Such policy and firewall modification would have been undesirable and would, in effect, have amounted to unauthorized channels into the enterprise networks.

An MSV protective theater was also created in the lab. This is a virtualized system that allows destructive actions to be tested without adversely impacting the enterprise deployments themselves. For example, to understand the effects that malware might have on a specific system in one of the enterprises, that system could be imported into the protective theater and infected with malware to test what the destructive effects of the malware might be.
