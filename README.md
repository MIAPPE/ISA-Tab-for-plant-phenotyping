**This is a updated work-in-progress version of the phenotyping configuration for ISA metadata model**
The changes result from a set of issues discovered in the old version through testing it with a new release of ISA-API tools, i.e. validator and converter to JSON.
In collaboration with the ISA team, we are trying to come up with a more intuitive and unambiguous representation of phenotypic datasets in ISA model.



ISA-Tab configuration for plant phenotyping experiments
-------------------------------------------------------
is a selection of MIAPPE attributes mapped to the ISA-Tab format. The most essential attributes that seem common to all phenotyping experiments are contained in the Basic Configuration. The configuration constitutes a scaffolding to construct any phenotypic dataset by adding other relevant attributes from the MIAPPE list or whatever information you wish to keep in the dataset. In case of field or greenhouse experiments, the basic attributes common to all of them are contained in Field Configuration and Greenhouse Configuration, respectively. You can extend these configurations by adding more attributes, but the list of the basic environmental information is already there.