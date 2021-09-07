# COVID-19- mRNA Vaccine Degradation Prediction with Bi-directional GRU

## Blog

[Medium Blog](https://baotramduong.medium.com/covid-19-mrna-vaccine-degradation-prediction-with-deep-learning-bidirectional-gru-5c3549823057 "Blog")

## Introduction

<img src = '../main/Data & Images/RNA COVID-19.png'>

COVID-19 is the most important pandemic of the 21st century. As of September 2021, there have been a total of 222M cases, resulted in 4.59M deaths worldwide (Wordometer, 2021). 

Vaccination is an efficient approach to stop the pandemic with 95% effectiveness and is available to entire countries at the lowest cost. There are two vaccine designs: gene based and protein based. A protein-based vaccine teaches the immune system to fight the viruses or bacteria while the gene-based vaccines mimic the natural infection by holding the genetic instructions of the cell to generate the antigen, and particularly the surface spike protein in the case of coronaviruses (Abbasi, 2020). 

Messenger RNA molecules (mRNA) vaccines have taken the lead as the fastest vaccine candidates for COVID-19 because of their capacity for rapid development, high potency, safe administration and potential for low-cost manufacture (Qaid et al., 2021). mRNA vaccine acts by training the body to recognize and response to the proteins produced by disease-causing organisms such as viruses or bacteria.

However, one of the biggest challenges right now is how to design super stable mRNA. Researchers have observed that RNA molecules have the tendency to spontaneously degrade. This is a serious limitation - a single cut can render the mRNA vaccine useless. Currently, little is known on the details of where in the backbone of a given RNA is most prone to being affected. Without this knowledge, current mRNA vaccines against COVID-19 must be prepared and shipped under intense refrigeration, and are unlikely to reach more than a tiny fraction of human beings on the planet unless they can be stabilized.

## Data Source

<img src = '../main/Data & Images/df_info.png' height='75%' width='75%'>

* sequence - (1x107 string) Describes the RNA sequence, a combination of A, G, U, and C for each sample. Should be 107 characters long, and the first 68 bases should correspond to the 68 positions specified in seq_scored (note: indexed starting at 0).

* structure - (1x107 string) An array of (, ), and . characters that describe whether a base is estimated to be paired or unpaired. Paired bases are denoted by opening and closing parentheses e.g. (….) means that base 0 is paired to base 5, and bases 1–4 are unpaired.

* predicted_loop_type - (1x107 string) Describes the structural context (also referred to as 'loop type')of each character in sequence. Loop types assigned by bpRNA from Vienna RNAfold 2 structure. From the bpRNA_documentation: S: paired "Stem" M: Multiloop I: Internal loop B: Bulge H: Hairpin loop E: dangling End X: eXternal loop

* reactivity - (1x68 vector) An array of floating point numbers, should have the same length as seq_scored. These numbers are reactivity values for the first 68 bases as denoted in sequence, and used to determine the likely secondary structure of the RNA sample.

* deg_pH10 - (1x68 vector) An array of floating point numbers, should have the same length as seq_scored. These numbers are reactivity values for the first 68 bases as denoted in sequence, and used to determine the likelihood of degradation at the base/linkage after incubating without magnesium at high pH (pH 10).

* deg_Mg_pH10 - (1x68 vector) An array of floating point numbers, should have the same length as seq_scored. These numbers are reactivity values for the first 68 bases as denoted in sequence, and used to determine the likelihood of degradation at the base/linkage after incubating with magnesium in high pH (pH 10).

* deg_50C - (1x68 vector) An array of floating point numbers, should have the same length as seq_scored. These numbers are reactivity values for the first 68 bases as denoted in sequence, and used to determine the likelihood of degradation at the base/linkage after incubating without magnesium at high temperature (50 degrees Celsius).
* deg_Mg_50C - (1x68 vector) An array of floating point numbers, should have the same length as seq_scored. These numbers are reactivity values for the first 68 bases as denoted in sequence, and used to determine the likelihood of degradation at the base/linkage after incubating with magnesium at high temperature (50 degrees Celsius).

## Summary of Findings

### EDA

<img src = '../main/Data & Images/structure distribution.png'>

<img src = '../main/Data & Images/sequence distribution.png'>

<img src = '../main/Data & Images/predicted loop type distribution.png'>

<img src = '../main/Data & Images/average reactivity at each position.png'>

### Modeling

<img src = '../main/Data & Images/model_summary.png'>

<img src = '../main/Data & Images/acc_loss_curve.png'>

### Prediction

<img src = '../main/Data & Images/prediction dataframe.png'>

## Reference
Abbasi (2020) Abbasi J. Covid-19 and mRNA vaccines - first large test for a new approach. JAMA. 2020;324(12):1125–1127. doi: 10.1001/jama.2020.16866.

Coronavirus cases. Worldometer. (Sep 2021). https://www.worldometers.info/coronavirus/.
Phi, M. (2020, June 28). Illustrated Guide to LSTM’s and GRU’s: A step by step explanation. Medium. https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21.

Qaid, T. S., Mazaar, H., Alqahtani, M. S., Raweh, A. A., & Alakwaa, W. (2021). Deep sequence modeling for predicting COVID-19 mRNA vaccine degradation. PeerJ. Computer science, 7, e597. https://doi.org/10.7717/peerj-cs.597

Qureshi, M. (n.d.). COVID-19 mRNA Vaccine Degradation Prediction [MOOC]. Coursera. https://www.coursera.org/projects/covid-19-mrna-vaccine-degradation-prediction

Stanford University (2020) Stanford University OpenVaccine: COVID-19 mRNA vaccine degradation prediction. [8 October 2020]. https://www.kaggle.com/c/stanford-covid-vaccine/data
