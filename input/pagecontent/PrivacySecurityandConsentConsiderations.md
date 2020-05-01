[Previous Page - Data Provenance](DataProvenance.html)

### Gravity Data Principles
This IG utilizes [Gravity Data Principles](https://confluence.hl7.org/display/GRAV/Gravity+Data+Principles). 

### Privacy Considerations
*This section is still under development*


### Security Considerations

This IG utilizes security guidance established for FHIR R4 and covered in the US Core Security section. Links to relevant material are provided below and conformance constraints specific to this IG are described.
Many of the SDOH transactions include patient-specific information. For this reason, all SDOH transactions must be appropriately secured with access limited to authorized individuals, data protected while in transit and appropriate audit measures taken.

[Security considerations](http://hl7.org/fhir/R4/security.html) associated with FHIR transactions are applicable to this IG, particularly those related to:

* [Communications](http://hl7.org/fhir/R4/security.html#http)
* [Authentication](http://hl7.org/fhir/R4/security.html#authentication)
* [Authorization/Access Control](http://hl7.org/fhir/R4/security.html#authorization/access%20control)
* [Audit Logging](http://hl7.org/fhir/R4/security.html#audit%20logging)
* [Digital Signatures](http://hl7.org/fhir/R4/security.html#digital%20signatures)
* [Security Labels](http://hl7.org/fhir/R4/security-labels.html)
* [Binding]( https://www.hl7.org/fhir/security.html#binding)
 
 
Security conformance requirements specific to the SDOH-CC IG are as follows:

* Systems SHALL use TLS version 1.2 or higher for all transmissions not taking place over a secure network connection. (Using TLS even within a secured network environment is still encouraged to provide defense in depth.) US Federal systems SHOULD conform with FIPS PUB 140-2.
* Systems SHALL establish a risk analysis and management regime that conforms with HIPAA security regulatory requirements. In addition US Federal systems SHOULD conform with the risk management and mitigation requirements defined in NIST 800 series documents. This SHOULD include security category assignment in accordance with NIST 800-60 vol. 2 Appendix D.14. The coordination of risk management and the related security and privacy controls - policies, administrative practices, and technical controls - SHOULD be defined in the Business Associate Agreement when available.
* Systems SHALL implement consent requirements per their state, local, and institutional policies. The Business Associate Agreements SHOULD document systems mutual consent requirements.
* For Authentication and Authorization, Systems SHOULD support the [SMART App Launch Framework](http://www.hl7.org/fhir/smart-app-launch/history.cfml) for client <-> server interactions. NOTE: The SMART on FHIR specifications include the required OAuth 2.0 scopes for enabling security decisions.
* Systems SHALL reference a single time source to establish a common time base for security auditing, as well as clinical data records, among computing systems. The selected time service SHOULD be documented in the Business Associate Agreement when available.
* Systems SHALL keep audit logs of the various transactions.
* Systems SHALL conform to [FHIR Communications Security](http://hl7.org/fhir/R4/security.html#http) requirements.
* Systems MAY provide Provenance statements using the [US Core Provenance Profile](http://hl7.org/fhir/us/core/StructureDefinition-us-core-provenance.html) resource and associated requirements.
* Systems MAY implement the [FHIR Digital Signatures](http://hl7.org/fhir/R4/security.html#digital%20signatures) and provide feedback on its appropriateness for US Core transactions.
* Systems MAY protect the confidentiality of data at rest via encryption and associated access controls. The policies and methods used are outside the scope of this specification.

<br>
### Consent Considerations
This IG requires the use of a Consent resource to capture and exchange a subject's consent to share information with a requestor.  When consent to share is agreed, a Consent resource in included with the shared information.  When consent to share is not agreed, a Communication is provided as a response to the request message and the Consent resource is included in the response message to document the denial to share the requested information.

[Next Page - Additional Conformance Considerations](AdditionalConformanceConsiderations.html)