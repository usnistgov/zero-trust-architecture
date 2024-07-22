Use Case H: Data Level Security Scenarios
===========================================

.. include:: /_publication_note.rst

This use case covers subject access requests to data with different levels of classification. In these scenarios, the enterprise uses at least two levels of data classification. The actual levels and terms used are not relevant to the scenarios. A given resource may store or process data of multiple classification levels. Subject IDs can be provisioned with access to the level of data as well as the resource itself, and access privileges can differ between subjects.

Many of these scenarios are similar to scenarios in Use Case B, except that the granularity is at the data classification level and not the resource level. Instead of a resource assumed to have data at a single classification level only, a resource may contain data with multiple classification levels, and subjects may only have privileges to access data at a certain classification, or the enterprise may enact extra protections on data at some classification levels.

Scenario H-1: Full/Limited Access to Resource Data Based on Identity Attributes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the ability to curate or censor data from a resource based on the role or attributes of the subject identity. All identities have some access privileges to the resource, but for differing “levels” of data sensitivity. The classification of the data is not important in this scenario, just that there are at least two levels of access (“high/full” and “low/partial”). In this scenario, the origin of the ID does not matter (both could be Enterprise issued or Other), only that the IDs have different attributes that allow UserA to have full access and UserB to only view a redacted version of the data. Examples of this could include full read access to files versus only able to view file metadata, redacted fields in a database, or other differentiation.

This scenario is similar to Scenario B-1 in that both scenarios deal with two IDs with differing levels of privileges to the same resource. This scenario is a fine-grained version of that scenario, where both IDs have the same abstract privilege (e.g., “read”) but at different levels based on policy around data classification.

**Pre-Condition:** Both IDs can successfully authenticate and are authorized to access the resource to their respective privileges. The subject endpoints are in compliance with the enterprise security policy. The resource data has at least two different data/metadata classifications (high/low), with UserA able to view high-level data and UserB restricted to only low.

**Demonstration:** Two requests for the same enterprise resource are performed by UserA and UserB. UserA can access all data stored in the resource. UserB can only view a redacted or censored version of the same data.

**Purpose and Outcome:** This demonstration focuses on the tailored data access based on attributes or roles associated with a subject ID.

**Table 1 - Scenario H-1 Demonstrations**

+---------+---+----------+--------------------+--------------+------------------------------------------+
| Demo ID     | User     | Location           | Access Level | Desired Outcome                          |
|             |          | Req. > RSS         |              |                                          |
+=========+===+==========+====================+==============+==========================================+
| H-1.1   | a | UserA    | On-Prem -> On-Prem | High         | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.1   | b | UserB    | On-Prem -> On-Prem | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.2   | c | UserA    | On-Prem -> On-Prem | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.2   | d | UserB    | On-Prem -> On-Prem | High         | Access Not Successful                    |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.3   | e | UserA    | Branch -> On-Prem  | High         | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.3   | f | UserB    | Branch -> On-Prem  | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.4   | g | UserA    | Branch -> On-Prem  | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.4   | h | UserB    | Branch -> On-Prem  | High         | Access Not Successful                    |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.5   | i | UserA    | On-Prem -> Cloud   | High         | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.5   | j | UserB    | On-Prem -> Cloud   | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.6   | k | UserA    | On-Prem -> Cloud   | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.6   | l | UserB    | On-Prem -> Cloud   | High         | Access Not Successful                    |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.7   | m | UserA    | Branch -> Cloud    | High         | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.7   | n | UserB    | Branch -> Cloud    | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.8   | o | UserA    | Branch -> Cloud    | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.8   | p | UserB    | Branch -> Cloud    | High         | Access Not Successful                    |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.9   | q | UserA    | Remote -> Cloud    | High         | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.9   | r | UserB    | Remote -> Cloud    | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.10  | s | UserA    | Remote -> Cloud    | Low          | Access Successful                        |
+---------+---+----------+--------------------+--------------+------------------------------------------+
| H-1.10  | t | UserB    | Remote -> Cloud    | High         | Access Not Successful                    |
+---------+---+----------+--------------------+--------------+------------------------------------------+

