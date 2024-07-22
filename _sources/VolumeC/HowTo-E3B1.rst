Enterprise 3 Build 1 (E3B1) - EIG Crawl - Azure AD Conditional Access (later renamed Entra Conditional Access) as PE Product Guides
=======================================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all of the products used to implement E3B1. For additional details on E3B1's logical and physical architectures, please refer to :ref:`Enterprise 3 Build 1 (E3B1)<Enterprise 3 Build 1 (E3B1) - EIG Crawl - Azure AD Conditional Access (later renamed *Entra Conditional Access*) as PE>`.

Microsoft Azure Active Directory (AD)
-------------------------------------

.. _MicrosoftAzureAD:

Azure AD is a SaaS identity and access management platform. No installation steps are required. You will need to create your organization's instance of Azure AD and configure it to allow your users access to applications that use it for authentication and authorization.

1. After logging in to portal.azure.com, `create an Azure AD Tenant <https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-access-create-new-tenant>`__.

2. `Create a connection between your on-premises AD and Azure AD <https://docs.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-install-express>`__ to replicate user, group, and authentication information from your AD to Azure AD.

3. Configure the Azure AD Tenant to enable Single Sign-On Password Reset (SSPR). This gives users the ability to reset their passwords from https://aka.ms/sspr or from within their profile in Azure AD. This will be effective for both their AD and Azure AD accounts.

4. `Configure password writeback <https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-sspr-writeback>`__, which enables password changes in Azure AD to be replicated back to the on-premises AD.

5. The conditional access feature in Azure AD specifies conditions under which a user would be given access to a resource or application that uses Azure AD for authentication. MFA was configured as a requirement for access to all applications. `Configure MFA for all users. <https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa>`__

6. Access to resources based on device compliance was implemented as an essential feature in this solution. Access would only be granted to a user if the client device is compliant. Compliance is reported to Azure AD by Microsoft Endpoint Manager. `Enable this feature, Conditional Access Device Compliance. <https://docs.microsoft.com/en-us/mem/intune/protect/create-conditional-access-intune>`__

7. Configure an enterprise application, GitLab, to use Azure AD for authentication:

   a. GitLab was configured to directly authenticate to Azure AD using the SAML protocol. `GitLab must first be registered in Azure AD <https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app>`__ before Azure AD can be configured as the application's IdP.

   b. `Configure Azure AD as a SAML IdP for the GitLab application. <https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/add-application-portal-setup-sso>`__ Once that is implemented, access attempts to the target application will be redirected to Azure AD for authentication and authorization.

Microsoft Endpoint Manager
--------------------------

.. _MicrosoftEndpoint:

Microsoft Endpoint Manager is a cloud-based service that focuses on mobile device management (MDM) and mobile application management (MAM).

Configuration and Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add and verify a custom domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To connect an organization's domain name with Intune, a DNS registration needs to be configured. This gives users a familiar domain when connecting to Intune and using resources. Use the information found at the hyperlink to `create a custom domain <https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/add-custom-domain>`__.

Add users
^^^^^^^^^

Use the information at the hyperlink to `add users to Intune <https://learn.microsoft.com/en-us/mem/intune/fundamentals/users-add>`__.

Enroll devices in Microsoft Intune
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Enrolling devices allows them to receive configuration profiles and compliance policies. Configuration profiles configure features and settings on devices. Compliance policies help devices meet an organization's rules.

1. `Get an Apple MDM push certificate and add it to Endpoint Manager. <https://docs.microsoft.com/en-us/mem/intune/enrollment/apple-mdm-push-certificate-get>`__ This certificate is required to enroll iOS/iPadOS devices. Then enroll iOS devices in Microsoft Intune.

2.  `Create an iOS enrollment profile. <https://docs.microsoft.com/en-us/mem/intune/enrollment/ios-user-enrollment>`__ An enrollment profile defines the settings applied to a group of devices during enrollment.

