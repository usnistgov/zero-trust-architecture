Functional Demonstration Result Summaries
============================================

.. include:: /_publication_note.rst

This section provides a summary of the demonstration results for each of the builds that was implemented as part of this project. The summary results are organized according to the build phases that were defined in :ref:`Architecture and Builds`. The ZTA functionality demonstrated in each build performed as expected. Detailed results for each of the builds are provided in :ref:`EIG Crawl Phase Demonstration Results`, :ref:`EIG Run Phase Demonstration Results`, and :ref:`SDP, Microsegmentation, and SASE Phase Demonstration Results`. For each build, summary results for use cases A-H are provided.

EIG Crawl Phase Summary Demonstration Results
---------------------------------------------

This section lists the summary demonstration results for each of the builds that was implemented as part of the EIG crawl phase: E1B1, E2B1, and E3B1. Cloud-based scenarios, and more sophisticated scenarios such as Stolen Credential, Just-in-Time Access Privileges, Enterprise-ID Step-Up Authentication, Federated-ID Access, Confidence Level, and Service-Service Interactions scenarios were decided to be out of scope for the EIG crawl phase. Only E1B1 has a branch office; E2B1 and E3B1 do not.

Enterprise 1 Build 1 (E1B1) - EIG Crawl - Okta Identity Cloud and Ivanti Access ZSO as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have IaaS, PaaS, or SaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description**: This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets  - Not demonstrated due to lack of capability. There is no network-level enforcement present in this build.

-  Reauthentication of identified assets  - Not demonstrated due to lack of capability.

-  Discovery of transaction flows  - Demonstrated visibility of authentication and resource access attempts via Okta logs.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem) in accordance with policy via Okta Identity Cloud.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  Internet access enforcement for Enterprise and Contractor Users on an enterprise endpoint or BYOD  - Out of scope for EIG crawl phase.

-  Stolen credential using an enterprise endpoint or BYOD  - Out of scope for EIG crawl phase.

-  Just-in-Time Access Privileges  - Out of scope for EIG crawl phase.

-  Enterprise-ID Step-Up Authentication  - Out of scope for EIG crawl phase.

-  This build did not have the capability to verify resource compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for EIG crawl phase.

**Use Case D: Other-ID Access**  - Results are the same as for use case B. Users with Other-ID Access (e.g., a contractor) have authorized access to resources based on need, so results for these users are no different than the results for users with Enterprise-ID Access.

**Use Case E: Guest: No-ID Access**  - Out of scope for EIG crawl phase.

**Use Case F: Confidence Level**  - Out of scope for EIG crawl phase.

**Use Case G: Service-Service Interactions**  - Out of scope for EIG crawl phase.

**Use Case H: Data Level Security**  - Out of scope for EIG crawl phase.

Enterprise 2 Build 1 (E2B1) - EIG Crawl - Ping Identity Ping Federate as PE Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have IaaS, PaaS, or SaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description**: This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity

-  Discovery and authentication of endpoint assets  - Not demonstrated due to lack of capability. There is no network-level enforcement present in this build.

-  Reauthentication of identified assets  - Not demonstrated due to lack of capability.

-  Discovery of transaction flows  - Demonstrated visibility of authentication and resource access attempts via Ping Federate and Cisco Duo.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem) in accordance with policy via Ping Federate.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  Internet access enforcement for Enterprise and Contractor users on an enterprise endpoint or BYOD  - Out of scope for EIG crawl phase.

-  Stolen credential using an enterprise endpoint or BYOD  - Out of scope for EIG crawl phase.

-  Just-in-Time Access Privileges  - Out of scope for EIG crawl phase.

-  Enterprise-ID Step-Up Authentication  - Out of scope for EIG crawl phase.

-  This build did not have the capability to verify resource compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for EIG crawl phase.

**Use Case D: Other-ID Access**  - Results are the same as for use case B. Users with Other-ID Access (e.g., a contractor) have authorized access to resources based on need, so results for these users are no different than the results for users with Enterprise-ID Access.

**Use Case E: Guest: No-ID Access**  - Out of scope for EIG crawl phase.

**Use Case F: Confidence Level**  - Out of scope for EIG crawl phase.

**Use Case G: Service-Service Interactions**  - Out of scope for EIG crawl phase.

**Use Case H: Data Level Security**  - Out of scope for EIG crawl phase.

Enterprise 3 Build 1 (E3B1) - EIG Crawl - Azure AD Conditional Access (later renamed *Entra Conditional Access*) as PE Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have IaaS or PaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description**: This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets  - Not demonstrated due to lack of capability. There is no network-level enforcement present in this build.

-  Reauthentication of identified assets  - Not demonstrated due to lack of capability.

-  Discovery of transaction flows  - Demonstrated visibility of authentication and resource access attempts using Azure AD. Also, Azure AD audit logs that show activities were captured.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem) in accordance with policy via Azure AD Conditional Access.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  Internet access enforcement for Enterprise and Contractor Users on an enterprise endpoint or BYOD  - Out of scope for EIG crawl phase.

-  Stolen credential using an enterprise endpoint or BYOD  - Out of scope for EIG crawl phase.

-  Just-in-Time Access Privileges  - Out of scope for EIG crawl phase.

-  Enterprise-ID Step-Up Authentication  - Out of scope for EIG crawl phase.

-  This build did not have the capability to verify resource compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for EIG crawl phase.

**Use Case D: Other-ID Access**  - Results are the same as for use case B. Users with Other-ID Access (e.g., a contractor) have authorized access to resources based on need, so results for these users are no different than the results for users with Enterprise-ID Access.

**Use Case E: Guest: No-ID Access**  - Out of scope for EIG crawl phase.

**Use Case F: Confidence Level**  - Out of scope for EIG crawl phase.

**Use Case G: Service-Service Interactions**  - Out of scope for EIG crawl phase.

**Use Case H: Data Level Security**  - Out of scope for EIG crawl phase.

EIG Run Phase Summary Demonstration Results
-------------------------------------------

This section lists the summary demonstration results for each of the builds that was implemented as part of the EIG run phase: E1B2, E3B2, and E4B3. Only E1B2 has a branch office; E3B2 and E4B3 do not. More sophisticated scenarios such as Just-in-Time Access Privileges, Enterprise-ID Step-Up Authentication, Federated-ID Access, Confidence Level, and Service-Service Interactions scenarios were decided to be out of scope for the EIG run phase for E1B2 and E3B2.

Enterprise 1 Build 2 (E1B2) - EIG Run - Zscaler ZPA Central Authority (CA) as PE Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have SaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description**: This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets  - Not demonstrated due to lack of capability. There is no network-level enforcement present in this build.

-  Reauthentication of identified assets  - Not demonstrated due to lack of capability.

-  Discovery of transaction flows  - Demonstrated visibility of authentication and resource access attempts via Okta logs and Zscaler Private Access (ZPA).

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, Linux, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via ZPA.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources accordance with policy via ZIA.

-  Stolen credential using an enterprise endpoint or BYOD  - Zscaler does not detect a hostile request if all credentials are correct.

-  Just-in-Time Access Privileges  - Out of scope for EIG run phase.

-  Enterprise-ID Step-Up Authentication  - Out of scope for EIG run phase.

-  This build did not have the capability to verify resource compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for EIG run phase.

**Use Case D: Other-ID Access**  - Results are the same as for use case B. Users with Other-ID Access (e.g., a contractor) have authorized access to resources based on need, so results for these users are no different than the results for users with Enterprise-ID Access.

**Use Case E: Guest: No-ID Access**  - Guest requests public internet access. Zscaler Internet Access (ZIA) is configured to allow access to the internet if the device is unmanaged (i.e., No-ID).

**Use Case F: Confidence Level**  - Out of scope for EIG run phase. This use case was demonstrated in a later iteration of this build, E1B3.

**Use Case G: Service-Service Interactions**  - Out of scope for EIG run phase.

**Use Case H: Data Level Security**  - Out of scope for EIG run phase.

Enterprise 3 Build 2 (E3B2) - EIG Run - Microsoft Azure AD Conditional Access (later renamed *Entra Conditional Access*), Microsoft Intune, Forescout eyeControl, and Forescout eyeExtend as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build's summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description**: This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity

-  Discovery and authentication of endpoint assets was successfully demonstrated. Resources and endpoints were granted access to the network and if applicable, limited to a specific subnet or resource set based on Forescout policy. These policies were enforced by a Palo Alto Next-Generation Firewall (NGFW) and Cisco switch. Due to the location of these policy enforcement points (PEPs), unauthenticated endpoints were restricted to the local subnet in accordance with Forescout policy.

   -  Network assets were discovered by Forescout via both passive and active detection.

-  Reauthentication of identified assets was also successfully demonstrated using Forescout and Microsoft Intune.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  Azure AD captures sign-in logs to SaaS applications, PaaS, IaaS resources, and on-prem applications.

   -  Azure AD audit logs are captured that show activity including changes to cloud resources in the Azure tenant.

   -  Forescout captures sign-in and audit logs and network traffic for on-premises components.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via Azure AD Conditional Access.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources in accordance with policy via Defender for Cloud Apps and Defender for Endpoint. Note that the product name *Defender for Cloud Apps* was later changed to *Defender for Apps*)

   -  Policies within Defender for Cloud Apps were set up to allow, block, or limit access to resources.

   -  The build demonstrated that documents with sensitive data such as credit cards could be viewed but not downloaded.

-  Stolen credential using an enterprise endpoint or BYOD  - Azure AD does not detect a hostile request if all credentials are correct.

-  Just-in-Time Access Privileges  - Out of scope for EIG run phase.

-  Enterprise-ID Step-Up Authentication  - Out of scope for EIG run phase.

-  This build did not have the capability to verify chosen resource (e.g., GitLab) compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for EIG run phase.

**Use Case D: Other-ID Access**  - Results are the same as for use case B. Users with Other-ID Access (e.g., a contractor) have authorized access to resources based on need, so results for these users are no different than the results for users with Enterprise-ID Access.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Forescout was able to provide Internet access to unauthenticated guest devices connecting to a segmented portion of the enterprise network.

