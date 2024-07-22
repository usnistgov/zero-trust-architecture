Use Case C: Collaboration: Federated-ID Access
==================================================

.. include:: /_publication_note.rst

Scenario C-1: Full resource access using an enterprise endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a successfully authenticated Federated-ID accessing an enterprise-controlled resource. In this scenario, the maximum access configuration of the requester for the enterprise-managed resource is set to full access.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with full access to the resource.

**Demonstration:** The requestor using a Federated-ID will attempt to access an enterprise resource using an enterprise-owned endpoint.

**Purpose and Outcome:** This demonstration focuses on the endpoint location with endpoint/resource compliance (Compl).

**Table 1 - Scenario C-1 Demonstrations**

+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Demo ID     | Req EP Compl | Req Loc | RSS EP Compl | RSS Loc | Desired Outcome                                                                                                                                                        |
+=========+===+==============+=========+==============+=========+========================================================================================================================================================================+
| C-1.1   | a | Y            | On-Prem | Y            | On-Prem | Access Successful                                                                                                                                                      |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.1   | b | N            | On-Prem | Y            | On-Prem | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.1   | c | Y            | On-Prem | N            | On-Prem | Access Limited                                                                                                                                                         |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.1   | d | N            | On-Prem | N            | On-Prem | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Comment: In this set of demonstrations, the desired outcome will be to deny access to the resource in case the endpoint is not compliant. If the endpoint is compliant but the resource is not compliant, the access is restricted.    |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.2   | a | Y            | Branch  | Y            | On-Prem | Access Successful                                                                                                                                                      |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.2   | b | N            | Branch  | Y            | On-Prem | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.3   | a | Y            | Remote  | Y            | On-Prem | Access Successful                                                                                                                                                      |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.3   | b | N            | Remote  | Y            | On-Prem | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.4   | a | Y            | On-Prem | Y            | Cloud   | Access Successful                                                                                                                                                      |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.4   | b | N            | On-Prem | Y            | Cloud   | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.4   | c | Y            | On-Prem | N            | Cloud   | Access Limited                                                                                                                                                         |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.4   | d | N            | On-Prem | N            | Cloud   | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.5   | a | Y            | Branch  | Y            | Cloud   | Access Successful                                                                                                                                                      |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.5   | b | N            | Branch  | Y            | Cloud   | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.6   | a | Y            | Remote  | Y            | Cloud   | Access Successful                                                                                                                                                      |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-1.6   | b | N            | Remote  | Y            | Cloud   | Access Not Successful                                                                                                                                                  |
+---------+---+--------------+---------+--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Scenario C-2: Limited resource access using an enterprise endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a successfully authenticated Federated-ID accessing an enterprise-controlled resource. In this scenario, the maximum access configuration of the requester for the enterprise-managed resource is set to limited access.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with limited access to the resource.

**Demonstration:** The requestor using a Federated-ID will attempt to access an enterprise resource using an enterprise-owned endpoint.

**Purpose and Outcome:** This demonstration focuses on the endpoint location with endpoint/resource compliance (Compl).

**Table 2 - Scenario C-2 Demonstrations**

+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Demo ID     | Req EP Compl | Req Loc | RSS EP Compl | RSS Loc | Desired Outcome                                                                                                                                                    |
+=========+===+==============+=========+==============+=========+====================================================================================================================================================================+
| C-2.1   | a | Y            | On-Prem | Y            | On-Prem | Access Limited                                                                                                                                                     |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.1   | b | N            | On-Prem | Y            | On-Prem | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.1   | c | Y            | On-Prem | N            | On-Prem | Access Limited                                                                                                                                                     |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.1   | d | N            | On-Prem | N            | On-Prem | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Comment: In this set of demonstrations, the desired outcome will be to deny access to the resource in case the endpoint is not compliant. If the endpoint is compliant but the resource is not compliant, the access is restricted.|
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.2   | a | Y            | Branch  | Y            | On-Prem | Access Limited                                                                                                                                                     |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.2   | b | N            | Branch  | Y            | On-Prem | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.3   | a | Y            | Remote  | Y            | On-Prem | Access Limited                                                                                                                                                     |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.3   | b | N            | Remote  | Y            | On-Prem | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.4   | a | Y            | On-Prem | Y            | Cloud   | Access Limited                                                                                                                                                     |
+---------+---+--------------+         +--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.4   | b | N            | On-Prem | Y            | Cloud   | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.4   | c | Y            | On-Prem | N            | Cloud   | Access Limited                                                                                                                                                     |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.4   | d | N            | On-Prem | N            | Cloud   | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.5   | a | Y            | Branch  | Y            | Cloud   | Access Limited                                                                                                                                                     |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.5   | b | N            | Branch  | Y            | Cloud   | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.6   | a | Y            | Remote  | Y            | Cloud   | Access Limited                                                                                                                                                     |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-2.6   | b | N            | Remote  | Y            | Cloud   | Access Not Successful                                                                                                                                              |
+---------+---+--------------+---------+--------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Scenario C-3: Limited internet access using an enterprise endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a successfully authenticated Federated-ID accessing a non-enterprise-controlled resource in the public internet using an enterprise-owned endpoint device with limited internet access.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with limited access to the Internet.

