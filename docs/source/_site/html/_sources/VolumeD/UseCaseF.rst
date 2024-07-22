Use Case F: Confidence Level
===================================

.. include:: /_publication_note.rst

Scenario F-1: User reauthentication fails during active session
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario is based on a successful request with an established session to an enterprise resource using an enterprise-owned endpoint. The requestor's reauthentication will fail, reducing the confidence level to a point where the enterprise policy states that the active session should be terminated. This leads to terminating the active session.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with full access to the resource. A request to access the enterprise resource is granted and a session is established.

**Demonstration:** The reauthentication of the requestor fails, and the session will be terminated.

**Purpose and Outcome:** This demonstration focuses on the requester's identification, which fails re-authentication during an active session.

**Table 1 - Scenario F-1 Demonstrations**

+---------+---+---------+---------+---------+-------------------------------+
| Demo ID     | Re-auth | Req Loc | RSS Loc | Desired Outcome               |
+=========+===+=========+=========+=========+===============================+
| F-1.1   | a | Passes  | On-Prem | On-Prem | Session stays active          |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.1   | b | Fails   | On-Prem | On-Prem | Session will be terminated    |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.2   | a | Passes  | Branch  | On-Prem | Session stays active          |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.2   | b | Fails   | Branch  | On-Prem | Session will be terminated    |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.3   | a | Passes  | Remote  | On-Prem | Session stays active          |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.3   | b | Fails   | Remote  | On-Prem | Session will be terminated    |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.4   | a | Passes  | On-Prem | Cloud   | Session stays active          |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.4   | b | Fails   | On-Prem | Cloud   | Session will be terminated    |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.5   | a | Passes  | Branch  | Cloud   | Session stays active          |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.5   | b | Fails   | Branch  | Cloud   | Session will be terminated    |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.6   | a | Passes  | Remote  | Cloud   | Session stays active          |
+---------+---+---------+---------+---------+-------------------------------+
| F-1.6   | b | Fails   | Remote  | Cloud   | Session will be terminated    |
+---------+---+---------+---------+---------+-------------------------------+

Scenario F-2: Requesting endpoint reauthentication fails during active session 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario is based on a successful request with an established session to an enterprise resource using an enterprise-owned endpoint. The reauthentication of the requesting endpoint will fail, reducing the confidence level. The given enterprise has a policy that would trigger termination of an active session. This leads to terminating the active session.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with full access to the resource. A request to access the enterprise resource is granted and a session is established.

**Demonstration:** The reauthentication of the requestor's endpoint fails, and the session will be terminated.

**Purpose and Outcome:** This demonstration focuses on the requester's endpoint identification, which fails re-authentication during an active session.

**Table 2 - Scenario F-2 Demonstrations**

+---------+---+---------+----------+---------+-------------------------------+
| Demo ID     | Re-auth | Req. Loc | RSS Loc | Desired Outcome               |
+=========+===+=========+==========+=========+===============================+
| F-2.1   | a | Passes  | On-Prem  | On-Prem | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.1   | b | Fails   | On-Prem  | On-Prem | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.2   | a | Passes  | Branch   | On-Prem | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.2   | b | Fails   | Branch   | On-Prem | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.3   | a | Passes  | Remote   | On-Prem | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.3   | b | Fails   | Remote   | On-Prem | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.4   | a | Passes  | On-Prem  | Cloud   | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.4   | b | Fails   | On-Prem  | Cloud   | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.5   | a | Passes  | Branch   | Cloud   | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.5   | b | Fails   | Branch   | Cloud   | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.6   | a | Passes  | Remote   | Cloud   | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-2.6   | b | Fails   | Remote   | Cloud   | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+

Scenario F-3: Resource reauthentication fails during active session
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario is based on a successful request with an established session to an enterprise resource. The reauthentication of the resource will fail, reducing the confidence level. The level is now below the acceptable level for the resource according to enterprise policy. This leads to terminating the active session.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with full access to the resource. A request to access the enterprise resource is granted and a session is established.

**Demonstration:** The reauthentication of the resource fails, and the session will be terminated.

**Purpose and Outcome:** This demonstration focuses on the resource identification, which fails re-authentication during an active session.

**Table 3 - Scenario F-3 Demonstrations**

+---------+---+---------+----------+---------+-------------------------------+
| Demo ID     | Re-auth | Req. Loc | RSS Loc | Desired Outcome               |
+=========+===+=========+==========+=========+===============================+
| F-3.1   | a | Passes  | On-Prem  | On-Prem | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.1   | b | Fails   | On-Prem  | On-Prem | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.2   | a | Passes  | Branch   | On-Prem | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.2   | b | Fails   | Branch   | On-Prem | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.3   | a | Passes  | Remote   | On-Prem | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.3   | b | Fails   | Remote   | On-Prem | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.4   | a | Passes  | On-Prem  | Cloud   | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.4   | b | Fails   | On-Prem  | Cloud   | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.5   | a | Passes  | Branch   | Cloud   | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.5   | b | Fails   | Branch   | Cloud   | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.6   | a | Passes  | Remote   | Cloud   | Session stays active          |
+---------+---+---------+----------+---------+-------------------------------+
| F-3.6   | b | Fails   | Remote   | Cloud   | Session will be terminated    |
+---------+---+---------+----------+---------+-------------------------------+

Scenario F-4: Compliance fails during active session 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario is based on a successful request with an established session to an enterprise resource using an enterprise-owned endpoint. The endpoint will fall out of compliance, reducing the confidence level. The enterprise has a policy that indicates that the endpoint can no longer be used to access the given resource. This terminates the session.

