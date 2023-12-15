# Pathogen Contextual Data Specification
Metadata template for genomic surveillance of bacterial pathogens for vaccine and AMR purposes

## Rationale
Contextual metadata is crucial for effective genomic surveillance in public health as it provides valuable information about the
samples being analyzed, and facilitates aggregation of data from multiple sources (routine surveillance, research projects) to
identify broader trends across time and geography. In the case of bacterial pathogens, there are templates available for surveillance
and outbreak investigation for foodborne pathogens (e.g. the One Health Enterics template), but no consensus on fields of importance
for genomic surveillance of antimicrobial resistance and vaccine antigens. 

Here we propose a common framework for contextual metadata for genomic surveillance of bacterial pathogens for vaccine and AMR purposes.

This has been developed by members of various groups working on genomic surveillance to inform or monitor vaccine development and 
deployment in relation to a range of pathogens, including those with current vaccines (typhoid, Streptococcus pneumoniae, Group B 
Streptococcus, pertussis, Neisseria meningitidis) and those in various stages of vaccine development (Klebsiella, Shigella, non-typhoidal
Salmonella, etc).

## Approach
This framework incorporates fields proposed in the [PHA4GE Minimal Pathogen Agnostic Contextual Data Specification](https://github.com/pha4ge/minimal-pathogen-agnostic-contextual-data-specification) and [PHA4GE QC tags](https://github.com/pha4ge/contextual_data_QC_tags), and maps to [compulsory fields for INSDC submissions](https://submit.ncbi.nlm.nih.gov). We also draw on the approach to _purpose of sampling_ taken by the [PHA4GE SARS-CoV-2 Contextual Data Specification](Contextual). As with the PHA4GE templates, wherever possible we use terms from the [GenEpiO ontology](https://genepio.org/).

## Specification

| Field | Ontology ID | Definition | Guidance | Expected Value Type | Benefits | Considerations and Privacy |
|---|---|---|---|---|---|---|
| specimen collector sample ID | GENEPIO:0001123 | The user-defined name for the sample. | Original ID given to the sample at the primary laboratory | Alpha-numeric value | Linkage of sample with genomic, lab and epi data; Identifier tracking and establishing chain of custody; Can be considered Personal Health Identifiable (PHI) information | Public facing identifier can be used as replacement when sharing (such as a hash ID) |
| specimen source ID | GENEPIO:0100696 | The identifier assigned to the host or environment from which the specimen was derived (e.g. host subject ID, case ID, environmental site ID) | Provide the identifier for the source of the sample such as the case ID or site ID. | Alpha-numeric value | Allow for deduplication of cases; Traceability | Can be considered Personal Health Identifiable (PHI) information; Public facing identifier can be used as replacement when sharing (such as a hash ID) |
| geo_loc name (country) | GENEPIO:0001181 | The country where the sample was collected. | Use an ontology such as the Gazateer (GAZ). Equivalent to ISO3166-1 | Permitted values | Spatio-temporal analysis; International Health Regulations reporting requirements | If event counts in a country are low, perturbation may be required |
| geo_loc name (state/province/region) | GENEPIO:0001185 | The state/province/region where the sample was collected. | Use an ontology such as the Gazateer ontology (GAZ). Equivalent to ISO3166-2 | Permitted values | Spatio-temporal analysis | If event counts in a state/province/region are low, perturbation may be required |
| sample collected by | GENEPIO:0001153 | The name of the agency that collected the original sample. | The official organization name should be used (avoid abbreviations, alternate names as much as possible). | Auto complete controlled list | Recognition; Provenance; Contact for follow-up | Care should be taken with regards to potential geographical identification associated with organizational name. |
| sequenced by | GENEPIO:0100416 | The name of the agency that generated the sequence. | The official organization name should be used (avoid abbreviations, alternate names as much as possible). | Auto complete controlled list | Recognition; Provenance; Contact for follow-up | Negligible privacy concerns |
| sequence submitted by | GENEPIO:0001159 | The name of the agency that submitted the sequence to a database. | The official organization name should be used (avoid abbreviations, alternate names as much as possible). | Auto complete controlled list | Recognition; Provenance; Contact for follow-up | Negligible privacy concerns |
| data custodian organization name | GENEPIO:0100695 | The name of the organization with authority over how the sample and its associated information can be used. | The official organization name should be used (avoid abbreviations, alternate names as much as possible). | Auto complete controlled list | Jurisdictional authority over data use; Decision-making; Contact for follow-up | Care should be taken with regards to potential geographical identification associated with organizational name. |
| sample collection date | GENEPIO:0001174 | Date on which the sample was collected | For public health analyses this should be defined to the day. | ISO 8601 format (YYYY-MM-DD) | Spatio-temporal analysis | If event counts over a specific time period are low, perturbation may be required. |
| organism | GENEPIO:0001191 | Taxonomic name of the organism. | Use an ontology such as the NCBI Taxonomy Ontology (NCBITaxon). The name of the species should be provided. More granular information (e.g. serotype, sequence type, lineage) should be included in other fields. | Permitted values | Benefits all analyses | Taxonomic determinations may change depending on the method (PCR, culture, WGS etc) and reference database. The “organism” field in the sample record should reflect the taxonomic designation based on sequencing. |
| purpose of sampling | GENEPIO:0001198 | The reason that the sample was collected. | Use an ontology such as the Genomic Epidemiology Ontology (GenEpiO). | Permitted values | Informs potential sampling strategy bias | May have identifiability concerns when used in conjunction with other fields (i.e. geographic and temporal information) |



