**Demonstration:** The requestor using a Federated-ID will attempt to access two resources located in the public Internet. The resources are not controlled by the enterprise. One resource is allowed, the other one is blocked.

**Purpose and Outcome:** This demonstration focuses on the endpoint resource compliance with access of non-enterprise-controlled resources on the internet by a requester with internet access using an enterprise-controlled resource.

**Table 3 - Scenario C-3 Demonstrations**

+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| Demo ID     | Req EP Compl | Req Loc | RSS Access Policy | RSS Loc  | Desired Outcome                          |
+=========+===+==============+=========+===================+==========+==========================================+
| C-3.1   | a | Y            | On-Prem | Allowed RSS 1     | Internet | Access Successful                        |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.1   | b | N            | On-Prem | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.1   | c | Y            | On-Prem | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.1   | d | N            | On-Prem | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.2   | a | Y            | Branch  | Allowed RSS 1     | Internet | Access Successful                        |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.2   | b | N            | Branch  | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.2   | c | Y            | Branch  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.2   | d | N            | Branch  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.3   | a | Y            | Remote  | Allowed RSS 1     | Internet | Access Successful                        |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.3   | b | N            | Remote  | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.3   | c | Y            | Remote  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-3.3   | d | N            | Remote  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+

Scenario C-4: No internet access using enterprise owned endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a successfully authenticated Federated-ID accessing a non-enterprise-controlled resource in the public internet using a enterprise-owned endpoint device with internet access disabled. In this scenario, the Enterprise-ID may be allowed to access certain public internet resources but there is a separate policy for the endpoint which is not allowed any public internet access. The endpoint policy overrides the user identity policy and no requests for internet based resources are allowed.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor ID is authorized with limited access to the public Internet but not when coming from a particular enterprise owned endpoint that is not allowed to access the public internet.

**Demonstration:** The requestor using a Federated-ID will attempt to access two resources both located in the public Internet. The resources are not controlled by the enterprise. When using an endpoint that is denied all internet access, the endpoint policy overrides the identity policy and all internet access requests are denied.

**Purpose and Outcome:** This demonstration focuses on the endpoint access policies of non-enterprise-controlled resources on the internet by an endpoint that is not permitted internet access.

**Table 4 - Scenario C-4 Demonstrations**

+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| Demo ID     | Req EP Compl | Req Loc | RSS Access Policy | RSS Loc  | Desired Outcome                          |
+=========+===+==============+=========+===================+==========+==========================================+
| C-4.1   | a | Y            | On-Prem | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.1   | b | N            | On-Prem | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.1   | c | Y            | On-Prem | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.1   | d | N            | On-Prem | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.2   | a | Y            | Branch  | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.2   | b | N            | Branch  | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.2   | c | Y            | Branch  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.2   | d | N            | Branch  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.3   | a | Y            | Remote  | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.3   | b | N            | Remote  | Allowed RSS 1     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.3   | c | Y            | Remote  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-4.3   | d | N            | Remote  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+

Scenario C-5: Internet access using BYOD
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a successfully authenticated Federated-ID accessing a resource on the Internet using privately owned devices. For this scenario, additional testing of the endpoint is unnecessary because the access is restricted by policy due to the device being BYOD.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with limited access to the Internet. Both resources RSS1 and RSS2 are not managed by the enterprise. For example, RSS1 could be a gambling site and RSS2 could be a search engine. Endpoint compliance may not be fully determined in these scenarios.

**Demonstration:** The requestor using a Federated-ID will attempt to access two resources both located in the public Internet. The resources are not controlled by the enterprise. One resource is allowed, the other one is blocked. The endpoint itself is of type BYOD.

**Purpose and Outcome:** This demonstration focuses on BYOD endpoint compliance with access of non-enterprise-controlled resources on the internet by a requester with limited internet access.

