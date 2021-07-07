# SSIDDI
Self-Sovereign Identity Description, Discovery and Interoperability

## Motivation
Core aspects of the Self-Sovereign Identity (SSI) model are specified in the W3C Primers related to [Decentralized IDentifier (DID)](https://www.w3.org/TR/did-core/) and [Verifiable Credential (VC)](https://www.w3.org/TR/vc-data-model/). In particular, the VC specification defines a Verifiable Data Registry (VDR) responsible for "mediating the creation and verification" of all elements (identifiers, verifiable credential schemas, revocation registries, and so on) "which might be required to use verifiable credentials". We argue that the described data registry may have significant shortcomings due to the lack of sematic interoperability. In fact, the relevant questions on who, what and how can operate with those verifiable credentials will inevitably arise in any practical implementation of [VDR](https://www.w3.org/TR/vc-data-model/).

Answering these questions is especially important within the decentralized models in which identity owners are involved into trustworthy relationships, such as VC issuance in the Issuer-Holder pair and VC verification in the Holder-Verifier pair. If we consider these processes as parts of the whole VC service, an Issuer becomes a service provider meanwhile Holder and Verifier converts to service consumers. From the interoperability point of view, all necessary service-related information must be previously published by Issuers in order to be later discovered and utilized by Holders and Verifiers.

As for the semantic interoperability related to web services, such an approach based on the [Universal Description, Discovery and Interaction (UDDI)](http://uddi.xml.org/specification) specification has been already developed. We notice that the UDDI architecture can be easily adjusted to the VC services whereas the original data model of UDDI seems to be obsolete and intransferable to [VDR](https://www.w3.org/TR/vc-data-model/). In our opinion, an appropriate and up-to-date solution should be built within the frame of [Web Ontology Language (OWL)](https://www.w3.org/TR/owl2-syntax/).

By combining an UDDI-like registry architecture with an OWL-compliant data model, we pretend to design a generalized solution on semantic description, discovery and interoperability for self-sovereign identity and verifiable credentials.

## Definitions
Responding to these issues, the SSIDDI solution introduces a generalized concept of SSI Service as an ensemble of management operations related to the digital identity and its verifiable attributes (aka verifiable credentials). Even though the Identity Management (IM) is application specific, there are a few primary and common features to be considered.

First of all, we leave out of scope the self-issued identity systems and limit our analysis only to the provider-consumer type of identity relationships. In a typical scenario, a user acquires its credentials (identity card, driving licence, university diploma, medical insurance, etc.) from an accredited public provider and then uses them in relations with other identity or business services. Within the SSI model, such a scenario implies that an identity owner, as a DID Subject and/or VC Holder, establishes legal relations with the following two roles:
- Identity Service Provider (SSIS Provider) is a public entity that is legally accredited to manage SSI Services, e.g. as DID Controller or VC Issuer. The prerequisite of previous accreditation is important from the viewpoint of legal and organizational aspects of the ecosystem governance.
- Identity Service Subscriber (SSIS Subscriber) is a public entity that is subscribed to SSI Services and utilizes them in the Access Management (AM), e.g. as DID Validator or VC Verifier, and/or Business Processes (BP). Note that, the same entity may play both roles depending on a particular context. 

SSIDDI is focused on the semantic descriptions of SSI Services and the corresponding roles. In a very general manner, the identity service lifecycle includes the following basic stages:
- Stage 1 - Definitions (aka service design): At this stage, an Identity Service Provider designs and publishes the service definitions that can be later discovered and employed by their consumers. For example, a VC Issuer works out all necessary information on the VC issuance and stores it on a public registry. In its turn, the future VC Holders and VC Verifiers discover this information in order to make their business decisions. 
- Stage 2 - Registrations (aka service implementation, onboaring or enrolment): At this stage, the above-mentioned Identity Service Provider registers consumers in accordance with the previously published service descriptions. For example, a VC Issuer registers identity and attributes of a DID Subject - VC Holder. Moreover, the already registered VC Verifiers can subscribe to particular SSI Services of the particular provider.
- Stage 3 - Operations (aka service usage): At this stage, the Identity Service Provider and the consumers interoperate using the service definitions and registrations made at the previous stages. For example, the Issuer-Holder and Holder-Verifier pairs interact within the frames of VC issuance-acquisition and presentation-verification processes, respectively.

The technical interoperability between digital agents relies on the Decentralized Public Key Infrastructure (DPKI) and two types of registries:
- Digital Wallet as a private component of DPKI for storing individual cryptographic material and other digital assets of its owner. 
- Identity Registry as a public component of DPKI for storing the technical information (DIDs and DID documents) and cryptographic states of all DID Subjects registered in a particular ecosystem. Distributed Ledger Technology (DLT) provides the best-suited solution for implementing the Identity Registry.

To meet the semantic requirements of SSI Services, the SSIDDI solution defines an Identity Service Registry (SSIS Registry) for storing the semantic and technical descriptions of identity services and the relevant public entities. This registry type is inspired by the Universal Description, Discovery and Integration (UDDI) framework which is the international standard for semantic interoperability of web services.

From the VC Data Model [] viewpoint, the two registries, i.e. Identity Registry and Identity Service Registry, together represent a complete implementation of Verifiable Data Registry. However, following to the Separation of Concerns (SoC) principle, we argue that such a splitted registry solution brings multiple advantages in terms of:
- Guaranteeing pseudonymisation through separating identifiers and identity attributes.  
- Decoupling the service description from the service execution.
- Empowering the semantic techniques for describing identity and verifiable credentials.
- Enabling reusability of identity services and their components.
- Introducing a desired basis for the legal and organizational levels of interoperability.
- Simplifying the structure and maintenance of distributed ledgers.



## Key Requirements
**Ontology Model:**
- For legal persons’ data only (Privacy-by-Design)
- Multi-context, multi-language and multi-purpose
- Based on OWL / RDFS graphs
- Simple and partially flexible

**Registry Architecture:**
- Lightweight design (APIs)
- Public reading, Authorized writing (TAs, ACs, etc.)
- Highly-Available and Synchronized Registries

**Search Engine:**
- Query languages (GraphQL, SPARQL)
- Multi-format support (JSON, XML)
- Effective and Efficient

## Architecture

<img src="ssiddi_architecture.png" width="62%" height="" />

### Credential Lifecycle
Generally, the lifecycle of any identity-related service (in particular, verifiable credentials) can be divided into the following stages:
1. **Definitions**: At this stage, a provider develops and publishes service definitions. For example, a provider of Verifiable Credentials (Issuer) works out all necessary information (schemes, credential definitions, policies, etc.) to be discovered and used later by VC consumers (Holder and Verifier).
2. **Registrations** (_aka_ onboarding or enrolment): At this stage, the provider registers consumers (aka subscribers) of the published services. For example, the Issuer registers Holders, as consumers of VC services.
3. **Operations**: At this stage, the provider and the consumers interoperate using the service definitions and registrations made at the previous stages. Thus, the provider-consumer pairs, namely Issuer-Holder and Holder-Verifier, interact during the VC issuance and verification processes, respectively.

## Data Model
The data model must contain the following elements:
-	White Pages (Who): Provider Description including Contact Info, DID URLs, etc. 
-	Yellow Pages (What): Service Description including Taxonomies, VC Catalogues, etc.
-	Green Pages (How): Interface Description including Technical Info, VC Classes including Schema and Credential Definitions, Policies, etc.

### Ontology Graphs

<img src="ssiddi_vc_lifecycle.png" width="62%" height="" />

## Opened Questions



