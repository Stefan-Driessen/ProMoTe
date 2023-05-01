
# ProMoTe

## TODO:
- [ ] Critically reread everything.
- [x] Check and update hyperlinks as needed.
- [ ] Add data schema information in the right places w. Jaco.
- [ ] Add additional information surrounding data contracrts.
- [ ] Add short descriptions before each class.
- [ ] Consider cardinality  with MAY, MUST, etc.
- [x] Add and update UML-diagram.
- [ ] Add nice styling with css.

![UML](https://raw.githubusercontent.com/Stefan-Driessen/ProMoTe/main/ProMoTe_v4.png)

### Class: Resource

|**Class:**|<span style="font-weight:normal">[pmt:Resource](#class-resource)</span>|
|---|---|
|Definition:|A data product, or use case that can be described on a data catalog.|
|Subclass of:|[dcat:resource](https://www.w3.org/TR/vocab-dcat-2/#Class:Resource)|
|Usage Note:| The class of all data sets, data products and use cases that exist and are registered in the data catalog of the data mesh.|
|Usage Note:|If the data catalog also contains information on data sevices, this class can be used in conjunction with [dcat:DataService](https://www.w3.org/TR/vocab-dcat-2/#Class:Data_Service).|

  #### Property: Title
  |**Property:**|<span style="font-weight:normal">[dct:title](http://purl.org/dc/terms/title)</span>|
  |---|---|
  |Definition:|A name given to the item.|
  |Range:|[rdfs:Literal](http://www.w3.org/2000/01/rdf-schema#Literal)|

  #### Property: Resource Provider
  |**Property**|<span style="font-weight:normal">[pmt:resourceProvider](#property-resource-provider)</span>|
  |---|---|
  |Definition:|The agent responsible for providing the resource.|
  |SubProperty of:|[dct:publisher](http://purl.org/dc/terms/publisher)|
  |Range:|[foaf:Agent](http://xmlns.com/foaf/0.1/#term_Agent)|
  |Usage Note:|Resource Providers are either data product providers or use case providers.|

  #### Property: Domain
  |**Property:**|<span style="font-weight:normal">[pmt:domain](#property-domain)</span>|
  |---|---|
  |Definition|The domain from which the resource stems.|
  |Range:|[pmt:Domain](#class-domain)|.

  #### Property: Identifier
  |**Property:**|<span style="font-weight:normal">[dct:identifier](http://purl.org/dc/elements/1.1/identifier)</span>|
  |---|---|
  |Definition|An unambiguous reference to the resource within a given context.|
  |Usage Note:|Common values are a urn or url.|

  #### Property: Description
  |**Property**|<span style="font-weight:normal">[dct:description](http://purl.org/dc/elements/1.1/description)</span>|
  |---|---|
  |Definition|A human-readable account of the resource.|

  #### Property: Date Issued
  |**Property:**|<span style="font-weight:normal">[dct:issued](http://purl.org/dc/terms/issued)</span>|
  |---|---|
  |Definition|Date when the resource was first made available for consumers.|
  |Range:|[xsd:date](https://www.w3.org/2001/XMLSchema)|

  #### Property: Date Modified
  |**Property:**|<span style="font-weight:normal">[dct:modified](http://purl.org/dc/terms/modified)</span>|
  |---|---|
  |Definition|Date when the resource was last modified.|
  |Range:|[xsd:date](https://www.w3.org/2001/XMLSchema)|

  #### Property: Resource Type
  |**Property:**|<span style="font-weight:normal">[pmt:type](#property-resource-type)</span>|
  |---|---|
  |Definition|The type of the resource.|
  |subPropertyOf:|[dct:Type](http://purl.org/dc/terms/type)|
  |Range:|{[pmt:DataProduct](#class-data-product), [pmt:UseCase](#class-use-case), [pmt:DataSet](#class-data-set)}|

  #### Property: Keyword
  |**Property:**|<span style="font-weight:normal">[dcat:keyword](https://www.w3.org/ns/dcat#keyword)</span>|
  |---|---|
  |Definition|A keyword or tag describing the resource.|
  |Range:|[rdfs:Literal](http://www.w3.org/2000/01/rdf-schema#Literal)|

  #### Property: Language
  |**Property:**|<span style="font-weight:normal">[dct:language](https://www.w3.org/ns/dcat#keyword)</span>|
  |---|---|
  |Definition|A keyword or tag describing the resource.|
  |Range:|[rdfs:Literal](http://www.w3.org/2000/01/rdf-schema#Literal)|

  <h4 id="resource-property-institutional-knowledge">Property: Institutional Knowledge</h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:institutionalKnowledge](#resource-property-institutional-knowledge)</span>|
  |---|---|
  |Definition|Existing terminology within the organisation or domain that relates to a [pmt:Resource](#class-resource).|
  |Range:|[pmt:InstitutionalKnowledge](#class-institutional-knowledge)|

  #### Property: Newer Version
  |**Property:**|<span style="font-weight:normal">[pmt:hasNewVersion](#property-newer-version)</span>|
  |---|---|
  |Definition|A newer version of the data product, which will eventually replace this version.|
  |Comment:|This property is used for versioning, keeping an older version available helps consumers of the resources by giving them time to migrate to the new resource.|
  |isDefinedBy:|[dct:hasVersion](http://purl.org/dc/terms/hasVersion)|
  |Range:|[pmt:Resource](#class-resource)|
  |Usage Note:|Recommended usage is to describe until when this resource is available in the [dct:description](#property-description) property.|

  #### Property: Older Version
  |**Property:**|<span style="font-weight:normal">[pmt:hasOldVersion](#property-older-version)</span>|
  |---|---|
  |Definition|An older version of the data product, which this version is replacing.|
  |Comment:|This property is used for versioning, keeping an older version available helps consumers of the resources by giving them time to migrate to the new resource.|
  |isDefinedBy:|[dct:isVersionOf](http://purl.org/dc/terms/isVersionOf)|
  |Range:|[pmt:Resource](#class-resource)|
  |Usage Note:|Recommended usage is to describe when the old resource is no longer available in the [dct:description](#property-description) property.|

  #### Property: Consumes
  |**Property:**|<span style="font-weight:normal">[pmt:consumes](#property-consumes)</span>|
  |---|---|
  |Definition|A resource which is consumed to create or maintain this resource.|
  |Usage Note:|This property can refer to other resources on the data catalog or to source systems that are not onboarded on the catalog.|
  |Usage Note:|This property is an inverse property of [pmt:isConsumedBy](#property-consumed-by)|
  
   #### Property: Consumed By
  |**Property:**|<span style="font-weight:normal">[pmt:isConsumedBy](#property-consumed-by)</span>|
  |---|---|
  |Definition:|A data product or use case that consumes this data product.|
  |Range:| [pmt:DataProduct](#class-data-product), [pmt:UseCase](#class-use-case)|
  |Usage Note:|Linking consuming data products helps establish data lineage, whereas linking use cases to data products improves the discoverability, understandability of the data product and helps establish a [pmt:estimatedValue](#property-estimated-value)|
  |Usage Note:|This is an inverse property of [pmt:consumes](#property-consumes)|

  #### Property: Estimated Value
  |**Property:**|<span style="font-weight:normal">[pmt:estimatedValue](#property-estimated-value)</span>|
  |---|---|
  |Definition|An indication of the value the resource provides for the company.|
  |Usage Note:|Ideally the estimated value is backed by a quantifier, such as money or manhours saved. Otherwise a qualitative description of the value provided can be provided.|

  #### Property: Qualified Agent
  |**Property:**|<span style="font-weight:normal">[prov:qualifiedAttribution](https://www.w3.org/TR/prov-o/#qualifiedAttribution)</span>|
  |---|---|
  |Definition|A link to an agent, other than the [pmt:resourceProvider](#property-resource-provider), that is bears some responsibility for the resource.|
  |Usage Note:|Qualified agents are useful when ownership is split amongst several owners, such as a business owner and a technical owner.|

### Class: Domain
|**Class:**|<span style="font-weight:normal">[pmt:Domain](#class-domain)</span>|
|---|---|
|Definition:|The organisational sphere of knowledge and activity from which the data originates.|
|Usage Note:|Aligning data and software with domains is one of the primary concerns of building a data mesh and domain-driven design in general.|

  #### Property: Resource
  |**Property:**|<span style="font-weight:normal">[pmt:hasResource](#property-resource)</span>|
  |---|---|
  |Definition:|A resource offered in the domain.|
  |Usage Note:|This is an inverse property of [pmt:domain](#resource-domain)|

  <h4 id="domain-property-institutional-resource"> Property: Institutional Knowledge </h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:domainKnowledge](#domain-property-institutional-resource)</span>|
  |---|---|
  |Definition|Existing terminology within the organisation or domain that relates to a [pmt:Resource](#class-resource).|
  |Range:|[pmt:InstitutionalKnowledge](#class-institutional-knowledge)|

### Class: Institutional Knowledge
|**Class:**|<span style="font-weight:normal">[pmt:InstitutionalKnowledge]()</span>|
|---|---|
|Definition:|Superclass of terminology within the organisation or domain that can be related to a [pmt:Resource](#class:-resource).|
|Usage Note:|Examples include how the data relates to specifically defined terms, business objects or business processes.|
|Usage Note:|Recommended usage is to organise institutional knowledge in (existing) ontologies or business glossaries.|

  #### Property: Defining Domain
  |**Property:**|<span style="font-weight:normal">[pmt:definingDomain](#property-defining-domain)</span>|
  |---|---|
  |Definition:|The domain that defines and maintains the institutional knowledge.|
  |Usage Note:|This is an inverse property of [pmt:institutionalKnowledge](#domain-property-institutional-resource)|
  |Usage Note:|It is possible that a piece of institutional knowledge is maintained on an organisation-wide level, rather than on a domain-level, but there should still be a domain responsible for maintining organisation-wide knowledge.|

### Class: Data Product
|**Class:**|<span style="font-weight:normal">[pmt:DataProduct](#class-data-product)</span>|
|---|---|
|Definition:|A data product, in a data mesh environment.|
|Subclass of:|[pmt:resource](#class-resource)|
|Usage Note:| The class of all data products that exist and are registered in the data catalog of the data mesh.|
|Usage Note:|This class describes all everything that holds true across all underlying datasets, distributions, and output ports in the data product.|

  #### Property Data Provider
  |**Property:**|<span style="font-weight:normal">[pmt:dataProvider](#property-data-provider)</span>|
  |---|---|
  |Definition:|The actor responsible for providing the data product.|
  |SubPropertyOf:| [pmt:resourceProvider](#property-resource-provider) |

  #### Property: Dataset
  |**Property:**|<span style="font-weight:normal">[pmt:dataSet](#property-dataset)</span>|
  |---|---|
  |Definition:|A dataset that is offered through this data product.|
  |Range:| [pmt:Dataset](#class-dataset) |
  |Usage Note:|This is an inverse property of [pmt:offeredInDataProduct](#property-offered-in-data-product)|

  <h4 id="data-product-property-output-port"</h4> Property: Output Port </h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:outputPort](#data-product-property-output-port)</span>|
  |---|---|
  |Definition:|An output port that exposes a distribution of this data product.|
  |Range:| [pmt:OutputPort](#class:-output-port)|
  |Usage Note:|This is an inverse property of [pmt:exposesDataProduct](#property-exposes-data-product)|

### Class: Use Case
|**Class:**|<span style="font-weight:normal">[pmt:UseCase](#class-use-case)</span>|
|---|---|
|Definition:|A use case of a data product, in a data mesh environment.|
|Subclass of:|[pmt:resource](#class-resource)|
|Usage Note:|This is the class of all use cases that consume data products and are registered in the data catalog of the data mesh.|
|Usage Note:|If use cases generate new data, they can, over time also lead to new data products.|


  #### Property: Planned End Date
  |**Property:**|<span style="font-weight:normal">[pmt:plannedEndDate](#property-planned-end-date)</span>|
  |---|---|
  |Definition:|The date by which the use case plans to stop consuming data products.|
  |Usage Note:|Keeping track of a planned end date helps with data product maintenance. There is no need to put effort into maintaining a data product if there are no active use cases.|
  |Usage Note:|If there is no foreseeable end date, the planned end date can be indefinite.|

### Class: Dataset
Can be extended with spatial, temporal, bytesize, etc.

|**Class:**|<span style="font-weight:normal">[pmt:Dataset](#class-dataset)</span>|
|---|---|
|Definition:|A collection of data that can be described by a single logical schema and be consumed in one or more representations.|
|Sub-class of:|[dcat:Dataset](http://www.w3.org/ns/dcat#Dataset)|
|Usage Note:|This class describes the conceptual dataset. One or more representations might be available, with differing schematic layouts and formats or serializations.|
|Usage Note:|A dataset can exist as a precursor to  a data product and evolve to become a fully mature data produt over time. Not every data set needs to become a fully function data product however. Additionally, it is possible for a single data product to provide (access to) multiple datasets.|

  <h4 id="dataset-property-distribution"> Property: Distribution </h4>
  
  |**Property:**|<span style="font-weight:normal">[dcat:distribution](http://www.w3.org/ns/dcat#distribution)</span>|
  |---|---|
  |Definition:|An available distribution of the dataset.|
  
  <h4 id="dataset-property-logical-schema"> Property: Logical schema</h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:logicalSchema](#dataset-property-logical-schema)</span>|
  |---|---|
  |Definition:|TODO: Define with Jaco|
  
  <h4 id="dataset-property-data-product"> Property: Data Product </h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:offeredInDataProduct](#dataset-property-data-product)</span>|
  |---|---|
  |Definition:|A data product that makes this dataset available for consumption.|
  |Range:|[pmt:DataProduct](#class-data-procut)|
  |Usage Note:|This is an inverse property of [pmt:dataset](#property-data-set)|
  
  
### Class Distribution
Can add optional descriptors such as dcat:byteSyze, dct:spatial, dct:temporal
|**Class:**|<span style="font-weight:normal">[dcat:Distribution](http://www.w3.org/ns/dcat#Distribution)</span>|
|---|---|
|Definition:|A specific representation of a dataset. A dataset might be available in multiple serializations that may differ in various ways, including natural language, media-type or format, schematic organization, temporal and spatial resolution, level of detail or profiles (which might specify any or all of the above). |
|Usage Note:|This represents a general availability of a dataset. It implies no information about the actual access method of the data, which is described in [pmt:OutputPort](#class-output-port).

  <h4 id="distribution-property-output-port">Output Port</h4>

  |**Property:**|<span style="font-weight:normal">[pmt:correspondingOutputPort](#distribution-property-output-port)</span>|
  |---|---|
  |Definition:|An output port that exposes this distribution.|
  |Range:| [pmt:OutputPort](#class:-output-port)|
  |Usage Note:|This is an inverse property of [pmt:exposesDistribution](#output-port-property-distribution)|
  
  #### Property: Data schema
  |**Property:**|<span style="font-weight:normal">[pmt:dataSchema](#property-data-schema)</span>|
  |---|---|
  |Definition:|TODO: Define with Jaco|
  
  #### Property: Description
  |**Property**|<span style="font-weight:normal">[dct:description](http://purl.org/dc/elements/1.1/description)</span>|
  |---|---|
  |Definition|A human-readable account of the distribution.|
  
  <h4 id="distribution-property-logical-schema">Property: Logical schema</h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:logicalSchema](#distribution-property-logical-schema)</span>|
  |---|---|
  |Definition:|TODO: Define with Jaco|

### Class: Output Port
|**Class:**|<span style="font-weight:normal">[pmt:OutputPort](#class-output-port)</span>|
|---|---|
|Definition:|An output port of a data product that exposes a specific representation.|
|Usage Note:|Output ports represent the various ways in which data products expose their data. For example, data can be made available through a download link, a SQL-based API or a kafka-stream.|

  <h4 id="output-port-property-distribution"> Property: Distribution</h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:exposesDistribution](#output-port-property-distribution)</span>|
  |---|---|
  |Definition:|The distribution that is exposed for consumption through this output port.|
  |Range:|[dcat:Distribution](https://www.w3.org/TR/vocab-dcat-2/#Class:Distribution)|
 
  <h4 id="output-port-property-data-product"> Property: Data Product </h4>
  
  |**Property:**|<span style="font-weight:normal">[pmt:exposesDataProduct](#output-port-property-data-product)</span>|
  |---|---|
  |Definition:|The data product that this output port exposes for consumption.|
  |Usage Note:|This is an inverse property of [pmt:outputPort](#data-product-property-output-port)|
  |Range:|[pmt:OutputPort](#class-output-port)|
  
  #### Property: Consume Instructions
  |**Property**|<span style="font-weight:normal">[pmt:consumeInstructions](#property=consume-instructions)</span>|
  |---|---|
  |Definition|Human-readable instructions on how to consume data through this output port.|
  |Usage note:|Consume instructions are the informal equivalent of the [pmt:dataContract](#class-data-contract), which captures the formal promises and expectations of this output port.|
  
  #### Property: Data Contract
  |**Property**|<span style="font-weight:normal">[pmt:dataContract](#property-data-contract)</span>|
  |---|---|
  |Definition|The data contract associated with this output port.|

### Class: Data Contract
|**Class:**|<span style="font-weight:normal">[pmt:DataContract](#class-data-contract)</span>|
|---|---|
|Definition:|A collection of enforceable promises concerning the delivery of a data product or use case.|
|Usage Note:|Data Contracts are highly dependable on the requirements and culture of the organisation implementing a data mesh. External ontologies, such as ZOEK can be used to establish and describe data contracts.|







