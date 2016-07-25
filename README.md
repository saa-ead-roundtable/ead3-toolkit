# EAD3 Starter Kit

Prepared by the EAD Roundtable Steering Committee, Society of American Archivists

2016-07-19

![Creative Commons By 4.0 License](https://i.creativecommons.org/l/by/4.0/88x31.png)

This work is licensed under a [*Creative Commons Attribution 4.0 International License*](http://creativecommons.org/licenses/by/4.0/).

## Context and Usage

The [*EAD Roundtable*](http://www2.archivists.org/groups/encoded-archival-description-ead-roundtable#.V4BMO6JvnSl) of the Society of American Archivists promotes the implementation and use of encoding standards for dissemination of archival information. With the release of the Encoded Archival Description schema, Version EAD3 in 2015, the Roundtable aims to provide tools and information to promote and facilitate its use among the archival community. This EAD3 Starter Kit was created to facilitate awareness of and support implementation of the encoding standard.

The EAD3 Starter Kit comprises this document, along with a set of sample EAD3 files that comply with [**Describing Archives: A Content Standard** *(DACS)*](http://www2.archivists.org/standards/DACS#.V4BL5aJvnSk) recommendations. It is intended to be used as a quick-start study guide by anyone interested in learning or implementing EAD3. From a quick review of the files, you can get a sense of what bare-minimum DACS-compliant standardized EAD3 outputs look like. The files also showcase a number of new EAD3 elements that supersede EAD Version 2002 elements.

The files can additionally be used and adapted as templates, within local encoding contexts.

The EAD3 Starter Kit is intended to supplement other extant resources, which provide an overview of the EAD3 schema and a detailed enumeration of each element. We recommend consulting the following resources for more information:

- EAD Official Site: [https://www.loc.gov/ead/index.html](https://www.loc.gov/ead/index.html)
- EADiva: [http://eadiva.com/](http://eadiva.com/)

## The Sample Files

As each archival collection is unique in its nature and has its own unique encoding requirements, we created three different sample EAD3 files, available on GitHub at [https://github.com/saa-ead-roundtable/ead3-toolkit](https://github.com/saa-ead-roundtable/ead3-toolkit).

In creating these files, we kept the EAD3 encoding to a baseline minimum. In determining which elements to include in the examples, we used the following general parameters:

-   Include elements required for a valid EAD3 XML instance.
-   Include elements that are required by DACS for single-level through multilevel descriptions.
-   Include elements that have have have been broadly established as mandatory or required by statewide and regional EAD aggregators, as reflected through their specifications and "best practices & guidelines."

We did not include encodings that are highly-specific to local implementations (e.g., to support particular display needs and tied to specific stylesheets), as well as encodings that can facilitate transformations of EAD3 files for particular systems. Examples include the @label and @encodinganalog attributes, and &lt;head&gt; element.

Validating your EAD File
------------------------

The EAD3 standard was published in three forms, as a Document Type Declaration (DTD), an XML Schema Definition (XSD), and in Relax NG (RNG). The [*Preface*](https://www.loc.gov/ead/EAD3taglib/index.html#d0e115) to the EAD Tag Library explains the Technical Subcommittee’s choices as well as the limitations of the DTD (in brief, that it cannot support the additional namespaces one might choose to embed in &lt;objectxmlwrap&gt;). Other than this one limit on the DTD, your file should validate with all of them. We recommend the XSD or Relax NG but your system may require a DTD.

We also recommend that you store a local or hosted copy of the standard in the language of your choice. This will allow you to continue validation even if a remote copy goes offline. It ensures that your instance is self-contained. The following examples assume that ead3.rng/xsd/dtd is stored in the same directory as the XML file you are validating, to avoid faux URLs such as `http://yourlocalsite.org/wherever/you/store/it` or `../wherever/you/store/it`. When using these examples, please note instances of the filename and ensure you’ve written the correct static or relative path to *your* copy of the file. The location of the XML type and encoding declaration provides context on where to place the validation.

### Validating with RNG

```
<?xml version="1.0" encoding="UTF-8"?>
<?xml-model href="ead3.rng" type="application/xml" schematypens="http://relaxng.org/ns/structure/1.0"?>
```
If using Oxygen, one may also add the line:

```
<?oxygen RNGSchema="ead3.rng" type="xml"?>
```

### Validating with XSD

```
<?xml version="1.0" encoding="UTF-8"?>
<ead xmlns="http://ead3.archivists.org/schema/"
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xsi:schemaLocation="http://ead3.archivists.org/schema/ ead3.xsd">
```

### Validating with the DTD

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE ead PUBLIC "+// http://ead3.archivists.org/schema/ //DTD ead3 (Encoded Archival Description (EAD) Version 3)//EN" "ead3.dtd">
```

## An Encoding Walkthrough

### Single-level Minimum

**Sample file:** [ead3\_single\_level\_minimum.xml](https://github.com/saa-ead-roundtable/ead3-toolkit/blob/master/ead3_single_level_minimum.xml)

The Single-level Minimum sample file illustrates materials described at only one level &mdash; whether at the collection, series or any other single level. It consists of the following baseline EAD3 elements and includes elements that comply with DACS' requirements for single-level descriptions but are technically optional within the EAD3 schema. Linked DACS references are used only for elements required for compliance with DACS.


| **EAD3 element** | **Starting line number in sample file** | **Comments** | **DACS reference** |
| --- | --- | --- | --- |
| [&lt;ead&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-ead) | 3 | This is a required root element of an EAD file and must contain &lt;control&gt; followed by &lt;archdesc&gt;. It is recommended to keep a local copy of your preferred schema format (DTD, XSD, or RNG) in case of server outages where the schema is currently stored, as has happened with the 2002 EAD schema. Because validation methods vary by schema format chosen, none is included here. | |
| [&lt;control&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-control) | 4 | A new element in EAD3 and the first of &lt;ead&gt;’s two required child elements. Replaces &lt;eadheader&gt; and aligns more with EAC-CPF, a focus on data, and a focus on sources of information and standards used. &lt;control&gt; is used for recording bibliographic and administrative information about an EAD. It must contain the following elements: &lt;recordid&gt;, &lt;filedesc&gt;, &lt;maintenanceagency&gt;, &lt;maintenancestatus&gt; and &lt;maintenancehistory&gt;. | |
| [&lt;recordid&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-recordid) | 5 | This is a new element in EAD3 that designates a unique identifier for the EAD file. The template uses an optional @instanceurl attribute to record the URL of the EAD xml file. | |
| [&lt;filedesc&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-filedesc) | 6 | A child element of &lt;control&gt; that records bibliographic information about an EAD file such as description of the finding aid, author, title, subtitle, sponsor, edition, publisher, publishing series, and related notes. It must include a &lt;titlestmt&gt;. | |
| [&lt;titlestmt&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-titlestmt) | 7 | A child element of &lt;filedesc&gt; that groups together information about the name of an encoded finding aid and those responsible for its content. The template uses a required child element &lt;titleproper&gt; to record the title of a finding aid or finding aid series. | |
| [&lt;publicationstmt&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-publicationstmt) | 10 | A child element of &lt;filedesc&gt; that provides information concerning the publication or distribution of the EAD instance. | |
| [&lt;maintenancestatus&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-maintenancestatus) | 20 | A child element of &lt;control&gt; that records the current version status of the EAD file. The current status must always be recorded in the required attribute @value which is limited to revised, deleted, new, deletedsplit, deletedmerged, deletedreplaced, cancelled, derived). | |
| [&lt;maintenanceagency&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-maintenanceagency) | 21 | A child element of &lt;control&gt; that records information about the institution or service responsible for the creation, maintenance, and /or dissemination of the EAD file. This template uses an optional attribute @countrycode that specifies a unique code for the country in which the materials being described are held. The recommended source for country codes is the [ISO 3166-1 Codes for the Representation of Names of Countries, column Alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements). &lt;maintenanceagency&gt; must also include a child &lt;agencyname&gt; that records the name of the institution or service. This template also uses an optional element &lt;agencycode&gt; that provides a code for the institution or service responsible for the creation, maintenance, or dissemination of the EAD file. For best practices, use the format of International Standard Identifier for Libraries and Related Organizations (ISO 15511). The code is composed of a prefix, a dash, and an identifier. For specific codes, see [the Library of Congress’s code search](http://www.loc.gov/marc/organizations/). | |
| [&lt;languagedeclaration&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-languagedeclaration) | 25 | A new element in EAD3 and a child of &lt;control&gt; that indicates the language and script in which an EAD instance is written. | |
| [&lt;maintenencehistory&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-maintenancehistory) | 29 | A new element in EAD3 and a child of &lt;control&gt;. It’s used to record the history of the creation, revision, updates, and other modifications to the EAD file. Each event is recorded in a separate &lt;maintenanceevent&gt; element. | |
| [&lt;maintenanceevent&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-maintenanceevent) | 30 | A new element in EAD3 and a required and repeatable child element of &lt;maintenencyhistory&gt;. It is used to record maintenance activities of the EAD file. It must contain &lt;eventtype&gt;, &lt;eventdatetime&gt;, &lt;agenttype&gt;, &lt;agent&gt; in that order. | |
| [&lt;eventtype&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-eventtype) | 31 | A new element in EAD3 and a required child of &lt;maintenanceevent&gt;. It includes required attribute @value to record the type of maintenance activity performed. The possible values are cancelled, created, deleted, revised, unknown and updated. | |
| [&lt;eventdatetime&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-eventdatetime) | 32 | A new element of EAD3 and must follow &lt;eventtype&gt;. It is a required child of &lt;maintenenceevent&gt;. It records the date and time of a specific maintenance action for an EAD file. Though optional, it is strongly suggested to include @standarddatetime attribute with this tag which can be used to record an ISO 8601 standard-compliant form of the date and time of the maintenance event. | |
| [&lt;agenttype&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-agenttype)| 33 | A new element of EAD3 and must follow &lt;eventdatetime&gt;. It is a required child of &lt;maintenanceevent&gt;. It includes required attribute @value to indicate the type of agent responsible for the creation, modification, or deletion of an EAD file and must be set to human, machine or unknown. | |
| [&lt;agent&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-agent) | 34 | A new element of EAD3 and must follow &lt;agenttype&gt;. It is a required child of &lt;maintenanceevent&gt;. It provides the name of a person, institution, or system responsible for the creation, modification, or deletion of an EAD file. | |
| [&lt;archdesc&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-archdesc) | 44 | One of only two child elements of &lt;ead&gt;. &lt;archdesc&gt; follows the &lt;control&gt; element and wraps together all of the archival descriptive information in an EAD file. It includes elements describing the content, context, extent, administrative and other supplemental information that facilitates the use of the materials which are organized in hierarchical levels. It includes a required attribute @level which indicates the type of aggregation being described in the EAD file and must include the following values: class, collection, file, fonds, item, otherlevel, recordgrp, series, subfonds, subgrp, or subseries. &lt;archdesc&gt; must contain a required child &lt;did&gt;. | |
| [&lt;did&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-did) | 45 | A required child element of &lt;archdesc&gt; that binds together other elements and records information about the material to be described in the EAD file. It may also occur within other wrapper elements like c, c01, c02 ... c12. | |
| [&lt;repository&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-repository) | 46 | An optional child element of &lt;did&gt; that records the name of the institution, person, or family responsible for providing intellectual access to the materials being described. At least one of four name elements (&lt;persname&gt;, &lt;famname&gt;, &lt;corpname&gt;, or &lt;name&gt;) is required if this is used. This template uses &lt;corpname&gt; and the optional &lt;address&gt;. &lt;corpname&gt; is used to identify the organization responsible for the materials. The name of the organization is encoded within its required and repeatable child element &lt;part&gt;. &lt;address&gt; is used to bind together multiple required &lt;addressline&gt; child elements that provide information about the place where the repository is located and how it may be contacted. | [2.2](http://www2.archivists.org/standards/DACS/part_I/chapter_2/2_name_and_location_of_repository) |
| [&lt;origination&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-origination) | 56 | An optional child element of &lt;did&gt; that specifies the name of an individual, organization, or family responsible for the described materials. At least one of four name elements (&lt;persname&gt;, &lt;famname&gt;, &lt;corpname&gt;, or &lt;name&gt;) is required if this is used. This template uses the child element &lt;persname&gt; to identify the personal name of the collector which is encoded within its required and repeatable child element &lt;part&gt;. The experimental <relations> element may also satisfy DACS 2.6, but as it is designated as experimental, we chose to recommend use of &lt;origination&gt;. | [2.6](http://www2.archivists.org/standards/DACS/part_I/chapter_2/6_name_of_creators) |
| [&lt;unittitle&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-unittitle) | 61 | An optional child element of &lt;did&gt; that records the specified title for the described materials. It can be used at &lt;archdesc&gt; level and at the subordinate &lt;c&gt; levels. | [2.3](http://www2.archivists.org/standards/DACS/part_I/chapter_2/3_title) |
| [&lt;unitid&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-unitid) | 62 | An optional child element of &lt;did&gt; that provides an identifier for the materials being described. | [2.1](http://www2.archivists.org/standards/DACS/part_I/chapter_2/1_reference_code) |
| [&lt;unitdatestructured&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-unitdatestructured) | 63 | A new element in EAD3 and an optional child element of &lt;did&gt; that records machine-processable dates of the materials being described. We opted to highlight the use of this new element, in lieu of using &lt;unitdate&gt; with a @normal attribute (EAD3 supports the same general type of &lt;unitdate&gt; encoding as EAD Version 2002). Our sample file uses an optional attribute @unitdatetype that identifies the type of date expressed with possible values of bulk or inclusive. When &lt;unitdatestructured&gt; is used, it must contain one and only one of the following: &lt;daterange&gt;, &lt;dateset&gt;, &lt;datesingle&gt;. The sample file uses an optional child element &lt;daterange&gt; to bind together dates encoded with optional (but recommended) &lt;fromdate&gt; and &lt;todate&gt; elements. | [2.4](http://www2.archivists.org/standards/DACS/part_I/chapter_2/4_date)
| [&lt;physdescset&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-physdescset) | 75 | A new element in EAD3 and an optional child element of &lt;did&gt; that can be used to group two or more optional &lt;physdecstructured&gt; elements. &lt;physdecstructured&gt; element quantifies the physical or logical extent of the materials being described. It must include two required attributes @coverage and @physdescstructuredtype. @coverage, with two possible values whole or part, specifies whether the description refers to the entire unit or only a part of the materials. @physdescstructuredtype defines the type of amount being described with the following possible values:<ul><li>`carrier`: Refers to the number of containers.</li><li>`materialtype`: Indicates the type and/or number of items.</li><li>`spaceoccupied`: Describes the linear, cubic, or other space occupied by the materials.</li><li>`otherphysdescstructuredtype`: May be chosen if none of the other values are appropriate.</li></ul>&lt;physdescstructuredtype&gt; must include two required children. &lt;quantity&gt; to indicate the number of units present in &lt;unittype&gt; and &lt;unittype&gt; to indicate the type of unit being quantified such as boxes, linear feet, cubic feet, etc. | [2.5](http://www2.archivists.org/standards/DACS/part_I/chapter_2/5_extent) |
| [&lt;langmaterial&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-langmaterial) | 85 | An optional child element of &lt;did&gt; which identifies the languages and scripts represented in the materials. This template uses a required child element &lt;language&gt; to record the language(s) of the EAD file or of the materials being described. &lt;language&gt; also includes a strongly recommended attribute @langcode to record the code of the language which should be taken from from ISO 639-1, ISO 639-2b, ISO 639-3, or another controlled list. | [4.5](http://www2.archivists.org/standards/DACS/part_I/chapter_4/5_languages_and_scripts_of_the_material) |
| [&lt;accessrestrict&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-accessrestrict) | 89 | An optional element that records information about the conditions that affect the availability of the materials being described. | [4.1](http://www2.archivists.org/standards/DACS/part_I/chapter_4/1_conditions_governing_access) |
| [&lt;userestrict&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-userestrict) | 92 | An optional element that indicates any conditions that govern the use of the described materials. | [4.4](http://www2.archivists.org/standards/DACS/part_I/chapter_4/4_conditions_governing_reproduction_and_use) |
| [&lt;scopecontent&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-scopecontent) | 95 | An optional element that may contain the information about the arrangement of the materials, dates covered by the materials, significant organizations, individuals, events, places and subjects represented by the materials. | [3.1](http://www2.archivists.org/standards/DACS/part_I/chapter_3/1_scope_and_content) |

###  Single-level Optimum

**Sample file:** [ead3\_single\_level\_optimum.xml](https://github.com/saa-ead-roundtable/ead3-toolkit/blob/master/ead3_single_level_optimum.xml)

The Single-level Optimum sample file illustrates the elements included in the Single-level Minimum, along with the DACS recommended Optimum element &lt;bioghist&gt; and access points as recommended in the DACS "Overview of Archival Description."

| **EAD3 element** | **Starting line number in sample file** | **Comments** | **DACS reference** |
| --- | --- | --- | --- |
| [&lt;bioghist&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-bioghist) | 98 | An optional element can be used to provide a concise essay or chronology which highlights the historical context of the materials. Information could be added using a series of &lt;p&gt; elements and/or &lt;chronlist&gt;. | [2.7](http://www2.archivists.org/standards/DACS/part_I/chapter_2/7_administrative_biographical_history) |
| [&lt;controlaccess&gt;](https://www.loc.gov/ead/EAD3taglib/index.html#elem-controlaccess) | 101 | An optional element that binds together key access points – names, topics, places, functions, occupations, titles, and genre terms – that represents the context and contents of the materials being described. &lt;controlaccess&gt; may be used at multiple levels within a finding aid either within &lt;archdesc&gt; to provide access terms for the entirety of the materials or within &lt;c&gt;..&lt;c12&gt; i.e. Component level to provide terms specific to a component. This template uses the following two optional child elements to record the access points: <ul><li>&lt;persname&gt; to identify a name of a person who is related to the materials being described as either a source, creator, or subject. It includes an optional attribute @source to record the source of the controlled vocabulary, e.g. "lcnaf" for Library of Congress Name Authority File and @relator to highlight the contextual relationship, the identified person has with the materials being described.</li><li> &lt;subject&gt; to identify topics associated with or covered by the described materials. It includes an optional attribute @source to record the source of the controlled vocabulary, e.g. "lcsh" for Library of Congress Subject Heading.</li></ul> | [See DACS "Overview of Archival Description"](http://www2.archivists.org/standards/DACS/overview_of_archival_description) |

### Multi-level Optimum

**Sample file:** [ead3\_multi\_level\_optimum.xml](https://github.com/saa-ead-roundtable/ead3-toolkit/blob/master/ead3_multi_level_optimum.xml)

The Multi-level Optimum sample file illustrates materials described at multiple levels beginning with large accumulations (e.g. collection level, series level). It includes the elements in the Single-level Optimum, along with the following elements to highlight the level of arrangement of archival materials. Because the finding aid being used for this example included several digital archival objects, the Steering Committee chose to include these as an example of the &lt;dao&gt; element, revised in EAD3. A &lt;dao&gt; is not a necessary part of the Multi-level Optimum description, but if a digital archival object exists, local practice may support including it.

| **EAD3 element** | **Starting line number in sample file** | **Comments** | **DACS reference** |
| --- | --- | --- | --- |
| [&lt;dsc&gt;](http://www.loc.gov/ead/EAD3taglib/index.html#elem-dsc) | 119 | An element which bundles information about the hierarchical groupings of the materials being described. | |
| [&lt;c01&gt; through &lt;c12&gt;](http://www.loc.gov/ead/EAD3taglib/index.html#elem-c01) | 120, 134, 150, 164, 176 | <p>An optional child element of &lt;dsc&gt; that designates a subordinate part of the materials being described. Each &lt;c\#\#&gt; identifies a logical section, or level of the described materials. &lt;c\#\#&gt; may be further subdivided into smaller components and numbered. Note that unnumbered &lt;c&gt; components may be utilized, in lieu of numbered &lt;c\#\#&gt; components. Because this file is meant for human eyes vs. machine processing, we opted to use numbered &lt;c\#\#&gt; components in the sample file, making it easier for viewers to immediately discern the hierarchy. The best practices recommendation is to choose &lt;c&gt; or &lt;c\#\#&gt; and apply consistently across all EAD files.</p><p>This template uses an optional attribute @level (required on &lt;archdesc&gt; but not at lower levels) that identifies the logical type of component and uses on these values: class, collection, file, fonds, item, otherlevel, recordgrp, series, subfonds, subseries, subgrp.</p>| [See DACS "Multilevel Optimum" notes for identifying the whole-part relationship between levels of description](http://www2.archivists.org/standards/DACS/part_I/chapter_1) |
| [&lt;container&gt;](http://www.loc.gov/ead/EAD3taglib/index.html#elem-container) | 144, 160, 171, 186  | An optional child element of &lt;did&gt; that indicates the container in which the materials being described is housed. This template uses an optional attribute @localtype to record the type of container e.g., box, folder, file, etc. | |
| [&lt;dao&gt;](http://www.loc.gov/ead/EAD3taglib/index.html#elem-dao) | 161, 172 | An optional child element of &lt;did&gt; that is used for linking to born digital records or a digital representation of the materials being described. It requires an attribute @daotype that specifies whether the digital archival object is born digital or digitized from physical holdings i.e. derived. This template uses an optional attribute @href that records the Uniform Resource Identifier (URI) of the digital file. |
