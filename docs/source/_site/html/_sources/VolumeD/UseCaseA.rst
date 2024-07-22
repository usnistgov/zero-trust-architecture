Use Case A: Discovery and Identification of IDs, Assets, and Data Flows
========================================================================

.. include:: /_publication_note.rst

NIST SP 800-207 discusses the discovery and cataloging of all enterprise IDs, assets, and data flows as the initial step before migrating to a ZTA. An enterprise needs to identify and understand the workflows used in business processes, the IDs used, and the resources involved. Then it can move on to creating policies around those workflows. This use case covers this initial exercise.

The following discovery use cases did not originally appear in the Project Description but were subsequently included to reflect the full ZTA migration process described in NIST SP 800-207.

Scenario A-1: Discovery and authentication of endpoint assets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Discovery here is focused on detecting assets and flows on the network, mapping them to identified assets and flows, and providing access accordingly.

**Pre-Condition**: Enterprise-owned components (RSS and EP) have already undergone initial onboarding for the enterprise, and BYODs have already registered with the enterprise. Any necessary agents, certificates, etc. have been installed. Non-onboarded enterprise-owned components as well as non-registered BYODs are treated the same as unknown guest devices. BYOD devices must have a software agent installed that allows inspection of the devices to create a report of the device hygiene (e.g., look for accepted virus scanner and approved operating system [OS]). The enterprise infrastructure is a macrosegmented local network with an “enterprise” segment with resources that can only be accessed by authorized Enterprise-IDs and a “guest” segment with access to the public internet only.

**Demonstration**: Connect the device to the network and demonstrate network connectivity.

**Purpose and Outcome**: This scenario demonstrates the capability to authenticate assets at a specific location and provide enterprise network access. The enterprise endpoint management system should be able to differentiate between enterprise-owned and non-owned endpoints and place devices on the correct network segment.

**Table 1 - Scenario A-1 Demonstrations**

+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
| Demo ID     | Subj Type | Onboarded/Registered  | Auth Stat| Compl | Subj Loc | Desired Outcome                          |
+=========+===+===========+=======================+==========+=======+==========+==========================================+
| A-1.1   | a | RSS       | Y                     | A+       | Y     | On-Prem  | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | b | RSS       | Y                     | A+       | N     | On-Prem  | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | c | RSS       | Y                     | A-       | ---   | On-Prem  | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | d | RSS       | N                     | ---      | ---   | On-Prem  | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | e | EP        | Y                     | A+       | Y     | On-Prem  | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | f | EP        | Y                     | A+       | N     | On-Prem  | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | g | EP        | Y                     | A-       | ---   | On-Prem  | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | h | EP        | N                     | ---      | ---   | On-Prem  | Access to Public Network                 |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | i | BYOD      | Y                     | A+       | Y     | On-Prem  | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | j | BYOD      | Y                     | A+       | N     | On-Prem  | Limited Access to Network                |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | k | BYOD      | Y                     | A-       | ---   | On-Prem  | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | l | BYOD      | N                     | ---      | ---   | On-Prem  | Access to Public Network                 |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | m | Guest Dev.| ---                   | ---      | ---   | On-Prem  | Access to Public Network                 |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
| A-1.2   | a | RSS       | Y                     | A+       | Y     | Branch   | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | b | RSS       | Y                     | A+       | N     | Branch   | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | c | RSS       | Y                     | A-       | ---   | Branch   | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | d | RSS       | N                     | ---      | ---   | Branch   | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | e | EP        | Y                     | A+       | Y     | Branch   | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | f | EP        | Y                     | A+       | N     | Branch   | Limited Access to Network                |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | g | EP        | Y                     | A-       | ---   | Branch   | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | h | EP        | N                     | ---      | ---   | Branch   | Access to Public Network                 |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | i | BYOD      | Y                     | A+       | Y     | Branch   | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | j | BYOD      | Y                     | A+       | N     | Branch   | Limited Access to Network                |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | k | BYOD      | Y                     | A-       | ---   | Branch   | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | l | BYOD      | N                     | ---      | ---   | Branch   | Access to Public Network                 |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | m | Guest Dev.| ---                   | ---      | ---   | Branch   | Access to Public Network                 |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
| A-1.3   | a | EP        | Y                     | A+       | Y     | Remote   | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | b | EP        | Y                     | A+       | N     | Remote   | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | c | EP        | Y                     | A-       | ---   | Remote   | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | d | BYOD      | Y                     | A+       | Y     | Remote   | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | e | BYOD      | Y                     | A+       | N     | Remote   | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | f | BYOD      | Y                     | A-       | ---   | Remote   | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
| A-1.4   | a | RSS       | Y                     | A+       | Y     | Cloud    | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | b | RSS       | Y                     | A+       | N     | Cloud    | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | c | RSS       | Y                     | A-       | ---   | Cloud    | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | d | RSS       | N                     | ---      | ---   | Cloud    | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | e | EP        | Y                     | A+       | Y     | Cloud    | Access to Network                        |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | f | EP        | Y                     | A+       | N     | Cloud    | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+
|         | g | EP        | Y                     | A-       | ---   | Cloud    | No Access to Network                     |
+---------+---+-----------+-----------------------+----------+-------+----------+------------------------------------------+

