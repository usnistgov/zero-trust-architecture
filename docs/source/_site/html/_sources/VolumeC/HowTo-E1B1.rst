Enterprise 1 Build 1 (E1B1) - EIG Crawl - Okta Identity Cloud and Ivanti Access ZSO as PEs Product Guides
==========================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all of the products used to implement E1B1. For additional details on E1B1's logical and physical architectures, please refer to :ref:`architecture and builds`.

Okta Identity Cloud 
--------------------

.. _okta-identity-cloud:

The Okta Identity Cloud is a SaaS solution that provides ICAM capabilities to an enterprise. The following sections describe the setup of the Okta Identity Cloud, the Okta Access Gateway, and the Okta Verify application. Okta integrates with Radiant Logic for identity information, SailPoint to receive governance information, and Ivanti to delegate authentication for users accessing resources using mobile devices.

Configuration and Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The purpose of this subsection is to set up NCCoE's own instance of the Okta cloud so it can integrate with other ICAM tools and enable Okta to manage authentication and authorization of users accessing resources. Most configurations are completed within this instance of the Okta cloud.

1. Sign up for an account with Okta (okta.com) and follow steps to set up an admin account, along with configuring Okta Verify for the admin account. This will allow the admin to start configuring integrations and services.

2. Set up directory integration with Radiant Logic. User identity information is pulled from Radiant Logic into Okta for authentication and authorization. An Okta Lightweight Directory Access Protocol (LDAP) agent is installed on the Radiant Logic server for integration. Note: This step should be completed after Radiant Logic is configured.

3. Create Groups for Okta to apply a specific set of users to specific services or applications. This allows for automation of user governance at a large scale rather than manual configuration of individual users.

4. `Create application programming interface (API) tokens to be used by SailPoint and Radiant Logic <https://help.okta.com/oie/en-us/Content/Topics/Security/API.htm?cshid=Security_API#create-okta-api-token>`__ for communication. These tokens will allow Okta to give specific read/write privileges to other applications.

5. `Create a delegated authentication for Okta to be able to import users from Radiant Logic via LDAP. <https://help.okta.com/oie/en-us/Content/Topics/Security/Security_Authentication.htm>`__ This allows Okta to delegate the actual authentication to Radiant Logic. Okta does not store or know the password of the user. Note that a service account, created in the :ref:`Radiant Logic Integration<radiant-integration>`, needs to be created and used in this configuration.

6. Create application integration via Security Assertion Markup Language (SAML). We have Ivanti Neurons for UEM and 2 GitLab instances in Enterprise 1. Okta Access Gateway (AG) needs to be installed in order to configure on-premises applications. The Okta AG gives the Okta Identity Cloud visibility to the resources inside the enterprise. See :ref:`Okta Access Gateway<okta-access-gateway>` for installation instructions, which include information on configuring on-premises applications.

7. Create Identity Provider integration for Ivanti Access ZSO. This will allow delegated authentication for Ivanti for mobile devices. This involves `creating a custom application using SAML <https://help.okta.com/oie/en-us/Content/Topics/Apps/Apps_App_Integration_Wizard_SAML.htm>`__ and then `creating a SAML Identity Provider <https://help.okta.com/en-us/Content/Topics/Security/idp-add-saml.htm>`__.

8. `Configure Device Trust on iOS and Android devices to create device integrations. <https://help.okta.com/oie/en-us/Content/Topics/identity-engine/devices/config-mobile.htm>`__

9. `Create authentication policies. <https://help.okta.com/oie/en-us/Content/Topics/identity-engine/policies/create-auth-policy.htm>`__ These policies define how users will authenticate. By default, a “Catch All” policy is created when an application is created. We are creating an authentication policy that will allow Okta to trust Ivanti Access ZSO to be the delegated Identity Provider (IdP). To do this, when Okta checks that Okta Verify is a managed application on a device, it will delegate authentication to Ivanti Access ZSO.

Okta Verify App
~~~~~~~~~~~~~~~

.. _okta-verify-app:

The Okta Verify app is installed, usually on a mobile device, when a new user is onboarded. It serves as a tool to provide a second factor for authentication. The user can log in to the Okta Identity Cloud for the first time. For this setup, the user will be asked to change their password and perform setup. After the password update, the user can set up Okta Verify. `Follow the instructions for Android or iOS devices to install Okta Verify and complete the process. <https://help.okta.com/eu/en-us/Content/Topics/end-user/ov-overview.htm>`__

Okta Access Gateway
~~~~~~~~~~~~~~~~~~~

.. _okta-access-gateway:

The Okta Access Gateway (AG) is part of the Okta Identity Cloud. It can be leveraged to integrate legacy, on-prem applications into the Okta Identity Cloud. Since the Okta Identity Cloud cannot communicate with Enterprise 1 resources directly, the Okta AG acts as a proxy to facilitate that communication. `More information on installing and configuring the Okta AG is available online. <https://help.okta.com/en-us/Content/Topics/Access-Gateway/install-workflow.htm>`__

Radiant Logic RadiantOne
------------------------

.. _radiant-one:

Radiant Logic RadiantOne is an ICAM solution that unifies identity data, making access reusable and scalable for the enterprise.

Installation
~~~~~~~~~~~~

.. _radiant-install:

RadiantOne is to be installed on a Microsoft Windows 2019 server. See the RadiantOne v7.4.1 documentation from the `Radiant Logic website <https://www.radiantlogic.com/>`__ for system specifications. Prerequisites are in Chapter 1 of the *RadiantOne Installation Guide*. Note: You need to create an account within the Radiant Logic website in order to access the installation and configuration documentation.

Once you download and launch the executable for a Windows server installation, follow the step-by-step instructions provided on the screen. We used default settings unless specified below. Instructions can also be found in Chapter 2 of the *RadiantOne Installation Guide*.

-  Choose **RadiantOne Federated Identity Suite New Cluster/Standalone** for the **Install Set.**

-  Provide a name and password for the **Cluster settings.**

-  For the **Server Configuration** step, use the following ports: LDAP = 389, LDAPS = 636, and Scheduler Port = 1099.

Configuration
~~~~~~~~~~~~~

Sync with an LDAP server
^^^^^^^^^^^^^^^^^^^^^^^^

1. Once installation is complete, log in to RadiantOne from a web browser on the Radiant Logic server, https://localhost:7171. Note: ensure the proper SSL certificate is on the server for HTTPS.

