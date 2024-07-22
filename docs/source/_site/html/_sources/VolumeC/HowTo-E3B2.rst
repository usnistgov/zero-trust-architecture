Enterprise 3 Build 2 (E3B2) - EIG Run - Microsoft Azure AD Conditional Access (later renamed Entra Conditional Access), Microsoft Intune, Forescout eyeControl, and Forescout eyeExtend as PEs Product Guides
===================================================================================================================================================================================================================

.. include:: /_publication_note.rst

This section of the practice guide contains detailed instructions for installing, configuring, and integrating all the products used to implement E3B2. For additional details on E3B2's logical and physical architectures, please refer to :ref:`Architecture and Builds`. Build 2 was built on top of Build 1 and all the components in Build 1 were used in this build. For E3B1's configuration please refer to :ref:`Enterprise 3 Build 1<enterprise 3 build 1 (e3b1) - eig crawl - azure ad conditional access (later renamed Entra Conditional Access) as pe product guides>`. Below are the additional components added to Build 2.

Microsoft Azure AD Identity Protection
--------------------------------------

.. _microsoft-azure-id-protection:

This section offers a guide for setting up the various components that make up Azure AD Identity Protection in your environment.

1. To ensure that all users register for multifactor authentication, configure Azure AD Multifactor Authentication registration policy using the information found at `Configure MFA Registration Policy <https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy>`__.

2. Sign-in risk policy enables detection of and response to suspicious logon sessions and unusual logon activity. Use the information found at `Configure Sign-in Risk Policy <https://learn.microsoft.com/en-us/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa?source=recommendations#enable-sign-in-risk-policy-for-mfa>`__ to configure the sign-in risk policy.

3. User-risk policy enables detection of and response to compromised user accounts. To configure this policy, use the information found at `Configure User-Risk Policy <https://learn.microsoft.com/en-us/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa?source=recommendations#enable-sign-in-risk-policy-for-mfa>`__.

Microsoft Azure AD Identity Governance
--------------------------------------

.. _MicrosoftAzureADGov:

Azure AD Identity Governance enables organizations to manage access to resources applying access request and approval workflows, access assignments and removals, access expiration, and access reviews.

1. `Create an access package <https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-access-package-first>`__ to encapsulate the target resources in a single object.

2. `Create policies <https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-access-package-first>`__ to define approvers and eligible requestors.

3. Requesting access to the access package can be done using the information found at `Request access <https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-access-package-first>`__.

4. To approve or deny access requests, use the information found at `Approve or deny request <https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-request-approve>`__.

Microsoft Defender for Cloud Apps
---------------------------------

.. _microsoft-defender-cloud:

(Note that the product name *Defender for Cloud Apps* was later changed to *Defender for Apps)*

Microsoft Defender for Cloud Apps is a cloud access broker solution that protects cloud applications and on-premises web applications by monitoring session activity to those applications, ensuring compliance to defined policy and mitigating detected threats.

1. `Login to the portal and activate your Defender for Cloud Apps <https://learn.microsoft.com/en-us/defender-cloud-apps/get-started>`__ tenant.

2. `Connect your apps to Defender for Cloud Apps <https://learn.microsoft.com/en-us/defender-cloud-apps/get-started#step-1-set-instant-visibility-protection-and-governance-actions-for-your-apps>`__. For custom web applications including on-premises web applications, use the information on `connecting a custom app to Defender for Cloud Apps <https://docs.microsoft.com/en-us/defender-cloud-apps/proxy-deployment-any-app>`__ to integrate your custom web applications.

3. Use the information on `creating and assigning policies <https://learn.microsoft.com/en-us/defender-cloud-apps/get-started#step-3-control-cloud-apps-with-policies>`__ to provide security controls to apps, ensuring compliance and mitigating threats.

4. `Deploy Conditional Access App Control <https://learn.microsoft.com/en-us/defender-cloud-apps/get-started#step-5-deploy-conditional-access-app-control-for-catalog-apps>`__, which leverages Azure AD conditional access policies and enforcement for connected apps.

