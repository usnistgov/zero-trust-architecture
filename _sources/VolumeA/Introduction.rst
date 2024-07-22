Introduction to the Guide
==========================

.. include:: /_publication_note.rst

This guide outlines best practices for the implementation of zero trust architectures (ZTAs). These best practices were identified through a collaborative project at the National Cybersecurity Center of Ex-cellence (NCCoE). The NCCoE and its collaborators are using commercially available technology in lab environments to build interoperable, open standards-based ZTA implementations that align to the concepts and principles in `NIST Special Publication (SP) 800-207, Zero Trust Architecture <https://csrc.nist.gov/publications/detail/sp/800-207/final>`__. The implementations include ZTA approaches for enhanced identity governance (EIG), software-defined perimeter (SDP), microsegmentation, and secure access service edge (SASE). This project is developing, demonstrating, and documenting example ZTA solutions to help inform organizations as they develop plans to integrate ZTA into their enterprise environments. As the project progresses, this preliminary draft will be updated.

Audience
--------

The primary audience for this guide is medium and large enterprises. These enterprises are assumed to have trained operators and network administrators with the skills to deploy ZTA components and supporting components for data security, endpoint security, identity and access management, and security analytics. The enterprises are also assumed to have critical resources that require protection, some of which are located on-premises and others of which are in the cloud; and a requirement to provide partners, contractors, guests, and employees, both local and remote, with secure access to these critical resources. For a full list of assumptions for this project, see the :ref:`Assumptions` section.

While this guide supports `Executive Order 14028, Improving the Nation's Cybersecurity <https://www.federalregister.gov/documents/2021/05/17/2021-10460/improving-the-nations-cybersecurity>`__, which requires all federal agencies to develop plans to implement ZTA, it is not specific to federal agency audiences.

Readers of this guide should already be familiar with ZTA basics and the topics covered in `NIST Special Publication (SP) 800-207, Zero Trust Architecture <https://csrc.nist.gov/publications/detail/sp/800-207/final>`__.


Scope
-----

The scope of this guide is implementing a ZTA for a conventional, general-purpose enterprise IT infrastructure with support for traditional IT resources such as laptops, desktops, servers, mobile devices, and other systems with credentials. Discovery of resources, assets, communication flows, and other elements is also within scope. The focus is on using the ZTA to protect access to enterprise data, regardless of who initiates the access request (e.g., enterprise employees, partners, contractors, or corporate network guests), from where the access request is initiated (e.g., from the corporate network, a branch office, or the public internet), or where the resources are located, (e.g., on-premises or in the cloud). 

ZTAs for industrial control systems, operational technology (OT) environments, and Internet of Things (IoT) devices are explicitly out of scope for this project. Application of ZTA principles to these environments would be part of a separate project. For information on other related NCCoE projects, see `National Cybersecurity Center of Excellence, Internet of Things (IoT) <https://www.nccoe.nist.gov/iot>`__ and `National Cybersecurity Center of Excellence, Manufacturing <https://www.nccoe.nist.gov/manufacturing>`__. Addressing the risk and policy requirements of discovering and classifying data is also out of scope.


How to Use This Guide
----------------------

This guide provides technical details for 17 example ZTA implementations that were rigorously built in a lab at NCCoE. They were constructed according to the principles of zero trust and various zero trust architecture deployment approaches outlined in NIST SP 800-207, Zero Trust Architecture.

This version of the guide introduces a new manner of content delivery in two formats, one we refer to as the “High-Level Document in PDF Format” and the other as the “Full Document in Web Format.” The document in PDF format is meant to serve as an introductory reading with respect to insight into the project effort, as it provides a high-level summary of project goals, reference architecture, various ZTA implementations, and findings. The document in the web format provides in-depth details in terms of technologies leveraged, their specific integrations and configurations, and the use cases and scenarios demonstrated. The web format document also contains information on the implemented security capabilities and their mappings to the NIST Cybersecurity Framework (CSF) versions 1.1 and 2.0, NIST SP 800-53r5, and security measures outlined in “EO-Critical Software” under Executive Order (EO) 14028.

