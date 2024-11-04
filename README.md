# ProMoTe

### Disclaimer 
ProMoTe is under active development and evaluation from both the academic community and our industrial partners. If you intend to use this standard, feel free to reach out with questions and or feedback.

### License
This document is licensed under the [Creative Commons BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode) license.

## Table of Contents

<!-- toc -->

- [ProMoTe](#promote)
    - [Disclaimer](#disclaimer)
    - [License](#license)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [ProMoTe from a bird's-eye view](#promote-from-a-birds-eye-view)
  - [How to read and use this document.](#how-to-read-and-use-this-document)
  - [External Documents](#external-documents)
  - [Specification](#specification)
    - [Class: Resource](#class-resource)
      - [Property: Title](#property-title)
      - [Property: Resource Provider](#property-resource-provider)
      - [Property: Domain](#resource-property-domain)
      - [Property: Identifier](#property-identifier)
      - [Property: Description](#resource-property-description)
      - [Property: Date Issued](#property-date-issued)
      - [Property: Date Modified](#property-date-modified)
      - [Property: Resource Type](#property-resource-type)
      - [Property: Keyword](#property-keyword)
      - [Property: Language](#property-language)
      - [Property: Institutional Knowledge](#resource-property-institutional-knowledge)
      - [Property: Newer Version](#property-newer-version)
      - [Property: Older Version](#property-older-version)
      - [Property: Consumes](#resource-property-consumes)
      - [Property: Source System](#resource-property-source-system)
      - [Property: Is Consumed By](#resource-property-consumed-by)
      - [Property: Estimated Value](#property-estimated-value)
      - [Property: Qualified Attribution](#property-qualified-attribution)
      - [Property: Catalog Record](#resource-property-catalog-record)
    - [Class: Domain](#class-domain)
      - [Property: Resource](#property-resource)
      - [Property: Domain Knowledge](#property-domain-knowledge)
      - [Property: Domain Owner](#domain-property-domain-owner)
      - [Property: Domain Participant](#domain-property-domain-participant)
    - [Class: Institutional Knowledge](#class-institutional-knowledge)
      - [Property: Defining Domain](#property-defining-domain)
      - [Property: Knowledge URI](#property-knowledge-uri)
    - [Class: Data Product](#class-data-product)
      - [Property: Data Provider](#property-data-provider)
      - [Property: DataAsset](#property-data-asset)
      - [Property: Output Port](#data-product-property-output-port)
      - [Property: Input Port](#property-input-port)
      - [Property: Control Port](#property-control-port)
      - [Property: Transformation Logic](#data-product-property-transformation-logic)
      - [Property: Enfocement Logic](#data-product-property-enforcement-logic)
    - [Class: Use Case](#class-use-case)
      - [Property: Planned End Date](#property-planned-end-date)
    - [Class: Data Asset](#class-data-asset)
      - [Property: Distribution](#data-asset-property-distribution)
      - [Property: Logical Schema](#data-asset-property-logical-schema)
      - [Property: Data Product](#data-asset-property-data-product)
    - [Class Distribution](#class-distribution)
      - [Property: Output Port](#distribution-property-output-port)
      - [Property: Physical Schema](#distribution-property-physical-schema)
      - [Property: Description](#distribution-property-description)
    - [Class: Output Port](#class-output-port)
      - [Property: Exposes Distribution](#property-exposes-distribution)
      - [Property: Data Product](#property-exposes-data-product)
      - [Property: endpointURI](#property-endpoint-uri)
      - [Property: Consume Instructions](#property-consume-instructions)
      - [Property: Consumed By](#output-port-property-consumed-by)
      - [Property: Data Contract](#output-port-property-data-contract)
      - [Property: Access Management](#output-port-access-management)
    - [Class: Data Contract](#class-data-contract)
      - [Property: Provider Promise](#property-provider-promise)
      - [Property: Consumer Promise](#property-consumer-promise)
      - [Property: Policy](#data-contract-property-policy)
      - [Property: Service Level Agreement](#property-service-level-agreement)
      - [Property: Service Level Objective](#property-service-level-objective)
    - [Class: Input Port](#class-input-port)
      - [Property: Description](#input-port-property-description)
      - [Property: Data Product](#input-port-property-corresponding-data-product)
      - [Property: Consumes](#input-port-property-consumes)
      - [Property: Source System](#-property-source-system-)
      - [Property: Data Contract](#input-port-property-data-contract)
      - [Property: Physical Schema](#input-port-property-physical-schema)
    - [Class: Control Port](#class-control-port)
      - [Property: Description](#control-port-property-description)
      - [Property: Data Product](#control-port-property-corresponding-data-product)
      - [Property: Managed Policy](#control-port-property-policy)

<!-- tocstop -->

## Introduction
ProMoTe is a data Product Modelling Template for describing data products in a data mesh environment in a technology-independent manner. It was originally designed by researchers collaborating with large European companies that were looking to transition from a centralised, monolithic data landscape towards a more decentralised data-mesh (like) data landscape. ProMoTe is grounded in academic literature and industrial practice. It extends well-established ontologies (primarily [DCAT](https://www.w3.org/TR/vocab-dcat-2/)) in a way that is intended to help create data products that achieve the DAUTNIVS+ non-functional requirements (Discoverability, Addressability, Understandability, Truthful & Trustworthy, Natively Accessible, Interoperable, Valuable and Secure + Feedback-Driven). The first eight of these are described extensively in the original data mesh [book](https://www.oreilly.com/library/view/data-mesh/9781492092384/), published by Dehghani in 2020, whereas being Feedback-Driven originates from a desire to develop data products in an agile manner, akin to how DevOps has become standard practice for software development.

## ProMoTe from a bird's-eye view
The figure below shows an overview in UML of the classes described in ProMoTe and the relations that can be used to describe them; the classes and relations are also described in detail below. Additionally, whenever relevant, we describe how the different classes and properties contribute to achieving DAUTNIVS+ in the "Motivation" field. At a high level ProMoTe extends the [dcat:Resource](https://www.w3.org/TR/vocab-dcat-2/#Class:Resource) class with a subclass: [pmt:Resource](#class-resource). pmt:Resources come in three varieties: the [pmt:DataAsset](#class-dataasset), which is a subclass of [dct:Dataset](https://www.w3.org/TR/vocab-dcat-2/#Class:Dataset); the [pmt:Dataproduct](#class-data-product), which is the architectural quantum of a data mesh and the main focus of ProMoTe; and the [pmt:UseCase](#class-use-case), that describes how the data is consumed. Data Products make available one or more data sets. Each data set has one or more physical representations (distributions), which are exposed throught output ports.

Each resource is managed within a [pmt:Domain](#class-domain) that maintains semantic domain knowledge in [pmt:InstitutionalKnowledge](#class-institutional-knowledge). Data products ingest data through one or more [pmt:InputPort](#class-input-port)s and are governed through policies that are managed through [pmt:ControlPort](#class-control-port)s. Finally, data products make available one or more [dct:Distribution](#class-distribution)s of [pmt:DataAsset](#class-dataasset)s through an associated [pmt:OutputPort](#class-output-port). For each output port, an associated [pmt:DataContract](#class-data-contract) establishes the conditions that apply when consuming the underlying data.

## How to read and use this document.
With ProMoTe, you can help define metadata models to describe data products in the data catalogue of your data mesh, or it can help you determine what a data product should look like within your organisation and whether different maturity levels that contain various aspects exist. An academic paper illustrating these use cases of ProMoTe is underway. The core concepts of ProMoTe are also available as an ontology in a .owl-file, which can be found [here](https://github.com/Stefan-Driessen/ProMoTe/blob/main/ProMoTe.owl).

The key words MAY, MUST, MUST NOT, and SHOULD in this document are to be interpreted as described in [BCP 14](https://tools.ietf.org/html/bcp14) [RFC2119](https://tools.ietf.org/html/rfc2119) [RFC8174](https://tools.ietf.org/html/rfc8174) when, and only when, they appear in all capitals, as shown here.

## External Documents
ProMoTe is compliant with and incorporates terms from the [DCAT vocabulary](), which in turn makes use of [other vocabularies](https://www.w3.org/TR/vocab-dcat-2/#namespaces). This means that ProMoTe can both extend existing implementations using these standards and be extended with terminology from those vocabularies.

## Specification
![UML](https://raw.githubusercontent.com/Stefan-Driessen/ProMoTe/main/ProMoTe_v5.3.png)

### Class: Resource
The following properties are specific to this class: [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution), [catalog record](#resource-property-catalog-record).

<!-- Resources MUST have a [pmt:domain](#resource-property-domain") and a [dct:identifier](#property-identifier). Resources SHOULD have a [pmt:resourceProvider](#property-resource-provider).

Resources MAY be extended with one or more [pmt:consumes](#resource-property-consumes), [pmt:sourceSystem](#resource-property-consumes), and [consumed by](#resource-property-consumed-by) relations. Depending on the application, resources MAY be extended with a [dct:catalogRecord](https://www.w3.org/TR/vocab-dcat-2/#Class:Catalog_Record)-->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-resource">pmt:Resource</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A data product, data asset or use case that can be described on a data catalog.</td>
    </tr>
    <tr>
      <td>Subclass of:</td>
      <td><a href="https://www.w3.org/TR/vocab-dcat-2/#Class:Resource">dcat:Resource</a></td>
    </tr>
    <tr>
      <td>Comment</td>
      <td>The class of all distributions, data assets, data products and use cases that exist and are registered in the data catalog of the data mesh.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>If the data catalog also contains information on data sevices, this class can be used in conjunction with <a href="https://www.w3.org/TR/vocab-dcat-2/#Class:Data_Service">dcat:DataService</a>.</td>
    </tr>
  </tbody>
</table>

#### Property: Title
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/terms/title">dct:title</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A name given to the item.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="http://www.w3.org/2000/01/rdf-schema#Literal">rdfs:Literal</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>A title contributes to Discoverability, Addressability (if unique), and Understandability.</td>
    </tr>
  </tbody>
</table>

#### Property: Resource Provider
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-resource-provider">pmt:resourceProvider</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The agent responsible for providing the resource.</td>
    </tr>
    <tr>
      <td>SubProperty of:</td>
      <td><a href="http://purl.org/dc/terms/publisher">dct:publisher</a></td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="http://xmlns.com/foaf/0.1/#term_Agent">foaf:Agent</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Resource Providers are either data product providers or use case providers.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Resource providers are necessary to achieve Addressability, as well as making the development of the resource Feedback-Driven.</td>
    </tr>
  </tbody>
</table>

<h4 id="resource-property-domain"> Property: Domain</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#resource-property-domain">pmt:domain</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The domain from which the resource stems.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-domain">pmt:Domain</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Domains make resources more Addressable and Discoverable.</td>
    </tr>
  </tbody>
</table>

#### Property: Identifier
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/elements/1.1/identifier">dct:identifier</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>An unambiguous reference to the resource within a given context.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Common values are a urn or url.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>A unique identifier is a necessity for Addressability.</td>
    </tr>
  </tbody>
</table>

<h4 id="resource-property-description"> Property: Description </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/elements/1.1/description">dct:description</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A human-readable account of the resource.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Descriptions make the resource more Understandable. Additionally, descriptions can contribute to Discoverability if they are indexed in a data catalog.</td>
    </tr>
  </tbody>
</table>

#### Property: Date Issued
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/terms/issued">dct:issued</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>Date when the resource was first made available for consumers.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="https://www.w3.org/2001/XMLSchema">xsd:date</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Adding the date issued contributes to the Understandability of the resource.</td>
    </tr>
  </tbody>
</table>

#### Property: Date Modified
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/terms/modified">dct:modified</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>Date when the resource was last modified.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="https://www.w3.org/2001/XMLSchema">xsd:date</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>The date modified contributes to the Understandability, Interoperability, and Trustworthiness & Truthfulness.</td>
    </tr>
  </tbody>
</table>

#### Property: Resource Type
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-resource-type">pmt:type</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The type of the resource.</td>
    </tr>
    <tr>
      <td>subPropertyOf:</td>
      <td><a href="http://purl.org/dc/terms/type">dct:Type</a></td>
    </tr>
    <tr>
      <td>Range:</td>
      <td>{<a href="#class-data-product">pmt:DataProduct</a>, <a href="#class-use-case">pmt:UseCase</a>, <a href="#class-data-asset">pmt:DataAsset</a>}</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Describing the type of resource contributes to Discoverability and Understandability.</td>
    </tr>
  </tbody>
</table>

#### Property: Keyword
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="https://www.w3.org/ns/dcat#keyword">dcat:keyword</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A keyword or tag describing the resource.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="http://www.w3.org/2000/01/rdf-schema#Literal">rdfs:Literal</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Keywords contribute primarily to Discoverability and, to a lesser extent, to Understandability.</td>
    </tr>
  </tbody>
</table>

#### Property: Language
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="https://www.w3.org/ns/dcat#keyword">dct:language</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A keyword or tag describing the resource.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="http://www.w3.org/2000/01/rdf-schema#Literal">rdfs:Literal</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Describing the language of the resource contributes primarily to Understandability.</td>
    </tr>
  </tbody>
</table>

<h4 id="resource-property-institutional-knowledge">Property: Institutional Knowledge</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#resource-property-institutional-knowledge">pmt:institutionalKnowledge</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>Existing terminology within the organisation or domain that relates to a <a href="#class-resource">pmt:Resource</a>.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-institutional-knowledge">pmt:InstitutionalKnowledge</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Institutional knowledge contributes to Discoverability, Understandability and Interoperability.</td>
    </tr>
  </tbody>
</table>

#### Property: Newer Version
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-newer-version">pmt:hasNewVersion</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A newer version of the data product, which will eventually replace this version.</td>
    </tr>
    <tr>
      <td>Comment:</td>
      <td>This property is used for versioning, keeping an older version available helps consumers of the resources by giving them time to migrate to the new resource.</td>
    </tr>
    <tr>
      <td>isDefinedBy:</td>
      <td><a href="http://purl.org/dc/terms/hasVersion">dct:hasVersion</a></td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-resource">pmt:Resource</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Recommended usage is to describe until when this resource is available in the <a href="#resource-property-description">dct:description</a> property.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Versioning in general contributes to Discoverability, Addressability, Understandability, Truthfulness & Trustworthiness, and Interoperability.</td>
    </tr>
  </tbody>
</table>

#### Property: Older Version
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-older-version">pmt:hasOldVersion</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>An older version of the data product, which this version is replacing.</td>
    </tr>
    <tr>
      <td>Comment:</td>
      <td>This property is used for versioning, keeping an older version available helps consumers of the resources by giving them time to migrate to the new resource.</td>
    </tr>
    <tr>
      <td>isDefinedBy:</td>
      <td><a href="http://purl.org/dc/terms/isVersionOf">dct:isVersionOf</a></td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-resource">pmt:Resource</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Recommended usage is to describe when the old resource is no longer available in the <a href="#resource-property-description">dct:description</a> property.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Versioning in general contributes to Discoverability, Addressability, Understandability, Truthfulness & Trustworthiness, and Interoperability.</td>
    </tr>
  </tbody>
</table>

<h4 id="resource-property-consumes"> Property: Consumes </h4>
  <table>
    <thead>
      <tr>
        <th width="240px"><strong>Property:</strong></th>
        <th width="760px"><span style="font-weight:normal"><a href="#resource-property-consumes">pmt:consumes</a></span></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Definition</td>
        <td>A resource or output port of a data product which is consumed to create or maintain this resource.</td>
      </tr>
      <tr>
        <td>Range</td>
        <td>{<a href="#class-resource">pmt:Resource</a>, <a href="#class-output-port">pmt:OutputPort</a>}</td>
      </tr>
      <tr>
        <td>Usage Note:</td>
        <td>This property is an inverse property of <a href="#resource-property-consumed-by">pmt:isConsumedBy</a></td>
      </tr>
      <tr>
        <td>Motivation:</td>
        <td>In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
      </tr>
    </tbody>
  </table>

<h4 id="resource-property-source-system"> Property: Source System </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#resource-property-source-system">pmt:sourceSystem</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>An IT system that generates or stores data in this resource, such as a specific data warehouse, data lake, or database.</td>
    </tr>
    <tr>
    <tr>
      <td>Domains</td>
      <td>{<a href="#class-data-asset">pmt:DataAsset</a>, <a href="#class-distribution">pmt:Distribution</a>}</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This property can be used to describe either where a specific data set or distribution lives, or give information on the input port of a data product.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
    </tr>
  </tbody>
</table>
  
<h4 id="resource-property-consumed-by"> Property: Consumed By </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#resource-property-consumed-by">pmt:isConsumedBy</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>An input port of a data product or a use case that consumes this data product.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-input-port">pmt:InputPort</a>, <a href="#class-use-case">pmt:UseCase</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Linking consuming data products helps establish data lineage, whereas linking use cases to data products improves the discoverability, understandability of the data product and helps establish a <a href="#property-estimated-value">pmt:estimatedValue</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
      </tr>
    <!-- <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#property-consumes">pmt:consumes</a></td>
    </tr> -->
  </tbody>
</table>

#### Property: Estimated Value
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-estimated-value">pmt:estimatedValue</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>An indication of the value the resource provides for the company.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Ideally the estimated value is backed by a quantifier, such as money or manhours saved. Otherwise a qualitative description of the value provided can be provided.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Explicitly including an estimated value is necessary for establishing that a resource is Valuable.</td>
    </tr>
  </tbody>
</table>

#### Property: Qualified Attribution
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="https://www.w3.org/TR/prov-o/#qualifiedAttribution">prov:qualifiedAttribution</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A link to an agent, other than the <a href="#property-resource-provider">pmt:resourceProvider</a>, that is bears some responsibility for the resource.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Qualified attributions are useful when ownership is split amongst several owners, such as a business owner and a technical owner.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Qualified Attributions contribute to the Addressability of the resource.</td>
    </tr>
  </tbody>
</table>

<h4 id="resource-property-catalog-record">Property: Catalog Record</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal">pmt:catalogRecord</span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The record describing this resource in a data catalog</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="https://www.w3.org/TR/vocab-dcat-2/#Class:Catalog_Record">dcat:CatalogRecord</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Catalog records contribute to Discoverability, Addressability, Understandability, Interoperability and Value.</td>
    </tr>
  </tbody>
</table>

### Class: Domain
The following properties are specific to this class: [resource](#property-resource), [domain knowledge](property-domain-knowledge), [domain owner](#domain-property-domain-owner), [domain participant](#domain-property-domain-participant).

<!-- Domains SHOULD have at least one [pmt:resource](#property-resource). Domains MAY be extended with owners or other responsible actors through a [pmt:qualifiedAttribution](#property-qualified-attribution) relation. -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-domain">pmt:Domain</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The organisational sphere of knowledge and activity from which the data originates.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Aligning data and software with domains is one of the primary concerns of building a data mesh and domain-driven design in general.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Domains make resources more Addressable and Discoverable.</td>
    </tr>
  </tbody>
</table>

#### Property: Resource
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-resource">pmt:hasResource</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A resource offered in the domain.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td>[pmt:Resource](#class-resource)</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#resource-domain">pmt:domain</a></td>
    </tr>
  </tbody>
</table>

<h4 id="property-domain-knowledge"> Property: Domain Knowledge </h4>
  <table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-domain-knowledge">pmt:domainKnowledge</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>Existing terminology within the organisation or domain that relates to a <a href="#class-resource">pmt:Resource</a>.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-institutional-knowledge">pmt:InstitutionalKnowledge</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#property-defining-domain">pmt:definingDomain</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Institutional knowledge contributes to Discoverability, Understandability and Interoperability.</td>
    </tr>
  </tbody>
</table>

<h4 id="domain-property-domain-owner"> Property: Domain Owner </h4>
  <table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#domain-property-domain-owner">pmt:domainOwner</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The person who carries the high-level responsibility for domain, the business processes in it and the data they generate.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="http://xmlns.com/foaf/0.1/#term_Agent">foaf:Agent</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Domain owners help assign responsibility for the different data products, which contributes to Addressability.</td>
    </tr>
  </tbody>
</table>

<h4 id="domain-property-domain-participant"> Property: Domain Participant </h4>
  <table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#domain-property-domain-participant">pmt:domainParticipant</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A person who is active within the domain.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="http://xmlns.com/foaf/0.1/#term_Agent">foaf:Agent</a></td>
    </tr>
  </tbody>
</table>

### Class: Institutional Knowledge
The following properties are specific to this class: [defining domain](#property-defining-domain), [knowledge URI](#property-knowledge-uri).

<!-- Institutional Knowledge MAY be extended with owners or other responsible actors through a [pmt:qualifiedAttribution](#property-qualified-attribution) relation. -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-defining-domain">pmt:InstitutionalKnowledge</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>Superclass of terminology within the organisation or domain that can be related to a <a href="#class-resource">pmt:Resource</a>.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Examples include how the data relates to specifically defined terms, business objects or business processes.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Recommended usage is to organise institutional knowledge in (existing) ontologies or business glossaries.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Institutional knowledge contributes to Discoverability, Understandability and Interoperability.</td>
    </tr>
  </tbody>
</table>

#### Property: Defining Domain
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-defining-domain">pmt:definingDomain</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The domain that defines and maintains the institutional knowledge.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#domain-property-institutional-resource">pmt:institutionalKnowledge</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>It is possible that a piece of institutional knowledge is maintained on an organisation-wide level, rather than on a domain-level, but there should still be a domain responsible for maintining organisation-wide knowledge.</td>
    </tr>
  </tbody>
</table>

  #### Property: Knowledge URI
  <table>
    <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-knowledge-uri">pmt:knowledgeURI</a></span></th>
    </tr>
    </thead>
    <tbody>
      <tr>
        <td>Definition:</td>
        <td>A link to documentation about the institutional knowledge.</td>
      </tr>
      <tr>
        <td>Usage Note:</td>
        <td>Best practice is to store institutional knowledge in a business glossary or domain ontologies.</a></td>
      </tr>
    </tbody>
  </table>

### Class: Data Product
The following properties are specific to this class: [data provider](#property-data-provider), [data asset](#property-data-asset), [output port](#data-product-property-output-port), [input port](#property-input-port), [control port](#property-control-port), [transformation logic](#data-product-property-transformation-logic), [enforcement logic](#data-product-property-enforcement-logic).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [pmt:resourceProvider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#resource-property-consumes),  [consumed by](#resource-property-consumed-by), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

<!-- Data Products MUST have a [pmt:dataProvider](#property-data-provider) and at least one [pmt:dataset](#property-dataset), [pmt:outputPort](#data-product-property-output-port) and [pmt:inputPort](#property-input-port). Data Products SHOULD have at least one [pmt:consumedBy](#resource-property-consumed-by). A data products [pmt:type](#property-resource-type) MUST NOT be anything other than "Data Product". -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-data-product">pmt:DataProduct</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A data product, in a data mesh environment.</td>
    </tr>
    <tr>
      <td>Subclass of:</td>
      <td><a href="#class-resource">pmt:Resource</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>The class of all data products that exist and are registered in the data catalog of the data mesh.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This class describes all everything that holds true across all underlying data assets, distributions, and output ports in the data product.</td>
    </tr>
  </tbody>
</table>

#### Property Data Provider
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-data-provider">pmt:dataProvider</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The actor responsible for providing the data product.</td>
    </tr>
    <tr>
      <td>SubPropertyOf:</td>
      <td><a href="#property-resource-provider">pmt:resourceProvider</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Data providers are essential to achieve Addressability, as well as making the development of the resource Feedback-Driven.</td>
    </tr>
  </tbody>
</table>

#### Property: Data Asset
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-data-asset">pmt:dataAsset</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A data asset that is offered through this data product.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-data-asset">pmt:Data Asset</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#property-offered-in-data-product">pmt:offeredInDataProduct</a></td>
    </tr>
  </tbody>
</table>

<h4 id="data-product-property-output-port"> Property: Output Port </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#data-product-property-output-port">pmt:outputPort</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>An output port that exposes a distribution of this data product.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-output-port">pmt:OutputPort</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#property-exposes-data-product">pmt:exposesDataProduct</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Output ports make different distributions of a data product's data assets Natively Accessible. Additionally, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability. </td>
    </tr>
  </tbody>
</table>

#### Property: Input Port
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-input-port">pmt:inputPort</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>An input port through which data is ingested into this data product.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-input-port">pmt:InputPort</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
    </tr>
  </tbody>
</table>

#### Property: Control Port
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-control-port">pmt:controlPort</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A control port through which the policies of this data product are managed.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-control-port">pmt:ControlPort</a></td>
    </tr>
  </tbody>
</table>

<h4 id="data-product-property-transformation-logic">Property: Transformation Logic</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#data-product-property-transformation-logic">pmt:transformationLogic</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The logic or code used to transform data coming in from the input ports of the data product to the distributions that are exposerd through the output ports.</td>
    </tr>
    <!-- <tr>
      <td>Motivation:</td>
      <td></td>
    </tr> -->
  </tbody>
</table>

<h4 id="data-product-property-enforcement-logic">Property: Enfocement Logic</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#data-product-property-enforcement-logic">pmt:enforcementLogic</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The logic or code used to (semi-)automatically enforce the policies that govern the data product.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Automating enforcement logic contributes to the Truthfulness & Trustworthiness of the data product.</td>
    </tr>
  </tbody>
</table>

### Class: Use Case
The following property is specific to this class: [planned end date](#property-planned-end-date).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#resource-property-consumes), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

<!-- Use cases MUST have at least one [pmt:consumes](#resource-property-consumes) property to indicate which data asset or output port they consume. Use cases SHOULD have a [pmt:estimatedValue](#property-estimated-value) and a [pmt:plannedEndDate](#property-planned-end-date). -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-use-case">pmt:UseCase</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A use case of a data product, in a data mesh environment.</td>
    </tr>
    <tr>
      <td>Subclass of:</td>
      <td><a href="#class-resource">pmt:Resource</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is the class of all use cases that consume data products and are registered in the data catalog of the data mesh.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>If use cases generate new data, they can, over time also lead to new data products.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Explicitly tracking use cases contributes to Discoverability, Understandability, Interoperability, Value and Feedback-Driven development.</td>
    </tr>
  </tbody>
</table>


#### Property: Planned End Date
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-planned-end-date">pmt:plannedEndDate</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The date by which the use case plans to stop consuming data products.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Keeping track of a planned end date helps with data product maintenance. There is no need to put effort into maintaining a data product if there are no active use cases.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>If there is no foreseeable end date, the planned end date can be indefinite.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Planned end dates of use cases are important for establishing Value and achieving Feedback-Driven development.</td>
    </tr>
  </tbody>
</table>

### Class: Data Asset
The following properties are specific to this class: [distribution](#data-asset-property-distribution), [logical](#data-asset-property-logical-schema), [data product](#data-asset-property-data-product).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#resource-property-consumes), [consumed by](#resource-property-consumed-by), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

The following properties are inherited from the super-class [dcat:Dataset](https://www.w3.org/TR/vocab-dcat-2/#Class:Dataset): [spatial/geographic coverage](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_spatial), [spatial resolution](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_spatial_resolution), [temporal coverage](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_temporal), [temporal resolution](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_temporal_resolution).

<!-- Datasets SHOULD have a [pmt:logicalSchema](#dataset-property-logical-schema). Datasets SHOULD be extended with additional properties from the superclass [dcat:Dataset](http://www.w3.org/ns/dcat#Dataset) as needed by context. -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-data-asset">pmt:DataAsset</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A collection of data that can be described by a single logical schema and be consumed in one or more techincal representations (distributions) through one or more output ports.</td>
    </tr>
    <tr>
      <td>Sub-class of:</td>
      <td><a href="#class-resource">pmt:Resource</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This class describes the conceptual dataset. One or more representations might be available, with differing schematic layouts and formats or serializations.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>A data asset can exist as a precursor to  a data product and evolve to become a fully mature data produt over time. Not every data set needs to become a fully function data product however. Additionally, it is possible for a single data product to provide (access to) multiple data assets.</td>
    </tr>
  </tbody>
</table>

<h4 id="data-asset-property-distribution"> Property: Distribution </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://www.w3.org/ns/dcat#distribution">dcat:distribution</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A physical manifestion of (a subset of) the data asset.</td>
    </tr>
  </tbody>
</table>
  
<h4 id="data-asset-property-logical-schema"> Property: Logical schema</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#data-asset-property-logical-schema">pmt:logicalSchema</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A description of the data structure and internal relations at the data asset-level.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Logical schemas describe the structure of data that holds true across different distributions of the data asset. Structural descriptions of different distributions are described in <a href="#property-technical-schema">pmt:technicalSchema</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Logical schemas contribute to Understandability and Interoperability.</td>
    </tr>
  </tbody>
</table>
  
<h4 id="data-asset-property-data-product"> Property: Data Product </h4>  
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#data-asset-property-data-product">pmt:offeredInDataProduct</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A data product that makes this data asset available for consumption.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-data-procut">pmt:DataProduct</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#property-data-asset">pmt:dataAsset</a></td>
    </tr>
  </tbody>
</table>
  
### Class: Distribution
The following property is specific to this class: [technical schema](#property-technical-schema).
The following property is shared with the [pmt:DataProduct](#class-data-product) class: [output port](#distribution-property-output-port). The following properties are shared with the [pmt:Resource](#class-resource) class: [title](#property-title), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [source system](#resource-property-source-system), [consumed by](#resource-property-consumed-by), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

The following properties are inherited from the super-class [dcat:Distribution](https://www.w3.org/TR/vocab-dcat-2/#Class:Distribution): [spatial/geographic coverage](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_spatial), [spatial resolution](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_spatial_resolution), [temporal coverage](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_temporal), [temporal resolution](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_temporal_resolution).

<!-- Distributions SHOULD have a [pmt:technicalSchema](#property-technical-schema) -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-distribution">pmt:Distribution</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A technical collection of data representating one or more data assets. Data assets might be available in multiple serializations that may differ in various ways, including natural language, media-type or format, schematic organization, temporal and spatial resolution, level of detail or profiles (which might specify any or all of the above). A distribution might also combine information from multiple data assets.</td>
    </tr>
    <tr>
      <td>Subclass-of:</td>
      <td><a href="http://www.w3.org/ns/dcat#Distribution">dcat:Distribution</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This represents a general availability of a dataset. It implies no information about the actual access method of the data, which is described in <a href="#class-output-port">pmt:OutputPort</a>.</td>
    </tr>
  </tbody>
</table>

<h4 id="distribution-property-output-port">Output Port</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#distribution-property-output-port">pmt:correspondingOutputPort</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>An output port that exposes this distribution.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-output-port">pmt:OutputPort</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#output-port-property-distribution">pmt:exposesDistribution</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Output ports make different distributions of a data product's data assets Natively Accessible. Additionally, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability. </td>
    </tr>
  </tbody>
</table>
  
<h4 id="distribution-property-physical-schema">Property: Physical Schema</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#distribution-property-physical-schema">pmt:physicalSchema</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A description of the data structure and internal relations at the distribution-level.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Physical schemas describe the structure of data of a specific <a href="#class-distribution">distribution</a> of a <a href="#class-data-asset">pmt:DataAsset</a>. Structural descriptions that hold true across all distributions of a data asset are described in <a href="#data-asset-property-logical-schema">pmt:logicalSchema</a></td>
  </tr>
  <tr>
      <td>Motivation:</td>
      <td>Physical schemas help with Understandability and Interoperability.</td>
    </tr>
  </tbody>
</table>
  
<h4 id="distribution-property-description"> Property: Description</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/elements/1.1/description">dct:description</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A human-readable account of the distribution.</td>
    </tr>
  </tbody>
  <tr>
    <td>Motivation:</td>
    <td>Adding a description of the distribution improves Understandability, and potentially Discoverability and Interoperability. </td>
  </tr>
</table>

### Class: Output Port
The following properties are specific to this class: [distribution](#output-port-property-distribution), [data product](#output-port-property-data-product).

<!-- Output Ports MUST have a [pmt:exposesDistribution](#property-exposes-distribution) and a [pmt:exposesDataProduct](#output-port-property-data-product). Output Ports SHOULD have [pmt:consumeInstructions](#property-consume-instructions), [pmt:dataContract](#property-data-contract), and at least one [pmt:consumedBy](#output-port-property-consumed-by). -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-output-port">pmt:OutputPort</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>An output port of a data product that exposes a specific representation.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Output ports represent the various ways in which data products expose their data. For example, data can be made available through a download link, a SQL-based API or a kafka-stream.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Output ports are necessary for achieving Native Accessability.</td>
    </tr>
  </tbody>
</table>

#### Property: Exposes Distribution
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-exposes-distribution">pmt:exposesDistribution</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The distribution that is exposed for consumption through this output port.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="https://www.w3.org/TR/vocab-dcat-2/#Class:Distribution">dcat:Distribution</a></td>
    </tr>
  </tbody>
</table>
 
#### Property: Exposes Data Product
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-exposes-data-product">pmt:exposesDataProduct</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The data product that this output port exposes for consumption.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is an inverse property of <a href="#data-product-property-output-port">pmt:outputPort</a></td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-data-product">pmt:DataProduct</a></td>
    </tr>
  </tbody>
</table>

#### Property: Endpoint URI
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-endpoint-uri">pmt:endpointURI</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A unique URI for the endpoint of this output port.</td>
    </tr>
    <tr>
      <td>See Also of:</td>
      <td><a href="https://www.w3.org/TR/vocab-dcat-2/#Property:data_service_endpoint_url">dcat:endpointURL</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Unique endpoints contribute to Addressability and Native Accessibility.</td>
    </tr>
  </tbody>
</table>

#### Property: Consume Instructions
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property=consume-instructions">pmt:consumeInstructions</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>Human-readable instructions on how to consume data through this output port.</td>
    </tr>
    <tr>
      <td>SubProperty of:</td>
      <td><a href="https://www.w3.org/TR/vocab-dcat-2/#Property:data_service_endpoint_description">dcat:endpointDescription</a></td>
    </tr>
    <tr>
      <td>Usage note:</td>
      <td>Consume instructions are the informal equivalent of the <a href="#class-data-contract">pmt:dataContract</a>, which captures the formal promises and expectations of this output port.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Consume instructions help with making the data Natively Accessible, and, potentially, Interoperable.</td>
    </tr>
  </tbody>
</table>

<h4 id="output-port-property-consumed-by"> Property: Consumed By </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#output-port-property-consumed-by">pmt:isConsumedBy</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>The input port of a data product or a use case that consumes this data product.</td>
    </tr>
    <tr>
      <td>Range:</td>
      <td><a href="#class-input-port">pmt:InputPort</a>, <a href="#class-use-case">pmt:UseCase</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Linking consumed data products and operational sources helps establish data lineage, as well a <a href="#property-estimated-value">pmt:estimatedValue</a> for the connsumed data products.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Keeping track of who consumes what data contributes to determining Value, as well as establishing data lineage. In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
    </tr>
  </tbody>
</table>
  
<h4 id="output-port-property-data-contract"> Property: Data Contract</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#output-port-property-data-contract">pmt:dataContract</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A data contract associated with an output port. If the output port is the input port of another data contract, the data contract regulates how the data flows into that data product.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Data Contracts contribute to Understandability, Truthfulness & Trustworthiness, Native Accessibility and Security.</td>
    </tr>
  </tbody>
</table>

<h4 id="output-port-access-management">Property: Access Management</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#output-port-access-management">pmt:accessManagement</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The enforcement of access rights on an output port.</td>
    </tr>
    <tr>
      <td>Usage Note</td>
      <td>Access Management is usually provided by the organisation as part of a larger IAM framework</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Access Mangement contributes to Security, Native Accessibility and Feedback-Driven.</td>
    </tr>
  </tbody>
</table>

### Class: Data Contract
The following properties are specific to this class: [providerPromise](#property-provider-promise), [consumerPromise](#property-consumer-promise), [service level agreement](#property-service-level-agreement), [service level objective](#property-service-level-objective).

<!-- Data contracts SHOULD refer to policies that are used to manage this data product using [pmt:policy](#data-contract-property-policy). -->

<table>
    <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-data-contract">pmt:DataContract</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A collection of enforceable promises concerning the delivery of a data product or use case.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Data contracts are highly dependable on the requirements and culture of the organisation implementing a data mesh. External standards, can and should be used to establish and describe data contracts. Examples include the <a href="https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en">SCC</a> for transferring data outside of the EU, <a href="https://www.ciso-portal.com/iso-9001-cybersecurity/">ISO9001</a> for security purposes or <a href="https://github.com/paypal/data-contract-template/blob/main/docs/README.md#Data-quality">Paypal's standard</a> for a data contract in a data mesh.</td>
    </tr>
  </tbody>
  <tr>
    <td>Motivation:</td>
    <td>Data Contracts contribute to Understandability, Truthfulness & Trustworthiness, Native Accessibility and Security.</td>
  </tr>
</table>

#### Property: Provider Promise
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-provider-promise">pmt:providerPromise</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A promise made by the <a href="#property-data-provider">pmt:dataProvider</a> to the data consumer that is captured in the data contract.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Provider promises can also be captured in a <a href="#property-service-level-agreement">pmt:SLA</a>, <a href="#property-service-level-objective">pmt:SLO</a> or in a <a href="#data-contract-property-promise">pmt:policy</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Provider promises contribute to Truthfulness & Trustworthiness, Native Accessibility and Security.</td>
    </tr>
  </tbody>
</table>

#### Property: Consumer Promise
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-consumer-promise">pmt:consumerPromise</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A promise required from the data consumer to the <a href="#property-data-provider">pmt:dataProvider</a> that is captured in the data contract.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Consumer promises can also be captured in a <a href="#property-service-level-agreement">pmt:SLA</a> or in a <a href="#data-contract-property-policy">pmt:policy</a>.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Consumer promises contribute to Security.</td>
    </tr>
  </tbody>
</table>

<h4 id="data-contract-property-policy">Property: Policy</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#data-contract-property-policy">pmt:policy</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A policy that is explained and enforced in the data contract.</td>
    </tr>
      <td>Usage Note:</td>
      <td>A wide variety of policies may exist that manage different aspects of the data product such as: computational policies, data product standardized protocols, and automated tests and automated monitoring.
      </td>
    </tr>
    </tr>
      <td>Usage Note:</td>
      <td>Best practice is to use additional documentation to describe and manage the different types of policies that exist within a data mesh ecosystem.
      </td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Policies can contribute to one or more of Understandability, Truthfulness & Trustworthiness and Security.</td>
    </tr>
  </tbody>
</table>

#### Property: Service Level Agreement
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-service-level-agreement">pmt:SLA</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A service level agreement related to the delivery of data through the output port of this data contract.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Best practice is to use additional documentation to describe and manage SLAs in the data mesh ecosystem.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Service level agreements contribute to Understandability, Truthfulness & Trustworthiness, Native Accessibility and Security.</td>
    </tr>
  </tbody>
</table>

#### Property: Service Level Objective
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#property-service-level-objective">pmt:SLO</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A service level objective related to the delivery of data through the output port of this data contract.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Best practice is to use additional documentation to describe and manage SLOs in the data mesh ecosystem.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Service level objectives contribute to Understandability, Truthfulness & Trustworthiness, Native Accessibility and Security.</td>
    </tr>
  </tbody>
</table>

### Class: Input Port
<!-- Input Ports MUST have a [pmt:correspondingDataProduct](#input-port-corresponding-data-product). Input ports MUST have either a [pmt:consumes](#input-port-property-consumes) relation or a [pmt:sourceSystem](#input-port-property-source-system) relation. Input ports SHOULD be extended with a [dct:description](#input-port-property-description) relation. -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-input-port">pmt:InputPort</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>An input port of a data product which relates to a source system or an output port of another data product.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Keeping track of who consumes what data contributes to determining Value, as well as establishing data lineage. In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
    </tr>
  </tbody>
</table>

<h4 id="input-port-property-description"> Property: Description</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#input-port-property-description">dct:description</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A human-readable account of the input port.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Adding a description of the distribution improves Understandability, and potentially Discoverability and Interoperability. </td>
    </tr>
  </tbody>
</table>

<h4 id="input-port-property-corresponding-data-product"> Property: Corresponding Data Product</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#input-port-property-corresponding-data-product">pmt:correspondingDataProduct</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The data product of this input port.</td>
    </tr>
    <tr>
      <td>Usage Note</td>
      <td>This is an inverse property of <a href="#property-input-port">pmt:inputPort</a></td>
    </tr>
  </tbody>
</table>

<h4 id="input-port-property-consumes"> Property: Consumes </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#input-port-property-consumes">pmt:consumes</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A resource or output port of a data product which is consumed to create or maintain this input port.</td>
    </tr>
    <tr>
      <td>Range</td>
      <td>{<a href="#class-resource">pmt:Resource</a>, <a href="#class-output-port">pmt:OutputPort</a>}</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This property is an inverse property of <a href="#resource-property-consumed-by">pmt:isConsumedBy</a></td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Keeping track of who consumes what data contributes to determining Value, as well as establishing data lineage. In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
    </tr>
  </tbody>
</table>

<h4 id="input-port-property-source-system"> Property: Source System </h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#input-port-property-source-system">pmt:sourceSystem</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>An IT system that generates or stores data that is used for this data product, such as a speficic data warehouse, data lake, or database.</td>
    </tr>
    <tr>
      <td>Domain</td>
      <td>{<a href="#class-data-asset">pmt:DataAsset</a>, <a href="#class-input-port">pmt:InputPort</a>}</td>
    </tr>
      <td>Usage Note:</td>
      <td>This property can be used to describe either where a specific data set or distribution lives, or give information on the input port of a data product.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>In addition to making data products Feedback-Driven, tracking lineage in general contributes to Discoverability, Addressability, Understandability, and Interoperability.</td>
    </tr>
  </tbody>
</table>

<h4 id="input-port-property-data-contract"> Property: Data Contract</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#input-port-property-data-contract">pmt:dataContract</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A data contract associated with an output port. If the output port is the input port of another data contract, the data contract regulates how the data flows into that data product.</td>
    </tr>
    <tr>
      <td>Motivation:</td>
      <td>Data Contracts contribute to Understandability, Truthfulness & Trustworthiness, Native Accessibility and Security.</td>
    </tr>
  </tbody>
</table>

<h4 id="input-port-property-physical-schema">Property: Physical Schema</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#input-port-property-physical-schema">pmt:physicalSchema</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A description of the data structure and internal relations at the distribution-level.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Physical schemas describe the structure of data of a specific <a href="#class-distribution">distribution</a> of a <a href="#class-data-asset">pmt:DataAsset</a>. Structural descriptions that hold true across all distributions of a data asset are described in <a href="#data-asset-property-logical-schema">pmt:logicalSchema</a></td>
  </tr>
  <tr>
      <td>Motivation:</td>
      <td>Physical schemas help with Understandability and Interoperability.</td>
    </tr>
  </tbody>
</table>

### Class: Control Port
<!-- Control Ports MUST have a [pmt:correspondingDataProduct](#control-port-corresponding-data-product). Contorl port SHOULD refer to the policies that are manged through them with a [policy](#control-port-property-policy) property. Control ports MAY be extended with a [dct:description](#control-port-property-description) property. -->

<table>
  <thead>
    <tr>
      <th width="240px"><strong>Class:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#class-control-port">pmt:ControlPort</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition:</td>
      <td>A control port through which a data product's policies can be managed by external parties such as the <a href="#property-data-provider">pmt:dataProvider</a> or a federated governance team. </td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Since control ports are highly dependent on the infrastructure provided in the data mesh, as well as the policies employed in the organisation, description of control ports SHOULD be extended with external documentation as the situation requires.</td>
    </tr>
  </tbody>
</table>

<h4 id="control-port-property-description"> Property: Description</h4> 
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/elements/1.1/description">dct:description</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A human-readable account of the control port.</td>
    </tr>
  </tbody>
</table>

<h4 id="control-port-property-corresponding-data-product"> Property: Corresponding Data Product</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#control-port-property-corresponding-data-product">pmt:correspondingDataProduct</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The data product whose policies are managed through this control port.</td>
    </tr>
    <tr>
      <td>Usage Note</td>
      <td>This is an inverse property of <a href="#property-control-port">pmt:controlPort</a></td>
    </tr>
  </tbody>
</table>

<h4 id="control-port-property-policy">Property: Policy</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#control-port-property-policy">pmt:managedPolicy</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>A policy that can be managed through this control port.</td>
    </tr>
      <td>Usage Note:</td>
      <td>A wide variety of policies may exist that manage different aspects of the data product such as: computational policies, data product standardized protocols, and automated tests and automated monitoring.
      </td>
    </tr>
    </tr>
      <td>Usage Note:</td>
      <td>Best practice is to use additional documentation to describe and manage the different types of policies that exist within a data mesh ecosystem.
      </td>
    </tr>
  </tbody>
</table>
