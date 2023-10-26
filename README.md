# South African Bank Risk Dataset

[![DOI](https://zenodo.org/badge/358567011.svg)](https://zenodo.org/badge/latestdoi/358567011)

Give Feedback 📑: [DSFSI Resource Feedback Form](https://docs.google.com/forms/d/e/1FAIpQLSf7S36dyAUPx2egmXbFpnTBuzoRulhL5Elu-N1eoMhaO7v10w/formResponse)

## About Dataset

This repository is an initial pipeline for reading, processing, labelling and classifying unstructured annual reports of South African (SA) banks with the aim of identifying financial risk. It leveraged work by the Corporate Financial Information Environment-Final Report Structure Extractor (CFIE–FRSE) of El-Haj et al. which created a corpus of annual reports of United Kingdom (UK) companies.

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
    │   │   ├── wordlists                     <- Lists of keywords/substrings to extract linguistic features
    │   │   │   ├── causal.txt                <- Causal reasoning wordlist relating to performance commentary, based on a composite wordlist from El-Haj et al.
    │   │   │   ├── causalMartin50.txt        <- Causal reasoning wordlist based on El-Haj et al.
    │   │   │   ├── causalMartinAll.txt       <- Causal reasoning wordlist based on El-Haj et al.
    │   │   │   ├── ForwardLooking.txt        <- Forwardlooking wordlist based on the list proposed by Hussainey et al.
    │   │   │   ├── forwardLookingNew.txt     <- Forwardlooking wordlist based on an updated version of the list proposed by Hussainey et al.
    │   │   │   ├── HenryNeg2006.txt          <- Negative wordlist based on Henry (2006)
    │   │   │   ├── HenryNeg2008.txt          <- Negative wordlist based on Henry (2008)
    │   │   │   ├── HenryPos2006.txt          <- Positive wordlist based on Henry (2006)
    │   │   │   ├── HenryPos2008.txt          <- Positive wordlist based on Henry (2008)
    │   │   │   ├── LMnegative.txt            <- Negative wordlist based on Loughran and McDonald
    │   │   │   ├── LMpositive.txt            <- Positive wordlist based on Loughran and McDonald
    │   │   │   ├── newStrategy.txt           <- Wordlist for identifying strategy-related commentary based on El-Haj et al.
    │   │   │   ├── performance.txt           <- Wordlist for identifying performance-related commentary based on El-Haj et al.
    │   │   │   └── Uncertainty.txt           <- Uncertainty wordlist based on Loughran and McDonald
    │   │   ├── coMap.csv                     <- Reference data: Company mapping file
    │   │   ├── docMap.csv                    <- Reference data: Document mapping file 
    │   │   ├── fileNoMap.csv                 <- Output data: PDF files read that were not in the document mapping file 
    │   │   ├── header.csv                    <- Output data: Header text extracted from PDF files
    │   │   ├── match.csv                     <- Keywords to match and classify headers based on El-Haj et al.
    │   │   └── MatchToC.txt                  <- Keywords to identify Table of Content header
    │   ├── processed
    │   │   ├── docReadability.csv            <- Readability results per document without the text
    │   │   ├── pageBlocks.csv                <- Text blocks per page per document with word counts per page and per wordlist
    │   │   ├── pageText.csv                  <- Text per page per document with word counts per page and per wordlist
    │   │   ├── pageTextRef.csv               <- Text per page of reference report to validate word counts with CFIE–FRSE
    │   │   ├── prob_test_LR.csv              <- Probability of risk on test dataset reports predicted by Logistic Regression
    │   │   └── prob_test_SVMa.csv            <- Probability of risk on test dataset reports predicted by Support Vector Machine with auto gamma
    │   └── raw
    │       ├── Annual Reports                <- PDF files downloaded from internet websites
    │       │   ├── Bank                      <- Annual reports read and processed to create the dataset
    │       │   └── Insurer                   <- Empty folder for insurer reports to be stored in future
    │       └── Other                         <- Other risk-related reports downloaded from internet websites
    ├── notebooks                                       <- Python code
    │   ├── colab                                       <- Code for Google Colaboratory and cloud runtime
    │   │   ├── 1_0_Colab Import.ipynb                  <- Extract PDF text, convert booklets, count words by page and write pageText.csv
    │   │   ├── 2_0_Colab EDA.ipynb                     <- Exploratory Data Analysis (incl. Chi-Square) and write docReadability.csv
    │   │   ├── 3_0_Colab Classifier.ipynb              <- Loop through raw and stemmed/lemmatized tokens as well as classifiers
    │   │   ├── 4_0_Colab Classifier Applied LR.ipynb   <- Logistic Regression prediction, LIME, feature selection and write prob_test_LR.csv
    │   │   └── 4_1_Colab Classifier Applied SVMa.ipynb <- Support Vector Machine (with auto gamma) prediction, LIME, feature selection and write prob_test_SVMa.csv
    │   └── jupyter                                     <- Code for Python 3 and local runtime e.g. using Jupyter or JupyterLab
    │       │── 1_0_Import.ipynb                        <- Extract PDF text, convert booklets, count words by page and write pageText.csv
    │       └── 1_1_Import Count Blocks.ipynb           <- Extract PDF text, convert booklets, count words by page and write pageBlocks.csv
    ├── .gitignore
    ├── LICENSE
    └── README.md

## Online Repository link

* [Zenodo Data Repository](https://zenodo.org/record/6769996) - Link to the data repository.

## Authors

* **Lamont Theron** 
* **Vukosi Marivate** - [@vukosi](https://twitter.com/vukosi)

See also the list of [contributors](https://github.com/dsfsi/za-bank-risk/contributors) who participated in this project.

## License

Data is Licensed under CC 4.0 BY SA
Code is Licences under MIT License.