3.  `Enroll Android devices in Microsoft Intune. <https://docs.microsoft.com/en-us/mem/intune/enrollment/android-enroll>`__ To enable Android Enterprise, an administrative Google account needs to be connected to the Intune tenant.

4.  `Create an iOS compliance policy in Microsoft Intune. <https://docs.microsoft.com/en-us/mem/intune/protect/create-compliance-policy>`__ It will be evaluated before access is allowed from iOS devices.

5. `Create an Android compliance policy in Microsoft Intune. <https://docs.microsoft.com/en-us/mem/intune/protect/create-compliance-policy>`__ It will be evaluated before access is allowed from Android devices.

6. `Create an iOS/macOS configuration profile <https://docs.microsoft.com/en-us/mem/intune/configuration/device-features-configure#create-the-profile>`__ for iOS or Mac devices.

Configure conditional access rules
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Conditional access is used to control the devices and apps that can connect to company resources. Use the information in the hyperlink to `create device-based conditional access policies <https://learn.microsoft.com/en-us/mem/intune/protect/create-conditional-access-intune>`__.

Manage applications
^^^^^^^^^^^^^^^^^^^

**iOS/iPadOS:** Use the instructions at `Add iOS Store Apps <https://docs.microsoft.com/en-us/mem/intune/apps/store-apps-ios>`__ to select apps from the iOS/iPadOS store that will be approved for installation on your managed iOS or iPadOS devices.

**Android**: For this build we added Managed Google Play apps. Managed Google Play is Google's enterprise app store which serves as a source of applications for Android Enterprise in Intune. Use the instructions at `Add Android Store Apps <https://docs.microsoft.com/en-us/mem/intune/apps/store-apps-android>`__ to select apps that will be approved for installation and made available to your managed devices.

**Windows**: Use the information provided at `select approved apps <https://learn.microsoft.com/en-us/mem/intune/apps/apps-add-office365>`__ to choose which apps should be added to your Windows devices.

There is more than one way to configure Windows apps in Intune. We configured the app using App suite information. For other ways, `refer to the Microsoft documentation <https://docs.microsoft.com/en-us/mem/intune/apps/apps-add-office365>`__.

Microsoft Defender for Endpoint
-------------------------------

.. _microsoft-defender:

Microsoft Defender for Endpoint provides endpoint protection, detection, and response to threats.

Configuration and Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Enable Microsoft Defender for Endpoint
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use the information at `Configure Microsoft Defender for Endpoint in Microsoft Intune \| Microsoft Learn <https://learn.microsoft.com/en-us/mem/intune/protect/advanced-threat-protection-configure>`__ to enable Defender for Endpoint.

1. Use the information in the provided hyperlink to `onboard devices <https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/onboard-configure?view=o365-worldwide>`__. Once devices are onboarded, threat signals and vulnerability information are automatically collected from them.

2. You can optionally `enable supervised mode on iOS devices <https://learn.microsoft.com/en-us/mem/intune/remote-actions/device-supervised-mode>`__ using information at the hyperlink. Supervised mode gives administrators greater control over corporate-owned devices.

3. Alerts and security incidents can be viewed and responded to by accessing the Defender for Endpoint cloud component. Use the information in the hyperlink to `view and respond to discovered threats <https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response?view=o365-worldwide>`__.

Create Endpoint Detection and Response policy (Windows 10 and later)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Endpoint detection and response (EDR) policies are used to detect advanced attacks in near real-time. Use the information in the hyperlink to `create an EDR policy <https://learn.microsoft.com/en-us/mem/intune/protect/endpoint-security-edr-policy>`__.

Create an antivirus policy
^^^^^^^^^^^^^^^^^^^^^^^^^^

An antivirus policy defines the behavior of the antivirus software agent on the endpoint. Use the information in the hyperlinks to `create an antivirus policy <https://learn.microsoft.com/en-us/mem/intune/protect/endpoint-security-antivirus-policy>`__ and `configure antivirus policy settings <https://learn.microsoft.com/en-us/mem/intune/protect/antivirus-microsoft-defender-settings-windows>`__.

