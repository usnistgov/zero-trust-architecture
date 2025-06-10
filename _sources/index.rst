**NIST SPECIAL PUBLICATION 1800-35**

Implementing a Zero Trust Architecture: Full Document 
=========================================================================

.. include:: /_publication_note.rst

.. toctree::
   :maxdepth: 1
   :titlesonly:
   :glob:
   :hidden:

   VolumeA/ExecutiveSummary.rst
   VolumeA/Introduction.rst
   VolumeA/ProjectOverview.rst
   VolumeB/architecture.rst
   VolumeC/index.rst
   VolumeB/GeneralFindings.rst
   VolumeD/index.rst
   VolumeE/index.rst
   VolumeB/ZeroTrustTakeaways.rst
   glossary.rst
   acronyms.rst
   changelog.rst


+----------------------------+----------------------------+-----------------------+------------------------+
| **Oliver Borchert**        | **Brian Butler**           | **Madhu Dodda**       | **Frank Briguglio**    |
|                            |                            |                       |                        |
| **Gema Howell**            | **Mike Delaguardia**       | **Tim LeMaster**      | **Ryan Tighe**         |
|                            |                            |                       |                        |
| **Alper Kerman**           | **Matthew Hyatt**          | Lookout               | SailPoint              |
|                            |                            |                       |                        |
| **Scott Rose**             | **Randy Martin**           | |                     | |                      |
|                            |                            |                       |                        |
| **Murugiah Souppaya**      | **Peter Romness**          | **Ken Durbin**        |                        |
|                            |                            |                       |                        |
| National Institute of      | Cisco                      | **James Elliott**     |                        |
|                            |                            |                       |                        |
| Standards and Technology   | |                          | **Earl Matthews**     |                        |
|                            |                            |                       |                        |
| |                          | **Corey Bonnell**          | **David Pricer**      |                        |
|                            |                            |                       |                        |
| **Jason Ajmo**             | **Dean Coclin**            | Mandiant              |                        |
|                            |                            |                       |                        | 
| **Yemi Fashina**           | DigiCert                   | |                     | **Chris Jensen**       |
|                            |                            |                       |                        |
| **Parisa Grayeli**         | |                          | **Joey Cruz**         | **Joshua Moll**        |
|                            |                            |                       |                        |
| **Joseph Hunt**            | **Ryan Johnson**           | **Tarek Dawoud**      | Tenable                |
|                            |                            |                       |                        |
| **Jason Hurlburt**         | **Dung Lam**               | **Carmichael Patton** | |                      |
|                            |                            |                       |                        |
| **Nedu Irrechukwu**        | **Darwin Tolbert**         | **Alex Pavlovsky**    | **Jason White**        |
|                            |                            |                       |                        |
| **Joshua Klosterman**      | F5                         | **Brandon Stephenson**| Trellix, Public Sector |
|                            |                            |                       |                        |
| **Oksana Slivina**         | |                          | **Clay Taylor**       | |                      |
|                            |                            |                       |                        |
| **Susan Symington**        | **Tim Jones**              | Microsoft             | **Joe Brown**          |
|                            |                            |                       |                        |
| **Allen Tan**              | **Tom May**                | |                     | **Gary Bradt**         |
|                            |                            |                       |                        |
| The MITRE Corporation      | Forescout                  | **Bob Lyons**         | Zimperium              |
|                            |                            |                       |                        |
| |                          | |                          | **Vinu Panicker**     | |                      |
|                            |                            |                       |                        |
| **Karen Scarfone**         | **Christopher Altman**     | Okta                  | **Jeffrey Adorno**     |
|                            |                            |                       |                        |
|                            |                            | |                     |                        |
|                            |                            |                       |                        |
|                            |                            | **Peter Bjork**       |                        |
|                            |                            |                       |                        |
|                            |                            | **Hans Drolshagen**   |                        |
|                            |                            |                       |                        |
|                            |                            | Omnissa               |                        |
|                            |                            |                       |                        |
| Scarfone Cybersecurity     | **Alex Bauer**             | |                     | **Syed Ali**           |
|                            |                            |                       |                        |
| |                          | **Marco Genovese**         | **Imran Bashir**      | **Bob Smith**          |
|                            |                            |                       |                        |
| **William Barker**         | Google Cloud               | **Ali Haider**        | Zscaler                |
|                            |                            |                       |                        |
| Dakota Consulting          | |                          | **Nishit Kothari**    |                        |
|                            |                            |                       |                        |
| |                          | **Andrew Campagna**        | **Sean Morgan**       |                        |
|                            |                            |                       |                        |
| **Peter Gallagher**        | **John Dombroski**         | **Seetal Patel**      |                        |
|                            |                            |                       |                        |
| **Aaron Palermo**          | **Adam Frank**             | **Norman Wong**       |                        |
|                            |                            |                       |                        |
| Appgate                    | **Nalini Kannan**          | Palo Alto Networks    |                        |
|                            |                            |                       |                        |
| |                          | **Priti Patil**            | |                     |                        |
|                            |                            |                       |                        |
| **Madhu Balaji**           | **Harmeet Singh**          | **Zack Austin**       |                        |
|                            |                            |                       |                        |
| **Adam Cerini**            | **Mike Spisak**            | **Shawn Higgins**     |                        |
|                            |                            |                       |                        |
| **Rajarshi Das**           | **Krishna Yellepeddy**     | **Rob Woodsworth**    |                        |
|                            |                            |                       |                        |
| AWS (Amazon Web Services)  | IBM                        | PC Matic              |                        |
|                            |                            |                       |                        |
| |                          | |                          | |                     |                        |
|                            |                            |                       |                        |
| **Jacob Barosin**          | **Nicholas Herrmann**      | **Mitchell Lewars**   |                        |
|                            |                            |                       |                        |
| **Kyle Black**             | **Corey Lund**             | **Bryan Rosensteel**  |                        |
|                            |                            |                       |                        |
| **Scott Gordon**           | **Farhan Saifudin**        | Ping Identity         |                        |
|                            |                            |                       |                        |
| **Jerry Haskins**          | Ivanti                     | |                     |                        |
|                            |                            |                       |                        |
| **Keith Luck**             |                            | **Don Coltrain**      |                        |
|                            |                            |                       |                        |
| **Dale McKay**             |                            | **Wade Ellery**       |                        |
|                            |                            |                       |                        |
| **Sunjeet Randhawa**       |                            | **Deborah McGinn**    |                        |
|                            |                            |                       |                        |
| Broadcom                   |                            | Radiant Logic         |                        |
+----------------------------+----------------------------+-----------------------+------------------------+

