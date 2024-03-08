# Contextual metadata specification for genomic surveillance of bacterial pathogens for vaccine and AMR purposes
_UNDER DEVELOPMENT_

## Rationale
Contextual metadata is crucial for effective genomic surveillance in public health as it provides valuable information about the
samples being analyzed, and facilitates aggregation of data from multiple sources (routine surveillance, research projects) to
identify broader trends across time and geography. In the case of bacterial pathogens, there are templates available for surveillance
and outbreak investigation for foodborne pathogens (e.g. the One Health Enterics template), but no consensus on fields of importance
for genomic surveillance of antimicrobial resistance and vaccine antigens. 

Here we propose a common framework for contextual metadata for genomic surveillance of bacterial pathogens for vaccine and AMR purposes.

This has been developed by members of various groups working on genomic surveillance to inform or monitor vaccine development and 
deployment in relation to a range of pathogens, including those with current vaccines (_Salmonella_ Typhi, _Streptococcus pneumoniae_, Group B 
Streptococcus, pertussis, _Neisseria meningitidis_) and those in various stages of vaccine development (_Klebsiella_, Shigella, non-typhoidal
_Salmonella_, etc).

_THIS SPECIFICATION IS STILL UNDER ACTIVE DEVELOPMENT._ 

_Please feel free to provide suggestions and feedback via the [issues tracker](https://github.com/vaxgenomics/metadata/issues)._

## Approach
This framework incorporates fields proposed in the [PHA4GE Minimal Pathogen Agnostic Contextual Data Specification](https://github.com/pha4ge/minimal-pathogen-agnostic-contextual-data-specification) and [PHA4GE QC tags](https://github.com/pha4ge/contextual_data_QC_tags), and maps to [compulsory fields for INSDC submissions](https://submit.ncbi.nlm.nih.gov). We also draw on the approach to _purpose of sampling_ taken by the [PHA4GE SARS-CoV-2 Contextual Data Specification](https://github.com/pha4ge/SARS-CoV-2-Contextual-Data-Specification). As with the PHA4GE templates, wherever possible we use terms from the [GenEpiO ontology](https://genepio.org/).

This template is intended for dual use - to facilitate data collection and to enable data sharing. Strength of requirements will vary by use case (e.g. some fields are required for data collection but not for data sharing). Differential requirements are indicated by use case in the template. Users may filter based on intended use (data collection or data sharing). Care should be taken to ensure that metadata provided do not result in sharing of patient identifiable information. In addition, no metadata should be shared without relevant ethical approvals.

A template for data entry in Google Sheets is available [here](https://docs.google.com/spreadsheets/d/1U2io0XkCf6a0SkQe0lp76POlIY2gb-mPb9FnZV6C2nw/edit?usp=sharing).

## Contributors

Initial contributors include Megan Carey, Zoe Dyson, Elita Jauneikaite, Stephanie Lo, Dorota Jamrozy, James Meiring, Odile Harrison, Mary Maranga, Kevin Scott, Roisin Ure, Andrew Preston, Nicholas Feasey, John Crump, Kate Baker, Kelly Wyres, Kat Holt.

## Specification
| Ontology ID                                     | Required for data collection?  | Required for data sharing? |Definition                                                                                  | Guidance                                                                                                   | Value Type                           | Benefits                                                     | Considerations & Privacy                                | Linkage(s) with other metadata templates         |
|--------------------------------------------------|------------|------------|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|--------------------------------------|--------------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|
| biosample accession number [GENEPIO:0001139](http://purl.obolibrary.org/obo/GENEPIO_0001139)        | Required   |Required   | The identifier assigned to a BioSample in INSDC archives.                                   | Store the accession returned from the BioSample submission. NCBI BioSamples will have the prefix SAMN, while ENA BioSamples will have the prefix SAMEA.   | Alpha-numeric value                 | Linkage of sample with genomic, lab and epi data; identifier tracking and establishing chain of custody.   |                                                            |                                                      |
| specimen collector sample ID [GENEPIO:0001123](http://purl.obolibrary.org/obo/GENEPIO_0001123)         | Required   | Required   | The user-defined name for the sample.                                                     | Original ID given to the sample at the primary laboratory.                                                  | Alpha-numeric value                 | Linkage of sample with genomic, lab and epi data; identifier tracking and establishing chain of custody; can be considered Personal Health Identifiable (PHI) information.   | Public facing identifier can be used as replacement when sharing (such as a hash ID)     | pha4ge minimal, INSDC required ('sample')        |
| alternative sample ID [GENEPIO:0100427](http://purl.obolibrary.org/obo/GENEPIO_0100427)             | Optional   | Optional  | A data field which describes an alternative sample identifier assigned to the sample by another organization. | Provide any alternative identifiers for the sample here, separated by commas. Alternative identifiers assigned to the sample should be tracked along with original IDs to establish chain of custody. If the information is unknown or cannot be provided, leave blank or provide a null value.   | Alpha-numeric value                 | Additional identifier that can be used to confirm sample identity.   |                                                            |                                                      |
| specimen source ID [GENEPIO:0100696](http://purl.obolibrary.org/obo/GENEPIO_0100696)               | Required   | Required   | The identifier assigned to the host or environment from which the specimen was derived (e.g. host subject ID, case ID, environmental site ID). | Provide the identifier for the source of the sample such as the case ID or site ID.                     | Alpha-numeric value                 | Allow for deduplication of cases; traceability.            | Can be considered Personal Health Identifiable (PHI) information; public facing identifier can be used as replacement when sharing (such as a hash ID).   | pha4ge minimal                                      |
| organism [GENEPIO:0001191](http://purl.obolibrary.org/obo/GENEPIO_0001191)                          | Required   | Required   | Taxonomic name of the organism. Use an ontology such as the NCBI Taxonomy Ontology (NCBITaxon). The name of the species should be provided. | More granular information (e.g. serotype, sequence type, lineage) should be included in other fields.    | Alpha-numeric value                 |                                                            |                                                            | INSDC required                                      |
| citation     [NCIT:C127797](http://purl.obolibrary.org/obo/NCIT_C127797)                                       | Optional   | Recommended   | Pubmed ID or DOI for publications relating to the sample.                                                                            | May describe sample collection, processing, and/or sequencing. Multiple identifiers can be included, separated by commas.                     | Alpha-numeric value                 | Additional context and chain of custody information available from publication.   |                                                            |                                                      |
| sample collected by [GENEPIO:0001153](http://purl.obolibrary.org/obo/GENEPIO_0001153)             | Required   | Required   | The name of the agency that collected the original sample.                                   | The official organization name should be used (avoid abbreviations, alternate names as much as possible).   | Auto complete controlled list       | Recognition; provenance; contact for follow-up.           | Care should be taken with regards to potential geographical identification associated with organizational name.   | pha4ge minimal                                      |
| sequenced by [GENEPIO:0100416](http://purl.obolibrary.org/obo/GENEPIO_0100416)                   | Required   | Required   | The name of the agency that generated the sequence.                                        | The official organization name should be used (avoid abbreviations, alternate names as much as possible).   | Auto complete controlled list       | Recognition; provenance; contact for follow-up.           | Negligible privacy concerns.                            | pha4ge minimal                                      |
| sequence submitted by [GENEPIO:0001159](http://purl.obolibrary.org/obo/GENEPIO_0001159)           | Required   | Required   | The name of the agency that generated the sequence.                                        | The official organization name should be used (avoid abbreviations, alternate names as much as possible).   | Auto complete controlled list       | Recognition; provenance; contact for follow-up.           | Negligible privacy concerns.                            | pha4ge minimal                                      |
| data custodian organization name  [GENEPIO:0100695](http://purl.obolibrary.org/obo/GENEPIO_0100695) | Required | Required | The name of the organization with authority over how the sample and its associated information can be used. | The official organization name should be used (avoid abbreviations, alternate names as much as possible).   | Auto complete controlled list       | Jurisdictional authority over data use; decision-making; contact for follow-up.   | Care should be taken with regards to potential geographical identification associated with organizational name.   | pha4ge minimal                                      |
| sample collection date [GENEPIO:0001174](http://purl.obolibrary.org/obo/GENEPIO_0001174)         | Required   | Required   | Date on which the sample was collected.                                                   | Indicate the date the specimen from which the bacteria was isolated was collected from the host. For public health analyses, this should be defined to the day.   | ISO 8601 format (YYYY-MM-DD)        | Spatio-temporal analysis                                  | If event counts over a specific time period are low, perturbation may be required.   | pha4ge minimal, INSDC required (collection_date)   |
| repeat isolate                                 | Required   | Required   | Please flag any repeat isolates in this column. Repeat isolates are those that represent the same infection episode as one that is already included in the data set. | Leave the column blank for the 'primary' isolate (either the first, or the best quality, genome for each unique case) and indicate 'replicate' for any isolates that represent repeats of a primary isolate. For relevant pathogens, treat mother-baby dyad as the same 'episode' and record as repeats   |                                    |                                                            |                                                            |                                                      |
| geo_loc name (country) [GENEPIO:0001181](http://purl.obolibrary.org/obo/GENEPIO_0001181)         | Required   | Required   | The country where the sample was collected.                                               | Select the country name from the dropdown list in the template.                                                | Permitted values                    | Spatio-temporal analysis; International Health Regulations reporting requirements   | If event counts in a country are low, perturbation may be required.   | pha4ge minimal, INSDC required (geo_loc_name)     |
| geo_loc name (state/province/region) [GENEPIO:0001185](http://purl.obolibrary.org/obo/GENEPIO_0001185)| Recommended | Optional | Provide the state/province/territory name from the GAZ geography ontology.                  | Search for geography terms here: [https://www.ebi.ac.uk/ols/ontologies/gaz](https://www.ebi.ac.uk/ols/ontologies/gaz)   | Permitted values                    | Spatio-temporal analysis                                  | If event counts in a state/province/region are low, perturbation may be required | pha4ge minimal                                      |
| specimen source material category [GENEPIO:0001237](http://purl.obolibrary.org/obo/GENEPIO_0001237)| Required | Required | The type of material from which the specimen was obtained. Specimens are usually categorized as food, body products or tissues, or environmental material | Select option from the dropdown list in the template.                                                           | Permitted values                    |                                                            |                                                            | INSDC required ('isolation_source')                   |
| subject anatomical site [GENEPIO:0000025](http://purl.obolibrary.org/obo/GENEPIO_0000025)        | Required   | Required   | Name of site where the specimen was obtained from, such as a specific organ or tissue.     | Select option from the dropdown list in the template.                                                           | Permitted values                    | Adds clarity regarding the specific site of colonisation or infection.   |                                                            | INSDC optional ('host_tissue_sampled')             |
| subject biospecimen [NCIT:C70699](http://purl.obolibrary.org/obo/NCIT_C70699)        | Required   | Required   | Any material sample taken from a biological entity for testing, diagnostic, propagation, treatment or research purposes.     | Select option from the dropdown list in the template.                                                           | Permitted values                    |    |                                                            |              |
| infection acquired during travel [GENEPIO:0000123](http://purl.obolibrary.org/obo/GENEPIO_0000123)| Required   | Was infection acquired during travel?                                                     | Based on public health or study definition; this may be defined differently for different organisms. Select response from the dropdown list in the template.                            | Permitted values                    | Understanding origin of pathogen causing infection, spatio-temporal analysis   | Definitions can be complex and setting-specific; details should be recorded elsewhere (e.g. study or surveillance protocol). Harmonisation of definitions may be required for downstream data aggregation and analysis.   | INSDC required                                      |
| travel destination [GENEPIO:0001783](http://purl.obolibrary.org/obo/GENEPIO_0001783)             | Recommended   | Optional   | If infection was acquired during travel, please indicate country of travel where infection is assumed to have occurred. | Example: if the bacteria was isolated in Australia from a patient who became infected during recent travel to India, you would record Country = Australia, and Travel Country = India. | Permitted values                    | Understanding origin of pathogen causing infection, spatio-temporal analysis   |                                                            |                                                      |
| travel note                                      | Recommended   | Optional   | Use this column to record additional information about travel associated isolates.           | Example: if the city or sub-national region of travel is known, please enter it here.                        | Alpha numeric value                 | Understanding origin of pathogen causing infection, spatio-temporal analysis   |                                                            |                                                      |
| host [GENEPIO:0100629](http://purl.obolibrary.org/obo/GENEPIO_0100628)              | Required if host-associated   | Required   | The natural (as opposed to laboratory) host to the organism from which the sample was obtained. | Use the full taxonomic name, eg, "Homo sapiens".                   | Alpha-numeric value      |     |     |  
| host age [GENEPIO:0001392](http://purl.obolibrary.org/obo/GENEPIO_0001392)                       | Required | Optional| Age of the host at the time of sampling.                                                  | Provide the age in years, except for children under 1 years. For those younger than 1 year, please use d to indicate age in days (e.g. 6d = 6 days) or m to indicate age in months (e.g. 9m = 9 months).   | Auto complete controlled list      | Assessment of age-specific distribution of AMR and/or impact of vaccination   | Can be considered Personal Health Identifiable (PHI) information. Should not be shared without relevant ethical approval. Consider privacy concerns and indicate age group instead where suitable (see below) |                                                      |
| host age category [GENEPIO:0001394](http://purl.obolibrary.org/obo/GENEPIO_0001394)              | Required   | Required   | Age category/bin of the individual from whom the bacteria was isolated (used instead of 'Age' in case of ethical/privacy concerns around sharing exact age). | Determination of relevant age groups will vary by pathogen. Example age groups could include: early neonates (0-6 days), late neonates (7-27 days), post-neonatal infants (28-364 days), young children (1-4 years), older children (5-9 years), young adolescents (10-14 years), older adolescents (15-19 years), young adults (20-24 years), adults (25-59 years, grouped in 5 year intervals), older adults (60-99 years, grouped in 5 year intervals, plus a category for people older than 100 years). Source: http://tinyurl.com/agecategory                    | Auto complete controlled list      | Assessment of age-specific distribution of AMR and/or impact of vaccination   | Can be considered Personal Health Identifiable (PHI) information, depending on resolution and potential to triangulate with additional available metadata. Should not be shared without relevant ethical approval.   |         Source of potential age categories: https://www.thelancet.com/journals/lanhl/article/PIIS2666-7568(21)00115-X/fulltext#tbl1                                             |
| host sex [GENEPIO:0000031](http://purl.obolibrary.org/obo/GENEPIO_0000031)                       | Required | Optional| Sex of the individual from whom the bacteria was isolated. ('Female', 'Male', 'Not Provided', 'Restricted Access') | Use the dropdown list provided in the template.                                                           | Auto complete controlled list      | Assessment of sex-specific distribution of AMR and/or impact of vaccination   | Can be considered Personal Health Identifiable (PHI) information. Should not be shared without relevant ethical approval.   |                                                      |
| host health state [GENEPIO:0001388](http://purl.obolibrary.org/obo/GENEPIO_0001388)             | Required | Recommended| Health status of the host at the time of sample collection.                                  | Indicate whether this pathogen isolate represents symptomatic infection or asymptomatic carriage. Use the dropdown list provided in the template.                            | Auto complete controlled list      | Assessment of carriage vs. incident disease                  |                                                            |                                                      |
| host disease [GENEPIO:0001391](http://purl.obolibrary.org/obo/GENEPIO_0001391)                   | Required | Recommended | A host data field which describes the name of the disease experienced by the host.          | Controlled vocabulary - [https://www.ncbi.nlm.nih.gov/mesh/](https://www.ncbi.nlm.nih.gov/mesh/)             | Alpha numeric value                 |                                                            | If you are creating a template for a specific pathogen or syndrome, consider providing additional guidance for appropriate values for host health state, disease, outcome, and complications. You may wish to define/restrict values based on organism/study.   | INSDC required                                      |
| host disease outcome [GENEPIO:0001390](http://purl.obolibrary.org/obo/GENEPIO_0001390)            | Recommended | Optional | Final outcome of disease                                                                   | If isolated from infection, indicate outcome of infection (e.g. “lived, died, lost to follow up)." Use the dropdown list provided in the template.                                | Auto complete controlled list      | Assessment of impact of AMR and/or vaccination on host outcome.   |                                                            | INDSC optional (host_disease_outcome)              |
| host vaccination status [GENEPIO:0001404](http://purl.obolibrary.org/obo/GENEPIO_0001404)        | Recommended | Recommended | The vaccination status of the host (fully vaccinated, partially vaccinated, or not vaccinated). | This should be based on the definitions used for the study. However, recommend also to record specific details of vaccine type, dose, timing in the subsequent fields to facilitate harmonisation of definitions in downstream analyses. Use the dropdown list provided in the template. | Permitted values                    | Assessment of impact of vaccination on AMR                   |                                                            | pha4ge SARS-CoV2 contextual data                    |
| vaccine name [GENEPIO:0001405](http://purl.obolibrary.org/obo/GENEPIO_0001405)                   | Recommended | Optional| The name of the vaccine(s) administered.                                                | Provide the scientific/research name of the vaccine followed by the name of the manufacturer, separated by a comma. If an individual received doses of different vaccines, provide the information in the order received, separated by a semi-colon. | Alpha numeric value                 | Assessment of product-specific impact of vaccination on AMR   |                                                            | pha4ge SARS-CoV2 contextual data                    |
| number of vaccine doses received [GENEPIO:0001406](http://purl.obolibrary.org/obo/GENEPIO_0001406)| Recommended | Optional| The number of doses of the vaccine received by the host.                                   | Record how many doses of the vaccine the host has received.                                                  | Permitted values                    | Assessment of impact of full vs partial vs no vaccination on AMR   |                                                            | pha4ge SARS-CoV2 contextual data                    |
| first dose vaccination date [GENEPIO:0001407](http://purl.obolibrary.org/obo/GENEPIO_0001407)    | Recommended | Optional|  The date the host was first vaccinated.                                                 | Provide the first dose vaccination date in ISO 8601 standard format "YYYY-MM-DD".                           | Alpha numeric value                 | Spatio-temporal analysis of impact of vaccine on AMR          |                                                            | pha4ge SARS-CoV2 contextual data                    |
| last dose vaccination date [GENEPIO:0001408](http://purl.obolibrary.org/obo/GENEPIO_0001408)     | Recommended | Optional|  The date the host received their last dose of vaccine.                                   | Provide the last dose vaccination date in ISO 8601 standard format "YYYY-MM-DD".                            | Alpha numeric value                 | Spatio-temporal analysis of impact of vaccine on AMR          |                                                            | pha4ge SARS-CoV2 contextual data                    |
| quality control method name [GENEPIO:0100557](http://purl.obolibrary.org/obo/GENEPIO_0100557)    | Required| Recommended| The name of the method used to assess whether a sequence passed a predetermined quality control threshold. | Example: ncov-tools                                                                                         | Alpha numeric value                 |                                                            |                                                            | pha4ge QC tags                                      |
| quality control method version [GENEPIO:0100558](http://purl.obolibrary.org/obo/GENEPIO_0100558) | Required| Recommended| The version number of the method used to assess whether a sequence passed a predetermined quality control threshold. | example: 1.2.3                                                                                            | Alpha numeric value                 |                                                            |                                                            | pha4ge QC tags                                      |
| quality control determination [GENEPIO:0100559](http://purl.obolibrary.org/obo/GENEPIO_0100559)  | Required| Recommended| The determination of a quality control assessment.                                       | Example: sequence failed quality control [GENEPIO:0100564](http://purl.obolibrary.org/obo/GENEPIO_0100564)                                                | Permitted values                    |                                                            |                                                            | pha4ge QC tags                                      |
| quality control issues [GENEPIO:0100560](http://purl.obolibrary.org/obo/GENEPIO_0100560)         | Required| Recommended|The reason contributing to, or causing, a low quality determination in a quality control assessment. | Example: low average genome coverage [GENEPIO:0100570](http://purl.obolibrary.org/obo/GENEPIO_0100570)                                                    | Permitted values                    |                                                            |                                                            | pha4ge QC tags                                      |
| quality control details [GENEPIO:0100561](http://purl.obolibrary.org/obo/GENEPIO_0100561)        | Required | Recommended|The details surrounding a low quality determination in a quality control assessment.      | Example: CT value of 39. Low viral load. Low DNA concentration after amplification.                          | Alpha numeric value                 |                                                            |                                                            | pha4ge QC tags                                      |
| purpose of sampling [GENEPIO:0001198](http://purl.obolibrary.org/obo/GENEPIO_0001198)           | Required   | Required   | The reason that the sample was collected.                                               | Indicate the sampling frame, and whether it was targeted to specific types of clinical or pathogen phenotypes. Example: Targeted [Cluster/Outbreak investigation], Non-targeted [Surveillance]. Select option from drop-down menu. | Permitted values.                   | Informs potential sampling strategy bias.                 | May have identifiability concerns when used in conjunction with other fields (i.e. geographic and temporal information). |                                                      |
| purpose of sampling detail                        | Recommended   | Optional   | Describe the purpose of sampling further.                                                | Example: Targeted surveillance for carbapenem-resistant isolates; Investigation of typhoid outbreak linked to food vendor                                                     | Alpha-numerical value                |                                                            |                                                            |                                                      |
| sample collection project name field              | Recommended   | Optional   |  A data field which describes the project/initiative/program for which the sample was collected. | Provide the name of the project and/or the project ID here. If the information is unknown or cannot be provided, leave blank or provide a null value. | Alpha-numerical value                | Useful in meta-analyses, enables stratification of data by study and/or site to generate regional prevalence estimates.   |                                                            |                                                      |
| population vaccination status                    | Recommended | Recommended | Indicate when the target population from which the samples were collected was first vaccinated against the target organism. | E.g. '2019', 'No vaccination'                                                                               | Alpha-numerical value                |                                                            |                                                            |                                                      |
| population vaccination coverage                  | Recommended |Recommended | What is the estimated vaccine coverage in this population at the time of sampling?         | E.g. 'None', '90%'                                                                                        | Alpha-numerical value                |                                                            |                                                            |                                                      |
| population vaccine name                          | Optional   | Optional   | Which vaccine/s are used in this population?                                               | Guidance under development                                                              | Alpha-numerical value                |                                                            |                                                            |                                                      |
