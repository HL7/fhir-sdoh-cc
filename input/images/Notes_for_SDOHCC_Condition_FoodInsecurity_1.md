---
title: Notes for SDOHCC_Condition_FoodInsecurity_1
active: Notes for SDOHCC_Condition_FoodInsecurity_1
---

[Previous Page](Profiles_used_in_this_IG.html)


## Additional Guidance for [SDOHCC_Condition_FoodInsecurity_1 Profile](StructureDefinition-SDOHCC-Condition-FoodInsecurity-1.html)

The FHIR Observation, Condition and Goal resources reference one another. Therefore, to support interoperability and analytics, similar approaches have been used in the structured representation of food insecurity observations, conditions and goals. 

The diagram below shows the relationship between Observation, Condition and Goal. 

An initial Observation (1) is evidence for a Condition (2) that is addressed by a Goal (3) that has an outcome of a later Observation (4).

<table><tr><td><img src="Condition mindmap 2020.01.27.png" /></td></tr></table>


The sections that follow provide additional guidance on 1) specific elements of this profile and 2) efforts to align the profile with the following correlated Observation and Goal profiles:

* 	SDOHCC_Observation_FoodInsecurity_1
* 	SDOHCC_Goal_FoodInsecurity_1

<br>
### Condition.evidence

To align this food insecurity condition with the food insecurity observation that supports it, this element is constrained to Condition.evidence.detail which, in turn, is constrained to reference only SDOHCC_Observation_FoodInsecurity_1.

<br>
### Condition.code

This element references sdohcc_ValueSet_FoodInsecurity_1. This value set contains the SNOMED CT codes listed below.

| Code                    | Display                            |
|-------------------------|------------------------------------|
| 733423003               | Food insecurity (finding)          |
| sdohcc-sctt-21000243108 | Mild food insecurity (finding)     |
| sdohcc-sctt-31000243105 | Moderate food insecurity (finding) |
| sdohcc-sctt-41000243104 | Severe food insecurity (finding)   |
{:class="table table-bordered"}
{:.table-striped}

<br>

1.	This value set is also used for: <br>
	* Observation.code in SDOHCC_Observation_FoodInsecurity_1
		
	The consistent use of similar codes for a condition and an observation referenced as evidence for that condition will facilitate analytics and interoperability between Condition and Observation.

	**Example:**

	* 	SDOHCC_Condition_FoodInsecurity_1 modeled with:
		* Condition code = Mild food insecurity 

	aligns with the observation that this condition references (via Condition.evidence.detail):
	* 	SDOHCC_Observation_FoodInsecurity_1 modeled with:
		* Observation code = Mild food insecurity 
		* Observation value = Known present

2.	The Food insecurity (finding) code in this value set is also used as the value for:

	*	Goal.target.measure in SDOHCC_Goal_FoodInsecurity_1

	The consistent use of similar codes for a condition and a goal that addresses that condition will facilitate analytics and interoperability between Condition and Goal.

	**Example:**

	* SDOHCC_Condition_FoodInsecurity_1 modeled with:
		* Condition code = Food insecurity 

	aligns with the goal that address this condition (via Goal.addresses):

	*	SDOHCC_Goal_FoodInsecurity_1 modeled with:
		* Goal description: Food security <br> 
	and
		* Goal target measure = Food insecurity 
		* Goal target detail = Known absent
		 
<br>

### Condition.severity

This element is prohibited. 

In lieu of a value set of food insecurity codes with precoordinated severities, this profile could have allowed only Condition.code = Food insecurity and represented severity using Condition.severity. However, the FHIR Observation Resource does not provide a separate element for modifying the severity of Observation.code. Therefore, Observation.code for SDOHCC_Observation_FoodInsecurity_1 uses a value set of food insecurity codes that have precoordinated severity. To enable consistency across the Observation and Condition profiles, Condition.code and Observation.code use the same value set and Condition.Severity is prohibited. 

<br>

### Condition.onset

This element is constrained to Period. Similar to the constraint for Observation.effective for SDOHCC_Observation_FoodInsecurity_1, Date is not allowed for Condtition.onset. 

Observation.effective is constrained to Period because, unlike some observations (e.g., a seizure, body weight, etc.) that occur at a point in time, the observation of Food insecurity is about a state that is present over an extended period of time (e.g., the past month, year, etc.). Similarly, Condition.onset constrains the onset of the condition of Food insecurity to occur over a period of time (e.g., the past month, year, etc.) as opposed to at a point in time.

<br>

### Condition.abatement

This element is constrained to Period or Date. Although Date is not allowed for Condition.onset for the reasons stated above, Date is allowed for Condition.abatement because the condition of food insecurity could end at a specific point in time (e.g., the day a paycheck from a new job arrives or access to meals in a food program starts).





[Next Page](Notes_for_SDOHCC_Goal_FoodInsecurity_1.html)