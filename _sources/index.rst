Implementing a Zero Trust Architecture 
=========================================

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


+----------------------------+----------------------------+-----------------------+------------------------+
| **Oliver Borchert**        | **Brian Butler**           | **Madhu Dodda**       | **Frank Briguglio**    |
|                            |                            |                       |                        |
| **Gema Howell**            | **Mike Delaguardia**       | **Tim LeMaster**      | **Ryan Tighe**         |
|                            |                            |                       |                        |
| **Alper Kerman**           | **Matthew Hyatt**          | Lookout               | SailPoint              |
|                            |                            |                       |                        |
| **Scott Rose**             | **Randy Martin**           | |                     | |                      |
|                            |                            |                       |                        |
| **Murugiah Souppaya**      | **Peter Romness**          | **Ken Durbin**        | **Kyle Black**         |
|                            |                            |                       |                        |
| National Institute of      | Cisco                      | **James Elliott**     | **Scott Gordon**       |
|                            |                            |                       |                        |
| Standards and Technology   | |                          | **Earl Matthews**     | **Sunjeet Randhawa**   |
|                            |                            |                       |                        |
| |                          | **Corey Bonnell**          | **David Pricer**      | Symantec by Broadcom   |
|                            |                            |                       |                        |
| **Jason Ajmo**             | **Dean Coclin**            | Mandiant              | |                      |
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
| **Peter Bjork**            | **Corey Lund**             | **Bryan Rosensteel**  |                        |
|                            |                            |                       |                        |
| **Hans Drolshagen**        | **Farhan Saifudin**        | Ping Identity         |                        |
|                            |                            |                       |                        |
| **Keith Luck**             | Ivanti                     | |                     |                        |
|                            |                            |                       |                        |
| **Jerry Haskins**          |                            | **Don Coltrain**      |                        |
|                            |                            |                       |                        |
| **Dale McKay**             |                            | **Wade Ellery**       |                        |
|                            |                            |                       |                        |
| Broadcom (VMware)          |                            | **Deborah McGinn**    |                        |
|                            |                            |                       |                        |
|                            |                            | Radiant Logic         |                        |
+----------------------------+----------------------------+-----------------------+------------------------+

July 2024

FOURTH PRELIMINARY DRAFT

|This graphic contains the logos for NIST and the NCCoE.|

DISCLAIMER
----------

Certain commercial entities, equipment, products, or materials may be identified by name or company logo or other insignia in order to acknowledge their participation in this collaboration or to describe an experimental procedure or concept adequately. Such identification is not intended to imply special status or relationship with NIST or recommendation or endorsement by NIST or NCCoE; neither is it intended to imply that the entities, equipment, products, or materials are necessarily the best available for the purpose.

National Institute of Standards and Technology Special Publication 1800-35, Natl. Inst. Stand. Technol. Spec. Publ. 1800-35, (July 2024), CODEN: NSPUE2

FEEDBACK
---------

NIST is using an agile process to publish this content. As work continues on implementing additional example solutions, documentation is being made available as soon as possible rather than delaying release until all builds are completed. You can improve this guide by contributing feedback. As you review and adopt this solution for your own organization, we ask you and your colleagues to share your experience and advice with us.

Please submit comments by completing the comment template spreadsheet posted on https://www.nccoe.nist.gov/projects/implementing-zero-trust-architectures and emailing it to nccoe-zta-project@list.nist.gov.

Public comment period: July 31, 2024 through September 30, 2024

All comments are subject to release under the Freedom of Information Act.

NIST is particularly interested in your feedback on the following questions:

1.	How well do the practices in this guide relate to existing practices leveraged by your organization? Are there significant gaps between the sets of practices that this guide should address?

2.	How do you expect this guide to influence your future practices and processes?

3.	How do you envision using this guide? What changes would you like to see to increase/improve that use?

4.	What suggestions do you have on changing the format of the provided information?


| National Cybersecurity Center of Excellence
| National Institute of Standards and Technology
| 100 Bureau Drive
| Mailstop 2002
| Gaithersburg, MD 20899
| Email: nccoe@nist.gov

NATIONAL CYBERSECURITY CENTER OF EXCELLENCE
-------------------------------------------

The National Cybersecurity Center of Excellence (NCCoE), a part of the National Institute of Standards and Technology (NIST), is a collaborative hub where industry organizations, government agencies, and academic institutions work together to address businesses ' most pressing cybersecurity issues. This public-private partnership enables the creation of practical cybersecurity solutions for specific industries, as well as for broad, cross-sector technology challenges. Through consortia under Cooperative Research and Development Agreements (CRADAs), including technology partners—from Fortune 50 market leaders to smaller companies specializing in information technology security—the NCCoE applies standards and best practices to develop modular, adaptable example cybersecurity solutions using commercially available technology. The NCCoE documents these example solutions in the NIST Special Publication 1800 series, which maps capabilities to the NIST Cybersecurity Framework and details the steps needed for another entity to re-create the example solution. The NCCoE was established in 2012 by NIST in partnership with the State of Maryland and Montgomery County, Maryland.

