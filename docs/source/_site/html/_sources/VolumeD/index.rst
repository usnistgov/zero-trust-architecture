Functional Demonstrations
=====================================================

.. include:: /_publication_note.rst

.. toctree::
   :maxdepth: 1
   :titlesonly:
   :glob:
   :hidden:
   
   FunctionalLabDemonstration.rst
   UseCaseA.rst
   UseCaseB.rst
   UseCaseC.rst
   UseCaseD.rst
   UseCaseE.rst
   UseCaseF.rst
   UseCaseG.rst
   UseCaseH.rst
   FunctionalDemonstrationResultSummaries.rst
   results/index.rst


This section is intended to assist the lab operator through the set of ZTA scenarios and use cases that have been defined for demonstration in this project. To reduce the number of iterations, some potential demonstrations have been omitted because they are not sufficiently different from another demonstration that has been included. For example, if the requester's access to a resource is blocked due to a noncompliant on-premises resource, then it is sufficient to demonstrate this once with an on-premises-to-on-premises request; this demonstration does not need to be repeated making the request from a branch office or remote access location because the location of the requester in this demonstration is irrelevant. The lab demonstration playbook is not exhaustive for all enterprise operations, and it does not capture all possible demonstration cases.

Several demonstration scenarios listed here are presented as a maximal approach to zero trust. This includes assumptions about user intent that may not always be determined in an actual operational setting. For example, subjects may be classified as compromised in some way so that all access requests are part of an intentional attack and not mistaken queries from valid (uncompromised) subjects. As such, some demonstrations may seem extreme for most enterprise operations. This is only to demonstrate the most extreme cases, as a less severe response such as logging and/or sending an alert to a human administrator is also possible.

This collection of demonstration scenarios is still under development. Additional scenarios and use cases may be included in the next version as the implementations evolve and add capabilities.
