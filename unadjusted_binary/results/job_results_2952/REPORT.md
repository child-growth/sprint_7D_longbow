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

**Outcome Variable:** stunted

## Predictor Variables

**Intervention Variable:** lag_WHZ_quart

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat      studyid                    country                        lag_WHZ_quart    stunted   n_cell      n
----------  -------------------------  -----------------------------  --------------  --------  -------  -----
12 months   ki0047075b-MAL-ED          BANGLADESH                     1                      0       12    230
12 months   ki0047075b-MAL-ED          BANGLADESH                     1                      1       14    230
12 months   ki0047075b-MAL-ED          BANGLADESH                     2                      0       56    230
12 months   ki0047075b-MAL-ED          BANGLADESH                     2                      1       35    230
12 months   ki0047075b-MAL-ED          BANGLADESH                     3                      0       63    230
12 months   ki0047075b-MAL-ED          BANGLADESH                     3                      1       26    230
12 months   ki0047075b-MAL-ED          BANGLADESH                     4                      0       21    230
12 months   ki0047075b-MAL-ED          BANGLADESH                     4                      1        3    230
12 months   ki0047075b-MAL-ED          BRAZIL                         1                      0       24    194
12 months   ki0047075b-MAL-ED          BRAZIL                         1                      1        1    194
12 months   ki0047075b-MAL-ED          BRAZIL                         2                      0       59    194
12 months   ki0047075b-MAL-ED          BRAZIL                         2                      1        3    194
12 months   ki0047075b-MAL-ED          BRAZIL                         3                      0       75    194
12 months   ki0047075b-MAL-ED          BRAZIL                         3                      1        3    194
12 months   ki0047075b-MAL-ED          BRAZIL                         4                      0       28    194
12 months   ki0047075b-MAL-ED          BRAZIL                         4                      1        1    194
12 months   ki0047075b-MAL-ED          INDIA                          1                      0       85    228
12 months   ki0047075b-MAL-ED          INDIA                          1                      1       50    228
12 months   ki0047075b-MAL-ED          INDIA                          2                      0       51    228
12 months   ki0047075b-MAL-ED          INDIA                          2                      1       16    228
12 months   ki0047075b-MAL-ED          INDIA                          3                      0       15    228
12 months   ki0047075b-MAL-ED          INDIA                          3                      1        5    228
12 months   ki0047075b-MAL-ED          INDIA                          4                      0        5    228
12 months   ki0047075b-MAL-ED          INDIA                          4                      1        1    228
12 months   ki0047075b-MAL-ED          NEPAL                          1                      0       62    231
12 months   ki0047075b-MAL-ED          NEPAL                          1                      1        8    231
12 months   ki0047075b-MAL-ED          NEPAL                          2                      0       81    231
12 months   ki0047075b-MAL-ED          NEPAL                          2                      1       11    231
12 months   ki0047075b-MAL-ED          NEPAL                          3                      0       54    231
12 months   ki0047075b-MAL-ED          NEPAL                          3                      1        4    231
12 months   ki0047075b-MAL-ED          NEPAL                          4                      0       10    231
12 months   ki0047075b-MAL-ED          NEPAL                          4                      1        1    231
12 months   ki0047075b-MAL-ED          PERU                           1                      0       23    244
12 months   ki0047075b-MAL-ED          PERU                           1                      1        7    244
12 months   ki0047075b-MAL-ED          PERU                           2                      0       40    244
12 months   ki0047075b-MAL-ED          PERU                           2                      1       29    244
12 months   ki0047075b-MAL-ED          PERU                           3                      0       62    244
12 months   ki0047075b-MAL-ED          PERU                           3                      1       29    244
12 months   ki0047075b-MAL-ED          PERU                           4                      0       42    244
12 months   ki0047075b-MAL-ED          PERU                           4                      1       12    244
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                      0       28    250
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                      1       17    250
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                      0       32    250
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                      1       17    250
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                      0       64    250
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                      1       20    250
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                      0       60    250
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                      1       12    250
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      0       10    231
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      1       21    231
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      0       33    231
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      1       28    231
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      0       36    231
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      1       42    231
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      0       35    231
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      1       26    231
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                      0       10     57
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                      1        5     57
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                      0        9     57
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                      1       10     57
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                      0        6     57
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                      1       13     57
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          4                      0        2     57
12 months   ki1000108-CMC-V-BCS-2002   INDIA                          4                      1        2     57
12 months   ki1000108-IRC              INDIA                          1                      0        0      5
12 months   ki1000108-IRC              INDIA                          1                      1        1      5
12 months   ki1000108-IRC              INDIA                          2                      0        4      5
12 months   ki1000108-IRC              INDIA                          2                      1        0      5
12 months   ki1000108-IRC              INDIA                          3                      0        0      5
12 months   ki1000108-IRC              INDIA                          3                      1        0      5
12 months   ki1000108-IRC              INDIA                          4                      0        0      5
12 months   ki1000108-IRC              INDIA                          4                      1        0      5
12 months   ki1000109-EE               PAKISTAN                       1                      0        0     86
12 months   ki1000109-EE               PAKISTAN                       1                      1       30     86
12 months   ki1000109-EE               PAKISTAN                       2                      0        6     86
12 months   ki1000109-EE               PAKISTAN                       2                      1       18     86
12 months   ki1000109-EE               PAKISTAN                       3                      0       10     86
12 months   ki1000109-EE               PAKISTAN                       3                      1        6     86
12 months   ki1000109-EE               PAKISTAN                       4                      0        2     86
12 months   ki1000109-EE               PAKISTAN                       4                      1       14     86
12 months   ki1017093b-PROVIDE         BANGLADESH                     1                      0       91    549
12 months   ki1017093b-PROVIDE         BANGLADESH                     1                      1       65    549
12 months   ki1017093b-PROVIDE         BANGLADESH                     2                      0      106    549
12 months   ki1017093b-PROVIDE         BANGLADESH                     2                      1       48    549
12 months   ki1017093b-PROVIDE         BANGLADESH                     3                      0      121    549
12 months   ki1017093b-PROVIDE         BANGLADESH                     3                      1       23    549
12 months   ki1017093b-PROVIDE         BANGLADESH                     4                      0       82    549
12 months   ki1017093b-PROVIDE         BANGLADESH                     4                      1       13    549
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      0      210   1289
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      1       72   1289
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      0      221   1289
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      1       66   1289
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      0      261   1289
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      1       36   1289
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      0      376   1289
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      1       47   1289
12 months   ki1101329-Keneba           GAMBIA                         1                      0      163    608
12 months   ki1101329-Keneba           GAMBIA                         1                      1       76    608
12 months   ki1101329-Keneba           GAMBIA                         2                      0      133    608
12 months   ki1101329-Keneba           GAMBIA                         2                      1       21    608
12 months   ki1101329-Keneba           GAMBIA                         3                      0      118    608
12 months   ki1101329-Keneba           GAMBIA                         3                      1       15    608
12 months   ki1101329-Keneba           GAMBIA                         4                      0       69    608
12 months   ki1101329-Keneba           GAMBIA                         4                      1       13    608
12 months   ki1112895-Guatemala BSC    GUATEMALA                      1                      0       10    154
12 months   ki1112895-Guatemala BSC    GUATEMALA                      1                      1       22    154
12 months   ki1112895-Guatemala BSC    GUATEMALA                      2                      0       18    154
12 months   ki1112895-Guatemala BSC    GUATEMALA                      2                      1       24    154
12 months   ki1112895-Guatemala BSC    GUATEMALA                      3                      0       23    154
12 months   ki1112895-Guatemala BSC    GUATEMALA                      3                      1       15    154
12 months   ki1112895-Guatemala BSC    GUATEMALA                      4                      0       27    154
12 months   ki1112895-Guatemala BSC    GUATEMALA                      4                      1       15    154
12 months   ki1113344-GMS-Nepal        NEPAL                          1                      0        6      8
12 months   ki1113344-GMS-Nepal        NEPAL                          1                      1        2      8
12 months   ki1113344-GMS-Nepal        NEPAL                          2                      0        0      8
12 months   ki1113344-GMS-Nepal        NEPAL                          2                      1        0      8
12 months   ki1113344-GMS-Nepal        NEPAL                          3                      0        0      8
12 months   ki1113344-GMS-Nepal        NEPAL                          3                      1        0      8
12 months   ki1113344-GMS-Nepal        NEPAL                          4                      0        0      8
12 months   ki1113344-GMS-Nepal        NEPAL                          4                      1        0      8
12 months   ki1114097-CMIN             BANGLADESH                     1                      0       38    240
12 months   ki1114097-CMIN             BANGLADESH                     1                      1       76    240
12 months   ki1114097-CMIN             BANGLADESH                     2                      0       33    240
12 months   ki1114097-CMIN             BANGLADESH                     2                      1       37    240
12 months   ki1114097-CMIN             BANGLADESH                     3                      0       22    240
12 months   ki1114097-CMIN             BANGLADESH                     3                      1       10    240
12 months   ki1114097-CMIN             BANGLADESH                     4                      0       17    240
12 months   ki1114097-CMIN             BANGLADESH                     4                      1        7    240
12 months   ki1114097-CMIN             PERU                           1                      0       18    560
12 months   ki1114097-CMIN             PERU                           1                      1       20    560
12 months   ki1114097-CMIN             PERU                           2                      0       52    560
12 months   ki1114097-CMIN             PERU                           2                      1       24    560
12 months   ki1114097-CMIN             PERU                           3                      0      101    560
12 months   ki1114097-CMIN             PERU                           3                      1       22    560
12 months   ki1114097-CMIN             PERU                           4                      0      280    560
12 months   ki1114097-CMIN             PERU                           4                      1       43    560
18 months   ki0047075b-MAL-ED          BANGLADESH                     1                      0       18    219
18 months   ki0047075b-MAL-ED          BANGLADESH                     1                      1       21    219
18 months   ki0047075b-MAL-ED          BANGLADESH                     2                      0       51    219
18 months   ki0047075b-MAL-ED          BANGLADESH                     2                      1       46    219
18 months   ki0047075b-MAL-ED          BANGLADESH                     3                      0       47    219
18 months   ki0047075b-MAL-ED          BANGLADESH                     3                      1       29    219
18 months   ki0047075b-MAL-ED          BANGLADESH                     4                      0        5    219
18 months   ki0047075b-MAL-ED          BANGLADESH                     4                      1        2    219
18 months   ki0047075b-MAL-ED          BRAZIL                         1                      0       14    176
18 months   ki0047075b-MAL-ED          BRAZIL                         1                      1        0    176
18 months   ki0047075b-MAL-ED          BRAZIL                         2                      0       50    176
18 months   ki0047075b-MAL-ED          BRAZIL                         2                      1        5    176
18 months   ki0047075b-MAL-ED          BRAZIL                         3                      0       68    176
18 months   ki0047075b-MAL-ED          BRAZIL                         3                      1        2    176
18 months   ki0047075b-MAL-ED          BRAZIL                         4                      0       37    176
18 months   ki0047075b-MAL-ED          BRAZIL                         4                      1        0    176
18 months   ki0047075b-MAL-ED          INDIA                          1                      0       41    228
18 months   ki0047075b-MAL-ED          INDIA                          1                      1       60    228
18 months   ki0047075b-MAL-ED          INDIA                          2                      0       56    228
18 months   ki0047075b-MAL-ED          INDIA                          2                      1       33    228
18 months   ki0047075b-MAL-ED          INDIA                          3                      0       27    228
18 months   ki0047075b-MAL-ED          INDIA                          3                      1        9    228
18 months   ki0047075b-MAL-ED          INDIA                          4                      0        2    228
18 months   ki0047075b-MAL-ED          INDIA                          4                      1        0    228
18 months   ki0047075b-MAL-ED          NEPAL                          1                      0       47    228
18 months   ki0047075b-MAL-ED          NEPAL                          1                      1       14    228
18 months   ki0047075b-MAL-ED          NEPAL                          2                      0       67    228
18 months   ki0047075b-MAL-ED          NEPAL                          2                      1       21    228
18 months   ki0047075b-MAL-ED          NEPAL                          3                      0       53    228
18 months   ki0047075b-MAL-ED          NEPAL                          3                      1        7    228
18 months   ki0047075b-MAL-ED          NEPAL                          4                      0       17    228
18 months   ki0047075b-MAL-ED          NEPAL                          4                      1        2    228
18 months   ki0047075b-MAL-ED          PERU                           1                      0       21    218
18 months   ki0047075b-MAL-ED          PERU                           1                      1       23    218
18 months   ki0047075b-MAL-ED          PERU                           2                      0       37    218
18 months   ki0047075b-MAL-ED          PERU                           2                      1       29    218
18 months   ki0047075b-MAL-ED          PERU                           3                      0       44    218
18 months   ki0047075b-MAL-ED          PERU                           3                      1       33    218
18 months   ki0047075b-MAL-ED          PERU                           4                      0       20    218
18 months   ki0047075b-MAL-ED          PERU                           4                      1       11    218
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                      0       11    240
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                      1       13    240
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                      0       28    240
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                      1       17    240
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                      0       51    240
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                      1       28    240
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                      0       68    240
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                      1       24    240
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      0        4    223
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      1       20    223
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      0       20    223
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      1       42    223
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      0       23    223
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      1       48    223
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      0       28    223
18 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      1       38    223
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                      0        8     75
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                      1       11     75
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                      0        7     75
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                      1       22     75
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                      0        5     75
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                      1       15     75
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          4                      0        3     75
18 months   ki1000108-CMC-V-BCS-2002   INDIA                          4                      1        4     75
18 months   ki1000108-IRC              INDIA                          1                      0        4      8
18 months   ki1000108-IRC              INDIA                          1                      1        2      8
18 months   ki1000108-IRC              INDIA                          2                      0        0      8
18 months   ki1000108-IRC              INDIA                          2                      1        1      8
18 months   ki1000108-IRC              INDIA                          3                      0        0      8
18 months   ki1000108-IRC              INDIA                          3                      1        1      8
18 months   ki1000108-IRC              INDIA                          4                      0        0      8
18 months   ki1000108-IRC              INDIA                          4                      1        0      8
18 months   ki1000109-EE               PAKISTAN                       1                      0        6    112
18 months   ki1000109-EE               PAKISTAN                       1                      1       42    112
18 months   ki1000109-EE               PAKISTAN                       2                      0        2    112
18 months   ki1000109-EE               PAKISTAN                       2                      1       28    112
18 months   ki1000109-EE               PAKISTAN                       3                      0       10    112
18 months   ki1000109-EE               PAKISTAN                       3                      1       18    112
18 months   ki1000109-EE               PAKISTAN                       4                      0        2    112
18 months   ki1000109-EE               PAKISTAN                       4                      1        4    112
18 months   ki1017093b-PROVIDE         BANGLADESH                     1                      0       66    414
18 months   ki1017093b-PROVIDE         BANGLADESH                     1                      1       67    414
18 months   ki1017093b-PROVIDE         BANGLADESH                     2                      0       76    414
18 months   ki1017093b-PROVIDE         BANGLADESH                     2                      1       41    414
18 months   ki1017093b-PROVIDE         BANGLADESH                     3                      0       62    414
18 months   ki1017093b-PROVIDE         BANGLADESH                     3                      1       27    414
18 months   ki1017093b-PROVIDE         BANGLADESH                     4                      0       62    414
18 months   ki1017093b-PROVIDE         BANGLADESH                     4                      1       13    414
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      0      137    855
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      1       67    855
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      0      123    855
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      1       42    855
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      0      159    855
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      1       48    855
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      0      230    855
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      1       49    855
18 months   ki1101329-Keneba           GAMBIA                         1                      0      146    611
18 months   ki1101329-Keneba           GAMBIA                         1                      1       91    611
18 months   ki1101329-Keneba           GAMBIA                         2                      0      127    611
18 months   ki1101329-Keneba           GAMBIA                         2                      1       35    611
18 months   ki1101329-Keneba           GAMBIA                         3                      0       99    611
18 months   ki1101329-Keneba           GAMBIA                         3                      1       23    611
18 months   ki1101329-Keneba           GAMBIA                         4                      0       77    611
18 months   ki1101329-Keneba           GAMBIA                         4                      1       13    611
18 months   ki1113344-GMS-Nepal        NEPAL                          1                      0        4     22
18 months   ki1113344-GMS-Nepal        NEPAL                          1                      1       10     22
18 months   ki1113344-GMS-Nepal        NEPAL                          2                      0        0     22
18 months   ki1113344-GMS-Nepal        NEPAL                          2                      1        2     22
18 months   ki1113344-GMS-Nepal        NEPAL                          3                      0        4     22
18 months   ki1113344-GMS-Nepal        NEPAL                          3                      1        0     22
18 months   ki1113344-GMS-Nepal        NEPAL                          4                      0        0     22
18 months   ki1113344-GMS-Nepal        NEPAL                          4                      1        2     22
18 months   ki1114097-CMIN             BANGLADESH                     1                      0       22    233
18 months   ki1114097-CMIN             BANGLADESH                     1                      1       94    233
18 months   ki1114097-CMIN             BANGLADESH                     2                      0       13    233
18 months   ki1114097-CMIN             BANGLADESH                     2                      1       50    233
18 months   ki1114097-CMIN             BANGLADESH                     3                      0       17    233
18 months   ki1114097-CMIN             BANGLADESH                     3                      1       17    233
18 months   ki1114097-CMIN             BANGLADESH                     4                      0       12    233
18 months   ki1114097-CMIN             BANGLADESH                     4                      1        8    233
18 months   ki1114097-CMIN             PERU                           1                      0        4    447
18 months   ki1114097-CMIN             PERU                           1                      1        6    447
18 months   ki1114097-CMIN             PERU                           2                      0       19    447
18 months   ki1114097-CMIN             PERU                           2                      1       19    447
18 months   ki1114097-CMIN             PERU                           3                      0       52    447
18 months   ki1114097-CMIN             PERU                           3                      1       53    447
18 months   ki1114097-CMIN             PERU                           4                      0      233    447
18 months   ki1114097-CMIN             PERU                           4                      1       61    447
3 months    ki0047075b-MAL-ED          BANGLADESH                     1                      0       47    245
3 months    ki0047075b-MAL-ED          BANGLADESH                     1                      1        7    245
3 months    ki0047075b-MAL-ED          BANGLADESH                     2                      0       90    245
3 months    ki0047075b-MAL-ED          BANGLADESH                     2                      1       15    245
3 months    ki0047075b-MAL-ED          BANGLADESH                     3                      0       61    245
3 months    ki0047075b-MAL-ED          BANGLADESH                     3                      1       14    245
3 months    ki0047075b-MAL-ED          BANGLADESH                     4                      0       11    245
3 months    ki0047075b-MAL-ED          BANGLADESH                     4                      1        0    245
3 months    ki0047075b-MAL-ED          BRAZIL                         1                      0       34    218
3 months    ki0047075b-MAL-ED          BRAZIL                         1                      1        2    218
3 months    ki0047075b-MAL-ED          BRAZIL                         2                      0       95    218
3 months    ki0047075b-MAL-ED          BRAZIL                         2                      1        5    218
3 months    ki0047075b-MAL-ED          BRAZIL                         3                      0       55    218
3 months    ki0047075b-MAL-ED          BRAZIL                         3                      1        4    218
3 months    ki0047075b-MAL-ED          BRAZIL                         4                      0       21    218
3 months    ki0047075b-MAL-ED          BRAZIL                         4                      1        2    218
3 months    ki0047075b-MAL-ED          INDIA                          1                      0       72    239
3 months    ki0047075b-MAL-ED          INDIA                          1                      1       16    239
3 months    ki0047075b-MAL-ED          INDIA                          2                      0       79    239
3 months    ki0047075b-MAL-ED          INDIA                          2                      1       10    239
3 months    ki0047075b-MAL-ED          INDIA                          3                      0       44    239
3 months    ki0047075b-MAL-ED          INDIA                          3                      1        8    239
3 months    ki0047075b-MAL-ED          INDIA                          4                      0        8    239
3 months    ki0047075b-MAL-ED          INDIA                          4                      1        2    239
3 months    ki0047075b-MAL-ED          NEPAL                          1                      0       47    236
3 months    ki0047075b-MAL-ED          NEPAL                          1                      1        1    236
3 months    ki0047075b-MAL-ED          NEPAL                          2                      0       84    236
3 months    ki0047075b-MAL-ED          NEPAL                          2                      1        8    236
3 months    ki0047075b-MAL-ED          NEPAL                          3                      0       74    236
3 months    ki0047075b-MAL-ED          NEPAL                          3                      1        5    236
3 months    ki0047075b-MAL-ED          NEPAL                          4                      0       17    236
3 months    ki0047075b-MAL-ED          NEPAL                          4                      1        0    236
3 months    ki0047075b-MAL-ED          PERU                           1                      0       11    282
3 months    ki0047075b-MAL-ED          PERU                           1                      1        7    282
3 months    ki0047075b-MAL-ED          PERU                           2                      0       54    282
3 months    ki0047075b-MAL-ED          PERU                           2                      1       16    282
3 months    ki0047075b-MAL-ED          PERU                           3                      0       76    282
3 months    ki0047075b-MAL-ED          PERU                           3                      1       23    282
3 months    ki0047075b-MAL-ED          PERU                           4                      0       71    282
3 months    ki0047075b-MAL-ED          PERU                           4                      1       24    282
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                      0       30    271
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                      1        1    271
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                      0       49    271
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                      1       10    271
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                      0       77    271
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                      1       16    271
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                      0       64    271
3 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                      1       24    271
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      0       10    252
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      1        1    252
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      0       41    252
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      1       13    252
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      0       69    252
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      1       13    252
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      0       78    252
3 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      1       27    252
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                      0        5     24
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                      1        4     24
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                      0        7     24
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                      1        0     24
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                      0        3     24
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                      1        3     24
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          4                      0        2     24
3 months    ki1000108-CMC-V-BCS-2002   INDIA                          4                      1        0     24
3 months    ki1000108-IRC              INDIA                          1                      0        0      2
3 months    ki1000108-IRC              INDIA                          1                      1        0      2
3 months    ki1000108-IRC              INDIA                          2                      0        2      2
3 months    ki1000108-IRC              INDIA                          2                      1        0      2
3 months    ki1000108-IRC              INDIA                          3                      0        0      2
3 months    ki1000108-IRC              INDIA                          3                      1        0      2
3 months    ki1000108-IRC              INDIA                          4                      0        0      2
3 months    ki1000108-IRC              INDIA                          4                      1        0      2
3 months    ki1000109-EE               PAKISTAN                       1                      0        2     30
3 months    ki1000109-EE               PAKISTAN                       1                      1        2     30
3 months    ki1000109-EE               PAKISTAN                       2                      0        0     30
3 months    ki1000109-EE               PAKISTAN                       2                      1        2     30
3 months    ki1000109-EE               PAKISTAN                       3                      0        2     30
3 months    ki1000109-EE               PAKISTAN                       3                      1       10     30
3 months    ki1000109-EE               PAKISTAN                       4                      0        4     30
3 months    ki1000109-EE               PAKISTAN                       4                      1        8     30
3 months    ki1017093b-PROVIDE         BANGLADESH                     1                      0      228    587
3 months    ki1017093b-PROVIDE         BANGLADESH                     1                      1       28    587
3 months    ki1017093b-PROVIDE         BANGLADESH                     2                      0      151    587
3 months    ki1017093b-PROVIDE         BANGLADESH                     2                      1       23    587
3 months    ki1017093b-PROVIDE         BANGLADESH                     3                      0      100    587
3 months    ki1017093b-PROVIDE         BANGLADESH                     3                      1       23    587
3 months    ki1017093b-PROVIDE         BANGLADESH                     4                      0       26    587
3 months    ki1017093b-PROVIDE         BANGLADESH                     4                      1        8    587
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      0      542   2211
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      1       35   2211
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      0      467   2211
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      1       23   2211
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      0      448   2211
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      1       34   2211
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      0      603   2211
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      1       59   2211
3 months    ki1101329-Keneba           GAMBIA                         1                      0      141    707
3 months    ki1101329-Keneba           GAMBIA                         1                      1       22    707
3 months    ki1101329-Keneba           GAMBIA                         2                      0      108    707
3 months    ki1101329-Keneba           GAMBIA                         2                      1       12    707
3 months    ki1101329-Keneba           GAMBIA                         3                      0      158    707
3 months    ki1101329-Keneba           GAMBIA                         3                      1       27    707
3 months    ki1101329-Keneba           GAMBIA                         4                      0      203    707
3 months    ki1101329-Keneba           GAMBIA                         4                      1       36    707
3 months    ki1114097-CMIN             BANGLADESH                     1                      0       67    248
3 months    ki1114097-CMIN             BANGLADESH                     1                      1       25    248
3 months    ki1114097-CMIN             BANGLADESH                     2                      0       52    248
3 months    ki1114097-CMIN             BANGLADESH                     2                      1       20    248
3 months    ki1114097-CMIN             BANGLADESH                     3                      0       28    248
3 months    ki1114097-CMIN             BANGLADESH                     3                      1       20    248
3 months    ki1114097-CMIN             BANGLADESH                     4                      0       14    248
3 months    ki1114097-CMIN             BANGLADESH                     4                      1       22    248
3 months    ki1114097-CMIN             PERU                           1                      0      103    586
3 months    ki1114097-CMIN             PERU                           1                      1       18    586
3 months    ki1114097-CMIN             PERU                           2                      0      114    586
3 months    ki1114097-CMIN             PERU                           2                      1        5    586
3 months    ki1114097-CMIN             PERU                           3                      0      150    586
3 months    ki1114097-CMIN             PERU                           3                      1        5    586
3 months    ki1114097-CMIN             PERU                           4                      0      176    586
3 months    ki1114097-CMIN             PERU                           4                      1       15    586
6 months    ki0047075b-MAL-ED          BANGLADESH                     1                      0       29    236
6 months    ki0047075b-MAL-ED          BANGLADESH                     1                      1        5    236
6 months    ki0047075b-MAL-ED          BANGLADESH                     2                      0       77    236
6 months    ki0047075b-MAL-ED          BANGLADESH                     2                      1       19    236
6 months    ki0047075b-MAL-ED          BANGLADESH                     3                      0       68    236
6 months    ki0047075b-MAL-ED          BANGLADESH                     3                      1       16    236
6 months    ki0047075b-MAL-ED          BANGLADESH                     4                      0       19    236
6 months    ki0047075b-MAL-ED          BANGLADESH                     4                      1        3    236
6 months    ki0047075b-MAL-ED          BRAZIL                         1                      0       36    207
6 months    ki0047075b-MAL-ED          BRAZIL                         1                      1        1    207
6 months    ki0047075b-MAL-ED          BRAZIL                         2                      0       74    207
6 months    ki0047075b-MAL-ED          BRAZIL                         2                      1        4    207
6 months    ki0047075b-MAL-ED          BRAZIL                         3                      0       70    207
6 months    ki0047075b-MAL-ED          BRAZIL                         3                      1        2    207
6 months    ki0047075b-MAL-ED          BRAZIL                         4                      0       20    207
6 months    ki0047075b-MAL-ED          BRAZIL                         4                      1        0    207
6 months    ki0047075b-MAL-ED          INDIA                          1                      0       89    235
6 months    ki0047075b-MAL-ED          INDIA                          1                      1       23    235
6 months    ki0047075b-MAL-ED          INDIA                          2                      0       66    235
6 months    ki0047075b-MAL-ED          INDIA                          2                      1       16    235
6 months    ki0047075b-MAL-ED          INDIA                          3                      0       30    235
6 months    ki0047075b-MAL-ED          INDIA                          3                      1        6    235
6 months    ki0047075b-MAL-ED          INDIA                          4                      0        3    235
6 months    ki0047075b-MAL-ED          INDIA                          4                      1        2    235
6 months    ki0047075b-MAL-ED          NEPAL                          1                      0       59    235
6 months    ki0047075b-MAL-ED          NEPAL                          1                      1        4    235
6 months    ki0047075b-MAL-ED          NEPAL                          2                      0       83    235
6 months    ki0047075b-MAL-ED          NEPAL                          2                      1        5    235
6 months    ki0047075b-MAL-ED          NEPAL                          3                      0       65    235
6 months    ki0047075b-MAL-ED          NEPAL                          3                      1        4    235
6 months    ki0047075b-MAL-ED          NEPAL                          4                      0       13    235
6 months    ki0047075b-MAL-ED          NEPAL                          4                      1        2    235
6 months    ki0047075b-MAL-ED          PERU                           1                      0       25    270
6 months    ki0047075b-MAL-ED          PERU                           1                      1        9    270
6 months    ki0047075b-MAL-ED          PERU                           2                      0       52    270
6 months    ki0047075b-MAL-ED          PERU                           2                      1       12    270
6 months    ki0047075b-MAL-ED          PERU                           3                      0       78    270
6 months    ki0047075b-MAL-ED          PERU                           3                      1       16    270
6 months    ki0047075b-MAL-ED          PERU                           4                      0       57    270
6 months    ki0047075b-MAL-ED          PERU                           4                      1       21    270
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                      0       29    251
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                      1        9    251
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                      0       41    251
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                      1        7    251
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                      0       61    251
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                      1       14    251
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                      0       69    251
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                      1       21    251
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      0       24    242
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      1        8    242
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      0       44    242
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      1        9    242
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      0       56    242
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      1       20    242
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      0       57    242
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      1       24    242
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                      0        7     41
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                      1        2     41
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                      0       11     41
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                      1        3     41
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                      0        9     41
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                      1        6     41
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          4                      0        2     41
6 months    ki1000108-CMC-V-BCS-2002   INDIA                          4                      1        1     41
6 months    ki1000108-IRC              INDIA                          1                      0        0      3
6 months    ki1000108-IRC              INDIA                          1                      1        0      3
6 months    ki1000108-IRC              INDIA                          2                      0        2      3
6 months    ki1000108-IRC              INDIA                          2                      1        0      3
6 months    ki1000108-IRC              INDIA                          3                      0        1      3
6 months    ki1000108-IRC              INDIA                          3                      1        0      3
6 months    ki1000108-IRC              INDIA                          4                      0        0      3
6 months    ki1000108-IRC              INDIA                          4                      1        0      3
6 months    ki1000109-EE               PAKISTAN                       1                      0       12     48
6 months    ki1000109-EE               PAKISTAN                       1                      1       10     48
6 months    ki1000109-EE               PAKISTAN                       2                      0        4     48
6 months    ki1000109-EE               PAKISTAN                       2                      1        6     48
6 months    ki1000109-EE               PAKISTAN                       3                      0        4     48
6 months    ki1000109-EE               PAKISTAN                       3                      1        6     48
6 months    ki1000109-EE               PAKISTAN                       4                      0        0     48
6 months    ki1000109-EE               PAKISTAN                       4                      1        6     48
6 months    ki1017093b-PROVIDE         BANGLADESH                     1                      0        6     38
6 months    ki1017093b-PROVIDE         BANGLADESH                     1                      1        2     38
6 months    ki1017093b-PROVIDE         BANGLADESH                     2                      0        9     38
6 months    ki1017093b-PROVIDE         BANGLADESH                     2                      1        3     38
6 months    ki1017093b-PROVIDE         BANGLADESH                     3                      0        7     38
6 months    ki1017093b-PROVIDE         BANGLADESH                     3                      1        2     38
6 months    ki1017093b-PROVIDE         BANGLADESH                     4                      0        9     38
6 months    ki1017093b-PROVIDE         BANGLADESH                     4                      1        0     38
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      0      435   1899
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      1       51   1899
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      0      338   1899
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      1       58   1899
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      0      417   1899
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      1       51   1899
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      0      484   1899
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      1       65   1899
6 months    ki1101329-Keneba           GAMBIA                         1                      0      194    748
6 months    ki1101329-Keneba           GAMBIA                         1                      1       27    748
6 months    ki1101329-Keneba           GAMBIA                         2                      0      193    748
6 months    ki1101329-Keneba           GAMBIA                         2                      1       15    748
6 months    ki1101329-Keneba           GAMBIA                         3                      0      142    748
6 months    ki1101329-Keneba           GAMBIA                         3                      1       19    748
6 months    ki1101329-Keneba           GAMBIA                         4                      0      133    748
6 months    ki1101329-Keneba           GAMBIA                         4                      1       25    748
6 months    ki1112895-Guatemala BSC    GUATEMALA                      1                      0       45    233
6 months    ki1112895-Guatemala BSC    GUATEMALA                      1                      1       20    233
6 months    ki1112895-Guatemala BSC    GUATEMALA                      2                      0       44    233
6 months    ki1112895-Guatemala BSC    GUATEMALA                      2                      1       24    233
6 months    ki1112895-Guatemala BSC    GUATEMALA                      3                      0       34    233
6 months    ki1112895-Guatemala BSC    GUATEMALA                      3                      1       15    233
6 months    ki1112895-Guatemala BSC    GUATEMALA                      4                      0       40    233
6 months    ki1112895-Guatemala BSC    GUATEMALA                      4                      1       11    233
6 months    ki1114097-CMIN             BANGLADESH                     1                      0       71    239
6 months    ki1114097-CMIN             BANGLADESH                     1                      1       44    239
6 months    ki1114097-CMIN             BANGLADESH                     2                      0       32    239
6 months    ki1114097-CMIN             BANGLADESH                     2                      1       27    239
6 months    ki1114097-CMIN             BANGLADESH                     3                      0       30    239
6 months    ki1114097-CMIN             BANGLADESH                     3                      1       10    239
6 months    ki1114097-CMIN             BANGLADESH                     4                      0       16    239
6 months    ki1114097-CMIN             BANGLADESH                     4                      1        9    239
6 months    ki1114097-CMIN             PERU                           1                      0       67    609
6 months    ki1114097-CMIN             PERU                           1                      1       14    609
6 months    ki1114097-CMIN             PERU                           2                      0       97    609
6 months    ki1114097-CMIN             PERU                           2                      1        4    609
6 months    ki1114097-CMIN             PERU                           3                      0      138    609
6 months    ki1114097-CMIN             PERU                           3                      1        5    609
6 months    ki1114097-CMIN             PERU                           4                      0      269    609
6 months    ki1114097-CMIN             PERU                           4                      1       15    609
9 months    ki0047075b-MAL-ED          BANGLADESH                     1                      0       20    233
9 months    ki0047075b-MAL-ED          BANGLADESH                     1                      1        9    233
9 months    ki0047075b-MAL-ED          BANGLADESH                     2                      0       57    233
9 months    ki0047075b-MAL-ED          BANGLADESH                     2                      1       28    233
9 months    ki0047075b-MAL-ED          BANGLADESH                     3                      0       71    233
9 months    ki0047075b-MAL-ED          BANGLADESH                     3                      1       21    233
9 months    ki0047075b-MAL-ED          BANGLADESH                     4                      0       27    233
9 months    ki0047075b-MAL-ED          BANGLADESH                     4                      1        0    233
9 months    ki0047075b-MAL-ED          BRAZIL                         1                      0       23    198
9 months    ki0047075b-MAL-ED          BRAZIL                         1                      1        0    198
9 months    ki0047075b-MAL-ED          BRAZIL                         2                      0       70    198
9 months    ki0047075b-MAL-ED          BRAZIL                         2                      1        2    198
9 months    ki0047075b-MAL-ED          BRAZIL                         3                      0       79    198
9 months    ki0047075b-MAL-ED          BRAZIL                         3                      1        1    198
9 months    ki0047075b-MAL-ED          BRAZIL                         4                      0       22    198
9 months    ki0047075b-MAL-ED          BRAZIL                         4                      1        1    198
9 months    ki0047075b-MAL-ED          INDIA                          1                      0       82    231
9 months    ki0047075b-MAL-ED          INDIA                          1                      1       28    231
9 months    ki0047075b-MAL-ED          INDIA                          2                      0       77    231
9 months    ki0047075b-MAL-ED          INDIA                          2                      1       18    231
9 months    ki0047075b-MAL-ED          INDIA                          3                      0       18    231
9 months    ki0047075b-MAL-ED          INDIA                          3                      1        5    231
9 months    ki0047075b-MAL-ED          INDIA                          4                      0        2    231
9 months    ki0047075b-MAL-ED          INDIA                          4                      1        1    231
9 months    ki0047075b-MAL-ED          NEPAL                          1                      0       57    231
9 months    ki0047075b-MAL-ED          NEPAL                          1                      1        7    231
9 months    ki0047075b-MAL-ED          NEPAL                          2                      0       88    231
9 months    ki0047075b-MAL-ED          NEPAL                          2                      1        9    231
9 months    ki0047075b-MAL-ED          NEPAL                          3                      0       57    231
9 months    ki0047075b-MAL-ED          NEPAL                          3                      1        2    231
9 months    ki0047075b-MAL-ED          NEPAL                          4                      0       10    231
9 months    ki0047075b-MAL-ED          NEPAL                          4                      1        1    231
9 months    ki0047075b-MAL-ED          PERU                           1                      0       29    251
9 months    ki0047075b-MAL-ED          PERU                           1                      1       13    251
9 months    ki0047075b-MAL-ED          PERU                           2                      0       58    251
9 months    ki0047075b-MAL-ED          PERU                           2                      1       15    251
9 months    ki0047075b-MAL-ED          PERU                           3                      0       55    251
9 months    ki0047075b-MAL-ED          PERU                           3                      1       21    251
9 months    ki0047075b-MAL-ED          PERU                           4                      0       43    251
9 months    ki0047075b-MAL-ED          PERU                           4                      1       17    251
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                      0       27    250
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                      1       13    250
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                      0       42    250
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                      1       12    250
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                      0       66    250
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                      1       19    250
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                      0       56    250
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                      1       15    250
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      0       13    236
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                      1       13    236
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      0       32    236
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                      1       30    236
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      0       53    236
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                      1       25    236
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      0       42    236
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                      1       28    236
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                      0        7     50
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                      1        2     50
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                      0       15     50
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                      1        7     50
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                      0        4     50
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                      1        9     50
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          4                      0        3     50
9 months    ki1000108-CMC-V-BCS-2002   INDIA                          4                      1        3     50
9 months    ki1000108-IRC              INDIA                          1                      0        0      5
9 months    ki1000108-IRC              INDIA                          1                      1        0      5
9 months    ki1000108-IRC              INDIA                          2                      0        4      5
9 months    ki1000108-IRC              INDIA                          2                      1        0      5
9 months    ki1000108-IRC              INDIA                          3                      0        0      5
9 months    ki1000108-IRC              INDIA                          3                      1        1      5
9 months    ki1000108-IRC              INDIA                          4                      0        0      5
9 months    ki1000108-IRC              INDIA                          4                      1        0      5
9 months    ki1000109-EE               PAKISTAN                       1                      0        6     78
9 months    ki1000109-EE               PAKISTAN                       1                      1       22     78
9 months    ki1000109-EE               PAKISTAN                       2                      0       12     78
9 months    ki1000109-EE               PAKISTAN                       2                      1       16     78
9 months    ki1000109-EE               PAKISTAN                       3                      0        6     78
9 months    ki1000109-EE               PAKISTAN                       3                      1       12     78
9 months    ki1000109-EE               PAKISTAN                       4                      0        2     78
9 months    ki1000109-EE               PAKISTAN                       4                      1        2     78
9 months    ki1017093b-PROVIDE         BANGLADESH                     1                      0       28    119
9 months    ki1017093b-PROVIDE         BANGLADESH                     1                      1        9    119
9 months    ki1017093b-PROVIDE         BANGLADESH                     2                      0       26    119
9 months    ki1017093b-PROVIDE         BANGLADESH                     2                      1        7    119
9 months    ki1017093b-PROVIDE         BANGLADESH                     3                      0       19    119
9 months    ki1017093b-PROVIDE         BANGLADESH                     3                      1        9    119
9 months    ki1017093b-PROVIDE         BANGLADESH                     4                      0       16    119
9 months    ki1017093b-PROVIDE         BANGLADESH                     4                      1        5    119
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      0      337   1655
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                      1       77   1655
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      0      310   1655
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                      1       56   1655
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      0      346   1655
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                      1       47   1655
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      0      432   1655
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                      1       50   1655
9 months    ki1101329-Keneba           GAMBIA                         1                      0      218    679
9 months    ki1101329-Keneba           GAMBIA                         1                      1       54    679
9 months    ki1101329-Keneba           GAMBIA                         2                      0      131    679
9 months    ki1101329-Keneba           GAMBIA                         2                      1       22    679
9 months    ki1101329-Keneba           GAMBIA                         3                      0      134    679
9 months    ki1101329-Keneba           GAMBIA                         3                      1       14    679
9 months    ki1101329-Keneba           GAMBIA                         4                      0       98    679
9 months    ki1101329-Keneba           GAMBIA                         4                      1        8    679
9 months    ki1112895-Guatemala BSC    GUATEMALA                      1                      0       22    178
9 months    ki1112895-Guatemala BSC    GUATEMALA                      1                      1       18    178
9 months    ki1112895-Guatemala BSC    GUATEMALA                      2                      0       33    178
9 months    ki1112895-Guatemala BSC    GUATEMALA                      2                      1       20    178
9 months    ki1112895-Guatemala BSC    GUATEMALA                      3                      0       25    178
9 months    ki1112895-Guatemala BSC    GUATEMALA                      3                      1       18    178
9 months    ki1112895-Guatemala BSC    GUATEMALA                      4                      0       28    178
9 months    ki1112895-Guatemala BSC    GUATEMALA                      4                      1       14    178
9 months    ki1113344-GMS-Nepal        NEPAL                          1                      0        6      6
9 months    ki1113344-GMS-Nepal        NEPAL                          1                      1        0      6
9 months    ki1113344-GMS-Nepal        NEPAL                          2                      0        0      6
9 months    ki1113344-GMS-Nepal        NEPAL                          2                      1        0      6
9 months    ki1113344-GMS-Nepal        NEPAL                          3                      0        0      6
9 months    ki1113344-GMS-Nepal        NEPAL                          3                      1        0      6
9 months    ki1113344-GMS-Nepal        NEPAL                          4                      0        0      6
9 months    ki1113344-GMS-Nepal        NEPAL                          4                      1        0      6
9 months    ki1114097-CMIN             BANGLADESH                     1                      0       56    244
9 months    ki1114097-CMIN             BANGLADESH                     1                      1       59    244
9 months    ki1114097-CMIN             BANGLADESH                     2                      0       35    244
9 months    ki1114097-CMIN             BANGLADESH                     2                      1       24    244
9 months    ki1114097-CMIN             BANGLADESH                     3                      0       27    244
9 months    ki1114097-CMIN             BANGLADESH                     3                      1       17    244
9 months    ki1114097-CMIN             BANGLADESH                     4                      0       18    244
9 months    ki1114097-CMIN             BANGLADESH                     4                      1        8    244
9 months    ki1114097-CMIN             PERU                           1                      0       30    573
9 months    ki1114097-CMIN             PERU                           1                      1       18    573
9 months    ki1114097-CMIN             PERU                           2                      0       56    573
9 months    ki1114097-CMIN             PERU                           2                      1       20    573
9 months    ki1114097-CMIN             PERU                           3                      0      113    573
9 months    ki1114097-CMIN             PERU                           3                      1       16    573
9 months    ki1114097-CMIN             PERU                           4                      0      295    573
9 months    ki1114097-CMIN             PERU                           4                      1       25    573


