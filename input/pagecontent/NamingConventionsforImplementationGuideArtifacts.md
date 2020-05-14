[Previous Page - Overview of Capability Statements](OverviewofCapabilityStatements.html)

 **This page is currently under development**
 
 

This section provides naming conventions for names of profiles, value sets and examples within the SDOH-CC implementation guide. It also provides conventions for ids and titles used for the artifact. 

* An artifact's name is a "computer-friendly" name that has meaning to a human and can be processed by a computer (e.g. string pattern, regular expression matching). 
* The id is the unique way of "naming" the artifact in a computable way but does not have meaning and is not intended to be understandable by a human. 
* An artifact's title is a "human-friendly" name. 

Artifact names alone cannot fully represent the intent and use case(s) of each artifact in a way that allows artifact differentiation. Therefore, the objective when assigning an artifact name is to provide unique high-level names which, to the degree possible, adhere to somewhat consistent patterns. Detailed information about an artifact will not be imparted by its name and must be obtained by referencing the full artifact.  

Where possible, we follow a consistent pattern between the name and the title. The id also follows a pattern, but for value sets the id includes a meaningless, unique, alpha-numeric string to support computer processing. Examples of each are described below in the conventions established for the artifacts in theis implementation guide. 

<br>

Conventions that apply to Implementation Guide Artifact names include:

* Uniqueness - Artifact names MUST be unique. <br>
* Artifact names will have segments as described in the Naming Conventions sections that follow. <br>
* The first letter in each segment of an artifact's name MUST be capitalized. <br>
* Concatenated capitalized words (Pascal Casing) MUST be used if a segment of an artifact name contains more than one word. <br>
														
				Example: SDOHCC_Observation_FoodInsecurity_1

* File type - Tooling will automatically append the file type (e.g., xml, json, etc.) to artifact names. Therefore, file type is not included in naming conventions or examples provided here.
<br>

Where a title is used for an artifact, it will align with the artifact name but without the underscores. 
<br>


### Conventions for Profile Names

Gravity profile names MUST contain the segments below, separated by underscores, in the order specified.
* **Segment 1**: SDOHCC 
      
  This segment is the identifier assigned to the Gravity Project by HL7. (Case for this segment is all upper case since profiles are currently generated in Forge which requires upper case for the first letter of the name.)<br>
	
* **Segment 2**: FHIR resource name (e.g., Observation, Goal, etc.)

	* Concatenated FHIR resource names MUST be represented as in FHIR using concatenated capitalized words (Pascal Casing). 

			Example: QuestionnaireResponse 
							
* **Segment 3**: A high-level label for the content category that the profile addresses (e.g., food insecurity, housing, transportation, etc.). 
	 
	Overtime, it is likely that additional guidance will be developed for assigning high-level labels. It is recognized that there is subjectivity in identifying a high-level label for the category of content that the profile addresses. Therefore, achieving some degree of consistency in choosing high-level labels will be challenging. However, developing guidance for more granular category names may be even more challenging without any guarantee of improvement in consistency.<br>

	* High-level labels SHOULD use the singular form.
	* High-level labels that cannot be described with one word (e.g., food insecurity, blood pressure) MUST use concatenated capitalized words (Pascal Casing). 
				
				Example: FoodInsecurity



* **Segment 4**: A number intended to distinguish different profiles for which Segments 1, 2 and 3 are identical. (e.g., Gravity profiles that address the same high-level category for a given FHIR resource). 

    The first profile with a unique combination of Segments 1, 2, and 3, will be assigned a number "1" for Segment 4. As new profiles with the same unique combination of segments 1, 2, and 3 are added, numbers for Segment 4 will be assigned in sequential order.

	*  Profile names that are identical, except for the Segment 4 number, are not versions of a single profile. Rather, they are distinct profiles that address similar high-level domains.



				Example: "SDOHCC_Goal_FoodInsecurity_1 and SDOHCC_Goal_FoodInsecurity_2" are not versions of the same food insecurity goal profile. Rather, they are	different profiles for the Goal Resource that each address food insecurity. 
				
	*  Profiles with the same number for Segment 4 do not necessarily correlate to one another.
     
			
				Example: "SDOHCC_Goal_FoodInsecurity_1" does not necessarily correlate with "SDOHCC_Observation_FoodInsecurity_1".
					
