Plant phenotyping experiments in ISA model
==========================================

[ISA](https://isa-specs.readthedocs.io/en/latest/) experimental metadata model allows to manage scientific datasets by structuring experimental metadata and linking files with resulting data. A textual serialisation formats of ISA model is [ISA-Tab](https://isa-specs.readthedocs.io/en/latest/isatab.html).

We provide ISA-Tab configurations for plant phenotyping experiments described according to MIAPPE 1.0 recommendations. Using the commmon configurations  allows to create predicatable and unambiguous representation of phenotypic datasets in ISA model.

ISA-Tab configurations
----------------------

ISA configuration is a selection of MIAPPE attributes mapped to the ISA-Tab format. The most essential attributes that seem common to all phenotyping experiments are contained in the Basic Configuration. This configuration constitutes a scaffolding to construct any phenotypic dataset by adding other relevant attributes from the MIAPPE list or whatever information you wish to keep in the dataset. In case of field or greenhouse experiments, the basic attributes common and specific to those environments are contained in Field Configuration and Greenhouse Configuration, respectively. You can extend these configurations by adding more attributes to extend the basic environmental information or experimental objects' description.

**isaconfig-phenotyping** contains the configurations for constructing datasets with [ISA-tools](http://isa-tools.org/software-suite/).

**isa-templates** provides templates of ISA text files, prefilled with protocols and material ID's (to demonstrate biological and technical replications). You can can simply edit it in you Notepad or Spreadsheet, however, it is still advisable to validate with ISA-tools. There is also an equivalent Excel workbook with ISA files as sheets (for simplicity, it's not part of ISA standard) with export-to-txt macro.

**datasets** includes examples of ISA-formatted phenotyping datasets.


Updates
-------

**v1.0**

[First version](https://github.com/MIAPPE/ISA-Tab-for-plant-phenotyping/tree/v1.0.0) of MIAPPE-ISA mapping was published in 2016 as a result of TransPLANT project. Later changes to this version result from a set of issues discovered through testing it with a new release of ISA-API tools, i.e. validator and converter to JSON. All corrections to the initial configuration can be found in branch [1.0](https://github.com/MIAPPE/ISA-Tab-for-plant-phenotyping/tree/v1.0). As compared to the description in the paper, the main changes are:
  - extracting all general properties of a study (i.e. Study start, Study Duration, Growth facility, Geographic location) and grouping them as parameters of the `Protocol` "Growth" in the Study file. This ensures that all the remaining `Characteristics` of `Source` describe only the biological objects under study.
  - assuming that `Sample` corresponds to an experimental unit (observation unit) that hosts some amount of the biological objects described as a `Source`, and thus grouping all the technical information about the experimental unit (type of experimental unit, id, block, column, row, etc) as `Characteristics` of `Sample` in the Study file
  - renaming `Characteristics[Organism part]` to `Parameter Value[Organism part]` of a newly added `Protocol` "Phenotyping" in the Assay file. The reason for this change is that in each Assay different parts of the organisms from the same experimental unit (`Sample`) can be investigated, which would lead to multivalued `Characteristics`. Since `Protocol` is declared in an Assay, its parameters should be separated from those in the other Assays.
  - moving `Parameter Value[Trait Definition File]` from "Data Transformation" `Protocol` to "Phenotyping" `Protocol`
