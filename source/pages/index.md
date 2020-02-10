---
title: Implementation Guide Home Page
layout: default
active: home
---

<!-- { :.no_toc } -->

<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}

<!-- end TOC -->

### Description




|**IG Realm:**         | **US**                                        |
|--------------------------|--------------------------------------------|
|**IG Type:**             | **STU**                                         |
|**Exchange Methods:**     | **RESTful Query, Messaging, Documents, Tasks** |
{:class="table table-bordered"}
{:.table-striped}

<br>

**IG Dependencies**
This IG utilizes and adopts guidance developed in several other FHIR&reg; Implementation Guides. 

Additional information regarding the conformance to guidance developed in these IGs is available in the Overview of Data Sharing Transactions section and Capability Statement section of this IG.  


| Implementation Guide Name                                                               |  IG Code         | Version                      |
|-----------------------------------------------------------------|-------------------------------------------|-------------------------------------|
| HL7 FHIR US Core               |  [US Core]( http://hl7.org/fhir/us/core/2019Sep/)                | Version 3.1.0 - FHIR R4      |
| Structured Data Capture                         |   [SDC]( http://build.fhir.org/ig/HL7/sdc/)        | V3.0.2                       |
| C-CDA on FHIR R4     |     [C-CDA on FHIR](https://build.fhir.org/ig/HL7/ccda-on-fhir-r4/)           | Version (1.1.0)              |
| DaVinci Clinical Data exchange            | [CDex](http://hl7.org/fhir/us/davinci-cdex/2019Jun/) | Version (1.0.0)              |
| Bidirectional Services eReferrals                      |  [BSer](http://build.fhir.org/ig/HL7/bser/) | Version (0.2.0) for FHIR R3  |
{:class="table table-bordered"}
{:.table-striped}


<br>
##  Purpose
This HL7&reg; IG defines FHIR R4 profiles, extensions and value sets needed to exchange SDOH content defined by the Gravity Project. It supports the following use cases:
1.	Document SDOH data in conjunction with the patient encounter,
2.	Document and track SDOH related interventions to completion,
3.	Gather and aggregate SDOH data for uses beyond the point of care (e.g. population health, quality reporting, risk adjustment/risk stratification, and research.
The IG defines how to represent coded content used to support the following care activities: screening, clinical assessment/diagnosis, goal setting, and the planning and performing of interventions. It addresses the need to gather SDOH information in the context of clinical encounters and describes how to share SDOH information and other relevant information with outside organizations for the purpose of coordinating services and support to address SDOH related needs, or for other purposes such as population health, quality assessment, and research.

<br>
## Latest Changes

| Number         | Description                                                                                                                                                              |
|---------------|----------------------------------------------------------------------------------------------------|
| 4             | Added notes for Profiles                                       |
| 3             | Updates to Use Case 1                                       |
| 2             | Update naming conventions to sdohcc                                        |
| 1             | Redesign chapters                                         |
{:class="table table-bordered"}
{:.table-striped}

<br>
## Note to Reviewers and Balloters

Review of version 0.0.2 of the IG is intended to gather high-level comments about the overall approach to the Implementation Guide and its positioning in terms of supporting the use cases defined for the Gravity Project. It also is aimed at identifying omissions that impact the quality of the IG.

Feedback on V0.0.2 of the IG should be sent to gravityproject@emiadvisors.net between January 30, 2020  and  February 20, 2020

<br>
##  How to Read This Guide

This Guide is divided into several pages which are listed at the top of each page in the menu bar.
* TOC: The TOC page lists the available pages for quick navigation to the available pages of content
* [Home](index.html): The home page contains the narrative implementer guidance that makes up this FHIR IG. It contains an introduction to the implementation guide
* [Background](Background.html): Provides background of The Gravity Project.
* [SDOH](SDOH_Content.html) Content: Lists types of information that is relevant when exchanging clinical information or doing a referral .
* [Personas and Patient Stories](Personas_and_Patient_Stories.html): Summarizes the actors and transactions used to accomplish the use cases
* [Use Cases](Use_Cases.html): Overview of the use cases covered.
* [Profiles Used in this IG](Profiles_used_in_this_IG.html): Lists and briefly describes all the profiles, extensions and value sets defined in this IG as well as the other profiles used to accomplish the covered use cases but defined in other IGs.
* [Security and Consent](Security_and_Consent.html): Links to relevant material are provided below and conformance constraints specific to this IG are described.
* [Conformance Guidance](Conformance_Guidance.html): Includes important terms, definitions, interpretations, assumptions and conformance requirements relevant to this guide.
* [Profiles and Extensions](profiles.html): This area of the IG describes the set of machine processable FHIR profiles and extension that are defined in this guide. These are profiles and extensions that have been specifically to exchange SDOH data defined for discrete representation through the Gravity Community collaboration process. Each Profile page includes a narrative introduction to explain the profile, a formal definition and a Quick Start guide to describe relevant mechanisms to query for the resource.
* [Terminology](terminology.html): This area of the IG describes the set of machine-processable FHIR value set definitions for the value sets used in the profiles and extensions defined in this IG. It also holds machine processable value set definitions for value sets that may be used with profiles and extensions defined in other IGs. During development and testing of the Implementation guide, the value set definitions reference a placeholder code system that holds placeholder codes. Placeholder codes are temporary codes which exist solely for the purpose of development and testing. They are fully defined in terms of the intended Code System for their eventual representation and in terms of the specific representational definition required by that intended coded system. Placeholder codes evaporate prior to the IG being published.  They are replaced with real codes established by each Standards Development Organization (SDO) authorized to update the intended code systems.  The value set definitions also are updated prior to publication and the IG is updated to include links to the value set expansions intended to be used when implementing according to the specifications of the published IG.
* [Capability Statements](capstatements.html): This area of the IG describes the machine processable FHIR capability statements for each of the system actors identified in the use cases.
* [Other](other.html): This area of the IG contains explanations of and links to all the examples used in this guide.
* [Downloads](downloads.html): This page provides links to the downloadable machine processable artifacts described in the other areas of the IG.

<br>
## How to Use This Guide: Practical Guidance for Implementers at All Levels of Standards Adoption

This area is reserved for content being developed by Lisa and Corey. It will describe the following scenarios:

1.	Implementers who have already developed mechanisms for gathering and sharing (providing and receiving) SDOH related information and have systems in production use of this information today.
2.	Implementers who currently are developing new systems that gather and share SDOH related information and plan to deploy them within the next 12-18 months (before 2021).
3.	Implementers who currently do not gather or share SDOH information.
		a.	Implementers who gather and produce C-CDA documents to support sharing of clinical encounter or patient summary information but have not yet implemented FHIR application interfaces (APIs) or support for the use of FHIR APIs offered by other systems to facilitate the sharing of clinical information.
		b.	Implementers who gather clinical encounter or patient summary information but do not yet produce C-CDA documents to support sharing of that information and have not yet implemented FHIR application interfaces (APIs) or support for the use of FHIR APIs offered by other systems to facilitate the sharing of clinical information.

<br>

## Acknowledgements

Reserve this area to included acknowledgements for the people and organizations involved in developing and maintaining this Implementation Guide.

There may also be some required copyright acknowledgements for certain Code Systems or other acknowledgements required by HL7 and FHIR.

The Placeholder Code Creation process was originally developed for Elimu profiles and SMART app development. It was modified in the context of creating this IG to make it more broadly applicable.

<br>
## Authors

Reserve this area to include authors of this guide.



