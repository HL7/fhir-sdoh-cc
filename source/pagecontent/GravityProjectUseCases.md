[Previous Page - Gravity Project SDOH Coded Content](GravityProjectSDOHCodedContent.html)

The Gravity use cases focus on the functionality and interoperability required to allow an end-user to document, retrieve, send, exchange, and aggregate coded social risk data.  These use cases are high-level descriptions of the most value-add interactions between the various actors identified within [Patient Story 1](PatientStory1.html). 
	
This use case utilizes guidance provided for implementers in the FHIR Structured Data Capture Implementation Guide. This IG defines the profiles needed to constrain the FHIR Questionnaire and Questionnaire Response resources based on guidance supplied in the SDC IG and using coded SDOH content established by the Gravity Community for the Food Insecurity domain. 


| Use Case                                                                                                                                                         | Description |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| [Use Case 1: Document SDOH Data](UseCase1.html)     |   Document SDOH Data in Conjunction with the Patient Encounter          |
| [Use Case 2: Track SDOH Interventions](UseCase2.html)       |  Document and Track SDOH Related Interventions to Completion        |
| [Use Case 3: Aggregate SDOH Data ](UseCase3.html) | Gather and Aggregate SDOH Data for Uses Beyond the Point of Care            |
{:class="table table-bordered"}
{:.table-striped}

<br>
##  Use Case Actors 

The following system actors are established to accomplish the use cases covered in this IG:


| System Actor                                                                                                                                                      | Description of the Technical Role|
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| PMEHR (Practice Management/EHR)          | The system that initiates the task to request patients to be screened using a certain screening questionnaire.                                                                                                   |
| Screening App                            | The system that receives the screening request and then initiates screening of patient through the Patient App. This system sends completed questionnaire responses to the intended recipient.                   |
| Patient App                              | The system that enables a patient to complete a screening questionnaire.                                                                                                                                         |
| Clinical Data R/R (Registry/Repository)  | A system that requests clinical information which may include SDOH information also gathered during clinical care encounters.                                                                                    |
| Referral Initiator                       | A system that initiates a referral for services. This system also is a recipient of information returned from the Referral Recipient regarding a referral previously made.                                       |
| Services Directory                       | A system that offers a directory of available services and the endpoints for sharing information with each organization in the directory.                                                                        |
| Referral Recipient                       | A system that receives a referral for providing services to a patient. This system also sends information to the Referral Initiator system as activities associated with the referral are initiated or complete. |
| HIE                                      | A system that receives information from a PMEHR. This system also may request information from a PMEHR.                                                                                                          |
| Aggregator App                           | A system that receives or requests information from a PMEHR, aggregates/processes it, then outputs results and shares those results with another system.                                                         |
| Aggregate Data R/R (Registry/Repository) | A system that receives data that has been aggregated by another system.  <br>                                                                                                                                        |
{:class="table table-bordered"}
{:.table-striped}

Each system actor may play the technical role of a FHIR server or a FHIR client as it fulfills the data exchange interactions required to support this use case.

<br>
## Utilization of other FHIR IG's

Sharing SDOH content defined in this IG can be accomplished in a number of ways. The information flows described in this IG make use of mechanisms defined in other FHIR IGs.  The guidance included in this IG explains how to use those mechanisms (defined elsewhere) to accomplish the use cases covered in this guide. 

This IG utilizes this large body of prior work in order to accelerate alignment and interoperability throughout the healthcare IT ecosystem. It should however be noted that gaining a full appreciation for the material and technical mechanisms required to conform to this implementation guide requires significant investment of time and resources.    

The following FHIR IGs are utilized in this IG to support the three use cases:


| FHIR IG                                                                                                                                                  | Summary of Transactions Utilized |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| [Structured Data Capture (SDC)](http://hl7.org/fhir/us/sdc/index.html)     | This IG describes the data sharing mechanisms used to share, prepopulate, and submit data using structured forms.                                                                                                                                                              |
| [Clinical Data Exchange (CDex)](http://hl7.org/fhir/us/davinci-cdex/2019Jun)          | This IG describes the data sharing mechanisms to use RESTful API calls to query for and post FHIR resources, and to create and share tasks that request specific types of data or documents to be returned to the requesting system.                                   |
| [Bidirectional Service Exchange  (BSeR)](http://hl7.org/fhir/us/bser/index.html)  | This IG describes how to establish a task to execute a serviceRequest for a procedure to be performed within another organization and then a response to be returned to indicate the status of the requested intervention as well as the relevant request information. |
| [CCDA on FHIR](http://hl7.org/fhir/us/ccda/STU1)         | This IG describes how represent Consolidated CDA Templates for Clinical Notes (C-CDA) 2.1 templates using FHIR profiles.                                                                               |
{:class="table table-bordered"}
{:.table-striped}

 <br>

[Next Page - Use Case 1](UseCase1.html)