---
title: Profiles used in this IG
layout: default
active: Profiles used in this IG
---

[Previous Page](Use_Case_3.html)



## SDOH Profiles Defined in this IG


| Name                         | Description | Additional Technical Notes | 
|---------------------------------------------------------------------------------|-------------|------------|
| [SDOHCC_Observation_FoodInsecurity_1](StructureDefinition-SDOHCC-Observation-FoodInsecurity-1.html)  |  This profile supports SDOHCC data elements that focus on the Food Insecurity domain. <br>The profile constrains Observations related to: Food insecurity. <br> It allows the creation of Observations of: Food insecurity unknown, Food insecurity absent (aka Food security present), Food insecurity present, Mild food insecurity present, Moderate food insecurity present, and Severe food insecurity present.                                                         | [Notes for SDOHCC_Observation_FoodInsecurity_1](Notes_for_SDOHCC_Observation_FoodInsecurity_1.html)|
| [SDOHCC_Condition_FoodInsecurity_1](StructureDefinition-SDOHCC-Condition-FoodInsecurity-1.html)       | This profile supports SDOHCC Project data elements that focus on the Food Insecurity domain. <br>The profile constrains Conditions related to: Food insecurity, Mild food insecurity, Moderate food insecurity, or Severe food insecurity.   | [Notes for SDOHCC_Condition_FoodInsecurity_1](Notes_for_SDOHCC_Condition_FoodInsecurity_1.html) | 
| [SDOHCC_Goal_FoodInsecurity_1](StructureDefinition-SDOHCC-Goal-FoodInsecurity-1.html) |This profile supports SDOHCC Project data elements that focus on the Food Insecurity domain. <br>The profile constrains Goals related to: Food Security.   | [Notes for SDOHCC_Goal_FoodInsecurity_1](Notes_for_SDOHCC_Goal_FoodInsecurity_1.html) |
| [SDOHCC_Procedure_FoodInsecurity_1](StructureDefinition-SDOHCC-Procedure-FoodInsecurity-1.html)| This profile supports Gravity Project data elements that focus on the Food Insecurity domain. <br> The profile constrains Procedures related to: Food Insecurity. | [Notes for SDOHCC_Procedure_FoodInsecurity](Notes_for_SDOHCC_Procedure_FoodInsecurity_1.html) |
{:class="table table-bordered"}
{:.table-striped}

<br>
## Profiles Reused from US Core

US Core Implementation Guide (v3.1.0: STU3 Update) based on FHIR R4. 

The US Core Implementation Guide is based on FHIR Version R4 and defines the minimum conformance requirements for accessing patient data. The Argonaut pilot implementations, ONC 2015 Edition Common Clinical Data Set (CCDS), and the latest proposed ONC U.S. Core Data for Interoperability (USCDI) provided the requirements for this guide. The prior Argonaut search and vocabulary requirements, based on FHIR DSTU2, are updated in this guide to support FHIR Version R4. These profiles are the foundation for future US Realm FHIR implementation guides. In addition to Argonaut, they are used by DAF-Research, QI-Core, and CIMI. Under the guidance of HL7 and the HL7 US Realm Steering Committee, the content will expand in future versions to meet the needs specific to the US Realm.

These requirements were originally developed, balloted, and published in FHIR DSTU2 as part of the Office of the National Coordinator for Health Information Technology (ONC) sponsored Data Access Framework (DAF) project. For more information on how DAF became US Core see the [US Core Change Notes](https://www.hl7.org/fhir/us/core/change-notes.html).
* [US Core Practitioner](http://hl7.org/fhir/us/core/StructureDefinition-us-core-practitioner.html)
* [US Core PractitionerRole](http://hl7.org/fhir/us/core/StructureDefinition-us-core-practitionerrole.html)
* [US Core Organization](http://hl7.org/fhir/us/core/StructureDefinition-us-core-organization.html)
* [US Core Location](http://hl7.org/fhir/us/core/StructureDefinition-us-core-location.html)
* [US Core Patient](http://hl7.org/fhir/us/core/StructureDefinition-us-core-patient.html)
* [US Core Condition Profile](http://hl7.org/fhir/us/core/StructureDefinition-us-core-condition.html)
* [US Core Goal Profile](http://hl7.org/fhir/us/core/StructureDefinition-us-core-goal.html)
* [US Core Procedure Profile](http://hl7.org/fhir/us/core/StructureDefinition-us-core-procedure.html)
* [US Core Encounter](http://hl7.org/fhir/us/core/StructureDefinition-us-core-encounter.html)

<br>
## Profiles Reused from SDC

Structured Data Capture FHIR IG (v2.5.0: STU 3 Ballot 1). The current version is 2.0.0 based on FHIR v3.5.0.
* [SDC Questionaire](http://hl7.org/fhir/uv/sdc/2018Sep/sdc-questionnaire.html) Collect observational data
* [SDC Questionnaire Response](http://hl7.org/fhir/uv/sdc/2018Sep/sdc-questionnaireresponse.html) Collect observational data
* [SDC ValueSet](http://hl7.org/fhir/uv/sdc/2018Sep/sdc-valueset.html) 
* [SDC Code System](http://hl7.org/fhir/uv/sdc/2018Sep/sdc-codesystem.html)
* [SDC Data Element](http://hl7.org/fhir/us/sdc/sdc-dataelement.html)
* [EndPoint extension](http://hl7.org/fhir/uv/sdc/2018Sep/sdc-questionnaire-endpoint.html)
* [SDC Populatable Questionnaire](http://hl7.org/fhir/uv/sdc/2018Sep/sdc-questionnaire-populate.html)	Questionnaire with information required for auto or pre population

<br>
## Profiles Reused from CDex

* [CommunicationRequest](http://hl7.org/fhir/us/davinci-cdex/2019Jun/StructureDefinition-cdex-communicationrequest.html)
* [Communication](http://hl7.org/fhir/us/davinci-cdex/2019Jun/StructureDefinition-cdex-communication.html)

<br>
## Profiles Reused from BSeR

Bidirectional Services eReferrals (BSeR) FHIR IG (v0.1.0: STU 1 Ballot 1) based on FHIR vSTU3.
* Task
* MessageHeader
* ServiceRequest
* Consent



[Next Page](Notes_for_SDOHCC_Condition_FoodInsecurity_1.html)