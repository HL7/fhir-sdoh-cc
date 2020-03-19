---
title: Naming Conventions for Gravity FHIR Artifacts and Placeholder Codes
active: Naming Conventions for Gravity FHIR Artifacts and Placeholder Codes
---

[Previous Page](Conformance_Guidance.html)

 **This page is currently under development**
 
This section provides guidance on naming conventions for Gravity FHIR profiles, profile examples, profile instance samples, and value sets.  

Overtime, the number of each of these artifacts will increase. Artifact names cannot fully represent the intent and use case(s) of each artifact in a way that will allow artifact differentiation based only on names. Therefore, the objective is to provide unique names which, to the degree possible, adhere to somewhat consistent patterns. However, the names will be at a high-level. Detailed information about an artifact will not be imparted by its name and must be obtained by referencing the full artifact.
<br>

# Conventions that Apply to All Gravity FHIR Artifact Names

* Uniqueness - Artifact names MUST be unique. <br>
* Artifact names will have segments as described in the Naming Conventions sections that follow. <br>
* Capitalization <br>

	*  With the exception of Segment 1, the first letter in each segment of an artifacts name MUST be capitalized. <br>
	* Tools (e.g., Trifolia, Forge, etc.) differ in their constraints on capitalization. For this reason, case for this first segment of the name may vary.
	* Concatenated capitalized words (Pascal Casing) MUST be used if a segment of an artifacts name contains more than one word. <br>
														
				Example: SDOHCC_Observation_FoodInsecurity_1

* File type - Tooling will automatically append the file type (e.g., StructureDefinition.xml, json, etc.) to artifact names. Therefore, file type is not included in naming conventions or examples provided here.
<br>
<br>

## Naming Conventions for Gravity FHIR Profiles


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



				Example: "SDOHCC_Goal_FoodInsecurity_1 and SDOHCC_Goal_FoodInsecurity_2"  are not versions of the same food insecurity goal profile. Rather, they are	different goal profiles that each address food insecurity. 
				
	*  Profiles with the same number for Segment 4 do not necessarily correlate to one another.
     
			
				Example: "SDOHCC_Goal_FoodInsecurity_1" does not necessarily correlate with "SDOHCC_Observation_FoodInsecurity_1".
					
<br>					
### Examples of Gravity FHIR Profile Names
							
	SDOHCC_Condition_FoodInsecurity_1
	SDOHCC_Goal_FoodInsecurity_1
	SDOHCC_Goal_Transportation_1
	SDOHCC_Observation_FoodInsecurity_1			
	SDOHCC_Observation_FoodInsecurity_2
	SDOHCC_QuestionnaireResponse_Housing_1

<br>
## Naming Conventions for Gravity FHIR Profile Examples 
The names for profile examples mirror the names of the profiles that they are examples of. Additionally, profile example names have a Segment 5 which appends "Example" to the profile name. A shortened description of each profile segment is repeated here for the readers convenience.

Gravity profile example names MUST contain the segments below, separated by underscores, in the order specified:
* **Segment 1**: SDOHCC

* **Segment 2**: FHIR resource name (e.g., Observation, Goal, etc.)

* **Segment 3**: A high-level label for the content category that the profile addresses (e.g., food insecurity)

* **Segment 4**: A number intended to distinguish different profiles for which segments 1, 2 and 3 are identical. 

* **Segment 5**: Example


<br>
### 	Examples of Gravity FHIR Profile Example Names
							
	SDOHCC_Goal_Transportation_1_Example
	SDOHCC_Observation_FoodInsecurity_1_Example
	SDOHCC_Observation_FoodInsecurity_2_Example
	SDOHCC_Observation_Housing_2_Example
	SDOHCC_QuestionnaireResponse_FoodInsecurity_1_Example


<br>
## Naming Conventions for Gravity FHIR Profile Instance Samples 
True instances of a patient profile are not provided in an IG because some instance data (e.g., patient demographic data) cannot be shared. However, instance samples may be useful (e.g., for Connectathons). 

The names for profile instance samples mirror the names of the profiles that they are instance samples of. Additionally, profile instance sample names have a Segment 5 which appends "InstanceSample" to the profile name. A shortened description of each profile segment is repeated here for the readers convenience.

Gravity profile instance samples names MUST contain the segments below, separated by underscores, in the order specified:
<br>
* **Segment 1**: SDOHCC<br>

* **Segment 2**: FHIR resource name (e.g., Observation, Goal, etc.)<br>

*	**Segment 3**: A high-level label for the content category that the profile addresses (e.g., food 
insecurity)<br>

*	**Segment 4**: A number intended to distinguish different profiles for which segments 1, 2 and 3 are identical. <br>

*	**Segment 5**: InstanceSample <br>


<br>
### Examples of Gravity FHIR Profile Instance Sample Names

	SDOHCC_Condition_FoodInsecurity_1_InstanceSample
	SDOHCC_Goal_Transportation_1_InstanceSample
	SDOHCC_Observation_FoodInsecurity_1_InstanceSample
	SDOHCC_Observation_Housing_2_InstanceSample


<br>
## Naming Conventions for Gravity FHIR Value Sets

The segment names for value sets are similar in purpose and order to those for profiles. 

Gravity value set names MUST contain the segments below, separated by underscores, in the order specified:

*	**Segment 1**: sdohcc<br>
       	This segment is the identifier assigned to the Gravity Project by HL7. (Case for this segment is all lower case since value sets are currently generated in a tool (termSpace) which allows lower case for the first letter of the name.)<br>

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
		* Sometimes true, Often true, Never true

		"Intervention" - could be a high-level label for the following value sets: 
		* Referral to food pantry program, Referral to garden program, Referral to delivered meals program
		* Home delivered meals education, Garden program education, Nutrition education

		"BodyStructure" - could be a high-level label for the following value sets: 
		* Hand, Foot, Finger, Toe
		* Brachial artery, Radial Artery, Digital Artery
	
Note: This last trio of values are an example of why labels with more granularity will not necessarily simplify the assignment of labels since any of the following labels	could have worked: "ArterialBodyStructure", "VascularBodyStructure", "ExtremityBodyStructure".
	
* **Segment 4**: A number intended to distinguish different value sets for which Segments 1, 2 and 3 are identical. (e.g., value sets that contain content with the same high-level label).  

	The first value set with a unique combination of Segments 1, 2, and 3, be assigned a number "1" for Segment 4. As new value sets with the same unique combination of Segments 1, 2, and 3 are added, numbers for Segment 4 will be assigned in sequential order.

	* Value set names that are identical, except for the number assigned for Segment 4, are not versions of a single value set. Rather, they are distinct value sets that contain content categorized with the same high-level label.
				
			For example, "sdohcc_ValueSet_Intervention_1" and "sdohcc_ValueSet_Intervention_2" 
		are not versions of the same value set, but rather value sets with different Intervention 
		content (e.g., for a different use case).
		
  * Value sets with same number assigned for Segment 4 do not necessarily correlate to one another.
				
		
			For example, "sdohcc_ValueSet_Intervention_1" does not necessarily
		correlate with  sdohcc_ValueSet_ContextValue_1.
			
<br>

### 	Examples of Gravity FHIR Value Set Names

	sdohcc_ValueSet_ContextValue_1 
	sdohcc_ValueSet_ContextValue_2 	
	sdohcc_ValueSet_ContextValue_3 
	sdohcc_ValueSet_FoodInsecurity_1 	
	sdohcc_ValueSet_InterpretationValue_1 
	sdohcc_ValueSet_InterpretationValue_2

<br>


[Next Page](Placeholder_Code_Systems,_Codes,_and_Value_Sets.html)