<br>					
#### Examples of Profile Name
							
	SDOHCC_Condition_FoodInsecurity_1
	SDOHCC_Goal_FoodInsecurity_1
	SDOHCC_Goal_Transportation_1
	SDOHCC_Observation_FoodInsecurity_1			
	SDOHCC_Observation_FoodInsecurity_2
	SDOHCC_QuestionnaireResponse_Housing_1
	
<br>	
#### Examples of a Profile Title and id, given a specific name

| Profile Name | Profile Title | Profile id |
| -------- | -------- | -------- |
| SDOHCC_Condition_FoodInsecurity_1     | SDOHCC Condition FoodInsecurity 1     | SDOHCC-Condition-FoodInseurity-1     |
{:class="table table-bordered"}
{:.table-striped}


<br>
### Conventions for Value Set Name
<br>
A value set is a collection of coded concepts. The coded concepts can come from the same or different code systems.  Additionally, a value set can include temporary codes where needed. The definition of the value set is not considered final until the IG in which the value set is defined becomes published.  Before publication, all value set definitions MUST be defined in an external value set management resource such as the HL7 UTG or NLM VSAC. The segment names for value sets are similar in purpose and order to those for profiles. However, value set ids are unique, meaningless identifiers just as an OID in VSAC is a menaingless identifier

Gravity value set names MUST contain the segments below, separated by underscores, in the order specified:

*	**Segment 1**: SDOHCC This segment is the identifier assigned to the Gravity Project by HL7. 
				
*	**Segment 2**: ValueSet

*	**Segment 3**: A high-level label for the category of content (e.g., intervention, context value, body structure, device, etc.) that the value set contains. <br>

	Overtime, it is likely that additional guidance will be developed for assigning high-level labels. It is recognized that there is subjectivity in identifying a high-level label for the category of content in a value set. Therefore, achieving some degree of consistency in choosing high-level labels will be challenging. However, developing guidance for more granular category names may be even more challenging without any guarantee of improvement in consistency. 

	* High level labels SHOULD use the singular form (e.g. Intervention not Interventions).
	
	* High-level labels that cannot be described with a single word (e.g., body structure) MUST use concatenated capitalized words (Pascal Casing). 


			Example: BodyStructure

	*Examples of "high-level labels" for Segment 3:*

	The examples were chosen to illustrate the challenges of selecting a high-level label for a value set. They illustrate how a value set might fit into more than one high-level label, although only one can be selected.

		"ContextValue" - could be the high-level label for the following value sets: 
		* Absent, Present, Unknown 
		* At risk, Not at risk, Unknown

		"InterpretationValue" - could be a high-level label for the following value sets:
		* Very low, Low, High, Very high
		* Normal, Abnormal

		"Intervention" - could be a high-level label for the following value sets: 
		* Referral to food pantry program, Referral to garden program, Referral to delivered meals program
		* Home delivered meals education, Garden program education, Nutrition education

		"BodyStructure" - could be a high-level label for the following value sets: 
		* Hand, Foot, Finger, Toe
		* Brachial Artery, Radial Artery, Digital Artery
	
Note: This last trio of values are an example of why labels with more granularity will not necessarily simplify the assignment of labels since any of the following labels could have worked: "ArterialBodyStructure", "VascularBodyStructure", "ExtremityBodyStructure".
	
* **Segment 4**: A number to distinguish different value sets for which Segments 1, 2 and 3 are identical. (e.g., value sets that contain content with the same high-level label).  

	The first value set with a unique combination of Segments 1, 2, and 3, be assigned a number "1" for Segment 4. As new value sets with the same unique combination of Segments 1, 2, and 3 are added, numbers for Segment 4 will be assigned in sequential order.

	* Value set names that are identical, except for the number assigned for Segment 4, are not versions of a single value set. Rather, they are distinct value sets that contain content categorized with the same high-level label.
				
			For example, "SDOHCC_ValueSet_Intervention_1" and "SDOHCC_ValueSet_Intervention_2" are not versions of the same value set, but rather value sets with different Intervention content (e.g., for a different use case).
		
  * Value sets with the same number assigned for Segment 4 do not necessarily correlate to one another.
				
		
			For example, "SDOHCC_ValueSet_Intervention_1" does not necessarily correlate with  "SDOHCC_ValueSet_ContextValue_1".
			
<br>

