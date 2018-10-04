---
title: "Risk Factor Analysis"
output: 
  html_document:
    keep_md: TRUE
    self_contained: true
required_packages:  ['github://HBGD-UCB/longbowRiskFactors','github://jeremyrcoyle/skimr@vector_types', 'github://tlverse/delayed']
params:
  roles:
    value:
      - exclude
      - strata
      - id
      - W
      - A
      - Y
  data: 
    value: 
      type: 'web'
      uri: 'https://raw.githubusercontent.com/HBGD-UCB/longbowRiskFactors/master/inst/sample_data/birthwt_data.rdata'
  nodes:
    value:
      strata: ['study_id', 'mrace']
      id: ['subjid']
      W: ['apgar1', 'apgar5', 'gagebrth', 'mage', 'meducyrs', 'sexn']
      A: ['parity_cat']
      Y: ['haz01']
  script_params:
    value:
      parallelize:
        input: checkbox
        value: FALSE
      count_A:
        input: checkbox
        value: TRUE
      count_Y:
        input: checkbox
        value: TRUE        
      baseline_level:
        input: 'character'
        value: "[1,2)"
  output_directory:
    value: ''
editor_options: 
  chunk_output_type: console
---







## Methods
## Outcome Variable

**Outcome Variable:** pers_wast

## Predictor Variables

