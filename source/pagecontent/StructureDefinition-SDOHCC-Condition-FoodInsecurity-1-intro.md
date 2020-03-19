## Profile design 
This profile is adapted from US Core Procedure. However, the value set bindings are not necessarily compliant. 

## Additional Guidance

The FHIR Observation, Condition and Goal resources reference one another. Therefore, to support interoperability and analytics, similar approaches have been used in the structured representation of food insecurity observations, conditions and goals. 

The diagram below shows an example of a relationship between Observation, Condition and Goal. 

An initial Observation (1) is evidence for a Condition (2) that is addressed by a Goal (3) that has an outcome of a later Observation (4).

<table><tr><td><img src="Condition mindmap 2020.01.27.png" /></td></tr></table>

The sections that follow provide additional guidance on 1) specific elements of this profile and 2) efforts to align the profile with the following correlated Observation and Goal profiles:
* SDOHCC_Observation_FoodInsecurity_1
* SDOHCC_Goal_FoodInsecurity_1

### Condition.evidence

To align this food insecurity condition with the food insecurity observation that supports it, this element is constrained to Condition.evidence.detail which, in turn, is constrained to reference only SDOHCC_Observation_FoodInsecurity_1. When evidence for a food insecurity condition exists in the form of a food insecurity observation, decisions related to linking the condition to the relevant observation that may support it are up to the implementor. 

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


The above options allow a general Food insecurity condition or a more specific Food insecurity condition (e.g., mild, moderate, or severe).

**1**	This value set is also used for:

* Observation.code in SDOHCC_Observation_FoodInsecurity_1

The consistent use of similar codes for a condition and an observation referenced as evidence for that condition will facilitate analytics and interoperability between Condition and Observation.

*Example*:

* SDOHCC_Condition_FoodInsecurity_1 modeled with:
	* Condition code = Mild food insecurity 

aligns with the observation that this condition references (via Condition.evidence.detail):

* SDOHCC_Observation_FoodInsecurity_1 modeled with:
	* Observation code = Mild food insecurity 
	* Observation value = Known present

**2**	The Food insecurity (finding) code in this value set is also used as the value for:

* Goal.target.measure in SDOHCC_Goal_FoodInsecurity_1

The consistent use of similar codes for a condition and a goal that addresses that condition will facilitate analytics and interoperability between Condition and Goal.

*Example*:
* SDOHCC_Condition_FoodInsecurity_1 modeled with:
	* Condition code = Food insecurity 

aligns with the goal that address this condition (via Goal.addresses):

* SDOHCC_Goal_FoodInsecurity_1 modeled with:
	* Goal description: Food security <br> and <br>
	* Goal target measure = Food insecurity
	* Goal target detail = Known absent

### Condition.severity

This element is prohibited. 

In lieu of a value set of food insecurity codes with precoordinated severities, this profile could have allowed only “Condition.code = Food insecurity” and represented severity using Condition.severity. However, the FHIR Observation Resource does not provide a separate element for modifying the severity of Observation.code. Therefore, Observation.code for SDOHCC_Observation_FoodInsecurity_1 uses a value set of food insecurity codes that have precoordinated severity. To enable consistency across the Observation and Condition profiles, Condition.code and Observation.code use the same value set and Condition.Severity is prohibited. 

### Condition.onset

Condition.onset is constrained to dateTime. While it is recognized that “Food insecurity” is a state that may have its onset over a more extended (or fuzzy) period of time (e.g., the past month), dateTime was chosen over Period in part because dateTime is not open-ended whereas Period, when used without an end date, is open-ended. However, the fuzziness related to the exact onset of food insecurity is probably best handled by using a lower precision representation (e.g., month/year or year) for dateTime as opposed to a higher precision representation (e.g., year/month/date/hour/min).

### Condition.abatement

Condition.abatement is constrained to “dateTime”. Where the abatement period is somewhat fuzzy, this element might use month/year. However, since the condition of food insecurity may possibly end at a specific point in time (e.g., upon receipt of a paycheck from a new job or gaining eligibility to a food program) a higher precision representation (e.g., year/month/date/hour/min) might also be used for dateTime.