**Pre-Condition:** The requestor is identified and authenticated. The endpoint used is tested and considered compliant. A request to access the enterprise resource is granted and a session is established.

**Demonstration:** The requesting endpoint falls out of policy (becomes not compliant), and the session will be terminated. The requesting endpoint is either enterprise-owned or BYOD. It cannot be a guest endpoint for these demonstrations.

**Purpose and Outcome:** This demonstration focuses on the requester's endpoint compliance, which changes from compliant to not compliant during an active session.

**Table 4 - Scenario F-4 Demonstrations**

+---------+---+--------------+---------+---------+------------------------------------------+
| Demo ID     | Req EP Compl | Req Loc | RSS Loc | Desired Outcome                          |
+=========+===+==============+=========+=========+==========================================+
| F-4.1   | a | Y            | On-Prem | On-Prem | Session stays active                     |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.1   | b | N            | On-Prem | On-Prem | Session will be terminated               |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.2   | a | Y            | Branch  | On-Prem | Session stays active                     |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.2   | b | N            | Branch  | On-Prem | Session will be terminated               |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.3   | a | Y            | Remote  | On-Prem | Session stays active                     |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.3   | b | N            | Remote  | On-Prem | Session will be terminated               |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.4   | a | Y            | On-Prem | Cloud   | Session stays active                     |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.4   | b | N            | On-Prem | Cloud   | Session will be terminated               |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.5   | a | Y            | Branch  | Cloud   | Session stays active                     |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.5   | b | N            | Branch  | Cloud   | Session will be terminated               |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.6   | a | Y            | Remote  | Cloud   | Session stays active                     |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-4.6   | b | N            | Remote  | Cloud   | Session will be terminated               |
+---------+---+--------------+---------+---------+------------------------------------------+

Scenario F-5: Compliance improves between requests 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario is the inverse of scenario F-4. Here, there is an initial rejection due to compliance issues, followed by a mitigation that improves the confidence level. Then a repeat request will be successful and establish a session to an enterprise resource.

**Pre-Condition:** The requestor is identified and could be authenticated, depending on when authentication takes place in the process. The endpoint used is tested and initially considered noncompliant. The endpoint then improves its compliance status and the request is re-issued. A request to access the enterprise resource is granted and a session is established.

**Demonstration:** The requesting endpoint is initially out of policy (not compliant) but can remediate the issue and is successful in a repeated request for the same resource.

**Purpose and Outcome:** This demonstration focuses on the requester's endpoint compliance, which changes from not compliant to compliant before fully establishing a session.

**Table 5 - Scenario F-5 Demonstrations**

+---------+---+--------------+---------+---------+------------------------------------------+
| Demo ID |   | Req EP Compl | Req Loc | RSS Loc | Desired Outcome                          |
+=========+===+==============+=========+=========+==========================================+
| F-5.1   | a | N            | On-Prem | On-Prem | Access Not Successful                    |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.1   | b | Y            | On-Prem | On-Prem | Access Successful                        |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.2   | a | N            | Branch  | On-Prem | Access Not Successful                    |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.2   | b | Y            | Branch  | On-Prem | Access Successful                        |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.3   | a | N            | Remote  | On-Prem | Access Not Successful                    |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.3   | b | Y            | Remote  | On-Prem | Access Successful                        |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.4   | a | N            | On-Prem | Cloud   | Access Not Successful                    |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.4   | b | Y            | On-Prem | Cloud   | Access Successful                        |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.5   | a | N            | Branch  | Cloud   | Access Not Successful                    |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.5   | b | Y            | Branch  | Cloud   | Access Successful                        |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.6   | a | N            | Remote  | Cloud   | Access Not Successful                    |
+---------+---+--------------+---------+---------+------------------------------------------+
| F-5.6   | b | Y            | Remote  | Cloud   | Access Successful                        |
+---------+---+--------------+---------+---------+------------------------------------------+

Scenario F-6: Enterprise-ID Violating Data Use Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to a violation of the enterprise data use policy. In this scenario, an enterprise-ID attempts to transfer a large amount of data from the resource, triggering a data use policy violation. Example: The ID is only allowed to access 1 file/day but attempts to access 2 files/day (note that the time interval here is arbitrary and can be set to whatever makes operation easiest). The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). In this scenario, the subject is playing the role of an insider threat and is intentionally trying to perform actions that violate the enterprise data use policy.

**Pre-Condition**: Valid Enterprise-ID has successfully authenticated to resource and authorized to use resource within data use policy. Endpoint used is compliant with the enterprise security policy (either enterprise-owned or BYOD).

**Demonstration**: A valid Enterprise-ID attempts to access more data than allowed during an authenticated/authorized session. The system detects and responds by terminating the session.

**Purpose and Outcome**: Demonstrating the system responding to violation of the enterprise data security policy by terminating access to the resource.

**Table 6 - Scenario F-6 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome                                         |
+=========+===+========================================+==================+===================================================+=========================================================+
| F-6.1   | a | Ent-Owned                              | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | b | Ent-Owned                              | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | c | Ent-Owned                              | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.1   | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | a | BYOD                                   | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | b | BYOD                                   | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | c | BYOD                                   | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-6.2   | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+

Scenario F-7: Other-ID Violating Data Use Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to a violation of the enterprise data use policy. In this scenario, an other-ID attempts to transfer a large amount of data from the resource, triggering a data use policy violation. Example: The ID is only allowed to access one file/day but attempts to access two files/day. The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). In this scenario, the subject is playing the role of an insider threat and is intentionally trying to perform actions that violate the enterprise data use policy.

