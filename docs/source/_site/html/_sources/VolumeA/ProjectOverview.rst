Project Overview
=================

Motivation for the Project
---------------------------
As enterprise data and resources become distributed across on-premises environments and multiple clouds, protecting them has become increasingly challenging. Many users need access from anywhere, at any time, from any device to support the organization’s mission. Data is created, stored, transmitted, and processed across different organizations’ environments, which are distributed across on-premises and multiple clouds to meet ever-evolving business use cases. It is no longer feasible to simply protect data and resources at the perimeter of the enterprise environment or to assume that all users, devices, applications, and services within it can be trusted. 

A zero-trust architecture (ZTA) enables secure authorized access to assets—machines, applications and services running on them, and associated data and resources—whether located on-premises or in the cloud, for a hybrid workforce and partners based on an organization’s defined access policy. For each access request, ZTA explicitly verifies the context available at access time—this includes both static user profile information or non-person entity information such as the requester’s identity and role; and dynamic information such as geolocation, the requesting device’s health and credentials, the sensitivity of the resource, access pattern anomalies, and whether the request is warranted and in accordance with the organization’s business process logic. If the defined policy is met, a secure session is created to protect all information transferred to and from the resource. A real-time, risk-based assessment of resource access and access pattern anomaly detection with continuous policy evaluation are performed to establish and maintain the access. A ZTA can also protect organizations from non-organizational resources that their users and applications may connect to, helping to stop threats originating from outside of the organization’s control. 

The goal of this project is to develop and demonstrate various ZTA implementations. NCCoE is collaborating with ZTA technology providers to build numerous example ZTA solutions and demonstrate their ability to meet the tenets of ZTA described in NIST SP 800-207. The goal of the solutions is to enforce corporate security policy dynamically and in near-real-time to restrict access to authenticated, authorized users, devices, and non-person entities while flexibly supporting a complex set of diverse business outcomes involving both remote and on-premises workforces, use of the cloud, partner collaboration, and support for contractors. The example solutions are designed to demonstrate the ability to protect against and detect attacks and malicious insiders. They showcase the ability of ZTA products to interoperate with existing enterprise and cloud technologies while trying to minimize impact on end-user experience. 

The project can help organizations plan how to evolve their existing enterprise environments to ZTA, starting with an assessment of their current resources, strengths, and weaknesses, and setting mile-stones along a path of continuous improvement, gradually bringing them closer to achieving the ZTA goals they have prioritized based on risk, cost, resources, and their unique mission. The goal is to ena-ble organizations to thoughtfully apply ZTA controls that best protect their business while enabling them to operate as they need to.

Challenges in Implementing ZTA
-------------------------------

Throughout this project, numerous challenges organizations may face in implementing ZTA have been identified, including the following:

- Organization buy-in and support, such as:

 - Perception that ZTA is suited only for large organizations and requires significant investment rather than understanding that ZTA is a set of guiding principles suitable for organizations of any size

 - Concern that ZTA might negatively impact the operation of the environment or end-user experience

 - Lack of resources to develop necessary policies and a pilot or proof-of-concept implementation needed to inform a transition plan

 - Leveraging existing investments and balancing priorities while making progress toward a ZTA via modernization initiatives 

 - Lack of understanding regarding what additional skills and training administrators, security personnel, operators, end users, and policy decision makers may require

- Missing foundational pieces, such as:

 - Lack of adequate asset inventory and management needed to fully understand the business applications, assets, and processes that need to be protected, with no clear understanding of the criticality of these resources

 - Lack of adequate digital definition, management, and tracking of user roles across the organization needed to enforce fine-grained, need-to-know access policy for specific applications and services

 - Lack of visibility of the organization’s communications and usage patterns—limited understanding of the transactions that occur between an organization’s subjects, assets, applications, and services, and absence of the data necessary to identify these communications and their specific flows

 - Lack of information regarding everything that encompasses the organization’s attack surface. Organizations can usually address threats with traditional security tools in the layers that they currently manage and maintain such as networks and applications, but elements of a ZTA may extend beyond their normal purview. False assumptions are often made in understanding the health of a device as well as its exposure to supply chain risks.

- Technical challenges, such as:

 - Integrating various types of commercially available technologies of varying maturities, assessing capabilities, and identifying technology gaps to build a complete ZTA

 - Lack of a standardized policy to distribute, manage, and enforce security policy, causing organizations to face either a fragmentary policy environment or non-interoperable components

 - Lack of common understanding and language of ZTA across the community and within the organization, gauging the organization’s ZTA maturity, determining which ZTA approach is most suitable for the business, and developing an implementation plan

 - There is not a single ZTA that fits all. ZTAs need to be designed and integrated for each organization based on the organization’s requirements and risk tolerance, as well as its existing invested technologies and environments.

Project Approach
----------------

This project began with a clean laboratory environment that we populated with various applications and services that would be expected in a typical enterprise to create several baseline enterprise architectures. Examples include SIEMs, vulnerability scanning and assessment tools, security validation tools, and discovery tools. 

Next, we used a phased approach to develop example ZTA solutions. This approach was designed to represent how we believe most enterprises will evolve their enterprise architecture toward ZTA, i.e., by starting with their already-existing enterprise environment and gradually adding or adapting capa-bilities. Our first implementations with minimum viable solution were EIG deployments because the identity-based controls provided by EIG are foundational components of ZTA. We called this phase of the project the EIG crawl phase, which did not include cloud capabilities, and followed by the EIG run phase, which we added cloud capabilities. We gradually deployed additional functional components and capabilities to address an increasing number of ZTA requirements and deployed microsegmenta-tion, SDP, and SASE approaches. The microsegmentation approach places one or more resources on unique network segments protected by gateway security components and/or places software agents or firewalls on endpoint assets to implement host-based microsegmentation. The SDP approach in-volves reconfiguring the network based on policy access decisions. When implemented at the applica-tion layer, this may be accomplished by establishing a secure channel between a software agent on the endpoint requesting access to the resource and the resource gateway. The SASE approach delivers converged network and security as a service capability, including Software-Defined Wide Area Net-work (SD-WAN), Secure Web Gateway (SWG), Cloud Access Security Broker (CASB), Next Generation Firewall (NGFW), and Zero Trust Network Access (ZTNA). SASE supports branch office, remote worker, and on-premises secure access use cases. SASE is primarily delivered as a service and enables zero trust access based on the identity of the device or entity, combined with real-time context and securi-ty and compliance policies.

Given the importance of discovery to the successful implementation of a ZTA, we initially deployed it to continuously observe the environment and use those observations to audit and validate the documented baseline map on an ongoing basis. Because we had instantiated the baseline environment ourselves, we already had a good initial understanding of it. However, we were able to use the discovery tools to audit and validate what we deployed and provisioned, correlate known data with information reported by the tools, and use the tool outputs to formulate initial zero trust policy, ultimately ensuring that observed network flows correlate to static policies.

As we continue to develop additional ZTA builds, we do so with the understanding that there is no single approach for migrating to ZTA that is best for all enterprises and the recognition that ZTA is a set of concepts and principles, not a set of technical specifications that can be complied with. The objective, instead, is continuous improvement of access control processes and policies in accordance with the principles of ZTA. 