**Use Case F: Confidence Level**  - Out of scope for EIG run phase. This use case was demonstrated in a later iteration of this build, E3B3.

**Use Case G: Service-Service Interactions**  - Out of scope for EIG run phase. This use case was demonstrated in a later iteration of this build, E3B3.

**Use Case H: Data Level Security**  - Out of scope for EIG run phase.

Enterprise 4 Build 3 (E4B3) - EIG Run - IBM Security Verify as PE Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have SaaS or PaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description**: This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of managed endpoint assets were successfully demonstrated, based on IBM Security MaaS360 policy configuration.

   -  This build also demonstrated the capability to limit or reduce user access levels in certain scenarios.

   -  Resource authentication and limited access to the network were not demonstrated because IBM considers them out of scope for their products. Other technologies should be used to perform these functions.

-  Reauthentication of identified assets was also successfully demonstrated using IBM Security MaaS360.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  IBM Verify captures sign-in logs to cloud resources and on-prem applications.

   -  IBM QRadar receives and parses sign-in logs for visibility.

   -  IBM considers API call visibility out of scope for their products. Other technologies should be used to perform this function.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via IBM Verify.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

   -  We were unable to invalidate MaaS360 certificates to complete some scenarios, including scenarios that require the endpoint to fail authentication.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources in accordance with policy via the IBM Secure Browser.

   -  Policies within IBM MaaS360 were set up to allow, block, or limit access to resources.

   -  MaaS360 disables resources like the Secure Browser outside of policy hours, and some scenarios related to this were not completed.

   -  The IBM Secure Browser is only available on mobile devices.

-  Stolen credential scenarios using an enterprise endpoint or BYOD were completed successfully.

   -  We were unable to invalidate MaaS360 certificates or duplicate MaaS360 certificates to another mobile device to complete some scenarios, including stolen credential scenarios and scenarios that require the endpoint to fail authentication. IBM Security MaaS360 does not detect a hostile request if all credentials are correct. 

-  Just-in-Time (JIT) Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

-  Administrators can manually add/revoke these JIT access privileges for users.

-  JIT access privileges with automation were not tested and require integration with other zero trust tools that have the capabilities to manage access for users.

   -  Enterprise-ID Step-Up Authentication  - The build did not include the capability to prompt for re-authentication in the middle of an active session with the chosen resources (e.g., GitLab).

   -  This build did not have the capability to verify resource compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for EIG run phase.

**Use Case D: Other-ID Access**  - Results are the same as for use case B. Users with Other-ID Access (e.g., a contractor) have authorized access to resources based on need, so results for these users are no different than the results for users with Enterprise-ID Access.

**Use Case E: Guest: No-ID Access**  - IBM considers Guest (No-ID) access out of scope for their products. Other technologies should be used to perform this function.

**Use Case F: Confidence Level**

**Description**: This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users that fail re-authentication lose access to resources. With successful re-authentication, access is maintained.

   -  Users that are not able to reauthenticate successfully to IBM Verify immediately lose access to resources.

-  Requesting endpoint reauthentication failure during active session use case was not demonstrated.

   -  Due to security of MaaS360 certificate storage, we were unable to invalidate the endpoint's credentials to produce an unsuccessful endpoint authentication.

-  Resource authentication is out of scope for IBM; other technologies should be used.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  MaaS360 determines the compliance state of devices that it manages.

   -  Devices lose access to resources and internet sites defined in policy once QRadar and CloudPak 4 Security are made aware of their noncompliant status.

   -  Devices that return to a compliant state have their access restored.

-  User sessions violating data use policies are blocked or terminated.

   -  IBM Guardium Data Security was configured to alert QRadar of access to sensitive database tables and successfully terminated active sessions to a monitored database.

   -  QRadar and CloudPak 4 Security were configured to remove previously authorized user access to authorized resources after receiving alerts from IBM Guardium Data Security.

-  User access for accounts violating internet use policy was terminated and blocked.

   -  On accessing a known bad URL with MaaS360 Secure Browser on a mobile device, access to GitLab was revoked via CloudPak for Security, and IBM Verify disabled the user's account.

-  User sessions and devices attempting to access unauthorized resources or bad URLs were blocked or terminated.

   -   IBM Verify was configured to alert QRadar of unauthorized access requests.

   -  QRadar and CloudPak 4 Security were configured to remove previously authorized user access to authorized resources after receiving alerts from IBM Verify.

   -  User's follow-up access requests for authorized resources were denied.

-  ID denied/terminated access due to suspicious endpoint use case was not demonstrated.

   -  IBM considers suspicious activity/network monitoring out of scope for their product. Other technologies should be used for this use case.

**Use Case G: Service-Service Interactions**  - Out of scope for EIG run phase. IBM considers service-to-service use cases out of scope for their product. Other technologies should be used for this use case.

**Use Case H: Data Level Security**

Description: This use case covers subject access requests to data with different levels of classification.

-  Access to data based on identity attributes  - Users accessing data resources are allowed or denied access to sensitive data (on-prem and cloud) based on user identity/attributes in accordance with policy via IBM Guardium.

-  Access to data based on requesting endpoint  - Capability was not included in this build.

-  Internet access restricted when accessing data with high classification  - Capability was not included in this build.

-  Requestor challenged to re-authenticate when accessing data with high classification  - Capability was not included in this build.

-  User temporarily granted access privileges to data with high classification  - Capability was not included in this build.

-  Certain operations can be prevented based on subject endpoint, location, or another factor  - Capability was not included in this build.

-  Extra protection for highly classified data when stored on an endpoint  - Capability was not included in this build.

SDP, Microsegmentation, and SASE Phase Summary Demonstration Results
--------------------------------------------------------------------

This section lists the summary demonstration results for each of the builds that was implemented as part of the Software-Defined Perimeter (SDP), Microsegmentation, and SASE phase.

Enterprise 1 Build 3 (E1B3) - SDP - Zscaler ZPA CA as PE Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

E1B3 is very similar to E1B2. They use the same products and technologies and have the same architecture, but are configured differently with respect to timeouts and policies. Consequently, the results of use Cases A, B (1-6), C, D (1-6), and E were the same for build E1B3 as they were for E1B2. Summary results for other use cases demonstrated with E1B3 are as follows:

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  Just-in-Time Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  A manual process was used to demonstrate providing users with additional privileges to resources.

   -  Integration with other products can be used to automate just-in-time privileges. However, those products were not part of this build.

-  Enterprise-ID Step-Up Authentication  - Both Enterprise and Contractor Users are prompted for additional factor authentication when attempting to access sensitive resources.

   -  Step-up authentication is available through an enhancement request to upgrade ZPA. However, this enhancement was not available during the time of this build.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users successfully authenticate and reauthenticate to Zscaler. Once authenticated, access to resources is available based on policies.

   -  Once the authentication time period expires, user cannot access resources. If reauthentication fails, the user loses access to resources.

-  Resource authentication is out of scope for Zscaler; other technologies should be used to perform this function.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  Zscaler checks endpoint compliance prior to allowing access. Endpoint compliance is checked periodically.

-  The ability to monitor and detect violations of data use policies was not demonstrated.

   -  This build was not used to demonstrate that user sessions violating data use policies are blocked or terminated because the tool that can provide this capability, Cloud Browser Isolation (CBI), was not available during the time of this build.

-  User sessions and devices attempting to access malicious sites were blocked.

   -  Internet use policy: ZIA policies denied access to malicious internet resources and ZIA displayed the access denied message on the browser.

-  User sessions and devices attempting to access unauthorized resources were blocked.

   -  Policies configured in ZPA and ZIA dictated what resources a user could access. User access to resources were evaluated on an individual basis based on ZIA and ZPA policies.

-  This build was not used to demonstrate that an ID is denied/terminated access due to suspicious endpoint because the tool that can provide this capability, Zscaler Deception, was not available during the time of this build.

**Use Case G: Service-to-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Service-to-Service use cases were not demonstrated because the tool that can provide this capability, Zscaler for Workloads, was not available during the time of this build.

**Use Case H: Data Level Security**  - Out of scope for this phase.

Enterprise 2 Build 3 (E2B3) - Microsegmentation - Cisco ISE, Cisco Secure Workload, and Ping Identity Ping Federate as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have IaaS, SaaS, or PaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets were successfully demonstrated.

   -  Resources and endpoints were discovered, authenticated, granted access to the network and, if applicable, limited to a specific subnet or resource set based on Cisco Identity Services Engine (ISE) policy. These policies were enforced by a Palo Alto NGFW, Cisco Switch, or Cisco Access Point.

   -  Cisco Secure Workload (CSW) enforces resource access policies. CSW does not verify resource compliance.

-  Reauthentication of identified assets was also successfully demonstrated using Cisco ISE policy configuration.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  Cisco ISE captured sign-in logs to on-prem applications.

   -  Logs for resources are provided by CSW.

   -  IBM QRadar received logs from ISE as well as other components in the build.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access** 

**Description**: This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, Linux, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem) in accordance with policy via Cisco ISE and Ping Federate.

   -  The policy engines can differentiate between employees and contractors and provide different access permissions to each user type.

-  For this build, although Cisco ISE can be leveraged to deny-list URLs, Cisco recommends using a web filtering tool to control access to internet resources.

-  Stolen credential using an enterprise endpoint or BYOD  - Cisco ISE does not detect a hostile request if all credentials are correct. 

-  Just-in-Time Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  Policies are updated within ISE to allow specific access.

-  Enterprise-ID Step-Up Authentication  - Both Enterprise and Contractor Users are prompted for additional factor authentication when attempting to access sensitive resources.

   -  Cisco ISE does not provide an authentication mechanism to authenticate to the resource. However, a policy must be updated to allow the user and endpoint to reach the resource via the specific protocol that the resource is using. Therefore, we updated an ISE policy to allow that specific protocol for the user. The user then got reauthenticated and was allowed access.

