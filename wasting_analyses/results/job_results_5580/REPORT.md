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

**Intervention Variable:** predexfd6

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat        studyid                    country                        predexfd6    pers_wast   n_cell       n
------------  -------------------------  -----------------------------  ----------  ----------  -------  ------
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     0                    0      108     238
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     0                    1        5     238
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                    0      117     238
0-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                    1        8     238
0-24 months   ki0047075b-MAL-ED          BRAZIL                         0                    0      175     212
0-24 months   ki0047075b-MAL-ED          BRAZIL                         0                    1        1     212
0-24 months   ki0047075b-MAL-ED          BRAZIL                         1                    0       35     212
0-24 months   ki0047075b-MAL-ED          BRAZIL                         1                    1        1     212
0-24 months   ki0047075b-MAL-ED          INDIA                          0                    0      196     234
0-24 months   ki0047075b-MAL-ED          INDIA                          0                    1       19     234
0-24 months   ki0047075b-MAL-ED          INDIA                          1                    0       19     234
0-24 months   ki0047075b-MAL-ED          INDIA                          1                    1        0     234
0-24 months   ki0047075b-MAL-ED          NEPAL                          0                    0      203     235
0-24 months   ki0047075b-MAL-ED          NEPAL                          0                    1        3     235
0-24 months   ki0047075b-MAL-ED          NEPAL                          1                    0       29     235
0-24 months   ki0047075b-MAL-ED          NEPAL                          1                    1        0     235
0-24 months   ki0047075b-MAL-ED          PERU                           0                    0      156     270
0-24 months   ki0047075b-MAL-ED          PERU                           0                    1        0     270
0-24 months   ki0047075b-MAL-ED          PERU                           1                    0      113     270
0-24 months   ki0047075b-MAL-ED          PERU                           1                    1        1     270
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   0                    0      243     248
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   0                    1        2     248
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    0        3     248
0-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    1        0     248
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                    0      246     248
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                    1        0     248
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    0        2     248
0-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    1        0     248
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          0                    0        0      19
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          0                    1        0      19
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                    0       19      19
0-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                    1        0      19
0-24 months   ki1000108-IRC              INDIA                          0                    0       12      14
0-24 months   ki1000108-IRC              INDIA                          0                    1        2      14
0-24 months   ki1000108-IRC              INDIA                          1                    0        0      14
0-24 months   ki1000108-IRC              INDIA                          1                    1        0      14
0-24 months   ki1000109-EE               PAKISTAN                       0                    0      282     754
0-24 months   ki1000109-EE               PAKISTAN                       0                    1       30     754
0-24 months   ki1000109-EE               PAKISTAN                       1                    0      416     754
0-24 months   ki1000109-EE               PAKISTAN                       1                    1       26     754
0-24 months   ki1000304b-SAS-CompFeed    INDIA                          0                    0       16     413
0-24 months   ki1000304b-SAS-CompFeed    INDIA                          0                    1        2     413
0-24 months   ki1000304b-SAS-CompFeed    INDIA                          1                    0      355     413
0-24 months   ki1000304b-SAS-CompFeed    INDIA                          1                    1       40     413
0-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          0                    0      136     166
0-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          0                    1       30     166
0-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          1                    0        0     166
0-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          1                    1        0     166
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     0                    0      461     640
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     0                    1       13     640
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                    0      164     640
0-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                    1        2     640
0-24 months   ki1101329-Keneba           GAMBIA                         0                    0     1296    2120
0-24 months   ki1101329-Keneba           GAMBIA                         0                    1       84    2120
0-24 months   ki1101329-Keneba           GAMBIA                         1                    0      715    2120
0-24 months   ki1101329-Keneba           GAMBIA                         1                    1       25    2120
0-24 months   ki1113344-GMS-Nepal        NEPAL                          0                    0      242    1120
0-24 months   ki1113344-GMS-Nepal        NEPAL                          0                    1       46    1120
0-24 months   ki1113344-GMS-Nepal        NEPAL                          1                    0      714    1120
0-24 months   ki1113344-GMS-Nepal        NEPAL                          1                    1      118    1120
0-24 months   ki1148112-LCNI-5           MALAWI                         0                    0      195     240
0-24 months   ki1148112-LCNI-5           MALAWI                         0                    1        3     240
0-24 months   ki1148112-LCNI-5           MALAWI                         1                    0       42     240
0-24 months   ki1148112-LCNI-5           MALAWI                         1                    1        0     240
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     0                    0     5880   31350
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     0                    1      580   31350
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     1                    0    23674   31350
0-24 months   kiGH5241-JiVitA-3          BANGLADESH                     1                    1     1216   31350
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     0                    0     1772    9264
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     0                    1      204    9264
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                    0     6766    9264
0-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                    1      522    9264
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     0                    0      109     238
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     0                    1        4     238
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     1                    0      122     238
0-6 months    ki0047075b-MAL-ED          BANGLADESH                     1                    1        3     238
0-6 months    ki0047075b-MAL-ED          BRAZIL                         0                    0      176     212
0-6 months    ki0047075b-MAL-ED          BRAZIL                         0                    1        0     212
0-6 months    ki0047075b-MAL-ED          BRAZIL                         1                    0       35     212
0-6 months    ki0047075b-MAL-ED          BRAZIL                         1                    1        1     212
0-6 months    ki0047075b-MAL-ED          INDIA                          0                    0      197     233
0-6 months    ki0047075b-MAL-ED          INDIA                          0                    1       17     233
0-6 months    ki0047075b-MAL-ED          INDIA                          1                    0       18     233
0-6 months    ki0047075b-MAL-ED          INDIA                          1                    1        1     233
0-6 months    ki0047075b-MAL-ED          NEPAL                          0                    0      201     234
0-6 months    ki0047075b-MAL-ED          NEPAL                          0                    1        4     234
0-6 months    ki0047075b-MAL-ED          NEPAL                          1                    0       29     234
0-6 months    ki0047075b-MAL-ED          NEPAL                          1                    1        0     234
0-6 months    ki0047075b-MAL-ED          PERU                           0                    0      156     270
0-6 months    ki0047075b-MAL-ED          PERU                           0                    1        0     270
0-6 months    ki0047075b-MAL-ED          PERU                           1                    0      114     270
0-6 months    ki0047075b-MAL-ED          PERU                           1                    1        0     270
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   0                    0      241     246
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   0                    1        2     246
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    0        3     246
0-6 months    ki0047075b-MAL-ED          SOUTH AFRICA                   1                    1        0     246
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                    0      246     248
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                    1        0     248
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    0        2     248
0-6 months    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    1        0     248
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          0                    0        0      19
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          0                    1        0      19
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                    0       15      19
0-6 months    ki1000108-CMC-V-BCS-2002   INDIA                          1                    1        4      19
0-6 months    ki1000108-IRC              INDIA                          0                    0       11      14
0-6 months    ki1000108-IRC              INDIA                          0                    1        3      14
0-6 months    ki1000108-IRC              INDIA                          1                    0        0      14
0-6 months    ki1000108-IRC              INDIA                          1                    1        0      14
0-6 months    ki1000109-EE               PAKISTAN                       0                    0      280     732
0-6 months    ki1000109-EE               PAKISTAN                       0                    1       32     732
0-6 months    ki1000109-EE               PAKISTAN                       1                    0      398     732
0-6 months    ki1000109-EE               PAKISTAN                       1                    1       22     732
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     0                    0      459     637
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     0                    1       13     637
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     1                    0      164     637
0-6 months    ki1017093b-PROVIDE         BANGLADESH                     1                    1        1     637
0-6 months    ki1101329-Keneba           GAMBIA                         0                    0     1256    1918
0-6 months    ki1101329-Keneba           GAMBIA                         0                    1       37    1918
0-6 months    ki1101329-Keneba           GAMBIA                         1                    0      614    1918
0-6 months    ki1101329-Keneba           GAMBIA                         1                    1       11    1918
0-6 months    ki1113344-GMS-Nepal        NEPAL                          0                    0      234    1066
0-6 months    ki1113344-GMS-Nepal        NEPAL                          0                    1       44    1066
0-6 months    ki1113344-GMS-Nepal        NEPAL                          1                    0      706    1066
0-6 months    ki1113344-GMS-Nepal        NEPAL                          1                    1       82    1066
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     0                    0      101     228
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     0                    1        5     228
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                    0      110     228
6-24 months   ki0047075b-MAL-ED          BANGLADESH                     1                    1       12     228
6-24 months   ki0047075b-MAL-ED          BRAZIL                         0                    0      163     197
6-24 months   ki0047075b-MAL-ED          BRAZIL                         0                    1        1     197
6-24 months   ki0047075b-MAL-ED          BRAZIL                         1                    0       32     197
6-24 months   ki0047075b-MAL-ED          BRAZIL                         1                    1        1     197
6-24 months   ki0047075b-MAL-ED          INDIA                          0                    0      184     227
6-24 months   ki0047075b-MAL-ED          INDIA                          0                    1       26     227
6-24 months   ki0047075b-MAL-ED          INDIA                          1                    0       17     227
6-24 months   ki0047075b-MAL-ED          INDIA                          1                    1        0     227
6-24 months   ki0047075b-MAL-ED          NEPAL                          0                    0      200     230
6-24 months   ki0047075b-MAL-ED          NEPAL                          0                    1        2     230
6-24 months   ki0047075b-MAL-ED          NEPAL                          1                    0       28     230
6-24 months   ki0047075b-MAL-ED          NEPAL                          1                    1        0     230
6-24 months   ki0047075b-MAL-ED          PERU                           0                    0      138     248
6-24 months   ki0047075b-MAL-ED          PERU                           0                    1        1     248
6-24 months   ki0047075b-MAL-ED          PERU                           1                    0      108     248
6-24 months   ki0047075b-MAL-ED          PERU                           1                    1        1     248
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   0                    0      237     242
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   0                    1        2     242
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    0        3     242
6-24 months   ki0047075b-MAL-ED          SOUTH AFRICA                   1                    1        0     242
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                    0      233     235
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                    1        0     235
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    0        2     235
6-24 months   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                    1        0     235
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          0                    0        0      19
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          0                    1        0      19
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                    0       19      19
6-24 months   ki1000108-CMC-V-BCS-2002   INDIA                          1                    1        0      19
6-24 months   ki1000108-IRC              INDIA                          0                    0       12      14
6-24 months   ki1000108-IRC              INDIA                          0                    1        2      14
6-24 months   ki1000108-IRC              INDIA                          1                    0        0      14
6-24 months   ki1000108-IRC              INDIA                          1                    1        0      14
6-24 months   ki1000109-EE               PAKISTAN                       0                    0      272     736
6-24 months   ki1000109-EE               PAKISTAN                       0                    1       38     736
6-24 months   ki1000109-EE               PAKISTAN                       1                    0      378     736
6-24 months   ki1000109-EE               PAKISTAN                       1                    1       48     736
6-24 months   ki1000304b-SAS-CompFeed    INDIA                          0                    0       12     369
6-24 months   ki1000304b-SAS-CompFeed    INDIA                          0                    1        1     369
6-24 months   ki1000304b-SAS-CompFeed    INDIA                          1                    0      293     369
6-24 months   ki1000304b-SAS-CompFeed    INDIA                          1                    1       63     369
6-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          0                    0      130     153
6-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          0                    1       23     153
6-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          1                    0        0     153
6-24 months   ki1000304b-SAS-FoodSuppl   INDIA                          1                    1        0     153
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     0                    0      419     601
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     0                    1       32     601
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                    0      144     601
6-24 months   ki1017093b-PROVIDE         BANGLADESH                     1                    1        6     601
6-24 months   ki1101329-Keneba           GAMBIA                         0                    0     1166    1938
6-24 months   ki1101329-Keneba           GAMBIA                         0                    1      132    1938
6-24 months   ki1101329-Keneba           GAMBIA                         1                    0      598    1938
6-24 months   ki1101329-Keneba           GAMBIA                         1                    1       42    1938
6-24 months   ki1113344-GMS-Nepal        NEPAL                          0                    0      218    1094
6-24 months   ki1113344-GMS-Nepal        NEPAL                          0                    1       60    1094
6-24 months   ki1113344-GMS-Nepal        NEPAL                          1                    0      670    1094
6-24 months   ki1113344-GMS-Nepal        NEPAL                          1                    1      146    1094
6-24 months   ki1148112-LCNI-5           MALAWI                         0                    0      171     216
6-24 months   ki1148112-LCNI-5           MALAWI                         0                    1        3     216
6-24 months   ki1148112-LCNI-5           MALAWI                         1                    0       42     216
6-24 months   ki1148112-LCNI-5           MALAWI                         1                    1        0     216
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     0                    0     1640    8858
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     0                    1      230    8858
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                    0     6276    8858
6-24 months   kiGH5241-JiVitA-4          BANGLADESH                     1                    1      712    8858


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
* agecat: 0-24 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 0-24 months, studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 0-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
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
* agecat: 0-6 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-6 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 0-6 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6-24 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 6-24 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 6-24 months, studyid: ki1000109-EE, country: PAKISTAN
* agecat: 6-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 6-24 months, studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 6-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-24 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 0-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 0-24 months, studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
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
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 6-24 months, studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6-24 months, studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 6-24 months, studyid: ki1000108-IRC, country: INDIA
* agecat: 6-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 6-24 months, studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness







