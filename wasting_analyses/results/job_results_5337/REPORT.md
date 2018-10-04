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

**Outcome Variable:** wast_rec90d

## Predictor Variables

**Intervention Variable:** predfeed3

**Adjustment Set:**

* arm
* sex
* month
* brthmon
* W_mage
* meducyrs
* feducyrs
* hhwealth_quart
* hfoodsec
* W_mhtcm
* vagbrth
* W_gagebrth
* W_birthwt
* W_birthlen
* W_nrooms
* W_nchldlt5
* W_parity
* impfloor
* impsan
* safeh20
* delta_W_mage
* delta_meducyrs
* delta_feducyrs
* delta_hhwealth_quart
* delta_hfoodsec
* delta_W_mhtcm
* delta_vagbrth
* delta_W_gagebrth
* delta_W_birthwt
* delta_W_birthlen
* delta_W_nrooms
* delta_W_nchldlt5
* delta_W_parity
* delta_impfloor
* delta_impsan
* delta_safeh20

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat        studyid               country                        predfeed3    wast_rec90d   n_cell       n
------------  --------------------  -----------------------------  ----------  ------------  -------  ------
0-24 months   ki0047075b-MAL-ED     BANGLADESH                     0                      0        5     118
0-24 months   ki0047075b-MAL-ED     BANGLADESH                     0                      1        6     118
0-24 months   ki0047075b-MAL-ED     BANGLADESH                     1                      0       37     118
0-24 months   ki0047075b-MAL-ED     BANGLADESH                     1                      1       70     118
0-24 months   ki0047075b-MAL-ED     BRAZIL                         0                      0        2      23
0-24 months   ki0047075b-MAL-ED     BRAZIL                         0                      1        7      23
0-24 months   ki0047075b-MAL-ED     BRAZIL                         1                      0        4      23
0-24 months   ki0047075b-MAL-ED     BRAZIL                         1                      1       10      23
0-24 months   ki0047075b-MAL-ED     INDIA                          0                      0       22     177
0-24 months   ki0047075b-MAL-ED     INDIA                          0                      1       31     177
0-24 months   ki0047075b-MAL-ED     INDIA                          1                      0       48     177
0-24 months   ki0047075b-MAL-ED     INDIA                          1                      1       76     177
0-24 months   ki0047075b-MAL-ED     NEPAL                          0                      0        5      92
0-24 months   ki0047075b-MAL-ED     NEPAL                          0                      1       34      92
0-24 months   ki0047075b-MAL-ED     NEPAL                          1                      0       15      92
0-24 months   ki0047075b-MAL-ED     NEPAL                          1                      1       38      92
0-24 months   ki0047075b-MAL-ED     PERU                           0                      0        1      32
0-24 months   ki0047075b-MAL-ED     PERU                           0                      1       12      32
0-24 months   ki0047075b-MAL-ED     PERU                           1                      0        5      32
0-24 months   ki0047075b-MAL-ED     PERU                           1                      1       14      32
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   0                      0        7      78
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   0                      1       47      78
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   1                      0        6      78
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   1                      1       18      78
0-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                      0        7      45
0-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                      1       24      45
0-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                      0        1      45
0-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                      1       13      45
0-24 months   ki1000109-EE          PAKISTAN                       0                      0       38     514
0-24 months   ki1000109-EE          PAKISTAN                       0                      1        6     514
0-24 months   ki1000109-EE          PAKISTAN                       1                      0      262     514
0-24 months   ki1000109-EE          PAKISTAN                       1                      1      208     514
0-24 months   ki1113344-GMS-Nepal   NEPAL                          0                      0       68     940
0-24 months   ki1113344-GMS-Nepal   NEPAL                          0                      1       86     940
0-24 months   ki1113344-GMS-Nepal   NEPAL                          1                      0      370     940
0-24 months   ki1113344-GMS-Nepal   NEPAL                          1                      1      416     940
0-24 months   kiGH5241-JiVitA-3     BANGLADESH                     0                      0     1034   14674
0-24 months   kiGH5241-JiVitA-3     BANGLADESH                     0                      1      890   14674
0-24 months   kiGH5241-JiVitA-3     BANGLADESH                     1                      0     7332   14674
0-24 months   kiGH5241-JiVitA-3     BANGLADESH                     1                      1     5418   14674
0-24 months   kiGH5241-JiVitA-4     BANGLADESH                     0                      0        8     106
0-24 months   kiGH5241-JiVitA-4     BANGLADESH                     0                      1        0     106
0-24 months   kiGH5241-JiVitA-4     BANGLADESH                     1                      0       74     106
0-24 months   kiGH5241-JiVitA-4     BANGLADESH                     1                      1       24     106
0-6 months    ki0047075b-MAL-ED     BANGLADESH                     0                      0        2      58
0-6 months    ki0047075b-MAL-ED     BANGLADESH                     0                      1        4      58
0-6 months    ki0047075b-MAL-ED     BANGLADESH                     1                      0       10      58
0-6 months    ki0047075b-MAL-ED     BANGLADESH                     1                      1       42      58
0-6 months    ki0047075b-MAL-ED     BRAZIL                         0                      0        0      14
0-6 months    ki0047075b-MAL-ED     BRAZIL                         0                      1        7      14
0-6 months    ki0047075b-MAL-ED     BRAZIL                         1                      0        1      14
0-6 months    ki0047075b-MAL-ED     BRAZIL                         1                      1        6      14
0-6 months    ki0047075b-MAL-ED     INDIA                          0                      0       12      82
0-6 months    ki0047075b-MAL-ED     INDIA                          0                      1       20      82
0-6 months    ki0047075b-MAL-ED     INDIA                          1                      0       13      82
0-6 months    ki0047075b-MAL-ED     INDIA                          1                      1       37      82
0-6 months    ki0047075b-MAL-ED     NEPAL                          0                      0        3      42
0-6 months    ki0047075b-MAL-ED     NEPAL                          0                      1       17      42
0-6 months    ki0047075b-MAL-ED     NEPAL                          1                      0        6      42
0-6 months    ki0047075b-MAL-ED     NEPAL                          1                      1       16      42
0-6 months    ki0047075b-MAL-ED     PERU                           0                      0        0      11
0-6 months    ki0047075b-MAL-ED     PERU                           0                      1        3      11
0-6 months    ki0047075b-MAL-ED     PERU                           1                      0        0      11
0-6 months    ki0047075b-MAL-ED     PERU                           1                      1        8      11
0-6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   0                      0        2      28
0-6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   0                      1       16      28
0-6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   1                      0        2      28
0-6 months    ki0047075b-MAL-ED     SOUTH AFRICA                   1                      1        8      28
0-6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                      0        1      12
0-6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                      1        6      12
0-6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                      0        0      12
0-6 months    ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                      1        5      12
0-6 months    ki1000109-EE          PAKISTAN                       0                      0       18     216
0-6 months    ki1000109-EE          PAKISTAN                       0                      1        4     216
0-6 months    ki1000109-EE          PAKISTAN                       1                      0       76     216
0-6 months    ki1000109-EE          PAKISTAN                       1                      1      118     216
0-6 months    ki1113344-GMS-Nepal   NEPAL                          0                      0       28     300
0-6 months    ki1113344-GMS-Nepal   NEPAL                          0                      1       34     300
0-6 months    ki1113344-GMS-Nepal   NEPAL                          1                      0       96     300
0-6 months    ki1113344-GMS-Nepal   NEPAL                          1                      1      142     300
0-6 months    kiGH5241-JiVitA-3     BANGLADESH                     0                      0      470    9160
0-6 months    kiGH5241-JiVitA-3     BANGLADESH                     0                      1      890    9160
0-6 months    kiGH5241-JiVitA-3     BANGLADESH                     1                      0     2382    9160
0-6 months    kiGH5241-JiVitA-3     BANGLADESH                     1                      1     5418    9160
0-6 months    kiGH5241-JiVitA-4     BANGLADESH                     0                      0        4      20
0-6 months    kiGH5241-JiVitA-4     BANGLADESH                     0                      1        0      20
0-6 months    kiGH5241-JiVitA-4     BANGLADESH                     1                      0       10      20
0-6 months    kiGH5241-JiVitA-4     BANGLADESH                     1                      1        6      20
6-24 months   ki0047075b-MAL-ED     BANGLADESH                     0                      0        3      60
6-24 months   ki0047075b-MAL-ED     BANGLADESH                     0                      1        2      60
6-24 months   ki0047075b-MAL-ED     BANGLADESH                     1                      0       27      60
6-24 months   ki0047075b-MAL-ED     BANGLADESH                     1                      1       28      60
6-24 months   ki0047075b-MAL-ED     BRAZIL                         0                      0        2       9
6-24 months   ki0047075b-MAL-ED     BRAZIL                         0                      1        0       9
6-24 months   ki0047075b-MAL-ED     BRAZIL                         1                      0        3       9
6-24 months   ki0047075b-MAL-ED     BRAZIL                         1                      1        4       9
6-24 months   ki0047075b-MAL-ED     INDIA                          0                      0       10      95
6-24 months   ki0047075b-MAL-ED     INDIA                          0                      1       11      95
6-24 months   ki0047075b-MAL-ED     INDIA                          1                      0       35      95
6-24 months   ki0047075b-MAL-ED     INDIA                          1                      1       39      95
6-24 months   ki0047075b-MAL-ED     NEPAL                          0                      0        2      50
6-24 months   ki0047075b-MAL-ED     NEPAL                          0                      1       17      50
6-24 months   ki0047075b-MAL-ED     NEPAL                          1                      0        9      50
6-24 months   ki0047075b-MAL-ED     NEPAL                          1                      1       22      50
6-24 months   ki0047075b-MAL-ED     PERU                           0                      0        1      21
6-24 months   ki0047075b-MAL-ED     PERU                           0                      1        9      21
6-24 months   ki0047075b-MAL-ED     PERU                           1                      0        5      21
6-24 months   ki0047075b-MAL-ED     PERU                           1                      1        6      21
6-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   0                      0        5      50
6-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   0                      1       31      50
6-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   1                      0        4      50
6-24 months   ki0047075b-MAL-ED     SOUTH AFRICA                   1                      1       10      50
6-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                      0        6      33
6-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   0                      1       18      33
6-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                      0        1      33
6-24 months   ki0047075b-MAL-ED     TANZANIA, UNITED REPUBLIC OF   1                      1        8      33
6-24 months   ki1000109-EE          PAKISTAN                       0                      0       20     298
6-24 months   ki1000109-EE          PAKISTAN                       0                      1        2     298
6-24 months   ki1000109-EE          PAKISTAN                       1                      0      186     298
6-24 months   ki1000109-EE          PAKISTAN                       1                      1       90     298
6-24 months   ki1113344-GMS-Nepal   NEPAL                          0                      0       40     640
6-24 months   ki1113344-GMS-Nepal   NEPAL                          0                      1       52     640
6-24 months   ki1113344-GMS-Nepal   NEPAL                          1                      0      274     640
6-24 months   ki1113344-GMS-Nepal   NEPAL                          1                      1      274     640
6-24 months   kiGH5241-JiVitA-3     BANGLADESH                     0                      0      564    5514
6-24 months   kiGH5241-JiVitA-3     BANGLADESH                     0                      1        0    5514
6-24 months   kiGH5241-JiVitA-3     BANGLADESH                     1                      0     4950    5514
6-24 months   kiGH5241-JiVitA-3     BANGLADESH                     1                      1        0    5514
6-24 months   kiGH5241-JiVitA-4     BANGLADESH                     0                      0        4      86
6-24 months   kiGH5241-JiVitA-4     BANGLADESH                     0                      1        0      86
6-24 months   kiGH5241-JiVitA-4     BANGLADESH                     1                      0       64      86
6-24 months   kiGH5241-JiVitA-4     BANGLADESH                     1                      1       18      86


