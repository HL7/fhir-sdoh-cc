---
title: Use Case 1
layout: default
active: Use Case 1
---

[Previous Page](Use_Cases.html)


This use case is relevant to how coded SDOH data are captured in a health care system and how data are shared with other systems.  SDOH data are documented either as part of screening or assessment/ diagnosis activities and may be the reason for ordering care activities. 

Transactions: 
1.	Initiate Screening Task
2.	Return Screen
3.	Update Screening Task
4.	Communication Request
5.	Communication Response
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



<table><tr><td><img src="UC1 Gather and Share SDOH Data.png" /></td></tr></table>

<table><tr><td><img src="UC1 flow.png" /></td></tr></table>

<br>
## Use Case 1, Part 1
In Use Case 1, part 1, the Practice Management/EHR (PMEHR) system initiates the task to request screening information be collected from a patient.  The PMEHR system selects the screening form to be used and supplies patient information for the list of patients to be screened by a certain data. The Screening App system receives the task and executes a sub-task for each patient, notifying the person at their selected telecom address, prepopulating the questionnaireResponse, and collected the completed questionnaireResponse. The Patient App can be a mobile app that interacts as a client to the Screening App system, or it can be a simple e-mail client with browser capabilities to launch a link supplied to email.

As each questionnaireResponse is completed, the Screening App forwards the completed QuestionnaireResponse to the task requester (PMEHR). The PMEHR attaches the received QuestionnaireResponse to the appropriate patient record and allows the user to view the screening results that were received. As each sub-task is completed, the Screening App updates the progress for the larger task.  If the deadline for the Task runs out, or when all sub-tasks are completed, the Screening App notifies the system that initiated the task of the completion. The system that initiated the task can query the Screening App to gather statistics about the task that was completed (number of sub-tasks initiated, number completed successfully, number started by not completed, number not completed.)

<br>
## Use Case 1, Part 2
In Use Case 1 part 2, the PMEHR allows the user to gather other SDOH related information during the course of the clinical visit.  The practitioner can record a Clinical Assessment Observation, for example to indicate if Food Insecurity is present or absent, based on the screening information and other information gained during the patient encounter. The practitioner determines if the patient agrees there is a problem (condition) or risk of a problem regarding, for example Food Insecurity which the patient would like to see addressed.  The condition or risk can be added to the patients Problem List or noted as a Health Concern that should be tracked and addressed.  A care plan to address the condition or risk can be established by identifying a goal and the interventions that can be completed to make progress toward that goal. The Practitioner can document the planned interventions and any that are performed, or referred to be performed by a different organization. The interventions demonstrated initially in this use case are relevant to addressing SDOH Food Insecurity. At a subsequent visit, the practitioner can record if planned interventions had been completed based on responses received to earlier service requests, or based on information provided by the patient.  After each visit, the PMEHR system can provide a summary of the patient encounter or a snapshot of the care plan established to address the patients conditions/needs.  Outside systems can query for the care plan data or the encounter or care plan documents. Alternatively, outside systems can request to have this information sent to them, and the PMEHR system can respond to those requests, or send the data or document to a systems that has subscribed to the information, or has a business agreement to receive the information.  

<br>
## Use Case 1, Part 3
In Use Case 1, part 3, an outside systems queries for or requests information to be communicated from the clinical setting. Two options are supported. First, FHIR RESTful mechanisms can be used to query and retrieve the relevant data or documents.  Second, a Communication Request message can be used to request the data or encounter documents. The Communication message can be used to respond to a Communication Request (solicited communication). Alternatively, a Communication message can be used  to send the documents to a known recipient (unsolicited communication).



[Next Page](Use_Case_2.html)