Use Case G: Service-Service Interactions
================================================

.. include:: /_publication_note.rst

This use case covers non-person entities and API calls between services. This covers automated processes as well. It is assumed MFA is not possible as there is no human subject involved in the session establishment. The enterprise should be able to uniquely identify (and authenticate) both the subject and resource in each test scenario. The method of this could vary and is not dictated in these scnearios. Endpoints where the service is running could be physical or virtual and include services running in containers.

Scenario G-1: Service Calls Between Resources 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates service-to-service communication between resources located on enterprise-operated infrastructure (on-prem or branch). Both resources (subject and requested resource) are considered authenticated and in compliance. The subject can be authorized or unauthorized to perform the action, as indicated in the table.

**Pre-Condition**: Two subjects, one authorized to perform the action and the other not authorized. All actors are in compliance with the enterprise security posture and authenticated to all relevant enterprise systems. All communications (successful and failed) are logged.

**Demonstration**: The subject system performs an action that involves an API call, or other service-to-service communication to another resource. All communication is logged.

**Purpose and Outcome**: This scenario demonstrates how the enterprise architecture prevents unauthorized communication between services and records all communication attempts (successful and prevented).

**Table 1 - Scenario G-1 Demonstrations**

+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| Demo ID     | Subj. Location                              | Authorized | RSS Loc | Desired Outcome             |
+=========+===+=============================================+============+=========+=============================+
| G-1.1   | a | On-prem                                     | Yes        | On-Prem | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | b | On-prem                                     | No         | On-Prem | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | c | Branch                                      | Yes        | On-Prem | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | d | Branch                                      | No         | On-Prem | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | e | Remote (IaaS)                               | Yes        | On-Prem | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | f | Remote (IaaS)                               | No         | On-Prem | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | g | Remote (PaaS)                               | Yes        | On-Prem | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | h | Remote (PaaS)                               | No         | On-Prem | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | i | Remote (SaaS)                               | Yes        | On-Prem | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.1   | j | Remote (SaaS)                               | No         | On-Prem | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | a | On-prem                                     | Yes        | Branch  | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | b | On-Prem                                     | No         | Branch  | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | c | Branch                                      | Yes        | Branch  | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | d | Branch                                      | No         | Branch  | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | e | Remote (IaaS)                               | Yes        | Branch  | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | f | Remote (IaaS)                               | No         | Branch  | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | g | Remote (PaaS)                               | Yes        | Branch  | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | h | Remote (Paas)                               | No         | Branch  | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | i | Remote (SaaS)                               | Yes        | Branch  | Access successful           |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+
| G-1.2   | j | Remote (Saas)                               | No         | Branch  | Access not successful       |
+---------+---+---------------------------------------------+------------+---------+-----------------------------+

Scenario G-2: Service Calls to Cloud-Based Resources
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates service-to-service communication between resources located on enterprise-operated infrastructure (on-prem or branch) and cloud-based assets. Both resources (subject and requested resource) are considered authenticated and in compliance. The subject can be authorized or unauthorized to perform the action, as indicated in the table. The requested resource is IaaS, PaaS, or SaaS.

**Pre-Condition**: Two subjects, one authorized to perform the action and the other not authorized. All actors are in compliance and authenticated to all relevant enterprise systems. All communications (successful and failed) are logged.

**Demonstration**: The subject system performs an action that involves an API call or some other service-to-service communication to a resource. All communication is logged.

**Purpose and Outcome**: This scenario demonstrates how the enterprise architecture prevents unauthorized communication between services and records all communication attempts (successful and prevented).

**Table 2 - Scenario G-2 Demonstrations**

+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| Demo ID     | Subj. Location                              | Authorized | RSS Type | Desired Outcome             |
+=========+===+=============================================+============+==========+=============================+
| G-2.1   | a | On-prem                                     | Yes        | IaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.1   | b | On-prem                                     | No         | IaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.1   | c | Branch                                      | Yes        | IaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.1   | d | Branch                                      | No         | IaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.1   | e | Remote                                      | Yes        | IaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.1   | f | Remote                                      | No         | IaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.2   | a | On-prem                                     | Yes        | PaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.2   | b | On-prem                                     | No         | PaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.2   | c | Branch                                      | Yes        | PaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.2   | d | Branch                                      | No         | PaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.2   | e | Remote                                      | Yes        | PaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.2   | f | Remote                                      | No         | PaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.3   | a | On-prem                                     | Yes        | SaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.3   | b | On-Prem                                     | No         | SaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.3   | c | Branch                                      | Yes        | SaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.3   | d | Branch                                      | No         | SaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.3   | e | Remote                                      | Yes        | SaaS     | Access successful           |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+
| G-2.3   | f | Remote                                      | No         | SaaS     | Access not successful       |
+---------+---+---------------------------------------------+------------+----------+-----------------------------+

Scenario G-3: Service Calls between Cloud-Based Resources
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates service-to-service communication between resources located on separate cloud-based resources. Both resources (subject and requested resource) are considered authenticated and in compliance. The subject can be authorized or unauthorized to perform the action, as indicated in the table. The resources are IaaS, PaaS, or SaaS.

**Pre-Condition**: Two subjects, one authorized to perform the action and the other not authorized. All actors are in compliance and authenticated to all relevant enterprise systems. All communications (successful and failed) are logged.

**Demonstration**: The subject system performs an action that involves an API call or some other service-to-service communication to a resource. All communication is logged.

