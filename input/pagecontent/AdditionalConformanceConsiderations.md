[Previous Page - Privacy, Security and Consent Considerations](PrivacySecurityandConsentConsiderations.html)

This section includes important terms, definitions, interpretations, assumptions and conformance requirements relevant to this guide.

### Conformance Verbs
The conformance verbs - **SHALL, SHOULD, MAY** - used in this guide are defined in [FHIR Conformance Rules](http://hl7.org/fhir/R4/conformance-rules.html).


<br>
### Must Support
For profiles defined in other IGs, the meaning of Must Support is established in the defining IG.
For profiles defined in this IG, Must Support will conform with [US Core definition](https://build.fhir.org/ig/HL7/US-Core-R4/general-guidance.html#must-support).


<br>
#### Missing Data
If the source system does not have data for a *Must Support* data element with minimum cardinality = 0, the data element is omitted from the resource. If the source system does not have data for a required data element (in other words, where the minimum cardinality is > 0), follow guidance defined in the core FHIR specification and summarized in the [US Core IG](http://hl7.org/fhir/us/core/general-guidance.html#missing-data). 

<br>
### U.S. Core Data for Interoperability and 2015 Edition Common Clinical Data Set
The US Core Profiles were originally designed to meet the 2015 Edition certification criterion for Patient Selection 170.315(g)(7), and Application Access - Data Category Request 170.315(g)(8). They were created for each item in the [2015 Edition Common Clinical Data Set (CCDS)](https://www.healthit.gov/sites/default/files/ccds_reference_document_v1_1.pdf). The 3.1.0 version of the US Core Profiles IG includes new requirements from the latest proposed ONC [U.S. Core Data for Interoperability (USCDI)](https://www.healthit.gov/topic/laws-regulation-and-policy/notice-proposed-rulemaking-improve-interoperability-health) and includes all the [API Resource Collection in Health (ARCH)](https://www.healthit.gov/isa/api-resource-collection-health-arch) resources.

<br>

#### Conformance to US Core Profiles
Any actor acting as a FHIR Server in this IG SHALL:
*	Be able to populate all profile data elements that have a minimum cardinality >= 1 and/or flagged as Must Support as defined by that profiles StructureDefinition.
*	Conform to the US Core Server Capability Statement expectations for that profiles type.

Any actor acting a FHIR Client in this IG SHALL: 
*	Be able to process and retain all profile data elements that have a minimum cardinality >= 1 and/or flagged as Must Support as defined by that profiles StructureDefinition.
*	Conform to the US Core Client Capability Statement expectations for that profiles type.

#### US Core Profile Exceptions
US Core Profiles were designed for use cases where a range of RESTful search requirements were needed which are not applicable for use cases in scope for SDOH-CC. The table below summarizes differences between the search requirements of SDOH-CC and the search requirements of US Core.



[Next Page - Overview of Capability Statements](OverviewofCapabilityStatements.html)