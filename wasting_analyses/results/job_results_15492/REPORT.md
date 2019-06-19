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

**Intervention Variable:** predfeed3

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat      studyid               country                        predfeed3    swasted   n_cell       n
----------  --------------------  -----------------------------  ----------  --------  -------  ------
Birth       ki0047075b-MAL-ED     BANGLADESH                     0                  0       32     227
Birth       ki0047075b-MAL-ED     BANGLADESH                     0                  1        2     227
Birth       ki0047075b-MAL-ED     BANGLADESH                     1                  0      187     227
Birth       ki0047075b-MAL-ED     BANGLADESH                     1                  1        6     227
Birth       ki0047075b-MAL-ED     BRAZIL                         0                  0       80     177
Birth       ki0047075b-MAL-ED     BRAZIL                         0                  1        0     177
Birth       ki0047075b-MAL-ED     BRAZIL                         1                  0       97     177
Birth       ki0047075b-MAL-ED     BRAZIL                         1                  1        0     177
Birth       ki0047075b-MAL-ED     INDIA                          0                  0       42     193
Birth       ki0047075b-MAL-ED     INDIA                          0                  1        1     193
Birth       ki0047075b-MAL-ED     INDIA                          1                  0      144     193
Birth       ki0047075b-MAL-ED     INDIA                          1                  1        6     193
Birth       ki0047075b-MAL-ED     NEPAL                          0                  0       67     166
Birth       ki0047075b-MAL-ED     NEPAL                          0                  1        2     166
Birth       ki0047075b-MAL-ED     NEPAL                          1                  0       95     166
Birth       ki0047075b-MAL-ED     NEPAL                          1                  1        2     166
Birth       ki0047075b-MAL-ED     PERU                           0                  0       88     265
Birth       ki0047075b-MAL-ED     PERU                           0                  1        0     265
Birth       ki0047075b-MAL-ED     PERU                           1                  0      177     265
Birth       ki0047075b-MAL-ED     PERU                           1                  1        0     265
Birth       ki0047075b-MAL-ED     SOUTH AFRICA                   0                  0      143     231
Birth       ki0047075b-MAL-ED     SOUTH AFRICA                   0                  1        1     231
Birth       ki0047075b-MAL-ED     SOUTH AFRICA                   1                  0       87     231
Birth       ki0047075b-MAL-ED     SOUTH AFRICA                   1                  1        0     231
Birth       ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                  0       64     114
Birth       ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                  1        1     114
Birth       ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                  0       49     114
Birth       ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                  1        0     114
Birth       ki1000109-EE          PAKISTAN                       0                  0        0       1
Birth       ki1000109-EE          PAKISTAN                       0                  1        0       1
Birth       ki1000109-EE          PAKISTAN                       1                  0        1       1
Birth       ki1000109-EE          PAKISTAN                       1                  1        0       1
Birth       kiGH5241-JiVitA-3     BANGLADESH                     0                  0     1371   15136
Birth       kiGH5241-JiVitA-3     BANGLADESH                     0                  1       26   15136
Birth       kiGH5241-JiVitA-3     BANGLADESH                     1                  0    13519   15136
Birth       kiGH5241-JiVitA-3     BANGLADESH                     1                  1      220   15136
Birth       kiGH5241-JiVitA-4     BANGLADESH                     0                  0        3      31
Birth       kiGH5241-JiVitA-4     BANGLADESH                     0                  1        0      31
Birth       kiGH5241-JiVitA-4     BANGLADESH                     1                  0       28      31
Birth       kiGH5241-JiVitA-4     BANGLADESH                     1                  1        0      31
6 months    ki0047075b-MAL-ED     BANGLADESH                     0                  0       34     237
6 months    ki0047075b-MAL-ED     BANGLADESH                     0                  1        0     237
6 months    ki0047075b-MAL-ED     BANGLADESH                     1                  0      201     237
6 months    ki0047075b-MAL-ED     BANGLADESH                     1                  1        2     237
6 months    ki0047075b-MAL-ED     BRAZIL                         0                  0       93     209
6 months    ki0047075b-MAL-ED     BRAZIL                         0                  1        0     209
6 months    ki0047075b-MAL-ED     BRAZIL                         1                  0      116     209
6 months    ki0047075b-MAL-ED     BRAZIL                         1                  1        0     209
6 months    ki0047075b-MAL-ED     INDIA                          0                  0       54     233
6 months    ki0047075b-MAL-ED     INDIA                          0                  1        1     233
6 months    ki0047075b-MAL-ED     INDIA                          1                  0      174     233
6 months    ki0047075b-MAL-ED     INDIA                          1                  1        4     233
6 months    ki0047075b-MAL-ED     NEPAL                          0                  0      101     233
6 months    ki0047075b-MAL-ED     NEPAL                          0                  1        0     233
6 months    ki0047075b-MAL-ED     NEPAL                          1                  0      132     233
6 months    ki0047075b-MAL-ED     NEPAL                          1                  1        0     233
6 months    ki0047075b-MAL-ED     PERU                           0                  0       87     270
6 months    ki0047075b-MAL-ED     PERU                           0                  1        0     270
6 months    ki0047075b-MAL-ED     PERU                           1                  0      183     270
6 months    ki0047075b-MAL-ED     PERU                           1                  1        0     270
6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   0                  0      159     248
6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   0                  1        3     248
6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   1                  0       86     248
6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   1                  1        0     248
6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                  0      149     240
6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                  1        0     240
6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                  0       91     240
6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                  1        0     240
6 months    ki1000109-EE          PAKISTAN                       0                  0       24     375
6 months    ki1000109-EE          PAKISTAN                       0                  1        2     375
6 months    ki1000109-EE          PAKISTAN                       1                  0      342     375
6 months    ki1000109-EE          PAKISTAN                       1                  1        7     375
6 months    ki1113344-GMS-Nepal   NEPAL                          0                  0       79     458
6 months    ki1113344-GMS-Nepal   NEPAL                          0                  1        0     458
6 months    ki1113344-GMS-Nepal   NEPAL                          1                  0      372     458
6 months    ki1113344-GMS-Nepal   NEPAL                          1                  1        7     458
6 months    kiGH5241-JiVitA-3     BANGLADESH                     0                  0     1461   16253
6 months    kiGH5241-JiVitA-3     BANGLADESH                     0                  1       29   16253
6 months    kiGH5241-JiVitA-3     BANGLADESH                     1                  0    14571   16253
6 months    kiGH5241-JiVitA-3     BANGLADESH                     1                  1      192   16253
6 months    kiGH5241-JiVitA-4     BANGLADESH                     0                  0       12      89
6 months    kiGH5241-JiVitA-4     BANGLADESH                     0                  1        0      89
6 months    kiGH5241-JiVitA-4     BANGLADESH                     1                  0       77      89
6 months    kiGH5241-JiVitA-4     BANGLADESH                     1                  1        0      89
24 months   ki0047075b-MAL-ED     BANGLADESH                     0                  0       30     208
24 months   ki0047075b-MAL-ED     BANGLADESH                     0                  1        0     208
24 months   ki0047075b-MAL-ED     BANGLADESH                     1                  0      178     208
24 months   ki0047075b-MAL-ED     BANGLADESH                     1                  1        0     208
24 months   ki0047075b-MAL-ED     BRAZIL                         0                  0       71     169
24 months   ki0047075b-MAL-ED     BRAZIL                         0                  1        0     169
24 months   ki0047075b-MAL-ED     BRAZIL                         1                  0       97     169
24 months   ki0047075b-MAL-ED     BRAZIL                         1                  1        1     169
24 months   ki0047075b-MAL-ED     INDIA                          0                  0       54     225
24 months   ki0047075b-MAL-ED     INDIA                          0                  1        1     225
24 months   ki0047075b-MAL-ED     INDIA                          1                  0      169     225
24 months   ki0047075b-MAL-ED     INDIA                          1                  1        1     225
24 months   ki0047075b-MAL-ED     NEPAL                          0                  0       97     225
24 months   ki0047075b-MAL-ED     NEPAL                          0                  1        0     225
24 months   ki0047075b-MAL-ED     NEPAL                          1                  0      128     225
24 months   ki0047075b-MAL-ED     NEPAL                          1                  1        0     225
24 months   ki0047075b-MAL-ED     PERU                           0                  0       62     199
24 months   ki0047075b-MAL-ED     PERU                           0                  1        0     199
24 months   ki0047075b-MAL-ED     PERU                           1                  0      136     199
24 months   ki0047075b-MAL-ED     PERU                           1                  1        1     199
24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   0                  0      151     232
24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   0                  1        0     232
24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   1                  0       81     232
24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   1                  1        0     232
24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                  0      131     210
24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                  1        0     210
24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                  0       79     210
24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                  1        0     210
24 months   ki1113344-GMS-Nepal   NEPAL                          0                  0       66     404
24 months   ki1113344-GMS-Nepal   NEPAL                          0                  1        2     404
24 months   ki1113344-GMS-Nepal   NEPAL                          1                  0      327     404
24 months   ki1113344-GMS-Nepal   NEPAL                          1                  1        9     404
24 months   kiGH5241-JiVitA-3     BANGLADESH                     0                  0      783    8313
24 months   kiGH5241-JiVitA-3     BANGLADESH                     0                  1       35    8313
24 months   kiGH5241-JiVitA-3     BANGLADESH                     1                  0     7204    8313
24 months   kiGH5241-JiVitA-3     BANGLADESH                     1                  1      291    8313
24 months   kiGH5241-JiVitA-4     BANGLADESH                     0                  0       14     151
24 months   kiGH5241-JiVitA-4     BANGLADESH                     0                  1        1     151
24 months   kiGH5241-JiVitA-4     BANGLADESH                     1                  0      132     151
24 months   kiGH5241-JiVitA-4     BANGLADESH                     1                  1        4     151


