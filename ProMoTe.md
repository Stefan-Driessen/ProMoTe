# ProMoTe

## TODO:
- [x] Check and update hyperlinks as needed.
- [ ] Add data and logical schema information in the right places w. Jaco.
- [ ] Add additional information surrounding data contracrts.
- [x] Add short descriptions before each class.
- [ ] Consider cardinality  with MAY, MUST, etc.
- [ ] Add an intro that explains what this is and where we borrow from.`
- [x] Add and update UML-diagram.
- [ ] Manually style all the tables to fit the width of the page.
- [ ] Critically reread everything.

![UML](https://raw.githubusercontent.com/Stefan-Driessen/ProMoTe/main/ProMoTe_v4.png)

### Class: Resource
The following properties are specific to this class: [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#property-consumes),  [consumed by](#property-consumed-by), [estimated value](#property-estimated-value), [qualified agent](#property-qualified-agent). 

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
<td>{<a href="#class-data-product">pmt:DataProduct</a>, <a href="#class-use-case">pmt:UseCase</a>, <a href="#class-data-set">pmt:DataSet</a>}</td>
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

  #### Property: Consumes
<table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#property-consumes">pmt:consumes</a></span></th>
</tr>
</thead>
<tbody>
<tr>
<td>Definition</td>
<td>A resource which is consumed to create or maintain this resource.</td>
</tr>
<tr>
<td>Usage Note:</td>
<td>This property can refer to other resources on the data catalog or to source systems that are not onboarded on the catalog.</td>
</tr>
<tr>
<td>Usage Note:</td>
<td>This property is an inverse property of <a href="#property-consumed-by">pmt:isConsumedBy</a></td>
</tr>
</tbody>
</table>
  
   #### Property: Consumed By
<table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#property-consumed-by">pmt:isConsumedBy</a></span></th>
</tr>
</thead>
<tbody>
<tr>
<td>Definition:</td>
<td>A data product or use case that consumes this data product.</td>
</tr>
<tr>
<td>Range:</td>
<td><a href="#class-data-product">pmt:DataProduct</a>, <a href="#class-use-case">pmt:UseCase</a></td>
</tr>
<tr>
<td>Usage Note:</td>
<td>Linking consuming data products helps establish data lineage, whereas linking use cases to data products improves the discoverability, understandability of the data product and helps establish a <a href="#property-estimated-value">pmt:estimatedValue</a></td>
</tr>
<tr>
<td>Usage Note:</td>
<td>This is an inverse property of <a href="#property-consumes">pmt:consumes</a></td>
</tr>
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

  #### Property: Qualified Agent
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
<td>Qualified agents are useful when ownership is split amongst several owners, such as a business owner and a technical owner.</td>
</tr>
</tbody>
</table>

### Class: Domain
The following properties are specific to this class: [resource](#property-resource), [institutional knowledge](domain-property-institutional-resource).

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

  <h4 id="domain-property-institutional-resource"> Property: Institutional Knowledge </h4>
  
<table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#domain-property-institutional-resource">pmt:domainKnowledge</a></span></th>
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
The following property is specific to this class: [defining domain](#property-defining-domain.

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
<td>Superclass of terminology within the organisation or domain that can be related to a <a href="#class:-resource">pmt:Resource</a>.</td>
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

### Class: Data Product
The following properties are specific to this class: [data provider](#property-data-provider), [dataset](#property-dataset), [outputport](#data-product-property-output-port).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#property-consumes),  [consumed by](#property-consumed-by), [estimated value](#property-estimated-value), [qualified agent](#property-qualified-agent).

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

  <h4 id="data-product-property-output-port"</h4> Property: Output Port </h4>
  
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
<td><a href="#class:-output-port">pmt:OutputPort</a></td>
</tr>
<tr>
<td>Usage Note:</td>
<td>This is an inverse property of <a href="#property-exposes-data-product">pmt:exposesDataProduct</a></td>
</tr>
</tbody>
</table>

### Class: Use Case
The following property is specific to this class: [planned end date](#property-planned-end-date).

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#property-consumes), [estimated value](#property-estimated-value), [qualified agent](#property-qualified-agent).

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

The following properties are inherited from the super-class [pmt:Resource](#class-resource): [title](#property-title), [resource provider](#property-resource-provider), [domain](#resource-property-domain), [identifier](#property-identifier), [description](#resource-property-description), [date issued](#property-date-issued), [date modified](#property-date-modified), [resource type](#property-resource-type), [keyword](#property-keyword), [language](#property-language), [institutional knowledge](#resource-property-institutional-knowledge), [newer version](#property-newer-version), [older version](#property-older-version), [consumes](#property-consumes), [consumed by](#property-consumed-by), [estimated value](#property-estimated-value), [qualified agent](#property-qualified-agent).

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
<td>A collection of data that can be described by a single logical schema and be consumed in one or more representations.</td>
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
<td>TODO: Define with Jaco</td>
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
The following properties are specific to this class: [output port](#distribution-property-output-port), [data schema](#property-data-schema), [description](#distribution-property-description).

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
<td><a href="#class:-output-port">pmt:OutputPort</a></td>
</tr>
<tr>
<td>Usage Note:</td>
<td>This is an inverse property of <a href="#output-port-property-distribution">pmt:exposesDistribution</a></td>
</tr>
</tbody>
</table>
  
  #### Property: Data schema
<table>
<thead>
<tr>
<th width="240px"><strong>Property:</strong></th>
<th width="760px"><span style="font-weight:normal"><a href="#property-data-schema">pmt:dataSchema</a></span></th>
</tr>
</thead>
<tbody>
<tr>
<td>Definition:</td>
<td>TODO: Define with Jaco</td>
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
This class will be extended in the future.
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
<td>Data Contracts are highly dependable on the requirements and culture of the organisation implementing a data mesh. External ontologies, such as ZOEK can be used to establish and describe data contracts.</td>
</tr>
</tbody>
</table>