**Table 5 - Scenario C-5 Demonstrations**

+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| Demo ID     | Req EP Compl | Req Loc | RSS Access Policy | RSS Loc  | Desired Outcome                          |
+=========+===+==============+=========+===================+==========+==========================================+
| C-5.1   | a | Y            | On-Prem | Allowed RSS 1     | Internet | Access Successful                        |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.1   | b | N            | On-Prem | Allowed RSS 1     | Internet | Access Not Successful/Limited            |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.1   | c | Y            | On-Prem | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.1   | d | N            | On-Prem | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.2   | a | Y            | Branch  | Allowed RSS 1     | Internet | Access Successful                        |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.2   | b | N            | Branch  | Allowed RSS 1     | Internet | Access Not Successful/Limited            |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.2   | c | Y            | Branch  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.2   | d | N            | Branch  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.3   | a | Y            | Remote  | Allowed RSS 1     | Internet | Access Successful                        |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.3   | b | N            | Remote  | Allowed RSS 1     | Internet | Access Not Successful/Limited            |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.3   | c | Y            | Remote  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+
| C-5.3   | d | N            | Remote  | Blocked RSS 2     | Internet | Access Not Successful                    |
+---------+---+--------------+---------+-------------------+----------+------------------------------------------+

Scenario C-6: Access resources using BYOD
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a successfully authenticated federated ID accessing an enterprise-controlled resource using privately owned devices. For this scenario, additional testing for the endpoint is not necessary because the access is restricted by policy due to the device being BYOD.

**Pre-Condition:** The requestor is identified and authenticated. Per configuration, the requestor is authorized with full access to the resource. The system setup must lower the access level to the resource into a restricted access mode due to the usage of BYOD.

**Demonstration:** The requestor using a federated ID will attempt to access an enterprise resource using a privately owned device.

**Purpose and Outcome:** This demonstration focuses on the endpoint device (BYOD), lowering access level rights, and endpoint compliance and location.

**Table 6 - Scenario C-6 Demonstrations**

+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Demo ID |   | Req. EP Compl | Req. Loc | RSS EP Compl | RSS Loc | Desired Outcome                                                                                                                                               |
+=========+===+===============+==========+==============+=========+===============================================================================================================================================================+
| C-6.1   | a | Y             | On-Prem  | Y            | On-Prem | Access Limited                                                                                                                                                |
+---------+---+---------------+----------+--------------+         +---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.1   | b | N             |          | Y            |         | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+         +---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.1   | c | Y             |          | N            |         | Access Limited/Restricted                                                                                                                                     |
+---------+---+---------------+----------+--------------+         +---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.1   | d | N             |          | N            |         | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Comment: In this set of demonstrations, the desired outcome will be to deny access to the resource in case the endpoint is not compliant. If the endpoint is compliant, but the resource is not compliant, access is restricted.|
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.2   | a | Y             | Branch   | Y            | On-Prem | Access Limited                                                                                                                                                |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.2   | b | N             | Branch   | Y            | On-Prem | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.3   | a | Y             | Remote   | Y            | On-Prem | Access Limited                                                                                                                                                |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.3   | b | N             | Remote   | Y            | On-Prem | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.4   | a | Y             | On-Prem  | Y            | Cloud   | Access Limited                                                                                                                                                |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.4   | b | N             | On-Prem  | Y            | Cloud   | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.4   | c | Y             | On-Prem  | N            | Cloud   | Access Limited/Restricted                                                                                                                                     |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.4   | d | N             | On-Prem  | N            | Cloud   | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.5   | a | Y             | Branch   | Y            | Cloud   | Access Limited                                                                                                                                                |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.5   | b | N             | Branch   | Y            | Cloud   | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.6   | a | Y             | Remote   | Y            | Cloud   | Access Limited                                                                                                                                                |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
| C-6.6   | b | N             | Remote   | Y            | Cloud   | Access Not Successful                                                                                                                                         |
+---------+---+---------------+----------+--------------+---------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

Scenario C-7: Stolen credential using an enterprise endpoint 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a stolen credential employing an enterprise endpoint.

**Pre-Condition:** The requestor's credential is stolen and is used to attempt accessing an enterprise resource using an enterprise endpoint that may or may not also be stolen (e.g., laptop that still has a smart token/smart card inserted). When the requester's credentials is marked “Flagged Stolen”, MFA should fail.

**Demonstration:** The requestor, using a stolen federated ID, will attempt to access an enterprise resource using an enterprise endpoint; the enterprise endpoint may be stolen as well.

