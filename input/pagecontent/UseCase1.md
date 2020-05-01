[Previous Page - Use Cases, System and Technical Actors](UseCasesSystemandTechnicalActors.html)


This use case is relevant to how coded SDOH data are captured in a health care system and how data are shared with other systems.  SDOH data are documented either as part of screening or assessment/ diagnosis activities and may be the reason for ordering care activities. 

<br><br>

<table><tr><td><img src="UC1 actors color.png" /></td></tr></table>

**Practice Management/EHR (PMEHR)** - gathers and shares SDOH information in a clinical care setting.

Capability                   | FHIR API resources and operations | 
|----------------------------------|----------------|
| Initiate a screening task for a list of patients and a specific screening tool to be used [1]. Receive individual patient consent and screening information as it becomes available [2]. Associate received information from a patient's chart. Recieve a confirmation when a screening task has been completed [3].     | [base]/$process-message <br> [Bundle MessageHeader](https://www.hl7.org/fhir/messageheader.html)  <br> [Task](https://www.hl7.org/fhir/task.html) <br> [List](https://www.hl7.org/fhir/list.html) <br> [US Core Patient](https://www.hl7.org/fhir/us/core/StructureDefinition-us-core-patient.html)<br> [SDC Questionnaire](http://hl7.org/fhir/us/sdc/sdc-questionnaire.html) <br> [SDC Questionnaire Response](http://hl7.org/fhir/us/sdc/sdc-questionnaireresponse.html)  <br> [Observation](https://www.hl7.org/fhir/observation.html)        |
| Enable review of received screening information associated with a patient's medical record. Enable the clinician to document an SDOH clinical finding. Permit clinicians to document an SDOH issue as a health concern or condition to be tracked on the patient's problem list. Include a structured SDOH goal in the patient's documentation to facilitate outcome tracking. Docment planned or completed activites to address SDOH needs using structured data. | [SDOHCC_Observation_FoodInsecurity_1](StructureDefinition-SDOHCC-Observation-FoodInsecurity-1.html) <br>[SDOHCC_Condition_FoodInsecurity_1](StructureDefinition-SDOHCC-Condition-FoodInsecurity-1.html   ) <br>[SDOHCC_Goal_FoodInsecurity_1](StructureDefinition-SDOHCC-Goal-FoodInsecurity-1.html) <br>[SDOHCC_Procedure_FoodInsecurity_1](StructureDefinition-SDOHCC-Procedure-FoodInsecurity-1.html) <br>|
|Receive a communication requesting SDOH information gathered during a patient encounter [4]. Initiate a communication with the requested for SDOH informaiton as structured data or using a standard visit summary [5]. | [CDEX Communication Request](http://hl7.org/implement/standards/fhir/us/davinci-cdex/2019Jun/StructureDefinition-cdex-communicationrequest.html) <br> [CDEX Communication](http://hl7.org/implement/standards/fhir/us/davinci-cdex/2019Jun/StructureDefinition-cdex-communication.html) <br> [base]/Composition/[id]/$document <br> or [C-CDA document](http://www.hl7.org/fhir/us/ccda/StructureDefinition-CCDA-on-FHIR-Continuity-of-Care-Document.html)|
{:class="table table-bordered"}
{:.table-striped}

**Screening App Actor** - receives and executes the screening task by interacting with the patient and PMEHR.


| Capability                   | FHIR API resources and operations | 
|----------------------------------|----------------|
| Upon receiving request [1], initiate the requesed screening task for the list of patients, using the supplied questionnaire. <br>Interface with the user to gather the needed data sharing consent and collect the screening responses and compute the screening interpretation.     |     [Task](https://www.hl7.org/fhir/task.html), [List](https://www.hl7.org/fhir/list.html),  [US Core Patient](https://www.hl7.org/fhir/us/core/StructureDefinition-us-core-patient.html) <br>[SDC Questionnaire](http://hl7.org/fhir/us/sdc/sdc-questionnaire.html)        |   
| Return the consent and screening information to the screening task initiator [2]. If the patient does not consent to share screening information, return SDOH screening indicating patient preference not to participate [2.1]         |  [Consent](https://www.hl7.org/fhir/consent.html), [SDC QuestionnaireResponse](http://hl7.org/fhir/us/sdc/sdc-questionnaireresponse.html), <br> [Observation](https://www.hl7.org/fhir/observation.html)             |   
| Update the task initiator when the task is completed [3]           |   [Task](https://www.hl7.org/fhir/task.html)              |   
{:class="table table-bordered"}
{:.table-striped}

<br><br>

**Clinical R/R Actor** - any actor needing to request SDOH information gathered during a clinical encounter to support treatment, payment, or operations. 

| Capability                   | FHIR API resources and operations | 
|----------------------------------|----------------|
|   Initiate a communication request for SDOH information gathered during a clinical encounter [4.1], [4.2], [4.3]        |    [CDEX CommunicationRequest](http://hl7.org/implement/standards/fhir/us/davinci-cdex/2019Jun/StructureDefinition-cdex-communicationrequest.html)            |              
| Receive information that was requested [5.1], [5.2], [5.3].                 | [CDEX Communication](https://build.fhir.org/ig/HL7/davinci-ecdx/branches/master/StructureDefinition-cdex-communication-definitions.html)
{:class="table table-bordered"}
{:.table-striped}


<br><br>


| Human Actor                      | Business Actor | System Actor  | Technical Role    |
|----------------------------------|----------------|---------------|-------------------|
| (Not specific to a System Actor) |                |               |                   |
| Patient                          | n/a            | Screening App | Initiate Screening Task Recipient, <br> Return Screen Initiator, <br>Screening Task Update Initiator |
| Clinical Staff Member            | PCP Practice   | EHR           | Initiate Screening Task Initiator,<br> Return Screen Recipient,<br> Screening Task Update Recipient,<br>Communication Request Receiver,<br> Communication Sender     |
| Care Coordinator,<br>Researcher,<br> Population Health Worker           | Payor,<br> Research Org,<br> HIE  | Clinical Data R-R           | Communication Request Requestor,<br> Communication Recipient  |
{:class="table table-bordered"}
{:.table-striped}
<br>

### Use Case 1 Messages and Transactions
This Actor Transaction diagram shows the technical system roles and information exchange transaction for Use Case 1:

| Transaction | Example |
|----------------------------------|----------------|
|1.	Initiate Screening Task<br>|    BundleMessage-NewTask-Example-1   |
| 2.	Return Screen<br> |      |
|		2.1.	Consent provided by patient<br>|  BundleMessage_ReturnScreen_Example_1      |
|	 	2.2.	Consent not provided by patient <br>| BundleMessage_ReturnScreen_Example_1      |
| 3.	Update Screening Task<br>| BundleMessage_TaskUpdate_Example_1      |
| 4.	Communication Request<br>|       |
|			4.1.	CDA document request<br>|  BundleTransaction_CDEX_Request_Example_1     |
|			4.2.	FHIR composition resource request<br>|   BundleTransaction_CDEX_Request_Example_2    |
|			4.3.	FHIR Screening questionnaire request<br>|  BundleTransaction_CDEX_Request_Example_3     |
|5.	Communication Response<br>|      |
|			5.1.	CDA document response<br>|  BundleTransaction_CDEX_Response_Example_4      |
|			5.2.	FHIR composition resource response<br>| BundleTransaction_CDEX_Response_Example_5      |
|			5.3.	FHIR Screening questionnaire response<br>|  BundleTransaction_CDEX_Response_Example_6.xml     |
| Questionnaire Resource Example | 	Questionnaire_Hunger_Vital_ Sign_Example_1 |
{:class="table table-bordered"}
{:.table-striped}


<br><br>
### Use Case 1 Actors
**Practice Management/EHR (PMEHR)** - gathers and shares SDOH information in a clinical care setting.  

| Capability                   | FHIR API resources and operations |
|----------------------------------|----------------|
| Initiate a screening task for a a list of patients and a specivic screening tool to be used [1].  Recieve individual patient consent and screening information as it becomes available [2]. Associate received information from a patient's chart. Recieve a confirmation when a screening task has been completed [3].        |  [base]/$process-message <br> [Bundle MessageHeader](https://www.hl7.org/fhir/messageheader.html), [Task](https://www.hl7.org/fhir/task.html) <br> [List](https://www.hl7.org/fhir/list.html), [US Core Patient](https://www.hl7.org/fhir/us/core/StructureDefinition-us-core-patient.html) <br>[SDC Questionnaire](http://hl7.org/fhir/us/sdc/sdc-questionnaire.html) <br>[SDC QuestionnaireResponse](http://hl7.org/fhir/us/sdc/sdc-questionnaireresponse.html), [Observation](https://www.hl7.org/fhir/observation.html) |
| Enable review of received screening information associated with a patient's medical record. Enable the clinician to document an SDOH clinical finding. Permit clinicians to document an SDOH issue as a health concern or condition to be tracked on the patient's problem list. Include a structured SDOH goal in the patient's documentation to facilitate outcome tracking. Document planned or completed activities to address SDOH needs using structured data     |    [SDOHCC_Observation_FoodInsecurity_1](StructureDefinition-SDOHCC-Observation-FoodInsecurity-1.html) <br> [SDOHCC_Condition_FoodInsecurity_1](StructureDefinition-SDOHCC-Condition-FoodInsecurity-1.html)<br> [SDOHCC_Goal_FoodInsecurity_1](StructureDefinition-SDOHCC-Goal-FoodInsecurity-1.html) <br> [SDOHCC_Procedure_FoodInsecurity_1](StructureDefinition-SDOHCC-Procedure-FoodInsecurity-1.html)              |
 | Receive a communication requesting SDOH information gathered during a patient encounter [4]. Initiate a communication with the requested for SDOH information as structured data or using a standard visit summary [5]. |  [CDEX Communication Request](http://hl7.org/implement/standards/fhir/us/davinci-cdex/2019Jun/StructureDefinition-cdex-communicationrequest.html)  <br> [CDEX Communication](http://hl7.org/implement/standards/fhir/us/davinci-cdex/2019Jun/StructureDefinition-cdex-communication.html)<br>[C-CDA on FHIR Composition](http://www.hl7.org/fhir/us/ccda/StructureDefinition-CCDA-on-FHIR-Continuity-of-Care-Document.html) <br> [base]/Composition/[id]/$document <br> Or [C-CDA document](http://www.hl7.org/implement/standards/product_brief.cfm?product_id=492) |
{:class="table table-bordered"}
{:.table-striped}

<br><br>

### Use Case 1 Elements

| Use Case Element            | Initiate Screening Task  |
|-----------------------------|---|
| **Assumptions**                 |  Practice determines appropriate questions to address patient consent to share SDOH information and offers options to gather patient preferences regarding whether the patient: <br>  does not want to answer the survey; <br>would prefer to answer the survey on paper at the appointment;<br> would prefer to discuss these questions with a care coordinator at the appointment; <br>would prefer to discuss these questions with his or her provider at the appointment; and,<br> needs assistance to translate or interpret the questions.  <br>Patient demographic data is up to date. |
| **Preconditions**               |  A list of patients to be screened is known, and the screening questions and answers to be used is expressed in a Questionnaire Resource. The Consent languaged has been agreed. |
| **Transaction #  1**             |  Initiate Screening Task |
| **Message Content (Payload)**   | A message bundle that includes a Screening Task to be initiated with the list of patients and the Questionnaire  |
| **Post Condition**              |  The screening task is initiated and each patient in the list has been asked to consent to share SDOH questionnaire results, and to  take the questionnaire.|
| **Alternate Flow (Paper Form)** | The person my choose not to consent to share the information and the screening is not performed.  |
{:class="table table-bordered"}
{:.table-striped}
<br>



| Use Case Element            | Return Screen  |
|-----------------------------|---|
| **Assumptions**                 | The person is who they puport to be -- they have a known and trusted identity.  |
| **Preconditions**               | Patient has completed the consent and the Questionnaire.  |
| **Transaction #  2**             |  The QuestionnaireResponse and the Consent are returned together as a Composition to the organization that initiated the Screening Request. |
| **Message Content (Payload)**   | Message Bundle, Composition, Consent, QuestionnaireResponse, Questionnaire  |
| **Post Condition**              | The recipient system recieves the screening information and indexes it into it's document repository.   |
| **Alternate Flow (Paper Form)** | The message indicates the person did not consent to sharing their SDOH information and the screening was not performed.  |
{:class="table table-bordered"}
{:.table-striped}
<br>


| Use Case Element            | Update Screening Task  |
|-----------------------------|---|
| **Assumptions**                 |   |
| **Preconditions**               |   |
| **Transaction #  3**             |  The message indicates a new status for the Screening Task |
| **Message Content (Payload)**   |  The Screening Task with an updated status to Completed. |
| **Post Condition**              |  The status of the screening task on the requesting system has been updated to completed. |
| **Alternate Flow (Paper Form)** |   |
{:class="table table-bordered"}
{:.table-striped}

<br>



| Use Case Element            | Communication Request  |
|-----------------------------|---|
| **Assumptions**                 |   |
| **Preconditions**               |  Requester system initiates a request for a specific type of document or for a type of data. |
| **Transaction #  4**             | **Communication Request** <br>Requester system (Clinical R-R) sends Communication Request to the PMEHR  |
| **Message Content (Payload)**   | Communication Request  |
| **Post Condition**              |  PMEHR receives the CommunicationRequest.. |
| **Alternate Flow (Paper Form)** |    |
{:class="table table-bordered"}
{:.table-striped}


<br>


| Use Case Element            | Communication Response  |
|-----------------------------|---|
| **Assumptions**                 |   |
| **Preconditions**               |  The system receiving the CommunicationRequest keeps track of document available for sharing using the DocumentReference Resource. |
| **Transaction #  5**             | **Communication Response** <br>PMEHR sends the requested documents to the Recipient(s) indicated in the request. |
| **Message Content (Payload)**   | Payload depends on what the request requested.  |
| **Post Condition**              |  The recipient system(s) receive the requested documents or data. |
| **Alternate Flow (Paper Form)** |  |
{:class="table table-bordered"}
{:.table-striped}



<br>


<table><tr><td><img src="UC1 flow.png" /></td></tr></table>

<br>
### Use Case 1, Part 1
In Use Case 1, part 1, the Practice Management/EHR (PMEHR) system initiates the task to request screening information be collected from a patient.  The PMEHR system selects the screening form to be used and supplies patient information for the list of patients to be screened by a certain data. The Screening App system receives the task and executes a sub-task for each patient, notifying the person at their selected telecom address, prepopulating the questionnaireResponse, and collected the completed questionnaireResponse. The Patient App can be a mobile app that interacts as a client to the Screening App system, or it can be a simple e-mail client with browser capabilities to launch a link supplied to email.

As each questionnaireResponse is completed, the Screening App forwards the completed QuestionnaireResponse to the task requester (PMEHR). The PMEHR attaches the received QuestionnaireResponse to the appropriate patient record and allows the user to view the screening results that were received. As each sub-task is completed, the Screening App updates the progress for the larger task.  If the deadline for the Task runs out, or when all sub-tasks are completed, the Screening App notifies the system that initiated the task of the completion. The system that initiated the task can query the Screening App to gather statistics about the task that was completed (number of sub-tasks initiated, number completed successfully, number started by not completed, number not completed.)

<br>
### Use Case 1, Part 2
In Use Case 1 part 2, the PMEHR allows the user to gather other SDOH related information during the course of the clinical visit.  The practitioner can record a Clinical Assessment Observation, for example to indicate if Food Insecurity is present or absent, based on the screening information and other information gained during the patient encounter. The practitioner determines if the patient agrees there is a problem (condition) or risk of a problem regarding, for example Food Insecurity which the patient would like to see addressed.  The condition or risk can be added to the patients Problem List or noted as a Health Concern that should be tracked and addressed.  A care plan to address the condition or risk can be established by identifying a goal and the interventions that can be completed to make progress toward that goal. The Practitioner can document the planned interventions and any that are performed, or referred to be performed by a different organization. The interventions demonstrated initially in this use case are relevant to addressing SDOH Food Insecurity. At a subsequent visit, the practitioner can record if planned interventions had been completed based on responses received to earlier service requests, or based on information provided by the patient.  After each visit, the PMEHR system can provide a summary of the patient encounter or a snapshot of the care plan established to address the patients conditions/needs.  Outside systems can query for the care plan data or the encounter or care plan documents. Alternatively, outside systems can request to have this information sent to them, and the PMEHR system can respond to those requests, or send the data or document to a systems that has subscribed to the information, or has a business agreement to receive the information.  

<br>
### Use Case 1, Part 3
In Use Case 1, part 3, an outside systems queries for or requests information to be communicated from the clinical setting. Two options are supported. First, FHIR RESTful mechanisms can be used to query and retrieve the relevant data or documents.  Second, a Communication Request message can be used to request the data or encounter documents. The Communication message can be used to respond to a Communication Request (solicited communication). Alternatively, a Communication message can be used  to send the documents to a known recipient (unsolicited communication).

### Data Representation Reference Information

#### Structured Document Clinical Note Types

Use this information to request clinical note(s) (DocumentReference or Composition, DiagnosticReport, CarePlan).

The Pull (Solicited Request) information exchange mechanism enables Information Request Sender to request a general type of document and permits the Information Request Recipient to respond with any of the more specific document types defined to be in that note type category.

The Pull (GET) information exchange mechanism requires the Information Client to use specific codes when querying the Information Source. 

Reference the various types of clinical note types via the concepts in the associated value sets.

| Clinical Note Type          | General Code (LOINC) | Specific Types Value Set Name    | Value Set Reference (available in VSAC)    |
|-----------------------------|----------------------|----------------------------------|--------------------------------------------|
| History and Physical Note   | 34117-2              | HPDocumentType                   | 2.16.840.1.113883.1.11.20.22               |
| Progress Note               | 11506-3              | ProgressNoteDocumentTypeCode     | 2.16.840.1.113883.11.20.8.1                |
| Referral Note               | 57133-1              | ReferralDocumentType             | 2.16.840.1.113883.1.11.20.2.3              |
| Consultation Note           | 11488-4              | ConsultDocumentType              | 2.16.840.1.113883.11.20.9.31               |
| Procedure Note              | 28570-0              | ProcedureNoteDocumentTypeCodes   | 2.16.840.1.113883.11.20.6.1                |
| Care Plan                   | 18776-5              | Care Plan Document Type          | 2.16.840.1.113762.1.4.1099.10              |
| Continuity of Care Document | 34133-9              | N/A                              | N/A                                        |
{:class="table table-bordered"}
{:.table-striped}

#### Helpful Communication Request Recipient Organization Endpoint format codes (this in only relevant for the Request (Solicited Communication) Information Exchange mechanism.


|       Profile                                    |    Format Code                           |    Media Type    |    When to use                                                           |   |   |
|--------------------------------------------------|------------------------------------------|------------------|--------------------------------------------------------------------------|---|---|
| HL7 C-CDA R2.1 using a structured body           | urn:hl7-org:sdwg:ccda-structuredBody:2.1 | text/xml         | To receive document bundles that contain C-CDA R2.1 structured documents |   |   |
| HL7 C-CDA R2.1 using a non-structured body       | urn:hl7-org:sdwg:ccda-nonXMLBody:2.1     | text/xml         | binary resource                                                          |   |   |
| HL7 C-CDA-On-FHIR using a structured Composition |                                          | text/xml         |                                                                          |   |   |
| HL7 C-CDA-On-FHIR using a structured Composition |                                          | text/json        |                                                                          |   |   |
| HL7 C-CDA-On-FHIR using a non-structured body    |                                          | text/xml         |                                                                          |   |   |
| HL7 C-CDA-On-FHIR using a non-structured body    |                                          | text/json        |                                                                          |   |   |
{:class="table table-bordered"}
{:.table-striped}


#### Sample Structured Data Codes

Note: there are many search parameters and other details for the FHIR search API.  Refer to the FHIR specification for [details](http://hl7.org/fhir/search.html).

|    Data Element Description                                                                                    | C-CDA Entry Template                       | C-CDA data coding                                                                           | FHIR Resource |
|----------------------------------------------------------------------------------------------------------------|--------------------------------------------|---------------------------------------------------------------------------------------------|---------------|
| **What are the A1C results after 2018-01-01 for this patient?**                                                    |                                            |                                                                                             |               |
| FHIR Query String:                                                                                             |                                            |                                                                                             |               |
| Observation?patient=[the patient's id]&date=ge2018-01-01&code=4548-4                                           |                                            |                                                                                             |               |
| Test Result: A1C                                                                                               |                                            | 4548-4 Hemoglobin A1c/Hemoglobin.total in Blood (LOINC)                                     |               |
| **What are the patient's vital sign measurements in reverse chronological order?**                                 |                                            |                                                                                             |               |
| FHIR Query String:                                                                                             |                                            |                                                                                             |               |
| Observation?_sort=-date&patient=[this patient's id]&category=vital-signs                                       |                                            |                                                                                             |               |
| Vital Sign: weight                                                                                             | Vital Sign Observation                     | 29463-7 Weight (LOINC)                                                                      |               |
| Vital Sign: height                                                                                             | Vital Sign Observation                     | 8302-2 Height (LOINC)                                                                       |               |
| Vital Sign: BMI                                                                                                | Vital Sign Observation                     | 39156-5 Body Mass Index (BMI)                                                               |               |
| **What are the patient's active conditions?**                                                                      |                                            |                                                                                             |               |
| FHIR Query String:                                                                                             |                                            |                                                                                             |               |
| Condition?patient=[this patient's id]&clinicalstatus=active                                                    |                                            |                                                                                             |               |
| Condition/Diagnosis: Type II Diabetes                                                                          | Problem Concern                            | E11 (ICD-10) Type 2 diabetes mellitus                                                       |               |
| Condition/diagnosis: Amputated left foot                                                                       | Problem Concern                            | Z89.432 Acquired absence left foot (ICD-10)                                                 | Condition     |
| Condition/diagnosis: Hypertension                                                                              | Problem Concern                            | I10 (ICD-10)                                                                                | Condition     |
| **What is the patient's current smoking status?**                                                                  |                                            |                                                                                             |               |
| Observation?patient=1032702&code=72166-2&_sort=-date&_count=1                                                  |                                            |                                                                                             |               |
| Social History: Smoking Status                                                                                 | Social History Observation                 | 72166-2 Tobacco Smoking Status (LOINC)                                                      |               |
| **What medications is the patient taking?**                                                                        |                                            |                                                                                             |               |
| MedicationStatement?patient=[this patient's id]                                                                |                                            |                                                                                             |               |
|                                                                                                                | Medication Activity                        |                                                                                             |               |
| Medication:                                                                                                    | Medication Information                     | 316151 Lisinopril 10 MG (RxNorm)                                                            |               |
|                                                                                                                | Indication                                 | 38341003 | Hypertensive disorder,systemic arterial (disorder) (SCT)                         |               |
| **What devices does the patient have?**                                                                            |                                            |                                                                                             |               |
| Device?patient=[this patient's id]                                                                             |                                            |                                                                                             |               |
| Device: Wheel chair                                                                                            | Non-medicinal Supply/product instance      | 58938008 | Wheelchair device (physical object) | (SCT)                                      |               |
| Device: Crutches                                                                                               | Non-medicinal Supply                       | 363753007 | Crutches (physical object) | (SCT)                                              |               |
| Device: Prosthetic left foot                                                                                   | Non-medicinal Supply                       | 449694008 | Implantation of prosthetic device of lower leg (procedure) | (SCT)              |               |
| **What procedures has the patient had?**                                                                      |                                            |                                                                                             |               |
| Procedure?patient=[this patient's id]                                                                          |                                            |                                                                                             |               |
| Procedures                                                                                                     | Diabetic Retinal Exam                      | 67028 Diabetic Retinal Exam (CPT)                                                           |               |
| Procedures:                                                                                                    | Procedure activity Procedure               | 46786008 | Fitting of prosthesis or prosthetic device of leg below knee (procedure) | (SCT) |               |
| Procedures:                                                                                                    |                                            | Implantation of prosthetic device of lower leg (CPT)                                        |               |
| **Who is the patient's Primary Care Provider?**                                                                    |                                            |                                                                                             |               |
| Patient/this patient's id (note: parse the generalPractitioner field)                                          |                                            |                                                                                             |               |
| Primary Care Provider for Patient                                                                              | Performer or ResponsibleParty functionCode | 446050000 Primary Care Provider (SCT)                                                       |               |
|                                                                                                                |                                            | or PCP Primary Care Provider (ParticipationFunction)                                        |               |
| **What type of health insurance does the patient have?**                                                           |                                            |                                                                                             |               |
| Coverage?patient=[this patient's id]&status=active (note: parse coverage resource to get the fields you need.) |                                            |                                                                                             |               |
| Coverage: Health Insurance type                                                                                | Coverage Activity / Policy Activity        | Need help                                                                                   |               |
{:class="table table-bordered"}
{:.table-striped}

[Next Page - Use Case 2](UseCase2.html)