The following strata were considered:

* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 12 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 12 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 12 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 12 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 12 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 12 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 12 months, studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 12 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 12 months, studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 12 months, studyid: ki1114097-CMIN, country: PERU
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 18 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 18 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 18 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 18 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 18 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 18 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 18 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 18 months, studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 18 months, studyid: ki1114097-CMIN, country: PERU
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 3 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 3 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 3 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 3 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 3 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 3 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 3 months, studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 3 months, studyid: ki1114097-CMIN, country: PERU
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 6 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 6 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 6 months, studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 6 months, studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 6 months, studyid: ki1114097-CMIN, country: PERU
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 9 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 9 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 9 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 9 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 9 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 9 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 9 months, studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 9 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 9 months, studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 9 months, studyid: ki1114097-CMIN, country: PERU

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 12 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 12 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 12 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 12 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 12 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 18 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 18 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 18 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 18 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 18 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 18 months, studyid: ki1114097-CMIN, country: PERU
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 3 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 3 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 3 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 3 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 6 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 6 months, studyid: ki1114097-CMIN, country: PERU
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 9 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 9 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 9 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 9 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 9 months, studyid: ki1113344-GMS-Nepal, country: NEPAL

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness







# Results Detail

## Results Plots
![](/tmp/408f54fb-85b1-4989-9b2d-17ed0d6a1f13/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/408f54fb-85b1-4989-9b2d-17ed0d6a1f13/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/408f54fb-85b1-4989-9b2d-17ed0d6a1f13/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/408f54fb-85b1-4989-9b2d-17ed0d6a1f13/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat      studyid                    country                        intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  -------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  ----------
12 months   ki0047075b-MAL-ED          PERU                           1                    NA                0.2333333   0.0816734   0.3849933
12 months   ki0047075b-MAL-ED          PERU                           2                    NA                0.4202899   0.3035833   0.5369964
12 months   ki0047075b-MAL-ED          PERU                           3                    NA                0.3186813   0.2227473   0.4146153
12 months   ki0047075b-MAL-ED          PERU                           4                    NA                0.2222222   0.1111093   0.3333351
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                0.3777778   0.2358383   0.5197172
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                    NA                0.3469388   0.2133950   0.4804826
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                    NA                0.2380952   0.1468302   0.3293603
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                    NA                0.1666667   0.0804113   0.2529220
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                0.6774194   0.5125055   0.8423333
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                    NA                0.4590164   0.3336932   0.5843396
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                    NA                0.5384615   0.4275890   0.6493341
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                    NA                0.4262295   0.3018594   0.5505996
12 months   ki1017093b-PROVIDE         BANGLADESH                     1                    NA                0.4166667   0.3392322   0.4941012
12 months   ki1017093b-PROVIDE         BANGLADESH                     2                    NA                0.3116883   0.2384672   0.3849094
12 months   ki1017093b-PROVIDE         BANGLADESH                     3                    NA                0.1597222   0.0998319   0.2196126
12 months   ki1017093b-PROVIDE         BANGLADESH                     4                    NA                0.1368421   0.0676690   0.2060152
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                0.2553191   0.2044073   0.3062310
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    NA                0.2299652   0.1812615   0.2786688
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    NA                0.1212121   0.0840797   0.1583446
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    NA                0.1111111   0.0811506   0.1410716
12 months   ki1101329-Keneba           GAMBIA                         1                    NA                0.3179916   0.2589023   0.3770810
12 months   ki1101329-Keneba           GAMBIA                         2                    NA                0.1363636   0.0821186   0.1906087
12 months   ki1101329-Keneba           GAMBIA                         3                    NA                0.1127820   0.0589779   0.1665860
12 months   ki1101329-Keneba           GAMBIA                         4                    NA                0.1585366   0.0794176   0.2376556
12 months   ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                0.6875000   0.5263801   0.8486199
12 months   ki1112895-Guatemala BSC    GUATEMALA                      2                    NA                0.5714286   0.4212767   0.7215804
12 months   ki1112895-Guatemala BSC    GUATEMALA                      3                    NA                0.3947368   0.2388186   0.5506551
12 months   ki1112895-Guatemala BSC    GUATEMALA                      4                    NA                0.3571429   0.2117590   0.5025268
12 months   ki1114097-CMIN             BANGLADESH                     1                    NA                0.6666667   0.5799513   0.7533820
12 months   ki1114097-CMIN             BANGLADESH                     2                    NA                0.5285714   0.4113882   0.6457547
12 months   ki1114097-CMIN             BANGLADESH                     3                    NA                0.3125000   0.1515685   0.4734315
12 months   ki1114097-CMIN             BANGLADESH                     4                    NA                0.2916667   0.1094402   0.4738931
12 months   ki1114097-CMIN             PERU                           1                    NA                0.5263158   0.3674201   0.6852115
12 months   ki1114097-CMIN             PERU                           2                    NA                0.3157895   0.2111915   0.4203874
12 months   ki1114097-CMIN             PERU                           3                    NA                0.1788618   0.1110741   0.2466494
12 months   ki1114097-CMIN             PERU                           4                    NA                0.1331269   0.0960464   0.1702074
18 months   ki0047075b-MAL-ED          PERU                           1                    NA                0.5227273   0.3748025   0.6706521
18 months   ki0047075b-MAL-ED          PERU                           2                    NA                0.4393939   0.3193803   0.5594075
18 months   ki0047075b-MAL-ED          PERU                           3                    NA                0.4285714   0.3177832   0.5393597
18 months   ki0047075b-MAL-ED          PERU                           4                    NA                0.3548387   0.1860221   0.5236554
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                0.5416667   0.3419079   0.7414255
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                    NA                0.3777778   0.2358264   0.5197291
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                    NA                0.3544304   0.2487296   0.4601312
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                    NA                0.2608696   0.1709544   0.3507848
18 months   ki1017093b-PROVIDE         BANGLADESH                     1                    NA                0.5037594   0.4186838   0.5888350
18 months   ki1017093b-PROVIDE         BANGLADESH                     2                    NA                0.3504274   0.2638721   0.4369826
18 months   ki1017093b-PROVIDE         BANGLADESH                     3                    NA                0.3033708   0.2077470   0.3989946
18 months   ki1017093b-PROVIDE         BANGLADESH                     4                    NA                0.1733333   0.0875607   0.2591060
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                0.3284314   0.2639470   0.3929158
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    NA                0.2545455   0.1880406   0.3210503
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    NA                0.2318841   0.1743578   0.2894103
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    NA                0.1756272   0.1309529   0.2203016
18 months   ki1101329-Keneba           GAMBIA                         1                    NA                0.3839662   0.3219967   0.4459358
18 months   ki1101329-Keneba           GAMBIA                         2                    NA                0.2160494   0.1526234   0.2794754
18 months   ki1101329-Keneba           GAMBIA                         3                    NA                0.1885246   0.1190629   0.2579863
18 months   ki1101329-Keneba           GAMBIA                         4                    NA                0.1444444   0.0717574   0.2171315
18 months   ki1114097-CMIN             BANGLADESH                     1                    NA                0.8103448   0.7388507   0.8818390
18 months   ki1114097-CMIN             BANGLADESH                     2                    NA                0.7936508   0.6935061   0.8937955
18 months   ki1114097-CMIN             BANGLADESH                     3                    NA                0.5000000   0.3315727   0.6684273
18 months   ki1114097-CMIN             BANGLADESH                     4                    NA                0.4000000   0.1848345   0.6151655
3 months    ki0047075b-MAL-ED          PERU                           1                    NA                0.3888889   0.1632801   0.6144977
3 months    ki0047075b-MAL-ED          PERU                           2                    NA                0.2285714   0.1300276   0.3271152
3 months    ki0047075b-MAL-ED          PERU                           3                    NA                0.2323232   0.1489863   0.3156601
3 months    ki0047075b-MAL-ED          PERU                           4                    NA                0.2526316   0.1650992   0.3401640
3 months    ki1017093b-PROVIDE         BANGLADESH                     1                    NA                0.1093750   0.0711097   0.1476403
3 months    ki1017093b-PROVIDE         BANGLADESH                     2                    NA                0.1321839   0.0818168   0.1825510
3 months    ki1017093b-PROVIDE         BANGLADESH                     3                    NA                0.1869919   0.1180275   0.2559562
3 months    ki1017093b-PROVIDE         BANGLADESH                     4                    NA                0.2352941   0.0925916   0.3779966
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                0.0606586   0.0411774   0.0801398
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    NA                0.0469388   0.0282072   0.0656704
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    NA                0.0705394   0.0476753   0.0934035
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    NA                0.0891239   0.0674147   0.1108331
3 months    ki1101329-Keneba           GAMBIA                         1                    NA                0.1349693   0.0824771   0.1874615
3 months    ki1101329-Keneba           GAMBIA                         2                    NA                0.1000000   0.0462862   0.1537138
3 months    ki1101329-Keneba           GAMBIA                         3                    NA                0.1459459   0.0950353   0.1968566
3 months    ki1101329-Keneba           GAMBIA                         4                    NA                0.1506276   0.1052483   0.1960069
3 months    ki1114097-CMIN             BANGLADESH                     1                    NA                0.2717391   0.1806532   0.3628250
3 months    ki1114097-CMIN             BANGLADESH                     2                    NA                0.2777778   0.1741101   0.3814455
3 months    ki1114097-CMIN             BANGLADESH                     3                    NA                0.4166667   0.2769148   0.5564185
3 months    ki1114097-CMIN             BANGLADESH                     4                    NA                0.6111111   0.4515426   0.7706796
3 months    ki1114097-CMIN             PERU                           1                    NA                0.1487603   0.0853010   0.2122197
3 months    ki1114097-CMIN             PERU                           2                    NA                0.0420168   0.0059393   0.0780943
3 months    ki1114097-CMIN             PERU                           3                    NA                0.0322581   0.0044192   0.0600970
3 months    ki1114097-CMIN             PERU                           4                    NA                0.0785340   0.0403510   0.1167171
6 months    ki0047075b-MAL-ED          PERU                           1                    NA                0.2647059   0.1161374   0.4132744
6 months    ki0047075b-MAL-ED          PERU                           2                    NA                0.1875000   0.0916976   0.2833024
6 months    ki0047075b-MAL-ED          PERU                           3                    NA                0.1702128   0.0940979   0.2463276
6 months    ki0047075b-MAL-ED          PERU                           4                    NA                0.2692308   0.1706121   0.3678494
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                0.2368421   0.1013981   0.3722861
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                    NA                0.1458333   0.0457886   0.2458780
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                    NA                0.1866667   0.0983074   0.2750259
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                    NA                0.2333333   0.1457774   0.3208892
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                0.2500000   0.0996606   0.4003394
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                    NA                0.1698113   0.0685179   0.2711047
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                    NA                0.2631579   0.1639524   0.3623634
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                    NA                0.2962963   0.1966496   0.3959430
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                0.1049383   0.0776838   0.1321927
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    NA                0.1464646   0.1116316   0.1812977
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    NA                0.1089744   0.0807355   0.1372132
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    NA                0.1183971   0.0913648   0.1454294
6 months    ki1101329-Keneba           GAMBIA                         1                    NA                0.1221719   0.0789671   0.1653768
6 months    ki1101329-Keneba           GAMBIA                         2                    NA                0.0721154   0.0369376   0.1072931
6 months    ki1101329-Keneba           GAMBIA                         3                    NA                0.1180124   0.0681446   0.1678803
6 months    ki1101329-Keneba           GAMBIA                         4                    NA                0.1582278   0.1012837   0.2151720
6 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                0.3076923   0.1952491   0.4201355
6 months    ki1112895-Guatemala BSC    GUATEMALA                      2                    NA                0.3529412   0.2391128   0.4667696
6 months    ki1112895-Guatemala BSC    GUATEMALA                      3                    NA                0.3061224   0.1768003   0.4354446
6 months    ki1112895-Guatemala BSC    GUATEMALA                      4                    NA                0.2156863   0.1025627   0.3288099
6 months    ki1114097-CMIN             BANGLADESH                     1                    NA                0.3826087   0.2935929   0.4716245
6 months    ki1114097-CMIN             BANGLADESH                     2                    NA                0.4576271   0.3302365   0.5850177
6 months    ki1114097-CMIN             BANGLADESH                     3                    NA                0.2500000   0.1155288   0.3844712
6 months    ki1114097-CMIN             BANGLADESH                     4                    NA                0.3600000   0.1714486   0.5485514
9 months    ki0047075b-MAL-ED          PERU                           1                    NA                0.3095238   0.1694323   0.4496153
9 months    ki0047075b-MAL-ED          PERU                           2                    NA                0.2054795   0.1126063   0.2983526
9 months    ki0047075b-MAL-ED          PERU                           3                    NA                0.2763158   0.1755796   0.3770520
9 months    ki0047075b-MAL-ED          PERU                           4                    NA                0.2833333   0.1690858   0.3975808
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                0.3250000   0.1795606   0.4704394
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                    NA                0.2222222   0.1111148   0.3333296
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                    NA                0.2235294   0.1347855   0.3122734
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                    NA                0.2112676   0.1161260   0.3064092
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                0.5000000   0.3074012   0.6925988
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                    NA                0.4838710   0.3592135   0.6085284
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                    NA                0.3205128   0.2167274   0.4242982
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                    NA                0.4000000   0.2849923   0.5150077
9 months    ki1017093b-PROVIDE         BANGLADESH                     1                    NA                0.2432432   0.1044149   0.3820716
9 months    ki1017093b-PROVIDE         BANGLADESH                     2                    NA                0.2121212   0.0720511   0.3521913
9 months    ki1017093b-PROVIDE         BANGLADESH                     3                    NA                0.3214286   0.1477119   0.4951453
9 months    ki1017093b-PROVIDE         BANGLADESH                     4                    NA                0.2380952   0.0551603   0.4210302
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                0.1859903   0.1484983   0.2234824
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    NA                0.1530055   0.1161134   0.1898975
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    NA                0.1195929   0.0875023   0.1516834
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    NA                0.1037344   0.0765052   0.1309637
9 months    ki1101329-Keneba           GAMBIA                         1                    NA                0.1985294   0.1510899   0.2459689
9 months    ki1101329-Keneba           GAMBIA                         2                    NA                0.1437908   0.0881520   0.1994297
9 months    ki1101329-Keneba           GAMBIA                         3                    NA                0.0945946   0.0474109   0.1417783
9 months    ki1101329-Keneba           GAMBIA                         4                    NA                0.0754717   0.0251486   0.1257948
9 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                0.4500000   0.2953930   0.6046070
9 months    ki1112895-Guatemala BSC    GUATEMALA                      2                    NA                0.3773585   0.2464916   0.5082253
9 months    ki1112895-Guatemala BSC    GUATEMALA                      3                    NA                0.4186047   0.2707364   0.5664729
9 months    ki1112895-Guatemala BSC    GUATEMALA                      4                    NA                0.3333333   0.1903648   0.4763019
9 months    ki1114097-CMIN             BANGLADESH                     1                    NA                0.5130435   0.4215030   0.6045839
9 months    ki1114097-CMIN             BANGLADESH                     2                    NA                0.4067797   0.2811762   0.5323831
9 months    ki1114097-CMIN             BANGLADESH                     3                    NA                0.3863636   0.2421962   0.5305311
9 months    ki1114097-CMIN             BANGLADESH                     4                    NA                0.3076923   0.1299212   0.4854634
9 months    ki1114097-CMIN             PERU                           1                    NA                0.3750000   0.2379237   0.5120763
9 months    ki1114097-CMIN             PERU                           2                    NA                0.2631579   0.1640710   0.3622447
9 months    ki1114097-CMIN             PERU                           3                    NA                0.1240310   0.0671009   0.1809611
9 months    ki1114097-CMIN             PERU                           4                    NA                0.0781250   0.0486955   0.1075545


### Parameter: E(Y)


agecat      studyid                    country                        intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  -------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  ----------
12 months   ki0047075b-MAL-ED          PERU                           NA                   NA                0.3155738   0.2571407   0.3740068
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   NA                   NA                0.2640000   0.2092493   0.3187507
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.5064935   0.4418809   0.5711062
12 months   ki1017093b-PROVIDE         BANGLADESH                     NA                   NA                0.2714026   0.2341712   0.3086339
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.1714507   0.1508672   0.1920342
12 months   ki1101329-Keneba           GAMBIA                         NA                   NA                0.2055921   0.1734423   0.2377419
12 months   ki1112895-Guatemala BSC    GUATEMALA                      NA                   NA                0.4935065   0.4142863   0.5727267
12 months   ki1114097-CMIN             BANGLADESH                     NA                   NA                0.5416667   0.4784974   0.6048359
12 months   ki1114097-CMIN             PERU                           NA                   NA                0.1946429   0.1618216   0.2274641
18 months   ki0047075b-MAL-ED          PERU                           NA                   NA                0.4403670   0.3743163   0.5064176
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   NA                   NA                0.3416667   0.2815391   0.4017942
18 months   ki1017093b-PROVIDE         BANGLADESH                     NA                   NA                0.3574879   0.3112664   0.4037095
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.2409357   0.2122537   0.2696176
18 months   ki1101329-Keneba           GAMBIA                         NA                   NA                0.2651391   0.2301105   0.3001677
18 months   ki1114097-CMIN             BANGLADESH                     NA                   NA                0.7253219   0.6678862   0.7827575
3 months    ki0047075b-MAL-ED          PERU                           NA                   NA                0.2482270   0.1977186   0.2987353
3 months    ki1017093b-PROVIDE         BANGLADESH                     NA                   NA                0.1396934   0.1116252   0.1677615
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.0682949   0.0577780   0.0788117
3 months    ki1101329-Keneba           GAMBIA                         NA                   NA                0.1371994   0.1118203   0.1625786
3 months    ki1114097-CMIN             BANGLADESH                     NA                   NA                0.3508065   0.2912923   0.4103206
3 months    ki1114097-CMIN             PERU                           NA                   NA                0.0733788   0.0522485   0.0945092
6 months    ki0047075b-MAL-ED          PERU                           NA                   NA                0.2148148   0.1657364   0.2638932
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   NA                   NA                0.2031873   0.1533098   0.2530647
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.2520661   0.1972475   0.3068848
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.1184834   0.1039441   0.1330227
6 months    ki1101329-Keneba           GAMBIA                         NA                   NA                0.1149733   0.0920981   0.1378484
6 months    ki1112895-Guatemala BSC    GUATEMALA                      NA                   NA                0.3004292   0.2414375   0.3594209
6 months    ki1114097-CMIN             BANGLADESH                     NA                   NA                0.3765690   0.3150122   0.4381258
9 months    ki0047075b-MAL-ED          PERU                           NA                   NA                0.2629482   0.2083772   0.3175192
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   NA                   NA                0.2360000   0.1832587   0.2887413
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.4067797   0.3439736   0.4695858
9 months    ki1017093b-PROVIDE         BANGLADESH                     NA                   NA                0.2521008   0.1737550   0.3304466
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.1389728   0.1223021   0.1556435
9 months    ki1101329-Keneba           GAMBIA                         NA                   NA                0.1443299   0.1178775   0.1707823
9 months    ki1112895-Guatemala BSC    GUATEMALA                      NA                   NA                0.3932584   0.3212966   0.4652203
9 months    ki1114097-CMIN             BANGLADESH                     NA                   NA                0.4426230   0.3801724   0.5050735
9 months    ki1114097-CMIN             PERU                           NA                   NA                0.1378709   0.1096173   0.1661244


### Parameter: RR


agecat      studyid                    country                        intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  -------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  ----------
12 months   ki0047075b-MAL-ED          PERU                           1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki0047075b-MAL-ED          PERU                           2                    1                 1.8012422   0.8884067   3.6520140
12 months   ki0047075b-MAL-ED          PERU                           3                    1                 1.3657771   0.6672600   2.7955324
12 months   ki0047075b-MAL-ED          PERU                           4                    1                 0.9523810   0.4194406   2.1624740
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                    1                 0.9183673   0.5363048   1.5726105
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                    1                 0.6302521   0.3684754   1.0780032
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                    1                 0.4411765   0.2327370   0.8362947
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                    1                 0.6775956   0.4700095   0.9768651
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                    1                 0.7948718   0.5778621   1.0933771
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                    1                 0.6291959   0.4302786   0.9200725
12 months   ki1017093b-PROVIDE         BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki1017093b-PROVIDE         BANGLADESH                     2                    1                 0.7480519   0.5544258   1.0092996
12 months   ki1017093b-PROVIDE         BANGLADESH                     3                    1                 0.3833333   0.2522477   0.5825403
12 months   ki1017093b-PROVIDE         BANGLADESH                     4                    1                 0.3284211   0.1916596   0.5627705
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    1                 0.9006969   0.6733601   1.2047860
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    1                 0.4747475   0.3293953   0.6842391
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    1                 0.4351852   0.3111906   0.6085857
12 months   ki1101329-Keneba           GAMBIA                         1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki1101329-Keneba           GAMBIA                         2                    1                 0.4288278   0.2764411   0.6652168
12 months   ki1101329-Keneba           GAMBIA                         3                    1                 0.3546696   0.2125574   0.5917953
12 months   ki1101329-Keneba           GAMBIA                         4                    1                 0.4985558   0.2927108   0.8491586
12 months   ki1112895-Guatemala BSC    GUATEMALA                      1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki1112895-Guatemala BSC    GUATEMALA                      2                    1                 0.8311688   0.5844908   1.1819546
12 months   ki1112895-Guatemala BSC    GUATEMALA                      3                    1                 0.5741627   0.3627190   0.9088656
12 months   ki1112895-Guatemala BSC    GUATEMALA                      4                    1                 0.5194805   0.3247688   0.8309295
12 months   ki1114097-CMIN             BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki1114097-CMIN             BANGLADESH                     2                    1                 0.7928571   0.6131466   1.0252400
12 months   ki1114097-CMIN             BANGLADESH                     3                    1                 0.4687500   0.2755904   0.7972939
12 months   ki1114097-CMIN             BANGLADESH                     4                    1                 0.4375000   0.2311123   0.8281957
12 months   ki1114097-CMIN             PERU                           1                    1                 1.0000000   1.0000000   1.0000000
12 months   ki1114097-CMIN             PERU                           2                    1                 0.6000000   0.3832779   0.9392664
12 months   ki1114097-CMIN             PERU                           3                    1                 0.3398374   0.2093327   0.5517030
12 months   ki1114097-CMIN             PERU                           4                    1                 0.2529412   0.1677364   0.3814273
18 months   ki0047075b-MAL-ED          PERU                           1                    1                 1.0000000   1.0000000   1.0000000
18 months   ki0047075b-MAL-ED          PERU                           2                    1                 0.8405797   0.5672461   1.2456221
18 months   ki0047075b-MAL-ED          PERU                           3                    1                 0.8198758   0.5588431   1.2028355
18 months   ki0047075b-MAL-ED          PERU                           4                    1                 0.6788219   0.3902556   1.1807624
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    1                 1.0000000   1.0000000   1.0000000
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                    1                 0.6974359   0.4119570   1.1807466
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                    1                 0.6543330   0.4072127   1.0514202
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4                    1                 0.4816054   0.2907153   0.7978381
18 months   ki1017093b-PROVIDE         BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
18 months   ki1017093b-PROVIDE         BANGLADESH                     2                    1                 0.6956244   0.5157361   0.9382577
18 months   ki1017093b-PROVIDE         BANGLADESH                     3                    1                 0.6022137   0.4211616   0.8610978
18 months   ki1017093b-PROVIDE         BANGLADESH                     4                    1                 0.3440796   0.2039768   0.5804130
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    1                 0.7750339   0.5589651   1.0746245
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    1                 0.7060350   0.5145477   0.9687839
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    1                 0.5347456   0.3877885   0.7373940
18 months   ki1101329-Keneba           GAMBIA                         1                    1                 1.0000000   1.0000000   1.0000000
18 months   ki1101329-Keneba           GAMBIA                         2                    1                 0.5626781   0.4025008   0.7865987
18 months   ki1101329-Keneba           GAMBIA                         3                    1                 0.4909926   0.3283835   0.7341225
18 months   ki1101329-Keneba           GAMBIA                         4                    1                 0.3761905   0.2217675   0.6381424
18 months   ki1114097-CMIN             BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
18 months   ki1114097-CMIN             BANGLADESH                     2                    1                 0.9793989   0.8396387   1.1424225
18 months   ki1114097-CMIN             BANGLADESH                     3                    1                 0.6170213   0.4355835   0.8740350
18 months   ki1114097-CMIN             BANGLADESH                     4                    1                 0.4936170   0.2861908   0.8513821
3 months    ki0047075b-MAL-ED          PERU                           1                    1                 1.0000000   1.0000000   1.0000000
3 months    ki0047075b-MAL-ED          PERU                           2                    1                 0.5877551   0.2852929   1.2108821
3 months    ki0047075b-MAL-ED          PERU                           3                    1                 0.5974026   0.3020256   1.1816545
3 months    ki0047075b-MAL-ED          PERU                           4                    1                 0.6496241   0.3305194   1.2768129
3 months    ki1017093b-PROVIDE         BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
3 months    ki1017093b-PROVIDE         BANGLADESH                     2                    1                 1.2085386   0.7204517   2.0272915
3 months    ki1017093b-PROVIDE         BANGLADESH                     3                    1                 1.7096400   1.0283282   2.8423500
3 months    ki1017093b-PROVIDE         BANGLADESH                     4                    1                 2.1512605   1.0681145   4.3327956
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    1                 0.7738193   0.4636320   1.2915335
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    1                 1.1628927   0.7368388   1.8352990
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    1                 1.4692706   0.9818467   2.1986692
3 months    ki1101329-Keneba           GAMBIA                         1                    1                 1.0000000   1.0000000   1.0000000
3 months    ki1101329-Keneba           GAMBIA                         2                    1                 0.7409091   0.3817332   1.4380366
3 months    ki1101329-Keneba           GAMBIA                         3                    1                 1.0813268   0.6413051   1.8232625
3 months    ki1101329-Keneba           GAMBIA                         4                    1                 1.1160137   0.6823632   1.8252545
3 months    ki1114097-CMIN             BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
3 months    ki1114097-CMIN             BANGLADESH                     2                    1                 1.0222222   0.6189964   1.6881168
3 months    ki1114097-CMIN             BANGLADESH                     3                    1                 1.5333333   0.9543334   2.4636161
3 months    ki1114097-CMIN             BANGLADESH                     4                    1                 2.2488889   1.4704097   3.4395183
3 months    ki1114097-CMIN             PERU                           1                    1                 1.0000000   1.0000000   1.0000000
3 months    ki1114097-CMIN             PERU                           2                    1                 0.2824463   0.1082794   0.7367596
3 months    ki1114097-CMIN             PERU                           3                    1                 0.2168459   0.0828064   0.5678565
3 months    ki1114097-CMIN             PERU                           4                    1                 0.5279232   0.2764801   1.0080396
6 months    ki0047075b-MAL-ED          PERU                           1                    1                 1.0000000   1.0000000   1.0000000
6 months    ki0047075b-MAL-ED          PERU                           2                    1                 0.7083333   0.3315960   1.5130945
6 months    ki0047075b-MAL-ED          PERU                           3                    1                 0.6430260   0.3137406   1.3179119
6 months    ki0047075b-MAL-ED          PERU                           4                    1                 1.0170940   0.5203449   1.9880665
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    1                 1.0000000   1.0000000   1.0000000
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                    1                 0.6157407   0.2520695   1.5040955
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                    1                 0.7881481   0.3751487   1.6558169
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                    1                 0.9851852   0.4971229   1.9524141
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                    1                 0.6792453   0.2911848   1.5844718
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                    1                 1.0526316   0.5176493   2.1405093
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                    1                 1.1851852   0.5950497   2.3605824
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    1                 1.3957219   0.9814285   1.9849023
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    1                 1.0384615   0.7195397   1.4987393
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    1                 1.1282546   0.7984070   1.5943729
6 months    ki1101329-Keneba           GAMBIA                         1                    1                 1.0000000   1.0000000   1.0000000
6 months    ki1101329-Keneba           GAMBIA                         2                    1                 0.5902778   0.3231420   1.0782501
6 months    ki1101329-Keneba           GAMBIA                         3                    1                 0.9659535   0.5567390   1.6759490
6 months    ki1101329-Keneba           GAMBIA                         4                    1                 1.2951242   0.7819595   2.1450559
6 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    1                 1.0000000   1.0000000   1.0000000
6 months    ki1112895-Guatemala BSC    GUATEMALA                      2                    1                 1.1470588   0.7045457   1.8675069
6 months    ki1112895-Guatemala BSC    GUATEMALA                      3                    1                 0.9948980   0.5691017   1.7392709
6 months    ki1112895-Guatemala BSC    GUATEMALA                      4                    1                 0.7009804   0.3699026   1.3283863
6 months    ki1114097-CMIN             BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
6 months    ki1114097-CMIN             BANGLADESH                     2                    1                 1.1960709   0.8321422   1.7191600
6 months    ki1114097-CMIN             BANGLADESH                     3                    1                 0.6534091   0.3636380   1.1740893
6 months    ki1114097-CMIN             BANGLADESH                     4                    1                 0.9409091   0.5304597   1.6689485
9 months    ki0047075b-MAL-ED          PERU                           1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki0047075b-MAL-ED          PERU                           2                    1                 0.6638567   0.3501730   1.2585371
9 months    ki0047075b-MAL-ED          PERU                           3                    1                 0.8927126   0.4992431   1.5962878
9 months    ki0047075b-MAL-ED          PERU                           4                    1                 0.9153846   0.4992839   1.6782614
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                    1                 0.6837607   0.3495355   1.3375713
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                    1                 0.6877828   0.3781315   1.2510070
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4                    1                 0.6500542   0.3445302   1.2265119
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                    1                 0.9677419   0.6088405   1.5382098
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                    1                 0.6410256   0.3875518   1.0602812
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                    1                 0.8000000   0.4946948   1.2937270
9 months    ki1017093b-PROVIDE         BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki1017093b-PROVIDE         BANGLADESH                     2                    1                 0.8720539   0.3643269   2.0873503
9 months    ki1017093b-PROVIDE         BANGLADESH                     3                    1                 1.3214286   0.6021137   2.9000727
9 months    ki1017093b-PROVIDE         BANGLADESH                     4                    1                 0.9788360   0.3758722   2.5490573
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                    1                 0.8226528   0.6007956   1.1264356
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                    1                 0.6430058   0.4596843   0.8994359
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                    1                 0.5577410   0.4005878   0.7765465
9 months    ki1101329-Keneba           GAMBIA                         1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki1101329-Keneba           GAMBIA                         2                    1                 0.7242798   0.4596195   1.1413383
9 months    ki1101329-Keneba           GAMBIA                         3                    1                 0.4764765   0.2740571   0.8284035
9 months    ki1101329-Keneba           GAMBIA                         4                    1                 0.3801537   0.1872174   0.7719200
9 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki1112895-Guatemala BSC    GUATEMALA                      2                    1                 0.8385744   0.5146742   1.3663151
9 months    ki1112895-Guatemala BSC    GUATEMALA                      3                    1                 0.9302326   0.5683098   1.5226424
9 months    ki1112895-Guatemala BSC    GUATEMALA                      4                    1                 0.7407407   0.4275642   1.2833088
9 months    ki1114097-CMIN             BANGLADESH                     1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki1114097-CMIN             BANGLADESH                     2                    1                 0.7928756   0.5550433   1.1326175
9 months    ki1114097-CMIN             BANGLADESH                     3                    1                 0.7530817   0.4979845   1.1388547
9 months    ki1114097-CMIN             BANGLADESH                     4                    1                 0.5997392   0.3276071   1.0979225
9 months    ki1114097-CMIN             PERU                           1                    1                 1.0000000   1.0000000   1.0000000
9 months    ki1114097-CMIN             PERU                           2                    1                 0.7017544   0.4152187   1.1860237
9 months    ki1114097-CMIN             PERU                           3                    1                 0.3307494   0.1839368   0.5947430
9 months    ki1114097-CMIN             PERU                           4                    1                 0.2083333   0.1232532   0.3521432


### Parameter: PAR


agecat      studyid                    country                        intervention_level   baseline_level      estimate     ci_lower     ci_upper
----------  -------------------------  -----------------------------  -------------------  ---------------  -----------  -----------  -----------
12 months   ki0047075b-MAL-ED          PERU                           1                    NA                 0.0822404   -0.0618403    0.2263211
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.1137778   -0.2398396    0.0122841
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.1709258   -0.3260770   -0.0157747
12 months   ki1017093b-PROVIDE         BANGLADESH                     1                    NA                -0.1452641   -0.2083090   -0.0822193
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.0838684   -0.1272454   -0.0404914
12 months   ki1101329-Keneba           GAMBIA                         1                    NA                -0.1123995   -0.1545915   -0.0702076
12 months   ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                -0.1939935   -0.3404416   -0.0475454
12 months   ki1114097-CMIN             BANGLADESH                     1                    NA                -0.1250000   -0.1910783   -0.0589217
12 months   ki1114097-CMIN             PERU                           1                    NA                -0.3316729   -0.4829957   -0.1803502
18 months   ki0047075b-MAL-ED          PERU                           1                    NA                -0.0823603   -0.2143127    0.0495921
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.2000000   -0.3885157   -0.0114843
18 months   ki1017093b-PROVIDE         BANGLADESH                     1                    NA                -0.1462715   -0.2150020   -0.0775410
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.0874957   -0.1422370   -0.0327544
18 months   ki1101329-Keneba           GAMBIA                         1                    NA                -0.1188271   -0.1645225   -0.0731318
18 months   ki1114097-CMIN             BANGLADESH                     1                    NA                -0.0850229   -0.1426492   -0.0273966
3 months    ki0047075b-MAL-ED          PERU                           1                    NA                -0.1406619   -0.3573475    0.0760236
3 months    ki1017093b-PROVIDE         BANGLADESH                     1                    NA                 0.0303184   -0.0009051    0.0615418
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                 0.0076363   -0.0094528    0.0247254
3 months    ki1101329-Keneba           GAMBIA                         1                    NA                 0.0022301   -0.0439109    0.0483711
3 months    ki1114097-CMIN             BANGLADESH                     1                    NA                 0.0790673    0.0036816    0.1544530
3 months    ki1114097-CMIN             PERU                           1                    NA                -0.0753815   -0.1283958   -0.0223672
6 months    ki0047075b-MAL-ED          PERU                           1                    NA                -0.0498911   -0.1874493    0.0876671
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.0336549   -0.1572597    0.0899500
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                 0.0020661   -0.1380398    0.1421720
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                 0.0135451   -0.0104130    0.0375033
6 months    ki1101329-Keneba           GAMBIA                         1                    NA                -0.0071987   -0.0430722    0.0286748
6 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                -0.0072631   -0.1024955    0.0879692
6 months    ki1114097-CMIN             BANGLADESH                     1                    NA                -0.0060397   -0.0699742    0.0578949
9 months    ki0047075b-MAL-ED          PERU                           1                    NA                -0.0465756   -0.1732077    0.0800565
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.0890000   -0.2200169    0.0420169
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.0932203   -0.2745090    0.0880683
9 months    ki1017093b-PROVIDE         BANGLADESH                     1                    NA                 0.0088576   -0.1070143    0.1247295
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.0470175   -0.0783275   -0.0157076
9 months    ki1101329-Keneba           GAMBIA                         1                    NA                -0.0541995   -0.0880695   -0.0203295
9 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                -0.0567416   -0.1921623    0.0786791
9 months    ki1114097-CMIN             BANGLADESH                     1                    NA                -0.0704205   -0.1366087   -0.0042324
9 months    ki1114097-CMIN             PERU                           1                    NA                -0.2371291   -0.3653482   -0.1089101


### Parameter: PAF


agecat      studyid                    country                        intervention_level   baseline_level      estimate     ci_lower     ci_upper
----------  -------------------------  -----------------------------  -------------------  ---------------  -----------  -----------  -----------
12 months   ki0047075b-MAL-ED          PERU                           1                    NA                 0.2606061   -0.3695278    0.6008088
12 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.4309764   -0.9981174   -0.0248114
12 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.3374690   -0.6883063   -0.0595372
12 months   ki1017093b-PROVIDE         BANGLADESH                     1                    NA                -0.5352349   -0.7879571   -0.3182342
12 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.4891692   -0.7618180   -0.2587139
12 months   ki1101329-Keneba           GAMBIA                         1                    NA                -0.5467113   -0.7620841   -0.3576627
12 months   ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                -0.3930921   -0.7378435   -0.1167321
12 months   ki1114097-CMIN             BANGLADESH                     1                    NA                -0.2307692   -0.3651429   -0.1096222
12 months   ki1114097-CMIN             PERU                           1                    NA                -1.7040077   -2.6263100   -1.0162804
18 months   ki0047075b-MAL-ED          PERU                           1                    NA                -0.1870265   -0.5293467    0.0786707
18 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.5853659   -1.2540721   -0.1150419
18 months   ki1017093b-PROVIDE         BANGLADESH                     1                    NA                -0.4091648   -0.6198535   -0.2258796
18 months   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.3631496   -0.6097296   -0.1543410
18 months   ki1101329-Keneba           GAMBIA                         1                    NA                -0.4481690   -0.6317034   -0.2852786
18 months   ki1114097-CMIN             BANGLADESH                     1                    NA                -0.1172210   -0.2023735   -0.0380990
3 months    ki0047075b-MAL-ED          PERU                           1                    NA                -0.5666667   -1.7354880    0.1027398
3 months    ki1017093b-PROVIDE         BANGLADESH                     1                    NA                 0.2170351   -0.0374059    0.4090701
3 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                 0.1118138   -0.1765327    0.3294919
3 months    ki1101329-Keneba           GAMBIA                         1                    NA                 0.0162545   -0.3846753    0.3010959
3 months    ki1114097-CMIN             BANGLADESH                     1                    NA                 0.2253873   -0.0215400    0.4126272
3 months    ki1114097-CMIN             PERU                           1                    NA                -1.0272919   -1.8353929   -0.4495037
6 months    ki0047075b-MAL-ED          PERU                           1                    NA                -0.2322515   -1.0707810    0.2667289
6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.1656347   -0.9634044    0.3079856
6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                 0.0081967   -0.7370565    0.4337123
6 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                 0.1143210   -0.1123641    0.2948106
6 months    ki1101329-Keneba           GAMBIA                         1                    NA                -0.0626118   -0.4250283    0.2076341
6 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                -0.0241758   -0.3956903    0.2484464
6 months    ki1114097-CMIN             BANGLADESH                     1                    NA                -0.0160386   -0.2008355    0.1403198
9 months    ki0047075b-MAL-ED          PERU                           1                    NA                -0.1771284   -0.7718179    0.2179606
9 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    NA                -0.3771186   -1.0594285    0.0791349
9 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.2291667   -0.7677304    0.1453161
9 months    ki1017093b-PROVIDE         BANGLADESH                     1                    NA                 0.0351351   -0.5535584    0.4007536
9 months    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                    NA                -0.3383218   -0.5812249   -0.1327327
9 months    ki1101329-Keneba           GAMBIA                         1                    NA                -0.3755252   -0.6249241   -0.1644049
9 months    ki1112895-Guatemala BSC    GUATEMALA                      1                    NA                -0.1442857   -0.5467295    0.1534461
9 months    ki1114097-CMIN             BANGLADESH                     1                    NA                -0.1590982   -0.3203142   -0.0175674
9 months    ki1114097-CMIN             PERU                           1                    NA                -1.7199367   -2.8164371   -0.9384718