**Purpose and Outcome:** This demonstration focuses on the requester's federated ID as well as the status of the user's credentials (e.g., smartcard, hardware token, or endpoint device) as either reported stolen or not reported stolen.

**Table 7 - Scenario C-7 Demonstrations**

+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| Demo ID |   | Req            | Req Loc | Req EP         | RSS Loc | Desired Outcome                          |
|         |   | Credential     |         |                |         |                                          |
+=========+===+================+=========+================+=========+==========================================+
| C-7.1   | a | Active         | On-Prem | Active         | On-Prem | Access Successful                        |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.1   | b | Active         | On-Prem | Flagged Stolen | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.1   | c | Flagged Stolen | On-Prem | Active         | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.1   | d | Flagged Stolen | On-Prem | Flagged Stolen | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.2   | a | Active         | Branch  | Active         | On-Prem | Access Successful                        |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.2   | b | Active         | Branch  | Flagged Stolen | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.2   | c | Flagged Stolen | Branch  | Active         | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.2   | d | Flagged Stolen | Branch  | Flagged Stolen | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.3   | a | Active         | Remote  | Active         | On-Prem | Access Successful                        |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.3   | b | Active         | Remote  | Flagged Stolen | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.3   | c | Flagged Stolen | Remote  | Active         | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.3   | d | Flagged Stolen | Remote  | Flagged Stolen | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.4   | a | Active         | On-Prem | Active         | Cloud   | Access Successful                        |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.4   | b | Active         | On-Prem | Flagged Stolen | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.4   | c | Flagged Stolen | On-Prem | Active         | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.4   | d | Flagged Stolen | On-Prem | Flagged Stolen | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.5   | a | Active         | Branch  | Active         | Cloud   | Access Successful                        |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.5   | b | Active         | Branch  | Flagged Stolen | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.5   | c | Flagged Stolen | Branch  | Active         | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.5   | d | Flagged Stolen | Branch  | Flagged Stolen | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.6   | a | Active         | Remote  | Active         | Cloud   | Access Successful                        |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.6   | b | Active         | Remote  | Flagged Stolen | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.6   | c | Flagged Stolen | Remote  | Active         | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+
| C-7.6   | d | Flagged Stolen | Remote  | Flagged Stolen | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+----------------+---------+------------------------------------------+

Scenario C-8: Stolen credential using BYOD 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario deals with a request using a stolen credential employing a BYOD endpoint.

**Pre-Condition:** The requestor's credential is stolen and is used to attempt accessing an enterprise resource using a privately owned device (BYOD). For scenarios where the requester's credentials is marked “Flagged Stolen”, MFA should fail. For BOYD devices determined to be out of compliance with the enterprise security policy would not be granted access regardless of subject authentication results (see C-5/6).

**Demonstration:** The requestor using a stolen federated ID will attempt to access an enterprise resource using a BYOD endpoint.

**Purpose and Outcome:** This demonstration focuses on the requester's ID credentials (e.g., smartcard, hardware token, or endpoint device) as either reported stolen or not reported stolen.

**Table 8 - Scenario C-8 Demonstrations**

+---------+---+----------------+---------+------------+---------+------------------------------------------+
| Demo ID |   | Req            | Req Loc | Req EP     | RSS Loc | Desired Outcome                          |
|         |   | Credential     |         | Compliance |         |                                          |
+=========+===+================+=========+============+=========+==========================================+
| C-8.1   | a | Active         | On-Prem | Y          | On-Prem | Access Successful                        |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.1   | b | Flagged Stolen | On-Prem | Y          | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.2   | a | Active         | Branch  | Y          | On-Prem | Access Successful                        |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.2   | b | Flagged Stolen | Branch  | Y          | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.3   | a | Active         | Remote  | Y          | On-Prem | Access Successful                        |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.3   | b | Flagged Stolen | Remote  | Y          | On-Prem | Access Not Successful                    |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.4   | a | Active         | On-Prem | Y          | Cloud   | Access Successful                        |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.4   | b | Flagged Stolen | On-Prem | Y          | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.5   | a | Active         | Branch  | Y          | Cloud   | Access Successful                        |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.5   | b | Flagged Stolen | Branch  | Y          | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.6   | a | Active         | Remote  | Y          | Cloud   | Access Successful                        |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
| C-8.6   | b | Flagged Stolen | Remote  | Y          | Cloud   | Access Not Successful                    |
+---------+---+----------------+---------+------------+---------+------------------------------------------+