To learn more about the NCCoE, visit https://www.nccoe.nist.gov/. To learn more about NIST, visit https://www.nist.gov.

NIST CYBERSECURITY PRACTICE GUIDES
-----------------------------------

NIST Cybersecurity Practice Guides (Special Publication 1800 series) target specific cybersecurity challenges in the public and private sectors. They are practical, user-friendly guides that facilitate the adoption of standards-based approaches to cybersecurity. They show members of the information security community how to implement example solutions that help them align with relevant standards and best practices, and provide users with the materials lists, configuration files, and other information they need to implement a similar approach.

The documents in this series describe example implementations of cybersecurity practices that businesses and other organizations may voluntarily adopt. These documents do not describe regulations or mandatory practices, nor do they carry statutory authority.

ABSTRACT
----------

A zero trust architecture (ZTA) enables secure authorized access to enterprise resources that are distributed across on-premises and multiple cloud environments, while enabling a hybrid workforce and partners to access resources from anywhere, at any time, from any device in support of the organization's mission. 

This NIST Cybersecurity Practice Guide explains how organizations can implement ZTA consistent with the concepts and principles outlined in NIST Special Publication (SP) 800-207, Zero Trust Architecture. The NCCoE worked with 24 collaborators under Cooperative Research Development Agreements (CRADAs) to integrate commercially available technology to build 17 ZTA example implementations and demonstrate a number of common use cases. Detailed technical information on each build can serve as a valuable resource for your technology implementers by providing models they can emulate. The lessons learned from the implementations and integrations can benefit your organization by saving time and resources. This guide also includes mappings of ZTA principles to commonly used security standards and guidance.


KEYWORDS
---------

*enhanced identity governance (EIG); identity, credential, and access management (ICAM); microsegmentation; secure access service edge (SASE); software-defined perimeter (SDP); zero trust; zero trust architecture (ZTA).*

ACKNOWLEDGMENTS
----------------

We are grateful to the following individuals for their generous contributions of expertise and time.

-  Appgate: Jason Garbis, Adam Rose, Jonathan Roy

-  AWS (Amazon Web Services): Conrad Fernandes\*, Harrison Holstein, Quint Van Deman

-  Broadcom (VMware): Andrew Babakian\*, Genc Domi\*, Paul Mancuso, Dennis Moreau\*, Wayne Pauley\*, Jacob Rapp\*

-  Cisco: Ken Andrews, Robert Bui, Leo Lebel, Tom Oast, Aaron Rodriguez, Kelly Sennett, Steve Vetter, Micah Wilson

-  F5: Daniel Cayer, David Clark, Jay Kelley, Darrell Pierson

-  Forescout: Yejin Jang\*, Neal Lucier\*

-  Google Cloud: Tim Knudson\*

-  IBM: Nilesh Atal, Himanshu Gupta, Lakshmeesh Hegde, Sharath Math, Naveen Murthy, Nikhil Shah, Deepa Shetty, Harishkumar Somashekaraiah

-  IT Coalition: Aaron Cook, Vahid Esfahani\*, Jeff Laclair, Ebadullah Siddiqui\*, Musumani Woods\*

-  Ivanti: Patty Arcano, Jeffery Burton, Jay Dineshkumar

-  Lookout: Tyler Croak, Jeff Gilhool, Hashim Khan\*

-  Microsoft: Thomas Detzner, Ehud Itshaki, Janet Jones, Hemma Prafullchandra\*, Enrique Saggese, Sarah Young

-  MITRE: Eileen Division\*, Spike Dog, Sallie Edwards, Ayayidjin Gabiam, Jolene Loveless\*, Karri Meldorf, Kenneth Sandlin, Lauren Swan, Jessica Walton

-  NIST: Mike Bartock, Douglas Montgomery, Cherilyn Pascoe, Kevin Stine

-  Okta: Brian Dack, Sean Frazier, Naveed Mirza, Kelsey Nelson, Ron Wilson

-  PC Matic: Andy Tuch

-  Ping Identity: Ivan Anderson, Aubrey Turner

-  Radiant Logic: Bill Baz, Rusty Deaton, John Petrutiu, Lauren Selby

-  SailPoint: Peter Amaral, Jim Russell, Esteban Soto

-  Symantec by Broadcom: Eric Michael

