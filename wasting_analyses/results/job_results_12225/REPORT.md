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

**Outcome Variable:** swasted

## Predictor Variables

**Intervention Variable:** earlybf

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat      studyid                   country                        earlybf    swasted   n_cell       n
----------  ------------------------  -----------------------------  --------  --------  -------  ------
Birth       ki0047075b-MAL-ED         BANGLADESH                     0                0       85     240
Birth       ki0047075b-MAL-ED         BANGLADESH                     0                1        3     240
Birth       ki0047075b-MAL-ED         BANGLADESH                     1                0      147     240
Birth       ki0047075b-MAL-ED         BANGLADESH                     1                1        5     240
Birth       ki0047075b-MAL-ED         BRAZIL                         0                0      104     183
Birth       ki0047075b-MAL-ED         BRAZIL                         0                1        0     183
Birth       ki0047075b-MAL-ED         BRAZIL                         1                0       79     183
Birth       ki0047075b-MAL-ED         BRAZIL                         1                1        0     183
Birth       ki0047075b-MAL-ED         INDIA                          0                0       76     202
Birth       ki0047075b-MAL-ED         INDIA                          0                1        3     202
Birth       ki0047075b-MAL-ED         INDIA                          1                0      119     202
Birth       ki0047075b-MAL-ED         INDIA                          1                1        4     202
Birth       ki0047075b-MAL-ED         NEPAL                          0                0       89     168
Birth       ki0047075b-MAL-ED         NEPAL                          0                1        2     168
Birth       ki0047075b-MAL-ED         NEPAL                          1                0       75     168
Birth       ki0047075b-MAL-ED         NEPAL                          1                1        2     168
Birth       ki0047075b-MAL-ED         PERU                           0                0       68     279
Birth       ki0047075b-MAL-ED         PERU                           0                1        0     279
Birth       ki0047075b-MAL-ED         PERU                           1                0      211     279
Birth       ki0047075b-MAL-ED         PERU                           1                1        0     279
Birth       ki0047075b-MAL-ED         SOUTH AFRICA                   0                0       90     245
Birth       ki0047075b-MAL-ED         SOUTH AFRICA                   0                1        1     245
Birth       ki0047075b-MAL-ED         SOUTH AFRICA                   1                0      153     245
Birth       ki0047075b-MAL-ED         SOUTH AFRICA                   1                1        1     245
Birth       ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   0                0       10     118
Birth       ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   0                1        0     118
Birth       ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   1                0      107     118
Birth       ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   1                1        1     118
Birth       ki1000109-EE              PAKISTAN                       0                0        0       1
Birth       ki1000109-EE              PAKISTAN                       0                1        0       1
Birth       ki1000109-EE              PAKISTAN                       1                0        1       1
Birth       ki1000109-EE              PAKISTAN                       1                1        0       1
Birth       ki1000304b-SAS-CompFeed   INDIA                          0                0      141     158
Birth       ki1000304b-SAS-CompFeed   INDIA                          0                1        4     158
Birth       ki1000304b-SAS-CompFeed   INDIA                          1                0       13     158
Birth       ki1000304b-SAS-CompFeed   INDIA                          1                1        0     158
Birth       ki1017093c-NIH-Crypto     BANGLADESH                     0                0        4      23
Birth       ki1017093c-NIH-Crypto     BANGLADESH                     0                1        0      23
Birth       ki1017093c-NIH-Crypto     BANGLADESH                     1                0       18      23
Birth       ki1017093c-NIH-Crypto     BANGLADESH                     1                1        1      23
Birth       ki1126311-ZVITAMBO        ZIMBABWE                       0                0     4929   11513
Birth       ki1126311-ZVITAMBO        ZIMBABWE                       0                1      443   11513
Birth       ki1126311-ZVITAMBO        ZIMBABWE                       1                0     5862   11513
Birth       ki1126311-ZVITAMBO        ZIMBABWE                       1                1      279   11513
Birth       kiGH5241-JiVitA-3         BANGLADESH                     0                0    15303   15648
Birth       kiGH5241-JiVitA-3         BANGLADESH                     0                1      252   15648
Birth       kiGH5241-JiVitA-3         BANGLADESH                     1                0       91   15648
Birth       kiGH5241-JiVitA-3         BANGLADESH                     1                1        2   15648
Birth       kiGH5241-JiVitA-4         BANGLADESH                     0                0      205     683
Birth       kiGH5241-JiVitA-4         BANGLADESH                     0                1        3     683
Birth       kiGH5241-JiVitA-4         BANGLADESH                     1                0      473     683
Birth       kiGH5241-JiVitA-4         BANGLADESH                     1                1        2     683
6 months    ki0047075b-MAL-ED         BANGLADESH                     0                0       91     240
6 months    ki0047075b-MAL-ED         BANGLADESH                     0                1        2     240
6 months    ki0047075b-MAL-ED         BANGLADESH                     1                0      147     240
6 months    ki0047075b-MAL-ED         BANGLADESH                     1                1        0     240
6 months    ki0047075b-MAL-ED         BRAZIL                         0                0      114     209
6 months    ki0047075b-MAL-ED         BRAZIL                         0                1        0     209
6 months    ki0047075b-MAL-ED         BRAZIL                         1                0       95     209
6 months    ki0047075b-MAL-ED         BRAZIL                         1                1        0     209
6 months    ki0047075b-MAL-ED         INDIA                          0                0       94     236
6 months    ki0047075b-MAL-ED         INDIA                          0                1        2     236
6 months    ki0047075b-MAL-ED         INDIA                          1                0      137     236
6 months    ki0047075b-MAL-ED         INDIA                          1                1        3     236
6 months    ki0047075b-MAL-ED         NEPAL                          0                0      140     236
6 months    ki0047075b-MAL-ED         NEPAL                          0                1        0     236
6 months    ki0047075b-MAL-ED         NEPAL                          1                0       96     236
6 months    ki0047075b-MAL-ED         NEPAL                          1                1        0     236
6 months    ki0047075b-MAL-ED         PERU                           0                0       71     273
6 months    ki0047075b-MAL-ED         PERU                           0                1        0     273
6 months    ki0047075b-MAL-ED         PERU                           1                0      202     273
6 months    ki0047075b-MAL-ED         PERU                           1                1        0     273
6 months    ki0047075b-MAL-ED         SOUTH AFRICA                   0                0       94     250
6 months    ki0047075b-MAL-ED         SOUTH AFRICA                   0                1        0     250
6 months    ki0047075b-MAL-ED         SOUTH AFRICA                   1                0      153     250
6 months    ki0047075b-MAL-ED         SOUTH AFRICA                   1                1        3     250
6 months    ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   0                0       42     247
6 months    ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   0                1        0     247
6 months    ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   1                0      205     247
6 months    ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   1                1        0     247
6 months    ki1000109-EE              PAKISTAN                       0                0      299     376
6 months    ki1000109-EE              PAKISTAN                       0                1        8     376
6 months    ki1000109-EE              PAKISTAN                       1                0       68     376
6 months    ki1000109-EE              PAKISTAN                       1                1        1     376
6 months    ki1000304b-SAS-CompFeed   INDIA                          0                0     1199    1334
6 months    ki1000304b-SAS-CompFeed   INDIA                          0                1       38    1334
6 months    ki1000304b-SAS-CompFeed   INDIA                          1                0       92    1334
6 months    ki1000304b-SAS-CompFeed   INDIA                          1                1        5    1334
6 months    ki1017093c-NIH-Crypto     BANGLADESH                     0                0       96     715
6 months    ki1017093c-NIH-Crypto     BANGLADESH                     0                1        0     715
6 months    ki1017093c-NIH-Crypto     BANGLADESH                     1                0      619     715
6 months    ki1017093c-NIH-Crypto     BANGLADESH                     1                1        0     715
6 months    ki1113344-GMS-Nepal       NEPAL                          0                0      355     510
6 months    ki1113344-GMS-Nepal       NEPAL                          0                1        4     510
6 months    ki1113344-GMS-Nepal       NEPAL                          1                0      148     510
6 months    ki1113344-GMS-Nepal       NEPAL                          1                1        3     510
6 months    ki1126311-ZVITAMBO        ZIMBABWE                       0                0     3354    7339
6 months    ki1126311-ZVITAMBO        ZIMBABWE                       0                1       34    7339
6 months    ki1126311-ZVITAMBO        ZIMBABWE                       1                0     3916    7339
6 months    ki1126311-ZVITAMBO        ZIMBABWE                       1                1       35    7339
6 months    kiGH5241-JiVitA-3         BANGLADESH                     0                0    16518   16784
6 months    kiGH5241-JiVitA-3         BANGLADESH                     0                1      230   16784
6 months    kiGH5241-JiVitA-3         BANGLADESH                     1                0       36   16784
6 months    kiGH5241-JiVitA-3         BANGLADESH                     1                1        0   16784
6 months    kiGH5241-JiVitA-4         BANGLADESH                     0                0     1727    4833
6 months    kiGH5241-JiVitA-4         BANGLADESH                     0                1       11    4833
6 months    kiGH5241-JiVitA-4         BANGLADESH                     1                0     3073    4833
6 months    kiGH5241-JiVitA-4         BANGLADESH                     1                1       22    4833
24 months   ki0047075b-MAL-ED         BANGLADESH                     0                0       83     211
24 months   ki0047075b-MAL-ED         BANGLADESH                     0                1        0     211
24 months   ki0047075b-MAL-ED         BANGLADESH                     1                0      128     211
24 months   ki0047075b-MAL-ED         BANGLADESH                     1                1        0     211
24 months   ki0047075b-MAL-ED         BRAZIL                         0                0       89     169
24 months   ki0047075b-MAL-ED         BRAZIL                         0                1        0     169
24 months   ki0047075b-MAL-ED         BRAZIL                         1                0       79     169
24 months   ki0047075b-MAL-ED         BRAZIL                         1                1        1     169
24 months   ki0047075b-MAL-ED         INDIA                          0                0       92     227
24 months   ki0047075b-MAL-ED         INDIA                          0                1        1     227
24 months   ki0047075b-MAL-ED         INDIA                          1                0      133     227
24 months   ki0047075b-MAL-ED         INDIA                          1                1        1     227
24 months   ki0047075b-MAL-ED         NEPAL                          0                0      133     228
24 months   ki0047075b-MAL-ED         NEPAL                          0                1        0     228
24 months   ki0047075b-MAL-ED         NEPAL                          1                0       95     228
24 months   ki0047075b-MAL-ED         NEPAL                          1                1        0     228
24 months   ki0047075b-MAL-ED         PERU                           0                0       52     201
24 months   ki0047075b-MAL-ED         PERU                           0                1        0     201
24 months   ki0047075b-MAL-ED         PERU                           1                0      148     201
24 months   ki0047075b-MAL-ED         PERU                           1                1        1     201
24 months   ki0047075b-MAL-ED         SOUTH AFRICA                   0                0       91     235
24 months   ki0047075b-MAL-ED         SOUTH AFRICA                   0                1        0     235
24 months   ki0047075b-MAL-ED         SOUTH AFRICA                   1                0      144     235
24 months   ki0047075b-MAL-ED         SOUTH AFRICA                   1                1        0     235
24 months   ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   0                0       34     214
24 months   ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   0                1        0     214
24 months   ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   1                0      180     214
24 months   ki0047075b-MAL-ED         TANZANIA, UNITED REPUBLIC OF   1                1        0     214
24 months   ki1017093c-NIH-Crypto     BANGLADESH                     0                0       71     514
24 months   ki1017093c-NIH-Crypto     BANGLADESH                     0                1        0     514
24 months   ki1017093c-NIH-Crypto     BANGLADESH                     1                0      439     514
24 months   ki1017093c-NIH-Crypto     BANGLADESH                     1                1        4     514
24 months   ki1113344-GMS-Nepal       NEPAL                          0                0      307     454
24 months   ki1113344-GMS-Nepal       NEPAL                          0                1       11     454
24 months   ki1113344-GMS-Nepal       NEPAL                          1                0      134     454
24 months   ki1113344-GMS-Nepal       NEPAL                          1                1        2     454
24 months   ki1126311-ZVITAMBO        ZIMBABWE                       0                0      158     370
24 months   ki1126311-ZVITAMBO        ZIMBABWE                       0                1       14     370
24 months   ki1126311-ZVITAMBO        ZIMBABWE                       1                0      184     370
24 months   ki1126311-ZVITAMBO        ZIMBABWE                       1                1       14     370
24 months   kiGH5241-JiVitA-3         BANGLADESH                     0                0     8267    8603
24 months   kiGH5241-JiVitA-3         BANGLADESH                     0                1      335    8603
24 months   kiGH5241-JiVitA-3         BANGLADESH                     1                0        1    8603
24 months   kiGH5241-JiVitA-3         BANGLADESH                     1                1        0    8603
24 months   kiGH5241-JiVitA-4         BANGLADESH                     0                0     1649    4735
24 months   kiGH5241-JiVitA-4         BANGLADESH                     0                1       55    4735
24 months   kiGH5241-JiVitA-4         BANGLADESH                     1                0     2957    4735
24 months   kiGH5241-JiVitA-4         BANGLADESH                     1                1       74    4735


