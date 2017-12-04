**This is an updated, work-in-progress version of the phenotyping configuration for ISA metadata model**

The changes in this branch result from a set of issues discovered in the old version through testing it with a new release of ISA-API tools, i.e. validator and converter to JSON.
In collaboration with the ISA team, we are trying to come up with a more intuitive and unambiguous representation of phenotypic datasets in ISA model.

The main changes include:
  - extracting all general properties of a study (i.e. Study start, Study Duration, Growth facility, Geographic location) and grouping them as parameters of the `Protocol` "Growth" in the Study file. This ensures that all the remaining `Characteristics` of `Source` describe only the biological objects under study.
  - assuming that `Sample` corresponds to an experimental unit (observation unit) that hosts some amount of the biological objects described as a `Source`, and thus grouping all the technical information about the experimental unit (type of experimental unit, id, block, column, row, etc) as `Characteristics` of `Sample` in the Study file
  - renaming `Characteristics[Organism part]` to `Parameter Value[Organism part]` of a newly added `Protocol` "Phenotyping" in the Assay file. The reason for this change is that in each Assay different parts of the organisms from the same experimental unit (`Sample`) can be investigated, which would lead to multivalued `Characteristics`. Since `Protocol` is declared in an Assay, its parameters should be separated from those in the other Assays.
  - moving `Parameter Value[Trait Definition File]` from "Data Transformation" `Protocol` to "Phenotyping" `Protocol`


ISA-Tab configuration for plant phenotyping experiments
-------------------------------------------------------
is a selection of MIAPPE attributes mapped to the ISA-Tab format. The most essential attributes that seem common to all phenotyping experiments are contained in the Basic Configuration. The configuration constitutes a scaffolding to construct any phenotypic dataset by adding other relevant attributes from the MIAPPE list or whatever information you wish to keep in the dataset. In case of field or greenhouse experiments, the basic attributes common to all of them are contained in Field Configuration and Greenhouse Configuration, respectively. You can extend these configurations by adding more attributes, but the list of the basic environmental information is already there.