Create Defender compliance policy
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Compliance policies can help protect organizational data by requiring users and devices to meet defined security requirements. Use the information in the hyperlink to `create a Defender for Endpoint compliance policy <https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-conditional-access?view=o365-worldwide#step-3-create-the-compliance-policy-in-intune>`__.

Microsoft Defender Antivirus
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Microsoft Defender Antivirus is leveraged by Microsoft Defender by Endpoint. It is anti-malware software built into Windows client devices that detects threats and malware on client devices and quarantines infected files. Defender Antivirus is enabled by default.

1. `Check the status of real-time protection <https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-security-center-antivirus?view=o365-worldwide#ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app>`__ to ensure it's on.

2. `Turn real-time protection on or off <https://support.microsoft.com/en-us/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963>`__.

Microsoft Sentinel
------------------

.. _microsoft-sentinel:

Microsoft Sentinel is a cloud-native SIEM and SOAR system. It can be used for security analytics, threat intelligence, attack detection, and threat response.

There is no need to install Sentinel, as it is a managed service. Instead, it needs to be enabled and configured in your Azure environment. It also needs a workspace to store and correlate ingested data.

1. `Enable Sentinel and configure a workspace. <https://docs.microsoft.com/en-us/azure/sentinel/quickstart-onboard#enable-microsoft-sentinel->`__

2. Use the general instructions found at `Connector to Data Sources <https://docs.microsoft.com/en-us/azure/sentinel/quickstart-onboard#connect-data-sources>`__ to enable log forwarding to Sentinel from various devices, systems, and services. Each data source will have to be connected independently from other data sources, so you must perform this step once per data source. In this build, Azure AD, Endpoint Manager, Defender for Endpoint, Microsoft 365, and Tenable.io were configured to send logs using this method.

3. The Log Analytics Agent is a log forwarder that accepts syslog and Common Event Format (CEF) formatted logs and then forwards the logs to Sentinel. If you have a product or device without a native Sentinel integration, `install and configure the Log Analytics Agent on a virtual machine. <https://docs.microsoft.com/en-us/azure/sentinel/connect-log-forwarder?tabs=rsyslog>`__ Once completed, the log forwarder will be able to receive syslog data on UDP port 514. Then configure the product or device that will be the data source to send logs via syslog to the log forwarder using the product's instructions.

Microsoft 365
--------------------

.. _microsoft-365:

Microsoft 365 is a suite of SaaS-based productivity applications used for a variety of activities such as word processing, accounting, creating presentations, email, and others. Microsoft 365 was enabled in the environment and was used as a set of protected target applications. Use the information at `Activate Microsoft 365 <https://support.microsoft.com/en-us/office/activate-office-5bd38f38-db92-448b-a982-ad170b1e187e#bkmk_hup>`__ to activate your Microsoft 365 subscription.

Use the `Microsoft 365 Sign-in <https://www.office.com/>`__ link to log on to Microsoft 365. Use your email address and password. You will be required to authenticate using multi-factor authentication.

Once authentication is complete, you will see the various Microsoft 365 applications, such as Word, Excel, PowerPoint, and Outlook in your dashboard.

F5 BIG-IP
---------

.. _F5BIGIP:

BIG-IP is both a load balancer and an identity-aware proxy. In this phase of the build, it was primarily used as an identity-aware reverse proxy that forwarded or denied traffic to protected back-end applications.

Installation, Configuration, and Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

BIG-IP was deployed into the environment using a virtual machine image or open virtual appliance (OVA) file. Once this OVA import operation is complete, log into the virtual machine console and assign an IP address to a network interface, then continue configuration by connecting to its web interface. This BIG-IP image has both the Access Policy Manager (APM) and the Local Traffic Manager modules installed.

