## Profile design 
This profile is adapted from US Core Procedure. However, the value set bindings are not necessarily compliant. 

## Additional Guidance

This is a draft profile that is included in this IG to give implementers an idea of how Gravity intends to develop this profile. As the Gravity project continues to develop content, this Procedure profile will also align with CarePlan and BSeR ServiceRequest profiles which will also be further developed in future versions of the Gravity IG.

The FHIR Procedure, ServiceRequest and CarePlan resources reference one another. Therefore, to support interoperability and analytics, similar approaches will be considered in the structured representation of food insecurity procedures, service requests and care plans. 

Although the Gravity Procedure, ServiceRequest and CarePlan profiles are still being developed, the diagram below shows potential relationships between Procedure, ServiceRequest and CarePlan (as well as the Conditions and/or Observations that they reference). 

 <table><tr><td><img src="Procedure Mindemap 2020.01.27.png" /></td></tr></table>


CarePlan may reference ServiceRequest. Procedure may be based on ServiceRequest or CarePlan. The Procedure, CarePlan and ServiceRequest may reference Condition and/or Observation.
 
The sections that follow provide additional guidance on 1) specific elements of this profile, and 2) efforts to align the profile with the following correlated Condition and Observation profiles:

* SDOHCC_Condition_FoodInsecurity_1
* SDOHCC_Observation_FoodInsecurity_1

### Procedure.code

This element references sdohcc_ValueSet_FoodInsecurityIntervention_1. Currently, this value set contains the SNOMED CT extension codes listed below. However, the current value set is only for the purpose of demonstrating a Food Insecurity Procedure for this IG. The members of this value set will increase as the Gravity Project continues to develop content.

| Code                     | Display                                                                               |
|--------------------------|---------------------------------------------------------------------------------------|
| sdohcc-sctt-111000243109 | Assistance with application for Supplemental Nutrition Assistance Program (procedure) |
| sdohcc-sctt-101000243107 | Evaluation of eligibility for Supplemental Nutrition Assistance Program (procedure)   |
{:class="table table-bordered"}
{:.table-striped}

This value set may also be used ServiceRequest profiles (which are yet to be developed) for:

* ServiceRequest.code  

The consistent use of similar codes for a Procedure and a referenced ServiceRequest, that the Procedure is based on, will facilitate analytics and interoperability between Procedure and ServiceRequest.

*Example*:
* SDOHCC_Procedure_FoodInsecurity_1 modeled with:
	* Procedure.code = Assistance with application for Supplemental Nutrition Assistance Program 

May align with a service request that this procedure references (via Procedure.basedOn) such as:
* SDOHCC_ServiceRequest_FoodInsecurity_1 (yet to be developed) modeled with:
	* ServiceRequest.code = Assistance with application for Supplemental Nutrition Assistance Program

### Procedure.basedOn

This element currently references http://hl7.org/fhir/StructureDefinition/ServiceRequest and http://hl7.org/fhir/StructureDefinition/CarePlan. As Gravity content development continues, this element may reference Gravity ServiceRequest and CarePlan profiles which are yet to be created.

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

This element can be used to justify why the procedure was performed. It can be used to reference SDOHCC_Condition_FoodInsecurity_1 and SDOHCC_Observation_FoodInsecurity_1. If needed, it can also reference other Condition, Observation, Procedure and 
DocumentReference profiles. 

### Procedure.reasonCode

This element can be used to provide a coded reason for why a procedure was performed. This element could have been used in this profile to reference sdohcc_ValueSet_FoodInsecurity_1 (see members below) which was also used for Condition.code and Observation.code in SDOHCC_Condition_FoodInsecurity_1 and SDOHCC_Observation_FoodInsecurity_1. 

| Code                    | Display                            |
|-------------------------|------------------------------------|
| 733423003               | Food insecurity (finding)          |
| sdohcc-sctt-21000243108 | Mild food insecurity (finding)     |
| sdohcc-sctt-31000243105 | Moderate food insecurity (finding) |
| sdohcc-sctt-41000243104 | Severe food insecurity (finding)   |
{:class="table table-bordered"}
{:.table-striped}

However, this approach was deliberately avoided in this profile since Procedure.reasonCode overlaps significantly with Procedure.reasonReference and multiple approaches to representing the same information may negatively impact interoperability. Therefore, although this profile does not expressly prohibit this element, it is strongly recommended that Procedure.reasonReference be used to justify why the procedure was performed. 
