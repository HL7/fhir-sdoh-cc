[Previous Page - Use Case 3](UseCase3.html)

This IG uses a variety of FHIR data exchange methods and worflow mechanisms. 

Use cases #1 and #2 address the need to push data to a recipient an event occurs to make information ready to be shared. FHIR messages and FHIR transaction are used to complete multiple RESTful actions at once with specific expectations as to how the messages and transactions will be handled. Use case #3 provides guidance on the use of FHIR transactions and batch transactions, again, to process multiple RESTful actions together and in a predefined way.

Use cases #1, #2, and #3 support exchange of information as collections of data resources or as documents. Guidance is provided for sharing FHIR documents and CDA documents using a DocumentReference with the CDA data artifact carried as a attachment in an encapsulated Binary resource.

A combination of Task, actionable CommunicationRequests and ServiceRequest resources are used to drive workflows needed to accomplish the SDOH-CC use cases.

[Next Page - Security and Consent Considerations](SecurityandConsentConsiderations.html)