1. `Deploy BIG-IP OVA <https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.hostclient.doc/GUID-8ABDB2E1-DDBF-40E3-8ED6-DC857783E3E3.html>`__ into your VMware environment.

2. Access the BIG-IP web interface by entering the IP address or DNS name into a web browser. Then `complete the initial setup and configuration of BIG-IP. <https://techdocs.f5.com/kb/en-us/products/big-ip_ltm/manuals/product/bigip-system-initial-configuration-11-6-0/1.html#conceptid>`__

3. `Create virtual servers which map to back-end protected applications <https://techdocs.f5.com/kb/en-us/products/big-ip_ltm/manuals/product/bigip-system-initial-configuration-11-6-0/1.html#conceptid>`__—in this build, to our Guacamole application server.

4. `Configure BIG-IP to use Azure AD as the SAML IdP for external authentication to access back-end applications. <https://community.f5.com/t5/technical-articles/azure-active-directory-and-big-ip-apm-integration/ta-p/286351>`__ The instructions at `Configure BIG-IP Easy Button for Header Based SSO <https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/f5-big-ip-headers-easy-button>`__ and the video at `Azure AD and BIG-IP APM Integration Video <https://www.youtube.com/watch?v=6NDUaDz7NQE>`__ provide additional references.

5. Once these instructions are completed, BIG-IP, leveraging Azure AD for external authentication, will only allow successfully authenticated and authorized users to access Guacamole. Access to the backend application is either done by connecting directly via the DNS name of the application or by going to **myapps.microsoft.com** and selecting the backend application icon, such as **F5 Guacamole_SSO** as shown below.

..

   |Figure1|

6. For this build, `configure BIG-IP to send logs to Microsoft Sentinel. <https://support.f5.com/csp/article/K85539421>`__ Then you can observe BIG-IP logs in Sentinel, as shown below.

..

   |Figure2|

Lookout Mobile Endpoint Security (MES)
--------------------------------------

.. _lookout-mes:

Lookout Mobile Endpoint Security (MES) solution is used to control mobile device access to corporate resources based on risk assessment. Risk is assessed based on information collected from devices by the Lookout service. Lookout then communicates this risk level to the MDM (Microsoft Endpoint Manager (Intune)) which determines whether the device is compliant or not.

Configuration and Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Before configuring Lookout, collect the following information from Azure AD: **Azure AD tenant ID** and **Azure AD group object ID**.

1. Go to **Azure Active Directory** > **Properties** and locate **Tenant ID**. Copy and save it to the text file.

2. Go to **Azure Active Directory** > **Groups** to open the **Groups \| All groups** pane.

3. Select the group with full access *rights* (Lookout Admin group).

4. Copy the (group) **Object Id,** and then save it in a text file.

The following steps are to be completed in the Lookout Enterprise admin console and will enable a connection to Lookout's service for Intune enrolled devices.

1. Sign in to the Lookout for Work console and go to **System** > **Integrations**, and then select **Choose a product to set up**. Select **Microsoft Azure**. Copy and paste the Azure AD (AAD) tenant ID and group object ID from the text file that was created in previous steps.

..

   |Figure3|

2. | Stay in **System** > **Integrations**, and then select **Choose a product to set up.** Select Microsoft
   | **Intune**.

3. Configure Intune connector settings.

..

   |Figure4|

After Lookout MES is enabled, a connection to Lookout in Intune needs to be set up.

1. Go back to Microsoft Endpoint Manager and enable the Mobile Threat Defense connector there.

2. Select **Tenant administration > Connectors and tokens > Mobile Threat Defense.**

3. On the **Mobile Threat Defense** pane, select **Add.**

4. For **Mobile Threat Defense connector to setup,** select **Lookout** MTD solution from the drop-down list.

5. Configure the toggle options according to the organization's requirements. This screenshot shows examples.

..

   |Figure5|