2. Initial configuration is to sync up with an LDAP server. Go to **Settings > Server Backend > LDAP Data Sources.** The screenshot below shows the information created for Enterprise 1 AD. See the *RadiantOne Namespace Configuration Guide* Chapter 3 for details.

..

   |Figure1|

3. Once the connection is tested and successful, the integration is completed.

4. Next, create a Directory Namespace by going to **Directory Namespace** and selecting **Create New Naming Context.** Click **Next** and click **OK.**

..

   |Figure2|

5. Find **DC=NCCOE,DC=ORG** under **Root Naming Contexts** on the left side of the screen. Click the **New Level** button. Enter **ent1** as the name for the **OU** and click **OK.**

6. Click on **ou=ent1** on the left side and click the **New Level** button on the right to create a sub-ou called **groups.**

7. Click on **ou=ent1** on the left side and click the **New Level** button on the right to create a sub-ou called **users.**

8. Once configured and saved, click on **ou=users** and click on **Backend Mapping** on the right. Select **LDAP Backend.** Click **Next** and **Browse** for the proper **Remote Base DN.** Then click **OK.** The screenshot is the completed configuration for the sub-ou users Proxy Backend.

..

   |Figure3|

9. Go to **Objects** and create a primary object and Join Profile by clicking **Add** on each object. Click **Save.** Now we have data sources from LDAP and our database.

..

   |Figure4|

Create a namespace to bring in users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. In **Directory Namespace**, click the **+** sign. Create a naming context: **ou=hr,ou=lab,ou=nccoe,ou=org** and select **Virtual Tree** for the naming context type, then click **Next.**

2. Configure the Virtual Tree by choosing **Create a new view (.dvx),** setting the **Directory View** to **dv=ou_hr_ou_lab_ou_nccoe_ou_org** and clicking **OK**.

3. Next, create a sub-Namespace by clicking the **+ New level** button and entering the information depicted below.

..

   |Figure5|

4. Click on the sub-Namespace that was just created and click on **Backend Mapping**. Specify **ou=east,ou=hr,ou=lab,ou=nccoe,ou=org** as the naming context and select **HDAP Store** as the type, then click **Next**. Note: Instead of having an actual HR database, we are importing sample users from a text file.

5. Click on **ou=east** to edit properties. Scroll down to the bottom of the screen and click on the **Initialize** button. Then select a file with database users to import for initializing the High-Availability Directory Access Protocol (HDAP) store. Note: We are emulating an HR database with this file.

6. Go to the **Directory Browser** tab and refresh the data by clicking the **Refresh Tree** button.

7. Go to the OU that you just configured and expand it. The new users should now be available.

8. Go to **Directory Namespace** and click the **+** button to add new naming context (in our build, we used **ou=testing**). This is used to map to the LDAP backend the database information that was imported.

9. Click on the OU that was created. Click **OK** and **Save**.

..

   |Figure6|

10. Go to **Directory Browser** and hit the **Refresh** button.

11. Go to **Settings > Configuration > ORX Schema**, and find **OU=Testing** and check it. Click on **Generate LDAP Schema** at the bottom of the screen and click **OK**.

Integration
~~~~~~~~~~~

.. _radiant-integration:

Other applications, including SailPoint and Okta, will need the following information in order to integrate with Radiant Logic and pull information from it:

-  Hostname: radiant1.lab.nccoe.org (hostname of the Radiant Logic server)

-  Port: 389 (LDAP) and 636 (LDAPS)

Also, a service account and password need to be created on Radiant Logic for each application to be integrated. The service account is in the form of: uid=sailpointadmin,ou=globalusers,cn=config. Follow these steps to create each service account for SailPoint, Okta, and any other desired applications:

1. Go to **Directory Browser.**

2. On the left, go to **cn=config,** then **ou=globalusers** underneath it. Right-click on **ou=globalusers,** click **Add,** then click **New InetOrgPerson.**

3. Fill in the necessary entries. Click **Confirm** to save the configuration.

SailPoint IdentityIQ
--------------------

.. _sailpoint:

SailPoint IdentityIQ is the identity and access management software platform for governing the lifecycle of the enterprise user's identity.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _sailpoint-install:

The steps below explain the installation of the IdentityIQ server, initial configuration to import users from the Radiant Logic identity store, and configuration to manage the lifecycle of users.

1. To install IdentityIQ, first identify the platform and prerequisites. For this build, we used Windows 2019 with Apache Tomcat 9.0 and MS SQL Server 2019 as recommended requirements for release 8.2. Download the installation file from the SailPoint website and `follow the installation instructions <https://community.sailpoint.com/t5/IdentityIQ-Product-Guides/8-2-IdentityIQ-Installation-Guide/ta-p/196441>`__.