Readers are encouraged to begin by reading the document in PDF format (found at the `Main Project Page <https://www.nccoe.nist.gov/projects/implementing-zero-trust-architecture>`__) to perceive a high-level insight into the project. Then readers may drill down from that document into the deeper sections of the linked online document in web format to access in-depth information as needed. Therefore, this web content is organized as follows:

- :ref:`Project Overview` provides an overview about the NCCoE's “Implementing a Zero Trust Architecture” project from the viewpoints of motivation for the project, challenges in implementing ZTAs, project execution and implementation approach, as well as collaborating organizations and their contributions on the project.

- :ref:`Architecture and Builds` discusses the reference architectures considered for demonstrating various types of ZTA deployment approaches used across 17 implementations built. It also lists the technology products, along with out-of-the-box capabilities used in each build. Furthermore, this section provides information regarding the NCCoE lab's physical architecture platform used in implementing the builds.

- :ref:`Build Implementation Instructions` lists build instructions for 17 example implementations.

- :ref:`General Findings` explores the noteworthy findings and conclusions recorded throughout the demonstration of each ZTA deployment approach across 17 unique lab implementations.

- :ref:`Functional Demonstrations` discusses the essence of functional demonstrations scoped for the project from the viewpoints of demonstration methodology, use cases, and scenarios. It also lists the functional demonstration results for each implementation, both in summary and fully detailed formats.

- :ref:`Risk and Compliance Management` provides information regarding each build's implemented security capabilities and their mappings to the NIST CSF versions 1.1 and 2.0, NIST SP 800-53r5, and security measures outlined in “EO-Critical Software” under EO 14028.

- :ref:`Zero Trust Journey Takeaways` concludes that document by sharing a list of takeaways as recommended steps for a zero trust journey, intended for organizations that are considering ZTA adoption for their environments.

ZTA implementers and others seeking detailed information on designing and deploying ZTA solutions are encouraged to read all sections of the guide.

Cybersecurity professionals, compliance professionals, and others who are primarily concerned with how ZTA solutions relate to the CSF, NIST SP 800-53, and EO 14028 should focus on :ref:`Risk and Compliance Management`.

Anyone interested primarily in the lessons learned from the project should focus on the takeaways provided in :ref:`Zero Trust Journey Takeaways`.

Assumptions
-----------

This project is guided by the following assumptions:

-  `NIST SP 800-207, Zero Trust Architecture <https://csrc.nist.gov/publications/detail/sp/800-207/final>`__ is a definitive source of ZTA concepts and principles.

-  Enterprises that want to migrate gradually to an increasing use of ZTA concepts and principles in their network environments may desire to integrate ZTA with their legacy enterprise and cloud systems.

-  To prepare for a migration to ZTA, enterprises may want to inventory and prioritize all resources that require protection based on risk. They will also need to define policies that determine under what set of conditions subjects will be given access to each resource based on attributes of both the subject and the resource (e.g., location, type of authentication used, user role), as well as other variables such as day and time.

-  Enterprises should use a risk-based approach to set and prioritize milestones for their gradual adoption and integration of ZTA across their enterprise environment.

-  There is no single approach for migrating to ZTA that is best for all enterprises.

-  ZTA is a set of concepts and principles, not a set of technical specifications that can be complied with. Therefore, zero trust compliance is not an objective. Rather, the objective is continuous improvement of the access control processes and policies in accordance with the principles of ZTA.

-  Devices, applications, and other non-human entities can have different levels of capabilities:

-  Neither host-based firewalls nor host-based intrusion prevention systems (IPS) are mandatory components; they are, however, capabilities that can be added when a device is capable of supporting them.

-  Some limited functionality devices that are not able to host firewall, IPS, and other capabilities on their own may be associated with services that provide these capabilities for them. In this case, both the device and its supporting services can be considered the subject in the ZTA access interaction.

-  Some devices are bound to users (e.g., desktop, laptop, smartphone); other devices are not bound to users (e.g., kiosk endpoints, servers, applications, services). Both types of devices can be subjects and request access to enterprise resources.

-  ZTA components used in any given enterprise solution should be interoperable regardless of their vendor origin.