The following strata were considered:

* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* agecat: 24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 6 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* agecat: 6 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 6 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: Birth, studyid: ki1000109-EE, country: PAKISTAN
* agecat: Birth, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: Birth, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: Birth, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* agecat: Birth, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: Birth, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: Birth, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: Birth, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: Birth, studyid: ki1000109-EE, country: PAKISTAN
* agecat: Birth, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: Birth, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: Birth, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: Birth, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness



```
## Warning in fold_fun(n, ...): n <= V so using leave-one-out CV
```




# Results Detail

## Results Plots
![](/tmp/06041297-bd0e-4129-8322-123c3ccd0da4/f6128e7c-3fc1-4f7c-a0dd-544eb24e70c7/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/06041297-bd0e-4129-8322-123c3ccd0da4/f6128e7c-3fc1-4f7c-a0dd-544eb24e70c7/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/06041297-bd0e-4129-8322-123c3ccd0da4/f6128e7c-3fc1-4f7c-a0dd-544eb24e70c7/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/06041297-bd0e-4129-8322-123c3ccd0da4/f6128e7c-3fc1-4f7c-a0dd-544eb24e70c7/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat      studyid                   country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  ------------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
Birth       ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                0.0824646   0.0751086   0.0898207
Birth       ki1126311-ZVITAMBO        ZIMBABWE     1                    NA                0.0454323   0.0402236   0.0506411
6 months    ki1000304b-SAS-CompFeed   INDIA        0                    NA                0.0307195   0.0217846   0.0396544
6 months    ki1000304b-SAS-CompFeed   INDIA        1                    NA                0.0515464   0.0256358   0.0774570
6 months    ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                0.0100354   0.0066789   0.0133919
6 months    ki1126311-ZVITAMBO        ZIMBABWE     1                    NA                0.0088585   0.0059366   0.0117805
6 months    kiGH5241-JiVitA-4         BANGLADESH   0                    NA                0.0063291   0.0026465   0.0100118
6 months    kiGH5241-JiVitA-4         BANGLADESH   1                    NA                0.0071082   0.0030192   0.0111973
24 months   ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                0.0813953   0.0404753   0.1223154
24 months   ki1126311-ZVITAMBO        ZIMBABWE     1                    NA                0.0707071   0.0349542   0.1064599
24 months   kiGH5241-JiVitA-4         BANGLADESH   0                    NA                0.0322770   0.0232095   0.0413445
24 months   kiGH5241-JiVitA-4         BANGLADESH   1                    NA                0.0244144   0.0181484   0.0306804


### Parameter: E(Y)


agecat      studyid                   country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  ------------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
Birth       ki1126311-ZVITAMBO        ZIMBABWE     NA                   NA                0.0627117   0.0582829   0.0671405
6 months    ki1000304b-SAS-CompFeed   INDIA        NA                   NA                0.0322339   0.0235219   0.0409459
6 months    ki1126311-ZVITAMBO        ZIMBABWE     NA                   NA                0.0094018   0.0071937   0.0116099
6 months    kiGH5241-JiVitA-4         BANGLADESH   NA                   NA                0.0068281   0.0038634   0.0097927
24 months   ki1126311-ZVITAMBO        ZIMBABWE     NA                   NA                0.0756757   0.0486905   0.1026609
24 months   kiGH5241-JiVitA-4         BANGLADESH   NA                   NA                0.0272439   0.0220352   0.0324527


### Parameter: RR


agecat      studyid                   country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  ------------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
Birth       ki1126311-ZVITAMBO        ZIMBABWE     0                    0                 1.0000000   1.0000000   1.0000000
Birth       ki1126311-ZVITAMBO        ZIMBABWE     1                    0                 0.5509312   0.4764425   0.6370658
6 months    ki1000304b-SAS-CompFeed   INDIA        0                    0                 1.0000000   1.0000000   1.0000000
6 months    ki1000304b-SAS-CompFeed   INDIA        1                    0                 1.6779707   0.9039483   3.1147640
6 months    ki1126311-ZVITAMBO        ZIMBABWE     0                    0                 1.0000000   1.0000000   1.0000000
6 months    ki1126311-ZVITAMBO        ZIMBABWE     1                    0                 0.8827251   0.5518438   1.4120005
6 months    kiGH5241-JiVitA-4         BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
6 months    kiGH5241-JiVitA-4         BANGLADESH   1                    0                 1.1231017   0.5006266   2.5195572
24 months   ki1126311-ZVITAMBO        ZIMBABWE     0                    0                 1.0000000   1.0000000   1.0000000
24 months   ki1126311-ZVITAMBO        ZIMBABWE     1                    0                 0.8686869   0.4257907   1.7722718
24 months   kiGH5241-JiVitA-4         BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
24 months   kiGH5241-JiVitA-4         BANGLADESH   1                    0                 0.7564020   0.5185171   1.1034236


### Parameter: PAR


agecat      studyid                   country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
----------  ------------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
Birth       ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                -0.0197529   -0.0245725   -0.0149333
6 months    ki1000304b-SAS-CompFeed   INDIA        0                    NA                 0.0015144   -0.0009910    0.0040198
6 months    ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                -0.0006336   -0.0030294    0.0017622
6 months    kiGH5241-JiVitA-4         BANGLADESH   0                    NA                 0.0004989   -0.0029816    0.0039795
24 months   ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                -0.0057197   -0.0348034    0.0233641
24 months   kiGH5241-JiVitA-4         BANGLADESH   0                    NA                -0.0050331   -0.0120394    0.0019733


### Parameter: PAF


agecat      studyid                   country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
----------  ------------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
Birth       ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                -0.3149796   -0.3912631   -0.2428788
6 months    ki1000304b-SAS-CompFeed   INDIA        0                    NA                 0.0469816   -0.0343863    0.1219490
6 months    ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                -0.0673904   -0.3545909    0.1589178
6 months    kiGH5241-JiVitA-4         BANGLADESH   0                    NA                 0.0730725   -0.5885469    0.4591317
24 months   ki1126311-ZVITAMBO        ZIMBABWE     0                    NA                -0.0755814   -0.5364141    0.2470289
24 months   kiGH5241-JiVitA-4         BANGLADESH   0                    NA                -0.1847409   -0.4713636    0.0460475