Scenario H-2: Full/Limited Access to Resource Data Based on Requesting Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the ability to curate or censor data from a resource based on the endpoint used for the request. The classification of the data is not important in this scenario, just that there are at least two levels of access (“high/full” and “low/partial”). The identity has the highest access privileges to the resource, but only when using enterprise-owned endpoints that are in compliance with the enterprise security policy. When using BYOD (or enterprise-owned endpoints out-of-compliance), the access is lowered to only partial. In this scenario, the subject accessing the resource from an enterprise-owned endpoint has full access to all the data on the resource and when using a BYOD/out-of-compliance device, only views a limited version of the data. Examples of this could include full read access to files versus only able to view file metadata, and redacted fields in a database.

**Pre-Condition:** ID can successfully authenticate and is authorized to access the resource. The subject endpoints (enterprise-owned and BYOD) are in compliance with enterprise security policy. The resource data has at least two different data/metadata classifications (low/high).

**Demonstration:** A user can have data access privileges reduced based on the endpoint in use for the access query. In the outcomes, “Access Restricted” means that the subject is not able to access high-level data, only low. It is assumed that if the access can be restricted by the enterprise, it could also be denied (“Access Not Successful”).

**Purpose and Outcome:** This demonstration focuses on the tailored data access based on endpoint identity.

**Table 2 - Scenario H-2 Demonstrations**

+---------+---+---------------+------------------------+------------------------------------------+
| Demo ID     | Endpoint Type | Resource Location      | Desired Outcome                          |
+=========+===+===============+========================+==========================================+
| H-2.1   | a | Ent-Owned     | On-Prem                | Access Successful                        |
+---------+---+---------------+------------------------+------------------------------------------+
| H-2.1   | b | BYOD          | On-Prem                | Access Restricted                        |
+---------+---+---------------+------------------------+------------------------------------------+
| H-2.2   | c | Ent-Owned     | Cloud (IaaS)           | Access Successful                        |
+---------+---+---------------+------------------------+------------------------------------------+
| H-2.2   | d | BYOD          | Cloud (IaaS)           | Access Restricted                        |
+---------+---+---------------+------------------------+------------------------------------------+
| H-2.3   | e | Ent-Owned     | Cloud (PaaS)           | Access Successful                        |
+---------+---+---------------+------------------------+------------------------------------------+
| H-2.3   | f | BYOD          | Cloud (PaaS)           | Access Restricted                        |
+---------+---+---------------+------------------------+------------------------------------------+
| H-2.4   | g | Ent-Owned     | Cloud (SaaS)           | Access Successful                        |
+---------+---+---------------+------------------------+------------------------------------------+
| H-2.4   | h | BYOD          | Cloud (SaaS)           | Access Restricted                        |
+---------+---+---------------+------------------------+------------------------------------------+

Scenario H-3: Internet Access restricted when Accessing High Level Data
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the ability to restrict access requests to public Internet resources when there is an active session to a resource storing data with high classification. In this scenario, the ID type does not matter (Enterprise-ID or Other-ID). The subject endpoint type could be either Enterprise-Owned or BYOD and does not apply to Guest. Subject and resource location may not matter (though the tests require one public Internet resource) but may impact how the policies are enforced.

**Pre-Condition:** ID can successfully authenticate and is authorized to access the resource. The subject endpoints (enterprise-owned and BYOD) are in compliance with the enterprise security policy. The resource data has at least two different data/metadata classifications (low/high). There is a policy that subjects can access a given public Internet resource except when accessing a resource with high-level data.

**Demonstration:** A user can have public Internet access privileges reduced when accessing a resource with data at high level of classification.

**Purpose and Outcome:** This demonstration focuses on restricted Internet access when accessing high-level data.

**Table 3 - Scenario H-3 Demonstrations**