-  This build did not have the capability to verify resource compliance with policy. CSW information is not relayed to Cisco ISE.

**Use Case C: Federated-ID Access**  - Out of scope for this phase.

**Use Case D: Other-ID Access**  - Results are the same as for use case B. Users with Other-ID Access (e.g., a contractor) have authorized access to resources based on need, so results for these users are no different than the results for users with Enterprise-ID Access.

**Use Case E: Guest: No-ID Access**

**Description:** This use demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Access to the internet is allowed for all guest users.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful reauthentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully to Cisco ISE will immediately lose access to resources.

   -  Initial authentication with Cisco ISE provides user with access to resources per ISE policy. Periodic reauthentication is required, which verifies compliance as well.

-  Resource authentication was not demonstrated. Currently, CSW does not provide information to Cisco ISE.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  Upon login to endpoint device, compliance information is sent to the Cisco ISE and validated before the endpoint gains access to the network. Device compliance is checked periodically.

   -  Devices lose access to resources once the Cisco ISE is made aware of a noncompliant state.

-  The ability to monitor and detect violations for data use policy was demonstrated in the following ways:

   -  Cisco Secure Network Analytics (SNA) was leveraged to create policies to monitor violations of data use. Cisco Secure Endpoint also informed ISE of threats to the endpoints.

   -  Information from SNA was relayed to Cisco ISE to revoke user access.

-  User sessions and devices attempting to access unauthorized resources and malicious sites are blocked.

   -  Cisco SNA has native policies to detect malicious traffic such as command and control, Tor, bogon sites, etc. Specific URLs can be blocked, but Cisco recommends using a web filtering tool instead of SNA or ISE.

   -  User sessions and devices attempting to access unauthorized resources were blocked by Cisco ISE once the access attempt information was detected by SNA and relayed to ISE.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  Cisco Secure Endpoint detects threats and malicious behavior on endpoints and passes the information to Cisco ISE. Cisco ISE applies policies to quarantine the endpoints until malicious behavior is remediated.

-  Enterprise can deny access to resources when users are attempting access from suspicious endpoints.

   -  SNA policies were able to detect suspicious activities by endpoints. That information was passed to Cisco ISE, which quarantined the endpoint.

**Use Case G: Service-to-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Cisco CSW agents were deployed on resources and policies were applied to the resource to allow or deny API calls. A resource without the right authorizations to communicate with another resource was denied.

   -  CSW continuously monitors the communications in and out of a subject and develops policies based on that information.

-  Service-to-endpoint communications were demonstrated by using the CSW agents on resources.

-  Communication was successful by applying policy to allow access from the service to the endpoint.

**Use Case H: Data Level Security**  - Out of scope for this phase.

Enterprise 3 Build 3 (E3B3) - SDP and Microsegmentation - Microsoft Azure AD Conditional Access (later renamed *Entra Conditional Access*), Microsoft Intune, Microsoft Sentinel, Forescout eyeControl, and Forescout eyeExtend as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A summary of this build's results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets were successfully demonstrated. Resources and endpoints were granted access to the network and if applicable, limited to a specific subnet or resource set based on Forescout policy. These policies were enforced by a Palo Alto NGFW and Cisco Switch. Due to the location of these PEPs, unauthenticated endpoints were restricted to the local subnet in accordance with Forescout policy.

   -  Network assets were discovered by Forescout via both passive and active detection.

-  Reauthentication of identified assets was also successfully demonstrated using Forescout and Microsoft Intune.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  Azure AD captures sign-in logs to SaaS applications, PaaS, IaaS resources, and on-prem applications.

   -  Azure AD audit logs are captured that show activity including changes to cloud resources in the Azure tenant.

   -  Forescout captures sign-in and audit logs and network traffic for on-premises components.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via Azure AD Conditional Access.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources (on-prem and cloud) in accordance with policy via Defender for Cloud Apps and Defender for Endpoint. Note that the product name *Defender for Cloud Apps* was later changed to *Defender for Apps*).

   -  Policies within Defender for Cloud Apps were set up to allow, block, or limit access to resources.

   -  The build demonstrated that documents with sensitive data such as credit cards could be viewed but not downloaded.

-  Stolen credential using an enterprise endpoint or BYOD  - Azure AD does not detect a hostile request if all credentials are correct.

-  Just-in-Time (JIT) Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  JIT for VM Access

      -  Azure has a just-in-time feature capability for VM access that enables a user to access an Azure VM with SSH or RDP for a limited time when requested.

      -  Defender for Cloud checks that the user has the appropriate Azure role, then inserts allow rules from a specific user's IP address into the network security groups and Azure Firewall.

      -  This only occurs at the time that the user requests access to the VMs.

   -  JIT with Privileged Identity Management (PIM)

      -  PIM is used to provide an additional layer of authentication and authorization before requesting users are granted access to privileged Azure AD roles for a limited time.

      -  Once granted, a user gains elevated Azure AD administration privileges for a limited time.

      -  For this build, PIM only works within the Azure environment and does not extend to the on-prem infrastructure.

-  Enterprise-ID Step-Up Authentication  - Both Enterprise and Contractor Users are prompted for additional factor authentication when attempting to access sensitive resources.

   -  Azure AD Conditional Access provides additional authentication when a user attempts to access a portion of a site or a document with a sensitive label.

   -  An example of a sensitive site is a SharePoint site with a sensitive label.

   -  Conditional Access would prompt the user for additional authentication prior to allowing access.

-  This build did not have the capability to verify chosen resource (e.g., GitLab) compliance with policy.

**Use Case C: Federated-ID Access**

**Description:** These use cases demonstrate federated user-id access to enterprise 1 resources and the internet based on successfully achieving user and device security preconditions. For this demonstration, enterprise 3 users access enterprise 1 resources and the internet using enterprise 1 devices or BYOD.

-  An enterprise 3 federated user using an enterprise 1 laptop can access resources in enterprise 1 when on-premises, at the branch office, or remote.

   -  Users are authenticated using enterprise 3 credentials via the integration of the enterprise 1 and enterprise 3 identity providers (IdPs).

   -  Policies are applied to users and endpoints to allow or deny access to enterprise resources.

   -  Limited resource access can be achieved by applying policies to a specific set of users from enterprise 3.

-  An enterprise 3 federated user using an enterprise 1 laptop can access the internet when on-premises, at the branch office, or remote.

   -  Web filtering policies are enforced by the enterprise 1 PEPs when a federated user accesses the internet using an enterprise 1 device.

-  An enterprise 3 federated user using a BYOD laptop can access the internet when on-premises or at the branch office. When the user is remote, enterprise 1 policies do not apply.

   -  Web filtering policies are enforced by the enterprise 1 PEPs when a federated user accesses the internet using a BYOD device.

-  Stolen credentials are treated the same way for federated users and enterprise users.

   -  If user credentials are stolen and not reported, a malicious user will have access.

   -  Once user credentials/device is reported stolen, policies are applied to deny those users and devices. Users will need to update their credentials to regain access.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Forescout was able to provide Internet access to unauthenticated guest devices connecting to a segmented portion of the enterprise network.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful re-authentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully to Microsoft Intune Mobile Device Management (MDM) will be offboarded and immediately lose access to resources. Periodic reauthentication is required.

   -  Azure AD Conditional Access was configured to only allow connections from Intune compliant devices.

-  Resource authentication was not demonstrated. It could not be performed by the products in this build.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  Microsoft Intune determines, and then reports to Azure AD, the compliance state of devices that it manages. Endpoint compliance must be validated prior to allowing access. Endpoint compliance is checked periodically.

   -  Devices lose access to resources once Azure AD is made aware of a noncompliant state.

-  The ability to monitor and detect violations of data use policies was not demonstrated due to time limitations.

-  User sessions and devices attempting to access unauthorized resources and malicious sites were blocked or the sessions were terminated.

   -  Defender for Cloud Apps was configured to label sites as trusted or untrusted.

   -  If a site was untrusted, Defender for Endpoint enforced Defender for Cloud Apps Policy and prevented the user from visiting the site by blocking it.

   -  Additionally, Azure AD Conditional Access was configured to block users from accessing resources without proper authorization.

   -  Microsoft Sentinel was successfully configured to send API requests to Azure AD to terminate active sessions and disable user accounts when alerts indicating malicious events (e.g., attempts to access known bad internet sites) were received. Session termination was successfully tested for Office SaaS apps.

   -  The build did not have the capability to terminate sessions for the chosen on-premises/IaaS resource (e.g., GitLab).

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  Defender for Endpoint was configured as the Endpoint Detection and Response solution to detect and block threats and inform Azure AD via Intune.

   -  Defender for Endpoint has built-in sensors in the Windows platform and utilizes Windows Defender Firewall and Windows Anti-Virus to detect threats.

-  Enterprise can deny access to resources when users are accessing from suspicious endpoints.

   -  Once onboarded, devices with Defender for Endpoint detected threats that included malicious script execution, network reconnaissance, and Active Directory reconnaissance. 

   -  Defender for Endpoint categorized the threats, forwarded the alerts to Microsoft 365 Defender, and forwarded the risk information to Intune.

   -  Depending on the risk threshold set, Microsoft Intune changed the endpoint status to noncompliant.

   -  Azure AD received the noncompliant status information and blocked the devices from accessing resources.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Client apps were able to utilize either Azure roles or Azure AD authorizations to make successful API calls to Azure IaaS, PaaS, and Microsoft SaaS apps. Client apps without the right authorizations were denied.

   -  Client applications made API calls to manage an Azure VM, retrieve data managed by Azure AD, and retrieve data from Office365 mail and Microsoft Sentinel.

   -  Client apps without the right API permissions were denied.

-  Client apps hosted in Azure IaaS or Azure PaaS were able to make successful API calls to Azure IaaS, Azure PaaS, and Microsoft SaaS apps. Apps without the right authorizations were denied.

   -  A client application hosted/stored in an Azure VM or an Azure function was used to make successful API calls to manage an Azure VM, retrieve Azure AD-managed data, and retrieve data from Microsoft Sentinel and Office365 mail.

