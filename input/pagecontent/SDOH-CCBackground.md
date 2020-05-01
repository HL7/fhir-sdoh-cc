[Previous Page - Gravity Project Background](GravityProjectBackground.html)

###  SDOH Domain Scope

The Gravity Project focus on defining coded content to support three priority social domains, **food insecurity**, **housing instability and homelessness**, and **transportation access**.

<table><tr><td><img src="three SDOH domains.png" /></td></tr></table>


<br>
####  Out of SDOH Domain Scope

The Gravity Project will not focus on evaluating, testing, or harmonizing existing social risk screening tools and instruments, nor will it identify social risk data elements that do not directly support one of the three priority social domains previously listed in the Scope Statement. This project also will not validate or provide incentives for implementation of the identified SDOH data elements.

<br>
### Conceptual Framework

Coded SDOH content is captured across four core health care activities: screening, assessment/diagnosis, goal setting, and interventions. The conceptual framework illustrated below shows how these activities form a cycle of care. Over time, as additional screening and assessment is performed, a patients progress toward care goals can be tracked and measured.

<table><tr><td><img src="Gravity Project Conceptual Framework.png" /></td></tr></table>



<br>
### Data Modeling Framework
The figure below was derived from the HL7 Patient Care WG Domain Analysis model for Care Plan information. It informs the design of the  FHIR Resources used in this IG.

<table><tr><td><img src="Data Modeling Framework.png" /></td></tr></table>

The relationships between the various types of information are supported by the designs developed for the resources. The diagram below shows the data model for the assessment observation, condition (diagnosis), and goal (patient centered goal). The semantics designed for the profiled resources support the envisioned cycles of assessment, diagnosis, and goal setting. The mind map illustration represents profiles developed in this IG for the FHIR Observation, Condition, and Goal Resources. It shows instances of profiled Resources that would be used over time as part of an iterative care process. 

<table><tr><td><img src="SDOHCC FHIR IG Mindmap 1 smaller.png" /></td></tr></table>


The data modeling includes additional considerations specified using FHIR Path expressions.

| Profile                                                         | Additional Constraints                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Observation Profile 1 Example 1 | Food insecurity observation that is the result of clinical  assessment based on information collected in the screening  questionnaire and other information gathered during the  encounter. <br> 1) Allows an Observation that specifies Food insecurity absent (aka Food Security), Mild food insecurity, Moderate food insecurity, Severe Food insecurity, or Food insecurity, unknown. <br> 2) xpath rules could specify xpath that must either  Observation.valueCodableConcept or  Observation.dataAbsentReason, but not both, must be provided. |
| Condition                        | Allows a Condition that specifies Mild food insecurity, Moderate  food insecurity, Severe Food insecurity.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Goal                             | Patient-centered goal documenting the desired outcome  of planned interventions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Observation Profile 1 Example 2 | Food insecurity observation that is the result of a post-goal,  post-intervention evaluation/assessment.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
{:class="table table-bordered"}
{:.table-striped}

<br>
#### Role of the FHIR CarePlan Resource

The FHIR CarePlan Resource is at a Maturity Level 2 and a number of issues remain to be resolved before the SDOHCC_CarePlan_FoodInsecurity profile(s) can be considered. This includes comparing SDOHCC requirements to the profiling of the CarePlan Resource done in the US Core IG.

The diagram below is intended to show Resources that reference or are referenced by CarePlan as the patient progresses from:

* Screening Questionnaire Responses that lead to Screening Result Observation(s) and Assessment Observantion(s) <br> to <br>
* Conditions(s) - based on Observation(s)<br> to <br>
* CarePlan and Goal(s) - based on Condition(s)<br> to <br>
* Service Request(s) and Procedures(s) - based on CarePlan and Goal(s)<br> which result in <br>
* Subsequent Screening Result Observation(s) or Assessment Observations -> Subsequent Conditions(s) -> Revised Goal(s) -> updated or new Service Request(s) and Procedures(s)

Each time the resources referenced by the CarePlan are updated/versioned, the information that would be retrieved if the CarePlan resource was retrieved will be updated. A CarePlan resource functions as a "dynamic resource" countinuously pointing to the "current" view of the patient's plan. Snapshots of the CarePlan resource may need to be instantiated as a document to be preserved at a specific point in time to facilitate signature and sharing of the information with other parties as points in time. 

<table><tr><td><img src="care plan mindmap 20200408.png" /></td></tr></table>

Once this profile is created, additional guidance will be provided on 
1. how to use the specific elements of this resource
2. efforts to align the profile with the following correlated profiles:
	* SDOHCC_Observation_FoodInsecurity_1
	* SDOHCC_Condition_FoodInsecurtiy_1
	* SDOHCC_Goal_FoodInsecurity_1
	* SDOHCC_Procedure_FoodInsecurity_1
	* BSeR_ReferralServiceRequest
	* US Core CarePlan

[Next Page - Personas and Patient Stories](PersonasandPatientStories.html)