**Pre-Condition**: Valid Other-ID has successfully authenticated to resource and authorized to use resource within data use policy. Endpoint used is compliant with the enterprise security policy (either enterprise-owned or BYOD).

**Demonstration**: The enterprise can detect and respond when an Other-ID attempts to violate data use policy.

**Purpose and Outcome**: The enterprise can enforce data use policies on Other-IDs and can terminate access when a violation is detected.

**Table 7 - Scenario F-7 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome                                         |
+=========+===+========================================+==================+===================================================+=========================================================+
| F-7.1   | a | Ent-Owned                              | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | b | Ent-Owned                              | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | c | Ent-Owned                              | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.1   | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | a | BYOD                                   | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | b | BYOD                                   | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | c | BYOD                                   | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-7.2   | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+

Scenario F-8: Enterprise-ID Violating Internet Use Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to a violation of the enterprise Internet use policy. In this scenario, an enterprise-ID has an open session for a resource, but the endpoint sends an HTTP GET to a known bad URL, triggering policy violation. The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). In this scenario, the subject could be playing the role of an insider threat or the endpoint has been compromised, resulting in observed queries that appear to violate the enterprise Internet use policy.

**Pre-Condition**: Valid Enterprise-ID has successfully authenticated to resource and authorized to use resource. The endpoint used by the subject is compliant to the enterprise security policy (either enterprise-owned, BYOD or Guest). The enterprise can monitor outbound queries.

**Demonstration**: A valid Enterprise-ID has an open session and then attempts to open a session to a known bad URL. The system detects and responds by terminating the open session.

**Purpose and Outcome**: The enterprise can detect and respond when Enterprise-ID is using a potentially subverted endpoint and/or detects a violation of Internet use policies.

**Table 8 - Scenario F-8 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome                                         |
+=========+===+========================================+==================+===================================================+=========================================================+
| F-8.1   | a | Ent-Owned                              | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | b | Ent-Owned                              | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | c | Ent-Owned                              | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.1   | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | a | BYOD                                   | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | b | BYOD                                   | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | c | BYOD                                   | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.2   | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | a | Guest                                  | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | B | Guest                                  | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | c | Guest                                  | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | d | Guest                                  | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | e | Guest                                  | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | f | Guest                                  | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | g | Guest                                  | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | h | Guest                                  | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | i | Guest                                  | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | j | Guest                                  | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | k | Guest                                  | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-8.3   | l | Guest                                  | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+

Scenario F-9: Other-ID Violating Internet Use Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to a violation of the enterprise Internet use policy. In this scenario, an other-ID has an open session for a resource, but the endpoint sends an HTTP GET to a known bad URL, triggering policy violation. The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). In this scenario, the subject could be playing the role of an insider threat or the endpoint has been compromised, resulting in observed queries that appear to violate the enterprise Internet use policy.

**Pre-Condition**: Valid other-ID has successfully authenticated to resource and authorized to use resource. The endpoint used by the subject is compliant to the enterprise security policy (either enterprise-owned, BYOD or Guest). The enterprise can monitor outbound queries.

**Demonstration**: A valid other-ID is has an open session and then attempts to open a session to a known bad URL. The system detects and responds by terminating the open session.

**Purpose and Outcome**: The enterprise can detect and respond when other-ID is using a potentially subverted endpoint and/or detects a violation of Internet use policies.

**Table 9 - Scenario F-9 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome                                         |
+=========+===+========================================+==================+===================================================+=========================================================+
| F-9.1   | a | Ent-Owned                              | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | b | Ent-Owned                              | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | c | Ent-Owned                              | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.1   | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | a | BYOD                                   | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | b | BYOD                                   | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | c | BYOD                                   | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.2   | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | a | Guest                                  | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | b | Guest                                  | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | c | Guest                                  | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | d | Guest                                  | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | e | Guest                                  | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | f | Guest                                  | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | g | Guest                                  | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | h | Guest                                  | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | i | Guest                                  | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | j | Guest                                  | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | k | Guest                                  | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-9.3   | l | Guest                                  | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+

Scenario F-10: Enterprise-ID Attempting Unauthorized Access Detection and Response, Access Queries 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to violations of the enterprise authorization policy. In this scenario, an enterprise-ID attempts to access an unauthorized resource (and is prevented). Access privileges to previously authorized resources are then revoked and the Enterprise-ID is prevented from accessing previously authorized resources. The enterprise may take additional action based on the build (quarantine, log out, etc.). The subject is playing the role of an insider threat and is intentionally trying to access unauthorized resources.

**Pre-Condition**: The endpoint used by the subject is compliant to the enterprise security policy (either enterprise-owned, BYOD or Guest). The Enterprise-ID makes an unauthorized request that is flagged.

**Demonstration**: The enterprise can detect and respond when a possibly subverted or insider threat enterprise-ID is attempts to access unauthorized resources.

**Purpose and Outcome**: Previously authorized access privileges being revoked and follow-up access requests for authorized resources is denied.

**Table 10 - Scenario F-10 Demonstrations**

