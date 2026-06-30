# Citing GA4GH Standards

**Source**: TASC  
**Recommendation**: GA4GH-REC-05  
**Title**: Citing GA4GH Standards: A mechanism for creating digital object identifiers in support of GA4GH products  
**Related GitHub issues**: [#39](https://github.com/ga4gh/TASC/issues/39), [#179](https://github.com/samtools/hts-specs/issues/179)  
**Raised by**: Susan Fairley (Chief Standards Officer - GA4GH)  
**Authors**: Chen Chen, James Eddy, Ian Fore, Francesca Frexia, Angela Page, Alex Wagner, Andy Yates, Michael Baudis, Sasha Siegel  
**Date:** 2026-07-07  
**Status:** Draft  
**Keywords**: doi, citation  
**Work Streams Impacted**: All workstreams  
**Products Affected**: None directly  

## Abstract

This recommendation provides a uniform and consistent way for citing GA4GH products and digital outputs by generation of a digital object identifier (DOI) where GA4GH is DOI prefix (`10.59756`). We follow recomemndations from CrossRef \[CROSSREF\] to create DOIs whose suffixes are obsfucated and guidance on the correct metadata to provide. This guide is written from the understanding that DOIs will be minted via the CrossRef service. The recommendation applies to GA4GH documentary outputs, including products, standards, protocols, technical specifications, white papers, and selected blog posts. It does not apply to datasets, tools, or other research resources.

## Table of contents

- [Recommendation](#recommendation)
- [Background](#background)
- [Detailed Guidance](#detailed-guidance)
- [Use Cases](#use-cases)
- [Considerations](#considerations)
- [References](#references)
- [Contributors](#contributors)

## Recommendation

Digital object identifiers (DOI) for GA4GH digital assets MUST use the GA4GH prefix `10.59756` resulting in DOIs with the following format `https://doi.org/10.59756/SUFFIX`. Registration requests MUST be submitted to the originating group's co-leads (e.g. work stream, NIF, GIF, TASC) and then to the Technical Team unless another automated minting method has been created. DOIs MUST be registered using the GA4GH approved Registration Agency, currently CrossMap. DOI suffixes MUST be an obsufcated random string with no semantic meaning. 

The `<std_designator>` metadata field SHOULD follow the format `Work Stream Acronym + Document Name`. 

The Technical Team maintain a register of assigned suffixes to avoid clashing DOIs. DOIs MAY be created for any GA4GH digital output and for any version of said digital output. Newly approved products SHOULD request and assign a DOI to their digital materials including any specific versions. DOIs MUST NOT be minted for transitional or ephemeral materials e.g. a draft specification. 

GA4GH DOIs work alongside those created by other authorties and organisations e.g. publishers, open repositories and do not replace or supplant them. GA4GH DOIs MUST NOT redirect to another DOI URI. This recommendation MUST apply to GA4GH documentary outputs and MUST NOT apply to datasets, tools or other research resources.

## Background

A way to cite GA4GH digital outputs such as specifications was originally raised in 2016 in the hts-specs repository and later picked up on in 2022. The need was to create a way to cite a version of a GA4GH product without resorting to publications (the previous way this was achieved). Being able to generate DOIs would be one way of accomplishing this. Zenodo was cited as a possible solution but that results in a disconnect between the digital object a DOI points to and where said item is really maintained. Further discussion on Slack resulted in the conclusion that GA4GH should begin to mint DOIs itself and would do through the CrossRef platform as this would support "Standards" record types \[CROSSREF_RECORDS\].

## Detailed Guidance

GA4GH documentary outputs that represent approved standards, technical specifications, protocols, products, white papers, and other significant publications MUST be assigned a Digital Object Identifier (DOI) to provide a persistent, globally unique, and citable reference. The DOI MUST serve as the canonical identifier for the document and MUST remain stable regardless of future changes to document location or hosting infrastructure.

DOIs MUST use GA4GH's registered Crossref DOI prefix (10.59756) when minting DOIs for GA4GH documentary outputs. Associated metadata MUST be deposited with Crossref and MUST include all information required to support identification and discovery of the referenced document, including title, authors, publication date, location, and the designated `<std_designator>` value.

DOI suffixes MUST be generated as opaque identifiers and MUST NOT encode semantic or document-specific meaning. Human-readable information SHOULD be represented through deposited metadata rather than through the DOI structure itself.

### Standard Designator Assignment

Each DOI registration MUST include a `<std_designator>` metadata field identifying the originating Work Stream and document context. The `<std_designator>` value MUST follow the format:


```text
<WORK_STREAM_ACRONYM>_<DOCUMENT_NAME>
```

Examples include:

```text
FEDANALYIS_WES
LSG_CRAM
CLINPHEN_PHEN
DISCOVERY_BEACONV2
TASC_TS
```

Note that over time, workstreams will change names. Use the name of the work stream at the time of minting. Work Streams SHOULD use concise and stable designator values to promote consistency across DOI registrations. The `<std_designator>` value MUST uniquely identify the document category within the context of the originating Work Stream.


### DOI Request Process

Individuals responsible for a documentary output requiring a DOI (output leads) MUST submit a DOI request through their Work Stream Leads. Work Stream Leads MUST define the metadata associated with the DOI request, including the `<std_designator>`, in collaboration with the output leads. The completed request MUST be submitted to the GA4GH Technical Team together with all required metadata. The Technical Team MUST verify that the request is legitimate and appropriate prior to DOI creation. Where uncertainty exists regarding eligibility or governance, the Technical Team MAY escalate the request to the Chief Product Officer. Following DOI registration, the Technical Team MUST provide the DOI to the GA4GH Communications Team for publication through appropriate GA4GH channels. Automated versions of this process are permitted so long as the ethos of this flow is retained.

### Metadata Management

Metadata associated with a DOI MUST accurately describe the referenced document at the time of registration. Metadata SHOULD be updated when document locations or other deposited metadata elements change. Where a document is relocated, the DOI MUST continue to resolve to the authoritative version of the document. Changes in document location MUST NOT require minting a new DOI unless a new citable object is being created.

## Use Cases

### Use case - Approved GA4GH Products

When a product is approved through the GA4GH Product Development and Approval Process, DOIs MUST be assigned to support persistent and version-specific citation. At a minimum, DOI registration SHOULD be considered for:

- The approved version of the product specification
- The current version of the product specification
- The GA4GH product page

For example, a hypothetical GKS product named *Quatsch* could use the designator `GKS_QUATSCH` to associcate DOI registrations with the product and related documentation.

### Use case - White Papers and Position Pieces

GA4GH white papers, briefing documents, and position statements SHOULD be assigned a DOI that resolves to the authoritative GA4GH-controlled version of the document. External publication through repositories such as Zenodo or bioRxiv MUST NOT prevent the creation of a GA4GH-managed DOI. For example, a Regulatory and Ethics Work Stream position paper may use a designator such as `REWS_POSITIONPIECE` to identify the publication type within DOI metadata.

### Use case - Blog Posts and Web Publications

Blog posts, announcements, and news articles that require persistent citation MAY be assigned a DOI. In these cases, the DOI SHOULD be registered using a designator associated with GA4GH web content such as `GA4GHWEB_POST`. This enables long-term citation of significant web-based publications while maintaining consistency with other GA4GH documentary outputs.

## Considerations

- This recommendation applies to citation of GA4GH documentary outputs and MUST NOT be interpreted as a general-purpose identifier framework for datasets, software implementations, APIs, schemas, or data exchanged between systems.
- Citation and machine-readable identification are distinct requirements. While a DOI provides a stable citation mechanism for publications and documentation, additional identifier mechanisms MAY be required where standards need to be referenced within APIs, service registries, metadata models, or software implementations.
- DOI assignment SHOULD be considered independently from publication venue. A document MAY be published through multiple channels while retaining a single authoritative GA4GH-managed DOI.
- Work Streams SHOULD establish clear guidance regarding the versioning strategy for documentary outputs. Readers and implementers MUST be able to determine which version of a specification is being referenced by a citation.
- Multiple citation targets MAY exist for a single GA4GH product, including an approved specification, the latest specification, supporting documentation, and the product landing page. Work Streams SHOULD ensure that each DOI resolves to a clearly defined and distinguishable citable object.
- The creation of a DOI introduces a long-term maintenance obligation. GA4GH MUST ensure that associated metadata and resolution targets remain current throughout the lifetime of the identifier.
- Changes to document hosting platforms, repository structures, website implementations, or publication locations MUST NOT result in unnecessary DOI reassignment. Existing DOIs SHOULD continue to resolve to the authoritative version of the referenced document.
- Consistency across Work Streams is a primary objective of this recommendation. Work Streams SHOULD follow a common DOI registration and metadata model to avoid the introduction of competing citation practices within GA4GH.
- DOI assignment improves citation stability but does not replace the need for product governance, version management, release processes, or publication review procedures.
- Work Streams SHOULD consider the granularity of DOI assignment carefully. Assigning too few identifiers may limit citation precision, while assigning too many may introduce unnecessary governance and maintenance overhead.

## References

- \[CROSSREF\] \- [CrossRef: a DOI issuer](https://www.crossref.org/)
- \[CROSSREF_RECORDS\] \- [CrossRef Supported Record Types](https://www.crossref.org/documentation/schema-library/markup-guide-record-types/)
- \[TASC-ADR-001\] - [TASC-ADR-001: Use CrossRef as the DOI Registration Authority for GA4GH](../adr/TASC-ADR-001.md)
- \[TASC-ADR-002\] - [TASC-ADR-002: Separate Citation Identifiers from Machine-Readable Standard Identifiers](../adr/TASC-ADR-002.md)
- \[TASC-ADR-003\] - [TASC-ADR-003: Use Opaque DOI Suffixes](../adr/TASC-ADR-003.md)
- \[TASC-ADR-004\] - [TASC-ADR-004: Use Standard Designators for DOI Metadata Classification](../adr/TASC-ADR-004.md)

## Contributors

[People who contributed to the development of this recommendation, including reviewers and discussion participants.]

| Name | Organisation |
|------|-------------|
| Chen Chen | Ontario Institute for Cancer Research, GA4GH |
| James Eddy | Sage Bionetworks |
| Ian Fore | Independent |
| Francesca Frexia | Centre for Advanced Studies, Research and Development in Sardinia (CRS4) |
| Angela Page | Broad Institute, GA4GH |
| Alex Wagner | Nationwide Children's Hospital |
| Andy Yates | HDR UK |
| Michael Baudis | University of Zurich |
| Sasha Siegel | EMBL-EBI, GA4GH |

## Notes

OpenAI ChatGPT 5.5 (June 2026) was used to interpret and reformat original Google documents into this format. All content has been reviewed for accuracy.