June 2025

FINAL

|This graphic contains the logos for NIST and the NCCoE.|

**DISCLAIMER**

Certain commercial entities, equipment, products, or materials may be identified by name or company logo or other insignia in order to acknowledge their participation in this collaboration or to describe an experimental procedure or concept adequately. Such identification is not intended to imply special status or relationship with NIST or recommendation or endorsement by NIST or NCCoE; neither is it intended to imply that the entities, equipment, products, or materials are necessarily the best available for the purpose.

While NIST and the NCCoE address goals of improving management of cybersecurity and privacy risk through outreach and application of standards and best practices, it is the stakeholder's responsibility to fully perform a risk assessment to include the current threat, vulnerabilities, likelihood of a compromise, and the impact should the threat be realized before adopting cybersecurity measures such as this recommendation.

National Institute of Standards and Technology Special Publication 1800-35, Natl. Inst. Stand. Technol. Spec. Publ. 1800-35, (June 2025), CODEN: NSPUE2

**NIST TECHNICAL SERIES POLICIES**

`Copyright, Use, and Licensing Statements <https://www.nist.gov/nist-research-library/nist-publications>`__

`NIST Technical Series Publication Identifier Syntax <https://www.nist.gov/system/files/documents/2022/04/01/PubID_Syntax_NIST_TechPubs.pdf>`__

**AUTHOR ORCID IDS** 

Oliver Borchert: 0009-0006-1880-0542

Gema Howell: 0000-0002-0428-5045

Alper Kerman: 0009-0000-5880-8369

Scott Rose: 0000-0002-3105-7427

Murugiah Souppaya: 0000-0002-8055-8527

Karen Scarfone: 0000-0001-6334-9486

William Barker: 0000-0002-4113-8861


**FEEDBACK**

You can view or download the final guide at the `NCCoE ZTA project page <https://www.nccoe.nist.gov/projects/implementing-zero-trust-architecture>`__.

Comments on this publication may be submitted to: nccoe-zta-project@list.nist.gov.

All comments are subject to release under the Freedom of Information Act.


| National Cybersecurity Center of Excellence
| National Institute of Standards and Technology
| 100 Bureau Drive
| Mailstop 2002
| Gaithersburg, MD 20899
| Email: nccoe@nist.gov

**NATIONAL CYBERSECURITY CENTER OF EXCELLENCE**