-  Client applications were not able to make API calls to the chosen on-prem/IaaS application (e.g., GitLab) because the API authorization was issued by an external authorization provider.

-  For Service to Endpoint use cases:

   -  Intune was used to instruct the endpoint to take certain actions, such as to update itself and restart.

**Use Case H: Data Level Security**

**Description**: This use case covers subject access requests to data with different levels of classification.

-  Access to data based on identity attributes  - Leveraging Azure AD Conditional Access, differing levels of access were assigned to users depending on the classification of data in the cloud.

-  Access to data based on requesting endpoint  - Leveraging Azure AD Conditional Access and Microsoft Intune compliance feeds, differing levels of access were assigned to subjects based on the compliance status of their endpoints. This was only applicable to data resident in the cloud.

-  Internet access restricted when accessing data with high classification  - Leveraging Azure AD Conditional Access, allowed and excluded subject locations were specified. Data was differentiated based on which folder an object resided in. Controls were applicable to data in the cloud.

-  Requestor challenged to re-authenticate when accessing data with high classification  - Azure AD Conditional Access using the authentication context feature triggers MFA for sensitive data in the cloud.

-  User temporarily granted access privileges to data with high classification  - Azure AD Privileged Access Management was used to temporarily elevate subject privileges for a limited time so as to provide access to sensitive data and resources in the cloud.

-  Certain operations can be prevented based on subject endpoint, location, or another factor  - Access controls were applied in SharePoint that prevented the modification and downloading of files.

-  Extra protection for highly classified data when stored on an endpoint  - Encryption was applied to data that was downloaded and required a password for decryption.

-  Although data classification was out of scope for this project, the products used had the ability to classify data. Instead, for these use cases, sensitive data was differentiated from non-sensitive data by having them use different folders.

Enterprise 1 Build 4 (E1B4) - SDP - Appgate SDP Controller as PE Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have SaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets

   -  Appgate was not configured to discover network assets in this build, but can use network/cloud metadata APIs and DNS to discover network assets. For this build, endpoints used the Appgate Client in order to communicate with the Appgate Controller and be authenticated by it.

-  Reauthentication of identified assets  - Appgate requires reauthentication after a configurable period of time.

   -  User must reauthenticate once the authentication period is over. If reauthentication fails, the user does not have access to any resources.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  Appgate captures sign-in events, changes in user/device attributes, and traffic flow logs to on-prem and IaaS resources.

   -  Appgate logs are sent to IBM QRadar.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** This use case demonstrates user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, Linux, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, were allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policies enforced by the Appgate Gateway. Policies were configured with the Appgate Controller.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

   -  Appgate Gateways were deployed on-prem and in the AWS IaaS cloud to protect resources.

   -  Compliance of both the endpoint and resource were checked prior to allowing a user to access that resource.

-  For this build, Appgate did not manage access to internet resources. Appgate can enforce device proxy configuration and route Internet traffic through a web filtering tool to manage internet access, which was not implemented as part of this build.

-  Stolen credential using an enterprise endpoint or BYOD  - Appgate does not detect a hostile request if all credentials are correct. 

   -  Appgate can limit the location (by city, state, or country), number of allowed devices per user, and number of simultaneous logins by a user to prevent use of stolen credentials.

-  Just-in-Time Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  A manual process was used to demonstrate providing users with additional privileges to resources.

   -  Integration with other products can be used to automate just-in-time privileges. However, those products were not part of this build.

-  Enterprise-ID Step-Up Authentication  - Both Enterprise and Contractor Users were prompted for additional factor authentication when attempting to access sensitive resources.

   -  A policy was created within the Appgate Controller to require additional authentication to specific resources that are considered sensitive and need additional protection.

-  When accessing a resource, resource compliance is checked. An Appgate headless client is installed on the resource to provide information to the PE. If resource is not compliant, Appgate client will deny endpoint access to resource.

**Use Case C: Federated-ID Access**  - Out of scope for this phase.

**Use Case E: Guest: No-ID Access**

**Description**: This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Appgate SDP considers this out of scope for their products. Other technologies should be used to perform guest access enforcement.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful reauthentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully to the Appgate Controller will immediately lose access to resources. Device risk and condition-based access is reevaluated every five minutes.

   -  Initial authentication with Appgate controller provides user with access to resources assigned to that user. Periodic reauthentication and MFA or step-up authentication for access to critical resources is required, which verifies compliance as well.

-  Resource reauthentication failed during an active session.

   -  Once Appgate's headless client is authenticated, it periodically reauthenticates automatically using PKI or stored credentials. Compliance checks are also performed periodically per policy. If compliance fails on the resource, a user will lose access within five minutes to the resource. If compliance fails on the endpoint, the user will lose access to all resources.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  Upon login to the Appgate client, compliance information is sent to the Appgate controller and validated before the user can access any resources. Device compliance is checked every five minutes.

   -  Devices lose access to resources immediately when a noncompliant state is detected.

-  The ability to monitor and detect violations of data use policies was not demonstrated. Appgate does not have capabilities to manage data use policies.

-  User sessions and devices attempting to access unauthorized resources are blocked.

   -  Appgate policies determine if a user has access to a resource or not. If there is no policy to allow a user to access a resource and the user requests to reach that resource, the request will not be able to leave the end device or it will be denied by the Appgate Gateway. Appgate will not terminate the user's connection to the Gateway, but it will block access to the unauthorized resource.

   -  Appgate does not control access to internet websites and recommends leveraging a web filtering tool to perform this function.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  Appgate SDP clients perform compliance checks periodically and denies access to resources if compliances fails.

-  Enterprise can deny access to resources when users are accessing from suspicious endpoints.

   -  Appgate does not allow any traffic past the Appgate Gateway if there is no policy to allow that specific access from the user. Logs of these attempts are provided to the SIEM. Note: The SIEM can trigger a security event, which Appgate can consume to further restrict that user's access by deeming the user riskier.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Appgate headless clients are deployed on resources to make successful API calls to other resources (e.g., GitLab). A resource without the correct authorizations to communicate with another resource was denied.

   -  Headless clients were deployed to on-prem and AWS resources to validate successful service-to-service communications.

   -  Use cases for on-prem and AWS IaaS and PaaS were successfully performed.

   -  A SaaS solution was not available for this build.

-  Service-to-service communication between resources located on separate containers was successfully performed.

   -  A Kubernetes cluster was deployed with Appgate sidecar, which enforced policies applied at the namespace level.

-  Service-to-endpoint communications were demonstrated using headless clients installed on resources.

   -  Communication was successful by applying policy to allow access from service to the endpoint.

**Use Case H: Data Level Security**  - Out of scope for this phase.

Enterprise 2 Build 4 (E2B4) - SDP and SASE - Symantec Cloud Secure Web Gateway, Symantec ZTNA, and Symantec Cloud Access Security Broker as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have SaaS target resources. A summary of this build's results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets were successfully demonstrated.

   -  Resources and endpoints were granted access to the network and if applicable, limited to a specific subnet or resource set based on Symantec Endpoint Protection and Symantec Zero Trust Network Access (ZTNA) policy. These policies were enforced by an agent placed on the endpoint and cloud-based services including Symantec ZTNA and Symantec Cloud Secure Web Gateway.

-  Reauthentication of identified assets was successfully demonstrated using the Symantec endpoint agent's connection to the Symantec Cloud Secure Web Gateway.

-  Discovery of transaction flows - Visibility of authentication and resource access attempts was demonstrated.

   -  Symantec ZTNA captures sign-in and individual user action logs to SaaS applications, IaaS resources, and on-prem applications.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** These two use cases demonstrate user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, Linux and mobile device (iOS and Android) endpoints.

   -  Demonstration capability varied between the different platforms. The agent-based approach on Windows successfully completed all scenarios. The agent-based approach on MacOS successfully completed all scenarios with the exception of those involving device compliance. The Linux agent-based approach successfully completed all scenarios with the exception of those involving compliance and internet access, as the Linux agent does not possess the capability to connect to the Symantec Cloud Secure Web Gateway at this time. The mobile devices successfully completed all scenarios with the exception of those involving device compliance.

   -  An agent-less approach was also demonstrated on all of the above platforms using Symantec ZTNA. This method completed all scenarios with the exception of those involving device compliance.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via Symantec ZTNA.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type. This is accomplished through integration with the ICAM (Okta).

   -  The build demonstrated that sensitive data such as credit card information could have access controlled based on policy within Symantec DLP.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources in accordance with policy via Symantec Cloud Secure Web Gateway.

   -  Policies within Symantec Cloud Secure Web Gateway were set up to allow, block, or limit access to internet resources.

-  Stolen credential using an enterprise endpoint or BYOD  - Symantec by Broadcom does not detect a hostile request if all credentials are correct. Symantec by Broadcom is able to revoke unauthorized access once credentials have been reported stolen, and stolen credentials have been revoked. Concurrent session controls are available, and can terminate existing access sessions upon the creation of a new access session.

-  Just-in-Time (JIT) Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  In this build, Just-in-Time privileges can be manually completed to allow a user to access a resource. These policies can be temporary, giving the user access for a limited period of time. Symantec ZTNA provides an API to allow automated just-in-time provisioning, which can be integrated with other tools. One example is their integration with Slack, which allows automated just-in-time provisioning of access to resources in Symantec ZTNA.

-  Enterprise-ID Step-Up Authentication  - Step-up authentication capabilities are not included in this build. However, Symantec CloudSOC can provide step-up authentication when users access SaaS applications.

-  This build did not have the capability to verify chosen resource (e.g., GitLab) compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for this phase.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Unmanaged/guest device management capabilities are not included in this build. To control network access for unmanaged/guest devices, unauthenticated network traffic can be forwarded to the Symantec Cloud Secure Web Gateway for policy enforcement.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful re-authentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully to Symantec Endpoint Protection immediately lose access to resources. Periodic reauthentication is required.