2. Login into IdentityIQ from a web browser (http://localhost:8080) using the default login and password identified in the IdentityIQ Installation Guide. Make sure to change the default password by following the instructions provided in the Guide.

3. `Configure IQService. <https://documentation.sailpoint.com/connectors/iqservice/help/integrating_iqservice_admin/install_register.html>`__ This is needed in order to set up integration with AD.

4. Govern permissions by pushing employee and contractor users and groups to AD and Okta. Note: This step should be completed after the integration with AD and Okta is completed. Steps to configure integration are in :ref:`Integration with AD<sailpoint-integration-ad>` and :ref:`Integration with Radiant Logic<sailpoint-integration-radiant>`. After integration with AD and Okta is completed, navigate to the **Setup** drop-down menu and select **Roles**. Here we will create a birthright role and access profile for employees and contractors.

    a. Select the **New Role** drop-down button and select **Role**. The screenshot lists the four roles that are created for this build.

..

   |Figure7|

   b. For the **Employee Birthright Role**, use the configuration shown in the next two screenshots. Note that the **Assignment Rule** is where the value of **employee** is used to identify the users. This will push users into AD as a birthright. Once that role is configured, configure the corresponding contractor role the same way. Note that the **Assignment Rule** should be different for the contractor based on user information in SailPoint.

..

   |Figure8|

   |Figure9|

   c. For the **Employee Access Profile** role, add the groups that the employees belong to. This means that these users will have access to these groups as a birthright. Perform the same for the corresponding contractor role. Note that the **Entitlements** should be different for the contractor based on group information in Okta and AD.

5. The next step is to synchronize users and groups. To begin, navigate to the **Setup** tab and select **Tasks**.

    a. To create user aggregation, select the **New Task** drop down button and select **Account Aggregation**. The screenshot below depicts the aggregation configuration for Radiant Logic. This allows SailPoint to sync with Radiant Logic on any updates made to users. Repeat this step for AD and Okta accounts. Note that the **Account Aggregation Options** section is where the AD and Okta applications need to be selected to create the proper account aggregation.

..

   |Figure10|

   b. To create group aggregation, select the **New Task** drop down button and select **Account Aggregation**. This allows SailPoint to sync with AD on any updates made to users in the groups. Repeat this step for the Okta account. Note that the **Account Group Aggregation Options** section is where the Okta applications need to be selected to create the proper account aggregation.

6. Configure lifecycle processes through Rapid Setup Configuration. Click on the **Setup** cog and select **Rapid Setup** to begin. The Rapid Setup Configuration process allows onboarding of applications and manage functions such as joiner, mover, and leaver of identities. Use the “Using Rapid Setup” section of the `IdentityIQ Rapid Setup Guide <https://community.sailpoint.com/t5/IdentityIQ-Product-Guides/8-2-IdentityIQ-Rapid-Setup-Guide/ta-p/196225>`__ to guide the configuration.

    a. Configure **Joiner**, **Mover,** and **Leaver.**

    b. Configure **Identity Operations**.

    c. Configure Rapid Setup specific to AD users: Aggregation, Joiner, Mover, and Leaver.

7. Govern user permissions to applications on an individual basis. Configure procedures to provision and approve user access to resources. For Enterprise 1, the process is for an administrator or user to request approval to access an application. That request goes to the user's manager for review and approval. Once the manager approves the request, SailPoint kicks off an API call to Okta to configure access for that user.

Integration with Radiant Logic 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _sailpoint-integration-radiant:

1. In the **Applications** tab, select **Application Definition.** When the screen comes up, click on the **Add New Application** button.

2. Enter values for the **Name** (e.g., “Ent1-HR”) and **Owner** (e.g., “The Administrator”) fields. Select **LDAP** as the **Application Type** and ensure that **Authoritative Application** is enabled.

3. Click on the **Configuration** tab next to the current tab. The credentials that were created in Radiant Logic will need to be added.

..

   |Figure11|

4. Scroll down the screen and under the **Account** tab, add the Search DN, which is the one created from Radiant Logic.

5. Click on **Test Connection** to make sure that SailPoint is able to connect to Radiant Logic. Click **Save.**

6. You can go back into the **Configuration** tab and **Schema** sub-tab. Toward the bottom of the screen, there is a **Preview** button. You can click on that to preview the imported attributes. Note: We manually added schema attributes. This can be completed from Radiant Logic and imported. Please ensure that you have the correct attributes to integrate this.

7. To complete the setup, click **Save** to finish and import users from Radiant Logic.

8. Go to the **Setup** tab and click **Tasks.** Once in the new tab, click on the **New Task** button at the top right corner to create the account aggregation for Radiant Logic.

9. Perform identity attribute mapping. The screenshot shows mappings specific to this build only.

..

   |Figure12|

Integration with AD 
~~~~~~~~~~~~~~~~~~~~

.. _sailpoint-integration-ad:

1. Navigate to the **Applications** tab, click on **Application Definition**, then click the **Add New Application** button. Fill out the **Name** (e.g., “Ent1-AD-Ent-Users”), **Owner** (e.g., “The Administrator”), and **Application Type** (“Active Directory - Direct”).

2. Navigate to the **Configuration** tab. From here, input information for the IQ Service Host. The IP address is this server, the IdentityIQ server. IQ Service User is a user that was created in AD for this integration.

..

   |Figure13|

3. Scroll down to the **Domain Configuration** section. Input the domain information for where the users will be provisioned.

..

   |Figure14|

4. Scroll down to the **User Search Scope** section and input the Search DN information. This should be the AD domain location for your enterprise.

5. Navigate to the **Schema** and **Provisioning Policies** sub-tabs, and update information as necessary.

6. Then navigate to the **Correlation** tab to configure the correlation for application and identity attributes between SailPoint and AD.

..

   |Figure15|

7. Click **Save** to complete the configuration.

8. Go to **Setup** tab and click **Tasks**. Once in the new tab, click on the **New Task** button at the top right corner to create the account aggregation for AD.

Integration with Okta
~~~~~~~~~~~~~~~~~~~~~

1. Go into the **Applications** tab and select **Application Definition.** When the screen comes up, click on the **Add New Application** button.

2. Fill out the **Name** (e.g., “Ent1-Okta”) and **Owner** (“The Administrator”), select **Okta** as the **Application Type,** and enable the **Authoritative Application** option.

3. In the **Configuration** settings tab, the Okta URL and API token are needed. Note that the API token is created in Okta. Click **Save** to finish the setup.

..

   |Figure16|

Ivanti Neurons for UEM
----------------------

.. _ivanti-neurons:

Ivanti Neurons for UEM is a unified endpoint management (UEM) solution which is used to provision endpoints, grant access to enterprise resources, protect data, distribute applications, and enforce measures as required.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Install an MDM certificate for Apple devices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Apple Push Notification service (APNs) certificate needs to be installed in Ivanti Neurons for UEM to communicate with Apple devices. Apple devices use an APNs certificate to learn about updates, MDM policies, and incoming messages.

To acquire and install the MDM certificate:

1. Open the Ivanti Neurons for UEM console and go to **Admin > Apple > MDM Certificate** page to download a certificate signing request (CSR).

2. Upload the CSR to the `Apple Push Certificates Portal <https://identity.apple.com/pushcert/>`__ to create a new certificate.

3. Save the resulting certificate.

4. Install the certificate for the Ivanti Neurons for UEM tenant.

Configure Android Enterprise
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Android Enterprise allows personal and corporate applications on the same Android device. Android Enterprise configuration depends on the type of Google subscription. Please follow Ivanti documentation to `set up the integration <http://mi.extendedhelp.mobileiron.com/82/all/en/Setting_up_Android_enterprise.htm?Highlight=android%20enterprise>`__.

The Android Enterprise Work Profile configuration defines which features and apps are allowed, and which are restricted on Android enterprise devices. Do the following to configure the profile:

1. In the Cloud portal, go to **Configurations** and click **Add.**

2. Select the **Lockdown & Kiosk: Android Enterprise** configuration.

3. Enter a configuration name and description.

4. Click the **Work Profile** lockdown type.

5. Select the lockdown settings for Android devices.

Add a certificate authority
^^^^^^^^^^^^^^^^^^^^^^^^^^^

A certificate authority (CA) generates self-signed certificates to be used by the devices that Ivanti Neurons for UEM manages. For this implementation we used an external certificate authority (DigiCert) and a Connector to access it. Ivanti Cloud Connector provides access from the Ivanti Neurons for UEM service to corporate resources, such as an LDAP server or CA.

1. Install and configure a Connector (**Admin > Connector**).

2. In the **Certificate Management** page, click **Add** under the **Certificate Authority** section.

3. Choose **Connect to a publicly-trusted Cloud Certificate Authority.**

4. Enter a name for the CA.

5. Download the certificate from DigiCert and upload it to Ivanti Neurons for UEM.

..

   |Figure17|

Configure user settings
^^^^^^^^^^^^^^^^^^^^^^^

User settings define device registration options. Access them by opening Ivanti Neurons for UEM and going to **Users** > **User Settings**. Configure device and password settings there.

Add a policy
^^^^^^^^^^^^

Policies define requirements for devices and compliance actions (what happens if the rule is violated). To add a policy:

1. Go to **Policies** and click **+Add** (upper right).

2. Select a policy type and complete the settings. Policy types include Compromised Devices, Data Protection/Encryption Disabled, MDM/Device Administration Disabled, Out of Contact, and Allowed Apps.

3. Select the device groups that will receive this policy.

The following screenshots show an example of a Data Protection policy to be distributed to a custom group of devices.

|Figure18|

|Figure19|

Add a configuration for managed devices
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Configurations are collections of settings that Ivanti Neurons for UEM sends to devices. To add a configuration:

1. Click **Add.**

2. Select the type of configuration. There are numerous types of configurations available, including Privacy, Certificate, Default App Runtime Permissions, Passcode, Exchange, Wi-Fi, VPN, iOS/macOS/Windows Restrictions, and Software Updates.

..

   |Figure20|

3. Click **Next.**

4. Select a distribution level for the configuration.

Here is an example of a Privacy configuration:

|Figure21|

This is an example of an iOS AppConnect configuration:

|Figure22|

This screenshot shows a list of configurations pushed to a device:

|Figure23|

Integration with Ivanti Connector
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ivanti Connector provides access from Ivanti Neurons for UEM to corporate resources, such as an LDAP server. For the latest Connector installation instructions, select the appropriate version of the `Cloud Connector Guide <https://help.ivanti.com/mi/help/en_us/cld/8x/inst/LandingPage.htm>`__.

1. Once the Ivanti Connector has been set up and configured, navigate to the Ivanti Neurons for UEM console.

2. Connect to an LDAP Server to import users and groups. Navigate to **Admin > Infrastructure > LDAP > Add Server.** Complete configurations and save. Users can now be imported from the LDAP server.

.. _integration-with-okta-1:

Integration with Okta
~~~~~~~~~~~~~~~~~~~~~

IdP setup
^^^^^^^^^

1. Go to **Admin > Infrastructure > Identity > Add IdP.**

2. Generate a key for uploading to Okta IdP.

3. Log in to Okta IdP. Search IdP for the **MobileIron Cloud App** and add it to the IdP account.

4. Configure the **MobileIron Cloud App** on the IdP by pasting the above-generated key and the host information.

5. Export metadata from Okta to the Ivanti Neurons for UEM console.

6. In **Admin > Infrastructure > Identity > Add IdP,** select **Choose File** to import the downloaded metadata file to Ivanti Neurons for UEM and complete the setup.

7. When an IdP is added, user authentication automatically switches from LDAP to IdP.

Okta Verify app configuration preparation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. In the Okta Admin console, navigate to **Security > Device Integrations** and click **Add Platform.**

2. Select platform and click **Next.**

3. Copy the **Secret Key** for later usage and enter Device Management Provider and Enrollment Link settings.

4. Repeat for any other device platforms.

Okta Verify app configuration - Android
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. In the Ivanti Neurons for UEM console, navigate to **Apps > App Catalog.** Click **Add.**

2. Select the Google Play Store and search for **Okta Verify.** Select the official **Okta Verify** app.

3. Continue through the wizard until you reach the App Configurations page. Click the **+** button in the Managed Configurations for Android section.

4. Add desired settings. Under **Managed Configurations,** add the **Org URL** and **Management Hint** from the Okta Admin console. The Management hint will be the **Secret Key** you saved from the Okta console during preparation.

5. Click **Next,** then click **Done.**

Okta Verify app configuration - iOS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. In the Ivanti Neurons for UEM console, navigate to **Apps > App Catalog**. Click **Add**.

2. Select the iOS Store and search for **Okta Verify**. Select the official **Okta Verify** app.

3. Continue through the wizard until you reach the App Configurations page. Click the **+** button in the Apple Managed App Configuration section.

4. Add desired settings. Under **Apple Managed App Settings**, click **Add** and add two items.

    a. For the first item, the key will be **domainName**, the value will be your Org URL, and the type will be STRING.

    b. For the second item, the key will be **managementHint**, the value will be the **Secret Key** you saved from the Okta console during preparation, and the type will be STRING.

5. Click **Next,** then click **Done**.

Integration with QRadar
~~~~~~~~~~~~~~~~~~~~~~~

Ivanti log transfer setup
^^^^^^^^^^^^^^^^^^^^^^^^^

1. Set up an SSH server to host log files. Create a user account that can be used to host/transfer Ivanti Log Files.

2. In the Ivanti Neurons for UEM console, navigate to **Admin > Infrastructure > Audit Trails**.

3. Turn on **Audit Trails Export** and **Device Check-in Trails.**

4. Under Export Format, select **CEF** (Common Event Format).

5. Enter the IP address or hostname for the SSH server you set up previously.

6. Enter the username and password for the user you set up previously.

7. Enter the server path for where you would like the Ivanti log files to be stored on the SSH server.

8. Click **Test Connection and Save**. Ivanti log files will now be transferred to the SSH server on a regular basis.

QRadar setup
^^^^^^^^^^^^

1. In the QRadar console, navigate to **Admin > Extensions Management**. Click **Add**.

2. Select the Ivanti extension file provided by IBM. Click **Add**.

3. Continue through the wizard until you completed the extension installation.

4. In the QRadar console, navigate to **Admin > Log Sources.** Click +\ **New Log Source.**

5. In the search box, type **Ivanti**. Make sure **Ivanti** is selected in the menu and click **Step 2: Select Protocol Type**.

6. In the search box, type **Log File**. Make sure **Log File** is selected in the menu and click **Step 3: Configure Log Source Parameters**.

7. Enter a name for the log source and turn off **Coalescing Events**. Click **Step 4: Configure Protocol Parameters**. The settings are as follows:

    a. Log Source Identifier: **MobileIron Cloud**

    b. Service Type: SFTP

    c. Remote IP or Hostname: <Log server you set up previously>

    d. Remote port: 22

    e. Remote User/Password: <Credentials created earlier, if not using key file authentication>

    f. SSH Key File: <Credentials created earlier, if not using password authentication>

    g. Remote directory: Directory where Ivanti logs are being stored

    h. Recursive: On

    i. FTP File Type Pattern (Regex for Ivanti log files): ^.*\\.(zip|ZIP)$

    j. Processor: ZIP

    k. All other settings can be left as default

8. Click **Step 5: Test Protocol Parameters**. Run the tests and ensure the configuration is valid.

9. From the QRadar console, navigate to the **Admin** tab. Click **Deploy Changes**.

Ivanti Sentry
-------------

Ivanti Sentry is an inline gateway that manages, encrypts, and secures traffic between the mobile device and back-end enterprise systems. In this build, Ivanti Sentry acts as a PEP that controls access to enterprise resources.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this implementation we used a Standalone Sentry installation on-premises. For the latest Sentry installation instructions, select the appropriate version of the *Standalone Sentry On-Premises Installation Guide* at https://www.ivanti.com/support/product-documentation.

Next, create a profile for Standalone Sentry in the Ivanti Neurons for UEM console. For information on how to create a profile for Standalone Sentry and configure Standalone Sentry for ActiveSync and AppTunnel, see the `Sentry Guide for Cloud <https://help.ivanti.com/mi/help/en_us/SNTRY/9.x/gdcl/LandingPage.htm>`__. For the latest Sentry installation instructions, click on Sentry, then select the appropriate version of the Standalone Sentry On-Premises Installation Guide.

Ivanti Tunnel Configuration and Deployment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ivanti Tunnel is an application that connects a mobile device to the Ivanti Sentry. The process to deploy this app is similar to the deployment of the Okta Verify app in :ref:`Okta Verify App<okta-verify-app>`.

1. On the **App Configurations** page for the Tunnel app, create a Managed Configuration.

2.  Set the **Tunnel Profile Mode** to **MobileIron Sentry + Access.**

3.  Set the **Sentry Server** to the Sentry instance you created previously.

4.  Set the **SentryService** to the name of the IP Tunnel defined on the Sentry.

5.  Set the **ClientCertAlias** to the Sentry certificates you defined during Sentry configuration.

6.  Set any other options as needed.

7. Save the Managed Configuration and deploy to devices as needed.

Ivanti Access ZSO
-----------------

Ivanti Access ZSO is a cloud-based service that allows access to enterprise cloud resources based on user and device posture, and whether apps are managed or not. In this build, Ivanti Access ZSO functions as a delegated IdP, with Okta passing certain responsibilities to Ivanti Access ZSO.

Integration with Ivanti Neurons for UEM
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure that you have the **Manage MobileIron Access Integration** role in Ivanti Neurons for UEM enabled at **Admin > System > Roles Management.**

2. Navigate to **Users > Users** and click **Add > API User.**

3. Next, navigate to **Users > Users** and click on the username of the user you just created. Navigate to the **Roles** tab of that user and add the **Manage MobileIron Access Integration** role.

4. In the Ivanti Neurons for UEM console, go to **Admin > Infrastructure > Access.**

5. Enter the following: **Access Admin URL, Access Admin Username** (username for the Access administrator account created for Access integration), and **Access Admin Password.**

6. Click **Register.**

7. When Access is registered with Ivanti Neurons for UEM, you should see the following:

..

   |Figure24|

.. _integration-with-okta-2:

Integration with Okta
~~~~~~~~~~~~~~~~~~~~~

1. In the Okta Admin console, navigate to **Security > API** and generate an API token. Save this token for use in Access.

2. In the Ivanti Access ZSO console, navigate to **Profile > Federation.**

3. Select **Add Pair > Delegated IDP** and choose **Okta.**

4. Enter the Okta Domain URL and the Okta API Token you generated in Step 1. Click **Verify.**

5. Once the verification is complete, select the routing rules you'd like configured and click **Next.**

6. Verify the Signing Certificate settings and Encryption Certificate settings are correct and click **Next.**

7. Choose the desired **Unmanaged Device Authentication** setting and click **Done.**

8. You will see Okta in the Delegated IDP section. Okta will route authentication requests based on your settings.

Zimperium Mobile Threat Defense (MTD)
-------------------------------------

.. _zimperium-mtd:

Zimperium MTD can retrieve various device attributes, such as device name, model, OS, OS version, and owner's email address. It then continuously monitors the device's risk posture and reports any changes in the posture to Ivanti Neurons for UEM.

Installation, Configuration, and Integration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Create an API user
^^^^^^^^^^^^^^^^^^

To configure a Zimperium MTD console to work with Ivanti Neurons for UEM, an API user needs to be created and assigned a few roles.

1. In the Ivanti Neurons for UEM admin console, select **Users.**

2. Click **+ Add > API user.** The Add API User dialog page opens.

3. Enter the following details: **Username, Email, First Name, Last Name, Display Name,** and **Password.**

4. Confirm the password.

5. Deselect the **Cisco ISE Operations** option.

6. Click **Done.**

Assign roles to the API user
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From the admin console, go to **Users.**

2. Select the new API user created previously.

3. Click **Actions.**

4. From the User details page, select **Assign Roles.**

5. Select the following roles: **App & Content Management, App & Content Read Only, Common Platform Services (CPS), Device Actions, Device Management, Device Read Only, System Read Only,** and **User Read Only.**

Add an MDM server to the Zimperium console
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Log in to the Zimperium MTD console.

2. Navigate to **Manage > Integrations > Add MDM.**

3. Select **Cloud** to add it to the MTD console as an MDM server.

4. Enter the following required information: **URL, Username/Password, MDM Name,** and **Background Sync.**

5. Click **Finish.**

Activate MTD on Ivanti Neurons for UEM
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. From the Ivanti Neurons for UEM admin console, go to **Configurations.**

2. Click **+Add.**

3. Click **Mobile Threat Defense Activation.**

4. In the **Create Mobile Threat Defense Configuration** page, enter a name for the configuration.

5. In the Configuration Setup section, select the vendor **Zimperium.**

6. In the **License Key** field, enter a unique encrypted Mobile Threat Defense activation code.

7. In the **Wake up Intervals (mins)** field, set a time.

8. Click **Next.**

9. Select the **Enable this configuration** option.

10. Select **All Devices.**

11. Click **Done.**

Add custom attributes in Ivanti Neurons for UEM
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Custom device attributes will be applied to both Android and iOS devices based on threat severity.

1. To create custom attributes, in the Ivanti Neurons for UEM admin console go to **Admin > System > Attributes.** Enter each attribute name in lower case.

2. Create the custom attribute **mtdnotify** for **Low or Normal** severity threats:

   a. Click **Add New.** The **Attribute Name** and **Attribute Type** fields are displayed.

   b. Select **Device** as the attribute type.

   c. Name the custom attribute **mtdnotify.**

   d. Click **Save** to monitor and notify.

3. Create the custom attribute **mtdblock** for **Elevated** or **Critical** severity threats:

   a. Click **Add New.**

   b. Select **Device** as the attribute type.

   c. Name the custom attribute **mtdblock.**

   d. Click **Save** to monitor and notify.

4. Create the custom attribute **mtdquarantine** for **Elevated** or **Critical** severity threats:

   a. Click **Add New.**

   b. Select **Device** as the attribute type.

   c. Name the custom attribute **mtdquarantine.**

   d. Click **Save** to monitor, notify, and quarantine.

5. Create the custom attribute **mtdtiered4hours** for **Low, Normal, Elevated,** or **Critical** severity threats:

   a. Click **Add New.**

   b. Select **Device** as the attribute type.

   c. Name the custom attribute **mtdtiered4hours.**

   d. Click **Save** to monitor and notify, wait for four hours, block, wait for another four hours, and quarantine.

Create compliance policy
^^^^^^^^^^^^^^^^^^^^^^^^

Create compliance actions using custom policies based on the MTD custom attributes created above.

1. In Ivanti Neurons for UEM admin console, go to **Policies.**

2. Click **+ Add.**

3. Select **Custom Policy.**

4. Enter **mtdnotify** as the policy name.

5. Under **Conditions,** select **Custom Device Attribute.**

6. Select **mtdnotify** from the drop-down box and set the condition **is equal to** 1.

7. Under **Choose Actions,** select **Monitor** and **Send Email and Push Notification.**

8. Under **Email Message** fields, enter the subject and body text.

9. Under **Push Notification,** enter message text.

10. Click **Yes, Next,** and **Done.**

11. Repeat this procedure to add the following policies: **mtdblock, mtdquarantine, mtdtiered4hours.**

12. Add other policies if needed.

..

   |Figure25|

Create device groups and match with custom policies and custom device attributes created above
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. In Ivanti Neurons for UEM admin console, go to **Devices > Device Groups.**

2. Click **+ Add.**

3. Enter **mtdNotify** as the device group name.

4. Under Dynamically Managed groups, select **Custom Device Attribute.**

5. Select **mtdnotify** from the drop-down box and set the condition **is equal to** 1.

6. Click **Save.**

7. Repeat this procedure to add the following groups: **mtdBlock, mtdQuarantine, mtdTiered4hours.**

Configure Zimperium MTD management console
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Set up, configure, and use the MTD console for supported MTD activities. <https://help.ivanti.com/mi/help/en_us/mtd/8x/gdcl/Content/MTD_all/mtd_using_zConsole_intro.htm>`__ When configuring policies in the Zimperium admin console, use the available MDM actions and mitigation actions.

|Figure26|

IBM Cloud Pak for Security
--------------------------

.. _ibm-cp4s:

IBM Cloud Pak for Security platform enables the integration of existing security tools and provides understanding and management of threats in the environment.

1. `Deploy an OpenShift cluster. <https://www.ibm.com/docs/en/cloud-paks/1.0?topic=installing-openshift-container-platform-clusters>`__ OpenShift needs to be in place before Cloud Pak for Security can be installed.

2. `Install Cloud Pak for Security <https://www.ibm.com/docs/en/cloud-paks/cp-security/1.10?topic=installing>`__.

3. `Configure LDAP authentication <https://www.ibm.com/docs/en/cloud-paks/cp-security/1.10?topic=providers-configuring-ldap-authentication>`__ so Cloud Pak for Security can leverage an existing LDAP directory server for authentication.

Once those steps are complete, open a web browser and navigate to the DNS name for Cloud Pak for Security. Additional documentation can be found at `Cloud Pak for Security Documentation <https://www.ibm.com/docs/en/cloud-paks/cp-security/1.10>`__.

IBM Security QRadar XDR
-----------------------

.. _ibm-qradar:

IBM Security QRadar platform provides various security capabilities including threat detection and response, security information and event management (SIEM), and security orchestration, automation, and response (SOAR).

Install and configure QRadar following IBM's `QRadar Installation and Configuration Guide <https://www.ibm.com/docs/en/qsip/7.4?topic=SS42VS_7.4/com.ibm.qradar.doc/c_qradar_pdfs.html>`__.

Once that is complete, open a web browser and navigate to the QRadar server web interface by using its IP address or DNS name.

Tenable.io
----------

.. _tenable-io:

Tenable.io is a cloud-based platform that is used in this build to provide network discovery, vulnerability, and scanning capabilities for enterprise components.

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As a cloud-based platform, a license must first be obtained, and a cloud instance deployed by Tenable. Once that is completed, Tenable.io can be accessed through the web interface located at https://cloud.tenable.com.

Deploy an agent
^^^^^^^^^^^^^^^

1. In Tenable.io, click the hamburger menu (☰) in the top left corner and navigate to **Settings > Sensors > Nessus Agents.**

2. Click **Add Nessus Agent** and save the Linking Key.

3. On the target endpoint, download the agent from https://downloads.tenable.com. When the download completes, run the executable file.

4. In the setup window, fill in the key from step 2, the server (in our case, cloud.tenable.com:443), and the agent groups that this agent will be part of (in our case, Default). Click **Next.**

5. Click **Install** and approve the request if User Account Control (UAC) comes up.

6. When installation completes, updates will continue running in the background. The update and connection process may take some time. The endpoint will then be shown in the cloud tenant.

..

   |Figure27|

Deploy a scanner
^^^^^^^^^^^^^^^^

1. In Tenable.io, navigate to **Settings > Sensors > Cloud Scanners.**

2. Click **Add Nessus Scanner** and save the Linking Key.

3. Download the Nessus Scanner .ova file from https://downloads.tenable.com.

4. Deploy the .ova file in your virtual environment.

5. Once the scanner is running, navigate to the IP address shown in the console in a web browser.

6. Login with the default username *wizard* and default password *admin*.

7. Enter new administrator credentials and click **Create Account.**

8. Click **Finish Setup** and authenticate with the new administrator credentials.

9. On the left-side navigation pane, click **Nessus.**

10. Click the URL shown in the *Nessus Installation Info* pane.

11. Click the radio button next to *Managed Scanner* and click **Continue**.

12. Enter the Linking Key from step 2 and click **Continue.**

13. Enter credentials for a new administrator account and click **Submit.**

14. The scanner will initialize and be visible on tenable.io. Scans can now be scheduled.

Integration with QRadar
~~~~~~~~~~~~~~~~~~~~~~~

For Tenable.io and QRadar integration, follow the `Tenable and IBM QRadar SIEM Integration Guide <https://docs.tenable.com/integrations/IBM/QRadar/Content/PDF/Tenable_and_IBM_QRadar_SIEM_Integration_Guide.pdf>`__.

Tenable.ad
----------

.. _tenable-ad:

Tenable.ad provides AD monitoring to detect attacks and identify vulnerabilities. In this build, Tenable.ad is integrated with the on-premises AD installation and configured to forward alerts to the IBM QRadar SIEM.

For Tenable.ad installation and configuration, follow the `Tenable.ad On-Premise Installation Guide. <https://docs.tenable.com/identity-exposure/Installation/Content/03_Install/install_tenablead.htm>`__

For Tenable.ad and QRadar integration, follow the `Tenable and IBM QRadar SIEM Integration Guide <https://docs.tenable.com/integrations/IBM/QRadar/Content/PDF/Tenable_and_IBM_QRadar_SIEM_Integration_Guide.pdf>`__.

Tenable NNM
-----------

.. _tenable-nnm:

Tenable Nessus Network Monitoring (NNM) monitors network traffic at the packet level to provide visibility into both server and client-side vulnerabilities. In this build, NNM was set to Asset Discovery mode and linked to Tenable.io in order to provide visibility into all network actors.

For Tenable.ad installation and configuration, follow the `Tenable NNM Documentation <https://docs.tenable.com/nnm/Content/GetStarted.htm>`__.

Deploy a Tenable NNM instance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. In Tenable.io, navigate to **Settings > Sensors > Nessus Network Monitors.**

2. Click **Add Nessus Network Monitor** and save the Linking Key.

3. Download the NNM .ova file from https://downloads.tenable.com.

4. Deploy the .ova file in your virtual environment.

5. Once the NNM instance is running, navigate to the IP address shown in the console in a web browser on port 8835.

6. Enter credentials for a new administrator account and click **Submit.**

7. Enter the Linking Key from step 2 and click **Continue.**

8. The NNM instance will initialize and be visible on Tenable.io. Additional NNM configuration can now occur if needed.

Mandiant Security Validation (MSV)
----------------------------------

.. _mandiant-msv:

Mandiant Security Validation (MSV) allows organizations to continuously validate the effectiveness of their cybersecurity controls by running actions that may conflict with the organization's policy and determining if those actions are detected and/or blocked. In this build, MSV is configured to regularly test the build's zero trust policies and report on the results.

MSV Director Installation/Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Download the MSV Director software from the Mandiant web portal and deploy it in a virtual environment.

2. Log into the MSV command line interface using credentials provided by Mandiant.

3. Run the command ``sudo vsetnet`` to apply network configuration.

4. Run the command ``sudo vsetdb --password new_password`` to set a new password for the Director database.

5. Use a web browser to access the MSV Director web interface at ``https://Director_IP/``.

6. Sign into the web interface using credentials provided by Mandiant.

7. Review and accept the End User Licensing Agreement, and apply the license provide by Mandiant.

8. Configure the DNS settings by navigating to **Settings > Director Settings > DNS Servers.**

9. Configure the NTP settings by navigating to **Settings > Director Settings > NTP Servers.**

10. Add Security Zones corresponding with the enterprise's network segments by navigating to **Environment > Security Zones.**

11. Download security content from the Mandiant web portal.

12. Navigate to **Settings > Director Settings > Content.**

13. Select **Import,** browse to the downloaded security content, and select the content files.

14. Click **Upload Import** and upload the files into the MSV Director web interface.

15. Once the upload is complete, click **Apply Import** to import the content files into MSV.

MSV Network Actor Installation/Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Download the MSV Network Actor software from the Mandiant web portal and deploy it in a virtual environment.

2. Log into the MSV command line interface using credentials provided by Mandiant.

3. Run the command ``sudo vsetnet`` to apply network configuration.

4. In the MSV Director web interface, navigate to **Environment > Actors.**

5. Click **Add Network Actors** and fill out the new **Actor** form.

6. Identify the Actor you just created in the **Pending Actors** table, expand the **Actions** menu, and click **Connect** to initiate a Director-to-Actor registration.

7. Enter the Actor's fully qualified domain name (FQDN) or IP address.

MSV Endpoint Actor Installation/Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Deploy an endpoint machine running Windows, macOS, or Linux.

2. In the MSV Director web interface, navigate to **Library > Actor Installer Files** and download the relevant installer onto the endpoint.

3. Navigate to **Environment > Actors,** click **Add Endpoint Actors,** and fill out the new Actor form.

4. Execute the Actor installer on the endpoint and proceed through the install process.

5. At the end of the install process, identify the actor you just created in the **Pending Actors** table and enter the value from the **Code** field into the Actor configuration field.

|Figure28|

6. The endpoint will register itself with the MSV Director, and setup will be complete.

MSV Evaluation Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Once the MSV Director and Actors have been configured, evaluations can be created to test security controls and policies. In the MSV Director web interface, navigate to **Library > Actions.**

2. Find the action(s) you would like to use for the evaluation and select the **+Queue** button to add the action to the Queue. Repeat this process until you have added all needed actions to the Queue.

..

   |Figure29|

3. After actions have been added to the Queue, click the **Queue** button in the upper right side of the web interface.

4. Select each of the actions in the **Unassigned** section and drag them to the **Current Actions** section.

5. Scroll up to the top of the page and click the **Save** button.

6. Under the **Test Type** dropdown, choose **Evaluation.**

7. Enter a name and a description, then select the **Save** button to save the evaluation.

8. Your new evaluation can be found by navigating to **Library > Evaluations** and filtering on **User Created.**

MSV Evaluation Execution
~~~~~~~~~~~~~~~~~~~~~~~~

1. Navigate to **Library > Evaluations** and select the evaluation you'd like to run. Click the **Run** button.

2. From the Evaluation screen, press the **Run Evaluation** button.

..

   |Figure30|

3. Select the **Source Actor** and **Destination Actor** from the dropdown menus. Click **Run Now.**

4. The evaluation will run, providing results once the actions have been attempted/completed.

..

   |Figure31|

DigiCert CertCentral
--------------------

.. _digicert-certcentral:

CertCentral simplifies digital trust and automates certificate management by consolidating tasks for issuing, installing, inspecting, remediating, and renewing TLS/SSL certificates in one place. In this build, CertCentral provided TLS/SSL certificates to any system needing those services.

For the latest CertCentral setup and usage instructions, see https://docs.digicert.com/get-started/.

Requesting a certificate
~~~~~~~~~~~~~~~~~~~~~~~~

1. Generate a Certificate Signing Request. This can be done with OpenSSL or DigiCert's Certificate Utility. Save the private key for later use.

2. In the DigiCert CertCentral dashboard, navigate to **Certificates > Requests** and click **Request a Certificate**. Select the certificate type.

3. Upload or paste the Certificate Signing Request in the provided field.

4. Select the coverage length, and add any other additional options as needed.

5. Click **Submit Request**.

Obtaining and implementing a certificate
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. In the DigiCert CertCentral dashboard, navigate to **Certificates > Orders** and select the request that you previously created.

2. Click **Download certificate as** and select **More Options…**

3. You will be presented with a list of certificate format options. Select the option/format that best pertains to the platform you will be using the certificate on. Click **Download**.

4. Obtain the private key that was originally generated with your Certificate Signing Request. If using DigiCert's Certificate Utility, this can be found using the Export function.

5. The certificate and private key can now be imported/installed and used on the intended platform.

.. |Figure1| image:: images/E1B1-Figure1.png
   :alt: This is a screenshot showing LDAP data source information created for Enterprise 1 AD.
.. |Figure2| image:: images/E1B1-Figure2.png
   :alt: This screenshot is an example of creating a new naming context.
.. |Figure3| image:: images/E1B1-Figure3.png
   :alt: This is a screenshot of the settings for the Proxy Backend.
.. |Figure4| image:: images/E1B1-Figure4.png
   :alt: This screenshot shows an example of having data sources configured from LDAP and a database.
.. |Figure5| image:: images/E1B1-Figure5.png
   :alt: This screenshot shows an example of creating a sub-Namespace.
.. |Figure6| image:: images/E1B1-Figure6.png
   :alt: This screenshot shows an example of configuring an LDAP backend.
.. |Figure7| image:: images/E1B1-Figure7.png
   :alt: This screenshot lists the four roles that were created for this build.
.. |Figure8| image:: images/E1B1-Figure8.png
   :alt: This screenshot shows the interface of the Role Editor.
.. |Figure9| image:: images/E1B1-Figure9.png
   :alt: This screenshot shows an example of an Assignment Rule.
.. |Figure10| image:: images/E1B1-Figure10.png
   :alt: This screenshot depicts the aggregation configuration for Radiant Logic.
.. |Figure11| image:: images/E1B1-Figure11.png
   :alt: This screenshot shows the LDAP configuration for integration with Radiant Logic.
.. |Figure12| image:: images/E1B1-Figure12.png
   :alt: This screenshot shows identity attribute mappings specific to this build.
.. |Figure13| image:: images/E1B1-Figure13.png
   :alt: This screenshot shows the configuration for the IQ Service host.
.. |Figure14| image:: images/E1B1-Figure14.png
   :alt: This screenshot shows the domain configuration.
.. |Figure15| image:: images/E1B1-Figure15.png
   :alt: This screenshot shows the configuration for the Correlation tab.
.. |Figure16| image:: images/E1B1-Figure16.png
   :alt: This screenshot shows the configuration for integration with Okta.
.. |Figure17| image:: images/E1B1-Figure17.png
   :alt: This screenshot shows the Download Certificate interface.
.. |Figure18| image:: images/E1B1-Figure18.png
   :alt: This screenshot shows the first part of a Data Protection policy.
.. |Figure19| image:: images/E1B1-Figure19.png
   :alt: This screenshot shows the second part of a Data Protection policy.
.. |Figure20| image:: images/E1B1-Figure20.png
   :alt: This screenshot shows examples of types of configurations.
.. |Figure21| image:: images/E1B1-Figure21.png
   :alt: This screenshot shows an example of a Privacy configuration.
.. |Figure22| image:: images/E1B1-Figure22.png
   :alt: This screenshot shows an example of an iOS AppConnect configuration.
.. |Figure23| image:: images/E1B1-Figure23.png
   :alt: This screenshot shows a list of configurations pushed to a device.
.. |Figure24| image:: images/E1B1-Figure24.png
   :alt: This screenshot shows what will be displayed once Access is registered with Ivanti Neurons for UEM.
.. |Figure25| image:: images/E1B1-Figure25.png
   :alt: This screenshot shows a list of policies.
.. |Figure26| image:: images/E1B1-Figure26.png
   :alt: This is a screenshot of the Zimperium admin console.
.. |Figure27| image:: images/E1B1-Figure27.png
   :alt: This is a screenshot listing the linked agents.
.. |Figure28| image:: images/E1B1-Figure28.png
   :alt: This is a screenshot showing a list of the Pending Actors.
.. |Figure29| image:: images/E1B1-Figure29.png
   :alt: This is a screenshot showing a sample of an action in the library.
.. |Figure30| image:: images/E1B1-Figure30.png
   :alt: This is a screenshot of the Test Evaluation screen from MSV.
.. |Figure31| image:: images/E1B1-Figure31.png
   :alt: This is a screenshot of example results from running an MSV evaluation.