Microsoft Azure AD Application Proxy
------------------------------------

Azure AD Application Proxy enables users to securely connect to internal applications via the Internet. It has two components, Application Proxy service and Application Proxy connector, which work together to provide access to the internal application.

1. Configure `Application Proxy deployment prerequisites <https://learn.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy-add-on-premises-application?source=recommendations>`__.

2.  `Install and register the Application Proxy connectors <https://learn.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy-add-on-premises-application?source=recommendations#install-and-register-a-connector>`__. Once the application proxy connectors are successfully installed and registered, the Application Proxy service will be enabled automatically.

3. `Add your application <https://learn.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy-add-on-premises-application#add-an-on-premises-app-to-azure-ad>`__ to Application Proxy.

Microsoft Defender for Cloud
----------------------------

Defender for Cloud is a SaaS-based cloud security posture management and cloud workload protection platform. It enables organizations to monitor their cloud and on-premises resources, determine differences and security issues based on benchmarks and regulations, and provide recommendations to help remediate the issues. Within Defender for Cloud, benchmarks and regulations encapsulate policies that are used as baselines to measure how compliant your environment is. This leads to the generation of a secure score.

1. `Enable Defender for Cloud <https://learn.microsoft.com/en-us/azure/defender-for-cloud/get-started>`__ for your subscription.

2. To receive a secure score, which provides a numeric value indicating your point-in-time security posture, you must ensure that the Azure Security Benchmark initiative or at least one other listed regulation is selected and applied to your subscription. Azure Security Benchmark should automatically apply to your subscription. Examples of regulations include PCI DSS, HIPAA, and NIST SP 800-53. Azure Security Benchmark is comprised of a set of controls that detect security misconfigurations based on best practices from common compliance frameworks.

3. `Apply regulations to your subscription <https://learn.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard>`__.

4. Defender for Cloud will list recommendations for your environment to improve the security posture. `Apply the listed security recommendations <https://learn.microsoft.com/en-us/azure/defender-for-cloud/review-security-recommendations>`__.

Forescout eyeSight
------------------

.. _ForescouteyeSight:

Forescout eyeSight provides asset discovery with both active and passive techniques, and through integrations with network and security infrastructure.

For installation, configuration, and integration instructions, refer to :ref:`Forescout eyeSight<forescout-eyesight>`.

Forescout eyeControl
--------------------

.. _ForescouteyeControl:

Forescout eyeControl enforces and automates network policies across the enterprise.

For Forescout eyeControl installation instructions, visit the `Forescout Installation Overview <https://docs.forescout.com/bundle/install-guide-8-3/page/install-guide-8-3.Installation-Overview.html>`__.

Configuring a policy
~~~~~~~~~~~~~~~~~~~~

1. In the Forescout Console, choose a policy.

2. Select the network segment to which the policy will be applied.

3. Add **Conditions** to select the attributes of the hosts that the policy will be applied to.

4. Add **Actions** that will be applied to the selected hosts.

5. Add any additional rules that will be used in the policy.

6. Run the policy.

Forescout eyeSegment
--------------------

.. _ForescouteyeSegment:

Forescout eyeSegment accelerates zero trust segmentation through visibility into traffic and transaction flows.

For Forescout eyeSegment installation instructions, visit the `Forescout Installation Overview <https://docs.forescout.com/bundle/install-guide-8-3/page/install-guide-8-3.Installation-Overview.html>`__. After installation has been completed, visit the `eyeSegment Application How-to Guide <https://docs.forescout.com/bundle/eyeseg-5-19-0-htg/page/eyeseg-5-19-0-htg.About-the-eyeSegment-Application.html>`__ to configure and use eyeSegment to analyze your network traffic from a dynamic zone perspective, simplify segmentation planning, and automate access control list (ACL)/VLAN assignment.