# Results Detail

## Results Plots
![](/tmp/4f65daa9-f778-46aa-93a8-3dbfdd327b71/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/4f65daa9-f778-46aa-93a8-3dbfdd327b71/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/4f65daa9-f778-46aa-93a8-3dbfdd327b71/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/4f65daa9-f778-46aa-93a8-3dbfdd327b71/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat        studyid               country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  --------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    NA                0.0442478   0.0062515   0.0822441
0-24 months   ki0047075b-MAL-ED     BANGLADESH   1                    NA                0.0640000   0.0210033   0.1069967
0-24 months   ki1000109-EE          PAKISTAN     0                    NA                0.0961538   0.0498312   0.1424765
0-24 months   ki1000109-EE          PAKISTAN     1                    NA                0.0588235   0.0277608   0.0898863
0-24 months   ki1101329-Keneba      GAMBIA       0                    NA                0.0608696   0.0482520   0.0734871
0-24 months   ki1101329-Keneba      GAMBIA       1                    NA                0.0337838   0.0207633   0.0468042
0-24 months   ki1113344-GMS-Nepal   NEPAL        0                    NA                0.1597222   0.0998329   0.2196115
0-24 months   ki1113344-GMS-Nepal   NEPAL        1                    NA                0.1418269   0.1082720   0.1753819
0-24 months   kiGH5241-JiVitA-3     BANGLADESH   0                    NA                0.0897833   0.0794424   0.1001242
0-24 months   kiGH5241-JiVitA-3     BANGLADESH   1                    NA                0.0488550   0.0445372   0.0531727
0-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    NA                0.1032389   0.0836545   0.1228232
0-24 months   kiGH5241-JiVitA-4     BANGLADESH   1                    NA                0.0716246   0.0614168   0.0818323
0-6 months    ki1000109-EE          PAKISTAN     0                    NA                0.1025641   0.0548904   0.1502379
0-6 months    ki1000109-EE          PAKISTAN     1                    NA                0.0523810   0.0222067   0.0825552
0-6 months    ki1101329-Keneba      GAMBIA       0                    NA                0.0286156   0.0195257   0.0377055
0-6 months    ki1101329-Keneba      GAMBIA       1                    NA                0.0176000   0.0072885   0.0279115
0-6 months    ki1113344-GMS-Nepal   NEPAL        0                    NA                0.1582734   0.0975385   0.2190082
0-6 months    ki1113344-GMS-Nepal   NEPAL        1                    NA                0.1040609   0.0738829   0.1342389
6-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    NA                0.0471698   0.0067225   0.0876171
6-24 months   ki0047075b-MAL-ED     BANGLADESH   1                    NA                0.0983607   0.0454004   0.1513209
6-24 months   ki1000109-EE          PAKISTAN     0                    NA                0.1225806   0.0708810   0.1742803
6-24 months   ki1000109-EE          PAKISTAN     1                    NA                0.1126761   0.0701548   0.1551973
6-24 months   ki1017093b-PROVIDE    BANGLADESH   0                    NA                0.0709534   0.0472382   0.0946686
6-24 months   ki1017093b-PROVIDE    BANGLADESH   1                    NA                0.0400000   0.0086145   0.0713856
6-24 months   ki1101329-Keneba      GAMBIA       0                    NA                0.1016949   0.0852480   0.1181418
6-24 months   ki1101329-Keneba      GAMBIA       1                    NA                0.0656250   0.0464354   0.0848146
6-24 months   ki1113344-GMS-Nepal   NEPAL        0                    NA                0.2158273   0.1473736   0.2842811
6-24 months   ki1113344-GMS-Nepal   NEPAL        1                    NA                0.1789216   0.1416962   0.2161469
6-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    NA                0.1229947   0.1003160   0.1456733
6-24 months   kiGH5241-JiVitA-4     BANGLADESH   1                    NA                0.1018890   0.0893964   0.1143815


### Parameter: E(Y)


agecat        studyid               country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  --------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH   NA                   NA                0.0546218   0.0256911   0.0835526
0-24 months   ki1000109-EE          PAKISTAN     NA                   NA                0.0742706   0.0477670   0.1007741
0-24 months   ki1101329-Keneba      GAMBIA       NA                   NA                0.0514151   0.0420121   0.0608181
0-24 months   ki1113344-GMS-Nepal   NEPAL        NA                   NA                0.1464286   0.1171213   0.1757358
0-24 months   kiGH5241-JiVitA-3     BANGLADESH   NA                   NA                0.0572887   0.0532017   0.0613756
0-24 months   kiGH5241-JiVitA-4     BANGLADESH   NA                   NA                0.0783679   0.0692461   0.0874896
0-6 months    ki1000109-EE          PAKISTAN     NA                   NA                0.0737705   0.0469540   0.1005870
0-6 months    ki1101329-Keneba      GAMBIA       NA                   NA                0.0250261   0.0180336   0.0320185
0-6 months    ki1113344-GMS-Nepal   NEPAL        NA                   NA                0.1181989   0.0907652   0.1456326
6-24 months   ki0047075b-MAL-ED     BANGLADESH   NA                   NA                0.0745614   0.0403897   0.1087331
6-24 months   ki1000109-EE          PAKISTAN     NA                   NA                0.1168478   0.0839821   0.1497135
6-24 months   ki1017093b-PROVIDE    BANGLADESH   NA                   NA                0.0632280   0.0437545   0.0827015
6-24 months   ki1101329-Keneba      GAMBIA       NA                   NA                0.0897833   0.0770525   0.1025140
6-24 months   ki1113344-GMS-Nepal   NEPAL        NA                   NA                0.1882998   0.1555073   0.2210923
6-24 months   kiGH5241-JiVitA-4     BANGLADESH   NA                   NA                0.1063445   0.0949209   0.1177682


### Parameter: RR


agecat        studyid               country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
------------  --------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki0047075b-MAL-ED     BANGLADESH   1                    0                 1.4463999   0.4861604   4.3032566
0-24 months   ki1000109-EE          PAKISTAN     0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki1000109-EE          PAKISTAN     1                    0                 0.6117647   0.2993296   1.2503142
0-24 months   ki1101329-Keneba      GAMBIA       0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki1101329-Keneba      GAMBIA       1                    0                 0.5550193   0.3583068   0.8597282
0-24 months   ki1113344-GMS-Nepal   NEPAL        0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   ki1113344-GMS-Nepal   NEPAL        1                    0                 0.8879599   0.5699594   1.3833840
0-24 months   kiGH5241-JiVitA-3     BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   kiGH5241-JiVitA-3     BANGLADESH   1                    0                 0.5441432   0.4716397   0.6277924
0-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
0-24 months   kiGH5241-JiVitA-4     BANGLADESH   1                    0                 0.6937754   0.5484724   0.8775725
0-6 months    ki1000109-EE          PAKISTAN     0                    0                 1.0000000   1.0000000   1.0000000
0-6 months    ki1000109-EE          PAKISTAN     1                    0                 0.5107143   0.2436205   1.0706370
0-6 months    ki1101329-Keneba      GAMBIA       0                    0                 1.0000000   1.0000000   1.0000000
0-6 months    ki1101329-Keneba      GAMBIA       1                    0                 0.6150487   0.3158437   1.1976966
0-6 months    ki1113344-GMS-Nepal   NEPAL        0                    0                 1.0000000   1.0000000   1.0000000
0-6 months    ki1113344-GMS-Nepal   NEPAL        1                    0                 0.6574758   0.4064316   1.0635847
6-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   ki0047075b-MAL-ED     BANGLADESH   1                    0                 2.0852459   0.7575801   5.7396577
6-24 months   ki1000109-EE          PAKISTAN     0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   ki1000109-EE          PAKISTAN     1                    0                 0.9191994   0.5219425   1.6188136
6-24 months   ki1017093b-PROVIDE    BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   ki1017093b-PROVIDE    BANGLADESH   1                    0                 0.5637501   0.2402669   1.3227548
6-24 months   ki1101329-Keneba      GAMBIA       0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   ki1101329-Keneba      GAMBIA       1                    0                 0.6453125   0.4620058   0.9013485
6-24 months   ki1113344-GMS-Nepal   NEPAL        0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   ki1113344-GMS-Nepal   NEPAL        1                    0                 0.8290033   0.5673097   1.2114131
6-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    0                 1.0000000   1.0000000   1.0000000
6-24 months   kiGH5241-JiVitA-4     BANGLADESH   1                    0                 0.8284015   0.6717534   1.0215789


### Parameter: PAR


agecat        studyid               country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  --------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    NA                 0.0103741   -0.0197885    0.0405366
0-24 months   ki1000109-EE          PAKISTAN     0                    NA                -0.0218833   -0.0546309    0.0108643
0-24 months   ki1101329-Keneba      GAMBIA       0                    NA                -0.0094545   -0.0158071   -0.0031019
0-24 months   ki1113344-GMS-Nepal   NEPAL        0                    NA                -0.0132937   -0.0642940    0.0377067
0-24 months   kiGH5241-JiVitA-3     BANGLADESH   0                    NA                -0.0324946   -0.0412948   -0.0236944
0-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    NA                -0.0248710   -0.0421362   -0.0076057
0-6 months    ki1000109-EE          PAKISTAN     0                    NA                -0.0287936   -0.0612660    0.0036788
0-6 months    ki1101329-Keneba      GAMBIA       0                    NA                -0.0035896   -0.0080748    0.0008957
0-6 months    ki1113344-GMS-Nepal   NEPAL        0                    NA                -0.0400745   -0.0902480    0.0100990
6-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    NA                 0.0273916   -0.0084205    0.0632037
6-24 months   ki1000109-EE          PAKISTAN     0                    NA                -0.0057328   -0.0444810    0.0330154
6-24 months   ki1017093b-PROVIDE    BANGLADESH   0                    NA                -0.0077255   -0.0176019    0.0021509
6-24 months   ki1101329-Keneba      GAMBIA       0                    NA                -0.0119116   -0.0202919   -0.0035313
6-24 months   ki1113344-GMS-Nepal   NEPAL        0                    NA                -0.0275275   -0.0856632    0.0306081
6-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    NA                -0.0166501   -0.0360893    0.0027891


### Parameter: PAF


agecat        studyid               country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
------------  --------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
0-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    NA                 0.1899251   -0.5852079    0.5860345
0-24 months   ki1000109-EE          PAKISTAN     0                    NA                -0.2946429   -0.8058824    0.0718664
0-24 months   ki1101329-Keneba      GAMBIA       0                    NA                -0.1838851   -0.3096231   -0.0702193
0-24 months   ki1113344-GMS-Nepal   NEPAL        0                    NA                -0.0907859   -0.5007022    0.2071619
0-24 months   kiGH5241-JiVitA-3     BANGLADESH   0                    NA                -0.5672082   -0.7265340   -0.4225851
0-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    NA                -0.3173621   -0.5604966   -0.1121093
0-6 months    ki1000109-EE          PAKISTAN     0                    NA                -0.3903134   -0.8833650   -0.0263392
0-6 months    ki1101329-Keneba      GAMBIA       0                    NA                -0.1434326   -0.3324812    0.0187944
0-6 months    ki1113344-GMS-Nepal   NEPAL        0                    NA                -0.3390430   -0.8320753    0.0213086
6-24 months   ki0047075b-MAL-ED     BANGLADESH   0                    NA                 0.3673696   -0.2946403    0.6908630
6-24 months   ki1000109-EE          PAKISTAN     0                    NA                -0.0490623   -0.4387899    0.2350991
6-24 months   ki1017093b-PROVIDE    BANGLADESH   0                    NA                -0.1221846   -0.2853132    0.0202401
6-24 months   ki1101329-Keneba      GAMBIA       0                    NA                -0.1326710   -0.2283537   -0.0444414
6-24 months   ki1113344-GMS-Nepal   NEPAL        0                    NA                -0.1461898   -0.4998664    0.1240879
6-24 months   kiGH5241-JiVitA-4     BANGLADESH   0                    NA                -0.1565675   -0.3552417    0.0129816