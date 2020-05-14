### Overview

|IG Characteristic  |     Value |
|------------------------------------------------------|--------------------------------------------|
|**FHIR Version:** |    FHIR R4 |
|**IG Realm:** |    US |
|**IG Type:** |    STU |
|**Exchange Methods:** |    RESTful Query, Messages, Transactions, Documents, Tasks |
|**IG Dependencies:** |    The SDOH-CC IG utilizes and adopts guidance developed in several other FHIR&reg; Implementation Guides. |
{:.table-striped}




|IG Dependencies         |  IG Code         | Version                      |
|----------------------------------|-------------------------|---------------|
| HL7 FHIR US Core               |  [US Core](http://hl7.org/fhir/us/core/STU3.1)                | Version 3.1.0     |
| Structured Data Capture                         |   [SDC](http://hl7.org/fhir/uv/sdc/2019May)        | Version 2.7.0                     |
| C-CDA on FHIR R4     |     [C-CDA on FHIR](http://hl7.org/fhir/us/ccda/STU1)           | Version 1.0.0              |
| DaVinci Clinical Data exchange            | [CDex](http://hl7.org/fhir/us/davinci-cdex/2019Jun) | Version 0.1.0              |
| Bidirectional Services eReferrals                      |  [BSer](http://hl7.org/fhir/us/bser) | Version 1.0.0 |
{:.table-striped}




###  Purpose

This HL7&reg; IG defines FHIR R4 profiles, extensions and value sets needed to exchange SDOH content defined by the Gravity Project. It defines how to represent coded content used to support the following care activities: screening, clinical assessment/diagnosis, goal setting, and the planning and performing of interventions. It addresses the need to gather SDOH information in the context of clinical encounters and describes how to share SDOH information and other relevant information with outside organizations for the purpose of coordinating services and support to address SDOH related needs. It also demonstrates how to share clinical data to support secondary purposes such as population health, quality, and research. It supports the following use cases:
1.	Document SDOH data in conjunction with the patient encounter,
2.	Document and track SDOH related interventions to completion,
3.	Gather and aggregate SDOH data for uses beyond the point of care (e.g. public health, population health, quality measurement, risk adjustment, quality improvement, and research.)


### How to Use This Guide

A FHIR IG address the needs of multiple audiences. It provides technical artifacts that assist programmers when implementing standards-based FHIR application program interfaces (APIs) for specific purposes. It provides instructive material that explains how FHIR is used to accomplish specific uses cases. It also provides general information that helps business analysts and technology decision-makers understand the use cases and benefits associated with acheiving specific data exchange capabilities. A FHIR IG is as much a business planning tool as it is an educational resource and a technical specification.

However, one caveat must be clear: this FHIR IG and the other FHIR IG's it depends upon are at low levels of maturity.  Changes to the specification can be major and may happen rapidly as Gravity Project incorporates the full scope of SDOH content domains. Plan accordingly and budget for exploration and potential rework.  For example, the solutions tested at one Connectathon may need to be substantially revised before testing at the next Connectathon. Early engagement in FHIR IG development and sustained collaboration will create the opportunity to have greater impact on the design of these emerging implementer standards.


#### For implementers interested in getting started with FHIR
Read the IG to:
* Understand the design of FHIR APIs to inform your product management, clinical workflow planning, business planning, and to inform expectations about what will be possible in the future.
* Discover an additional/alternate API you could begin offering to give your customer a path toward utilizing standards
* Become more informed about the national direction for inclusion of SDOH information in clinical care
* Consider opportunities to utilize standards-based data exchange sooner rather than later
* Plan to utilize standards-based data exchange as you consider technology solutions, look at making future investments that can improve patient care 
* Imagine the role of standards-based data exchange as you advocate for yourself and others

Participate in Connectathon testing to:
* Engage your R&D team to develop new capabilities with FHIR
* Inform management about product development activities to prepare for FHIR APIs
* Accelerate product development efforts
* Adjust your product roadmap to adjust for more rapid support of FHIR APIs to the HL7 FHIR standard
* Learn how FHIR is being used to rapidly enable needed data exchange and speed adoption of new capabilities
* Introduce product management and technical resources in your development team to the HL7 FHIR standard
* Introduce clinical and technical resources in your practice about the HL7 FHIR standard
* Gain awareness of available and emerging technology solutions that offer services which would reduce administrative burden for your organization and offer other benefits for your organization
* Gain experience with data exchange made possible by the HL7 FHIR standard
* Help shape how FHIR is being used to rapidly enable needed data exchange and speed adoption of new capabilities
* Contribute patient and caregiver perspectives and requirements for the kinds of services and capabilities that would benefit individuals and families

Use the IG to:
* Find customers interested in moving toward standards-based data exchange
* Inform solution purchasing decisions and clarify/simplify your interoperability requirements
* Inform workflow design and information sharing possibilities
* Inform solution development or purchase decisions
* Determine when to start offering a FHIR API to your customers
* Bring standardized data solutions to market faster and avoid future product rework costs
* Avoid investment in products that are not aligned with where the industry and the nation are headed
* Plan to utilize standards-based data exchange as you look at making future investments
* Influence the development of products that are not aligned with where the industry and the nation are headed, **and** where individuals want health data exchange to go
* Advocate personally for information sharing that integrates into everyday life and improves the experience of care for individuals and families
<br>

#### For implementers interested in using existing standards to make incremental progress in the planned direction
* Apply the information exchange patterns and workflows developed in the IG to shape the flow of information available through the use of existing standards
* Use standardized content for FHIR messages and data payloads to populate the message content carried by existing transport standards
<br>

#### For implementers who are not yet sharing data using standards-based data exchange
* Develop APIs that support planned directions to make it easier to access and share information that will need to be exchanged
* Begin aligning internal data concepts with standard data elements, adopting the standard definitions and constraining values to adopted answer sets
* Be diligent about understanding definitions associated with codes and make accurate mappings between local concepts and standard codes

<br>

### Notes to Reviewers and Balloters

Feedback on V0.0.4 of the IG should be sent to gravityproject@emiadvisors.net between April 30, 2020 and  May 31, 2020. 

* Review of version 0.0.4 of the IG is intended to gather high-level comments about the overall approach to the Implementation Guide and its positioning in terms of supporting the use cases defined for the Gravity Project. It also is aimed at identifying omissions that impact the quality of the IG. It still contains IG Build errors and reviewers should be aware of imperfections that still need to be addressed in version 0.0.5. The list of the approved errors that can be disregarded for this version can be found on [Confluence Gravity FHIR IG](https://confluence.hl7.org/pages/viewpage.action?pageId=66922000#GravityFHIRIG-ApprovedSDOHCCFHIRIGErrorsandWarnings).

* Temporary Codes used in this IG will be replaced with permanent codes when they become available and before the IG is published as a Standard for Trial Use (STU).

* In v0.0.5 valueSet bindings for condition.code and procedure.code will be modified to conform with US Core profiles. 

* In v0.0.5, when an SDOHCC profile references a resource that has been profiled in US Core, the refrenced resource will conform to the US Core profile.

* For some of the examples, there are known issues/errors with the way IG Publisher is rendering the narrative view of the content. Nonetheless, the narrative view is included (as is) because it is useful to facilitate a general understanding of the profile and may be helpful for generating feedback about how to improve the way narrative is rendered. 

* Message, Transaction, and Workflow Content documentation is incomplete and some of the needed examples have not yet been loaded.

* Capability Statements have been sketched into the document but have not yet been developed and included in the IG.

* Minimal data provenance guidance has been included. This will be improved in v0.0.5.

* Minimal privacy, security and consent guidance has been included. This will be improved in v0.0.5.

* Within the profiles there is a known problem with some bound valueSets appearing as "unbound"

* Some examples do not come from US Core because they did not validate in Trifolia. Therefore, we used examples from HL7. In v0.0.5 examples will be based on US Core.

* Some example ids do not conform to the current naming convention and will be updated in v0.0.5.

  


### History of Document Changes

| Number         | Description                                                                                                                                                   |
|---------------|----------------------------------------------------------------------------------------------------|
| 27         | New chapter on how examples relate       |
| 26         | Additional profile       |
| 25         | Updates to naming conventions       |
| 24         | How to create screening instruments, use of temporary codes       |
| 23         | Expanded the ValueSet for coded Procedure      |
| 22          | Improved naming conventions      |
| 21           | Updated profiles and additional artifacts      |
| 20          |  New profiles and artifacts for v.0.0.4     |
| 19           | Resolved errors related to broken links      |
| 18           | Updates to authors and acknowledgements      |
| 17           | Additional guidance for form builder and temporary codes       |
| 16            | Created Must Support table |
| 15            | Updated Overview of Data Sharing Methods |
| 14            | Updated Security and Consent Considerations |
| 13            | Updated Notes to Reviewers and Balloters  |
| 12            | Added page Practical Guidance for All Audiences |
| 11            | Revisions to profiles and examples |
| 10            | Updates to dependencies to this IG |
| 9            | Updates to Use Case 1 and 2 tables |
| 8            | Change Placeholder Codes to "Temporary codes" and re-work code system naming |
| 7             | Update to How to Read this Guide to align with new publication algorithm                               |
| 6             | Update to Naming Conventions for Implementation Guide Artifacts                                  |
| 5             | Update to Placeholder Code System page                                   |
| 4             | Added notes for Profiles                                       |
| 3             | Updates to Use Case 1                                       |
| 2             | Update naming conventions to sdohcc                                        |
| 1             | Redesign chapters                                         |
{:class="table table-bordered"}
{:.table-striped}


### Acknowledgements
*This section is still under development*

We would like to thank the Agency for Healthcare Research and Quality (AHRQ), SIREN UCSF, UV Larner and Yale Nursing for their support for developing this IG and all [Gravity Project sponsors](https://confluence.hl7.org/display/GRAV/Gravity+Project+Sponsors) for their contributions to make rapid progress on the standardization of social determinants of health data.

Reserve this area to included acknowledgements for the people and organizations involved in developing and maintaining this Implementation Guide.

There may also be some required copyright acknowledgements for certain Code Systems or other acknowledgements required by HL7 and FHIR.

The Placeholder Code Creation process was originally developed for Elimu profiles and SMART app development. It was modified in the context of creating this IG to make it more broadly applicable.


|**Name**         | **Organization**                                        |
|--------------------------|--------------------------------------------|
| Lisa Nelson           | MaxMD                                         |
| Matt Elrod        | MaxMD                                   |
| Corey Smith        | AMA                                   |
| Monique van Berkum       | AMA                                 |
| Jim Shalaby        |   Elimu                                |
| Matt Menning        |  AMA                                  |
| Mohit Saigal        | AMA                                   |
| Becky Gradl          | Academy of Nutrition and Dietetics                                 |
| Sarah DeSilvey        |  Larner College of Medicine at the University of Vermont, SIREN                                  |
| Donna Pertel         |  Academy of Nutrition and Dietetics                                  |
| Evelyn Gallego        |  EMI Advisors, LLC                                  |
| Linda Hyde        |   EMI Advisors, LLC                                 |
| Lynette Elliott| EMI Advisors, LLC |
| Rob Hausam |        |
| Cheng Liu | MaxMD|
| Natasha Kreisle | MaxMD|
{:class="table table-bordered"}
{:.table-striped}



### Authors

<table>
<thead>
<tr>
<th>Name</th>
<th>Email</th>
</tr>
</thead>
<tbody>
<tr>
<td>HL7 International - Patient Care WG</td>
<td></td>
</tr>
<tr>
<td>HL7 International - Patient Care</td>
<td></td>
</tr>
</tbody>
</table>