+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| Demo ID      | Subj Type                              | Subject Location | Unauthorized RSS Location | Authorized RSS Location                                      | Desired Outcome             |
+=========+====+========================================+==================+===========================+==============================================================+=============================+
| F-10.1  | a  | Ent-Owned                              | On-prem          | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | b  | Ent-Owned                              | On-prem          | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | c  | Ent-Owned                              | On-prem          | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | d  | Ent-Owned                              | On-prem          | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | e  | Ent-Owned                              | Branch           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | f  | Ent-Owned                              | Branch           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | g  | Ent-Owned                              | Branch           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | h  | Ent-Owned                              | Branch           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | i  | Ent-Owned                              | Remote           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | j  | Ent-Owned                              | Remote           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | k  | Ent-Owned                              | Remote           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | l  | Ent-Owned                              | Remote           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | m  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | n  | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | o  | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | p  | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | q  | Ent-Owned                              | Branch           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | r  | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | s  | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | t  | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | u  | Ent-Owned                              | Remote           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | v  | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | w  | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | x  | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | y  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | z  | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | aa | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ab | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ac | Ent-Owned                              | Branch           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ad | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ae | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | af | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ag | Ent-Owned                              | Remote           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ah | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ai | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | aj | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ak | Ent-Owned                              | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | al | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | am | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | an | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ao | Ent-Owned                              | Branch           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ap | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | aq | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | ar | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | as | Ent-Owned                              | Remote           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | at | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | au | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.1  | av | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | a  | BYOD                                   | On-prem          | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | b  | BYOD                                   | On-prem          | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | c  | BYOD                                   | On-prem          | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | d  | BYOD                                   | On-prem          | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | e  | BYOD                                   | Branch           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | f  | BYOD                                   | Branch           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | g  | BYOD                                   | Branch           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | h  | BYOD                                   | Branch           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | i  | BYOD                                   | Remote           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | j  | BYOD                                   | Remote           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | k  | BYOD                                   | Remote           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | l  | BYOD                                   | Remote           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | m  | BYOD                                   | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | n  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | o  | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | p  | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | q  | BYOD                                   | Branch           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | r  | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | s  | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | t  | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | u  | BYOD                                   | Remote           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | v  | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | w  | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | x  | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | y  | BYOD                                   | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | z  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | aa | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ab | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ac | BYOD                                   | Branch           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ad | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ae | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | af | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ag | BYOD                                   | Remote           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ah | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ai | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | aj | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ak | BYOD                                   | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | al | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | am | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | an | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ao | BYOD                                   | Branch           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ap | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | aq | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | ar | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | as | BYOD                                   | Remote           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | at | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | au | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.2  | av | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful       |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | a  | Guest                                  | On-prem          | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | b  | Guest                                  | On-prem          | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | c  | Guest                                  | On-prem          | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | d  | Guest                                  | On-prem          | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | e  | Guest                                  | Branch           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | f  | Guest                                  | Branch           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | g  | Guest                                  | Branch           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | h  | Guest                                  | Branch           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | i  | Guest                                  | Remote           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | j  | Guest                                  | Remote           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | k  | Guest                                  | Remote           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | l  | Guest                                  | Remote           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | m  | Guest                                  | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | n  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | o  | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | p  | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | q  | Guest                                  | Branch           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | r  | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | s  | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | t  | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | u  | Guest                                  | Remote           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | v  | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | w  | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | x  | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | y  | Guest                                  | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | z  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | aa | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ab | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ac | Guest                                  | Branch           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ad | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ae | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | af | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ag | Guest                                  | Remote           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ah | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ai | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | aj | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ak | Guest                                  | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | al | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | am | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | an | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ao | Guest                                  | Branch           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ap | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | aq | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | ar | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | as | Guest                                  | Remote           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | at | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | au | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-10.3  | av | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+

Scenario F-11: Enterprise-ID Attempting Unauthorized Access Detection and Response, Ongoing Sessions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to violations of the enterprise authorization policy. In this scenario, an enterprise-ID has an open session for a resource, but the endpoint sends an HTTP GET to a known bad URL, triggering policy violation. The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). The subject is playing the role of an insider threat and is intentionally trying to access unauthorized resources.

**Pre-Condition**: Valid enterprise-ID has successfully authenticated to resource and authorized to use resource. The endpoint used by the subject is compliant to the enterprise security policy (either enterprise-owned, BYOD or Guest). The Enterprise-ID makes an authorized request that is flagged that results in current sessions being terminated.

**Demonstration**: The enterprise can detect and respond when a possibly subverted or insider threat enterprise-ID attempts to access unauthorized resources.

**Purpose and Outcome**: Previously authorized access privileges being revoked and follow-up access requests for authorized resources is denied.

**Table 11 - Scenario F-11 Demonstrations**

