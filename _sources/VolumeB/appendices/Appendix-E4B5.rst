Enterprise 4 Build 5 (E4B5) - SDP and Microsegmentation - AWS Verified Access and Amazon VPC Lattice as PEs
=====================================================================================================================================================

.. include:: /_publication_note.rst

Technologies
------------

E4B5 uses products from AWS, IBM, Mandiant, Okta, and Tenable. Certificates from DigiCert are also used. For more information on these collaborators and the products and technologies that they contributed to this project overall, see :ref:`Collaborators and Their Contributions`. 

E4B5 components consist of AWS Verified Access, Amazon VPC Lattice, Amazon ECS and AWS Lambda Functions, Okta Identity Cloud, Okta Verify App, IBM Security QRadar XDR, Tenable Cloud Security, Mandiant Security Validation (MSV), DigiCert CertCentral, and AWS IaaS.

*Table 1* lists all of the technologies used in Build E4B5. It lists the products used to instantiate each ZTA component and the security function that each component provides. The technologies in this table are used to support zero trust access for cloud resources only, not on-premises resources.

This build is focusing on implementing zero trust in AWS IaaS only.

**Table 1 - E4B5 Products and Technologies**

.. csv-table:: E4B5 Products and Technologies
    :file: csv/E4B5-Table1.csv
    :widths: 20, 30, 50
    :header-rows: 1

Build Architecture
------------------

In this section we present the logical architecture of E4B5. We also describe E4B5's physical architecture and present message flow diagrams for some of its processes.

Logical Architecture
~~~~~~~~~~~~~~~~~~~~

*Figure 1* depicts the logical architecture of E4B5. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), user authorizations, and requesting endpoint health. It also depicts the flow of messages supporting periodic reauthentication of the requesting user, the requesting endpoint, and the resource, as well as periodic verification of requesting endpoint health, all of which must be performed to continually reevaluate access. The labeled steps in *Figure 1* have the same meanings as they do in :ref:`General ZTA Reference Architecture<ArchitectureFigure1>`. However, *Figure 1* includes the specific products that instantiate the architecture of E4B5.

E4B5 was designed with AWS Verified Access and Amazon VPC Lattice serving as PE, PA, and PEP, and Okta Identity Cloud serving as the identity, access, and credential manager. A more detailed depiction of the messages that flow among components to support a user access request can be found in :ref:`Message Flow for a Request to Access a Resource that is Located in Amazon AWS IaaS`.

**Figure 1 - Logical Architecture of E4B5**

|Figure1|

Physical Architecture
~~~~~~~~~~~~~~~~~~~~~

This build is not using on-prem resources and is only focusing on Zero Trust implementation in AWS IaaS. 

*Figure 2* depicts the physical architecture of the AWS infrastructure that has been set up for use by Enterprise 4. As shown, the NCCoE ZTA lab on premises is connected to AWS via direct connect through NOAA/NWAVE, AWS direct connection and NCCoE's management account. From NCCoE's management account's transit gateway, it connects to AWS ZTA lab's transit gateway attachment which is then connected to AVA and to user interface VPC consisting of application load balancer and the application storefront. The application storefront is then connected to the checkout service in the checkout VPC via Amazon VPC lattice. Also, the application storefront is connected to the lambda as the orders service through Amazon VPC lattice.

**Figure 2 - Physical Architecture of the AWS Infrastructure Used by Enterprise 4**

|Figure2|

Message Flow for a Request to Access a Resource that is Located in Amazon AWS IaaS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This section depicts the authentication message flow supported by E4B5. In this flow, a subject who is authorized to access a resource in Amazon AWS (IaaS) requests and receives access to that resource. Access to the resource is authenticated and authorized by AWS Verified Access. The user may be accessing the resource from a non-mobile or mobile device. The device's posture is not being monitored.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Figure 3* depicts the high-level message flow supporting a user who requests access to a resource that is located in Amazon AWS IaaS.

**Figure 3 - Use Case E4B5 - User Requests Access to an Enterprise Resource in Amazon AWS IaaS**

|Figure3|

The message flow depicted in *Figure 2* consists of the following steps:

1. A user initiates access to an enterprise resource that is located on AWS IaaS. The endpoint sends a request packet to the resource that is intercepted by AVA.

2. AVA redirects the user to send a SAML request to the Okta Identity Cloud.

   Note: AWS partners with EPP vendors to perform compliance checks but they are not CRADA partners of this project. Therefore, compliance checks are out of scope.

3. The user's endpoint sends the SAML request to the Okta Identity Cloud, which is located on the internet.

4. Okta prompts for username and password.

5. The user responds with username and password.

6. Okta authenticates the user and verifies the device certificate.

7. Okta challenges the user to provide second-factor authentication by using the Okta Verify App.

8. The user provides the second authentication factor (e.g., biometrics).

9. Okta generates a SAML assertion token and sends it to the user's endpoint.

10. The user's endpoint sends the SAML assertion to AVA. AVA accepts the assertion and grants the access request.

11. The user accesses the resource based on enterprise policies.

.. |Figure1| image:: images/E4B5-Figure1.png
   :alt: This figure depicts the logical architecture of E4B5. It uses numbered arrows to depict the general flow of messages needed for a subject to request access to a resource and have that access request evaluated based on subject identity (both requesting user and requesting endpoint identity), authorizations, and requesting endpoint health.
.. |Figure2| image:: images/E4B5-Figure2.png
   :alt: This figure depicts the physical architecture of E4B5.
.. |Figure3| image:: images/E4B5-Figure3.png
   :alt: This figure depicts the high-level message flow supporting the use case.