Access the eyeSegment Dashboard
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. From the Forescout Console, click **Dashboards**. This will launch a web browser and authenticate to the Forescout Web Client.

2. At the top of the Forescout Web Client, click **Segmentation**.

3. The initial dashboard is the eyeSegment Matrix. This dashboard can be used to analyze traffic and transaction flows between different network hosts, segments, and groups.

4. Open the eyeSegment Policy dashboard, which can be used to apply proposed zero trust rules. The effect of these rules can be seen in the eyeSegment Matrix.

5. Open the eyeSegment Health dashboard, which provides information about Reporting Appliances, Traffic Sensors, Endpoint Coverage, and the connection to the eyeSegment cloud.

Forescout eyeExtend
-------------------

.. _ForescouteyeExtend:

Forescout eyeExtend automates security workflows across disparate products through integration with other security technologies.

For Forescout eyeExtend installation instructions, visit the `Forescout Installation Overview <https://docs.forescout.com/bundle/install-guide-8-3/page/install-guide-8-3.Installation-Overview.html>`__. Once installation has been completed, visit the `Connect Plugin Configuration Guide <https://docs.forescout.com/bundle/connect-1-7-1-h/page/c-about-the-connect-plugin.html>`__, which provides the capability to build custom integrations with products that are not already provided. However, Forescout also provides a wide range of integrations at the official `Forescout eyeExtend repository <https://github.com/Forescout/eyeExtend-Connect/tree/master/Intune>`__.

Integration with Microsoft Endpoint Manager
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Integration instructions for Microsoft Endpoint Manager can be found at Forescout's official GitHub repository: https://github.com/Forescout/eyeExtend-Connect/tree/master/Intune.

Microsoft Azure IaaS
--------------------

.. _MicrosoftAzureIaaS:

Azure IaaS provides compute, networking, and storage services that enable the creation of an enterprise IT infrastructure by subscribers. The following section describes the Azure IaaS components that were deployed in this build.

1. Virtual Networks (VNETs) are isolated customer networks. They contain subnets and are built in Azure. We have three VNETs: a hub VNET, which provides central connectivity for other VNETs, and a GitLab VNET and a WordPress VNET, which are both designed to protect individual apps and their associated resources. Use the information at `Create a VNET <https://learn.microsoft.com/en-us/azure/virtual-network/quick-create-portal?source=recommendations>`__ to create and configure a virtual network. To enable communication between the hub and other VNETs, `establish peering <https://learn.microsoft.com/en-us/azure/virtual-network/tutorial-connect-virtual-networks-portal?source=recommendations>`__ between them.

2. Public VNETs are regular VNETs that have hosts with public IP addresses. The GitLab VNET is configured as a public subnet with a public IP address attached to the Application Gateway which was configured to provide load balancing and protection against common web attacks.

3. Private VNETs are regular VNETs that have hosts with only private IP addresses and are reachable only by internal users by default. WordPress VNET was configured as a private VNET.

4. `Configure Azure Bastion <https://learn.microsoft.com/en-us/azure/bastion/quickstart-host-portal>`__ to enable web-based SSH and remote desktop-based access to servers and virtual machines.

5. `Instantiate and configure Azure Firewall <https://learn.microsoft.com/en-us/azure/firewall/tutorial-hybrid-portal>`__ in the hub VNET to provide protection for incoming traffic from both the Internet and the VPN traffic from on-prem clients.

6. `Use network security groups (NSGs) to filter inbound or outbound traffic <https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview?source=recommendations>`__ to or from Azure resources. Enable only ports that are necessary for appropriate access.

7. Azure App Gateway is a web traffic load balancer that can detect and stop common web attacks. The Azure App Gateway was configured to protect the GitLab application servers, and the WordPress servers. Use the information at `Application Gateway Quickstart <https://learn.microsoft.com/en-us/azure/application-gateway/quick-create-portal>`__ to configure the Application Gateway.