+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| Demo ID      | Subj Type                              | Subject Location | Unauthorized RSS Location | Authorized RSS Location                                      | Desired Outcome             |
+=========+====+========================================+==================+===========================+==============================================================+=============================+
| F-11.1  | a  | Ent-Owned                              | On-prem          | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | b  | Ent-Owned                              | On-prem          | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | c  | Ent-Owned                              | On-prem          | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | d  | Ent-Owned                              | On-prem          | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | e  | Ent-Owned                              | Branch           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | f  | Ent-Owned                              | Branch           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | g  | Ent-Owned                              | Branch           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | h  | Ent-Owned                              | Branch           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | i  | Ent-Owned                              | Remote           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | j  | Ent-Owned                              | Remote           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | k  | Ent-Owned                              | Remote           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | l  | Ent-Owned                              | Remote           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | m  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | n  | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | o  | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | p  | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | q  | Ent-Owned                              | Branch           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | r  | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | s  | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | t  | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | u  | Ent-Owned                              | Remote           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | v  | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | w  | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | x  | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | y  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | z  | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | aa | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ab | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ac | Ent-Owned                              | Branch           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ad | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ae | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | af | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ag | Ent-Owned                              | Remote           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ah | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ai | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | aj | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ak | Ent-Owned                              | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | al | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | am | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | an | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ao | Ent-Owned                              | Branch           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ap | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | aq | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | ar | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | as | Ent-Owned                              | Remote           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | at | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | au | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.1  | av | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | a  | BYOD                                   | On-prem          | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | b  | BYOD                                   | On-prem          | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | c  | BYOD                                   | On-prem          | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | d  | BYOD                                   | On-prem          | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | e  | BYOD                                   | Branch           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | f  | BYOD                                   | Branch           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | g  | BYOD                                   | Branch           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | h  | BYOD                                   | Branch           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | i  | BYOD                                   | Remote           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | j  | BYOD                                   | Remote           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | k  | BYOD                                   | Remote           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | l  | BYOD                                   | Remote           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | m  | BYOD                                   | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | n  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | o  | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | p  | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | q  | BYOD                                   | Branch           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | r  | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | s  | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | t  | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | u  | BYOD                                   | Remote           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | v  | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | w  | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | x  | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | y  | BYOD                                   | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | z  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | aa | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ab | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ac | BYOD                                   | Branch           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ad | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ae | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | af | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ag | BYOD                                   | Remote           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ah | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ai | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | aj | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ak | BYOD                                   | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | al | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | am | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | an | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ao | BYOD                                   | Branch           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ap | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | aq | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | ar | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | as | BYOD                                   | Remote           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | at | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | au | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.2  | av | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | a  | Guest                                  | On-prem          | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | b  | Guest                                  | On-prem          | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | c  | Guest                                  | On-prem          | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | d  | Guest                                  | On-prem          | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | e  | Guest                                  | Branch           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | f  | Guest                                  | Branch           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | g  | Guest                                  | Branch           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | h  | Guest                                  | Branch           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | i  | Guest                                  | Remote           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | j  | Guest                                  | Remote           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | k  | Guest                                  | Remote           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | l  | Guest                                  | Remote           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | m  | Guest                                  | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | n  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | o  | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | p  | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | q  | Guest                                  | Branch           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | r  | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | s  | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | t  | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | u  | Guest                                  | Remote           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | v  | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | w  | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | x  | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | y  | Guest                                  | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | z  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | aa | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ab | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ac | Guest                                  | Branch           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ad | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ae | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | af | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ag | Guest                                  | Remote           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ah | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ai | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | aj | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ak | Guest                                  | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | al | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | am | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | an | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ao | Guest                                  | Branch           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ap | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | aq | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | ar | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | as | Guest                                  | Remote           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | at | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | au | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-11.3  | av | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+

Scenario F-12: Other-ID Attempting Unauthorized Access Detection and Response, Access Queries 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to violations of the enterprise authorization policy. In this scenario, an Other-ID attempts to access an unauthorized resource (and is prevented). Access privileges to previously authorized resources are then revoked and the Other-ID is prevented from accessing previously authorized resources. The enterprise may take additional action based on the build (quarantine, log out, etc.). The subject is playing the role of an insider threat and is intentionally trying to access unauthorized resources.

**Pre-Condition**: The endpoint used by the subject is compliant to the enterprise security policy (either enterprise-owned, BYOD or Guest). The Other-ID makes an unauthorized request that is flagged.

**Demonstration**: The enterprise can detect and respond when a possibly subverted or insider threat Other-ID attempts to access unauthorized resources.

**Purpose and Outcome**: Previously authorized access privileges being revoked and follow-up access requests for authorized resources are denied.

**Table 12 - Scenario F-12 Demonstrations**

