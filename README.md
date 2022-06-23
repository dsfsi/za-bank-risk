# South African Bank Risk Dataset

## About Dataset

This repository is an initial pipeline for reading, processing, labelling and classifying unstructured annual reports of South
African (SA) banks with the aim of identifying financial risk. It leveraged work by the Corporate Financial Information Environment-Final Report Structure Extractor (CFIE–FRSE) of El-Haj et al. which created a corpus of annual reports of United Kingdom (UK) companies.

## About Data collection methodology

A register of banks licensed in SA was used to download annual reports from company websites and online portals.  Company structures, trading practices
and branding complicated the collection. The South African Bank of Athens Limited (‘SABA’) is an example, trading as Grobank after acquisition by GroCapital Holdings Proprietary Limited (‘GroCapital Holdings’). Subsidiary and group companies were analysed as separate entities. This applied to ABSA, Investec, Nedbank and Standard Bank.
A UK report was selected as reference to validate pre-processing results against the CFIE–FRSE tool. Pre-porcessing also mapped reports to companies and years, and labeled reports as positive or negative with respect to risk. Data was prepared by extracting text, counting all words and those in wordlists, and validating results against the reference. Processing included Bag of Words, word embedding, feature scaling and topic analysis. Modelling entailed various classifiers for which results were compared and the best performing models were applied in a prediction use case.

## Description of the data

Of the potential 297 annual reports from 2009 to 2019, 258 were sourced with the balance not found or the bank was not operational that year. Only 7 reports comprised multiple documents so for simplicity each document was treated as a report.

## Repository Organisation
------------
    ├── data
    │   ├── interim
    │   ├── processed
    │   └── raw
    │       ├── Annual Reports                <- PDF files downloaded from internet websites
    │       │     ├── Bank
    │       │     └── Insurer
    │       └── Other                         <- Other risk-related reports downloaded from internet websites
    ├── notebooks                             <- Python code
    │   ├── colab                             <- Code for Google Colaboratory and cloud runtime
    │   └── jupyter                           <- Code for Python 3 and local runtime e.g. using Jupyter or JupyterLab
    ├── .gitignore
    ├── LICENSE
    └── README.md

## Online Repository link

* [Zenodo Data Repository](https://doi.org/10.5281/zenodo.4682843) - Link to the data repository.

## Authors

* **Lamont Theron** 
* **Vukosi Marivate** - [@vukosi](https://twitter.com/vukosi)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments
* Media Monitoring Africa