The National Cybersecurity Center of Excellence (NCCoE), a part of the National Institute of Standards and Technology (NIST), is a collaborative hub where industry organizations, government agencies, and academic institutions work together to address businesses ' most pressing cybersecurity issues. This public-private partnership enables the creation of practical cybersecurity solutions for specific industries, as well as for broad, cross-sector technology challenges. Through consortia under Cooperative Research and Development Agreements (CRADAs), including technology partners—from Fortune 50 market leaders to smaller companies specializing in information technology security—the NCCoE applies standards and best practices to develop modular, adaptable example cybersecurity solutions using commercially available technology. The NCCoE documents these example solutions in the NIST Special Publication 1800 series, which maps capabilities to the NIST Cybersecurity Framework (CSF) and details the steps needed for another entity to re-create the example solution. The NCCoE was established in 2012 by NIST in partnership with the State of Maryland and Montgomery County, Maryland.

To learn more about the NCCoE, visit https://www.nccoe.nist.gov/. To learn more about NIST, visit https://www.nist.gov.

**NIST CYBERSECURITY PRACTICE GUIDES**

NIST Cybersecurity Practice Guides (Special Publication 1800 series) target specific cybersecurity challenges in the public and private sectors. They are practical, user-friendly guides that facilitate the adoption of standards-based approaches to cybersecurity. They show members of the information security community how to implement example solutions that help them align with relevant standards and best practices, and provide users with the materials lists, configuration files, and other information they need to implement a similar approach.

The documents in this series describe example implementations of cybersecurity practices that businesses and other organizations may voluntarily adopt. These documents do not describe regulations or mandatory practices, nor do they carry statutory authority.

**ABSTRACT**

A zero trust architecture (ZTA) enables secure authorized access to enterprise resources that are distributed across on-premises and multiple cloud environments, while enabling a hybrid workforce and partners to access resources from anywhere, at any time, from any device in support of the organization's mission. 

This NIST Cybersecurity Practice Guide explains how organizations can implement ZTA consistent with the concepts and principles outlined in NIST Special Publication (SP) 800-207, Zero Trust Architecture. The NCCoE worked with 24 collaborators under Cooperative Research and Development Agreements (CRADAs) to integrate commercially available technology to build 19 ZTA example implementations and demonstrate a number of common use cases. The guide includes detailed technical information on each example ZTA implementation, providing models that organizations can emulate. The Guide also summarizes best practices and lessons learned from the implementations and integrations to make it easier and more cost-effective to implement ZTA. This guide also includes mappings of ZTA principles and technologies to commonly used security standards and guidelines.


**KEYWORDS**

*enhanced identity governance (EIG); identity, credential, and access management (ICAM); microsegmentation; secure access service edge (SASE); software-defined perimeter (SDP); zero trust; zero trust architecture (ZTA).*

**ACKNOWLEDGMENTS**

We are grateful to the following individuals for their generous contributions of expertise and time.

-  Appgate: Jason Garbis, Adam Rose, Jonathan Roy

-  AWS (Amazon Web Services): Conrad Fernandes\*, Harrison Holstein, Quint Van Deman

-  Broadcom: Andrew Babakian\*, Genc Domi\*, Paul Mancuso, Eric Michael, Dennis Moreau\*, Wayne Pauley\*, Jacob Rapp\*, Lewis Shepherd

-  Cisco: Ken Andrews, Robert Bui, Leo Lebel, Tom Oast, Aaron Rodriguez, Kelly Sennett, Steve Vetter, Micah Wilson

-  F5: Daniel Cayer, David Clark, Jay Kelley, Darrell Pierson

-  Forescout: Yejin Jang\*, Neal Lucier\*

-  Google Cloud: Tim Knudson\*

-  IBM: Nilesh Atal, Himanshu Gupta, Lakshmeesh Hegde, Sharath Math, Naveen Murthy, Nikhil Shah, Deepa Shetty, Harishkumar Somashekaraiah

-  IT Coalition: Aaron Cook, Vahid Esfahani\*, Jeff Laclair, Ebadullah Siddiqui\*, Musumani Woods\*

-  Ivanti: Patty Arcano, Jeffery Burton, Jay Dineshkumar

-  Lookout: Tyler Croak, Jeff Gilhool, Hashim Khan\*

-  Microsoft: Thomas Detzner, Ehud Itshaki, Janet Jones, Hemma Prafullchandra\*, Enrique Saggese, Sarah Young