When Lookout is integrated with Intune MTD and the connection to Intune is enabled, Intune creates a classic conditional access policy in Azure AD. To view classic conditional access policy, go to **Azure Active Directory > Conditional Access > Classic policies**. Classic conditional access policy is used by Intune MTD to require that devices are registered in Azure AD so that they have a device ID before communicating to Lookout MTD. The ID is required so that devices can report their status to Intune.

Create MTD Device Compliance Policy with Intune
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Compliance policy is needed to detect threats and assess risks on mobile devices to determine if a device is compliant or not.

1. Open the Microsoft Endpoint Manager admin center.

2. Select **Endpoint security > Device Compliance > Create Policy.**

3. Select the **Platform,** and then **Create.**

4. On **Basics,** provide **Name** and **Description.** Select **Next** to continue.

5. On **Compliance settings,** expand and configure **Device Health.** Choose the Mobile Threat Level from the drop-down list for **Require the device to be at or under the Device Threat Level.** Choose the level for compliance.

6. Select **Next** to go to **Assignments.** Select the groups or users to which this policy should be assigned.

PC Matic Pro
------------

PC Matic Pro is an endpoint protection system that consists of a server for centralized management and agents installed on endpoints. In addition to scanning for malware, it uses a default-deny approach for preventing malicious and unauthorized programs and processes from executing. To configure PC Matic Pro, you will need to install the server, install the agents, and configure a list of allowed software.

PC Matic Pro Server needs to be installed on a server with Windows 2019 Server and SQL Server preinstalled.

1. Obtain the *OnPremInstallerRun.ps1* installation script from the vendor and open an elevated PowerShell window.

2. Execute the *OnPremInstallerRun.ps1* script by entering .\\OnPremInstallerRun.ps1 registryUser pcmatic -registryPwd <insert_password_here> -localDBUser pcm-app to install docker, pull down the container images, and deploy the container instances that make up the PC Matic Pro server.

3. Navigate to the PC Matic web server and verify that it is operational by opening a web browser and going to *https://<pcmaticDNSName>/web_portal.* In this build, the DNS name is nist.pcmaticfederal.com; as such, to access the server's web interface, we would go to https://nist.pcmaticfederal.com/web_portal.

Follow these steps to install PC Matic Endpoint Agents:

1. Open a web browser on a Windows or macOS client device. Navigate to the PC Matic Server web interface by browsing to https://nist.pcmaticfederal.com from the client device and log on with your credentials.

2. Click **Add a Device** and then click **Windows Installer** or **Mac Installer,** as appropriate, to download the PC Matic Endpoint Agent.

3. Install the agent.

4. Once installed, the agent will establish communications with the server and show up on the list of managed devices once you log on to the server as previously described.

5. Devices with an agent will register and come online.

..

   |Figure6|

Tenable.io
----------

For installation, configuration, and integration instructions, refer to :ref:`Tenable.io<tenable-io>`.

Integration with Microsoft Sentinel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. In Tenable.io, click the hamburger menu (☰) in the top left corner and navigate to **Settings >
   Access Control > Users.**

2. (Optional) Click **Create User** and create a new API user for Microsoft Sentinel. In this implementation, a standard administrator account was used.

3. Click the user who needs API keys generated. Then click **API KEYS > Generate > Continue.** Save the Access and Secret Keys, as they will not be shown again.

4. In Microsoft Sentinel, navigate to **Data Connectors.** Search *tenable* and click **Tenable.io Vulnerability Management (Preview) > Open Connector Page.**

5. Scroll down in the Instructions panel and save the Workspace ID and Primary Key.

6. Click **Deploy to Azure.**

7. Select the appropriate resource group.

8. In the Workspace ID and Workspace Key fields, enter the values obtained in step 5.

9. In the Tenable Access Key and Tenable Secret Key fields, enter the values obtained in step 3.

10. Click **Review + create.**

11. Click **Create.** Function deployment will begin. Once deployment is complete, it will take some time before Sentinel begins making calls to Tenable.io.

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

