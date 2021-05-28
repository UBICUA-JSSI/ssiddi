# SSIDDI
Self-Sovereign Identity Description, Discovery and Interoperability

## Motivation
Core aspects of the Self-Sovereign Identity (SSI) model are specified in the W3C Primers related to [Decentralized IDentifier (DID)](https://www.w3.org/TR/did-core/) and [Verifiable Credential (VC)](https://www.w3.org/TR/vc-data-model/). In particular, the VC specification defines a Verifiable Data Registry responsible for "mediating the creation and verification" of all elements (identifiers, verifiable credential schemas, revocation registries, and so on) "which might be required to use verifiable credentials". We notice that the described data registry can have shortcomings due to the lack of sematic interoperability. In any practical implementation, there will inevitably arise questions on who, what and how can operate with those verifiable credentials. 

This is especially important in the decentralized verification processes where the SSI roles interact in the Issuer-Holder and Holder-Verifier pairs. Considering these interactions as verifiable credential services, an Issuer represents a service provider meanwhile Holder and Verifier are service consumers. Thus, all service-related definitions must be previously published by Issuers in order to be subsequently discovered and used by Holders and Verifiers.

For web services, a similar semantic interoperability approach based on the [Universal Description, Discovery and Interaction (UDDI)](http://uddi.xml.org/specification) speification is well known and currently in use. Although the UDDI architecture can be easily adjusted to the VC services, the UDDI data model seems obsolete and hardly transferable to [Verifiable Data Registry](https://www.w3.org/TR/vc-data-model/). In our opinion, an appropriate data model can be built using [Web Ontology Language (OWL)](https://www.w3.org/TR/owl2-syntax/).

Combining an UDDI-like registry architecture and OWL-compliant data model, we pretend to design a general solution on semantic description, discovery and interoperability for self-sovereign identity and verifiable credentials.

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

<img src="ssiddi_architecture.png" width="70%" height="" />

### Lifecycle Management
Generally, the lifecycle of verifiable credentials consists of the following stages:
1. Definitions
2. Registrations
3. Operations

## Data Model
The data model must contain the following elements:
-	White Pages (Who): Provider Description including Contact Info, DID URLs, etc. 
-	Yellow Pages (What): Service Description including Taxonomies, VC Catalogues, etc.
-	Green Pages (How): Interface Description including Technical Info, VC Classes including Schema and Credential Definitions, Policies, etc.

### Ontology Graphs

<img src="ssiddi_vc_lifecycle.png" width="70%" height="" />



