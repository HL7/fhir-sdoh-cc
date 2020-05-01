[Previous Page - SDOH Coded Content](SDOHCodedContent.html)

The Gravity use cases focus on the functionality and interoperability required to allow an end-user to document, retrieve, send, exchange, and aggregate coded social risk data.  These use cases are high-level descriptions of the most value-add interactions between the various actors identified within [Patient Story 1](PatientStory1.html). 
	
This use case utilizes guidance provided for implementers in the FHIR Structured Data Capture Implementation Guide. This IG defines the profiles needed to constrain the FHIR Questionnaire and Questionnaire Response resources based on guidance supplied in the SDC IG and using coded SDOH content established by the Gravity Community for the Food Insecurity domain. 


| Use Case                                                                                                                                                         | Description |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| [Use Case 1: Document SDOH Data](UseCase1.html)     |   Document SDOH Data in Conjunction with the Patient Encounter          |
| [Use Case 2: Track SDOH Interventions](UseCase2.html)       |  Document and Track SDOH Related Interventions to Completion        |
| [Use Case 3: Aggregate SDOH Data ](UseCase3.html) | Gather and Aggregate SDOH Data for Uses Beyond the Point of Care            |
{:class="table table-bordered"}
{:.table-striped}


###  Use Case System Actors 

The following system actors are established to accomplish the use cases covered in this IG:


| System Actor                                                                                                                                                      | Description of the Technical Role|
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| PMEHR (Practice Management/EHR)          | The system that initiates the task to request a list of patients to be screened using a certain screening questionnaire.    The PMEHR actor is assumed to either be grouped with an SDC Form Designer actor or to have access to Questionnaire Resources produced by other systems that are compliant with the SDC Form Designer and SDC Form Manager actors. The PMEHR uses the capability of a Form Designer technical actor to create a Questionnaire Resource that expresses a screening instrument. See the LHC Form Builder for an example: [https://lhcforms.nlm.nih.gov/](https://lhcforms.nlm.nih.gov/.). For screening instruments included in the Gravity Project Master List, use temporary codes included in the Master List where permanent codes are not yet available.[Link to Section of the IG about the Master List and Temporary Codes](AboutSDOH-CCMasterListTemporaryCodeSystemandTemporaryCodes.html). |
| Screening App / Patient App                           | The system that receives the request to initiate a patient screening task and request screening responses to be communicated back. This system communicates completed questionnaire responses to the screening task initiator.  The Screening App plays the role of the SDC Form Filler.  This actor is grouped with a Patient App actor which provides the ability for a patient to consent to sharing screening information with the intended recipient of the screening information.  The Patient App is responsible for rendering and managing the completed responses. The Patient App actor plays the role of the SDC Form Response Manager. |
| Clinical Data R/R (Registry/Repository)  | A system that requests clinical information which may include SDOH information also gathered during clinical care encounters. |
| Referral Initiator                       | A system that initiates a referral for services. This system also is a recipient of information returned from the Referral Recipient regarding a referral previously made.                                       |
| Services Directory                       | A system that offers a directory of available services and the endpoints for sharing information with each organization in the directory. |
| Referral Recipient                       | A system that receives a referral for providing services to a patient. This system also sends information to the Referral Initiator system as activities associated with the referral are initiated or complete. |
| HIE                                      | A system that receives information from a PMEHR. This system also may request information from a PMEHR.                                                                                                          |
| Aggregator App                           | A system that receives or requests information from a PMEHR, aggregates/processes it, then outputs results and shares those results with another system.                                                         |
| Aggregate Data R/R (Registry/Repository) | A system that receives data that has been aggregated by another system.                                                                                                                                          |
{:class="table table-bordered"}
{:.table-striped}

Each system actor may play the technical role of a FHIR server or a FHIR client as it fulfills the data exchange interactions required to support this use case.


## Utilization of other FHIR IG's

Sharing SDOH content defined in this IG can be accomplished in a number of ways. The information flows described in this IG make use of mechanisms defined in other FHIR IGs.  The guidance included in this IG explains how to use those mechanisms (defined elsewhere) to accomplish the use cases covered in this guide. 

This IG utilizes this large body of prior work in order to accelerate alignment and interoperability throughout the healthcare IT ecosystem. It should however be noted that gaining a full appreciation for the material and technical mechanisms required to conform to this implementation guide requires significant investment of time and resources.    

The following FHIR IGs are utilized in this IG to support the three use cases:


| FHIR IG                                                                                                                                                  | Summary of Utilized Technical Actors and Transactions |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| [Structured Data Capture (SDC)](http://hl7.org/fhir/us/sdc/index.html)     |  This IG describes the data sharing mechanisms used to share, prepopulate, and submit data using structured forms. It defines the following technical actors:<br>    * Form Designer <br> * Form Manager <br>  * Form Filler<br>   * Form Response Manager<br>   * Form Archiver                                                                                                                                                           |
| [Clinical Data Exchange (CDex)](http://hl7.org/fhir/us/davinci-cdex/2019Jun)          | This IG describes the data sharing mechanisms to use RESTful API calls to query for and post FHIR resources, and to create and share tasks that request specific types of data or documents to be returned to the requesting system.It defines the following technical actors:<br> * Clinical Data Document Sender  <br>* Clinical Data Document Recipient  <br> * Clinical Data Document Source   <br> * Clincial Data Document Requester   <br> * Information Source <br> * Information Requester|
| [Bidirectional Service Exchange  (BSeR)](http://hl7.org/fhir/us/bser/index.html)  | This IG describes how to establish a task to execute a serviceRequest for a procedure to be performed within another organization and then a response to be returned to indicate the status of the requested intervention as well as the relevant request information. It defines the following technical actors: <br>  * Task Initiator <br>  * Task Recpient  <br> * Referral Requester <br>  *  Referral Receiver|
| [CCDA on FHIR](http://hl7.org/fhir/us/ccda/STU1)  |This IG describes how represent Consolidated CDA Templates for Clinical Notes (C-CDA) 2.1 templates using FHIR profiles. It defines the following technical actors: <br>  *Clinical Document Creator <br>  * Clinical Document Consumer                                                            |
| [Application SMART on FHIR](http://www.hl7.org/fhir/smart-app-launch/) | The SMART App Launch Framework connects third-party applications to Electronic Health Record data, allowing apps to launch from inside or outside the user interface of an EHR system. The framework supports apps for use by clinicians, patients, and others via a PHR or Patient Portal or any FHIR system where a user can give permissions to launch an app. It provides a reliable, secure authorization protocol for a variety of app architectures, including apps that run on an end-users device as well as apps that run on a secure server. The Launch Framework supports the four uses cases defined for Phase 1 of the Argonaut Project: <br> * Patients apps that launch standalone <br> * Patient apps that launch from a portal <br> * Provider apps that launch standalone <br> * Provider apps that launch from a portal. <br> It defines the following technical actors: <br> * smart-on-fhir app<br>* smart-on-fhir server |
{:class="table table-bordered"}
{:.table-striped}

[Next Page - Use Case 1](UseCase1.html)