-  MITRE: Eileen Division\*, Spike E. Dog\*, Sallie Edwards\*, Ayayidjin Gabiam, Jolene Loveless\*, Karri Meldorf, Kenneth Sandlin, Lauren Swan, Jessica Walton\*

-  NIST: Mike Bartock, Julia Chua, Douglas Montgomery, Cherilyn Pascoe, Michael Powell, Kevin Stine

-  Okta: Brian Dack, Sean Frazier, Naveed Mirza, Kelsey Nelson, Ron Wilson

-  Omnissa: Keith Luck\*

-  PC Matic: Andy Tuch

-  Ping Identity: Ivan Anderson, Aubrey Turner

-  Radiant Logic: Bill Baz, Rusty Deaton, John Petrutiu, Lauren Selby

-  SailPoint: Peter Amaral, Jim Russell, Esteban Soto

-  Tenable: Jeremiah Stallcup

- Zimperium: Dan Butzer, Jim Kovach\*, Kern Smith

-  Zscaler: Jeremy James, Lisa Lorenzin\*, Matt Moulton, Patrick Perry

*\* Former employee; all work for this publication was done while at that organization*

Special thanks to all who reviewed and provided feedback on this document.

The Technology Collaborators who participated in this project submitted their capabilities in response to a notice in the Federal Register. Respondents with relevant capabilities or product components were invited to sign a Cooperative Research and Development Agreement (CRADA) with NIST, allowing them to participate in a consortium to build this example solution. We worked with:

.. table:: Technology Partners/Collaborators

   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Appgate <https://www.appgate.com/>`__          | `IBM <https://www.ibm.com/>`__                                               | `PC Matic <https://www.pcmatic.com/pro/>`__                                |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `AWS <https://aws.amazon.com/>`__               | `Ivanti <https://www.ivanti.com/>`__                                         | `Ping Identity <https://www.pingidentity.com/>`__                          |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Broadcom <https://www.broadcom.com/>`__        | `Lookout <https://www.lookout.com/>`__                                       | `Radiant Logic <https://explore.radiantlogic.com/home>`__                  |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Cisco <https://www.cisco.com/>`__              | `Mandiant <https://www.mandiant.com/>`__                                     | `SailPoint <https://www.sailpoint.com/>`__                                 |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `DigiCert <https://www.digicert.com/>`__        | `Microsoft <https://www.microsoft.com/en-us/security/business/zero-trust>`__ | `Tenable <https://www.tenable.com/>`__                                     |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `F5 <https://www.f5.com/>`__                    | `Okta <https://www.okta.com/>`__                                             | `Trellix <https://www.trellix.com/en-us/index.html>`__                     |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Forescout <https://www.forescout.com/>`__      | `Omnissa <https://www.omnissa.com/>`__                                       | `Zimperium <https://www.zimperium.com/>`__                                 |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Google Cloud <https://cloud.google.com/>`__    | `Palo Alto Networks <https://www.paloaltonetworks.com/>`__                   | `Zscaler <https://www.zscaler.com/>`__                                     |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+

Note that after the VMware End User Computing division products were implemented at the NCCoE, VMware was acquired by Broadcom, then the VMware End User Computing Division was divested and reformed under a new entity, Omnissa LLC. Symantec was also previously acquired by Broadcom. 

**DOCUMENT CONVENTIONS**

The terms “shall” and “shall not” indicate requirements to be followed strictly to conform to the publication and from which no deviation is permitted. The terms “should” and “should not” indicate that among several possibilities, one is recommended as particularly suitable without mentioning or excluding others, or that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited. The terms “may” and “need not” indicate a course of action permissible within the limits of the publication. The terms “can” and “cannot” indicate a possibility and capability, whether material, physical, or causal.

**PATENT DISCLOSURE NOTICE**

NOTICE: The Information Technology Laboratory (ITL) has requested that holders of patent claims whose use may be required for compliance with the guidance or requirements of this publication disclose such patent claims to ITL. However, holders of patents are not obligated to respond to ITL calls for patents and ITL has not undertaken a patent search in order to identify which, if any, patents may apply to this publication.

As of the date of publication and following call(s) for the identification of patent claims whose use may be required for compliance with the guidance or requirements of this publication, no such patent claims have been identified to ITL. 

No representation is made or implied by ITL that licenses are not required to avoid patent infringement in the use of this publication.


.. |This graphic contains the logos for NIST and the NCCoE.| image:: images/Figure1.png
   :alt: This graphic contains the logos for NIST and the NCCoE.