The following strata were considered:

* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
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
* agecat: 6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
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
* agecat: Birth, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness



```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_mean is not a
## cv-aware learner, so self$predict_fold reverts to self$predict
```

```
## Warning in learner$predict_fold(learner_task, cv_fold): Lrnr_glm_TRUE is
## not a cv-aware learner, so self$predict_fold reverts to self$predict
```




# Results Detail

## Results Plots
![](/tmp/e853917a-899b-4f75-a429-b52ee08ae4d5/657c167a-2ce3-4805-96d4-959bbbc0b692/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/e853917a-899b-4f75-a429-b52ee08ae4d5/657c167a-2ce3-4805-96d4-959bbbc0b692/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/e853917a-899b-4f75-a429-b52ee08ae4d5/657c167a-2ce3-4805-96d4-959bbbc0b692/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/e853917a-899b-4f75-a429-b52ee08ae4d5/657c167a-2ce3-4805-96d4-959bbbc0b692/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat      studyid             country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  ------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
Birth       kiGH5241-JiVitA-3   BANGLADESH   0                    NA                0.0186113   0.0117909   0.0254317
Birth       kiGH5241-JiVitA-3   BANGLADESH   1                    NA                0.0160128   0.0134397   0.0185859
6 months    kiGH5241-JiVitA-3   BANGLADESH   0                    NA                0.0194631   0.0118914   0.0270348
6 months    kiGH5241-JiVitA-3   BANGLADESH   1                    NA                0.0130055   0.0108029   0.0152080
24 months   kiGH5241-JiVitA-3   BANGLADESH   0                    NA                0.0427873   0.0285666   0.0570080
24 months   kiGH5241-JiVitA-3   BANGLADESH   1                    NA                0.0388259   0.0340741   0.0435776


### Parameter: E(Y)


agecat      studyid             country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  ------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
Birth       kiGH5241-JiVitA-3   BANGLADESH   NA                   NA                0.0162526   0.0138117   0.0186936
6 months    kiGH5241-JiVitA-3   BANGLADESH   NA                   NA                0.0135975   0.0114712   0.0157238
24 months   kiGH5241-JiVitA-3   BANGLADESH   NA                   NA                0.0392157   0.0346894   0.0437419


### Parameter: RR


agecat      studyid             country      intervention_level   baseline_level     estimate    ci_lower   ci_upper
----------  ------------------  -----------  -------------------  ---------------  ----------  ----------  ---------
Birth       kiGH5241-JiVitA-3   BANGLADESH   0                    0                 1.0000000   1.0000000   1.000000
Birth       kiGH5241-JiVitA-3   BANGLADESH   1                    0                 0.8603806   0.5798318   1.276672
6 months    kiGH5241-JiVitA-3   BANGLADESH   0                    0                 1.0000000   1.0000000   1.000000
6 months    kiGH5241-JiVitA-3   BANGLADESH   1                    0                 0.6682129   0.4381616   1.019050
24 months   kiGH5241-JiVitA-3   BANGLADESH   0                    0                 1.0000000   1.0000000   1.000000
24 months   kiGH5241-JiVitA-3   BANGLADESH   1                    0                 0.9074164   0.6378732   1.290859


### Parameter: PAR


agecat      studyid             country      intervention_level   baseline_level      estimate     ci_lower    ci_upper
----------  ------------------  -----------  -------------------  ---------------  -----------  -----------  ----------
Birth       kiGH5241-JiVitA-3   BANGLADESH   0                    NA                -0.0023587   -0.0088930   0.0041757
6 months    kiGH5241-JiVitA-3   BANGLADESH   0                    NA                -0.0058656   -0.0130007   0.0012695
24 months   kiGH5241-JiVitA-3   BANGLADESH   0                    NA                -0.0035716   -0.0170293   0.0098861


### Parameter: PAF


agecat      studyid             country      intervention_level   baseline_level      estimate     ci_lower    ci_upper
----------  ------------------  -----------  -------------------  ---------------  -----------  -----------  ----------
Birth       kiGH5241-JiVitA-3   BANGLADESH   0                    NA                -0.1451252   -0.6296991   0.1953658
6 months    kiGH5241-JiVitA-3   BANGLADESH   0                    NA                -0.4313736   -1.0653766   0.0080113
24 months   kiGH5241-JiVitA-3   BANGLADESH   0                    NA                -0.0910758   -0.4944944   0.2034454