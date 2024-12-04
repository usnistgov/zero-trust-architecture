Enterprise 4 Build 5 (E4B5) - SDP and Microsegmentation - AWS Verified Access and Amazon VPC Lattice as PE
===================================================================================================================================================================

.. include:: /_publication_note.rst


This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E4B5. For additional details on E4B5's logical and physical architectures, please refer to :ref:`architecture and builds`.

AWS Verified Access 
---------------------------

AWS Verified Access provides secure access to corporate resources within the AWS cloud without the need for a VPN solution.

To create and use AWS Verified Access, use the information found at `Tutorial: Get started with Verified Access <https://docs.aws.amazon.com/verified-access/latest/ug/getting-started.html>`__. Items that need to be installed and configured are:

-  Create an AWS Verified Access Instance

-  Configure and attach a Verified Access trust provider to the AWS Verified Access instance

-  Create a Verified Access group

-  Add your application to be protected by creating a Verified Access endpoint

-  Configure DNS settings

-  Configure access policies

Note: For this build, access to resources is based on the user's identity. For example, an employee may have access to all resources while a contractor can only access certain resources. AWS Verified Access leveraged Okta user groups to verify user identity.


Amazon VPC Lattice
------------------------------------

For this build, resources were developed using AWS services deployed within the Amazon VPC Lattice. The Amazon VPC Lattice is a managed application networking service for connecting, securing, and monitoring resources within AWS VPCs. For information about Amazon VPC Lattice, please refer to the `Amazon VPC Lattice documentation <https://docs.aws.amazon.com/vpc-lattice/latest/ug/what-is-vpc-lattice.html#accessing>`__.

Note: Auth policies were leveraged to allow or deny communications from a source resource. Refer to the `Manage access to VPC Lattice services <https://docs.aws.amazon.com/vpc-lattice/latest/ug/access-management-overview.html>`__ document to create Auth policies. 

AWS IaaS
----------

For installation, configuration, and integration instructions, refer to :ref:`AWS IaaS<aws-iaas>`.

Okta Identity Cloud
-------------------

For installation, configuration, and integration instructions, refer to :ref:`Okta Identity Cloud<okta-identity-cloud>`.

For this build, users logging into a resource are authenticated via Okta with a password for the first factor and Okta Verify for the second factor. This process is completed when a user attempts to access the resource and AWS Verified Access redirects the user to authenticate via Okta. Use the link for `AWS Verified Access Integration with 3rd party identity providers <https://aws.amazon.com/blogs/networking-and-content-delivery/aws-verified-access-integration-with-3rd-party-identity-providers/>`__ to configure Okta and AWS Verified Access.

Okta Verify App
---------------

For installation, configuration, and integration instructions, refer to :ref:`Okta Verify App<okta-verify-app>`.

IBM Security QRadar XDR
-----------------------

For installation, configuration, and integration instructions, refer to :ref:`IBM Security QRadar XDR<ibm-qradar>`.

Tenable Cloud Security
-----------------------

Tenable Cloud Security provides visibility and risk assessment of cloud identities and resources on an organization, including information about permissions, account usage, and security configurations. For installation, configuration, and integration instructions, refer to the `Onboard AWS <https://docs.tenable.com/cloud-security.htm>`__ document from the Tenable website. In this document, there are two methods of configuration: Onboard AWS Organization and Onboard AWS Account. For this build, we use the Onboard AWS Organization instructions. Prior to configuration, review the considerations for each configuration method and any AWS costs associated with the setup.

Note: A Tenable account is needed to access and download the “Onboard AWS” document. 

Mandiant Security Validation (MSV)
-----------------------------------

For installation, configuration, and integration instructions, refer to :ref:`Mandiant Security Validation (MSV)<mandiant-msv>`.

DigiCert CertCentral
---------------------

For installation, configuration, and integration instructions, refer to :ref:`DigiCert CertCentral<digicert-certcentral>`.