-  Resource authentication was not demonstrated. It could not be performed by the products included in this build.

-  Compliant devices maintain or regain access to resources. Non-compliant devices or users with non-compliant devices lose access to resources.

   -  Symantec Endpoint Protection determines, and then reports to the Symantec Security Cloud, the compliance state of devices that it manages. Endpoint compliance must be validated prior to allowing access. Endpoint compliance is checked periodically.

   -  Devices lose access to resources once Symantec Security Cloud is made aware of a non-compliant state.

-  The ability to monitor, detect, and block violations of data use policies was demonstrated using Symantec DLP.

   -  However, the capability to fully terminate resource access was not demonstrated. The individual actions described can be detected and blocked, but an additional SOAR capability would need to be integrated to complete the full scenario.

-  User sessions and devices attempting to access unauthorized resources and malicious sites were blocked.

   -  The user's access sessions were not fully terminated. The individual actions described can be detected and blocked, but an additional SOAR capability would need to be integrated to complete the scenarios.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  The individual actions described can be detected and blocked, but an additional SOAR capability would need to be integrated to complete the scenarios.

-  Enterprise denying access to resources when users are accessing from suspicious endpoints was not fully demonstrated.

   -  The capabilities to demonstrate these scenarios are not included in this build. The individual actions described can be detected and blocked, but an additional SOAR capability would need to be integrated to complete the scenarios.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Use Case G was not demonstrated for this build, as the capability to manage Service-Service communications was not included in the build.

**Use Case H: Data Level Security**

**Description**: This use case covers subject access requests to data with different levels of classification.

-  Access to data based on identity attributes - Using Symantec DLP, this build is able to restrict data access and operations based on identity attributes, covering both on-prem and cloud-based resources.

-  Access to data based on requesting endpoint - Symantec DLP is able to restrict data access and operations based on endpoint type.

-  Internet access restricted when accessing data with high classification - Symantec DLP can prevent data classified as “high” from being uploaded to the internet or other destinations.

-  Requestor challenged to re-authenticate when accessing data with high classification  - Capabiliity was not included in this build.

-  User temporarily granted access privileges to data with high classification  - Capability was not included in this build.

-  Certain operations can be prevented based on subject endpoint, location or some other factor - Symantec DLP can control data operations based on endpoint type and endpoint location.

-  Extra protection for highly classified data when stored on an endpoint  - Capability was not included in this build.

Enterprise 3 Build 4 (E3B4) - SDP - F5 BIG-IP, F5 NGINX Plus, Forescout eyeControl, and Forescout eyeExtend as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets were successfully demonstrated. Resources and endpoints were granted access to the network and if applicable, limited to a specific subnet or resource set based on Forescout policy. These policies were enforced by a PAN NGFW and Cisco switch. Due to the location of these PEPs, unauthenticated endpoints were restricted to the local subnet in accordance with Forescout policy.

   -  Network assets were discovered by Forescout via both passive and active detection.

-  Reauthentication of identified assets was successfully demonstrated using Forescout.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  Azure AD captures sign-in logs to SaaS applications, PaaS and IaaS resources, and on-prem applications.

   -  Azure AD audit logs show activity, including changes to cloud resources in the Azure tenant.

   -  Forescout captures sign-in and audit logs and network traffic for on-premises components.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** These use cases demonstrate user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via BIG-IP.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  This build did not implement applying restrictions on accessing Internet resources by either Enterprise or Contractor Users using either an enterprise endpoint or BYOD from an on-premises or a remote environment.

-  Stolen credential using an enterprise endpoint or BYOD  - BIG-IP does not detect a hostile request if all credentials are correct.

-  Just-in-Time (JIT) Access Privileges - The build did not implement just-in-time access privileges.

-  Enterprise-ID Step-Up Authentication was not configured for this build.

-  This build did not have the capability to verify chosen resource (e.g., GitLab) compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for this phase.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Forescout was able to provide Internet access to unauthenticated guest devices connecting to a segmented portion of the enterprise network.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  User or devices that fail reauthentication lose access to resources. With successful reauthentication, access is maintained.

   -  A resource access web portal was implemented that provided users with access only to resources they were authorized to access.

   -  Users that fail reauthentication lose access to the resource access web portal. With successful re-authentication, access is regained. User reauthentication was implemented in BIG-IP via user inactivity timeouts. Users that failed reauthentication could not initiate access to resources.

   -  Device re-authentication was not implemented.

   -  BIG-IP checked device compliance and allowed or maintained access if compliance was positive. Sessions to the resource access portal were terminated if device compliance failed.

-  Resource reauthentication was not demonstrated. It could not be performed by the products in this build.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  BIG-IP leveraged the F5 access app and its integration to Microsoft Intune to determine endpoint compliance.

-  The ability to monitor and detect violations of data use policies was not demonstrated.

-  User sessions and devices attempting to block access to unauthorized resources and malicious sites was not implemented.

-  The capability to detect malicious or suspicious behavior on enterprise endpoints and BYOD or unmanaged endpoints was not implemented.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  The scenario for this build focused on securing the service-to-service call (e.g., east-west) traffic within a Kubernetes cluster.

-  Client apps utilized access policies assigned by the NGINX Service Mesh Controller to make successful API calls to services running within the NGINX Service Mesh framework. Service requests without the correct authorization were denied.

   -  The build used a Kubernetes cluster with client and web server application pods deployed for the service-to-service demonstration.

   -  The client applications and the web server were deployed in separate pods within the cluster. Each was deployed with an injected sidecar proxy.

   -  Mutual TLS-encrypted API calls were used between services, and the policy engine used access policies, HTTP routing rules, and mutually authenticated certificates to allow or deny access.

   -  All service policy modifications took effect immediately.

   -  The Kubernetes cluster and service mesh were deployed in Azure IaaS.

**Use Case H: Data Level Security**

**Description:** This use case covers subject access requests to data with different levels of classification.

-  Demonstration could not be completed; the build does not have the capability to demonstrate data level security use cases.

Enterprise 4 Build 4 (E4B4) - SDP, Microsegmentation, and EIG - VMware Workspace ONE Access, VMware Unified Access Gateway, and VMware NSX-T as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description**: This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of managed endpoint assets

   -  Demonstration was based on VMware Workspace One UEM policy configuration.

   -  This build also demonstrated the capability to limit or reduce user access levels in certain scenarios.

   -  Resource authentication and limited access to the network were not demonstrated because VMware considers them out of scope for their products. Other technologies should be used to perform these functions.

-  Reauthentication of identified assets  - The Workspace One UEM agent requires reauthentication after a configurable period of time.

   -  If reauthentication fails, user does not have access to resources.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  Workspace One UEM and Workspace One Access capture sign-in logs to resources and on-prem applications.

   -  VMware Tunnel can be used for discovery of transaction flows as it captures network traffic and tells what destinations users are accessing.

   -  VMware considers API call visibility out of scope in this build for their participating products. Other technologies should be used to perform this function.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** These use cases demonstrate user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, Mac, Linux, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via VMware Workspace One Access.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

-  In order to complete some scenarios, including scenarios that require the endpoint to fail authentication, certificates were removed from devices, which can be done automatically upon policy violations. Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources (on-prem and cloud) in accordance with policy via VMware Mobile Threat Detection.

   -  VMware MTD services are only available on iOS, Android, and ChromeOS devices.

-  Stolen credential scenarios using an enterprise endpoint or BYOD were partially completed successfully.

   -  Since the certificates are protected, we were unable to duplicate VMware UEM certificates to another mobile device to complete some scenarios, including stolen credential scenarios. VMware Workspace ONE does not detect a hostile request if only using password authentication. Passwordless authentication is therefore the recommended method. 

   -  Stolen devices can be wiped and blacklisted if reported.

-  Just-in-Time (JIT) Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  VMware considers JIT access out of scope for their products. Other technologies should be used to perform this function.

-  Enterprise-ID Step-Up Authentication  - The build did not include the capability to prompt for re-authentication in the middle of an active session with the chosen resources (e.g., GitLab).

-  This build did not have the capability to verify resource compliance with policy.

**Use Case C: Federated-ID Access**  - Out of scope for this phase.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Users without managed devices are provided access to public internet resources but no access to enterprise resources. VMware NSX provided a Guest network with access to public internet resources while blocking all traffic to enterprise resources and networks.

**Use Case F: Confidence Level**

**Description**: This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful reauthentication, access is maintained.

   -  Users that are not able to reauthenticate successfully to VMware Workspace One UEM immediately lose access to resources.

   -  Endpoint credentials were invalidated by removing the authentication certificate from the device.

-  Resource reauthentication is out of scope for VMware; other technologies should be used.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  VMware Workspace One UEM determines the compliance state of devices that it manages.

   -  Devices lose access to resources via VMware Tunnel when they are noncompliant per Workspace ONE UEM.

   -  Devices that return to a compliant state have their access restored via the UAG Tunnel.

-  The ability to monitor and detect violations of data use policies was not demonstrated. VMware considered data use policies out of scope for this build.

-  User sessions and devices attempting to access unauthorized resources and malicious sites are blocked.

   -  SOAR capability was not included in this build. Individual URLs can be blocked, but user accounts cannot be terminated/blocked based on URL access.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  VMware MTD can detect malicious behavior on endpoints that have an MTD agent.

   -  Unmanaged endpoints have no mechanism for behavior detection.

-  Enterprise can deny access to resources when users are accessing from suspicious endpoints.

-  Suspicious endpoint activity was monitored by VMware MTD and access to resources terminated via the UAG Tunnel.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  VMware NSX controlled Service-Service communication between on-prem services.

-  VMware NSX controlled Service-Endpoint communication where either the Service or the Endpoint was located on-prem.

-  Branch office, PaaS, and SaaS services were unavailable for demonstration in this build.

**Use Case H: Data Level Security**

Description: This use case covers subject access requests to data with different levels of classification.

-  VMware considers data level security out of scope for this project. Other products should be used for these services.

Note that after this build was completed, VMware was acquired by Broadcom.