+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| Demo ID     | Resource | Subject Endpoint Type | Location          | Access Level | Desired Outcome                |
|             |          |                       |                   |              |                                |
|             |          |                       | Req. > RSS        |              |                                |
+=========+===+==========+=======================+===================+==============+================================+
| H-3.1   | a | RSSA     | Ent-Owned             | On-Prem ->        | High         | Internet Access Not Successful |
|         |   |          |                       |                   |              |                                |
|         |   |          |                       | On-Prem           |              |                                |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.1   | b | RSSB     | Ent-Owned             | On-Prem ->        | Low          | Internet Access Successful     |
|         |   |          |                       |                   |              |                                |
|         |   |          |                       | On-Prem           |              |                                |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.2   | c | RSSA     | Ent-Owned             | Branch -> On-Prem | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.2   | d | RSSB     | Ent-Owned             | Branch -> On-Prem | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.3   | e | RSSA     | Ent-Owned             | Remote -> On-Prem | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.3   | f | RSSB     | Ent-Owned             | Remote -> On-Prem | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.4   | g | RSSA     | Ent-Owned             | On-Prem -> Cloud  | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.4   | h | RSSB     | Ent-Owned             | On-Prem -> Cloud  | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.5   | i | RSSA     | Ent-Owned             | Branch -> Cloud   | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.5   | j | RSSB     | Ent-Owned             | Branch -> Cloud   | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.6   | k | RSSA     | Ent-Owned             | Remote -> Cloud   | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.6   | l | RSSB     | Ent-Owned             | Remote -> Cloud   | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.7   | m | RSSA     | BYOD                  | On-Prem ->        | High         | Internet Access Not Successful |
|         |   |          |                       |                   |              |                                |
|         |   |          |                       | On-Prem           |              |                                |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.7   | n | RSSB     | BYOD                  | On-Prem ->        | Low          | Internet Access Successful     |
|         |   |          |                       |                   |              |                                |
|         |   |          |                       | On-Prem           |              |                                |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.8   | o | RSSA     | BYOD                  | Branch -> On-Prem | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.8   | p | RSSB     | BYOD                  | Branch -> On-Prem | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.9   | q | RSSA     | BYOD                  | Remote -> On-Prem | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.9   | r | RSSB     | BYOD                  | Remote -> On-Prem | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.10  | s | RSSA     | BYOD                  | On-Prem -> Cloud  | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.10  | t | RSSB     | BYOD                  | On-Prem -> Cloud  | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.11  | u | RSSA     | BYOD                  | Branch -> Cloud   | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.11  | v | RSSB     | BYOD                  | Branch -> Cloud   | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.12  | w | RSSA     | BYOD                  | Remote -> Cloud   | High         | Internet Access Not Successful |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+
| H-3.12  | x | RSSB     | BYOD                  | Remote -> Cloud   | Low          | Internet Access Successful     |
+---------+---+----------+-----------------------+-------------------+--------------+--------------------------------+

Scenario H-4:  Accessing High Level Data Triggers MFA Challenge
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates a requestor being challenged to re-authenticate when accessing data with high classification. In this scenario, the ID type does not matter (Enterprise-ID or Other-ID). The subject endpoint type could be either Enterprise-Owned or BYOD and does not apply to Guest. The subject has privileges to high classified data on the resource and has an active session with the resource handling low classified data. When attempting to access high classified data, a MFA challenge is presented to the user before the access is granted.

**Pre-Condition:** ID can successfully authenticate and is authorized to access the resource. The subject endpoints (enterprise-owned and BYOD) are in compliance with the enterprise security policy. The resource data has at least two different data classifications (low/high). The subject has an active session with the resource.

**Demonstration:** A user must reauthenticate before accessing high classified data even within an active session accessing low classified data.

**Purpose and Outcome:** This demonstration focuses on reauthentication to access high classified data.

**Table 4 - Scenario H-4 Demonstrations**

