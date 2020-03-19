[Previous Page - Security and Consent Considerations](SecurityandConsentConsiderations.html)

This section includes important terms, definitions, interpretations, assumptions and conformance requirements relevant to this guide.

### Conformance Verbs
The conformance verbs - **SHALL, SHOULD, MAY** - used in this guide are defined in [FHIR Conformance Rules](http://hl7.org/fhir/R4/conformance-rules.html).


<br>
### Must Support
For profiles defined in other IGs, the meaning of Must Support is established in the defining IG.
For profiles defined in this IG, Must Support means the following:
TBD

| Profile Name | Must Support Element |  Explanation |
|--------------|----------------|-------------|
|  SDOHCC_Procedure_FoodInsecurity_1            | status                |  preparation, in-progress, not-done, on-hold, stopped, completed, entered-in-error,  unknown<br>Binding: EventStatus (required)                            |
|  SDOHCC_Procedure_FoodInsecurity_1            | code              | 	Identification of the procedure<br>Binding: ProcedureCodes(SNOMEDCT) (example) Binding: sdohcc_ValueSet_FoodInsecurityIntervention_1 (preferred)                             |
|  SDOHCC_Procedure_FoodInsecurity_1            | subject               | Reference(US Core Patient Profile or Group)<br> Who the procedure was performed on                             |
|  SDOHCC_Procedure_FoodInsecurity_1            | performed[x]               | When the procedure was performed                             |
|  SDOHCC_Observation_FoodInsecurity_1            | status               |  Final <br>Binding: ObservationStatus (required) <br>Fixed Value: final                        |
|  SDOHCC_Observation_FoodInsecurity_1            | category               |   Classification of type of observation<br> Binding: ObservationCategoryCodes (preferred)                          |
|  SDOHCC_Observation_FoodInsecurity_1            | code               | 	Type of observation (code / type)<br>Binding: LOINCCodes (example)                          |
|  SDOHCC_Observation_FoodInsecurity_1            | subject               |  	Reference(US Core Patient Profile)<br> Who and/or what the observation is about                            |
|  SDOHCC_Observation_FoodInsecurity_1            | encounter               |  Reference(Encounter)	<br> Healthcare event during which this observation is made                            |
|  SDOHCC_Goal_FoodInsecurity_1            | lifecycleStatus               |  	proposed, planned, accepted,  active, on-hold, completed, cancelled, entered-in-error, rejected<br> Binding: GoalLifecycleStatus (required)                            |
|  SDOHCC_Goal_FoodInsecurity_1            | description              |  Code or text describing goal<br>Binding: SNOMEDCTClinicalFindings (example)                            |
|  SDOHCC_Goal_FoodInsecurity_1            | subject              |   	Reference(US Core Patient Profile)<br> Who this goal is intended for                           |
|  SDOHCC_Goal_FoodInsecurity_1            | target               |    Target outcome for the goal                          |
|  SDOHCC_Goal_FoodInsecurity_1            | due[x]                |   	Reach goal on or before                           |
|  SDOHCC_Condition_FoodInsecurity_1            | clinicalStatus               |   	active, recurrence, relapse, inactive, remission, resolved<br> Binding: ConditionClinicalStatusCodes (required)              |
|  SDOHCC_Condition_FoodInsecurity_1            | verificationStatus              |  	unconfirmed, provisional, differential, confirmed, refuted, entered-in-error<br>Binding: ConditionVerificationStatus (required)                       |
|  SDOHCC_Condition_FoodInsecurity_1            | category               | 	problem-list-item , encounter-diagnosis<br>Binding: ConditionCategoryCodes (extensible)                           |
|  SDOHCC_Condition_FoodInsecurity_1            | code               |   	Identification of the condition, problem or diagnosis<br> Binding: Condition/Problem/DiagnosisCodes (example)             |
|  SDOHCC_Condition_FoodInsecurity_1            | subject               | Reference(US Core Patient Profile)<br> Who has the condition?                             |
|  SDOHCC_Condition_FoodInsecurity_1            | encounter              | 	Reference(Encounter<br> Encounter created as part of                              |
|  SDOHCC_Condition_FoodInsecurity_1            | evidence               | BackboneElement<br>Supporting evidence                             |
{:class="table table-bordered"}
{:.table-striped}

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



[Next Page - Overview of Capability Statements](OverviewofCapabilityStatements.html)