Enterprise 1 Build 5 (E1B5) - SASE and Microsegmentation - PAN NGFW and PAN Prisma Access as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This build does not have SaaS resources. Its summary results are as follows:

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets

   -  For this build, endpoints used the Palo Alto Networks (PAN) Global Protect Client in order to communicate with the PAN PEPs (Next Generation firewalls or Prisma Access) and be authenticated by them.

   -  Authentication of resources was not performed due to time constraints and availability of product (Cortex XDR).

-  Reauthentication of identified assets  - Global Protect Client requires reauthentication after a configurable period of time.

   -  User must reauthenticate once the authentication period is over. If reauthentication fails, the user does not have access to resources.

-  Discovery of transaction flows  - Visibility of authentication and resource access attempts was demonstrated.

   -  PAN PEs capture sign-in events, changes in user/device attributes, and traffic flow logs to on-prem and IaaS resources.

   -  PAN PE logs are sent to IBM QRadar.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** These use cases demonstrate user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, Linux, and mobile device iOS endpoints. Other endpoints were not demonstrated due to time constraints.

   -  PAN has 3 PEs, which also act as PEPs: Users connected on-premises use the on-prem PAN PE/PEP (NGFW). Users in the branch office use the branch PAN PE/PEP (NGFW). Remote users use the cloud PE/PEP (Prisma Access).

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, whether on-prem, branch, or remote, were allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policies enforced by the PAN PEPs. Policies were configured with the PEs.

   -  The PE can differentiate between employees and contractors and provide different access permissions to each user type.

   -  PAN PEPs (NGFWs) were deployed on-prem and in the AWS IaaS cloud to protect resources. Prisma Access is the PEP for remote users.

   -  Compliance of the endpoint was checked prior to allowing a user to access that resource. Compliance of resources was not demonstrated due to time constraints.

-  For this build, URL filtering was performed at each PEP to manage access to internet resources. The PEP that is closest to the user performs the URL filtering for that user.

-  Stolen credential using an enterprise endpoint or BYOD  - PAN does not detect a hostile request if all credentials are correct. 

   -  PAN can limit the location (by city, state, or country), number of allowed devices per user, and number of simultaneous logins by a user to prevent use of stolen credentials.

-  Just-in-Time Access Privileges  - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  A manual process was used to demonstrate providing users with additional privileges to resources.

   -  Integration with other products can be used to automate just-in-time privileges. However, those products were not part of this build.

-  Enterprise-ID Step-Up Authentication  - Both Enterprise and Contractor Users were prompted for additional factor authentication when attempting to access sensitive resources.

   -  An authentication policy was created within the PE to require additional authentication to specific resources that are considered sensitive and need additional protection.

-  This build did not have the capability to verify chosen resource (e.g., GitLab) compliance with policy.

   -  Due to time constraints, Cortex XDR was not available for this build.

**Use Case C: Federated-ID Access**

**Description:** These use cases demonstrate federated user-id access to enterprise 1 resources and the internet based on successfully achieving user and device security preconditions. For this demonstration, enterprise 3 users access enterprise 1 resources and the internet using enterprise 1 devices or BYOD.

-  An enterprise 3 federated user using an enterprise 1 laptop can access resources in enterprise 1 when on-premises, at the branch office, or remote.

   -  Users are authenticated using enterprise 3 credentials via the integration of the enterprise 1 and enterprise 3 identity providers (IdPs).

   -  Policies are applied to users and endpoints to allow or deny access to enterprise resources.

   -  Limited resource access can be achieved by applying policies to a specific set of users from enterprise 3.

-  An enterprise 3 federated user using an enterprise 1 laptop can access the internet when on-premises, at the branch office, or remote.

   -  Web filtering policies are enforced by the enterprise 1 PEPs when a federated user accesses the internet using an enterprise 1 device.

-  An enterprise 3 federated user using a BYOD laptop can access the internet when on-premises or at the branch office. When the user is remote, enterprise 1 policies do not apply.

   -  Web filtering policies are enforced by the enterprise 1 PEPs when a federated user accesses the internet using a BYOD device.

-  Stolen credentials are treated the same way for federated users and enterprise users.

   -  If user credentials are stolen and not reported, a malicious user will have access.

   -  Once user credentials/device is reported stolen, policies are applied to deny those users and devices. Users will need to update their credentials to regain access.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Guest users are given access to the internet only via the on-prem PEP.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful reauthentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully via Global Protect will immediately lose access to resources.

   -  Initial authentication with the PAN PE provides user with authentication and compliance checks. Policies dictate what resources a user has access to. Periodic reauthentication and MFA or step-up authentication for access to critical resources is required, which verifies compliance as well.

-  Resource reauthentication is out of scope due to time constraints.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  Upon login to endpoint device, HIP information is sent to the PAN NGFW and validated before the endpoint gains access to the resources. Device compliance is checked periodically.

   -  Devices lose access to resources once the NGFW is made aware of a noncompliant state.

-  The ability to monitor and detect violations of data use policies was demonstrated with two methods.

   -  PAN demonstrated detecting specific types of data (e.g., bank accounts or SSN) and block access.

   -  Downloading more than a defined amount of data (e.g., more than 10MB) results in a denial of download.

-  User sessions and devices attempting to access unauthorized resources and malicious sites are blocked.

   -  PAN PE policies determine if a user has access to a resource or not. If there is no policy to allow a user to access a resource and the user requests to reach that resource, the request will be dropped by the PEP by default due to a deny policy for traffic that does not match any of the configured policies.

   -  PAN PE creates dynamic user groups which allow the PEP to deny or quarantine a user if the user attempts to access resources or URLs that are in violation of policy.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  Using dynamic user groups, PAN PEP detects behaviors that are considered malicious and blocks users from accessing resources once the PEP receives an update about a malicious detection.

-  Enterprise can deny access to resources when users are accessing from suspicious endpoints.

   -  Suspicious endpoint use cases were not demonstrated due to time constraints. Cortex XDR would be used to identify suspicious endpoints.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Due to time constraints, only some on-prem to on-prem service-to-service communications were demonstrated. We did not have time to demonstrate service-to-service communications for resources in the cloud. Policies were created to restrict access between resources based on API communications. However, PAN Cortex XDR, which would need to be installed on resource endpoints to provide compliance and threat information to the PE for it to make access decisions, was not available for this build. Therefore, we were not able to restrict access to a resource based on endpoint compliance or threat information.

**Use Case H: Data Level Security**

**Description**: This use case covers subject access requests to data with different levels of classification.

-  Access to data based on identity attributes  - PAN PEPs can inspect and apply policy to data based on predetermined sensitive information.

-  Access to data based on requesting endpoint  - HIPs are leveraged to make decisions about the endpoint.

-  Internet access restricted when accessing data with high classification  - PAN leverages dynamic user groups to identify user access based on specific criteria such as accessing sensitive data.

-  Requestor challenged to re-authenticate when accessing data with high classification  - PAN leverages authentication profiles to force users to provide MFA when accessing sensitive data.

-  User temporarily granted access privileges to data with high classification  - Temporary updates are available to access privileges.

-  Certain operations can be prevented based on subject endpoint, location, or another factor  - PAN can provide policies to limit access to data. PAN can allow or deny upload/download of data from a resource. PAN does not have the ability to limit read/write capabilities on a resource.

-  Extra protection for highly classified data when stored on an endpoint  - Cortex XDR, which can be leveraged to support this feature, was not available for this build.

-  While PAN PE/PEP can allow or deny access to specific data or applications within a resource, data classification is out of scope of this project. In order for this use case to be properly demonstrated, data must be classified. After classification, PAN PE/PEPs can develop policies to allow or deny user access to these data classes.

Enterprise 2 Build 5 (E2B5) - SDP and SASE - Lookout SSE and Okta Identity Cloud as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets - Capability was not included in this build.

-  Reauthentication of identified assets - Capability was not included in this build.

-  Discovery of transaction flows - Visibility of authentication and resource access attempts was demonstrated.

   -  Lookout SSE captures sign-in and individual user action logs to SaaS applications, IaaS resources, and on-prem applications.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** These two use cases demonstrate user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and mobile device (iOS and Android) endpoints.

   -  Demonstration capability varied between the different platforms. The agent-based approach on Windows and macOS successfully completed all scenarios. The mobile devices successfully completed all scenarios with the exception of those involving internet access policies that are time-bound.

   -  An agentless approach was also demonstrated on all of the above platforms using Lookout SSE. This method completed all scenarios with the exception of those involving device compliance.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via Lookout Private Access.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type. This is accomplished through integration with the ICAM (Okta).

   -  The build demonstrated that sensitive data such as credit card information could have access controlled based on policy within Lookout SSE.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources in accordance with policy via Lookout Internet Access.

   -  Policies within Lookout Internet Access were set up to allow, block, or limit access to internet resources.

-  Stolen credential using an enterprise endpoint or BYOD - Lookout does not detect a hostile request if all credentials are correct. Lookout is able to revoke unauthorized access once credentials have been reported stolen and stolen credentials have been revoked. Anomalous login policies can raise a user’s risk level if suspicious authentication attempts are made, and user access can be limited or blocked based on the user’s risk score.

-  Just-in-Time (JIT) Access Privileges - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  In this build, Just-in-Time privileges can be manually completed to allow a user to access a resource. These policies can be temporary, giving the user access for a limited period of time.

-  Enterprise-ID Step-Up Authentication - Step-up authentication capabilities were demonstrated with SaaS services (Google Workspace). Users requesting to access sensitive data were prompted for additional authentication factors.

-  This build did not have the capability to verify chosen resource (e.g., GitLab) compliance with policy. Lookout SSE can integrate with vulnerability management platforms to receive resource compliance information, but this was not demonstrated during the build.

**Use Case C: Federated-ID Access** - Out of scope for this build.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Unmanaged/guest device management capabilities are not included in this build. To control network access for unmanaged/guest devices, unauthenticated network traffic can be forwarded to the Lookout SSE for policy enforcement.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful re-authentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully to Lookout SSE immediately lose access to resources. Periodic reauthentication is required.