Scenario A-2: Reauthentication of identified assets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once an asset is identified and authenticated, continuous re-authentication is necessary.

**Pre-Condition:** The asset (user endpoint, resource) underwent previous authentication and is ready for operation.

**Demonstration:** The asset is reauthenticated and will either pass or fail reauthentication.

**Purpose and Outcome:** This scenario demonstrates the proper reauthentication of an asset and performs the desired action accordingly.

**Table 2 - Scenario A-2 Demonstrations**

+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| Demo ID     | Subj Type | Onboarded/Registered  | Auth Stat | Compl | Subj Loc | Desired Outcome                          |
+=========+===+===========+=======================+===========+=======+==========+==========================================+
| A-2.1   | a | RSS       | Y                     | RA+       | Y     | On-Prem  | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | b | RSS       | Y                     | RA+       | N     | On-Prem  | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | c | RSS       | Y                     | RA-       | ---   | On-Prem  | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | d | EP        | Y                     | RA+       | Y     | On-Prem  | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | e | EP        | Y                     | RA+       | N     | On-Prem  | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | f | EP        | Y                     | RA-       | ---   | On-Prem  | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | g | BYOD      | Y                     | RA+       | Y     | On-Prem  | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | h | BYOD      | Y                     | RA+       | N     | On-Prem  | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.1   | i | BYOD      | Y                     | RA-       | ---   | On-Prem  | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | a | RSS       | Y                     | RA+       | Y     | Branch   | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | b | RSS       | Y                     | RA+       | N     | Branch   | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | c | RSS       | Y                     | RA-       | ---   | Branch   | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | d | EP        | Y                     | RA+       | Y     | Branch   | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | e | EP        | Y                     | RA+       | N     | Branch   | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | f | EP        | Y                     | RA-       | ---   | Branch   | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | g | BYOD      | Y                     | RA+       | Y     | Branch   | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | h | BYOD      | Y                     | RA+       | N     | Branch   | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.2   | i | BYOD      | Y                     | RA-       | ---   | Branch   | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.3   | a | EP        | Y                     | RA+       | Y     | Remote   | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.3   | b | EP        | Y                     | RA+       | N     | Remote   | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.3   | c | EP        | Y                     | RA-       | ---   | Remote   | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.3   | d | BYOD      | Y                     | RA+       | Y     | Remote   | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.3   | e | BYOD      | Y                     | RA+       | N     | Remote   | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.3   | f | BYOD      | Y                     | RA-       | ---   | Remote   | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.4   | a | RSS       | Y                     | RA+       | Y     | Cloud    | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.4   | b | RSS       | Y                     | RA+       | N     | Cloud    | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.4   | c | RSS       | Y                     | RA-       | ---   | Cloud    | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.4   | d | EP        | Y                     | RA+       | Y     | Cloud    | Keep Access to Network                   |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.4   | e | EP        | Y                     | RA+       | N     | Cloud    | Max. Limited Access to Network           |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+
| A-2.4   | f | EP        | Y                     | RA-       | ---   | Cloud    | Terminate Access to Network              |
+---------+---+-----------+-----------------------+-----------+-------+----------+------------------------------------------+

Scenario A-3: Discovery of transaction flows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates the monitoring of transactions between endpoints. Transactions include user access to a resource or service-to-service communication.

**Pre-Condition:** User (Enterprise-ID or Other-ID) has a set of privileges to a resource and can successfully authenticate. Requesting endpoints are considered successfully authenticated. Some mechanism is present either on the endpoints or along the communication path that can observe and log actions.

**Demonstration**: Logs are produced that map user access requests, API calls, etc. between resources. The logs may be on a third resource.

**Purpose and Outcome:** This scenario demonstrates the discovery and recording of metadata of traffic flows between resources and user access requests/actions. The actual inspection of traffic (e.g., inspection of data) is not necessary.

**Table 3 - Scenario A-3 Demonstrations**

+---------+---+---------------+---------+---------+------------------------------------------+
| Demo ID     | Endpoint Type | Req Loc | RSS Loc | Desired Outcome                          |
+=========+===+===============+=========+=========+==========================================+
| A-3.1   | a | USER          | On-Prem | On-Prem | User request and action is recorded      |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.1   | b | RSS/Service   | On-Prem | On-Prem | API call is recorded                     |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.2   | a | USER          | On-Prem | Cloud   | User request and action is recorded      |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.2   | b | RSS/Service   | On-Prem | Cloud   | API call is recorded                     |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.3   | a | USER          | Branch  | On-Prem | User request and action is recorded      |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.3   | b | RSS/Service   | Branch  | On-Prem | API call is recorded                     |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.4   | a | USER          | Branch  | Cloud   | User request and action is recorded      |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.4   | b | RSS/Service   | Branch  | Cloud   | API call is recorded                     |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.5   | a | USER          | Remote  | On-Prem | User request and action is recorded      |
+---------+---+---------------+---------+---------+------------------------------------------+
| A-3.6   | a | USER          | Remote  | Cloud   | User request and action is recorded      |
+---------+---+---------------+---------+---------+------------------------------------------+
