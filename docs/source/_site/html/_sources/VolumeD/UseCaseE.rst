Use Case E: Guest: No-ID Access
=====================================

.. include:: /_publication_note.rst

Scenario E-1: Guest requests public internet access
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For No-ID access, the only deciding factor is the type of device used and any observable compliance state or sent traffic of the device. Authentication/authorization is not a factor (No-ID). Enterprise resource compliance is likewise assumed, as resources would not be visible otherwise.

**Pre-Condition:** The requestor does not need to authenticate (i.e., guest access). Per configuration, the requestor is authorized with default universal access to the resource (i.e., no authentication or authorization checks are performed). A request to access the enterprise resource is granted and a session is established. The resource is assumed to be in compliance.

**Demonstration:** Systems can differentiate between device classifications and perform some action based on policy to restrict privileged devices (i.e., enterprise-managed, BYOD) based on endpoint compliance policy.

**Purpose and Outcome:** This demonstration focuses on device identification and compliance (when applicable).

**Table 1 - Scenario E-1 Demonstrations**

+---------+---+---------------------+-----------------+-------------------+
| Demo ID     | Location of Subject | Access          | Desired Outcome   |
+=========+===+=====================+=================+===================+
| E-1.1   | a | On-Prem             | Public resource | Access Successful |
+---------+---+---------------------+-----------------+-------------------+
| E-1.1   | b | On-Prem             | Public internet | Access Successful |
+---------+---+---------------------+-----------------+-------------------+
| E-1.2   | a | Branch              | Public resource | Access Successful |
+---------+---+---------------------+-----------------+-------------------+
| E-1.2   | b | Branch              | Public internet | Access Successful |
+---------+---+---------------------+-----------------+-------------------+