.. _forescout-eyesight:

Forescout eyeSight provides asset discovery with both active and passive techniques, and through integrations with network and security infrastructure. In this build, Forescout was deployed on-premises in two virtual hosts: an Enterprise Manager and Forescout Appliance.

For Forescout installation instructions, visit the `Forescout Installation Overview <https://docs.forescout.com/bundle/install-guide-8-3/page/install-guide-8-3.Installation-Overview.html>`__.

Integration with AD
~~~~~~~~~~~~~~~~~~~

1. In AD, create a domain administrator service account for Forescout and save the credentials.

2. In the Forescout console, navigate to **Tools > Options > HPS Inspection Engine.**

3. In the **Domain Credentials** section, click the **Add** button.

4. Enter the domain information and credentials you saved earlier. Click **OK.**

5. Click **Apply.** After the new configuration is saved, click **Test** to verify that the credentials are working as expected.

Integration with Cisco Switch
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For Cisco Switch integration instructions, visit the `Switch Plugin Configuration Guide <https://docs.forescout.com/bundle/switch-8-14-3-h/page/switch-8-14-3-h.How-to-Work-with-the-Switch-Plugin.html>`__.

Integration with Cisco Wireless Controller
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For Cisco Wireless Controller integration instructions, visit the `Wireless Plugin Configuration Guide <https://docs.forescout.com/bundle/wireless-2-0-1-h/page/wireless-2-0-1-h.How-to-Work-with-the-Wireless-Plugin.html>`__.

Integration with Microsoft Sentinel
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. In the Forescout console, navigate to **Tools > Options > CEF.**

2. Click **Add.**

3. In the Add Server dialog, enter a Name, select **Use UDP for Connection,** and enter the IP address of the Sentinel Log Forwarder. Click **Next.**

4. Click the **Assign CounterACT Devices** radio button, and check all of the checkboxes next to the listed devices.

5. Click **Finish.** Verify that logs are being received by the Sentinel Log Forwarder.

Integration with Palo Alto Networks NGFW
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For Palo Alto Networks NGFW integration instructions, visit the `eyeExtend for Palo Alto Networks Next-Generation Firewall Configuration Guide <https://docs.forescout.com/bundle/pan-1-3-7-h/page/pan-1-3-7-h.About-the-Palo-Alto-Networks-Next-Generation-Fir.html>`__.

Integration with Tenable.io
~~~~~~~~~~~~~~~~~~~~~~~~~~~

For Tenable.io integration instructions, visit the `eyeExtend for Tenable.io Vulnerability Management Configuration Guide <https://docs.forescout.com/bundle/tenable-io-1-0-h/page/c-about-the-tenableio-vm-integration.html>`__.

Palo Alto Networks Next Generation Firewall
-------------------------------------------

For installation, configuration, and integration instructions, refer to :ref:`Palo Alto Networks Next Generation Firewall<palo-alto-ngfw>`.

DigiCert CertCentral
---------------------

For installation, configuration, and integration instructions, refer to :ref:`DigiCert CertCentral<digicert-certcentral>`.

.. |Figure1| image:: images/E3B1-Figure1.png
   :alt: This screenshot shows application icons at myapps.microsoft.com.
.. |Figure2| image:: images/E3B1-Figure2.png
   :alt: This is a screenshot showing how you can observe BIG-IP logs in Microsoft Sentinel.
.. |Figure3| image:: images/E3B1-Figure3.png
   :alt: This screenshot shows integration settings for Microsoft Azure.
.. |Figure4| image:: images/E3B1-Figure4.png
   :alt: This screenshot shows examples of Intune connector settings.
.. |Figure5| image:: images/E3B1-Figure5.png
   :alt: This screenshot shows examples of MDM compliance policy settings.
.. |Figure6| image:: images/E3B1-Figure6.png
   :alt: This screenshot shows a list of online agents.