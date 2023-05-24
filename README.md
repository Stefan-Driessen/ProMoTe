# ProMoTe

### Disclaimer 
ProMoTe is under active development and evaluation from both the academic community and our industrial partners. If you intend to use this standard, feel free to reach out with questions and or feedback.

### License
This document is licensed under the [Creative Commons BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode) license.

## Table of Contents

<!-- toc -->

* [Introduction](#introduction)
* [ProMoTe from a bird's-eye view](#promote-from-a-birds-eye-view)
* [How to read and use this document.](#how-to-read-and-use-this-document)
* [External Documents](#external-documents)
* [Specification](#specification)
  * [Class: Resource](#class-resource)
    * [Property: Title](#property-title)
    * [Property: Resource Provider](#property-resource-provider)
    * [Property: Identifier](#property-identifier)
    * [Property: Date Issued](#property-date-issued)
    * [Property: Date Modified](#property-date-modified)
    * [Property: Resource Type](#property-resource-type)
    * [Property: Keyword](#property-keyword)
    * [Property: Language](#property-language)
    * [Property: Newer Version](#property-newer-version)
    * [Property: Older Version](#property-older-version)
    * [Property: Estimated Value](#property-estimated-value)
    * [Property: Qualified Attribution](#property-qualified-attribution)
  * [Class: Domain](#class-domain)
    * [Property: Resource](#property-resource)
  * [Class: Institutional Knowledge](#class-institutional-knowledge)
    * [Property: Defining Domain](#property-defining-domain)
    * [Property: Knowledge URI](#property-knowledge-uri)
  * [Class: Data Product](#class-data-product)
    * [Property Data Provider](#property-data-provider)
    * [Property: Dataset](#property-dataset)
    * [Property: Input Port](#property-input-port)
  * [Class: Use Case](#class-use-case)
    * [Property: Planned End Date](#property-planned-end-date)
  * [Class: Dataset](#class-dataset)
  * [Class Distribution](#class-distribution)
    * [Property: Technical Schema](#property-technical-schema)
  * [Class: Output Port](#class-output-port)
    * [Property: Consume Instructions](#property-consume-instructions)
    * [Property: Data Contract](#property-data-contract)
  * [Class: Data Contract](#class-data-contract)
    * [Property: Provider Promise](#property-provider-promise)
    * [Property: Consumer Promise](#property-consumer-promise)
    * [Property: Service Level Agreement](#property-service-level-agreement)
    * [Property: Service Level Objective](#property-service-level-objective)
  * [Class: Input Port](#class-input-port)
  * [Class: Control Port](#class-control-port)

<!-- tocstop -->

## Introduction
ProMoTe is a data Product Modelling Template for describing data products in a data mesh environment in a technology-independent manner. It was originally designed by researchers collaborating with large European companies that were looking to transition from a centralised, monolithic data landscape towards a more decentralised data-mesh (like) data landscape. ProMoTe is grounded in academic literature and industrial practice. It extends well-established ontologies (primarily [DCAT](https://www.w3.org/TR/vocab-dcat-2/)) in a way that is intended to help create data products that achieve the DAUTNIVS+ non-functional requirements (Discoverability, Addressability, Understandability, Truthful & Trustworthy, Natively Accessible, Interoperable, Valuable and Secure + Feedback-Driven). The first eight of these are described extensively in the original data mesh [book](https://www.oreilly.com/library/view/data-mesh/9781492092384/), published by Dehghani in 2020, whereas being Feedback-Driven originates from a desire to develop data products in an agile manner, akin to how DevOps has become standard practice for software development.

## ProMoTe from a bird's-eye view
The figure below shows an overview in UML of the classes described in ProMoTe and the relations that can be used to describe them; the classes and relations are also described in detail below. At a high level ProMoTe extends the [dcat:Resource](https://www.w3.org/TR/vocab-dcat-2/#Class:Resource) class with a subclass: [pmt:Resource](#class-resource). pmt:Resources come in three varieties: the [pmt:Dataset](#class-dataset), which is a subclass of [dct:Dataset](https://www.w3.org/TR/vocab-dcat-2/#Class:Dataset); the [pmt:Dataproduct](#class-data-product), which is the architectural quantum of a data mesh and the main focus of ProMoTe; and the [pmt:UseCase](#class-use-case), that describes how the data is consumed.

Each resource is managed within a [pmt:Domain](#class-domain) that maintains semantic domain knowledge in [pmt:InstitutionalKnowledge](#class-institutional-knowledge). Data products ingest data through one or more [pmt:InputPort](#class-input-port)s and are governed through policies that are managed through [pmt:ControlPort](#class-control-port)s. Finally, data products make available one or more [dct:Distribution](#class-distribution)s of [pmt:Dataset](#class-dataset)s through an associated [pmt:OutputPort](#class-output-port). For each output port, an associated [pmt:DataContract](#class-data-contract) establishes the conditions that apply when consuming the underlying data.

## How to read and use this document.
With ProMoTe, you can help define metadata models to describe data products in the data catalogue of your data mesh, or it can help you determine what a data product should look like within your organisation and whether different maturity levels that contain various aspects exist. An academic paper illustrating these use cases of ProMoTe is underway. ProMoTe is also available as an ontology in a .owl-file, which can be found here TODO.

The key words MAY, MUST, MUST NOT, and SHOULD in this document are to be interpreted as described in [BCP 14](https://tools.ietf.org/html/bcp14) [RFC2119](https://tools.ietf.org/html/rfc2119) [RFC8174](https://tools.ietf.org/html/rfc8174) when, and only when, they appear in all capitals, as shown here.

## External Documents
ProMoTe is compliant with and incorporates terms from the [DCAT vocabulary](), which in turn makes use of [other vocabularies](https://www.w3.org/TR/vocab-dcat-2/#namespaces). This means that ProMoTe can both extend existing implementations using these standards and be extended with terminology from those vocabularies.

![UML](https://raw.githubusercontent.com/Stefan-Driessen/ProMoTe/main/ProMoTe_v4.png)

## Specification
### Class: Resource
The following properties are specific to this class: [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

Resources MAY be extended with one or more [pmt:consumes](#resource-property-consumes), [pmt:sourceSystem](#resource-property-consumes), and [consumed by](#resource-property-consumed-by) relations.

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
    <td>A data product, or use case that can be described on a data catalog.</td>
    </tr>
    <tr>
    <td>Subclass of:</td>
    <td><a href="https://www.w3.org/TR/vocab-dcat-2/#Class:Resource">dcat:resource</a></td>
    </tr>
    <tr>
    <td>Usage Note:</td>
    <td>The class of all data sets, data products and use cases that exist and are registered in the data catalog of the data mesh.</td>
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
</tbody>
</table>

<h4 id="resource-property-domain"> Property: Domain</h4>

  <table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#property-domain">pmt:domain</a></span></th>
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
<td>{<a href="#class-data-product">pmt:DataProduct</a>, <a href="#class-use-case">pmt:UseCase</a>, <a href="#class-data-set">pmt:Dataset</a>}</td>
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
<td>Recommended usage is to describe until when this resource is available in the <a href="#property-description">dct:description</a> property.</td>
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
<td>Recommended usage is to describe when the old resource is no longer available in the <a href="#property-description">dct:description</a> property.</td>
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
        <td>This property can refer to other resources on the data catalog or to source systems that are not onboarded on the catalog.</td>
      </tr>
      <tr>
        <td>Usage Note:</td>
        <td>This property is an inverse property of <a href="#resource-property-consumed-by">pmt:isConsumedBy</a></td>
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
    <td>An IT system that generates or stores data in this resource, such as a speficic data warehouse, data lake, or database.</td>
    </tr>
    <tr>
    <tr>
    <td>Domain</td>
    <td>{<a href="#class-dataset">pmt:Dataset</a>, <a href="#class-input-port">pmt:InputPort</a>}</td>
    </tr>
    <tr>
    <td>Usage Note:</td>
    <td>This property can be used to describe either where a specific data set or distribution lives, or give information on the input port of a data product.</td>
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
</tbody>
</table>

### Class: Domain
The following properties are specific to this class: [resource](#property-resource), [domain knowledge](property-domain-knowledge).

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
</tbody>
</table>

### Class: Institutional Knowledge
The following properties are specific to this class: [defining domain](#property-defining-domain), [knowledge URI](#property-knowledge-uri).

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
The following properties are specific to this class: [data provider](#property-data-provider), [dataset](#property-dataset), [output port](#data-product-property-output-port), [input port](#property-input-port), [control port](#property-control-port).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#resource-property-consumes),  [consumed by](#resource-property-consumed-by), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

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
      <td><a href="#class-resource">pmt:resource</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>The class of all data products that exist and are registered in the data catalog of the data mesh.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This class describes all everything that holds true across all underlying datasets, distributions, and output ports in the data product.</td>
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
  </tbody>
</table>

  #### Property: Dataset
<table>
  <thead>
    <tr>
    <th width="240px"><strong>Property:</strong></th>
    <th width="760px"><span style="font-weight:normal"><a href="#property-dataset">pmt:dataSet</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
    <td>Definition:</td>
    <td>A dataset that is offered through this data product.</td>
    </tr>
    <tr>
    <td>Range:</td>
    <td><a href="#class-dataset">pmt:Dataset</a></td>
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
  <td>Usage Note:</td>
  <td>This is an inverse property of <a href="#property-exposes-data-product">pmt:exposesDataProduct</a></td>
  </tr>
  </tbody>
</table>

### Class: Use Case
The following property is specific to this class: [planned end date](#property-planned-end-date).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#resource-property-consumes), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

Use cases MUST have at least one [pmt:consumes](#resource-property-consumes) property to indicate which dataset or output port they consume.

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
      <td><a href="#class-resource">pmt:resource</a></td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This is the class of all use cases that consume data products and are registered in the data catalog of the data mesh.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>If use cases generate new data, they can, over time also lead to new data products.</td>
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
</tbody>
</table>

### Class: Dataset
The following properties are specific to this class: [distribution](#dataset-property-distribution), [logical](#dataset-property-logical-schema), [data product](#dataset-property-data-product).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#resource-property-consumes), [consumed by](#resource-property-consumed-by), [estimated value](#property-estimated-value), [qualified attribution](#property-qualified-attribution).

The following properties are inherited from the super-class [dcat:Dataset](http://www.w3.org/ns/dcat#Dataset): [spatial/geographic coverage](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_spatial), [spatial resolution](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_spatial_resolution), [temporal coverage](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_temporal), [temporal resolution](https://www.w3.org/TR/vocab-dcat-2/#Property:dataset_temporal_resolution).

<table>
<thead>
<tr>
<th width="240px"><strong>Class:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#class-dataset">pmt:Dataset</a></span></th>
</tr>
</thead>
<tbody>
<tr>
<td>Definition:</td>
<td>A collection of data that can be described by a single logical schema and be consumed in one or more techincal representations (distributions) through one or more output ports.</td>
</tr>
<tr>
<td>Sub-class of:</td>
<td><a href="http://www.w3.org/ns/dcat#Dataset">dcat:Dataset</a></td>
</tr>
<tr>
<td>Usage Note:</td>
<td>This class describes the conceptual dataset. One or more representations might be available, with differing schematic layouts and formats or serializations.</td>
</tr>
<tr>
<td>Usage Note:</td>
<td>A dataset can exist as a precursor to  a data product and evolve to become a fully mature data produt over time. Not every data set needs to become a fully function data product however. Additionally, it is possible for a single data product to provide (access to) multiple datasets.</td>
</tr>
</tbody>
</table>

  <h4 id="dataset-property-distribution"> Property: Distribution </h4>
  
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
<td>An available distribution of the dataset.</td>
</tr>
</tbody>
</table>
  
  <h4 id="dataset-property-logical-schema"> Property: Logical schema</h4>
  
  <table>
  <thead>
  <tr>
  <th width="240px"><strong>Property:</strong></th>
  <th width="760px"><span style="font-weight:normal"><a href="#dataset-property-logical-schema">pmt:logicalSchema</a></span></th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td>Definition:</td>
  <td>A description of the data structure and internal relations at the dataset-level.</td>
  </tr>
  <tr>
    <td>Usage Note:</td>
    <td>Logical schemas describe the structure of data that holds true across different distributions of the dataset. Structural descriptions of different distributions are described in [pmt:technicalSchema](#property-technical-schema)</td>
  </tr>
  </tbody>
  </table>
  
  <h4 id="dataset-property-data-product"> Property: Data Product </h4>
  
<table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#dataset-property-data-product">pmt:offeredInDataProduct</a></span></th>
</tr>
</thead>
<tbody>
<tr>
<td>Definition:</td>
<td>A data product that makes this dataset available for consumption.</td>
</tr>
<tr>
<td>Range:</td>
<td><a href="#class-data-procut">pmt:DataProduct</a></td>
</tr>
<tr>
<td>Usage Note:</td>
<td>This is an inverse property of <a href="#property-data-set">pmt:dataset</a></td>
</tr>
</tbody>
</table>
  
### Class Distribution
The following properties are specific to this class: [output port](#distribution-property-output-port), [technical schema](#property-technical-schema)

Distributions SHOULD be extended with a <a href="#distribution-property-description">dct:description</a>.

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
    <td>A specific representation of a dataset. A dataset might be available in multiple serializations that may differ in various ways, including natural language, media-type or format, schematic organization, temporal and spatial resolution, level of detail or profiles (which might specify any or all of the above).</td>
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
</tbody>
</table>
  
  #### Property: Technical Schema
  <table>
    <thead>
    <tr>
    <th width="240px"><strong>Property:</strong></th>
    <th width="760px"><span style="font-weight:normal"><a href="#property-technical-schema">pmt:technicalSchema</a></span></th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>Definition:</td>
    <td>A description of the data structure and internal relations at the distribution-level.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Technical schemas describe the structure of data of a specific distribution of a [pmt:Dataset](#class-dataset). Structural descriptions that hold true across all distributions of a dataset are described in [pmt:logicalSchema](#dataset-property-logical-schema)</td>
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
</table>

### Class: Output Port
The following properties are specific to this class: [distribution](#output-port-property-distribution), [data product](#output-port-property-data-product), [data contract](#property-data-contract).

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
</tbody>
</table>

  <h4 id="output-port-property-distribution"> Property: Distribution</h4>
  
<table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#output-port-property-distribution">pmt:exposesDistribution</a></span></th>
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
 
  <h4 id="output-port-property-data-product"> Property: Data Product </h4>
  
<table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#output-port-property-data-product">pmt:exposesDataProduct</a></span></th>
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
<td><a href="#class-output-port">pmt:OutputPort</a></td>
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
<td>Usage note:</td>
<td>Consume instructions are the informal equivalent of the <a href="#class-data-contract">pmt:dataContract</a>, which captures the formal promises and expectations of this output port.</td>
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
  </tbody>
</table>
  
#### Property: Data Contract
<table>
<thead>
<tr>
<th width="240px"><strong>Property</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#property-data-contract">pmt:dataContract</a></span></th>
</tr>
</thead>
<tbody>
<tr>
<td>Definition</td>
<td>The data contract associated with this output port.</td>
</tr>
</tbody>
</table>

### Class: Data Contract
The following properties are specific to this class: [providerPromise](#property-provider-promise), [consumerPromise](#property-consumer-promise), [service level agreement](#property-service-level-agreement), [service level objective](#property-service-level-objective).

Data contracts SHOULD refer to policies that are used to manage this data product using [pmt:policy](#data-contract-property-policy).

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
      <td>Data contracts are highly dependable on the requirements and culture of the organisation implementing a data mesh. External standards, can and should be used to establish and describe data contracts. Examples include the [SCC](https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/standard-contractual-clauses-scc_en) for transferring data outside of the EU, the [ISO9001](https://www.ciso-portal.com/iso-9001-cybersecurity/) for security purposes or [Paypal's standard](https://github.com/paypal/data-contract-template/blob/main/docs/README.md#Data-quality) for a data contract in a data mesh.</td>
    </tr>
  </tbody>
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
      <td>A promise made by the [pmt:dataProvider](#property-data-provider) to the data consumer that is captured in the data contract.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Provider promises can also be captured in a [pmt:SLA](#property-service-level-agreement), [pmt:SLO](#property-service-level-objective) or in a [pmt:policy](#data-contract-property-promise)</td>
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
      <td>A promise required from the data consumer to the [pmt:dataProvider](#property-data-provider) that is captured in the data contract.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>Consumer promises can also be captured in a [pmt:SLA](#property-service-level-agreement) or in a [pmt:policy](#data-contract-property-promise)</td>
    </tr>
  </tbody>
</table>

<h4 id="data-contract-property-policy">Property: Policy</h4>
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property:</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="#data-contract-property-policy">pmt:promise</a></span></th>
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
  </tbody>
</table>

### Class: Input Port
Input Ports MUST have a [pmt:correspondingDataProduct](#input-port-corresponding-data-product). Input ports MUST have either a [pmt:consumes](#input-port-property-consumes) relation or a [pmt:sourceSystem](#input-port-property-source-system) relation. Input ports SHOULD be extended with a [dct:description](#input-port-property-description) relation.

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
  </tbody>
</table>

<h4 id="input-port-property-corresponding-data-product"> Property: Corresponding Data Product</h4>
  
<table>
  <thead>
    <tr>
      <th width="240px"><strong>Property</strong></th>
      <th width="760px"><span style="font-weight:normal"><a href="http://purl.org/dc/elements/1.1/description">pmt:correspondingDataProduct</a></span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>The data product of this input port.</td>
    </tr>
    <tr>
      <td>Usage Note</td>
      <td>This is an inverse property of [pmt:inputPort](#property-input-port)</td>
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
      <td>A resource or output port of a data product which is consumed to create or maintain this resource.</td>
    </tr>
    <tr>
      <td>Range</td>
      <td>{[pmt:Resource](#class-resource), [pmt:OutputPort](#class-output-port)}</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This property can refer to other resources on the data catalog or to source systems that are not onboarded on the catalog.</td>
    </tr>
    <tr>
      <td>Usage Note:</td>
      <td>This property is an inverse property of <a href="#resource-property-consumed-by">pmt:isConsumedBy</a></td>
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
      <td>{<a href="#class-dataset">pmt:Dataset</a>, <a href="#class-input-port">pmt:InputPort</a>}</td>
    </tr>
      <td>Usage Note:</td>
      <td>This property can be used to describe either where a specific data set or distribution lives, or give information on the input port of a data product.</td>
    </tr>
  </tbody>
</table>




### Class: Control Port
Control Ports MUST have a [pmt:correspondingDataProduct](#control-port-corresponding-data-product). Contorl port SHOULD refer to the policies that are manged through them with a [policy](#control-port-property-policy) property. Control ports MAY be extended with a [dct:description](#control-port-property-description) property.

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
      <td>This is an inverse property of [pmt:controlPort](#property-control-port)</td>
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
