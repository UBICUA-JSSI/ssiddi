# SSIDDI
Self-Sovereign Identity Description, Discovery and Interoperability

## Motivation
Core aspects of the Self-Sovereign Identity (SSI) model are specified in the W3C Primers related to [Decentralized IDentifier (DID)](https://www.w3.org/TR/did-core/) and [Verifiable Credential (VC)](https://www.w3.org/TR/vc-data-model/). In particular, the VC specification defines a Verifiable Data Registry (VDR) responsible for "mediating the creation and verification" of all elements (identifiers, verifiable credential schemas, revocation registries, and so on) "which might be required to use verifiable credentials". We argue that the described data registry may have significant shortcomings due to the lack of sematic interoperability. In fact, the relevant questions on who, what, when, where and how can operate with those verifiable credentials will inevitably arise in any practical implementation of [VDR](https://www.w3.org/TR/vc-data-model/).

Answering these questions is especially important within the decentralized models in which identity owners are involved into trustworthy relationships, such as VC issuance in the Issuer-Holder pair and VC verification in the Holder-Verifier pair. If we consider these processes as parts of the whole VC service, an Issuer becomes a service provider meanwhile Holder and Verifier converts to service consumers. From the interoperability point of view, all necessary service-related information must be previously published by Issuers in order to be later discovered and utilized by Holders and Verifiers.

It is mandatory that the service descriptions would be presented in both human and machine readable formats. Also, they should be published by accredited publishers/providers in order to propage trust for their subscribers/consumers. The semantic functionality leverages lifecycle management of identity services and allows orchestrating them in a multi-layer interoperability stack. As a consequence, the whole system meets the requirements of provenance, integrity and legality for qualified data in full compliance with the regulatory and interoperability frameworks, such as [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/data-protection-eu_en), [eIDAS](https://eur-lex.europa.eu/legal-content/EN/TXT/), [EIF](https://ec.europa.eu/isa2/eif_en), [EBSI](https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/EBSI), and others.

Concerning the semantic interoperability of web services, such an approach based on the [Universal Description, Discovery and Interaction (UDDI)](http://uddi.xml.org/specification) specification has been already developed. We notice that the UDDI architecture can be easily adjusted to the VC services whereas the original data model of UDDI seems to be obsolete and intransferable to [VDR](https://www.w3.org/TR/vc-data-model/). In our opinion, an appropriate and up-to-date solution should be built within the frame of [Web Ontology Language (OWL)](https://www.w3.org/TR/owl2-syntax/).

By combining an UDDI-like registry architecture with an OWL-compliant data model, we pretend to design a generalized solution on semantic description, discovery and interoperability for self-sovereign identity and verifiable credentials.

## Definitions
SSI Description, Disovery and Interoperability (SSIDDI) is an open initiative addressed to the integration, interoperability and governance in the SSI model. SSIDDI is focused on providing descriptions of very general concepts of Identity Management (IM). First of all, we introduce a definition of SSI Service:

**SSI Service** is an ensemble of management operations related to the digital identity and its verifiable attributes (_aka_ verifiable credentials). 

Our analysis is limited by the provider-consumer type of identity relationships. In a typical scenario, a user acquires its credentials (identity card, driving licence, university diploma, medical insurance, etc.) from a trusted service and then uses them in relations with other identity or business services. Within the SSI model, such a scenario implies that an identity owner, as a DID Subject and VC Holder, establishes legal relations with SSI Service providers: DID Controller and VC Issuer.

In a very general manner, we introduce a SSI Service lifecycle that includes the following basic stages:

- **Stage 1 - Definitions** (aka service design): At this stage, a SSI Service Provider designs and publishes the service definitions that can be later discovered and employed by their consumers. For example, a VC Issuer works out all necessary information on the VC issuance and stores it on a public registry. In its turn, the future VC Holders and VC Verifiers discover this information in order to make their business decisions. 
- **Stage 2 - Registrations** (aka service implementation, onboaring or enrolment): At this stage, the above-mentioned SSI Service Provider registers consumers in accordance with the previously published service descriptions. For example, a VC Issuer registers identity and attributes of a DID Subject - VC Holder. Moreover, the already registered VC Verifiers can subscribe to particular SSI Services of the particular provider.
- **Stage 3 - Operations** (aka service usage): At this stage, the SSI Service Provider and the consumers interoperate using the service definitions and registrations made at the previous stages. Thus, both Issuer-Holder and Holder-Verifier pairs interact within the frames of VC issuance-acquisition and VC presentation-verification processes, respectively.

The technical interoperability between DID Subjects relies on the Decentralized Public Key Infrastructure (DPKI) that is compound of two registry types:
- Digital Wallet as a private component of DPKI for storing individual cryptographic material and other digital assets of its owner. 
- Identity Registry as a public component of DPKI for storing the technical information and cryptographic states of all DID Subjects registered in a particular ecosystem. The Distributed Ledger Technology (DLT) provides the best-suited solution for implementing the Identity Registry.

To meet the requirements of semantic interoperability, we introduce a new type of registry:

**SSI Service Registry** is a public storage system for saving and finding the semantic and technical descriptions of SSI Services and the relevant information. 

From the [VC Data Model](https://www.w3.org/TR/vc-data-model/) viewpoint, the two registries, i.e. SSI Registry and SSI Service Registry, together represent a complete implementation of Verifiable Data Registry. However, following to the Separation of Concerns (SoC) principle, we argue that such a splitted registry solution brings multiple advantages in terms of:
- Guaranteeing pseudonymisation through separating identifiers and identity attributes.  
- Decoupling the service description from the service execution.
- Empowering the semantic techniques for describing identity and verifiable credentials.
- Enabling reusability of identity services and their components.
- Introducing a desired basis for the legal and organizational levels of interoperability.
- Simplifying the structure and maintenance of distributed ledgers.

Taking into account the above mentioned, the modified lifecycle diagram for verifiable credentials can be depicted as follows:

<img src="ssiddi_architecture.png" width="62%" height="" />

The SSIDDI solution defines three components of the SSI Service Registry: Data Model, Specification APIs and Technical Architecture.

## Data Model
SSIDDI has the following logical structure:
- **White Pages** that contain descriptions of accredited public entities, including name, discovery URLs, contact info, etc. Note that each accredited public entity can play two roles, i.e. Publisher and Subscriber, being a Subscriber in one context and a Publisher in another one.
- **Yellow Pages** that contain descriptions of SSI Services, including taxonomies, policies, etc. In other words, this element can be called a SSI Service Catalogue following the ideas discussed in the [SSI Governance whitepaper](https://www.researchgate.net/publication/348325716_Decentralized_SSI_Governance_the_missing_link_in_automating_business_decisions).
- **Green Pages** that contain technical details of SSI Services, including schemas, credential definitions, etc. At the further maturity state of the SSI model, a description language, e.g. Identity Service Description Language (ISDL), can be created for these reasons. Actually, SSIDDI relies on the raw descriptions done in the DID and VC specifications.

The data model of SSI Service Registry consists of the three main classes: Organization, Service and Interface, respectively. 

The SSIDDI model is built on top of the Resourse Definition Framework (RDF) that defines a "triple" as a basic semantic construct containing three core components: Subject, Predicate and Object. In the table below, there is a schematical example of RDF relationships between the three SSIDDI classes applied to a VC issuance of some university degree.

<table>
    <thead><tr><th>Subject</th><th>Predicate</th><th>Object</th><th>Comment</th></tr></thead>
    <tbody>
      <tr><td><b>Organization</b></td><td>identifiers</td><td>12345678-a12b-34c5-d678-123456780000</td><td>Organization Identifier Bag</td></tr>    
      <tr><td>Organization</td><td>urls</td><td>http://example.edu</td><td>Discovery URLs</td></tr>         
      <tr><td>Organization</td><td>name</td><td>Example University</td><td>Legal and Commercial names</td></tr>
      <tr><td>Organization</td><td>type</td><td>Education, University</td><td>Organization Classification</td></tr>      
      <tr><td>Organization</td><td>provides</td><td><b>Service</b></td><td>A list of SSI Service References</td></tr>
      <tr><td><b>Service</b></td><td>identifiers</td><td>did:example:123456789abcdefghi</td><td>Service Identifier Bag</td></tr>
      <tr><td>Service</td><td>type</td><td>University Degree</td><td>Service Taxonomy</td></tr>  
      <tr><td>Service</td><td>policy</td><td>http://example.edu/policies/1</td><td>Legal Disclaimer and Privacy Policy</td></tr>         
      <tr><td>Service</td><td>accreditation</td><td>Organization*</td><td>Accreditated by another Organization</td></tr>         
      <tr><td>Service</td><td>implements</td><td><b>Interface</b></td><td>A list of SSI Service Interfaces</td></tr>
      <tr><td><b>Interface</b></td><td>identifiers</td><td>12345678-a12b-34c5-d678-123456781001</td><td>Interface Identifier Bag</td></tr>
      <tr><td>Interface</td><td>type</td><td>Example University's Bachelor Degree Credential</td><td>A particular interface type</td></tr>      
      <tr><td>Interface</td><td>definition</td><td>http://example.edu/credentials/1</td><td>Credential Schema and Definition</td></tr>     
    </tbody>
</table>

### Organization Structure
Organization is the top-level data structure that contains descriptive information about a public organization or enterprise it describes and the services it offers. Each Organization structure consists of:
- **identifierBag** is a list of reference structures, each of which representing a single identification.
- **categoryBag** is a list of reference structures, each of which containing a single categorization.
- **discoveryURLs** is a list of URLs that point to service discovery documents.
- **name** is a set of organization names specified in different languages.
- **description** is a set of organization descriptions in different languages.
- **contacts** is a collection of contact structures, each of which containing description, emails, phones, addresses of organization representatives.
- **publishedServices** is a list of identity services that each organization can provide.
- **subscribedServices** is a list of identity services to which each organization can be subscribed.
- **accreditaion** tbd
- **signature**: tbd

### Service Structure
The Service structure is the logical child of a single organization and contains descriptive information of a particular identity service. Each Service structure consists of:
- **id** is an identity service identifier of an (DID).
- **name** is a set of service names specified in different languages.
- **description** is a set of service descriptions in different languages.
- **categoryBag** is a list of reference structures, each of which containing a single categorization.
- **policy** is a set of service policies (terms and conditions) specified in different languages.
- **interfaces** is a list of technical descriptions for the identity services provided.
- **signature**: tbd

### Interface Structure
The Interface structure is the logical child of a single service and contains technical descriptions of an identity service. It also describes the application-specific parameters and other settings. Each Interface structure consists of:
- **id** is an interface identifier (DID).
- **description** is a set of interface descriptions in different languages.
- **accessPoint** is a string used to convey the network address suitable for invoking the service being described.
-	**tbd**
- **categoryBag** is a list of categorizations that each describes a specific aspect of a particular Interface. 
- **signature**: tbd


## Specification APIs
SSIDDI specifies a set of APIs for the service providers and consumers to interact with the SSI Service Registry:
- **Inquiry API** defines the operations for searching the SSI Service Registry and retrieving details about specific registrations.
- **Publication API** defines the operations for an identity service provider managing its entries in the SSI Service Registry.
- **Subscription API** defines the operations for an identity service provider managing its entries in the SSI Service Registry.

### Inquiry API
The Inquiry API defines the operations for searching the SSI Service Registry and retrieving details about identity services:
- **find_entity** − Returns a list of entities that match a particular set of criteria.
- **find_service** − Returns a list of services that match a particular set of criteria.
- **find_interface** − Returns a list of interfaces that match a particular set of criteria.
- **get_entityDetail** − Returns the registration information for a entity, including all SSI Services.
- **get_serviceDetail** − Returns the complete registration information for a SSI Service.
- **get_interfaceDetail** − Returns the complete registration information for an interface.

### Publication API
The Publication API defines the operations for an accredited entity managing its entries in the SSI Service Registry:
- **save_entity** − Creates or updates an entity's information contained in the SSI Service  Registry.
- **save_service** − Creates or updates information about the SSI Services that an Entity provides and subscribed.
- **save_interface** − Creates or updates the technical information about a SSI Service implementation.
- **delete_business** − Removes the given business entities from the SSI Service Registry completely.
- **delete_service** − Removes the given identity service from the SSI Service Registry completely.
- **delete_interface** − Removes the given web services technical details from the SSI Service Registry.

### Subscription API
TODO

## Technical Architecture

The SSI Service Registry architecture must contain the following features:
- Intra-domain and cross-domain interaction
- High Availability 
- Replication functionality
- Modularization that allows import new elements to the existing ones
- Performance to provide the desirable Quality of Service (QoS).


### Ontology Graphs

<img src="ssiddi_vc_lifecycle.png" width="62%" height="" />

## Opened Questions

- [NACE SKOS rev.2](nace_skos_v1.0.rdf)

