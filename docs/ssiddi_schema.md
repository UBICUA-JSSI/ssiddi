# SSIDDI Schema
Primary schema of SSI Description, Discovery and Interoperability

## References
|Prefix  |Vocabulary Name                                |Vocabulary Title                           |
|--------|-----------------------------------------------|-------------------------------------------|
|xsd     |https://www.w3.org/2009/XMLSchema/XMLSchema#   |XML Schema 1.1 Definition                  |
|dc      |http://purl.org/dc/elements/1.1/               |Dublin Core Metadata Initiative            |
|rdf     |http://www.w3.org/1999/02/22-rdf-syntax-ns#    |Resource Description Framework (RDF)       |
|rdfs    |http://www.w3.org/2000/01/rdf-schema#          |RDF Schema 1.1                             |
|owl     |http://www.w3.org/2002/07/owl#                 |Ontology Web Language (OWL)                |
|skos    |http://www.w3.org/2004/02/skos/core#           |Simple Knowledge Organization System (SKOS)|
|uddi    |http://www.uddi.org/schema/uddi_v3#            |Universal Description, Discovery and Integration (UDDI) Schema|
|did     |https://www.w3.org/ns/did/v1                   |Decentralized IDentifier (DID) |
|vc      |https://www.w3.org/2018/credentials/v1         |Verifiable Credential (VC)    |
|sec     |https://w3id.org/security#                     |Security Vocabulary               |

## Classes
|            |Organization                               |
|------------|-------------------------------------------|
|Label:      |isdl:Organization                          |
|Definition: |Top-level class representing a public organization or enterprise it describes and the identity services it offers.|
|URI:        |                                           |
|Type:       |owl:Class                                  |
|SubclassOf: |isdl:Organization                          |
|Properties: |name, discoveryURLs, description, identifierBag, categoryBag, publishedServices, subscribedServices, accreditedBy, signature    |

|            |Service                                    |
|------------|-------------------------------------------|
|Label:      |isdl:Service                               |
|Definition: |Logical child of a single Organization that contains descriptive information of a particular identity service. |
|URI:        |                                           |
|Type:       |owl:Class                                  |
|SubclassOf: |isdl:Service                               |
|Properties: |id, name, description, categoryBag, policy, interfaces, signature    |

|            |Interface                                  |
|------------|-------------------------------------------|
|Label:      |isdl:Interface                             |
|Definition: |Logical child of a single Service that contains technical descriptions of an identity service.|
|URI:        |                                           |
|Type:       |owl:Class                                  |
|SubclassOf: |isdl:Interface                             |
|Properties: |id, description, identifierBag, categoryBag, publishedServices, subscribedServices, signature    |

|            |Credential                                 |
|------------|-------------------------------------------|
|Label:      |isdl:Credential                            |
|Definition: |The logical child of a single Service that contains technical descriptions of an identity service.|
|URI:        |                                           |
|Type:       |owl:Class                                  |
|SubclassOf: |isdl:Interface                             |
|Properties: |vc:id, vc:type, vc:issuer, vc:issuanceDate, vc:credentialSubject |

## Properties

