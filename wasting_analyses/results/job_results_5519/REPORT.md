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

**Intervention Variable:** nrooms

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat        studyid                    country                        nrooms    wast_rec90d   n_cell       n
------------  -------------------------  -----------------------------  -------  ------------  -------  ------
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                   0       32     121
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                   1       61     121
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     2                   0        7     121
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     2                   1        9     121
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     3                   0        2     121
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     3                   1        6     121
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     4+                  0        3     121
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     4+                  1        1     121
0-24 months   ki0047075b-MAL-ED          BRAZIL                         1                   0        0      23
0-24 months   ki0047075b-MAL-ED          BRAZIL                         1                   1        0      23
0-24 months   ki0047075b-MAL-ED          BRAZIL                         2                   0        0      23
0-24 months   ki0047075b-MAL-ED          BRAZIL                         2                   1        2      23
0-24 months   ki0047075b-MAL-ED          BRAZIL                         3                   0        1      23
0-24 months   ki0047075b-MAL-ED          BRAZIL                         3                   1        3      23
0-24 months   ki0047075b-MAL-ED          BRAZIL                         4+                  0        5      23
0-24 months   ki0047075b-MAL-ED          BRAZIL                         4+                  1       12      23
0-24 months   ki0047075b-MAL-ED          INDIA                          1                   0       27     173
0-24 months   ki0047075b-MAL-ED          INDIA                          1                   1       38     173
0-24 months   ki0047075b-MAL-ED          INDIA                          2                   0       23     173
0-24 months   ki0047075b-MAL-ED          INDIA                          2                   1       41     173
0-24 months   ki0047075b-MAL-ED          INDIA                          3                   0       14     173
0-24 months   ki0047075b-MAL-ED          INDIA                          3                   1       18     173
0-24 months   ki0047075b-MAL-ED          INDIA                          4+                  0        3     173
0-24 months   ki0047075b-MAL-ED          INDIA                          4+                  1        9     173
0-24 months   ki0047075b-MAL-ED          NEPAL                          1                   0        4      92
0-24 months   ki0047075b-MAL-ED          NEPAL                          1                   1       23      92
0-24 months   ki0047075b-MAL-ED          NEPAL                          2                   0        1      92
0-24 months   ki0047075b-MAL-ED          NEPAL                          2                   1        5      92
0-24 months   ki0047075b-MAL-ED          NEPAL                          3                   0        0      92
0-24 months   ki0047075b-MAL-ED          NEPAL                          3                   1        6      92
0-24 months   ki0047075b-MAL-ED          NEPAL                          4+                  0       14      92
0-24 months   ki0047075b-MAL-ED          NEPAL                          4+                  1       39      92
0-24 months   ki0047075b-MAL-ED          PERU                           1                   0        1      33
0-24 months   ki0047075b-MAL-ED          PERU                           1                   1        2      33
0-24 months   ki0047075b-MAL-ED          PERU                           2                   0        0      33
0-24 months   ki0047075b-MAL-ED          PERU                           2                   1        3      33
0-24 months   ki0047075b-MAL-ED          PERU                           3                   0        1      33
0-24 months   ki0047075b-MAL-ED          PERU                           3                   1        8      33
0-24 months   ki0047075b-MAL-ED          PERU                           4+                  0        4      33
0-24 months   ki0047075b-MAL-ED          PERU                           4+                  1       14      33
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0        0      77
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1        5      77
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                   0        0      77
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                   1        3      77
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                   0        0      77
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                   1        8      77
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4+                  0       12      77
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4+                  1       49      77
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        0      45
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        1      45
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   0        2      45
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   1       16      45
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   0        5      45
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   1        7      45
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4+                  0        1      45
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4+                  1       13      45
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                   0       75     326
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                   1      126     326
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                   0       32     326
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                   1       54     326
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                   0       11     326
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                   1       22     326
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          4+                  0        2     326
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          4+                  1        4     326
0-24 months   ki1000108-IRC              INDIA                          1                   0       66     394
0-24 months   ki1000108-IRC              INDIA                          1                   1       96     394
0-24 months   ki1000108-IRC              INDIA                          2                   0       70     394
0-24 months   ki1000108-IRC              INDIA                          2                   1      110     394
0-24 months   ki1000108-IRC              INDIA                          3                   0       14     394
0-24 months   ki1000108-IRC              INDIA                          3                   1       18     394
0-24 months   ki1000108-IRC              INDIA                          4+                  0       11     394
0-24 months   ki1000108-IRC              INDIA                          4+                  1        9     394
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                   0      101     307
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                   1      121     307
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     2                   0       11     307
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     2                   1       29     307
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     3                   0       12     307
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     3                   1       20     307
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     4+                  0        4     307
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     4+                  1        9     307
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     1                   0       68     311
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     1                   1       95     311
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     2                   0       26     311
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     2                   1       48     311
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     3                   0       12     311
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     3                   1       27     311
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     4+                  0       11     311
0-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     4+                  1       24     311
0-24 months   ki1113344-GMS-Nepal        NEPAL                          1                   0       34    1122
0-24 months   ki1113344-GMS-Nepal        NEPAL                          1                   1       56    1122
0-24 months   ki1113344-GMS-Nepal        NEPAL                          2                   0      116    1122
0-24 months   ki1113344-GMS-Nepal        NEPAL                          2                   1       98    1122
0-24 months   ki1113344-GMS-Nepal        NEPAL                          3                   0      114    1122
0-24 months   ki1113344-GMS-Nepal        NEPAL                          3                   1      164    1122
0-24 months   ki1113344-GMS-Nepal        NEPAL                          4+                  0      272    1122
0-24 months   ki1113344-GMS-Nepal        NEPAL                          4+                  1      268    1122
0-24 months   ki1114097-CONTENT          PERU                           1                   0        0       9
0-24 months   ki1114097-CONTENT          PERU                           1                   1        2       9
0-24 months   ki1114097-CONTENT          PERU                           2                   0        1       9
0-24 months   ki1114097-CONTENT          PERU                           2                   1        2       9
0-24 months   ki1114097-CONTENT          PERU                           3                   0        0       9
0-24 months   ki1114097-CONTENT          PERU                           3                   1        1       9
0-24 months   ki1114097-CONTENT          PERU                           4+                  0        1       9
0-24 months   ki1114097-CONTENT          PERU                           4+                  1        2       9
0-24 months   ki1135781-COHORTS          INDIA                          1                   0     1079    1959
0-24 months   ki1135781-COHORTS          INDIA                          1                   1      319    1959
0-24 months   ki1135781-COHORTS          INDIA                          2                   0      373    1959
0-24 months   ki1135781-COHORTS          INDIA                          2                   1      125    1959
0-24 months   ki1135781-COHORTS          INDIA                          3                   0       34    1959
0-24 months   ki1135781-COHORTS          INDIA                          3                   1       12    1959
0-24 months   ki1135781-COHORTS          INDIA                          4+                  0       13    1959
0-24 months   ki1135781-COHORTS          INDIA                          4+                  1        4    1959
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     1                   0     5322   15122
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     1                   1     3716   15122
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     2                   0     2363   15122
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     2                   1     1796   15122
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     3                   0      779   15122
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     3                   1      620   15122
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     4+                  0      264   15122
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     4+                  1      262   15122
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                   0     1864    4045
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                   1      636    4045
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     2                   0      743    4045
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     2                   1      248    4045
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     3                   0      269    4045
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     3                   1      107    4045
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     4+                  0      112    4045
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     4+                  1       66    4045
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     1                   0        8      59
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     1                   1       35      59
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     2                   0        2      59
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     2                   1        5      59
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     3                   0        1      59
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     3                   1        6      59
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     4+                  0        1      59
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     4+                  1        1      59
0-6 months    ki0047075b-MAL-ED          BRAZIL                         1                   0        0      14
0-6 months    ki0047075b-MAL-ED          BRAZIL                         1                   1        0      14
0-6 months    ki0047075b-MAL-ED          BRAZIL                         2                   0        0      14
0-6 months    ki0047075b-MAL-ED          BRAZIL                         2                   1        2      14
0-6 months    ki0047075b-MAL-ED          BRAZIL                         3                   0        0      14
0-6 months    ki0047075b-MAL-ED          BRAZIL                         3                   1        3      14
0-6 months    ki0047075b-MAL-ED          BRAZIL                         4+                  0        1      14
0-6 months    ki0047075b-MAL-ED          BRAZIL                         4+                  1        8      14
0-6 months    ki0047075b-MAL-ED          INDIA                          1                   0        6      78
0-6 months    ki0047075b-MAL-ED          INDIA                          1                   1       23      78
0-6 months    ki0047075b-MAL-ED          INDIA                          2                   0        5      78
0-6 months    ki0047075b-MAL-ED          INDIA                          2                   1       19      78
0-6 months    ki0047075b-MAL-ED          INDIA                          3                   0        9      78
0-6 months    ki0047075b-MAL-ED          INDIA                          3                   1       11      78
0-6 months    ki0047075b-MAL-ED          INDIA                          4+                  0        2      78
0-6 months    ki0047075b-MAL-ED          INDIA                          4+                  1        3      78
0-6 months    ki0047075b-MAL-ED          NEPAL                          1                   0        2      42
0-6 months    ki0047075b-MAL-ED          NEPAL                          1                   1        9      42
0-6 months    ki0047075b-MAL-ED          NEPAL                          2                   0        1      42
0-6 months    ki0047075b-MAL-ED          NEPAL                          2                   1        1      42
0-6 months    ki0047075b-MAL-ED          NEPAL                          3                   0        0      42
0-6 months    ki0047075b-MAL-ED          NEPAL                          3                   1        4      42
0-6 months    ki0047075b-MAL-ED          NEPAL                          4+                  0        5      42
0-6 months    ki0047075b-MAL-ED          NEPAL                          4+                  1       20      42
0-6 months    ki0047075b-MAL-ED          PERU                           1                   0        0      10
0-6 months    ki0047075b-MAL-ED          PERU                           1                   1        1      10
0-6 months    ki0047075b-MAL-ED          PERU                           2                   0        0      10
0-6 months    ki0047075b-MAL-ED          PERU                           2                   1        1      10
0-6 months    ki0047075b-MAL-ED          PERU                           3                   0        0      10
0-6 months    ki0047075b-MAL-ED          PERU                           3                   1        1      10
0-6 months    ki0047075b-MAL-ED          PERU                           4+                  0        0      10
0-6 months    ki0047075b-MAL-ED          PERU                           4+                  1        7      10
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0        0      27
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1        2      27
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                   0        0      27
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   2                   1        1      27
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                   0        0      27
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   3                   1        4      27
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4+                  0        3      27
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   4+                  1       17      27
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        0      12
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        0      12
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   0        0      12
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   1        5      12
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   0        1      12
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   1        2      12
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4+                  0        0      12
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4+                  1        4      12
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                   0       38     203
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                   1       77     203
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                   0       21     203
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          2                   1       37     203
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                   0        5     203
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          3                   1       20     203
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          4+                  0        2     203
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          4+                  1        3     203
0-6 months    ki1000108-IRC              INDIA                          1                   0       42     239
0-6 months    ki1000108-IRC              INDIA                          1                   1       66     239
0-6 months    ki1000108-IRC              INDIA                          2                   0       30     239
0-6 months    ki1000108-IRC              INDIA                          2                   1       70     239
0-6 months    ki1000108-IRC              INDIA                          3                   0       10     239
0-6 months    ki1000108-IRC              INDIA                          3                   1       10     239
0-6 months    ki1000108-IRC              INDIA                          4+                  0        4     239
0-6 months    ki1000108-IRC              INDIA                          4+                  1        7     239
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     1                   0       31     184
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     1                   1      101     184
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     2                   0        4     184
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     2                   1       22     184
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     3                   0        3     184
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     3                   1       15     184
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     4+                  0        1     184
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     4+                  1        7     184
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     1                   0       12     198
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     1                   1       85     198
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     2                   0        4     198
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     2                   1       43     198
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     3                   0        2     198
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     3                   1       26     198
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     4+                  0        3     198
0-6 months    ki1017093c-NIH-Crypto      BANGLADESH                     4+                  1       23     198
0-6 months    ki1113344-GMS-Nepal        NEPAL                          1                   0       14     360
0-6 months    ki1113344-GMS-Nepal        NEPAL                          1                   1       10     360
0-6 months    ki1113344-GMS-Nepal        NEPAL                          2                   0       36     360
0-6 months    ki1113344-GMS-Nepal        NEPAL                          2                   1       32     360
0-6 months    ki1113344-GMS-Nepal        NEPAL                          3                   0       22     360
0-6 months    ki1113344-GMS-Nepal        NEPAL                          3                   1       70     360
0-6 months    ki1113344-GMS-Nepal        NEPAL                          4+                  0       78     360
0-6 months    ki1113344-GMS-Nepal        NEPAL                          4+                  1       98     360
0-6 months    ki1114097-CONTENT          PERU                           1                   0        0       4
0-6 months    ki1114097-CONTENT          PERU                           1                   1        1       4
0-6 months    ki1114097-CONTENT          PERU                           2                   0        0       4
0-6 months    ki1114097-CONTENT          PERU                           2                   1        0       4
0-6 months    ki1114097-CONTENT          PERU                           3                   0        0       4
0-6 months    ki1114097-CONTENT          PERU                           3                   1        1       4
0-6 months    ki1114097-CONTENT          PERU                           4+                  0        0       4
0-6 months    ki1114097-CONTENT          PERU                           4+                  1        2       4
0-6 months    ki1135781-COHORTS          INDIA                          1                   0      568    1287
0-6 months    ki1135781-COHORTS          INDIA                          1                   1      319    1287
0-6 months    ki1135781-COHORTS          INDIA                          2                   0      227    1287
0-6 months    ki1135781-COHORTS          INDIA                          2                   1      125    1287
0-6 months    ki1135781-COHORTS          INDIA                          3                   0       22    1287
0-6 months    ki1135781-COHORTS          INDIA                          3                   1       12    1287
0-6 months    ki1135781-COHORTS          INDIA                          4+                  0       10    1287
0-6 months    ki1135781-COHORTS          INDIA                          4+                  1        4    1287
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     1                   0     1968    9466
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     1                   1     3716    9466
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     2                   0      748    9466
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     2                   1     1796    9466
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     3                   0      256    9466
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     3                   1      620    9466
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     4+                  0      100    9466
0-6 months    kiGH5241-JiVitA-3          BANGLADESH                     4+                  1      262    9466
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     1                   0      288    1096
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     1                   1      354    1096
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     2                   0      122    1096
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     2                   1      142    1096
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     3                   0       52    1096
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     3                   1       74    1096
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     4+                  0       22    1096
0-6 months    kiGH5241-JiVitA-4          BANGLADESH                     4+                  1       42    1096
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                   0       24      62
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                   1       26      62
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     2                   0        5      62
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     2                   1        4      62
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     3                   0        1      62
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     3                   1        0      62
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     4+                  0        2      62
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     4+                  1        0      62
6-24 months   ki0047075b-MAL-ED          BRAZIL                         1                   0        0       9
6-24 months   ki0047075b-MAL-ED          BRAZIL                         1                   1        0       9
6-24 months   ki0047075b-MAL-ED          BRAZIL                         2                   0        0       9
6-24 months   ki0047075b-MAL-ED          BRAZIL                         2                   1        0       9
6-24 months   ki0047075b-MAL-ED          BRAZIL                         3                   0        1       9
6-24 months   ki0047075b-MAL-ED          BRAZIL                         3                   1        0       9
6-24 months   ki0047075b-MAL-ED          BRAZIL                         4+                  0        4       9
6-24 months   ki0047075b-MAL-ED          BRAZIL                         4+                  1        4       9
6-24 months   ki0047075b-MAL-ED          INDIA                          1                   0       21      95
6-24 months   ki0047075b-MAL-ED          INDIA                          1                   1       15      95
6-24 months   ki0047075b-MAL-ED          INDIA                          2                   0       18      95
6-24 months   ki0047075b-MAL-ED          INDIA                          2                   1       22      95
6-24 months   ki0047075b-MAL-ED          INDIA                          3                   0        5      95
6-24 months   ki0047075b-MAL-ED          INDIA                          3                   1        7      95
6-24 months   ki0047075b-MAL-ED          INDIA                          4+                  0        1      95
6-24 months   ki0047075b-MAL-ED          INDIA                          4+                  1        6      95
6-24 months   ki0047075b-MAL-ED          NEPAL                          1                   0        2      50
6-24 months   ki0047075b-MAL-ED          NEPAL                          1                   1       14      50
6-24 months   ki0047075b-MAL-ED          NEPAL                          2                   0        0      50
6-24 months   ki0047075b-MAL-ED          NEPAL                          2                   1        4      50
6-24 months   ki0047075b-MAL-ED          NEPAL                          3                   0        0      50
6-24 months   ki0047075b-MAL-ED          NEPAL                          3                   1        2      50
6-24 months   ki0047075b-MAL-ED          NEPAL                          4+                  0        9      50
6-24 months   ki0047075b-MAL-ED          NEPAL                          4+                  1       19      50
6-24 months   ki0047075b-MAL-ED          PERU                           1                   0        1      23
6-24 months   ki0047075b-MAL-ED          PERU                           1                   1        1      23
6-24 months   ki0047075b-MAL-ED          PERU                           2                   0        0      23
6-24 months   ki0047075b-MAL-ED          PERU                           2                   1        2      23
6-24 months   ki0047075b-MAL-ED          PERU                           3                   0        1      23
6-24 months   ki0047075b-MAL-ED          PERU                           3                   1        7      23
6-24 months   ki0047075b-MAL-ED          PERU                           4+                  0        4      23
6-24 months   ki0047075b-MAL-ED          PERU                           4+                  1        7      23
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0        0      50
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1        3      50
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                   0        0      50
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   2                   1        2      50
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                   0        0      50
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   3                   1        4      50
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4+                  0        9      50
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   4+                  1       32      50
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        0      33
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        1      33
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   0        2      33
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   1       11      33
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   0        4      33
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   1        5      33
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4+                  0        1      33
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4+                  1        9      33
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                   0       37     123
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                   1       49     123
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                   0       11     123
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          2                   1       17     123
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                   0        6     123
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          3                   1        2     123
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          4+                  0        0     123
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          4+                  1        1     123
6-24 months   ki1000108-IRC              INDIA                          1                   0       24     155
6-24 months   ki1000108-IRC              INDIA                          1                   1       30     155
6-24 months   ki1000108-IRC              INDIA                          2                   0       40     155
6-24 months   ki1000108-IRC              INDIA                          2                   1       40     155
6-24 months   ki1000108-IRC              INDIA                          3                   0        4     155
6-24 months   ki1000108-IRC              INDIA                          3                   1        8     155
6-24 months   ki1000108-IRC              INDIA                          4+                  0        7     155
6-24 months   ki1000108-IRC              INDIA                          4+                  1        2     155
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                   0       70     123
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                   1       20     123
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     2                   0        7     123
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     2                   1        7     123
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     3                   0        9     123
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     3                   1        5     123
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     4+                  0        3     123
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     4+                  1        2     123
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     1                   0       56     113
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     1                   1       10     113
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     2                   0       22     113
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     2                   1        5     113
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     3                   0       10     113
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     3                   1        1     113
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     4+                  0        8     113
6-24 months   ki1017093c-NIH-Crypto      BANGLADESH                     4+                  1        1     113
6-24 months   ki1113344-GMS-Nepal        NEPAL                          1                   0       20     762
6-24 months   ki1113344-GMS-Nepal        NEPAL                          1                   1       46     762
6-24 months   ki1113344-GMS-Nepal        NEPAL                          2                   0       80     762
6-24 months   ki1113344-GMS-Nepal        NEPAL                          2                   1       66     762
6-24 months   ki1113344-GMS-Nepal        NEPAL                          3                   0       92     762
6-24 months   ki1113344-GMS-Nepal        NEPAL                          3                   1       94     762
6-24 months   ki1113344-GMS-Nepal        NEPAL                          4+                  0      194     762
6-24 months   ki1113344-GMS-Nepal        NEPAL                          4+                  1      170     762
6-24 months   ki1114097-CONTENT          PERU                           1                   0        0       5
6-24 months   ki1114097-CONTENT          PERU                           1                   1        1       5
6-24 months   ki1114097-CONTENT          PERU                           2                   0        1       5
6-24 months   ki1114097-CONTENT          PERU                           2                   1        2       5
6-24 months   ki1114097-CONTENT          PERU                           3                   0        0       5
6-24 months   ki1114097-CONTENT          PERU                           3                   1        0       5
6-24 months   ki1114097-CONTENT          PERU                           4+                  0        1       5
6-24 months   ki1114097-CONTENT          PERU                           4+                  1        0       5
6-24 months   ki1135781-COHORTS          INDIA                          1                   0      511     672
6-24 months   ki1135781-COHORTS          INDIA                          1                   1        0     672
6-24 months   ki1135781-COHORTS          INDIA                          2                   0      146     672
6-24 months   ki1135781-COHORTS          INDIA                          2                   1        0     672
6-24 months   ki1135781-COHORTS          INDIA                          3                   0       12     672
6-24 months   ki1135781-COHORTS          INDIA                          3                   1        0     672
6-24 months   ki1135781-COHORTS          INDIA                          4+                  0        3     672
6-24 months   ki1135781-COHORTS          INDIA                          4+                  1        0     672
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     1                   0     3354    5656
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     1                   1        0    5656
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     2                   0     1615    5656
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     2                   1        0    5656
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     3                   0      523    5656
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     3                   1        0    5656
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     4+                  0      164    5656
6-24 months   kiGH5241-JiVitA-3          BANGLADESH                     4+                  1        0    5656
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                   0     1576    2949
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                   1      282    2949
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     2                   0      621    2949
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     2                   1      106    2949
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     3                   0      217    2949
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     3                   1       33    2949
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     4+                  0       90    2949
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     4+                  1       24    2949


