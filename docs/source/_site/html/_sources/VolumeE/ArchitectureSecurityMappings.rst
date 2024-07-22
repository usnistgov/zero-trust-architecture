ZTA Security Mapping Context and Terminology
=================================================

.. include:: /_publication_note.rst

A *mapping* indicates that one concept is related to another concept. This publication introduces mappings for ZTA cybersecurity functions. They include both functions performed by the ZTA reference design's logical components (see :ref:`architecture and builds`) as well as functions performed by specific technologies used in the project's builds. The ZTA cybersecurity functions are based on the tenets of zero trust described in NIST SP 800-207. These tenets are a set of principles and strategies for system and security architects to use when designing, deploying, or upgrading systems and workflows. Architects and planners can use the zero trust tenets and the ZTA cybersecurity functions that are based on them when designing systems to help meet their cybersecurity requirements.

For this mapping, we have used the supportive relationship mapping style as defined in Section 4.2 of `NIST Internal Report (IR) 8477, Mapping Relationships Between Documentary Standards, Regulations, Frameworks, and Guidelines: Developing Cybersecurity and Privacy Concept Mappings <https://nvlpubs.nist.gov/nistpubs/ir/2024/NIST.IR.8477.pdf>`__.

Use Cases
~~~~~~~~~

Each set of mappings in this publication involves the ZTA cybersecurity functions and one of the following:

-  Subcategories from the `NIST Cybersecurity Framework (CSF 1.1) <https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04162018.pdf>`__ 

-  Subcategories from the `NIST Cybersecurity Framework 2.0 (CSF 2.0) <https://csrc.nist.gov/pubs/cswp/29/the-nist-cybersecurity-framework-20/ipd>`__

-  Security controls from `NIST SP 800-53r5 (Security and Privacy Controls for Information Systems and Organizations) <https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final>`__

-  Security measures defined in `Security Measures for “EO-Critical Software” Use Under Executive Order (EO) 14028 <https://www.nist.gov/itl/executive-order-improving-nations-cybersecurity/security-measures-eo-critical-software-use-2>`__ in support of `Executive Order (EO) 14028 <https://www.gsa.gov/technology/technology-products-services/it-security/executive-order-14028-improving-the-nations-cybersecurity>`__

All of the elements in these mappings—the ZTA cybersecurity functions, CSF Subcategories, SP 800-53 controls, and EO 14028 security measures—are concepts involving ways to reduce cybersecurity risk.

The mappings in this publication were developed to support two primary use cases. The mappings are not intended to be comprehensive, but rather to capture the strongest relationships involving ZTA cybersecurity functions.

1. **Why should organizations implement ZTA?** This use case identifies how implementing ZTA can support an organization with achieving CSF Subcategories, SP 800-53 controls, and EO 14028 security measures. This helps communicate to an organization's senior management that expending resources to implement ZTA can also aid in fulfilling other security requirements.

2. **How can organizations implement ZTA?** This use case identifies how an organization's existing implementations of CSF Subcategories, SP 800-53 controls, and EO 14028 security measures can help support a ZTA implementation. An organization wanting to implement ZTA might first assess its current security capabilities so that it can plan how to add missing capabilities and enhance existing capabilities in order to implement ZTA. Organizations can leverage their existing security investments and prioritize future security technology deployment to address the gaps.

These mappings are intended to be used by any organization that is interested in implementing ZTA or that has begun or completed a ZTA implementation.

Mapping Producers
~~~~~~~~~~~~~~~~~

The NCCoE ZTA project team performed the initial mapping between the cybersecurity functions performed by the ZTA reference design's logical components and the security characteristics in the cybersecurity documents, with input and feedback from the collaborators who have contributed technology to demonstrate ZTA capabilities. The collaborators performed the technology-specific mappings between the cybersecurity functions performed by collaborator products used in the project's ZTA builds and the security characteristics in the cybersecurity documents. In some cases, collaborators have not yet produced mappings for their products. These mappings are expected to be included in future versions of this document as collaborators develop them.

Mapping Approach
~~~~~~~~~~~~~~~~

The NCCoE asked each collaborator to indicate the mapping between the cybersecurity functions its technology components provide in one or more builds and the security characteristics in the cybersecurity documents. The logical components in the ZTA reference design were used as the organizing principle for enumerating collaborator products and mapping the cybersecurity functions of those products to security characteristics. Using this approach, the product-specific technology mappings are instantiations of the general reference design logical component mappings for each cybersecurity document.