#### 	Examples of Value Set Name

	SDOHCC_ValueSet_ContextValue_1 
	SDOHCC_ValueSet_ContextValue_2 	
	SDOHCC_ValueSet_ContextValue_3 
	SDOHCC_ValueSet_FoodInsecurity_1 	
	SDOHCC_ValueSet_InterpretationValue_1 
	SDOHCC_ValueSet_InterpretationValue_2


<br>

### Convention for Value Set Identifier

The pattern for meaningless value set ids is as follows (all in lowercase):

* **Segment 1**: sdohcc This segment is the identifier assigned to the Gravity Project by HL7.
* **Segement 2**: An abbreviation (called "Code System Prefix") used internally to identify the code system of the value set per the table below.
* **Segment 3**: vs for value set.
* **Segement 4**: A meaningless, random, alphanumberic string that is unique in the context of the combination of the first 3 segments. This convention assures a unique value set id. This value set id may be replaced in the future by a fomally registered identifier such as a VSAC OID.

| SDO Source Terminology           | Code System Prefix |
|----------------------------------|--------------------|
| SNOMED CT                        | sctt               |
| LOINC                            | lncct              |
| RXNORM                           | rxnnt              |
| ICD-10-CM                        | i10cmt             |
| CPT-4                            | cpt4t              |
| HL7                              | hl7t               |
| Grouping (multiple code systems) | grp                |
{:class="table table-bordered"}
{:.table-striped}

<br>

#### Examples of a Value Set Title and id, given a specific name

| Value Set Name                               | Value Set Title                   | Value Set id                                        |
|----------------------------------------------|-----------------------------------|-----------------------------------------------------|
| SDOHCC_ValueSet_FoodInsecurity_2             | SDOHCC ValueSet Food Insecurity 2 | sdohcc-i10cmt-vs-202004291638                       |
| SDOHCC_ValueSet_FoodInsecurityIntervention_1 | SDOHCC ValueSet Food Insecurity Intervention 2   | sdohcc-sctt-vs-c9f6c30c-6b84-3b4f-42d0-3b59040d6964 |
{:class="table table-bordered"}
{:.table-striped}

<br>
### Conventions for Example Name 

The convention for the name for a profile example is similar to the convention for the name of the profile that it is an example of. Additionally, the example name has a Segement 5 which appends "Example" to the profile name.  A shortened description of each profile segment is repeated here for the readers convenience. Note that the acutal example files do not contain a "name" data element bur rather just the example ids since they are instance examples of a resource that adheres to their respective profile. 

Gravity profile example names MUST contain the segments below, separated by underscores, in the order specified:
* **Segment 1**: SDOHCC

* **Segment 2**: FHIR resource name (e.g., Observation, Goal, etc.)

* **Segment 3**: A high-level label for the content category that the profile addresses (e.g., food insecurity)

* **Segment 4**: A number intended to distinguish different profiles for which segments 1, 2 and 3 are identical 

* **Segment 5**: Example

* **Segment 6**: A number to distinguish different examples for the same profile

<br>
#### 	Examples of Profile Example Names
							
	SDOHCC_Goal_Transportation_1_Example_1
	SDOHCC_Observation_FoodInsecurity_1_Example_1
	SDOHCC_Observation_FoodInsecurity_1_Example_2
	SDOHCC_Observation_FoodInsecurity_2_Example_1
	SDOHCC_Observation_Housing_2_Example_1
	SDOHCC_QuestionnaireResponse_FoodInsecurity_1_Example_1

Conventions for an example identifier align with the conventions for an example name but will use hyphens instead of underscores.
<br>

#### Examples of an Example Title and id, given a specific name

| Example Name                                | Example Title                               | Example id                                  |
|---------------------------------------------|---------------------------------------------|---------------------------------------------|
| SDOHCC_Condition_FoodInsecurity_1_Example_1 | SDOHCC Condition FoodInsecurity 1 Example 1 | SDOHCC-Condition-FoodInsecurity-1-Example-1 |
| SDOHCC_Procedure_FoodInsecurity_1_Example_1 | SDOHCC Procedure FoodInsecurity 1 Example 1 | SDOHCC-Procedure-FoodInsecurity-1-Example-1 |
{:class="table table-bordered"}
{:.table-striped}

[Next Page - About SDOH-CC Master List, Temporary Code System, and Temporary Codes](AboutSDOH-CCMasterListTemporaryCodeSystemandTemporaryCodes.html)