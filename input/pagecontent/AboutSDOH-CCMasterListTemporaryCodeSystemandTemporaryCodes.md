[Previous Page - Naming Conventions for Implementation Guide Artifacts](NamingConventionsforImplementationGuideArtifacts.html)

### Gravity Project Data Element Master List
The Gravity Project community collaborated to develop a list of data elements needed to share SDOH information related to Food Insecurity for the four activities of care:  screening, assessment/diagnosis, care planning, and intervention.  The result was a Master List of concepts to be coded using nationally recognized Code Systems.  Where available, the Master List identifies the code and Code System to be used to represent the data element concept when exchanging this data in a standardized format. Where the needed codes are not yet available in a nationally recognized Code System (recommended for use in the [Interoperability Standards Advisory](https://www.healthit.gov/isa/) ), the Master List includes temporary codes assigned within the context of the SDOH-CC IG to facilitate testing and balloting of the implementation guidance.  The Gravity Project works with Code System stewards to ensure that coding gaps are identified, considered and resolved.  As new codes become available, the temporary codes are replaced.  The intention of the Gravity Project is to replace all the vetted and confirmed temporary codes with permanent codes in a nationally recognized Code System prior to publication of the SDOH-CC IG.

The Master List also includes codes needed to facilitate the information exchange workflows covered by the Use Cases covered by the SDOH-CC IG.

Download the current master list of data elements identified for potential representation in the Gravity project including codes (permanent or temporary) used in this version of the SDOH CC IG: [Master and Temporary Codes](https://confluence.hl7.org/display/GRAV/SDOH-CC+Master+and+Temporary+Code+List)
 
 
 
<br>
### Temporary Code System
The SDOH-CC IG includes a Temporary Code System created to establish temporary codes for concepts needed to facilitate the sharing of SDOH (e.g. food insecurity) information across the four activities of care. The Temporary Code System exists to hold codes that will be replaced prior to publication with permanent codes from nationally recognized Code Systems. 

WARNING: Implementers need to be mindful of the use of temporary codes in the implementation guide.  Implementers must plan for the need to update applications when developing solutions to test and pilot the SDOH-CC guidance.  Temporary codes will be replaces with permanent codes from nationally recognized code systems prior to publication of this IG.
 
The process of issuing temporary codes in a Temporary Code System local to a FHIR IG was developed to support rapid assignment of needed codes that are guaranteed to be unique within the use of a specific IG managed by a specific workgroup/organization. Use of temporary codes supports IG testing activities which improves the certainty of proposed concept definitions and reduces the risk of issuing permanent codes that are not needed or not fit to meet demonstrated needs. This process is not intended to replace any processes being developed (e.g., by HTA, UTG, CIMI, etc.).


<br>
### Temporary Code Naming Conventions

Temporary codes are named using three segments. The resulting code is intentionally "unfriendly" to prevent implementers from growing attached to the code or becoming reliant on the temporary codes. The unfriendliness of the code evokes an important instinct to seek to replace the code with the type of code typically issues by nationally recognized Codes Systems. This is important to the design and supports the intention and commitment to replace temporary codes with permanent ones.
	
**Segment 1: IG Prefix (represents the IG code system in the CodeSystem Resource)**

The IG prefix is assigned when the IG proposal is approved within HL7. The SDOH-CC IG uses the prefix: sdohcc. 

	
**Segment 2: Temporary Code System Prefix (represents the intended/target code system)** 

To avoid confusion when later reconciling temporary codes against permanent codes, the Temporary Code System Prefix is intentionally not an official code system designation. While there is an expressed intention to replace temporary codes with permanent codes, there is no certainty how long it may take to accomplish the replacement process. The use of well formed, unique temporary codes mitigates the risk that creation of the permanent codes could delay use of the information exchange standard.

All prefixes are case insensitive. Lowercase is used here for consistency.


| SDO Source Terminology | Code System Prefix |
|------------------------|--------------------|
| SNOMED CT              | sctt               |
| LOINC                  | lncct              |
| RXNORM                 | rxnnt              |
| ICD-10-CM              | i10cmt             |
| CPT-4                  | cpt4t             |
| HL7                    | hl7t               |
{:class="table table-bordered"}
{:.table-striped}


**Segment 3: A unique identifier which may be any unique string (e.g., a specific time stamp or other string)** 

Time stamp will be the unique string used for all temporary codes systems other than SNOMED CT. SNOMED CT will use a unique string that is not a timestamp.  

When time stamp is used, the pattern YYYYMMDDHHmmssTZ is used to assure uniqueness. YYYY is a 4-digit year, MM is the 2-digit month, DD is the 2-digit day and HH is the 2-digit hour, mm is the minutes, ss is the seconds, TZ is the time zone. Time stamp should be the time at which a temporary code is created. The advantage of this approach for time stamp is the balance between simplicity and uniqueness.




[Next Page - About SDOH-CC IdentifierSystem Temporary Identifiers](AboutSDOH-CCIdentifierSystemTemporaryIdentifiers.html)