Mapping Relationship Definitions 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In this publication, we use the following relationship types from NIST IR 8477 to describe how the functions in our ZTA reference design are related to the NIST reference documents. Note that the *Supports* relationship applies to use case 1 only and the *Is Supported B*\ y relationship applies to use case 2 only.

-  **Supports**: ZTA function X *supports* security control/Subcategory/measure Y when X can be applied alone or in combination with one or more other functions to achieve Y in whole or in part.

-  **Is Supported By**: ZTA function X *is supported by* security control/Subcategory/measure Y when Y can be applied alone or in combination with one or more other security controls/Subcategories/measures to achieve X in whole or in part.

-  **Equivalent**: ZTA function X is *equivalent* to security control/Subcategory/measure Y when X is the function that Y describes.

Each relationship of type *Supports* (A supports B) or *Is Supported By* (B is supported by A) has one of the following properties assigned to it:

-  **Example of**: The supporting concept A is one way (an *example*) of achieving the supported concept B in whole or in part. However, B could also be achieved without applying A.

-  **Integral to**: The supporting concept A is *integral* *to* and a component of the supported concept B. A must be applied as part of achieving B.

-  **Precedes**: The supporting concept A *precedes* the supported concept B when A must be achieved before applying B. In other words, A is a prerequisite for B.

When determining whether a ZTA function's support for a given CSF Subcategory, SP 800-53 control, or EO 14028 security measure is integral to that support versus an example of that support, we do not consider how that function may in general be used to support the Subcategory, control, security measure, or other item. Rather, we consider only how that function is intended to support that Subcategory, control, security measure, or other item within the context of our ZTA reference design.

Also, when determining whether a ZTA function is supported by a CSF Subcategory with the relationship property of *precedes*, we do not consider whether or not it is possible to apply the function without first achieving the Subcategory. Rather, we consider whether or not, according to our ZTA reference design, the Subcategory is to be achieved prior to applying that function.

There may be cases in which a conflict arises between zero trust principles and a compliance control. This conflict may be due to the control assuming a particular architecture or process in place. A control's description may use language to indicate a particular role, technology, or process that would not necessarily be relevant in a ZTA. For example, some controls may include references to “remote access” or “perimeter defenses”, which seem irrelevant in a ZTA. In an ideal ZTA, the network location should not matter (tenet 2 in SP 800-207). Likewise, while zero trust does acknowledge that perimeters exist, wide-scale perimeter defenses should not be the sole location where access policies are enforced. The mappings in this document do not ignore controls with descriptions that seem to conflict with ZTA. Instead, the mappings attempt to meet the spirit of the control while noting that a ZTA principle may go beyond the baseline requirement. 

Mapping Process 
^^^^^^^^^^^^^^^^

The process that the NCCoE used to create the mapping from the logical components of the ZTA reference design to the security characteristics of a given document was as follows:

1. Create a table that lists each of the logical components of the ZTA reference design in column 1.

2. Describe each logical component's cybersecurity function in column 2.

3. Map each cybersecurity function to each of the security characteristics in the document to which the function is most strongly related, and list each of these security characteristics on different sub-rows within column 3. Begin each security characteristic entry with an underlined keyword that describes the mapping's relationship type (e.g., *Supports*, *Is Supported By,* or *Equivalent).* After the keyword describing the relationship type, put in parentheses the underlined keyword(s) describing the relationship's property if applicable (e.g., *Example of*, *Integral to*, or *Precedes*).

4. In the fourth column, provide a brief explanation of why that relationship type and property apply to the mapping.

5. After completing the mapping table entries as described above for all the logical components in the reference design, examine the mapping in the other direction, i.e., starting with the security characteristics listed in the document and considering whether they have a relationship to the logical components' cybersecurity functions in the reference design. In other words, step through each of the security characteristics in the document and determine if there is some logical component in the reference design that has a strong relationship to that security characteristic. If so, add an entry for that security characteristic mapping to that logical component's row in the table. By examining the mapping in both directions in this manner, security characteristic mappings are less likely to be overlooked or omitted.

The NCCoE applied this mapping process separately for each reference document. None of the mappings are intended to be exhaustive; they all focus on the strongest relationships involving each cybersecurity function in order to help organizations prioritize their work. Mapping every possible relationship, no matter how tenuous, would create so many mappings that they would not have any value in prioritization.
