Enterprise 3 Build 4 (E3B4) - SDP - F5 BIG-IP, F5 NGINX Plus, Forescout eyeControl, and Forescout eyeExtend as PEs Product Guides
===================================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E3B4. For additional details on E3B4's logical and physical architectures, please refer to :ref:`architecture and builds`.

F5 BIG-IP
---------

BIG-IP provides various functions including traffic management, single sign-on and secure web tunneling. In this phase of the build, it was primarily used as the zero trust PE and PEP that provided access to protected back-end applications via a web-based access portal.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See :ref:`F5 BIG-IP<F5BIGIP>`.

Integration with Microsoft Intune
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

BIG-IP integrates with Microsoft Intune to retrieve device compliance which is a prerequisite before access is granted to resources. Follow the steps at `BIG-IP APM Integration with Microsoft Intune <https://techdocs.f5.com/en-us/edge-client-7-2-2/big-ip-access-policy-manager-edge-client-and-application-configuration-7-2-2/configuring-access-policy-manager-for-mdm-applications.html#supporting-intune-deviceid>`__ to ensure that device compliance is appropriately retrieved by BIG-IP.

Integration with Microsoft Sentinel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See :ref:`F5 BIG-IP<F5BIGIP>`.

BIG-IP Configuration in Azure IaaS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

BIG-IP Web Application Firewall (WAF) was configured in Azure IaaS to protect internal applications in an Azure Virtual network.

Use the instructions at `Create an Azure VNET <https://learn.microsoft.com/en-us/azure/virtual-network/quick-create-portal>`__ to create a virtual network.

Use the instructions at `Configure a BIG-IP WAF <https://docs.cloud.f5.com/docs/how-to/app-security/web-app-firewall>`__ to configure the WAF.

F5 NGINX Plus 
--------------

NGINX Service Mesh, which uses NGINX Plus instances, provides an infrastructure layer that enables the efficient management and security configuration of microservices. The NGINX Service Mesh, which uses NGINX Plus instances as PEPs for each pod, was deployed in this build.

Use the instructions at `Configure NGINX Service Mesh <https://docs.nginx.com/nginx-service-mesh/>`__ to install and configure a service mesh.

F5 Access App
-------------

In addition to providing an additional compliance check, the F5 access app provides Intune certificate details that BIG-IP uses to query Microsoft Intune for device compliance for Intune-managed devices.

The F5 access app can be installed from the App Store or from the Play Store on iOS and Android devices, respectively. You can also use the steps in `Installing F5 access app using Microsoft Intune <https://techdocs.f5.com/en-us/apm-f5-access/apm-f5-access-windows-10-using-intune/c_f5_access_windows_chapter_title_overview.html#conceptId>`__ to install it on Intune-managed devices.

Microsoft AD
------------

AD provides centralized management of users, computers, and network services. It also provides authentication and authorization services for directory objects in an enterprise network. In our build, AD was used as the source of truth for identities and was then replicated to Azure AD. Azure AD was used as the identity provider and remained synced with the on-premises AD.

To deploy AD in your environment, use the guide found at `AD DS Deployment <https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/ad-ds-deployment>`__.

Microsoft Azure AD
------------------

For installation, configuration, and integration instructions, refer to :ref:`Microsoft Azure AD<MicrosoftAzureAD>`.

Microsoft Azure AD Identity Governance
--------------------------------------

For installation, configuration, and integration instructions, refer to :ref:`Microsoft Azure AD Identity Governance<MicrosoftAzureADGov>`.

Microsoft Intune
----------------

For installation, configuration, and integration instructions, refer to :ref:`Microsoft Endpoint Manager<MicrosoftEndpoint>`.

Microsoft Sentinel
------------------

For installation, configuration, and integration instructions, refer to :ref:`Microsoft Sentinel<microsoft-sentinel>`.

Tenable.io
----------

For installation, configuration, and integration instructions, refer to :ref:`Tenable.io<tenable-io>`.

Tenable.ad
----------

For installation, configuration, and integration instructions, refer to :ref:`Tenable.ad<tenable-ad>`.

Tenable NNM
-----------

For installation, configuration, and integration instructions, refer to :ref:`Tenable NNM<tenable-nnm>`.

Mandiant Security Validation (MSV)
-----------------------------------

For installation, configuration, and integration instructions, refer to :ref:`Mandiant Security Validation (MSV)<mandiant-msv>`.

Forescout eyeSight
------------------

For installation, configuration, and integration instructions, refer to :ref:`Forescout eyeSight<ForescouteyeSight>`.

Forescout eyeControl
--------------------

For installation, configuration, and integration instructions, refer to :ref:`Forescout eyeControl<ForescouteyeControl>`.

Forescout eyeSegment
--------------------

For installation, configuration, and integration instructions, refer to :ref:`Forescout eyeSegment<ForescouteyeSegment>`.

Forescout eyeExtend
-------------------

For installation, configuration, and integration instructions, refer to :ref:`Forescout eyeExtend<ForescouteyeExtend>`.

Microsoft Azure (IaaS)
----------------------

For installation, configuration, and integration instructions, refer to :ref:`Microsoft Azure (IaaS)<MicrosoftAzureIaaS>`.

DigiCert CertCentral
---------------------

For installation, configuration, and integration instructions, refer to :ref:`DigiCert CertCentral<digicert-certcentral>`.