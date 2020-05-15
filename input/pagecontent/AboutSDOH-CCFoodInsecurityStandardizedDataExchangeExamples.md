[Previous Page - About SDOH-CC IdentifierSystem Temporary Identifiers](AboutSDOH-CCIdentifierSystemTemporaryIdentifiers.html)

This IG defines a collection of profiles for representing screening information for food insecurity and documenting clinical data related to food insecurity which a clinician would record during a patient visit. It also defines profiles that support making a referral for services to address food insecurity and supplying feedback about a completed referral. Recording and sharing coded SDOH information improves how data can be used.

The example demonstrates how the SDOH-CC profiles supports four common uses of coded data.

1. Document Screening results digitally to allow them to be included in the patient's electronic health record.
2. Record SDOH Data in a way that aligns with the existing clinical data paradigm
3. Share SDOH referral information to connect the clinical setting with community-based support services
4. Gather SDOH information at the point of care and re-use the data to support quality measurement, research, and public or population health
5. Align with financial models, support claims payment, and the accelerate the shift toward value-based care <br>
 
###Example 1:

Initiate Screening [SDOHCC-Questionnaire-HungerVitalSign-1-Example-1](Questionnaire-SDOHCC-Questionnaire-HungerVitalSign-1-Example-1.html) is used as an instrument to assess food insecurity.
 
**Patient is screened for food insecurity prior to appointment. Screening information is available to clinician at point care to support clinical assessment of the patient's conditions.**<br>
1. [SDOHCC-QuestionnaireResponse-HungerVitalSign-1-Example-1](List-b1f72528-5501-4a6c-a5f3-9b86ec84264b.html) is used to hold the patient's responses to the Questionnaire screening instrument. 
2. SDOHCC_Observation_Foodinsecurity_1_Example_0 (STILL IN DEVELOPMENT) is a computed observation based on QuestionnaireResponse.<br>**Patient is seen in the office, 5/1/2019, and reports food insecurity that began about a month ago.**<br>
3. [SDOHCC_Observation_FoodInsecurity_1_Example_1](Observation-SDOHCC-Observation-FoodInsecurity-1-Example-1.html) is created.
4. [SDOHCC_Condition_FoodInsecurity_1_Example_1](Condition-SDOHCC-Condition-FoodInsecurity-1-Example-1.html) is created, and references [SDOHCC_Observation_FoodInsecurity_1_Example_1](Observation-SDOHCC-Observation-FoodInsecurity-1-Example-1.html).
5. [SDOHCC_Goal_FoodInsecurity_1_Example_1](Goal-SDOHCC-Goal-FoodInsecurity-1-Example-1.html) is created, and references [SDOHCC_Condition_FoodInsecurity_1_Example_1](Condition-SDOHCC-Condition-FoodInsecurity-1-Example-1.html). <br> **An intervention for social service assistance is requested.** <br> **Patient is seen by social services, 7/30/2019**<br>
6. [SDOHCC_Procedure_FoodInsecurity_1_Example_1](Procedure-SDOHCC-Procedure-FoodInsecurity-1-Example-1.html) is performed, and references [SDOHCC_Condition_FoodInsecurity_1_Example_1](Condition-SDOHCC-Condition-FoodInsecurity-1-Example-1.html). <br>**Patient is seen back in the office, 10/27/2019, and reports resolution of food insecurity**.<br>
7.  [SDOHCC_Observation_FoodInsecurity_1_Example_2](Observation-SDOHCC-Observation-FoodInsecurity-1-Example-2.html) is created, documenting absence of food insecurity.<br>[SDOHCC_Condition_FoodInsecurity_1_Example_1](Condition-SDOHCC-Condition-FoodInsecurity-1-Example-1.html) is updated to reflect that condition is now in remission, and adds a reference to [SDOHCC_Observation_FoodInsecurity_1_Example_2](Observation-SDOHCC-Observation-FoodInsecurity-1-Example-2.html).<br>[SDOHCC_Goal_FoodInsecurity_1_Example_1](Goal-SDOHCC-Goal-FoodInsecurity-1-Example-1.html) is updated to reflect that goal is achieved, and adds a reference to [SDOHCC_Observation_FoodInsecurity_1_Example_2](Observation-SDOHCC-Observation-FoodInsecurity-1-Example-2.html). <br> <table><tr><td><img src="FoodInsecurityExampleScenario2.png" /></td></tr></table><br>**Share SDOH referral information to connect the clinical setting with community-based support services**<br>STILL IN DEVELOPMENT<br>
8.  SDOHCC_ServiceRequest_FoodInsecurity_1_Example_1 <br>STILL IN DEVELOPMENT<br>**Gather SDOH information at the point of care and re-use the data to support quality measurement, research, and public or population health**<br>STILL IN DEVELOPMENT<br>
9.  Mind Map about eCQM<br>**Align with financial models, support claims payment, and the accelerate the shift toward value-based care**<br>STILL IN DEVELOPMENT<br>
10.  Mind Map about Claims

### Example 2:
The diagram below illustrates the same scenario from the perspective of three different encounter dates. It illustrates the capture of data provenance for the procedures performed on 7/30/2019, [date #2] and [date #3].



<table><tr><td><img src="FoodInsecurityExampleS2.png" /></td></tr></table>