+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| Demo ID     | Subject Endpoint Type | Location           | Successful MFA Challenge | Desired Outcome       |
|             |                       |                    |                          |                       |
|             |                       | Req. > RSS         |                          |                       |
+=========+===+=======================+====================+==========================+=======================+
| H-4.1   | a | Ent-Owned             | On-Prem -> On-Prem | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.1   | b | Ent-Owned             | On-Prem -> On-Prem | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.2   | c | Ent-Owned             | Branch -> On-Prem  | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.2   | d | Ent-Owned             | Branch -> On-Prem  | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.3   | e | Ent-Owned             | Remote -> On-Prem  | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.3   | f | Ent-Owned             | Remote -> On-Prem  | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.4   | g | Ent-Owned             | On-Prem -> Cloud   | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.4   | h | Ent-Owned             | On-Prem -> Cloud   | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.5   | i | Ent-Owned             | Branch -> Cloud    | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.5   | j | Ent-Owned             | Branch -> Cloud    | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.6   | k | Ent-Owned             | Remote -> Cloud    | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.6   | l | Ent-Owned             | Remote -> Cloud    | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.7   | m | BYOD                  | On-Prem -> On-Prem | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.7   | n | BYOD                  | On-Prem -> On-Prem | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.8   | o | BYOD                  | Branch -> On-Prem  | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.8   | p | BYOD                  | Branch -> On-Prem  | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.9   | q | BYOD                  | Remote -> On-Prem  | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.9   | r | BYOD                  | Remote -> On-Prem  | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.10  | s | BYOD                  | On-Prem -> Cloud   | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.10  | t | BYOD                  | On-Prem -> Cloud   | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.11  | u | BYOD                  | Branch -> Cloud    | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.11  | v | BYOD                  | Branch -> Cloud    | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.12  | w | BYOD                  | Remote -> Cloud    | No                       | Access Not Successful |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+
| H-4.12  | x | BYOD                  | Remote -> Cloud    | Yes                      | Access Successful     |
+---------+---+-----------------------+--------------------+--------------------------+-----------------------+

Scenario H-5:  Just-in-Time Access to High Level Data
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the ability to temporarily increase an ID's privileges to data with higher classification than the ID's base privileges. In this scenario, the ID type does not matter (Enterprise-ID or Other-ID). The subject endpoint type could be either Enterprise-Owned or BYOD and does not apply to Guest. In this scenario, “temporary” applies to only first access, but could be extended to include time limit or number of access requests before access privileges are revoked. This scenario could require human administration in the loop for approval or granting of privileges.

**Pre-Condition:** ID can successfully authenticate and is authorized to access low classification data initially. The subject requests (or attempts, which triggers the request) to access high classification data and the request is granted. The subject endpoints (enterprise-owned and BYOD) are in compliance with the enterprise security policy. The resource data has at least two different data classifications (low/high).

**Demonstration:** A user can be granted temporary access privileges to high level data when needed.

**Purpose and Outcome:** This demonstration focuses on quickly granting access to high level data on a temporary basis (time-based or number of access requests).

**Table 5 - Scenario H-5 Demonstrations**

+---------+---+---------------+------------------------+-----------------------+
| Demo ID     | Endpoint Type | Resource Location      | Desired Outcome       |
+=========+===+===============+========================+=======================+
| H-5.1   | a | Ent-Owned     | On-Prem                | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+
| H-5.1   | b | BYOD          | On-Prem                | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+
| H-5.2   | c | Ent-Owned     | Cloud (IaaS)           | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+
| H-5.2   | d | BYOD          | Cloud (IaaS)           | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+
| H-5.3   | e | Ent-Owned     | Cloud (PaaS)           | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+
| H-5.3   | f | BYOD          | Cloud (PaaS)           | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+
| H-5.4   | g | Ent-Owned     | Cloud (SaaS)           | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+
| H-5.4   | h | BYOD          | Cloud (SaaS)           | Access Successful     |
+---------+---+---------------+------------------------+-----------------------+

Scenario H-6:  Operations Denied When Accessing High Level Data
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates that certain operations can be prevented based on subject endpoint, location, or some other factor. The subject is authorized to access high classified data on the resource, but based on some factor, is prevented from performing certain actions on high classified data. For the scenario, the subject can perform all authorized operations when accessing the high level data using an enterprise-owned endpoint and is on-prem or branch. When using BYOD or remote, the subject can only read/view high classified data but cannot perform other operations. “Other operations” include writing/modifying data, downloading data to endpoint, deleting data, etc.

**Pre-Condition:** ID can successfully authenticate and is authorized to access the resource. The subject endpoints (enterprise-owned and BYOD) are in compliance with the enterprise security policy. The resource data has at least two different data/metadata classifications (low/high).