-  Resource authentication was not demonstrated. This capability was not included in this build. Lookout SSE can integrate with vulnerability management platforms to receive resource compliance information, but this was not demonstrated during the build.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  The Lookout Client determines, and then reports to Lookout SSE, the compliance state of devices that it manages. Endpoint compliance must be validated prior to allowing access. Endpoint compliance is checked periodically.

   -  Devices lose access to resources once Lookout SSE is made aware of a noncompliant state.

-  The ability to monitor, detect, and block violations of data use policies was demonstrated using Lookout SSE.

   -  However, the capability to fully terminate resource access was not demonstrated. The individual actions described can be detected and blocked, but an additional SOAR capability would need to be integrated to complete the full scenario.

-  User sessions and devices attempting to access unauthorized resources and malicious sites were blocked.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  The capabilities to demonstrate these scenarios are not included in this build. The individual actions described can be detected and blocked, but an additional SOAR capability would need to be integrated to complete the scenarios.

-  Enterprise denying access to resources when users are accessing from suspicious endpoints was not fully demonstrated.

   -  The capabilities to demonstrate these scenarios are not included in this build. The individual actions described can be detected and blocked, but an additional SOAR capability would need to be integrated to complete the scenarios.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Use Case G was not demonstrated for this build, as the capability to manage Service-Service communications was not included in the build.

**Use Case H: Data-Level Security**

**Description**: This use case covers subject access requests to data with different levels of classification.

-  Access to data based on identity attributes - Using Lookout SSE, this build is able to restrict data access and operations based on identity attributes, covering both on-prem and cloud-based resources.

-  Access to data based on requesting endpoint - Lookout SSE is able to restrict data access and operations based on endpoint type.

-  Internet access restricted when accessing data with high classification - This capability was not included in this build. Lookout recommends that policies are put into place to prevent data exfiltration. Lookout SSE has the ability to differentiate between corporate and personal accounts and cloud services to prevent sensitive data from being exfiltrated.

-  Requestor challenged to reauthenticate when accessing data with high classification - Lookout SSE was able to challenge for reauthentication with SaaS applications.

-  User temporarily granted access privileges to data with high classification - Lookout SSE is able to grant Just-In-Time access to high-level data when needed.

-  Certain operations can be prevented based on subject endpoint, location, or some other factor - Lookout SSE can control data operations based on endpoint type and endpoint location.

-  Extra protection for highly classified data when stored on an endpoint - Lookout SSE is able to encrypt highly classified data when downloaded to a user endpoint. Classified data is labeled using data security policy in Lookout SSE.

Enterprise 3 Build 5 (E3B5) - SDP and SASE - Microsoft Entra Conditional Access (formerly called Azure AD Conditional Access) and Microsoft Security Service Edge as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets

   -  Discovery and authentication of endpoint assets was successfully demonstrated. Endpoints were granted access to the network and if applicable, limited to a specific subnet or resource set based on Microsoft Security Service Edge (SSE) policy. Due to the configuration of the on-prem switch and firewall, unauthenticated endpoints were restricted to the local subnet.

   -  Network endpoints were discovered via the onboarding mechanism to Microsoft Intune.

-  Reauthentication of identified assets - Intune periodically reauthenticates each endpoint while also checking for compliance. Enforcement is done via Conditional Access policies.

-  Discovery of transaction flows - Visibility of authentication and resource access attempts was demonstrated.

   -  Entra ID captures sign-in logs to SaaS applications, PaaS and IaaS resources, and on-prem applications.

   -  Entra ID audit logs show activity, including changes to cloud resources in the Entra ID tenant or for tenant configuration changes.

   -  Entra ID also captures sign-in and audit logs for on-prem resources and applications with the use of SSE via the SSE traffic logs.

   -  Entra ID captures network access logs and audit logs for Internet access and access to private applications (on-prem and cloud) via the traffic logs.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** These use cases demonstrate user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and mobile device iOS and Android endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policy via Entra Conditional Access.

   -  The policy engine can differentiate between employees and contractors and provide different access permissions to each user type.

   -  The build demonstrated that documents with sensitive data such as credit cards could be viewed but not downloaded.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, are allowed or denied access to internet resources in accordance with policy via Defender for Apps and Defender for Endpoint.

   -  Policies within Defender for Apps were set up to allow, block, or limit access to resources.

-  Stolen credential using an enterprise endpoint or BYOD - Entra ID does not detect a hostile request if all credentials are correct.

-  Just-in-Time (JIT) Access Privileges - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  JIT for VM and Resource Access

      -  Azure and SSE working in combination can provide a JIT feature capability for resource access that enables an eligible user to access any enterprise VM with SSH, RDP, or TCP/IP protocol and IP/port combination for a limited time when requested.

      -  Defender for Cloud checks that the user has the appropriate Azure role, then inserts allow rules for a specific user’s IP address into the network security groups and Azure Firewall as well as SSE network access policies.

      -  SSE can leverage Azure JIT feature and extend JIT access to on-prem VMs and resources.

      -  This only occurs at the time that the user requests access to these resources.

   -  JIT with Privileged Identity Management (PIM)

      -  PIM is used to provide an additional layer of authentication and authorization before requesting users are granted access to privileged Entra ID roles for a limited time and scope.

      -  Once granted, a user gains elevated Entra ID administration privileges for a limited time.

      -  PIM works within the Azure environment and the on-prem hosted applications that use Entra ID as an identity provider, when leveraging Entra ID Group write-back.

-  Enterprise-ID Step-Up Authentication - Both Enterprise and Contractor Users are prompted for additional factor authentication when attempting to access sensitive resources.

   -  Entra Conditional Access provides additional authentication when a user attempts to access a portion of a site or a document with a sensitive label. An example of a sensitive site is a SharePoint site with a sensitive label.

   -  Conditional Access would prompt the user for additional authentication prior to allowing access.

**Use Case C: Federated-ID Access**

**Description:** These use cases demonstrate federated user-id access to Enterprise 1 resources and the internet based on successfully achieving user and device security preconditions. For this demonstration, Enterprise 3 users access Enterprise 1 resources and the internet using Enterprise 1 devices or BYOD.

-  An Enterprise 3 federated user using an Enterprise 1 laptop can access resources in Enterprise 1 when on-premises, at the branch office, or remote.

   -  Users are authenticated using Enterprise 3 credentials via the integration of the Enterprise 1 and Enterprise 3 IdPs.

   -  Policies are applied to users and endpoints to allow or deny access to enterprise resources.

   -  Limited resource access can be achieved by applying policies to a specific set of users from Enterprise 3.

-  An Enterprise 3 federated user using an Enterprise 1 laptop can access the internet when on-premises, at the branch office, or remote.

   -  Web filtering policies are enforced by the Enterprise 1 PEPs when a federated user accesses the internet using an Enterprise 1 device.

-  An Enterprise 3 federated user using a BYOD laptop can access the internet when on-premises or at the branch office. When the user is remote, Enterprise 1 policies do not apply.

   -  Web filtering policies are enforced by the Enterprise 1 PEPs when a federated user accesses the internet using a BYOD device.

-  Stolen credentials are treated the same way for federated users and enterprise users.

   -  If user credentials are stolen and not reported, a malicious user will have access.

   -  Once user credentials/devices are reported stolen, policies are applied to deny those users and devices. Users will need to update their credentials to regain access.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  This build was able to provide internet access to unauthenticated guest devices connecting to a segmented portion of the enterprise network.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful reauthentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully to Microsoft Intune Mobile Device Management (MDM) will be offboarded and immediately lose access to resources. Periodic reauthentication is required.

   -  Entra Conditional Access was configured to only allow connections from Intune-compliant devices.

-  Resource authentication was not demonstrated. It could not be performed by the products in this build.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  Microsoft Intune determines, and then reports to Entra ID, the compliance state of devices that it manages. Endpoint compliance must be validated prior to allowing access. Endpoint compliance is checked periodically.

   -  Devices lose access to resources once Entra ID is made aware of a noncompliant state.

-  The ability to monitor and detect violations of data use policies was demonstrated. The downloading and attempted exfiltration of documents with sensitive data was blocked.

-  User sessions and devices attempting to access unauthorized resources and malicious sites were blocked or the sessions were terminated.

   -  Defender for Apps was configured to label sites as trusted or untrusted.

   -  If a site was untrusted, Defender for Endpoint enforced Defender for Apps Policy and prevented the user from visiting the site by blocking it.

   -  Additionally, Entra Conditional Access was configured to block users from accessing resources without proper authorization.

   -  Microsoft Sentinel was successfully configured to send API requests to Entra ID to terminate active sessions and disable user accounts when alerts indicating malicious events (e.g., attempts to access known bad internet sites) were received. Session termination was successfully tested for Office SaaS apps and SSE-controlled IaaS and on-prem apps.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  Defender for Endpoint was configured as the Endpoint Detection and Response solution to detect and block threats and inform Entra ID via Intune.

   -  Defender for Endpoint has built-in sensors in the Windows platform and utilizes Windows Defender Firewall and Microsoft Defender Anti-Virus to detect threats.

-  Enterprise can deny access to resources when users are accessing from suspicious endpoints.

   -  Once onboarded, devices with Defender for Endpoint detected threats that included malicious script execution, network reconnaissance, and Active Directory reconnaissance. 

   -  Defender for Endpoint categorized the threats, forwarded the alerts to Microsoft 365 Defender, and forwarded the risk information to Intune.

   -  Depending on the risk threshold set, Microsoft Intune changed the endpoint status to noncompliant.

   -  Entra Conditional Access received the noncompliant status information and blocked the devices from accessing resources.

**Use Case G: Service-Service Interactions**

**Description:** This use case covers API calls between services and the ability of the policy engine to allow or deny calls to services based on properly assigned authorizations.