-  Tenable: Jeremiah Stallcup

- Zimperium: Dan Butzer, Jim Kovach\*, Kern Smith

-  Zscaler: Jeremy James, Lisa Lorenzin\*, Matt Moulton, Patrick Perry

*\* Former employee; all work for this publication was done while at that organization*

Special thanks to all who reviewed and provided feedback on this document.

The collaborators who have or will participate in this project's current or upcoming builds submitted their capabilities in response to a notice in the Federal Register. Respondents with relevant capabilities or product components were invited to sign a Cooperative Research and Development Agreement (CRADA) with NIST, allowing them to participate in a consortium to build this example solution. We are working with the following list of collaborators. 

.. table:: Technology Partners/Collaborators

   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Appgate <https://www.appgate.com/>`__          | `IBM <https://www.ibm.com/>`__                                               | `Ping Identity <https://www.pingidentity.com/>`__                          |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `AWS <https://aws.amazon.com/>`__               | `Ivanti <https://www.ivanti.com/>`__                                         | `Radiant Logic <https://explore.radiantlogic.com/home>`__                  |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Broadcom (VMware) <https://www.vmware.com/>`__ | `Lookout <https://www.lookout.com/>`__                                       | `SailPoint <https://www.sailpoint.com/>`__                                 |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Cisco <https://www.cisco.com/>`__              | `Mandiant <https://www.mandiant.com/>`__                                     | `Symantec by Broadcom <https://www.broadcom.com/products/cybersecurity>`__ |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `DigiCert <https://www.digicert.com/>`__        | `Microsoft <https://www.microsoft.com/en-us/security/business/zero-trust>`__ | `Tenable <https://www.tenable.com/>`__                                     |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `F5 <https://www.f5.com/>`__                    | `Okta <https://www.okta.com/>`__                                             | `Trellix <https://www.trellix.com/en-us/index.html>`__                     |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Forescout <https://www.forescout.com/>`__      | `Palo Alto Networks <http://www.paloaltonetworks.com/>`__                    | `Zimperium <https://www.zimperium.com/>`__                                 |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | `Google Cloud <https://cloud.google.com/>`__    | `PC Matic <https://www.pcmatic.com/pro/>`__                                  | `Zscaler <https://www.zscaler.com/>`__                                     |
   +-------------------------------------------------+------------------------------------------------------------------------------+----------------------------------------------------------------------------+

Note that after the VMware products were implemented at NCCoE, VMware was acquired by Broadcom.

DOCUMENT CONVENTIONS
---------------------

The terms “shall” and “shall not” indicate requirements to be followed strictly to conform to the publication and from which no deviation is permitted. The terms “should” and “should not” indicate that among several possibilities, one is recommended as particularly suitable without mentioning or excluding others, or that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited. The terms “may” and “need not” indicate a course of action permissible within the limits of the publication. The terms “can” and “cannot” indicate a possibility and capability, whether material, physical, or causal.

CALL FOR PATENT CLAIMS
-----------------------

This public review includes a call for information on essential patent claims (claims whose use would be required for compliance with the guidance or requirements in this Information Technology Laboratory (ITL) draft publication). Such guidance and/or requirements may be directly stated in this ITL Publication or by reference to another publication. This call also includes disclosure, where known, of the existence of pending U.S. or foreign patent applications relating to this ITL draft publication and of any relevant unexpired U.S. or foreign patents.

ITL may require from the patent holder, or a party authorized to make assurances on its behalf, in written or electronic form, either:

a) assurance in the form of a general disclaimer to the effect that such party does not hold and does not currently intend holding any essential patent claim(s); or

b) assurance that a license to such essential patent claim(s) will be made available to applicants desiring to utilize the license for the purpose of complying with the guidance or requirements in this ITL draft publication either:

   1. under reasonable terms and conditions that are demonstrably free of any unfair discrimination; or 

   2. without compensation and under reasonable terms and conditions that are demonstrably free of any unfair discrimination. 

Such assurance shall indicate that the patent holder (or third party authorized to make assurances on its behalf) will include in any documents transferring ownership of patents subject to the assurance, provisions sufficient to ensure that the commitments in the assurance are binding on the transferee, and that the transferee will similarly include appropriate provisions in the event of future transfers with the goal of binding each successor-in-interest. 

The assurance shall also indicate that it is intended to be binding on successors-in-interest regardless of whether such provisions are included in the relevant transfer documents. 

Such statements should be addressed to: nccoe-zta-project@list.nist.gov

.. |This graphic contains the logos for NIST and the NCCoE.| image:: images/Figure1.png
   :alt: This graphic contains the logos for NIST and the NCCoE.