**Demonstration:** The enterprise can restrict or prevent certain operations on high classified data when accessing resource. This could also include other factors such as access requests originating from a certain location, endpoint type/identity, etc.

**Purpose and Outcome:** This demonstration focuses on restricting privileges based on subject endpoint, location, or some other characteristic of the subject. For this scenario, “Operation Successful” means the subject can perform all authorized operations on the data. “Operation Denied” means that one or more operations (depending on the resource used in the demonstrated build) are prevented.

**Table 6 - Scenario H-6 Demonstrations**

+---------+---+-----------------------+----------+---------------------+-------------------------+
| Demo ID     | Subject Endpoint Type | Subject  | Data Classification | Desired Outcome         |
|             |                       |          |                     |                         |
|             |                       | Location |                     |                         |
+=========+===+=======================+==========+=====================+=========================+
| H-6.1   | a | Ent-Owned             | On-Prem  | Read/View           | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.1   | b | Ent-Owned             | On-Prem  | Other               | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.2   | c | Ent-Owned             | Branch   | Read/View           | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.2   | d | Ent-Owned             | Branch   | Other               | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.3   | e | Ent-Owned             | Remote   | Read/View           | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.3   | f | Ent-Owned             | Remote   | Other               | Operation Denied        |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.4   | g | BYOD                  | On-Prem  | Read/View           | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.4   | h | BYOD                  | On-Prem  | Other               | Operation Denied        |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.5   | i | BYOD                  | Branch   | Read/View           | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.5   | j | BYOD                  | Branch   | Other               | Operation Denied        |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.6   | k | BYOD                  | Remote   | Read/View           | Operation Successful    |
+---------+---+-----------------------+----------+---------------------+-------------------------+
| H-6.6   | l | BYOD                  | Remote   | Other               | Operation Denied        |
+---------+---+-----------------------+----------+---------------------+-------------------------+

Scenario H-7: High Classified Data Has Extra Protection When Stored on Endpoints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the ability to further protect the confidentiality of high classified data when stored on the subject endpoint (i.e., downloading a local copy or file). When the subject downloads or otherwise creates a copy of high classified data on the subject endpoint, that data (or file) is encrypted or has some further protection than the baseline host hardening (full drive encryption does not apply). For example, the subject wishes to download a local copy of high classified data. That downloaded file is encrypted with some key associated with the subject ID, so that the subject ID must pass a challenge (password, PIN, etc.) before performing actions on the local, downloaded copy.

**Pre-Condition:** Subject can successfully authenticate and is authorized to access high classification data. The subject endpoints (enterprise-owned and BYOD) are in compliance with the enterprise security policy. The subject wishes to download a local copy as a file. That local copy is created but encrypted or otherwise protected beyond or outside of the baseline endpoint confidentiality controls (e.g., full disk encryption).

**Demonstration:** High classified data has additional level of protection when stored on endpoints other than the resource.

**Purpose and Outcome:** This demonstration focuses on protecting the confidentiality of high classified data when downloaded. “Download Successful” means a local copy of the high classified data is created with additional encryption.

**Table 7 - Scenario H-7 Demonstrations**

+---------+---+---------------+------------------------+------------------------------------------+
| Demo ID     | Endpoint Type | Resource Location      | Desired Outcome                          |
+=========+===+===============+========================+==========================================+
| H-7.1   | a | Ent-Owned     | On-Prem                | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
| H-7.1   | b | BYOD          | On-Prem                | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
| H-7.2   | c | Ent-Owned     | Cloud (IaaS)           | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
| H-7.2   | d | BYOD          | Cloud (IaaS)           | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
| H-7.3   | e | Ent-Owned     | Cloud (PaaS)           | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
| H-7.3   | f | BYOD          | Cloud (PaaS)           | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
| H-7.4   | g | Ent-Owned     | Cloud (SaaS)           | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
| H-7.4   | h | BYOD          | Cloud (SaaS)           | Download Successful                      |
+---------+---+---------------+------------------------+------------------------------------------+