**Intervention Variable:** hfoodsec

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat        studyid                 country        hfoodsec                pers_wast   n_cell       n
------------  ----------------------  -------------  ---------------------  ----------  -------  ------
0-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Secure                     0      152     194
0-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Secure                     1        9     194
0-24 months   ki0047075b-MAL-ED       BANGLADESH     Mildly Food Insecure            0        4     194
0-24 months   ki0047075b-MAL-ED       BANGLADESH     Mildly Food Insecure            1        0     194
0-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Insecure                   0       27     194
0-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Insecure                   1        2     194
0-24 months   ki0047075b-MAL-ED       BRAZIL         Food Secure                     0        3     129
0-24 months   ki0047075b-MAL-ED       BRAZIL         Food Secure                     1        0     129
0-24 months   ki0047075b-MAL-ED       BRAZIL         Mildly Food Insecure            0       11     129
0-24 months   ki0047075b-MAL-ED       BRAZIL         Mildly Food Insecure            1        0     129
0-24 months   ki0047075b-MAL-ED       BRAZIL         Food Insecure                   0      115     129
0-24 months   ki0047075b-MAL-ED       BRAZIL         Food Insecure                   1        0     129
0-24 months   ki0047075b-MAL-ED       INDIA          Food Secure                     0      173     212
0-24 months   ki0047075b-MAL-ED       INDIA          Food Secure                     1       17     212
0-24 months   ki0047075b-MAL-ED       INDIA          Mildly Food Insecure            0        3     212
0-24 months   ki0047075b-MAL-ED       INDIA          Mildly Food Insecure            1        2     212
0-24 months   ki0047075b-MAL-ED       INDIA          Food Insecure                   0       16     212
0-24 months   ki0047075b-MAL-ED       INDIA          Food Insecure                   1        1     212
0-24 months   ki0047075b-MAL-ED       NEPAL          Food Secure                     0       93     128
0-24 months   ki0047075b-MAL-ED       NEPAL          Food Secure                     1        1     128
0-24 months   ki0047075b-MAL-ED       NEPAL          Mildly Food Insecure            0       14     128
0-24 months   ki0047075b-MAL-ED       NEPAL          Mildly Food Insecure            1        1     128
0-24 months   ki0047075b-MAL-ED       NEPAL          Food Insecure                   0       19     128
0-24 months   ki0047075b-MAL-ED       NEPAL          Food Insecure                   1        0     128
0-24 months   ki0047075b-MAL-ED       PERU           Food Secure                     0       27     112
0-24 months   ki0047075b-MAL-ED       PERU           Food Secure                     1        0     112
0-24 months   ki0047075b-MAL-ED       PERU           Mildly Food Insecure            0       29     112
0-24 months   ki0047075b-MAL-ED       PERU           Mildly Food Insecure            1        0     112
0-24 months   ki0047075b-MAL-ED       PERU           Food Insecure                   0       55     112
0-24 months   ki0047075b-MAL-ED       PERU           Food Insecure                   1        1     112
0-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Secure                     0      131     232
0-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Secure                     1        0     232
0-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Mildly Food Insecure            0       18     232
0-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Mildly Food Insecure            1        1     232
0-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Insecure                   0       81     232
0-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Insecure                   1        1     232
0-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Secure                     0       74     534
0-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Secure                     1        4     534
0-24 months   ki1017093-NIH-Birth     BANGLADESH     Mildly Food Insecure            0      379     534
0-24 months   ki1017093-NIH-Birth     BANGLADESH     Mildly Food Insecure            1       38     534
0-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Insecure                   0       34     534
0-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Insecure                   1        5     534
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Secure                     0      425     730
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Secure                     1       13     730
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Mildly Food Insecure            0      197     730
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Mildly Food Insecure            1       10     730
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Insecure                   0       82     730
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Insecure                   1        3     730
0-24 months   ki1113344-GMS-Nepal     NEPAL          Food Secure                     0      716    1148
0-24 months   ki1113344-GMS-Nepal     NEPAL          Food Secure                     1      112    1148
0-24 months   ki1113344-GMS-Nepal     NEPAL          Mildly Food Insecure            0      150    1148
0-24 months   ki1113344-GMS-Nepal     NEPAL          Mildly Food Insecure            1       12    1148
0-24 months   ki1113344-GMS-Nepal     NEPAL          Food Insecure                   0      120    1148
0-24 months   ki1113344-GMS-Nepal     NEPAL          Food Insecure                   1       38    1148
0-24 months   kiGH5241-JiVitA-3       BANGLADESH     Food Secure                     0    15022   31300
0-24 months   kiGH5241-JiVitA-3       BANGLADESH     Food Secure                     1      768   31300
0-24 months   kiGH5241-JiVitA-3       BANGLADESH     Mildly Food Insecure            0     9740   31300
0-24 months   kiGH5241-JiVitA-3       BANGLADESH     Mildly Food Insecure            1      606   31300
0-24 months   kiGH5241-JiVitA-3       BANGLADESH     Food Insecure                   0     4752   31300
0-24 months   kiGH5241-JiVitA-3       BANGLADESH     Food Insecure                   1      412   31300
0-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Secure                     0     4827   10229
0-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Secure                     1      399   10229
0-24 months   kiGH5241-JiVitA-4       BANGLADESH     Mildly Food Insecure            0     3341   10229
0-24 months   kiGH5241-JiVitA-4       BANGLADESH     Mildly Food Insecure            1      326   10229
0-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Insecure                   0     1235   10229
0-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Insecure                   1      101   10229
0-6 months    ki0047075b-MAL-ED       BANGLADESH     Food Secure                     0      156     194
0-6 months    ki0047075b-MAL-ED       BANGLADESH     Food Secure                     1        5     194
0-6 months    ki0047075b-MAL-ED       BANGLADESH     Mildly Food Insecure            0        4     194
0-6 months    ki0047075b-MAL-ED       BANGLADESH     Mildly Food Insecure            1        0     194
0-6 months    ki0047075b-MAL-ED       BANGLADESH     Food Insecure                   0       28     194
0-6 months    ki0047075b-MAL-ED       BANGLADESH     Food Insecure                   1        1     194
0-6 months    ki0047075b-MAL-ED       BRAZIL         Food Secure                     0        3     129
0-6 months    ki0047075b-MAL-ED       BRAZIL         Food Secure                     1        0     129
0-6 months    ki0047075b-MAL-ED       BRAZIL         Mildly Food Insecure            0       11     129
0-6 months    ki0047075b-MAL-ED       BRAZIL         Mildly Food Insecure            1        0     129
0-6 months    ki0047075b-MAL-ED       BRAZIL         Food Insecure                   0      115     129
0-6 months    ki0047075b-MAL-ED       BRAZIL         Food Insecure                   1        0     129
0-6 months    ki0047075b-MAL-ED       INDIA          Food Secure                     0      175     211
0-6 months    ki0047075b-MAL-ED       INDIA          Food Secure                     1       14     211
0-6 months    ki0047075b-MAL-ED       INDIA          Mildly Food Insecure            0        3     211
0-6 months    ki0047075b-MAL-ED       INDIA          Mildly Food Insecure            1        2     211
0-6 months    ki0047075b-MAL-ED       INDIA          Food Insecure                   0       15     211
0-6 months    ki0047075b-MAL-ED       INDIA          Food Insecure                   1        2     211
0-6 months    ki0047075b-MAL-ED       NEPAL          Food Secure                     0       91     127
0-6 months    ki0047075b-MAL-ED       NEPAL          Food Secure                     1        2     127
0-6 months    ki0047075b-MAL-ED       NEPAL          Mildly Food Insecure            0       14     127
0-6 months    ki0047075b-MAL-ED       NEPAL          Mildly Food Insecure            1        1     127
0-6 months    ki0047075b-MAL-ED       NEPAL          Food Insecure                   0       19     127
0-6 months    ki0047075b-MAL-ED       NEPAL          Food Insecure                   1        0     127
0-6 months    ki0047075b-MAL-ED       PERU           Food Secure                     0       27     112
0-6 months    ki0047075b-MAL-ED       PERU           Food Secure                     1        0     112
0-6 months    ki0047075b-MAL-ED       PERU           Mildly Food Insecure            0       29     112
0-6 months    ki0047075b-MAL-ED       PERU           Mildly Food Insecure            1        0     112
0-6 months    ki0047075b-MAL-ED       PERU           Food Insecure                   0       56     112
0-6 months    ki0047075b-MAL-ED       PERU           Food Insecure                   1        0     112
0-6 months    ki0047075b-MAL-ED       SOUTH AFRICA   Food Secure                     0      129     230
0-6 months    ki0047075b-MAL-ED       SOUTH AFRICA   Food Secure                     1        1     230
0-6 months    ki0047075b-MAL-ED       SOUTH AFRICA   Mildly Food Insecure            0       18     230
0-6 months    ki0047075b-MAL-ED       SOUTH AFRICA   Mildly Food Insecure            1        1     230
0-6 months    ki0047075b-MAL-ED       SOUTH AFRICA   Food Insecure                   0       81     230
0-6 months    ki0047075b-MAL-ED       SOUTH AFRICA   Food Insecure                   1        0     230
0-6 months    ki1113344-GMS-Nepal     NEPAL          Food Secure                     0      648    1048
0-6 months    ki1113344-GMS-Nepal     NEPAL          Food Secure                     1      104    1048
0-6 months    ki1113344-GMS-Nepal     NEPAL          Mildly Food Insecure            0      146    1048
0-6 months    ki1113344-GMS-Nepal     NEPAL          Mildly Food Insecure            1        8    1048
0-6 months    ki1113344-GMS-Nepal     NEPAL          Food Insecure                   0      130    1048
0-6 months    ki1113344-GMS-Nepal     NEPAL          Food Insecure                   1       12    1048
6-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Secure                     0      147     194
6-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Secure                     1       14     194
6-24 months   ki0047075b-MAL-ED       BANGLADESH     Mildly Food Insecure            0        4     194
6-24 months   ki0047075b-MAL-ED       BANGLADESH     Mildly Food Insecure            1        0     194
6-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Insecure                   0       26     194
6-24 months   ki0047075b-MAL-ED       BANGLADESH     Food Insecure                   1        3     194
6-24 months   ki0047075b-MAL-ED       BRAZIL         Food Secure                     0        3     129
6-24 months   ki0047075b-MAL-ED       BRAZIL         Food Secure                     1        0     129
6-24 months   ki0047075b-MAL-ED       BRAZIL         Mildly Food Insecure            0       11     129
6-24 months   ki0047075b-MAL-ED       BRAZIL         Mildly Food Insecure            1        0     129
6-24 months   ki0047075b-MAL-ED       BRAZIL         Food Insecure                   0      115     129
6-24 months   ki0047075b-MAL-ED       BRAZIL         Food Insecure                   1        0     129
6-24 months   ki0047075b-MAL-ED       INDIA          Food Secure                     0      167     212
6-24 months   ki0047075b-MAL-ED       INDIA          Food Secure                     1       23     212
6-24 months   ki0047075b-MAL-ED       INDIA          Mildly Food Insecure            0        3     212
6-24 months   ki0047075b-MAL-ED       INDIA          Mildly Food Insecure            1        2     212
6-24 months   ki0047075b-MAL-ED       INDIA          Food Insecure                   0       15     212
6-24 months   ki0047075b-MAL-ED       INDIA          Food Insecure                   1        2     212
6-24 months   ki0047075b-MAL-ED       NEPAL          Food Secure                     0       94     128
6-24 months   ki0047075b-MAL-ED       NEPAL          Food Secure                     1        0     128
6-24 months   ki0047075b-MAL-ED       NEPAL          Mildly Food Insecure            0       14     128
6-24 months   ki0047075b-MAL-ED       NEPAL          Mildly Food Insecure            1        1     128
6-24 months   ki0047075b-MAL-ED       NEPAL          Food Insecure                   0       19     128
6-24 months   ki0047075b-MAL-ED       NEPAL          Food Insecure                   1        0     128
6-24 months   ki0047075b-MAL-ED       PERU           Food Secure                     0       27     111
6-24 months   ki0047075b-MAL-ED       PERU           Food Secure                     1        0     111
6-24 months   ki0047075b-MAL-ED       PERU           Mildly Food Insecure            0       28     111
6-24 months   ki0047075b-MAL-ED       PERU           Mildly Food Insecure            1        0     111
6-24 months   ki0047075b-MAL-ED       PERU           Food Insecure                   0       55     111
6-24 months   ki0047075b-MAL-ED       PERU           Food Insecure                   1        1     111
6-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Secure                     0      130     231
6-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Secure                     1        0     231
6-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Mildly Food Insecure            0       18     231
6-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Mildly Food Insecure            1        1     231
6-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Insecure                   0       81     231
6-24 months   ki0047075b-MAL-ED       SOUTH AFRICA   Food Insecure                   1        1     231
6-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Secure                     0       72     492
6-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Secure                     1        4     492
6-24 months   ki1017093-NIH-Birth     BANGLADESH     Mildly Food Insecure            0      332     492
6-24 months   ki1017093-NIH-Birth     BANGLADESH     Mildly Food Insecure            1       45     492
6-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Insecure                   0       33     492
6-24 months   ki1017093-NIH-Birth     BANGLADESH     Food Insecure                   1        6     492
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Secure                     0      402     697
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Secure                     1       22     697
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Mildly Food Insecure            0      179     697
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Mildly Food Insecure            1       15     697
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Insecure                   0       74     697
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH     Food Insecure                   1        5     697
6-24 months   ki1113344-GMS-Nepal     NEPAL          Food Secure                     0      666    1120
6-24 months   ki1113344-GMS-Nepal     NEPAL          Food Secure                     1      142    1120
6-24 months   ki1113344-GMS-Nepal     NEPAL          Mildly Food Insecure            0      136    1120
6-24 months   ki1113344-GMS-Nepal     NEPAL          Mildly Food Insecure            1       24    1120
6-24 months   ki1113344-GMS-Nepal     NEPAL          Food Insecure                   0      114    1120
6-24 months   ki1113344-GMS-Nepal     NEPAL          Food Insecure                   1       38    1120
6-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Secure                     0     4501    9783
6-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Secure                     1      507    9783
6-24 months   kiGH5241-JiVitA-4       BANGLADESH     Mildly Food Insecure            0     3085    9783
6-24 months   kiGH5241-JiVitA-4       BANGLADESH     Mildly Food Insecure            1      400    9783
6-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Insecure                   0     1149    9783
6-24 months   kiGH5241-JiVitA-4       BANGLADESH     Food Insecure                   1      141    9783