The following strata were considered:

* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-24 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-24 months, studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-24 months, studyid: ki1135781-COHORTS, country: INDIA
* agecat: 0-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 0-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-6 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-6 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 0-6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-6 months, studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-6 months, studyid: ki1135781-COHORTS, country: INDIA
* agecat: 0-6 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 0-6 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6-24 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 6-24 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: ki1114097-CONTENT, country: PERU
* agecat: 6-24 months, studyid: ki1135781-COHORTS, country: INDIA
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-24 months, studyid: ki1135781-COHORTS, country: INDIA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-6 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-6 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 0-6 months, studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-6 months, studyid: ki1135781-COHORTS, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6-24 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 6-24 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1114097-CONTENT, country: PERU
* agecat: 6-24 months, studyid: ki1135781-COHORTS, country: INDIA
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness







# Results Detail

## Results Plots
![](/tmp/34e3c5d2-00fe-43a8-bb4f-d3e37098847c/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/34e3c5d2-00fe-43a8-bb4f-d3e37098847c/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/34e3c5d2-00fe-43a8-bb4f-d3e37098847c/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/34e3c5d2-00fe-43a8-bb4f-d3e37098847c/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat        studyid                 country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  ----------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki1000108-IRC           INDIA        1                    NA                0.5925926   0.5081592   0.6770260
0-24 months   ki1000108-IRC           INDIA        2                    NA                0.6111111   0.5401543   0.6820679
0-24 months   ki1000108-IRC           INDIA        3                    NA                0.5625000   0.3398407   0.7851593
0-24 months   ki1000108-IRC           INDIA        4+                   NA                0.4500000   0.2471890   0.6528110
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   1                    NA                0.5828221   0.5078896   0.6577545
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   2                    NA                0.6486486   0.5383045   0.7589928
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   3                    NA                0.6923077   0.5454181   0.8391972
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   4+                   NA                0.6857143   0.5210625   0.8503660
0-24 months   ki1113344-GMS-Nepal     NEPAL        1                    NA                0.6222222   0.4772128   0.7672316
0-24 months   ki1113344-GMS-Nepal     NEPAL        2                    NA                0.4579439   0.3557393   0.5601485
0-24 months   ki1113344-GMS-Nepal     NEPAL        3                    NA                0.5899281   0.4961167   0.6837394
0-24 months   ki1113344-GMS-Nepal     NEPAL        4+                   NA                0.4962963   0.4328205   0.5597721
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   1                    NA                0.4111529   0.3967984   0.4255075
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   2                    NA                0.4318346   0.4106720   0.4529972
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   3                    NA                0.4431737   0.4061487   0.4801987
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   4+                   NA                0.4980989   0.4376859   0.5585118
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    NA                0.2544000   0.2306160   0.2781840
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   2                    NA                0.2502523   0.2112209   0.2892837
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   3                    NA                0.2845745   0.2152607   0.3538883
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   4+                   NA                0.3707865   0.2617648   0.4798082
0-6 months    ki1113344-GMS-Nepal     NEPAL        1                    NA                0.4166667   0.1509081   0.6824252
0-6 months    ki1113344-GMS-Nepal     NEPAL        2                    NA                0.4705882   0.3004500   0.6407264
0-6 months    ki1113344-GMS-Nepal     NEPAL        3                    NA                0.7608696   0.6358674   0.8858717
0-6 months    ki1113344-GMS-Nepal     NEPAL        4+                   NA                0.5568182   0.4527929   0.6608435
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   1                    NA                0.6537650   0.6362711   0.6712588
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   2                    NA                0.7059748   0.6809241   0.7310256
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   3                    NA                0.7077626   0.6652765   0.7502486
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   4+                   NA                0.7237569   0.6585820   0.7889318
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   1                    NA                0.5514019   0.4969447   0.6058590
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   2                    NA                0.5378788   0.4527497   0.6230079
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   3                    NA                0.5873016   0.4656210   0.7089822
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   4+                   NA                0.6562500   0.4915378   0.8209622
6-24 months   ki1113344-GMS-Nepal     NEPAL        1                    NA                0.6969697   0.5197034   0.8742360
6-24 months   ki1113344-GMS-Nepal     NEPAL        2                    NA                0.4520548   0.3251598   0.5789498
6-24 months   ki1113344-GMS-Nepal     NEPAL        3                    NA                0.5053763   0.3899301   0.6208226
6-24 months   ki1113344-GMS-Nepal     NEPAL        4+                   NA                0.4670330   0.3911401   0.5429259
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    NA                0.1517761   0.1303785   0.1731737
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   2                    NA                0.1458047   0.1093596   0.1822498
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   3                    NA                0.1320000   0.0691088   0.1948912
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   4+                   NA                0.2105263   0.0986019   0.3224507


### Parameter: E(Y)


agecat        studyid                 country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  ----------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki1000108-IRC           INDIA        NA                   NA                0.5913706   0.5391835   0.6435576
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   NA                   NA                0.6237942   0.5698223   0.6777662
0-24 months   ki1113344-GMS-Nepal     NEPAL        NA                   NA                0.5222816   0.4773852   0.5671781
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   NA                   NA                0.4228277   0.4116994   0.4339560
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   NA                   NA                0.2613103   0.2419607   0.2806599
0-6 months    ki1113344-GMS-Nepal     NEPAL        NA                   NA                0.5833333   0.5108676   0.6557991
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   NA                   NA                0.6754701   0.6621313   0.6888089
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   NA                   NA                0.5583942   0.5167799   0.6000084
6-24 months   ki1113344-GMS-Nepal     NEPAL        NA                   NA                0.4934383   0.4388573   0.5480193
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   NA                   NA                0.1508986   0.1332882   0.1685090


### Parameter: RR


agecat        studyid                 country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  ----------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki1000108-IRC           INDIA        1                    1                 1.0000000   1.0000000   1.0000000
0-24 months   ki1000108-IRC           INDIA        2                    1                 1.0312500   0.8580769   1.2393722
0-24 months   ki1000108-IRC           INDIA        3                    1                 0.9492188   0.6232698   1.4456279
0-24 months   ki1000108-IRC           INDIA        4+                   1                 0.7593750   0.4733474   1.2182394
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   1                    1                 1.0000000   1.0000000   1.0000000
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   2                    1                 1.1129445   0.8989008   1.3779558
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   3                    1                 1.1878543   0.9265560   1.5228412
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   4+                   1                 1.1765414   0.8960725   1.5447964
0-24 months   ki1113344-GMS-Nepal     NEPAL        1                    1                 1.0000000   1.0000000   1.0000000
0-24 months   ki1113344-GMS-Nepal     NEPAL        2                    1                 0.7359813   0.5329026   1.0164493
0-24 months   ki1113344-GMS-Nepal     NEPAL        3                    1                 0.9480987   0.7149671   1.2572481
0-24 months   ki1113344-GMS-Nepal     NEPAL        4+                   1                 0.7976190   0.6114204   1.0405216
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   1                    1                 1.0000000   1.0000000   1.0000000
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   2                    1                 1.0503016   0.9889678   1.1154392
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   3                    1                 1.0778805   0.9845699   1.1800344
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   4+                   1                 1.2114686   1.0678224   1.3744385
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    1                 1.0000000   1.0000000   1.0000000
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   2                    1                 0.9836960   0.8201119   1.1799096
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   3                    1                 1.1186103   0.8617552   1.4520238
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   4+                   1                 1.4574942   1.0705777   1.9842457
0-6 months    ki1113344-GMS-Nepal     NEPAL        1                    1                 1.0000000   1.0000000   1.0000000
0-6 months    ki1113344-GMS-Nepal     NEPAL        2                    1                 1.1294118   0.5425546   2.3510464
0-6 months    ki1113344-GMS-Nepal     NEPAL        3                    1                 1.8260870   0.9451006   3.5282949
0-6 months    ki1113344-GMS-Nepal     NEPAL        4+                   1                 1.3363636   0.6875221   2.5975422
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   1                    1                 1.0000000   1.0000000   1.0000000
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   2                    1                 1.0798603   1.0329195   1.1289344
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   3                    1                 1.0825948   1.0137316   1.1561360
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   4+                   1                 1.1070598   1.0077955   1.2161013
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   1                    1                 1.0000000   1.0000000   1.0000000
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   2                    1                 0.9754751   0.8094622   1.1755356
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   3                    1                 1.0651063   0.8466683   1.3399005
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   4+                   1                 1.1901483   0.9087877   1.5586181
6-24 months   ki1113344-GMS-Nepal     NEPAL        1                    1                 1.0000000   1.0000000   1.0000000
6-24 months   ki1113344-GMS-Nepal     NEPAL        2                    1                 0.6486004   0.4440138   0.9474536
6-24 months   ki1113344-GMS-Nepal     NEPAL        3                    1                 0.7251052   0.5151021   1.0207249
6-24 months   ki1113344-GMS-Nepal     NEPAL        4+                   1                 0.6700908   0.4954356   0.9063169
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    1                 1.0000000   1.0000000   1.0000000
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   2                    1                 0.9606563   0.7209765   1.2800148
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   3                    1                 0.8697021   0.5291699   1.4293742
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   4+                   1                 1.3870847   0.8002791   2.4041662


### Parameter: PAR


agecat        studyid                 country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  ----------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki1000108-IRC           INDIA        1                    NA                -0.0012220   -0.0643943    0.0619503
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   1                    NA                 0.0409721   -0.0113008    0.0932450
0-24 months   ki1113344-GMS-Nepal     NEPAL        1                    NA                -0.0999406   -0.2405496    0.0406685
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   1                    NA                 0.0116748    0.0025342    0.0208153
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    NA                 0.0069103   -0.0085964    0.0224169
0-6 months    ki1113344-GMS-Nepal     NEPAL        1                    NA                 0.1666667   -0.0904389    0.4237722
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   1                    NA                 0.0217051    0.0109147    0.0324956
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   1                    NA                 0.0069923   -0.0279799    0.0419645
6-24 months   ki1113344-GMS-Nepal     NEPAL        1                    NA                -0.2035314   -0.3744911   -0.0325717
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    NA                -0.0008775   -0.0147036    0.0129486


### Parameter: PAF


agecat        studyid                 country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  ----------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki1000108-IRC           INDIA        1                    NA                -0.0020664   -0.1147791    0.0992501
0-24 months   ki1017093c-NIH-Crypto   BANGLADESH   1                    NA                 0.0656821   -0.0221660    0.1459803
0-24 months   ki1113344-GMS-Nepal     NEPAL        1                    NA                -0.1913538   -0.4952858    0.0508009
0-24 months   kiGH5241-JiVitA-3       BANGLADESH   1                    NA                 0.0276112    0.0057438    0.0489975
0-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    NA                 0.0264447   -0.0346067    0.0838934
0-6 months    ki1113344-GMS-Nepal     NEPAL        1                    NA                 0.2857143   -0.3252639    0.6150170
0-6 months    kiGH5241-JiVitA-3       BANGLADESH   1                    NA                 0.0321334    0.0159871    0.0480147
0-6 months    kiGH5241-JiVitA-4       BANGLADESH   1                    NA                 0.0125221   -0.0521476    0.0732170
6-24 months   ki1113344-GMS-Nepal     NEPAL        1                    NA                -0.4124758   -0.8113851   -0.1014157
6-24 months   kiGH5241-JiVitA-4       BANGLADESH   1                    NA                -0.0058151   -0.1018119    0.0818178