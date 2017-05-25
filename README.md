# What is biotoolsSchema?
**biotoolsSchema** is a formalised XML schema (XSD) which defines a description model for bioinformatics software.  It can be used to describe bioinformatics tools - application software with well-defined data processing functions (inputs, outputs and operations).   This includes simple tools with one or a few closely related functions, and complex, multimodal tools with many functions.  A broad range of software types (see below) are covered including tools available for immediate use as online services, or in a form which which you can download, install, configure and run yourself.

biotoolsSchema defines 50 important scientific, technical and administrative attributes.  It concentrates upon the salient common features, with a minimal core of 7 attributes, mandating the necessary and sufficient information to support cataloguing and discovery of software.  It is used by the [ELIXIR Tools & Data Services Registry](https://bio.tools).

Comprehensive documentation is available:
* http://biotoolsschema.readthedocs.io/en/latest/
* https://github.com/bio-tools/biotoolsSchema/blob/master/versions/biotools-2.0.0/docs/biotools-2.0.0.html (version 2.0.0, latest stable version)
* https://bio.tools/schema (version 2.0.0 currently in production in bio.tools)



# Information standard
biotoolsSchema provides the foundation for an information standard for the desription of tools that is being adopted by bio.tools.  The standard defines the attributes that must be defined for an entry to be labelled as a "minimal", "silver" and "gold" standard quality.  For more information see the [tools information standard](https://github.com/bio-tools/biotoolsSchemaDocs/blob/master/information_requirement.rst#information-requirement).

Attribute | Description | Format | minimal | silver | gold | element
--------- | ----------- | ------ | ------- | ------ | ---- | -------
**Name** | Canonical software name assigned by the software developer or service provider. | Text | y | y | y | `<name>`
**Description** | Short and concise textual description of the software function. | Text | y | y | y | `<description>`
**Homepage** | Homepage of the software, or some URL that best serves this purpose. | URL | y | y | y | `<homepage>`
**Software type** | The type of application software: a discrete software entity can have more than one type. | enum (from biotoolsSchema, see below) | y | y | y | `<toolType>`
**Unique ID** | Unique ID of the tool that is assigned upon registration of the software in bio.tools. | Text (URL-safe version of tool name) | y | y | y | `<toolID>`
**Scientific topics** | General scientific domain the software serves or other general category, e.g. "Proteomics". | Term and / or URI of [EDAM Topic](http://edamontology.org/topic_0004) concept(s)* | y | y | y | `<topic>`
**Scientific function** | The basic operation(s) performed by the software, e.g. "Multiple sequence alignment". | Term and / or URI of [EDAM Operation](http://edamontology.org/operation_0004) concept(s) | y | y | y | `<function><operation>`
**Type of input & output data** | Type of primary input / output data (if any), e.g. "Protein sequences". | Term and / or URI of [EDAM Data](http://edamontology.org/data_0006) concept(s) | - | y |  y | `<function><input>/<output><data>`
**Supported data formats** | Allowed format(s) of primary inputs/outputs, e.g. "FASTA". | Term and / or URI of [EDAM Format](http://edamontology.org/format_1915) concept(s) | - | y |  y | `<function><input>/<output><format>`
**Publication** | Publications about the software. | DOI, PMID or PMCID | - | y | y | `<publication>`
**Contact information** | Primary contact, e.g. a person, helpdesk or mailing list | Email address and / or URL | - | y | y | `<contact>`
**Issue tracker** | Link to tracker for software issues, bug reports, feature requests etc. | URL | - | - | y | `<link><type>Issue tracker</type>`
**Mailing list** | Link to mailing list for software announcements, discussions, support etc. | URL | - | - | y | `<link><type>Mailing list</type>`
**Repository** | Link to repository where source code, data and other files may be downloaded. | URL | - | - | y | `<link><type>Repository</type>`
**Documentation** | Link to documentation about the software e.g. manual, API specification or training material. | URL | - | - | y | `<documentation>`
**License** | Software or data usage license. | enum (from biotoolsSchema) | - | - | y | `<labels><license>`


*EDAM is a simple ontology of well established, familiar concepts that are prevalent within bioinformatics, including types of data and data identifiers, data formats, operations and topics. EDAM provides a set of terms with synonyms and definitions - organised into an intuitive hierarchy for convenient use.  You can read find [EDAM on GitHub](https://github.com/edamontology/edamontology).

  
## Tool types 
Valid values of toolType in in the candidate stable schema ([biotools-2.0.0](https://github.com/bio-tools/biotoolsSchema/blob/master/versions/biotools-2.0.0/)).

type | Description 
---- | ----------- 
Command-line tool | A tool with a text-based (command-line) interface.
Database portal | A Web application, suite or workbench providing a portal to a biological database.
Desktop application | A tool with a graphical user interface that runs on your desktop environment, e.g. on a PC or mobile device.
Library | A collection of components that are used to construct other tools.  bio.tools scope includes component libraries performing high-level bioinformatics functions but excludes lower-level programming libraries.
Ontology | A collection of information about concepts, including terms, synonyms, descriptions etc. | 2.0.0
Plug-in | A software component encapsulating a set of related functions, which are not standalone, i.e. depend upon other software for its use, e.g. a Javascript widget, or a plug-in, extension add-on etc. that extends the function of some existing tool.
Script | A tool written for some run-time environment (e.g. other applications or an OS shell) that automates the execution of tasks. Often a small program written in a general-purpose languages (e.g. Perl, Python) or some domain-specific languages (e.g. sed).
SPARQL endpoint | A service that provides queries over an RDF knowledge base via the SPARQL query language and protocol, and returns results via HTTP.
Suite | A collection of tools which are bundled together into a convenient toolkit.  Such tools typically share related functionality, a common user interface and can exchange data conveniently.  This includes collections of stand-alone command-line tools, or Web applications within a common portal.
Web application | A tool with a graphical user interface that runs in your Web browser.
Web API | An application programming interface (API) consisting of endpoints to a request-response message system accessible via HTTP.  Includes everything from simple data-access URLs to RESTful APIs.
Web service | An API described in a machine readable form (typically WSDL) providing programmatic access via SOAP over HTTP.
Workbench | An application or suite with a graphical user interface, providing an integrated environment for data analysis which includes or may be extended with any number of functions or tools.  Includes workflow systems, platforms, frameworks etc.
Workflow | A set of tools which have been composed together into a pipeline of some sort.  Such tools are (typically) standalone, but are composed for convenience, for instance for batch execution via some workflow engine or script.