The following strata were considered:

* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months, studyid: ki1017093-NIH-Birth, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 0-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki1017093-NIH-Birth, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months, studyid: ki1017093-NIH-Birth, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki1017093-NIH-Birth, country: BANGLADESH

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness







# Results Detail

## Results Plots
![](/tmp/5fafd92c-25f5-4de0-8940-bf2f89202b63/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/5fafd92c-25f5-4de0-8940-bf2f89202b63/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/5fafd92c-25f5-4de0-8940-bf2f89202b63/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/5fafd92c-25f5-4de0-8940-bf2f89202b63/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat        studyid                 country      intervention_level     baseline_level     estimate    ci_lower    ci_upper
------------  ----------------------  -----------  ---------------------  ---------------  ----------  ----------  ----------
0-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure            NA                0.1352657   0.1022925   0.1682389
0-24 months   ki1113344-GMS-Nepal     NEPAL        Mildly Food Insecure   NA                0.0740741   0.0169912   0.1311569
0-24 months   ki1113344-GMS-Nepal     NEPAL        Food Insecure          NA                0.2405063   0.1461788   0.3348339
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Food Secure            NA                0.0486384   0.0432883   0.0539885
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Mildly Food Insecure   NA                0.0585734   0.0517960   0.0653507
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Food Insecure          NA                0.0797831   0.0684326   0.0911336
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure            NA                0.0763490   0.0647894   0.0879086
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Mildly Food Insecure   NA                0.0889010   0.0739026   0.1038994
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Insecure          NA                0.0755988   0.0535037   0.0976939
0-6 months    ki1113344-GMS-Nepal     NEPAL        Food Secure            NA                0.1382979   0.1033714   0.1732244
0-6 months    ki1113344-GMS-Nepal     NEPAL        Mildly Food Insecure   NA                0.0519481   0.0023325   0.1015636
0-6 months    ki1113344-GMS-Nepal     NEPAL        Food Insecure          NA                0.0845070   0.0197469   0.1492672
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Food Secure            NA                0.0518868   0.0307599   0.0730137
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Mildly Food Insecure   NA                0.0773196   0.0397073   0.1149318
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Food Insecure          NA                0.0632911   0.0095607   0.1170215
6-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure            NA                0.1757426   0.1385963   0.2128889
6-24 months   ki1113344-GMS-Nepal     NEPAL        Mildly Food Insecure   NA                0.1500000   0.0716848   0.2283152
6-24 months   ki1113344-GMS-Nepal     NEPAL        Food Insecure          NA                0.2500000   0.1525616   0.3474384
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure            NA                0.1012380   0.0864161   0.1160600
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Mildly Food Insecure   NA                0.1147776   0.0972279   0.1323273
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Insecure          NA                0.1093023   0.0815486   0.1370560


### Parameter: E(Y)


agecat        studyid                 country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  ----------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki1113344-GMS-Nepal     NEPAL        NA                   NA                0.1411150   0.1126097   0.1696202
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   NA                   NA                0.0570607   0.0529791   0.0611424
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   NA                   NA                0.0807508   0.0720315   0.0894701
0-6 months    ki1113344-GMS-Nepal     NEPAL        NA                   NA                0.1183206   0.0906395   0.1460017
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   NA                   NA                0.0602582   0.0425793   0.0779372
6-24 months   ki1113344-GMS-Nepal     NEPAL        NA                   NA                0.1821429   0.1501475   0.2141382
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   NA                   NA                0.1071246   0.0962953   0.1179539


### Parameter: RR


agecat        studyid                 country      intervention_level     baseline_level     estimate    ci_lower   ci_upper
------------  ----------------------  -----------  ---------------------  ---------------  ----------  ----------  ---------
0-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure            Food Secure       1.0000000   1.0000000   1.000000
0-24 months   ki1113344-GMS-Nepal     NEPAL        Mildly Food Insecure   Food Secure       0.5476190   0.2440385   1.228850
0-24 months   ki1113344-GMS-Nepal     NEPAL        Food Insecure          Food Secure       1.7780289   1.1204380   2.821563
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Food Secure            Food Secure       1.0000000   1.0000000   1.000000
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Mildly Food Insecure   Food Secure       1.2042622   1.0293414   1.408908
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Food Insecure          Food Secure       1.6403325   1.3753517   1.956365
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure            Food Secure       1.0000000   1.0000000   1.000000
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Mildly Food Insecure   Food Secure       1.1644027   0.9309710   1.456365
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Insecure          Food Secure       0.9901738   0.7201880   1.361372
0-6 months    ki1113344-GMS-Nepal     NEPAL        Food Secure            Food Secure       1.0000000   1.0000000   1.000000
0-6 months    ki1113344-GMS-Nepal     NEPAL        Mildly Food Insecure   Food Secure       0.3756244   0.1398632   1.008798
0-6 months    ki1113344-GMS-Nepal     NEPAL        Food Insecure          Food Secure       0.6110509   0.2726833   1.369293
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Food Secure            Food Secure       1.0000000   1.0000000   1.000000
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Mildly Food Insecure   Food Secure       1.4901593   0.7901861   2.810192
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Food Insecure          Food Secure       1.2197929   0.4757539   3.127446
6-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure            Food Secure       1.0000000   1.0000000   1.000000
6-24 months   ki1113344-GMS-Nepal     NEPAL        Mildly Food Insecure   Food Secure       0.8535211   0.4859503   1.499121
6-24 months   ki1113344-GMS-Nepal     NEPAL        Food Insecure          Food Secure       1.4225352   0.9130749   2.216255
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure            Food Secure       1.0000000   1.0000000   1.000000
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Mildly Food Insecure   Food Secure       1.1337402   0.9259962   1.388091
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Insecure          Food Secure       1.0796569   0.8041589   1.449538


### Parameter: PAR


agecat        studyid                 country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  ----------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure          NA                 0.0058493   -0.0123562    0.0240547
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Food Secure          NA                 0.0084223    0.0045199    0.0123248
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure          NA                 0.0044018   -0.0036283    0.0124319
0-6 months    ki1113344-GMS-Nepal     NEPAL        Food Secure          NA                -0.0199773   -0.0353220   -0.0046325
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Food Secure          NA                 0.0083715   -0.0063203    0.0230632
6-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure          NA                 0.0064003   -0.0139130    0.0267135
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure          NA                 0.0058866   -0.0039881    0.0157612


### Parameter: PAF


agecat        studyid                 country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  ----------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure          NA                 0.0414505   -0.0964327    0.1619940
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   Food Secure          NA                 0.1476029    0.0766830    0.2130754
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure          NA                 0.0545107   -0.0502223    0.1487993
0-6 months    ki1113344-GMS-Nepal     NEPAL        Food Secure          NA                -0.1688401   -0.3013163   -0.0498502
6-24 months   ki1017093c-NIH-Crypto   BANGLADESH   Food Secure          NA                 0.1389263   -0.1388657    0.3489594
6-24 months   ki1113344-GMS-Nepal     NEPAL        Food Secure          NA                 0.0351388   -0.0829764    0.1403718
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   Food Secure          NA                 0.0549508   -0.0421981    0.1430439