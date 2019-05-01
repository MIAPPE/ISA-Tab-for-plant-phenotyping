**This is an updated, work-in-progress version of the phenotyping configuration for ISA metadata model**

ISA-Tab configuration for plant phenotyping experiments
-------------------------------------------------------
is a selection of MIAPPE attributes mapped to the ISA-Tab format. The most essential attributes that seem common to all phenotyping experiments are contained in the Basic Configuration. The configuration constitutes a scaffolding to construct any phenotypic dataset by adding other relevant attributes from the MIAPPE list or whatever information you wish to keep in the dataset. In case of field or greenhouse experiments, the basic attributes common to all of them are contained in Field Configuration and Greenhouse Configuration, respectively. You can extend these configurations by adding more attributes, but the list of the basic environmental information is already there.

*isaconfig-phenotyping* contains the configurations for constructing datasets with [ISA-tools](http://isa-tools.org/software-suite/).

*isa-templates* provides templates of ISA text files, prefilled with protocols and material ID's (to demonstrate biological and technical replications). You can can simply edit it in you Notepad or Spreadsheet, however, it is still advisable to validate with ISA-tools. There is also an equivalent Excel workbook with ISA files as sheets (for simplicity, it's not part of ISA standard) with export-to-txt macro.

*datasets* includes examples of ISA-formatted phenotyping datasets.


# ISA-Tab format for MIAPPE v1.1

One of the formats that can be used for a MIAPPE v1.1 submission is ISA-Tab. The present folder holds templates for each type of the I (Investigation), S (Study) and A (Assay) files, while this document explains the use of these templates. Depending on the template you choose, you might have to take slightly different actions, though the end result should be the same.