**Purpose and Outcome**: This scenario demonstrates how the enterprise architecture prevents unauthorized communication between services and records all communication attempts (successful and prevented).

**Table 3 - Scenario G-3 Demonstrations**

+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| Demo ID     | Subj. Type                              | Authorized | RSS Type | Desired Outcome             |
+=========+===+=========================================+============+==========+=============================+
| G-3.1   | a | IaaS                                    | Yes        | IaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.1   | b | IaaS                                    | No         | IaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.1   | c | PaaS                                    | Yes        | IaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.1   | d | PaaS                                    | No         | IaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.1   | e | SaaS                                    | Yes        | IaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.1   | f | SaaS                                    | No         | IaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.2   | a | IaaS                                    | Yes        | PaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.2   | b | IaaS                                    | No         | PaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.2   | c | PaaS                                    | Yes        | PaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.2   | d | PaaS                                    | No         | PaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.2   | e | SaaS                                    | Yes        | PaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.2   | f | SaaS                                    | No         | PaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.3   | a | IaaS                                    | Yes        | SaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.3   | b | IaaS                                    | No         | SaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.3   | c | PaaS                                    | Yes        | SaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.3   | d | PaaS                                    | No         | SaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.3   | e | SaaS                                    | Yes        | SaaS     | Access successful           |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+
| G-3.3   | f | SaaS                                    | No         | SaaS     | Access not successful       |
+---------+---+-----------------------------------------+------------+----------+-----------------------------+

Scenario G-4: Service Calls between Containers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This scenario demonstrates service-to-service communication between resources located on separate containers, both in the same runtime or part of a larger Kubernetes pod(s) deployment. Both resources (subject and requested resource) are considered authenticated and in compliance. The subject can be authorized or unauthorized to perform the action, as indicated in the table. The subject is either another container in a single container runtime (e.g., Docker), in the same Kubernetes pod, or in a different Kubernetes pod from the requested resource.

**Pre-Condition**: Two subjects, one authorized to perform the action and the other unauthorized. All actors are in compliance and authenticated to all relevant enterprise systems. All communications (successful and failed) are logged.

**Demonstration**: The subject system performs an action that involves an API call or some other service-to-service communication to a resource. The enterprise can prevent unauthorized service-to-server communication. All communication is logged regardless of the outcome.

**Purpose and Outcome**: This scenario demonstrates how the enterprise architecture prevents unauthorized communication between services and records all communication attempts (successful and prevented).

**Table 4 - Scenario G-4 Demonstrations**

+---------+---+---------------------------------------------+---------------+-----------------------------+
| Demo ID     | Subj. Location                              | Authorized    | Desired Outcome             |
+=========+===+=============================================+===============+=============================+
| G-4.1   | a | Bare runtime                                | Yes           | Access successful           |
+---------+---+---------------------------------------------+---------------+-----------------------------+
| G-4.1   | b | Bare runtime                                | No            | Access not successful       |
+---------+---+---------------------------------------------+---------------+-----------------------------+
| G-4.1   | c | Separate pod                                | Yes           | Access successful           |
+---------+---+---------------------------------------------+---------------+-----------------------------+
| G-4.1   | d | Separate pod                                | No            | Access not successful       |
+---------+---+---------------------------------------------+---------------+-----------------------------+
| G-4.1   | e | Same pod                                    | Yes           | Access successful           |
+---------+---+---------------------------------------------+---------------+-----------------------------+
| G-4.1   | f | Same pod                                    | No            | Access successful           |
+---------+---+---------------------------------------------+---------------+-----------------------------+

Scenario G-5: Service to Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this demonstration, an enterprise service reaches out to an enterprise managed endpoint to perform some action (e.g., maintenance, reconfiguration, etc.). User IDs are not directly involved in this scenario.

**Pre-Condition**: There is no active session from a subject to an enterprise resource. Both the subject endpoint and resource may be in compliance with enterprise security posture or expected to be in compliance after the session is completed. Service is located on-premises or as PaaS/SaaS (IaaS does not make sense as it is a service that is running in the cloud).

**Demonstration**: An enterprise service establishes a session with an endpoint to perform some administrative task, then closes the connection.

**Purpose and Outcome**: The enterprise can push administrative actions to enterprise endpoints in a secure manner.

**Table 5 - Scenario G-5 Demonstrations**

+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| Demo ID |   | Service Location                              | Endpoint Location | Endpoint Type                                      | Desired Outcome             |
+=========+===+===============================================+===================+====================================================+=============================+
| G-5.1   | a | On-Prem                                       | On-prem           | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | b | On-Prem                                       | Branch            | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | c | On-Prem                                       | Remote            | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | d | On-Prem                                       | On-prem           | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | e | On-Prem                                       | Branch            | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | f | On-Prem                                       | Remote            | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | g | PaaS                                          | On-prem           | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | h | PaaS                                          | Branch            | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | i | PaaS                                          | Remote            | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | j | PaaS                                          | On-prem           | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | k | PaaS                                          | Branch            | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | l | PaaS                                          | Remote            | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | m | SaaS                                          | On-prem           | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | n | SaaS                                          | Branch            | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | o | SaaS                                          | Remote            | Ent-Owned                                          | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | p | SaaS                                          | On-prem           | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | q | SaaS                                          | Branch            | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
| G-5.1   | r | SaaS                                          | Remote            | BYOD                                               | Access Successful           |
+---------+---+-----------------------------------------------+-------------------+----------------------------------------------------+-----------------------------+