-  Client apps were able to utilize either Azure roles or Entra ID authorizations to make successful API calls to Azure IaaS, PaaS, and Microsoft SaaS apps. Client apps without the correct authorizations were denied.

   -  Client applications made API calls to manage an Azure VM, retrieve data managed by Entra ID, and retrieve data from Microsoft 365 mail and Microsoft Sentinel.

   -  Client apps without the right API permissions were denied.

-  Client apps hosted in Azure IaaS or Azure PaaS were able to make successful API calls to Azure IaaS, Azure PaaS, and Microsoft SaaS apps. Apps without the correct authorizations were denied.

   -  A client application hosted/stored in an Azure VM or an Azure function was used to make successful API calls to manage an Azure VM, retrieve Entra ID-managed data, and retrieve data from Microsoft Sentinel and Microsoft 365 mail.

-  Client applications were not able to make API calls to the chosen on-prem/IaaS application (e.g., GitLab) because the API authorization was issued by an external authorization provider.

-  For Service-to-Endpoint use cases:

   -  Intune was used to instruct the endpoint to take certain actions, such as to update itself and restart.

**Use Case H: Data-Level Security**

**Description**: This use case covers subject access requests to data with different levels of classification.

-  Access to data based on identity attributes - Leveraging Entra Conditional Access, differing levels of access were assigned to users depending on the classification of data in the cloud.

-  Access to data based on requesting endpoint - Leveraging Entra Conditional Access and Microsoft Intune compliance feeds, differing levels of access were assigned to subjects based on the compliance status of their endpoints. This was only applicable to data resident in the cloud.

-  Internet access restricted when accessing data with high classification - Leveraging Entra Conditional Access, allowed and excluded subject locations were specified. Data was differentiated based on which folder an object resided in. Controls were applicable to data in the cloud.

-  Requestor challenged to reauthenticate when accessing data with high classification - Entra Conditional Access using the authentication context feature triggers MFA for sensitive data in the cloud.

-  User temporarily granted access privileges to data with high classification - Entra ID Privileged Identity Management was used to temporarily elevate subject privileges for a limited time so as to provide access to sensitive data and resources in the cloud.

-  Certain operations can be prevented based on subject endpoint, location, or another factor - Access controls were applied in SharePoint that prevented the modification and downloading of files.

-  Extra protection for highly classified data when stored on an endpoint - Encryption was applied to data that was downloaded and required a password for decryption.

-  Although data classification was out of scope for this project, the products used had the ability to classify data. Instead, for these use cases, sensitive data was differentiated from non-sensitive data by having them use different folders.

Enterprise 1 Build 6 (E1B6) - SDP and Microsegmentation - Ivanti Neurons for Zero Trust Access as PEs Summary Demonstration Results
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Use Case A: Discovery and Identification of IDs, Assets, and Data Flows**

**Description:** This use case demonstrates the ability of the enterprise to discover network assets, authenticate devices, and demonstrate network connectivity.

-  Discovery and authentication of endpoint assets

   -  For this build, endpoints used the Ivanti Secure Access Client in order to communicate with the nZTA Controller and be authenticated by it. Once authenticated, the endpoint has access to resources, including networks, based on policy.

   -  Authentication of resources use cases were not included in this build. This build does not have resource authentication as Ivanti Policy Secure (IPS), was not available due to time constraints.

-  Reauthentication of identified assets - Ivanti Secure Access Client requires reauthentication after a configurable period of time.

   -  User must reauthenticate once the authentication period is over. If reauthentication fails, the user does not have access to any resources.

-  Discovery of transaction flows - Visibility of authentication and resource access attempts was demonstrated.

   -  Ivanti nZTA captures sign-in events, changes in user/device attributes, and traffic flow logs to on-prem and IaaS resources.

   -  nZTA logs are sent to IBM QRadar.

**Use Case B: Enterprise-ID Access, Use Case D: Other-ID Access**

**Description:** These use cases demonstrate user access to enterprise resources based on successfully achieving user and device security preconditions.

-  For this build, we successfully demonstrated access using Windows, macOS, and Linux endpoints.

-  Both Enterprise and Contractor Users on an enterprise endpoint or BYOD, on-prem or remote, were allowed or denied access to enterprise resources (on-prem and cloud) in accordance with policies enforced by the Ivanti nZTA Gateway. Policies were configured with the Ivanti nZTA Controller.

   -  The policy engine (nZTA Controller) can differentiate between employees and contractors and provide different access permissions to each user type.

   -  Ivanti nZTA Gateways were deployed on-prem and in the AWS IaaS cloud to protect resources.

   -  Compliance of the endpoint was checked prior to allowing a user to access that resource.

-  For this build, Ivanti nZTA did not manage access to internet resources. Ivanti partners with another vendor to manage device access to internet resources.

-  Stolen credential using an enterprise endpoint or BYOD - Ivanti nZTA does not detect a hostile request if all credentials are correct. 

   -  Ivanti nZTA can limit the number of allowed devices per user and number of simultaneous logins by a user to help prevent use of stolen credentials.

-  Just-in-Time Access Privileges - Users are allowed to request and elevate privileges required to perform a given task for a limited period.

   -  A manual process was used to demonstrate providing users with additional privileges to resources.

-  Enterprise-ID Step-Up Authentication - Both Enterprise and Contractor Users were prompted to reauthenticate with multifactor authentication when attempting to access sensitive resources.

   -  A policy was created within the Ivanti nZTA Controller to require multifactor authentication to specific resources that are considered sensitive and need additional protection.

-  Verification of the chosen resource (e.g., GitLab) - This build did not have the capability to verify resource compliance because the product was not available due to time constraints.

**Use Case C: Federated-ID Access**

**Description:** These use cases demonstrate federated user-id access to Enterprise 1 resources and the internet based on successfully achieving user and device security preconditions. For this demonstration, Enterprise 3 users access Enterprise 1 resources and the internet using Enterprise 1 devices or BYOD.

-  An Enterprise 3 federated user using an Enterprise 1 laptop can access resources in Enterprise 1 when on-premises, at the branch office, or remote.

   -  Users are authenticated using Enterprise 3 credentials via the integration of the Enterprise 1 and Enterprise 3 IdPs.

   -  Policies are applied to users and endpoints to allow or deny access to enterprise resources.

   -  Limited resource access can be achieved by applying policies to a specific set of users from Enterprise 3.

-  An Enterprise 3 federated user using an Enterprise 1 laptop can access the internet when on-premises, at the branch office, or remote.

   -  Web filtering policies are enforced by the Enterprise 1 PEPs when a federated user accesses the internet using an Enterprise 1 device.

-  An Enterprise 3 federated user using a BYOD laptop can access the internet when on-premises or at the branch office. When the user is remote, Enterprise 1 policies do not apply.

   -  Web filtering policies are enforced by the Enterprise 1 PEPs when a federated user accesses the internet using a BYOD device.

-  Stolen credentials are treated the same way for federated users and enterprise users.

   -  If user credentials are stolen and not reported, a malicious user will have access.

Once user credentials/device is reported stolen, policies are applied to deny those users and devices. Users will need to update their credentials to regain access.

**Use Case E: Guest: No-ID Access**

**Description:** This use case demonstrates the ability of the enterprise to allow unmanaged guest devices to have access to public Internet resources.

-  Ivanti nZTA considers this out of scope for their products. Other technologies should be used to perform guest access enforcement.

**Use Case F: Confidence Level**

**Description:** This use case demonstrates the ability of the enterprise to allow, prevent, or terminate sessions to resources based on the continuous evaluation of user and device risk.

-  Users or devices that fail reauthentication lose access to resources. With successful reauthentication, access is maintained.

   -  Devices that are not able to reauthenticate successfully to the Ivanti nZTA Controller will immediately lose access to resources. Device risk and condition-based access is evaluated when there are changes to the device. Ivanti Secure Access Client monitors changes in real time.

   -  Initial authentication and compliance check with Ivanti nZTA controller provides the user with access to resources assigned to that user. Periodic reauthentication and MFA or step-up authentication for access to critical resources is required, which verifies compliance as well.

-  Resource reauthentication use cases are not included in this build. This build does not have resource authentication because the product was not available at this time. Other solutions can be leveraged to perform this function.

-  Compliant devices maintain or regain access to resources. Noncompliant devices or users with noncompliant devices lose access to resources.

   -  Upon login to the Ivanti Secure Access client, compliance information is sent to the nZTA controller and validated before the user can access any resources. Device compliance is checked when a change is detected on the endpoint.

   -  Devices lose access to resources in near-real-time when a noncompliant state is detected by the Secure Access client.

-  The ability to monitor and detect violations of data use policies was not demonstrated. Ivanti nZTA does not have capabilities to manage data use policies.

-  User sessions and devices attempting to access unauthorized resources are blocked.

   -  Ivanti nZTA policies determine if a user has access to a resource or not. If there is no policy to allow a user to access a resource and the user requests to reach that resource, the request will not be able to leave the end device or it will be denied by the Ivanti nZTA Gateway. nZTA will not terminate the user’s connection to the Gateway, but it will block access to the unauthorized resource.

   -  Ivanti nZTA does not control access to internet websites. Ivanti recommends leveraging another vendor’s tool to perform this function.

-  Enterprise can detect malicious behavior on enterprise endpoints and BYOD but not on unmanaged endpoints.

   -  Ivanti Secure Access clients perform compliance checks upon initial login and deny access to resources if compliance fails. Any change to the endpoint is evaluated by the Secure Access client.

-  Enterprise can deny access to resources when users are accessing from suspicious endpoints.

   -  Ivanti nZTA does not allow any traffic past the nZTA Gateway if there is no policy to allow that specific access from the user. Logs of these attempts are provided to the SIEM. Note: The SIEM can trigger a security event, which Ivanti can consume to further restrict that user's access by deeming the user riskier.

**Use Case G: Service-Service Interactions** - Service-to-Service use cases are not included in this build. Ivanti does not have this capability. Integration with other vendors is necessary.

**Use Case H: Data-Level Security** - Data-level security capabilities are not included in this build. Ivanti does not have this capability. Integration with other vendors is necessary.