+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| Demo ID      | Subj Type                              | Subject Location | Unauthorized RSS Location | Authorized RSS Location                                      | Desired Outcome             |
+=========+====+========================================+==================+===========================+==============================================================+=============================+
| F-12.1  | a  | Ent-Owned                              | On-prem          | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | b  | Ent-Owned                              | On-prem          | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | c  | Ent-Owned                              | On-prem          | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | d  | Ent-Owned                              | On-prem          | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | e  | Ent-Owned                              | Branch           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | f  | Ent-Owned                              | Branch           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | g  | Ent-Owned                              | Branch           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | h  | Ent-Owned                              | Branch           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | i  | Ent-Owned                              | Remote           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | j  | Ent-Owned                              | Remote           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | k  | Ent-Owned                              | Remote           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | l  | Ent-Owned                              | Remote           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | m  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | n  | Ent-Owned                              | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | o  | Ent-Owned                              | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | p  | Ent-Owned                              | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | q  | Ent-Owned                              | Branch           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | r  | Ent-Owned                              | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | s  | Ent-Owned                              | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | t  | Ent-Owned                              | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | u  | Ent-Owned                              | Remote           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | v  | Ent-Owned                              | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | w  | Ent-Owned                              | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | x  | Ent-Owned                              | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | y  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | z  | Ent-Owned                              | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | aa | Ent-Owned                              | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ab | Ent-Owned                              | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ac | Ent-Owned                              | Branch           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ad | Ent-Owned                              | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ae | Ent-Owned                              | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | af | Ent-Owned                              | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ag | Ent-Owned                              | Remote           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ah | Ent-Owned                              | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ai | Ent-Owned                              | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | aj | Ent-Owned                              | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ak | Ent-Owned                              | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | al | Ent-Owned                              | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | am | Ent-Owned                              | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | an | Ent-Owned                              | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ao | Ent-Owned                              | Branch           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ap | Ent-Owned                              | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | aq | Ent-Owned                              | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | ar | Ent-Owned                              | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | as | Ent-Owned                              | Remote           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | at | Ent-Owned                              | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | au | Ent-Owned                              | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.1  | av | Ent-Owned                              | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | a  | BYOD                                   | On-prem          | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | b  | BYOD                                   | On-prem          | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | c  | BYOD                                   | On-prem          | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | d  | BYOD                                   | On-prem          | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | e  | BYOD                                   | Branch           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | f  | BYOD                                   | Branch           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | g  | BYOD                                   | Branch           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | h  | BYOD                                   | Branch           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | i  | BYOD                                   | Remote           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | j  | BYOD                                   | Remote           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | k  | BYOD                                   | Remote           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | l  | BYOD                                   | Remote           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | m  | BYOD                                   | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | n  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | o  | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | p  | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | q  | BYOD                                   | Branch           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | r  | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | s  | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | t  | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | u  | BYOD                                   | Remote           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | v  | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | w  | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | x  | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | y  | BYOD                                   | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | z  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | aa | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ab | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ac | BYOD                                   | Branch           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ad | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ae | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | af | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ag | BYOD                                   | Remote           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ah | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ai | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | aj | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ak | BYOD                                   | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | al | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | am | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | an | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ao | BYOD                                   | Branch           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ap | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | aq | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | ar | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | as | BYOD                                   | Remote           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | at | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | au | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.2  | av | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful       |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | a  | Guest                                  | On-prem          | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | b  | Guest                                  | On-prem          | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | c  | Guest                                  | On-prem          | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | d  | Guest                                  | On-prem          | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | e  | Guest                                  | Branch           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | f  | Guest                                  | Branch           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | g  | Guest                                  | Branch           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | h  | Guest                                  | Branch           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | i  | Guest                                  | Remote           | On-prem                   | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | j  | Guest                                  | Remote           | Cloud (IaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | k  | Guest                                  | Remote           | Cloud (PaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | l  | Guest                                  | Remote           | Cloud (SaaS)              | On-prem                                                      | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | m  | Guest                                  | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | n  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | o  | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | p  | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | q  | Guest                                  | Branch           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | r  | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | s  | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | t  | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | u  | Guest                                  | Remote           | On-prem                   | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | v  | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | w  | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | x  | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | y  | Guest                                  | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | z  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | aa | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ab | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ac | Guest                                  | Branch           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ad | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ae | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | af | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ag | Guest                                  | Remote           | On-prem                   | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ah | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ai | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | aj | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ak | Guest                                  | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | al | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | am | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | an | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ao | Guest                                  | Branch           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ap | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | aq | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | ar | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | as | Guest                                  | Remote           | On-prem                   | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | at | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | au | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-12.3  | av | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Access not successful.      |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+

Scenario F-13: Other-ID Attempting Unauthorized Access Detection and Response, Ongoing Sessions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to violations of the enterprise authorization policy. In this scenario, an other-ID has an open session for a resource, but the endpoint sends an HTTP GET to a known bad URL, triggering a policy violation. The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). The subject is playing the role of an insider threat and is intentionally trying to access unauthorized resources.

**Pre-Condition**: Valid other-ID has successfully authenticated to resource and is authorized to use resource. The endpoint used by the subject is compliant to the enterprise security policy (either enterprise-owned, BYOD or Guest). The Other-ID makes an authorized request that is flagged as a violation and results in current sessions being terminated.

**Demonstration**: A valid other-ID has an authenticated and authorized session to a resource. The other-ID attempts to perform an unauthorized action or access request. The system responds by terminating active session(s).

**Purpose and Outcome**: The enterprise can detect and respond when a possibly subverted or insider threat other-ID attempts to access unauthorized resources.

**Table 13 - Scenario F-13 Demonstrations**

+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| Demo ID      | Subj Type                              | Subject Location | Unauthorized RSS Location | Authorized RSS Location                                      | Desired Outcome             |
+=========+====+========================================+==================+===========================+==============================================================+=============================+
| F-13.1  | a  | Ent-Owned                              | On-prem          | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | b  | Ent-Owned                              | On-prem          | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | c  | Ent-Owned                              | On-prem          | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | d  | Ent-Owned                              | On-prem          | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | e  | Ent-Owned                              | Branch           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | f  | Ent-Owned                              | Branch           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | g  | Ent-Owned                              | Branch           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | h  | Ent-Owned                              | Branch           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | i  | Ent-Owned                              | Remote           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | j  | Ent-Owned                              | Remote           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | k  | Ent-Owned                              | Remote           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | l  | Ent-Owned                              | Remote           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | m  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | n  | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | o  | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | p  | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | q  | Ent-Owned                              | Branch           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | r  | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | s  | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | t  | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | u  | Ent-Owned                              | Remote           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | v  | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | w  | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | x  | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | y  | Ent-Owned                              | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | z  | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | aa | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ab | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ac | Ent-Owned                              | Branch           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ad | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ae | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | af | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ag | Ent-Owned                              | Remote           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ah | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ai | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | aj | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ak | Ent-Owned                              | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | al | Ent-owned                              | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | am | Ent-owned                              | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | an | Ent-owned                              | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ao | Ent-Owned                              | Branch           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ap | Ent-owned                              | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | aq | Ent-owned                              | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | ar | Ent-owned                              | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | as | Ent-Owned                              | Remote           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | at | Ent-owned                              | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | au | Ent-owned                              | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.1  | av | Ent-owned                              | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | a  | BYOD                                   | On-prem          | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | b  | BYOD                                   | On-prem          | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | c  | BYOD                                   | On-prem          | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | d  | BYOD                                   | On-prem          | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | e  | BYOD                                   | Branch           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | f  | BYOD                                   | Branch           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | g  | BYOD                                   | Branch           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | h  | BYOD                                   | Branch           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | i  | BYOD                                   | Remote           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | j  | BYOD                                   | Remote           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | k  | BYOD                                   | Remote           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | l  | BYOD                                   | Remote           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | m  | BYOD                                   | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | n  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | o  | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | p  | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | q  | BYOD                                   | Branch           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | r  | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | s  | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | t  | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | u  | BYOD                                   | Remote           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | v  | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | w  | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | x  | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | y  | BYOD                                   | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | z  | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | aa | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ab | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ac | BYOD                                   | Branch           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ad | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ae | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | af | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ag | BYOD                                   | Remote           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ah | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ai | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | aj | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ak | BYOD                                   | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | al | BYOD                                   | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | am | BYOD                                   | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | an | BYOD                                   | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ao | BYOD                                   | Branch           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ap | BYOD                                   | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | aq | BYOD                                   | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | ar | BYOD                                   | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | as | BYOD                                   | Remote           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | at | BYOD                                   | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | au | BYOD                                   | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.2  | av | BYOD                                   | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | a  | Guest                                  | On-prem          | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | b  | Guest                                  | On-prem          | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | c  | Guest                                  | On-prem          | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | d  | Guest                                  | On-prem          | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | e  | Guest                                  | Branch           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | f  | Guest                                  | Branch           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | g  | Guest                                  | Branch           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | h  | Guest                                  | Branch           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | i  | Guest                                  | Remote           | On-prem                   | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | j  | Guest                                  | Remote           | Cloud (IaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | k  | Guest                                  | Remote           | Cloud (PaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | l  | Guest                                  | Remote           | Cloud (SaaS)              | On-prem                                                      | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | m  | Guest                                  | On-prem          | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | n  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | o  | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | p  | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | q  | Guest                                  | Branch           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | r  | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | s  | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | t  | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | u  | Guest                                  | Remote           | On-prem                   | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | v  | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | w  | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | x  | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (IaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | y  | Guest                                  | On-prem          | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | z  | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | aa | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ab | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ac | Guest                                  | Branch           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ad | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ae | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | af | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ag | Guest                                  | Remote           | On-prem                   | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ah | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ai | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | aj | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (PaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ak | Guest                                  | On-prem          | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | al | Guest                                  | On-prem          | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | am | Guest                                  | On-prem          | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | an | Guest                                  | On-prem          | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ao | Guest                                  | Branch           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ap | Guest                                  | Branch           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | aq | Guest                                  | Branch           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | ar | Guest                                  | Branch           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | as | Guest                                  | Remote           | On-prem                   | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | at | Guest                                  | Remote           | Cloud (IaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | au | Guest                                  | Remote           | Cloud (PaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+
| F-13.3  | av | Guest                                  | Remote           | Cloud (SaaS)              | Cloud (SaaS)                                                 | Active session terminated.  |
+---------+----+----------------------------------------+------------------+---------------------------+--------------------------------------------------------------+-----------------------------+

Scenario F-14: Enterprise-ID Denied Access Due to Suspicious Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to prevent access by an Enterprise-ID using a suspected compromised endpoint. In this scenario, an enterprise-ID sends an access request, but the subject endpoint has been flagged for suspicious traffic (e.g., doing nmap scans). The enterprise then flags the endpoint and prevents any access by the Enterprise-ID. The ID is not specifically being used in this scenario, and the subverted endpoint may not be performing actions that require authentication by the Enterprise-ID (e.g., access request to another resource).

**Pre-Condition**: Valid Enterprise-ID is authorized to use resource. The endpoint used by the subject has performed suspicious activity. The enterprise can monitor network traffic.

**Demonstration**: A valid enterprise-ID is using a possibly subverted endpoint. The enterprise-ID attempts to access an authorized resource, but the system determines the endpoint is untrusted and denies the access request.

**Purpose and Outcome**: The enterprise can detect and respond when Enterprise-ID is using a potentially subverted endpoint and prevents resource access.

**Table 14 - Scenario F-14 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome             |
+=========+===+========================================+==================+===================================================+=============================+
| F-14.1  | a | Ent-Owned                              | On-prem          | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | b | Ent-Owned                              | Branch           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | c | Ent-Owned                              | Remote           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.1  | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | a | BYOD                                   | On-prem          | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | b | BYOD                                   | Branch           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | c | BYOD                                   | Remote           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.2  | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | a | Guest                                  | On-prem          | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | b | Guest                                  | Branch           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | c | Guest                                  | Remote           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | d | Guest                                  | On-prem          | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | e | Guest                                  | Branch           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | f | Guest                                  | Remote           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | g | Guest                                  | On-prem          | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | h | Guest                                  | Branch           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | i | Guest                                  | Remote           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | j | Guest                                  | On-prem          | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | k | Guest                                  | Branch           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-14.3  | l | Guest                                  | Remote           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+

Scenario F-15: Other-ID Denied Access due to Suspicious Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to prevent access by an Other-ID using a suspected compromised endpoint. In this scenario, an Other-ID sends an access request, but the subject endpoint has been flagged for suspicious traffic (e.g., doing nmap scans). The enterprise then flags the endpoint and prevents any access by the Other-ID. The ID may not play a role in this scenario, the subverted endpoint may not be performing actions that require authentication by the Other-ID (e.g., service call from endpoint service, nmap scan, etc.).

**Pre-Condition**: Valid Other-ID is authorized to use resource. The endpoint used by the subject has performed suspicious activity. The enterprise can monitor network traffic.

**Demonstration**: A valid other-ID is using a possibly subverted endpoint. The other-ID attempts to access an authorized resource, but the system determines the endpoint is untrusted and denies the access request.

**Purpose and Outcome**: The enterprise can detect and respond when Other-ID is using a potentially subverted endpoint and prevents resource access.

**Table 15 - Scenario F-15 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome             |
+=========+===+========================================+==================+===================================================+=============================+
| F-15.1  | a | Ent-Owned                              | On-prem          | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | b | Ent-Owned                              | Branch           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | c | Ent-Owned                              | Remote           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.1  | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | a | BYOD                                   | On-prem          | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | b | BYOD                                   | Branch           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | c | BYOD                                   | Remote           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.2  | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | a | Guest                                  | On-prem          | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | b | Guest                                  | Branch           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | c | Guest                                  | Remote           | On-prem                                           | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | d | Guest                                  | On-prem          | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | e | Guest                                  | Branch           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | f | Guest                                  | Remote           | Cloud (IaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | g | Guest                                  | On-prem          | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | h | Guest                                  | Branch           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | i | Guest                                  | Remote           | Cloud (PaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | j | Guest                                  | On-prem          | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | k | Guest                                  | Branch           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+
| F-15.3  | l | Guest                                  | Remote           | Cloud (SaaS)                                      | Access not successful       |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+-----------------------------+

Scenario F-16: Enterprise-ID Access Terminated Due to Suspicious Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to a suspicious endpoint that is in use. In this scenario, an enterprise-ID has an open session for a resource, but the endpoint is performing suspicious activity (e.g., an nmap scan). The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). The ID is not specifically being tested in this scenario, and the subverted endpoint may not be performing actions that require authentication by the Enterprise-ID.

**Pre-Condition**: Valid Enterprise-ID has successfully authenticated to resource and is authorized to use resource. The enterprise can monitor outbound queries.

**Demonstration**: A valid enterprise-ID has an authenticated and authorized session open to a resource. The system detects suspicious activity from the subject endpoint and terminates active session(s).

**Purpose and Outcome**: The enterprise can detect and respond when Enterprise-ID is using a potentially subverted endpoint.

**Table 16 - Scenario F-16 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome                                         |
+=========+===+========================================+==================+===================================================+=========================================================+
| F-16.1  | a | Ent-Owned                              | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | b | Ent-Owned                              | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | c | Ent-Owned                              | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.1  | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | a | BYOD                                   | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | b | BYOD                                   | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | c | BYOD                                   | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.2  | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | a | Guest                                  | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | b | Guest                                  | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | c | Guest                                  | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | d | Guest                                  | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | e | Guest                                  | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | f | Guest                                  | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | g | Guest                                  | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | h | Guest                                  | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | i | Guest                                  | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | j | Guest                                  | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | k | Guest                                  | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-16.3  | l | Guest                                  | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+

Scenario F-17: Other-ID Access Terminated Due to Suspicious Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the enterprise's ability to detect and respond to suspicious endpoint that is in use. In this scenario, an Other-ID has an open session for a resource, but the endpoint is performing suspicious activity (e.g., an nmap scan). The enterprise then closes the session between the subject and the resource and may take additional action based on the build (quarantine, log out, etc.). The ID may not play a role in this scenario, and the subverted endpoint may not be performing actions that require authentication by the Other-ID.

**Pre-Condition**: Valid Other-ID has successfully authenticated to resource and is authorized to use resource. The enterprise can monitor outbound queries.

**Demonstration**: A valid enterprise-ID has an authenticated and authorized session open to a resource. The system detects suspicious activity from the subject endpoint and terminates active session(s).

**Purpose and Outcome**: The enterprise can detect and respond when Other-ID is using a potentially subverted endpoint.

**Table 17 - Scenario F-17 Demonstrations**

+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| Demo ID     | Subj Type                              | Subject Location | RSS Location                                      | Desired Outcome                                         |
+=========+===+========================================+==================+===================================================+=========================================================+
| F-17.1  | a | Ent-Owned                              | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | b | Ent-Owned                              | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | c | Ent-Owned                              | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | d | Ent-Owned                              | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | e | Ent-Owned                              | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | f | Ent-Owned                              | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | g | Ent-Owned                              | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | h | Ent-Owned                              | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | i | Ent-Owned                              | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | j | Ent-Owned                              | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | k | Ent-Owned                              | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.1  | l | Ent-Owned                              | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | a | BYOD                                   | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | b | BYOD                                   | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | c | BYOD                                   | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | d | BYOD                                   | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | e | BYOD                                   | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | f | BYOD                                   | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | g | BYOD                                   | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | h | BYOD                                   | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | i | BYOD                                   | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | j | BYOD                                   | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | k | BYOD                                   | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.2  | l | BYOD                                   | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | a | Guest                                  | On-prem          | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | b | Guest                                  | Branch           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | c | Guest                                  | Remote           | On-prem                                           | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | d | Guest                                  | On-prem          | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | e | Guest                                  | Branch           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | f | Guest                                  | Remote           | Cloud (IaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | g | Guest                                  | On-prem          | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | h | Guest                                  | Branch           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | i | Guest                                  | Remote           | Cloud (PaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | j | Guest                                  | On-prem          | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | k | Guest                                  | Branch           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
| F-17.3  | l | Guest                                  | Remote           | Cloud (SaaS)                                      | Access stopped (no longer able to connect to resource). |
+---------+---+----------------------------------------+------------------+---------------------------------------------------+---------------------------------------------------------+