The following strata were considered:

* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 0-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-6 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 0-6 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6-24 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-6 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6-24 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness







# Results Detail

## Results Plots
![](/tmp/0694b46c-4251-4e92-8f7a-908e53b7768d/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/0694b46c-4251-4e92-8f7a-908e53b7768d/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/0694b46c-4251-4e92-8f7a-908e53b7768d/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/0694b46c-4251-4e92-8f7a-908e53b7768d/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat        studyid               country        intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  --------------------  -------------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH     0                    NA                0.5454545   0.2068166   0.8840925
0-24 months   ki0047075b-MAL-ED     BANGLADESH     1                    NA                0.6542056   0.5647903   0.7436209
0-24 months   ki0047075b-MAL-ED     INDIA          0                    NA                0.3186200   0.2035394   0.4337006
0-24 months   ki0047075b-MAL-ED     INDIA          1                    NA                0.5620159   0.4701211   0.6539108
0-24 months   ki0047075b-MAL-ED     NEPAL          0                    NA                0.8717949   0.7698881   0.9737017
0-24 months   ki0047075b-MAL-ED     NEPAL          1                    NA                0.7169811   0.6011080   0.8328543
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA   0                    NA                0.8703704   0.7788517   0.9618891
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA   1                    NA                0.7500000   0.5833892   0.9166108
0-24 months   ki1000109-EE          PAKISTAN       0                    NA                0.1363636   0.0045897   0.2681376
0-24 months   ki1000109-EE          PAKISTAN       1                    NA                0.4425532   0.3734795   0.5116269
0-24 months   ki1113344-GMS-Nepal   NEPAL          0                    NA                0.5584416   0.4376550   0.6792281
0-24 months   ki1113344-GMS-Nepal   NEPAL          1                    NA                0.5292621   0.4753470   0.5831772
0-24 months   kiGH5241-JiVitA-3     BANGLADESH     0                    NA                0.4846690   0.4644359   0.5049020
0-24 months   kiGH5241-JiVitA-3     BANGLADESH     1                    NA                0.4257499   0.4140526   0.4374472
0-6 months    ki0047075b-MAL-ED     INDIA          0                    NA                0.5943107   0.4281047   0.7605168
0-6 months    ki0047075b-MAL-ED     INDIA          1                    NA                0.7344895   0.6082905   0.8606884
0-6 months    ki1113344-GMS-Nepal   NEPAL          0                    NA                0.7686243   0.6370739   0.9001747
0-6 months    ki1113344-GMS-Nepal   NEPAL          1                    NA                0.6123302   0.5253736   0.6992868
0-6 months    kiGH5241-JiVitA-3     BANGLADESH     0                    NA                0.6440073   0.6227512   0.6652634
0-6 months    kiGH5241-JiVitA-3     BANGLADESH     1                    NA                0.6887969   0.6748584   0.7027355
6-24 months   ki0047075b-MAL-ED     INDIA          0                    NA                0.5582189   0.3227050   0.7937327
6-24 months   ki0047075b-MAL-ED     INDIA          1                    NA                0.5226655   0.3975162   0.6478148
6-24 months   ki1113344-GMS-Nepal   NEPAL          0                    NA                0.5652174   0.4059418   0.7244930
6-24 months   ki1113344-GMS-Nepal   NEPAL          1                    NA                0.5000000   0.4354869   0.5645131


### Parameter: E(Y)


agecat        studyid               country        intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  --------------------  -------------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH     NA                   NA                0.6440678   0.5565826   0.7315530
0-24 months   ki0047075b-MAL-ED     INDIA          NA                   NA                0.6045198   0.5246128   0.6844268
0-24 months   ki0047075b-MAL-ED     NEPAL          NA                   NA                0.7826087   0.7016344   0.8635829
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA   NA                   NA                0.8333333   0.7515924   0.9150742
0-24 months   ki1000109-EE          PAKISTAN       NA                   NA                0.4163424   0.3511349   0.4815500
0-24 months   ki1113344-GMS-Nepal   NEPAL          NA                   NA                0.5340426   0.4848509   0.5832342
0-24 months   kiGH5241-JiVitA-3     BANGLADESH     NA                   NA                0.4298760   0.4185519   0.4412000
0-6 months    ki0047075b-MAL-ED     INDIA          NA                   NA                0.6951220   0.5922224   0.7980215
0-6 months    ki1113344-GMS-Nepal   NEPAL          NA                   NA                0.5866667   0.5072781   0.6660552
0-6 months    kiGH5241-JiVitA-3     BANGLADESH     NA                   NA                0.6886463   0.6752359   0.7020567
6-24 months   ki0047075b-MAL-ED     INDIA          NA                   NA                0.5263158   0.4116286   0.6410029
6-24 months   ki1113344-GMS-Nepal   NEPAL          NA                   NA                0.5093750   0.4496016   0.5691484


### Parameter: RR


agecat        studyid               country        intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  --------------------  -------------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH     0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki0047075b-MAL-ED     BANGLADESH     1                    0                 1.1993769   0.6350804   2.2650757
0-24 months   ki0047075b-MAL-ED     INDIA          0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki0047075b-MAL-ED     INDIA          1                    0                 1.7639066   1.1822451   2.6317440
0-24 months   ki0047075b-MAL-ED     NEPAL          0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki0047075b-MAL-ED     NEPAL          1                    0                 0.8224195   0.6733193   1.0045366
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA   0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA   1                    0                 0.8617021   0.6737479   1.1020896
0-24 months   ki1000109-EE          PAKISTAN       0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki1000109-EE          PAKISTAN       1                    0                 3.2453901   1.2192841   8.6383119
0-24 months   ki1113344-GMS-Nepal   NEPAL          0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki1113344-GMS-Nepal   NEPAL          1                    0                 0.9477484   0.7461299   1.2038480
0-24 months   kiGH5241-JiVitA-3     BANGLADESH     0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   kiGH5241-JiVitA-3     BANGLADESH     1                    0                 0.8784344   0.8387985   0.9199433
0-6 months    ki0047075b-MAL-ED     INDIA          0                    0                 1.0000000   1.0000000   1.0000000
0-6 months    ki0047075b-MAL-ED     INDIA          1                    0                 1.2358678   0.8893760   1.7173493
0-6 months    ki1113344-GMS-Nepal   NEPAL          0                    0                 1.0000000   1.0000000   1.0000000
0-6 months    ki1113344-GMS-Nepal   NEPAL          1                    0                 0.7966573   0.6385948   0.9938428
0-6 months    kiGH5241-JiVitA-3     BANGLADESH     0                    0                 1.0000000   1.0000000   1.0000000
0-6 months    kiGH5241-JiVitA-3     BANGLADESH     1                    0                 1.0695483   1.0318667   1.1086060
6-24 months   ki0047075b-MAL-ED     INDIA          0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   ki0047075b-MAL-ED     INDIA          1                    0                 0.9363094   0.5828318   1.5041651
6-24 months   ki1113344-GMS-Nepal   NEPAL          0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   ki1113344-GMS-Nepal   NEPAL          1                    0                 0.8846154   0.6486774   1.2063691


### Parameter: PAR


agecat        studyid               country        intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  --------------------  -------------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH     0                    NA                 0.0986133   -0.2193500    0.4165765
0-24 months   ki0047075b-MAL-ED     INDIA          0                    NA                 0.2858998    0.1854297    0.3863698
0-24 months   ki0047075b-MAL-ED     NEPAL          0                    NA                -0.0891862   -0.1782293   -0.0001430
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA   0                    NA                -0.0370370   -0.0955878    0.0215137
0-24 months   ki1000109-EE          PAKISTAN       0                    NA                 0.2799788    0.1439670    0.4159905
0-24 months   ki1113344-GMS-Nepal   NEPAL          0                    NA                -0.0243990   -0.1351746    0.0863766
0-24 months   kiGH5241-JiVitA-3     BANGLADESH     0                    NA                -0.0547930   -0.0732379   -0.0363481
0-6 months    ki0047075b-MAL-ED     INDIA          0                    NA                 0.1008112   -0.0315006    0.2331231
0-6 months    ki1113344-GMS-Nepal   NEPAL          0                    NA                -0.1819576   -0.3005433   -0.0633720
0-6 months    kiGH5241-JiVitA-3     BANGLADESH     0                    NA                 0.0446390    0.0253717    0.0639063
6-24 months   ki0047075b-MAL-ED     INDIA          0                    NA                -0.0319031   -0.2314319    0.1676257
6-24 months   ki1113344-GMS-Nepal   NEPAL          0                    NA                -0.0558424   -0.2034345    0.0917498


### Parameter: PAF


agecat        studyid               country        intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  --------------------  -------------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH     0                    NA                 0.1531100   -0.5217649    0.5286903
0-24 months   ki0047075b-MAL-ED     INDIA          0                    NA                 0.4729370    0.2787046    0.6148659
0-24 months   ki0047075b-MAL-ED     NEPAL          0                    NA                -0.1139601   -0.2380747   -0.0022878
0-24 months   ki0047075b-MAL-ED     SOUTH AFRICA   0                    NA                -0.0444444   -0.1181059    0.0243642
0-24 months   ki1000109-EE          PAKISTAN       0                    NA                 0.6724724    0.1526889    0.8733944
0-24 months   ki1113344-GMS-Nepal   NEPAL          0                    NA                -0.0456874   -0.2752195    0.1425303
0-24 months   kiGH5241-JiVitA-3     BANGLADESH     0                    NA                -0.1274624   -0.1718223   -0.0847817
0-6 months    ki0047075b-MAL-ED     INDIA          0                    NA                 0.1450267   -0.0692164    0.3163410
0-6 months    ki1113344-GMS-Nepal   NEPAL          0                    NA                -0.3101551   -0.5414695   -0.1135519
0-6 months    kiGH5241-JiVitA-3     BANGLADESH     0                    NA                 0.0648214    0.0366414    0.0921770
6-24 months   ki0047075b-MAL-ED     INDIA          0                    NA                -0.0606158   -0.5156189    0.2577911
6-24 months   ki1113344-GMS-Nepal   NEPAL          0                    NA                -0.1096292   -0.4410898    0.1455931