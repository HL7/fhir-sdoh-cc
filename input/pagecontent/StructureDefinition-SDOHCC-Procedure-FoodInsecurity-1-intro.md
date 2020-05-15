## Profile design 
This profile is adapted from US Core Procedure. However, the value set bindings are not necessarily compliant. 

## Additional Guidance

This draft profile is included in this IG to give implementers an idea of how Gravity intends to develop this profile. As the Gravity project continues to develop content, this Procedure profile will also align with CarePlan and BSeR ServiceRequest profiles which will also be further developed in future versions of the Gravity IG.

The FHIR Procedure, ServiceRequest and CarePlan resources reference one another. Therefore, to support interoperability and analytics, similar approaches will be considered in the structured representation of food insecurity Procedure, ServiceRequests and CarePlan profiles. 

Although the Gravity Procedure, ServiceRequest and CarePlan profiles are still being developed, the diagram below shows potential relationships between Procedure, ServiceRequest and CarePlan (as well as the Conditions and/or Observations that they reference). 

CarePlan may reference ServiceRequest. Procedure may be based on ServiceRequest or CarePlan. The Procedure, CarePlan and ServiceRequest may reference Condition and/or Observation. 
The diagram below shows an example of some of possible relationships between QuestionnaireResponse, Observation, Condition, CarePlan, Goal, ServiceRequest, and Procedure.

The initial QuestionnaireResponse (1) results in Observations (2,3) which are evidence for a Condition (4) that is addressed by a CarePlan (5) and Goal (6) which lead to a ServiceRequest (7) and Procedure (8).


<table><tr><td><img src="procedure profile mindmap 20200423.png" /></td></tr></table>

 
The sections that follow provide additional guidance on 1) specific elements of this profile, and 2) efforts to align the profile with the following correlated Condition and Observation profiles:

* SDOHCC_Condition_FoodInsecurity_1
* SDOHCC_Observation_FoodInsecurity_1

### Procedure.code

This element references SDOHCC_ValueSet_FoodInsecurityIntervention_1. Currently, this value set contains the temporary SNOMED CT codes listed below. The current value set is only for the purpose of demonstrating a Food Insecurity Procedure profile for this IG. The members of this value set may change as the Gravity Project continues to develop content.


| Code                     | Display                                                                        |
|--------------------------|--------------------------------------------------------------------------------|
| sdohcc-sctt-151000243108 | Assistance with application for food program (procedure)                       |
| sdohcc-sctt-191000243103 | Assistance with application for food program and nutrition program (procedure) |
| sdohcc-sctt-181000243100 | Assistance with application for nutrition program (procedure)                  |
| sdohcc-sctt-171000243102 | Assistance with application for program (procedure)                            |
| sdohcc-sctt-141000243105 | Education about food program (procedure)                                       |
| sdohcc-sctt-221000243107 | Education about food program and nutrition program (procedure)                 |
| sdohcc-sctt-211000243104 | Education about nutrition program (procedure)                                  |
| sdohcc-sctt-201000243101 | Education about program (procedure)                                            |
| sdohcc-sctt-131000243104 | Evaluation of eligibility for food program (procedure)                         |
| sdohcc-sctt-251000243100 | Evaluation of eligibility for food program and nutrition program (procedure)   |
| sdohcc-sctt-241000243103 | Evaluation of eligibility for nutrition program (procedure)                    |
| sdohcc-sctt-231000243109 | Evaluation of eligibility for program (procedure)                              |
| sdohcc-sctt-161000243106 | Provision of food from food program (procedure)                                |
| sdohcc-sctt-261000243102 | Provision of food voucher (procedure)                                          |
| sdohcc-sctt-271000243106 | Provision of fresh fruit and vegetable voucher (procedure)                     |
| sdohcc-sctt-281000243108 | Provision of Home-Delivered Meals (procedure)                                  |
| sdohcc-sctt-291000243105 | Provision of Medically Tailored Meals (procedure)                              |
{:class="table table-bordered"}
{:.table-striped}

This value set may also be used ServiceRequest profiles for:

* ServiceRequest.code  

The consistent use of similar codes for a Procedure and a referenced ServiceRequest, that the Procedure is based on, will facilitate analytics and interoperability between Procedure and ServiceRequest.

*Example*:
* SDOHCC_Procedure_FoodInsecurity_1 modeled with:
	* Procedure.code = Assistance with application for food program 

May align with a service request that this procedure references (via Procedure.basedOn) such as:
* SDOHCC_ServiceRequest_FoodInsecurity_1 (yet to be developed) modeled with:
	* ServiceRequest.code = Assistance with application for food program

The codes in the SDOHCC_ValueSet_FoodInsecurityIntervention_1 are high level codes that do not specify specific food programs. Further refinement of the four codes currently in this value set to the level of granularity of specific national, state and local food programs will likely be excessive precoordination for the US Extension and some local codes would not even be appropriate for the US Extension. Gravity is exploring options to refine the current set of codes (for Procedure.code and ServiceRequest.code) so that food programs (national or local) can be represented in a consistent manner. The option under consideration includes a Food Program value set that can be used with a modified existing element of the ServiceRequest Resource.

### Procedure.basedOn

This element currently references http://hl7.org/fhir/StructureDefinition/ServiceRequest and http://hl7.org/fhir/StructureDefinition/CarePlan and http://hl7.org/fhir/StructureDefinition/CarePlan. As Gravity content development continues, this element may reference Gravity ServiceRequest and CarePlan profiles which are yet to be created.

### Procedure.category

Currently, this element references http://hl7.org/fhir/ValueSet/procedure-category. This example HL7 value set contains the SNOMED CT codes listed below. However, as Gravity content development continues, this value set may change to reflect the high-level intervention categories being proposed by Gravity.

| Code      | Display                         |
|-----------|---------------------------------|
| 24642003  | Psychiatry procedure or service |
| 409063005 | Counselling                     |
| 409073007 | Education                       |
| 387713003 | Surgical procedure              |
| 103693007 | Diagnostic procedure            |
| 46947000  | Chiropractic manipulation       |
| 410606002 | Social service procedure        |
{:class="table table-bordered"}
{:.table-striped}


### Procedure.reasonReference

This element can be used to justify why the procedure was performed. It can be used to reference SDOHCC_Condition_FoodInsecurity_1 and SDOHCC_Observation_FoodInsecurity_1. If needed, it can also reference other Condition, Observation, Procedure and DocumentReference profiles. 

### Procedure.reasonCode

This element can be used to provide a coded reason for why a procedure was performed. This element could have been used in this profile to reference SDOHCC_ValueSet_FoodInsecurity_1 (see members below) which was also used for Condition.code and Observation.code in SDOHCC_Condition_FoodInsecurity_1 and SDOHCC_Observation_FoodInsecurity_1. 

| Code                    | Display                            |
|-------------------------|------------------------------------|
| 733423003               | Food insecurity (finding)          |
| sdohcc-sctt-21000243108 | Mild food insecurity (finding)     |
| sdohcc-sctt-31000243105 | Moderate food insecurity (finding) |
| sdohcc-sctt-41000243104 | Severe food insecurity (finding)   |
{:class="table table-bordered"}
{:.table-striped}



However, this approach was deliberately avoided in this profile since Procedure.reasonCode overlaps significantly with Procedure.reasonReference and multiple approaches to representing the same information may negatively impact interoperability. Therefore, although this profile does not expressly prohibit this element, it is strongly recommended that Procedure.reasonReference be used to justify why the procedure was performed. 