* Option 1: The spreadsheet template. Make sure to save each tab of this one as a tab-delimited text file. 
* Option 2: The text files. Be careful when editing this format manually, and pay attention to the number of (tab-separated) columns in each row.
* Option 3: The configuration for the [ISA Creator](https://github.com/ISA-tools/ISAcreator/releases). Please make sure to edit out the given example values, and that the files exported in the end hold all of your data. Note that, if you only have a single Study, you will have to edit the Investigation file manually! Using the ISA Creator also allows you to run the built-in validator for your files.

For questions, please consult the [MIAPPE v1.1 specification](https://github.com/MIAPPE/MIAPPE/tree/master/MIAPPE_Checklist-Data-Model-v1.1) first.



## Investigation file

Most fields have an explicit mapping to MIAPPE.

### `Investigation` section

The `Investigation` section is very similar to the respective MIAPPE section. The correspondence is as follows:



| Field # | MIAPPE                    | ISA-Tab                           |
|---------|---------------------------|-----------------------------------|
| 1       | Investigation unique ID   | Investigation Identifier          |
| 2       | Investigation title       | Investigation Title               |
| 3       | Investigation description | Investigation Description         |
| 4       | Submission date           | Investigation Submission Date     |
| 6       | Public release date       | Investigation Public Release Date |
| 7       | License                   | Comment[License]                  |
| 8       | MIAPPE version            | Comment[MIAPPE version]           |

In MIAPPE, only the investigation title and MIAPPE version are mandatory. Make sure that the dates you enter are in accordance with the ISO 8601 format (YYYY-MM-DD). The version, at this time, should be specified as `1.1`.

### `Investigation Publications` section

For publications, MIAPPE encourages the use of DOIs, though any identifier is acceptable. However, as opposed to ISA-Tab, which allows publications on the Investigation or Study level, MIAPPE only supports Investigation-level publications.

Subsequently, an identifier is expected in the `Investigation Publication DOI` field. If no DOI exists for a publication, the `Investigation PubMed ID` field may be used.

| Field # | MIAPPE                 | ISA-Tab                       |
|---------|------------------------|-------------------------------|
| 9       | Associated publication | Investigation Publication DOI |

If more publications are to be listed, they should all be on the same line and separated using tabs:

`Investigation Publication DOI⟶DOI_1⟶DOI_2`


### `Investigation Contacts` section

MIAPPE allows for the specification of people on both the Investigation and the Study level. The choice here is up to the user. For Investigation contacts, the mapping is as follows:

| Field # | MIAPPE             | ISA-Tab                                                                                            |
|---------|--------------------|----------------------------------------------------------------------------------------------------|
| 10      | Person ID          | Comment[Person ID]                                                                                 |
| 11      | Person name        | Investigation Person Last Name, Investigation Person First Name, Investigation Person Mid Initials |
| 12      | Person email       | Investigation Person Email                                                                         |
| 13      | Person affiliation | Investigation Person Address, Investigation Person Affiliation                                     |
| 14      | Person role        | Investigation Person Roles                                                                         |

Of course, more contacts may be provided per investigation. Following the example above, separate the details for each person with a tab character. Make sure to properly align each person's attributes, even if that means having to use multiple tabs in a row, e.g.:

```
Comment[Person ID]⟶1⟶2
Investigation Person Last Name⟶Smith⟶Doe
Investigation Person First Name⟶John⟶Jane
Investigation Person Mid Initials⟶⟶F.
```




### `Study` section

MIAPPE introduces new fields, most of which require ISA-Tab comments. Some fields belonging to MIAPPE Studies are divided over other ISA-Tab sections (see below).

| Field # | MIAPPE                                  | ISA-Tab                             |
|---------|-----------------------------------------|-------------------------------------|
| 15      | Study unique ID                         | Study Identifier                    |
| 16      | Study title                             | Study Title                         |
| 17      | Study description                       | Study Description                   |
| 18      | Start date of study                     | Comment[Study Start Date]           |
| 19      | End date of study                       | Comment[Study End Date]             |
| 20      | Contact institution                     | Comment[Study Contact Institution]  |
| 21      | Geographic location (country)           | Comment[Study Country]              |
| 22      | Experimental site name                  | Comment[Study Experimental Site]    |
| 23      | Geographic location (latitude)          | Comment[Study Latitude]             |
| 24      | Geographic location (longitude)         | Comment[Study Longitude]            |
| 25      | Geographic location (altitude)          | Comment[Study Altitude]             |

Additionally, you must use the `Comment[Trait Definition File]` to indicate the name of the file holding the descriptions of all observed variables. MIAPPE has no equivalent field since this information is all incorporated into the `Observed Variables` section.

Do not forget to indicate the name of the study file in the `Study File Name` field for each study. These filenames usually start with the `s_` prefix.

MIAPPE's Data File section is also included here:

| Field # | MIAPPE                                  | ISA-Tab                              |
|---------|-----------------------------------------|--------------------------------------|
| 26      | Data file link                          | Comment[Study Data File Link]        |
| 27      | Data file description                   | Comment[Study Data File Description] |
| 28      | Data file version                       | Comment[Study Data File Version]     |

More data files can be included too. Make sure to tab-separate and properly align their respective attributes!

### `Study Design Descriptors` section

More of MIAPPE's Study attributes are mapped here.

| Field # | MIAPPE                                 | ISA-Tab                                     |
|---------|----------------------------------------|---------------------------------------------|
| 29      | Description of the experimental design | Comment[Study Design Description]           |
| 30      | Type of experimental design            | Study Design Type                           |
| 31      | Observation unit level hierarchy       | Comment[Observation Unit Level Hierarchy]   |
| 32      | Observation unit description           | Comment[Observation Unit Description]       |
| 33      | Map of experimental design             | Comment[Map of Experimental Design]         |

Note that a class from the [Crop Research Ontology (CO_715)](http://www.cropontology.org/ontology/CO_715) should be provided for the `Type of experimental design`, and furthermore it should be a subclass of [CO_715:0000003 (Experimental design)](http://www.cropontology.org/terms/CO_715:0000003/Experimental%20design). 
For example, you would indicate that your experiment had a ["complete block design"](http://www.cropontology.org/terms/CO_715:0000145/) as `CO_715:0000145`.


```
Comment[Study Design Description]⟶Lines were repeated twice at each location using a complete block design. In order to limit competition effects, each block was organized into four sub-blocks corresponding to earliness groups based on a priori information. 
Study Design Type⟶CO_715:0000145
```


### `Study Publications` section

Refer to the `Investigation Publications` section.


### `Study Factors` section

This section is the equivalent of MIAPPE's Experimental Factors.

| Field # | MIAPPE                          | ISA-Tab                            |
|---------|---------------------------------|------------------------------------|
| 34      | Experimental Factor description | Comment[Study Factor Description]  |
| 35      | Experimental Factor type        | Study Factor Name                  |
| 36      | Experimental Factor values      | Comment[Study Factor Values]       |

The `Study Factor Name` is what you must later use in the column headings (of the Study file) to refer to the respective experimental factors.
Note that at least 2 factor values must be provided per factor. This can be done in the form of a semicolon-separated list:


```
Comment[Study Factor Description]⟶Daily watering 1 L per plant. 
Study Factor Name⟶Watering
Comment[Study Factor Values]⟶watered;unwatered
```


## `Study Assays` section

In this section, list the assay files in your ISA-Tab submission. No further information is necessary, but the Study Assay Measurement Type may indicate the type of measurements done (e.g. phenotyping, high throughput phenotyping, ...).  
An Assay file, as attached to a Study, cannot include Sample nodes from more than one Study.

```
STUDY ASSAYS
Study Assay File Name⟶"a_1_phenotyping.txt"⟶"a_2_phenotyping.txt"
Study Assay Measurement Type⟶phenotyping⟶phenotyping
```


### `Study Protocols` section

This section is used for some of the fields in the MIAPPE *Study* section, and more fields from different sections.

| Field # | MIAPPE                         | ISA-Tab                    |
|---------|--------------------------------|----------------------------|
| 37      | Description of growth facility | Study Protocol Type        |
| 38      | Type of growth facility        | Study Protocol URI         |
| 39      | Cultural Practices             | Study Protocol Description |


Note that, to indicate the above attributes, the `Study Protocol Name` field must always be set to "Growth".
Then, the above mapping may be followed. The `Study Protocol URI` field, being the ontology class for the growth facility, is optional. If given, it should be subclass of [CO_715:0000005 (Experimental condition)](http://www.cropontology.org/terms/CO_715:0000005/Experimental%20condition) from the [Crop Research Ontology (CO_715)](http://www.cropontology.org/ontology/CO_715)
For example, you would indicate that your experiment was conducted in a ["field environment condition"](http://www.cropontology.org/terms/CO_715:0000162/) as `CO_715:0000162`. The `Term Accession Number` and `Term Source REF` are not used.



Protocols in ISA-Tab can be parametrized with Protocol Parameters. We use these Parameters to present MIAPPE's *Environment Parameters*. Note that the environment parameters are listed under the Growth protocol in the Investigation file, but the actual values for them only appear in the Study file.

| Field # | MIAPPE                | ISA-Tab                        |
|---------|-----------------------|--------------------------------|
| 40      | Environment Parameter | Study Protocol Parameters Name |

Also note that multiple parameters may be listed here (separated by semicolons, not by tabs!).

For example, as far as the above attributes are concerned, this section would be composed in the following manner:

```
STUDY PROTOCOLS	
Study Protocol Name⟶Growth
Study Protocol Type⟶field environment condition
Study Protocol Type Term Accession Number⟶
Study Protocol Type Term Source REF⟶
Study Protocol Description⟶Irrigation was applied according needs during summer to prevent water stress.
Study Protocol URI⟶CO_715:0000162
Study Protocol Version⟶
Study Protocol Parameters Name⟶sowing density;pH
Study Protocol Parameters Name Term Accession Number⟶
Study Protocol Parameters Name Term Source REF⟶
Study Protocol Components Name⟶
Study Protocol Components Type⟶
Study Protocol Components Type Term Accession Number⟶
Study Protocol Components Type Term Source REF⟶
```

Study Protocols are also used for MIAPPE *Events*. In this case, the mapping is as follows:

| Field # | MIAPPE                 | ISA-Tab                    |
|---------|------------------------|----------------------------|
| 41      | Event type             | Study Protocol Name        |
| 42      | Event description      | Study Protocol Description |
| 43      | Event accession number | Study Protocol URI         |

For protocols describing Events, the `Study Protocol Type` must always be set to "Event". Note that the accession number for each event type is in the URI field. Once again, the [Crop Research Ontology (CO_715)](http://www.cropontology.org/ontology/CO_715) is used, and a subclass of [CO_715:0000006 (Time factor)](http://www.cropontology.org/terms/CO_715:0000006/Time%20factor) can be given, e.g. `CO_715:0000007` for the ["Sowing date"](http://www.cropontology.org/terms/CO_715:0000007/).

An Event protocol may look as follows:

```
STUDY PROTOCOLS	
Study Protocol Name⟶Planting⟶Fertilizing
Study Protocol Type⟶Event⟶Event
Study Protocol Type Term Accession Number⟶⟶
Study Protocol Type Term Source REF⟶⟶
Study Protocol Description⟶Sowing using seed drill⟶Fertilizer application: Ammonium nitrate at 3 kg/m2
Study Protocol URI⟶CO_715:0000007⟶CO_715:0000011
Study Protocol Version⟶⟶
Study Protocol Parameters Name⟶⟶
```

Two additional protocols must be defined. The `Sampling` protocol is only required in cases where MIAPPE samples are present. This protocol is used to indicate that a sampling operation takes place, transforming material from an ISA Sample (MIAPPE equivalent: Observation unit) into an ISA Extract (MIAPPE equivalent: Sample).

The only field in this protocol is fixed. The `Study Protocol Name` is always "Sampling".  
The respective protocol looks like:

```
STUDY PROTOCOLS	
Study Protocol Name⟶Sampling
Study Protocol Type⟶Sampling
Study Protocol Type Term Accession Number⟶
Study Protocol Type Term Source REF⟶
Study Protocol Description⟶
Study Protocol URI⟶
Study Protocol Version⟶
Study Protocol Parameters Name⟶Sampling Date;Sampling Description
```

Two fields from MIAPPE's Sample section are included here: the sampling date and the sampling description. 
ISA-Tab also allows native Date and Description fields for Material nodes (i.e. these did not have to be explicitly declared as protocol parameters). We nevertheless encourage the use of these parameters for the sampling protocol, as the native fields cannot be included in the ISA Creator configuration, making it harder for some users.


The `Phenotyping` protocol must be used to indicate that observations have been conducted in a study (i.e. that something has been measured). Its mandatory attribute follow the same pattern as above: the `Study Protocol Name` is set to `Phenotyping`.

```
STUDY PROTOCOLS	
Study Protocol Name⟶Phenotyping
Study Protocol Type⟶Phenotyping
Study Protocol Type Term Accession Number⟶
Study Protocol Type Term Source REF⟶
Study Protocol Description⟶
Study Protocol URI⟶
Study Protocol Version⟶
Study Protocol Parameters Name⟶
```

Finally, the `Data Transformation` protocol is used in Assay files, to indicate that a raw data file (included or not) has been processed to get the final results. Only its name needs to be declared in the Investigation.

```
STUDY PROTOCOLS	
Study Protocol Name⟶Data Transformation
Study Protocol Type⟶Data Transformation
Study Protocol Type Term Accession Number⟶
Study Protocol Type Term Source REF⟶
Study Protocol Description⟶
Study Protocol URI⟶
Study Protocol Version⟶
Study Protocol Parameters Name⟶
```


An Investigation file may only have one Study Protocols section per STUDY. Therefore, all of the above protocols need to be consolidated into one section. Protocols not in use may be omitted. 

The combined Protocols section could look as follows. Fixed fields (per protocol) are marked in this readme with \*asterisks\*.


```
STUDY PROTOCOLS
Study Protocol Name⟶*Growth*⟶Planting⟶Fertilizing⟶*Sampling*⟶*Phenotyping*⟶*Data transformation*
Study Protocol Type⟶Field environment condition⟶*Event*⟶*Event*⟶*Sampling*⟶*Phenotyping*⟶*Data transformation*
Study Protocol Type Term Accession Number⟶⟶⟶⟶⟶⟶
Study Protocol Type Term Source REF⟶⟶⟶⟶⟶⟶
Study Protocol Description⟶Irrigation was applied according needs during summer to prevent water stress.⟶Sowing using seed drill⟶Fertilizer application: Ammonium nitrate at 3 kg/m2⟶⟶⟶
Study Protocol URI⟶CO_715:0000162⟶CO_715:0000007⟶CO_715:0000011⟶⟶⟶
Study Protocol Version⟶⟶⟶⟶⟶⟶
Study Protocol Parameters Name⟶sowing density;pH⟶⟶⟶*Collection Date;Sample Description*⟶⟶
Study Protocol Parameters Name Term Accession Number⟶⟶⟶⟶⟶⟶
Study Protocol Parameters Name Term Source REF⟶⟶⟶⟶⟶⟶
Study Protocol Components Name⟶⟶⟶⟶⟶⟶
Study Protocol Components Type⟶⟶⟶⟶⟶⟶
Study Protocol Components Type Term Accession Number⟶⟶⟶⟶⟶⟶
Study Protocol Components Type Term Source REF⟶⟶⟶⟶⟶⟶
```


Or, in table form (the words in *italics* are fixed terms for the respective protocols):

| STUDY PROTOCOLS                                      |                                                                               |                         |                                                     |                                      |                         |                        |
|------------------------------------------------------|-------------------------------------------------------------------------------|-------------------------|-----------------------------------------------------|--------------------------------------|-------------------------|------------------------|
| Study Protocol Name                                  | *Growth*                                                                      | Planting                | Fertilizing                                         | *Sampling*                           | *Phenotyping*           | *Data transformation*  |
| Study Protocol Type                                  | Field environment condition                                                   | *Event*                 | *Event*                                             | *Sampling*                           | *Phenotyping*           | *Data transformation*  |
| Study Protocol Type Term Accession Number            |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Type Term Source REF                  |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Description                           | Irrigation was applied according needs during summer to prevent water stress. | Sowing using seed drill | Fertilizer application: Ammonium nitrate at 3 kg/m2 |                                      |                         |                        |
| Study Protocol URI                                   | CO_715:0000162                                                                | CO_715:0000007          | CO_715:0000011                                      |                                      |                         |                        |
| Study Protocol Version                               |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Parameters Name                       | sowing density;pH                                                             |                         |                                                     | *Collection Date;Sample Description* |                         |                        |
| Study Protocol Parameters Name Term Accession Number |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Parameters Name Term Source REF       |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Components Name                       |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Components Type                       |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Components Type Term Accession Number |                                                                               |                         |                                                     |                                      |                         |                        |
| Study Protocol Components Type Term Source REF       |                                                                               |                         |                                                     |                                      |                         |                        |


## Study file

Each row in the Study file represents a single MIAPPE Observation unit, which has the ISA Sample as its equivalent.
The Study file starts by specifying the plant materials in each observation unit. Then the `Growth` protocol (holding certain Study parameters and the environmental attributes) must be given, followed by the attributes of the observation unit itself (spatial information). At the end of the row, factors values (based on the factors specified in the Investigation file) may be specified per observation unit.
Event protocols may also be included here (after the `Growth` protocol), but the Sampling and Phenotyping protocols may only be applied in Assay files.

The file, therefore, on MIAPPE terms, follows this structure:

| Source Name | Characteristics[...] | Protocol REF | Parameter Value[...] | Protocol REF | Parameter Value[Event Date] | Sample Name | Characteristics[...] | Factor Value[...] |
|-------------|----------------------|--------------|----------------------|--------------|-----------------------------|-------------|----------------------|-------------------|
| source 1    |                      |              |                      |              |                             | exp. unit A |                      |                   |
| source 2    |                      |              |                      |              |                             | exp. unit B |                      |                   |


### Biological Material

[todo: organism is now just a string]
[todo: check for any references to ontology use in the ISA creator, since the explanation will be removed from this section]
[todo: fix numbers]

<!-- removed:
| 46      | Organism                                                       | Term Source REF                                              |
| 47      | Organism                                                       | Term Accession Number                                        |
-->

| Field # | MIAPPE                                                         | ISA-Tab                                                      |
|---------|----------------------------------------------------------------|--------------------------------------------------------------|
| 44      | Biological material ID                                         | Source Name                                                  |
| 45      | Organism                                                       | Characteristics[Organism]                                    |
| 46      | Genus                                                          | Characteristics[Genus]                                       |
| 47      | Species                                                        | Characteristics[Species]                                     |
| 48      | Infraspecific name                                             | Characteristics[Infraspecific name]                          |
| 49      | Biological material latitude                                   | Characteristics[Biological Material latitude]                |
| 50      | Biological material longitude                                  | Characteristics[Biological Material longitude]               |
| 51      | Biological material altitude                                   | Characteristics[Biological Material altitude]                |
| 52      | Biological material coordinates uncertainty                    | Characteristics[Biological Material Coordinates uncertainty] |
| 53      | Biological material preprocessing                              | Characteristics[Biological Material preprocessing]           |
| 54      | Material source ID (Holding institute/stock centre, accession) | Characteristics[Material Source ID]                          |
| 55      | Material source DOI                                            | Characteristics[Material Source DOI]                         |
| 56      | Material source latitude                                       | Characteristics[Material Source latitude]                    |
| 57      | Material source longitude                                      | Characteristics[Material Source longitude]                   |
| 58      | Material source altitude                                       | Characteristics[Material Source altitude]                    |
| 59      | Material source coordinates uncertainty                        | Characteristics[Material Source coordinates uncertainty]     |
| 60      | Material source description                                    | Characteristics[Material Source description]                 |



<!-- Note that the Organism may be qualified with an ontology term. The ISA Creator configuration for MIAPPE includes a recommendation for the ontology for the [NCBI taxonomy](https://www.ncbi.nlm.nih.gov/taxonomy) for this field. If you are not using the ISA Creator, make sure that you are indicating both the term and the ontology properly.

Ontologies referred to in an Investigation, Study or Assay file as Terms (i.e. with a Term Source REF / Term Accession Number field) must be declared at the top of the Investigation file, in the `ONTOLOGY SOURCE REFERENCE` section (see section 2.2.1 [here](https://isa-specs.readthedocs.io/en/latest/isatab.html#format)).

If you are not using the Creator, make sure that you use the proper prefixes/abbreviations to refer to classes from ontologies. -->

The Organism field should ideally point to a taxon from the [NCBI taxonomy](https://www.ncbi.nlm.nih.gov/taxonomy), though other references are also acceptable. 

Furthermore,the coordinates must be given in decimal degrees format. The altitude fields (for biological material and material source) must only hold numbers, but they are followed by a Unit column to hold the unit abbreviation.


You may have to repeat the description of each biological material many times, i.e. once for each observation unit it belongs to. 


#### Special case: whole-study level

In some cases, it may be necessary to have a single observation unit representing the entirety of a study. For example, sensors may be placed in a facility, and their measurements may be treated as representative of the global conditions. 

An observation unit would be necessary in this case too. This would mean that, for this unit, the associated source name should encompass all biological materials in this particular study. You can indicate that an observation unit covering the entire facility contents is the subject of these measurement(s) by defining its source as follows:

| Source Name | Characteristics[Organism] | Characteristics[...] | Sample Name | Characteristics[...] | Factor Value[...] |
|-------------|---------------------------|----------------------|-------------|----------------------|-------------------|
| `study`     | `NCBI:4107`               |                      |             |                      |                   |

The Organism attribute, which is mandatory, should indicate the genus of the biological material in the study. The above example assumes that the study involved materials only from the [Solanum species](https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=4107).

Note that, in this case, there can be **no factor value**.

### Protocols

Inclusion of the Growth protocol in the Study file is not mandatory (but it is **strongly** recommended that you specify as many environment parameters as you can - in which case they should appear here as the Growth protocol's parameters). The Growth protocol must be here, however, if any values of the environment parameters (declared already in the Investigation file) are to be specified. Each parameter may be followed by the `Term Source REF` and `Term Accession Number` fields, to enable references to ontology classes.

In the example in the Investigation section we included two environment parameters: sowing density and pH. These would be written out as:

| Source Name | ... | Protocol REF | Parameter Value[sowing density] |  Parameter Value[pH] |
|-------------|-----|--------------|---------------------------------|----------------------|
| source 1    | ... | Growth       | 300 seeds per m2                | 6.5                  |
| source 2    | ... | Growth       | 300 seeds per m2                | 6.5                  |

Note that, in the MIAPPE data model, environment parameter values apply, by definition, to all observation units in a study. Therefore these parameters must have the same value across all rows!


### Observation units

Each ISA-Tab source node must, after the application of protocols, lead to a Sample node. ISA-Tab samples are used as MIAPPE observation units, and carry their characteristics:

| Field # | MIAPPE                | ISA-Tab                                 |
|---------|-----------------------|-----------------------------------------|
| 63      | Observation unit ID   | Sample Name                             |
| 64      | Observation unit type | Characteristics[Observation Unit Type] |
| 65      | External ID           | Characteristics[External ID]            |
| 66      | Spatial distribution  | Characteristics[Spatial distribution]   |


The ISA configuration allows, by default, only specific `observation unit type`s, taken from the corresponding MIAPPE definition:

> Type of observation unit in textual form, usually one of the following: `block`, `sub-block`, `plot`, `plant`, `study`, `pot`, `replication or replicate`, `individual`, `virtual_trial`, `unit-parcel`.

<!-- Note that the current definition in MIAPPE has a trial level instead of the study level, but this should be changed in the next revision of the standard. -->

The `observation unit type` is stated in the study file, and repeated in each of the assay files. 

This list of possible values for the observation unit types column is non-exhaustive, but it should cover the majority of cases. It is possible to use a different unit type in the Creator (and in the Validator) by editing the configuration as follows:

#### Adding a new observation unit type

##### Step 1: Edit the study configuration (`s_study_basic.xml`)

The following section (around lines 95-99) looks as follows:
```
        <field data-type="list" header="Characteristics[Observation Unit Type]" is-file-field="false" is-forced-ontology="false" is-hidden="false" is-multiple-value="false" is-required="true">
            <description><![CDATA[(MIAPPE: Observation unit type) Type of observation unit in textual form, usually one of the following: block, sub-block, plot, plant, trial, pot, replication or replicate, individual, virtual_trial, unit-parcel]]></description>
            <default-value><![CDATA[plant]]></default-value>
            <list-values>block,sub-block,plot,plant,trial,pot,replicate,individual,virtual_trial,unit-parcel</list-values>
        </field>
```

Add the name of your unit to the list of allowed values:
`<list-values>**[new_unit_type]**,block,sub-block,plot,plant,trial,pot,replicate,individual,virtual_trial,unit-parcel</list-values>`

e.g.  
`<list-values>superblock,block,sub-block,plot,plant,trial,pot,replicate,individual,virtual_trial,unit-parcel</list-values>`

##### Step 2: Create a new assay configuration file

The name of the file should reflect the name of the new observation unit type and adhere to the pattern `phenotyping_[new_unit_type]_level.txt`, e.g. `phenotyping_superblock_level.txt`.

##### Step 3: Edit the new assay configuration file

The following lines have to be changed:

* On line 3, the `table-name` should include the name of the new unit type, e.g.
		`<isatab-configuration isatab-assay-type="generic_assay" isatab-conversion-target="generic" table-name="superblock_block_level">`
* On line 5, the `term-label` should also include the name of the new unit type, e.g.
		`<technology source-abbreviation="" term-accession="" term-label="superblock level analysis"/>`
* Modify line 12 to include the name of the new observation unit type in the list of values (should be the same as the respective line in the study configuration file), e.g.
		`<list-values>superblock,block,sub-block,plot,plant,trial,pot,replicate,individual,virtual_trial,unit-parcel</list-values>`

You may then use the new unit type in the ISA Creator.


### Factor values

Finally, any factor value must be attributed to the observation units. Factors, and their respective possible values, must be previously declared in the Investigation file too.

| Sample Name | Characteristics[...] | Factor Value[Watering] |
|-------------|----------------------|------------------------|
| exp. unit 1 | ...                  | watered                |
| exp. unit 2 | ...                  | watered                |
| exp. unit 3 | ...                  | unwatered              |

For more details about the specific meaning, contents and format of each field, see the [MIAPPE specification file](https://github.com/MIAPPE/MIAPPE/blob/master/MIAPPE_Checklist-Data-Model-v1.1/MIAPPE_Checklist-Data-Model-v1.1.xlsx).



## Assay file

The assay file starts with the Samples column (MIAPPE observation units) as defined in the study file. Then the Protocols should follow: Sampling may be used if there are any MIAPPE Samples (i.e. ISA-Tab Extracts) to speak of. The Phenotyping protocol must always be used in the end. The Sampling Date, a parameter value to the Sampling protocol, column is mandatory for Extracts, to indicate the collection date. The Date is not mandatory for the Phenotyping protocol.

Overall, the Sampling protocol applies on an ISA Sample (MIAPPE observation unit), and transforms a material (from a sample) into an Extract (MIAPPE sample). The sampling parameters describe the process, and the extract characteristics describe the resulting material.


### Samples

For the MIAPPE samples, the mapping is as follows:

| Field # | MIAPPE                            | ISA-Tab                                            |
|---------|-----------------------------------|----------------------------------------------------|
| 67      | Sample ID                         | Extract Name                                       |
| 68      | Plant structure development stage | Characteristics[Plant Structure Development Stage] |
| 79      | Plant anatomical entity           | Characteristics[Plant Anatomical Entity]           |
| 70      | Sample description                | Parameter Value[Sampling Description]              |
| 71      | Collection date                   | Parameter Value[Sampling Date]                     |
| 72      | External ID                       | Characteristics[External ID]                       |

The two Parameter Values in the above mapping both refer to the Sampling protocol.

The Sampling protocol can be applied as follows. The Plant structure development stage and the plant anatomical entity, according to MIAPPE recommendations, must refer to ontology classes.

| Sample Name | Characteristics[Observation Unit Type] | Protocol REF | Parameter Value[Sampling Date]  | Parameter Value[Sampling Description] | Extract Name | Characteristics[Plant Structure Development Stage] | Term Source REF | Term Accession Number | Characteristics[Plant Anatomical Entity] | Term Source REF | Term Accession Number | Characteristics[External ID] |
|-------------|----------------------------------------|--------------|---------------------------------|---------------------------------------|--------------|----------------------------------------------------|-----------------|-----------------------|------------------------------------------|-----------------|-----------------------|------------------------------|
| exp. unit A |                                        | Sampling     | 2017-06-22                      |                                       | sample I     |                                                    |                 |                       |                                          |                 |                       |                              |
| exp. unit B |                                        | Sampling     | 2017-06-23                      |                                       | sample II    |                                                    |                 |                       |                                          |                 |                       |                              |


### Phenotyping

Including the Phenotyping protocol is mandatory. The Phenotyping protocol points to the file holding all trait (MIAPPE observed variable) definitions. The Phenotyping protocol connects a Sample node to an Assay, optionally through an Extract.  
Note that each assay should be about **a single observation level**.


| Sample Name | Characteristics[Observation Unit Type] | (sampling details) | Protocol REF | Date | Assay Name | Raw Data File | Protocol REF        | Derived Data File |
|-------------|----------------------------------------|--------------------|--------------|------|------------|---------------|---------------------|-------------------|
| sample A    | plant                                  |                    | Phenotyping  |      | assay 1    | file 1        | Data Transformation | file 2            |
| sample B    | plant                                  |                    | Phenotyping  |      | assay 2    | NA            | Data Transformation | file 2            |

The Date column is optional (you will have to add it in the ISA Creator too, if you choose to include it), and in this case it would refer to the timestamp of a measurement done on an observation unit or (MIAPPE) sample. It is up to the user to decide whether the raw or processed files will accompany the metadata. If no raw data file is included, fill the respective fields with "NA". Note that the transition from raw to processed data file is marked using the Data Transformation protocol.



## Trait Definition File

The trait definition file includes the attributes from MIAPPE's Observed Variable section. The column headers are directly taken from MIAPPE, so no mapping is listed here. Do note that, for ontology classes, the ISA-Tab pattern of Term Source REF and Term Accession Number must be followed. An example could be the following:


| Variable ID  | Variable Name                            | Term Source REF | Term Accession Number | Trait         | Term Source REF | Term Accession Number | Method                          | Term Source REF | Term Accession Number | Method Description                                                                                                                                                                                                                                                                                                                                                              | Reference Associated to the Method      | Scale  | Term Source REF | Term Accession Number | Time Scale |
|--------------|------------------------------------------|-----------------|-----------------------|---------------|-----------------|-----------------------|---------------------------------|-----------------|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------|--------|-----------------|-----------------------|------------|
| Ant_Cmp_Cday | Anthesis computed in growing degree days | CO_322          | CO_322:0000794        | Anthesis time | CO_322          | CO_322:0000030        | Growing degree days to anthesis | CO_322          | CO_322:0000189        | Days to anthesis for male flowering was measured in thermal time (GDD: growing degree-days) according to Ritchie J, NeSmith D (1991;Temperature and crop development. Modeling plant and soil systems American Society of Agronomy Madison, Wisconsin USA) with TBASE=8°C and T0=30°C. Plant height was measured at 5 years with a ruler, one year after Botritis inoculation. | http://doi.org/10.2134/agronmonogr31.c2 | °C day | CO_322          | CO_322:0000510        | Date/Time  |

There should be one trait definition file per study. Its filename is indicated in the Study section of the Investigation file. 

Climatological variables should also be listed in the same file, the same way.


#### Events

An external `.csv` file is used to describe concrete occurrences of events. Although external files are outside the scope of ISA validation, the events listed in this file should be declared in the `Study Protocols` section of the Investigation file.

This means that there will be redundancy for certain fields ().

The csv file should look like this:



Each line in this file represents a single occurrence of an Event, and should therefore have exactly one date. The Observation Unit(s) column should list all affected units (multiple units are allowed on each row). If the column is empty, it is understood that this instance of the event affected all units in the study.
However, note some core differences: The Events may each have multiple dates (semicolon-separated). Additionally, different parameter values (dates) may be applied to different observation units.


## Data file

There is no official format for the data file. However, we recommend something like the following:

| Observation unit/Sample | Assay Name | Date                      | var1 | var2 | var3 | ... |
|-------------------------|------------|---------------------------|------|------|------|-----|
| obs. unit 1             | assay1     | 2017-06-10                | 1    | 1.2  | 4    | ... |
| sample 1                | assay5     | 2006-09-27T10:23:21+00:00 | 40   | 38   | 41   | ... |


# Final notes

After filling in all fields, please verify that the names of materials, protocols, parameters and variables are consistent across all ISA files. Do the same for the ontologies used. Depending on the filetype you are using:

* If you are using the ISA Creator and you have a single study, please make sure to edit the produced Investigation file and fill in all necessary fields.
* If you are using the plain text files, please remove the leftmost value in each row (listing the MIAPPE equivalents of each field) in order to get valid ISA files.
* If you are using the spreadsheet template for ISA-Tab, likewise, remove the leftmost column.





#### Pending changes
* The Study Factor Name is what you must later use in the column headings (of the Study file **or Assay file**) to refer to the respective experimental factors. Note that at least 2 factor values must be provided per factor. This can be done in the form of a semicolon-separated list:

