---
title: "Optimal Treatment Analysis"
output: 
  html_document:
    keep_md: TRUE
    self_contained: true
required_packages:  ['github://HBGD-UCB/longbowOptTX','github://jeremyrcoyle/skimr@vector_types', 'github://tlverse/delayed']
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
      W: []
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
      maximize:
        input: checkbox
        value: TRUE
  output_directory:
    value: '~/tmp/'
editor_options: 
  chunk_output_type: console
---







## Methods
## Outcome Variable

**Outcome Variable:** ever_wasted

## Predictor Variables

**Intervention Variable:** trth2o

**Adjustment Set:**

* arm
* sex
* W_mage
* meducyrs
* feducyrs
* hfoodsec
* W_mhtcm
* W_mwtkg
* W_mbmi
* W_nrooms
* W_nhh
* W_nchldlt5
* cleanck
* impfloor
* impsan
* safeh20
* delta_meducyrs
* delta_feducyrs
* delta_hfoodsec
* delta_W_mhtcm
* delta_W_mwtkg
* delta_W_mbmi
* delta_W_nrooms
* delta_W_nhh
* delta_W_nchldlt5
* delta_cleanck
* delta_impfloor
* delta_impsan
* delta_safeh20

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat                        studyid                    country                        trth2o    ever_wasted   n_cell     n
----------------------------  -------------------------  -----------------------------  -------  ------------  -------  ----
0-24 months (no birth wast)   ki0047075b-MAL-ED          BANGLADESH                     1                   0      104   135
0-24 months (no birth wast)   ki0047075b-MAL-ED          BANGLADESH                     1                   1       29   135
0-24 months (no birth wast)   ki0047075b-MAL-ED          BANGLADESH                     0                   0        2   135
0-24 months (no birth wast)   ki0047075b-MAL-ED          BANGLADESH                     0                   1        0   135
0-24 months (no birth wast)   ki0047075b-MAL-ED          BRAZIL                         1                   0       13   103
0-24 months (no birth wast)   ki0047075b-MAL-ED          BRAZIL                         1                   1        0   103
0-24 months (no birth wast)   ki0047075b-MAL-ED          BRAZIL                         0                   0       85   103
0-24 months (no birth wast)   ki0047075b-MAL-ED          BRAZIL                         0                   1        5   103
0-24 months (no birth wast)   ki0047075b-MAL-ED          INDIA                          1                   0        3     9
0-24 months (no birth wast)   ki0047075b-MAL-ED          INDIA                          1                   1        1     9
0-24 months (no birth wast)   ki0047075b-MAL-ED          INDIA                          0                   0        2     9
0-24 months (no birth wast)   ki0047075b-MAL-ED          INDIA                          0                   1        3     9
0-24 months (no birth wast)   ki0047075b-MAL-ED          NEPAL                          1                   0       49    83
0-24 months (no birth wast)   ki0047075b-MAL-ED          NEPAL                          1                   1       20    83
0-24 months (no birth wast)   ki0047075b-MAL-ED          NEPAL                          0                   0       12    83
0-24 months (no birth wast)   ki0047075b-MAL-ED          NEPAL                          0                   1        2    83
0-24 months (no birth wast)   ki0047075b-MAL-ED          PERU                           1                   0       37    49
0-24 months (no birth wast)   ki0047075b-MAL-ED          PERU                           1                   1        2    49
0-24 months (no birth wast)   ki0047075b-MAL-ED          PERU                           0                   0        8    49
0-24 months (no birth wast)   ki0047075b-MAL-ED          PERU                           0                   1        2    49
0-24 months (no birth wast)   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0        2    12
0-24 months (no birth wast)   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1        0    12
0-24 months (no birth wast)   ki0047075b-MAL-ED          SOUTH AFRICA                   0                   0        4    12
0-24 months (no birth wast)   ki0047075b-MAL-ED          SOUTH AFRICA                   0                   1        6    12
0-24 months (no birth wast)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        6    43
0-24 months (no birth wast)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        0    43
0-24 months (no birth wast)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                   0       33    43
0-24 months (no birth wast)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                   1        4    43
0-24 months (no birth wast)   ki1000108-CMC-V-BCS-2002   INDIA                          1                   0       68   119
0-24 months (no birth wast)   ki1000108-CMC-V-BCS-2002   INDIA                          1                   1       51   119
0-24 months (no birth wast)   ki1000108-CMC-V-BCS-2002   INDIA                          0                   0        0   119
0-24 months (no birth wast)   ki1000108-CMC-V-BCS-2002   INDIA                          0                   1        0   119
0-24 months (no birth wast)   ki1000108-IRC              INDIA                          1                   0       48   122
0-24 months (no birth wast)   ki1000108-IRC              INDIA                          1                   1       74   122
0-24 months (no birth wast)   ki1000108-IRC              INDIA                          0                   0        0   122
0-24 months (no birth wast)   ki1000108-IRC              INDIA                          0                   1        0   122
0-24 months (no birth wast)   ki1017093b-PROVIDE         BANGLADESH                     1                   0       16   687
0-24 months (no birth wast)   ki1017093b-PROVIDE         BANGLADESH                     1                   1        0   687
0-24 months (no birth wast)   ki1017093b-PROVIDE         BANGLADESH                     0                   0      549   687
0-24 months (no birth wast)   ki1017093b-PROVIDE         BANGLADESH                     0                   1      122   687
0-24 months (no birth wast)   ki1017093c-NIH-Crypto      BANGLADESH                     1                   0      366   754
0-24 months (no birth wast)   ki1017093c-NIH-Crypto      BANGLADESH                     1                   1       60   754
0-24 months (no birth wast)   ki1017093c-NIH-Crypto      BANGLADESH                     0                   0      280   754
0-24 months (no birth wast)   ki1017093c-NIH-Crypto      BANGLADESH                     0                   1       48   754
0-24 months (no birth wast)   ki1113344-GMS-Nepal        NEPAL                          1                   0        1     4
0-24 months (no birth wast)   ki1113344-GMS-Nepal        NEPAL                          1                   1        0     4
0-24 months (no birth wast)   ki1113344-GMS-Nepal        NEPAL                          0                   0        1     4
0-24 months (no birth wast)   ki1113344-GMS-Nepal        NEPAL                          0                   1        2     4
0-6 months (no birth wast)    ki0047075b-MAL-ED          BANGLADESH                     1                   0      127   134
0-6 months (no birth wast)    ki0047075b-MAL-ED          BANGLADESH                     1                   1        5   134
0-6 months (no birth wast)    ki0047075b-MAL-ED          BANGLADESH                     0                   0        2   134
0-6 months (no birth wast)    ki0047075b-MAL-ED          BANGLADESH                     0                   1        0   134
0-6 months (no birth wast)    ki0047075b-MAL-ED          BRAZIL                         1                   0       13   103
0-6 months (no birth wast)    ki0047075b-MAL-ED          BRAZIL                         1                   1        0   103
0-6 months (no birth wast)    ki0047075b-MAL-ED          BRAZIL                         0                   0       86   103
0-6 months (no birth wast)    ki0047075b-MAL-ED          BRAZIL                         0                   1        4   103
0-6 months (no birth wast)    ki0047075b-MAL-ED          INDIA                          1                   0        3     9
0-6 months (no birth wast)    ki0047075b-MAL-ED          INDIA                          1                   1        1     9
0-6 months (no birth wast)    ki0047075b-MAL-ED          INDIA                          0                   0        5     9
0-6 months (no birth wast)    ki0047075b-MAL-ED          INDIA                          0                   1        0     9
0-6 months (no birth wast)    ki0047075b-MAL-ED          NEPAL                          1                   0       61    83
0-6 months (no birth wast)    ki0047075b-MAL-ED          NEPAL                          1                   1        8    83
0-6 months (no birth wast)    ki0047075b-MAL-ED          NEPAL                          0                   0       13    83
0-6 months (no birth wast)    ki0047075b-MAL-ED          NEPAL                          0                   1        1    83
0-6 months (no birth wast)    ki0047075b-MAL-ED          PERU                           1                   0       38    49
0-6 months (no birth wast)    ki0047075b-MAL-ED          PERU                           1                   1        1    49
0-6 months (no birth wast)    ki0047075b-MAL-ED          PERU                           0                   0       10    49
0-6 months (no birth wast)    ki0047075b-MAL-ED          PERU                           0                   1        0    49
0-6 months (no birth wast)    ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0        2    12
0-6 months (no birth wast)    ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1        0    12
0-6 months (no birth wast)    ki0047075b-MAL-ED          SOUTH AFRICA                   0                   0        7    12
0-6 months (no birth wast)    ki0047075b-MAL-ED          SOUTH AFRICA                   0                   1        3    12
0-6 months (no birth wast)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        6    43
0-6 months (no birth wast)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        0    43
0-6 months (no birth wast)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                   0       36    43
0-6 months (no birth wast)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                   1        1    43
0-6 months (no birth wast)    ki1000108-CMC-V-BCS-2002   INDIA                          1                   0       80   114
0-6 months (no birth wast)    ki1000108-CMC-V-BCS-2002   INDIA                          1                   1       34   114
0-6 months (no birth wast)    ki1000108-CMC-V-BCS-2002   INDIA                          0                   0        0   114
0-6 months (no birth wast)    ki1000108-CMC-V-BCS-2002   INDIA                          0                   1        0   114
0-6 months (no birth wast)    ki1000108-IRC              INDIA                          1                   0       71   120
0-6 months (no birth wast)    ki1000108-IRC              INDIA                          1                   1       49   120
0-6 months (no birth wast)    ki1000108-IRC              INDIA                          0                   0        0   120
0-6 months (no birth wast)    ki1000108-IRC              INDIA                          0                   1        0   120
0-6 months (no birth wast)    ki1017093b-PROVIDE         BANGLADESH                     1                   0       16   683
0-6 months (no birth wast)    ki1017093b-PROVIDE         BANGLADESH                     1                   1        0   683
0-6 months (no birth wast)    ki1017093b-PROVIDE         BANGLADESH                     0                   0      631   683
0-6 months (no birth wast)    ki1017093b-PROVIDE         BANGLADESH                     0                   1       36   683
0-6 months (no birth wast)    ki1017093c-NIH-Crypto      BANGLADESH                     1                   0      412   749
0-6 months (no birth wast)    ki1017093c-NIH-Crypto      BANGLADESH                     1                   1       10   749
0-6 months (no birth wast)    ki1017093c-NIH-Crypto      BANGLADESH                     0                   0      317   749
0-6 months (no birth wast)    ki1017093c-NIH-Crypto      BANGLADESH                     0                   1       10   749
0-6 months (no birth wast)    ki1113344-GMS-Nepal        NEPAL                          1                   0        1     4
0-6 months (no birth wast)    ki1113344-GMS-Nepal        NEPAL                          1                   1        0     4
0-6 months (no birth wast)    ki1113344-GMS-Nepal        NEPAL                          0                   0        3     4
0-6 months (no birth wast)    ki1113344-GMS-Nepal        NEPAL                          0                   1        0     4
6-24 months                   ki0047075b-MAL-ED          BANGLADESH                     1                   0      108   135
6-24 months                   ki0047075b-MAL-ED          BANGLADESH                     1                   1       25   135
6-24 months                   ki0047075b-MAL-ED          BANGLADESH                     0                   0        2   135
6-24 months                   ki0047075b-MAL-ED          BANGLADESH                     0                   1        0   135
6-24 months                   ki0047075b-MAL-ED          BRAZIL                         1                   0       13   103
6-24 months                   ki0047075b-MAL-ED          BRAZIL                         1                   1        0   103
6-24 months                   ki0047075b-MAL-ED          BRAZIL                         0                   0       88   103
6-24 months                   ki0047075b-MAL-ED          BRAZIL                         0                   1        2   103
6-24 months                   ki0047075b-MAL-ED          INDIA                          1                   0        4     9
6-24 months                   ki0047075b-MAL-ED          INDIA                          1                   1        0     9
6-24 months                   ki0047075b-MAL-ED          INDIA                          0                   0        2     9
6-24 months                   ki0047075b-MAL-ED          INDIA                          0                   1        3     9
6-24 months                   ki0047075b-MAL-ED          NEPAL                          1                   0       53    83
6-24 months                   ki0047075b-MAL-ED          NEPAL                          1                   1       16    83
6-24 months                   ki0047075b-MAL-ED          NEPAL                          0                   0       12    83
6-24 months                   ki0047075b-MAL-ED          NEPAL                          0                   1        2    83
6-24 months                   ki0047075b-MAL-ED          PERU                           1                   0       37    49
6-24 months                   ki0047075b-MAL-ED          PERU                           1                   1        2    49
6-24 months                   ki0047075b-MAL-ED          PERU                           0                   0        8    49
6-24 months                   ki0047075b-MAL-ED          PERU                           0                   1        2    49
6-24 months                   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0        2    12
6-24 months                   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1        0    12
6-24 months                   ki0047075b-MAL-ED          SOUTH AFRICA                   0                   0        6    12
6-24 months                   ki0047075b-MAL-ED          SOUTH AFRICA                   0                   1        4    12
6-24 months                   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        6    43
6-24 months                   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        0    43
6-24 months                   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                   0       34    43
6-24 months                   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   0                   1        3    43
6-24 months                   ki1000108-CMC-V-BCS-2002   INDIA                          1                   0       90   120
6-24 months                   ki1000108-CMC-V-BCS-2002   INDIA                          1                   1       30   120
6-24 months                   ki1000108-CMC-V-BCS-2002   INDIA                          0                   0        0   120
6-24 months                   ki1000108-CMC-V-BCS-2002   INDIA                          0                   1        0   120
6-24 months                   ki1000108-IRC              INDIA                          1                   0       78   122
6-24 months                   ki1000108-IRC              INDIA                          1                   1       44   122
6-24 months                   ki1000108-IRC              INDIA                          0                   0        0   122
6-24 months                   ki1000108-IRC              INDIA                          0                   1        0   122
6-24 months                   ki1017093b-PROVIDE         BANGLADESH                     1                   0       14   615
6-24 months                   ki1017093b-PROVIDE         BANGLADESH                     1                   1        0   615
6-24 months                   ki1017093b-PROVIDE         BANGLADESH                     0                   0      502   615
6-24 months                   ki1017093b-PROVIDE         BANGLADESH                     0                   1       99   615
6-24 months                   ki1017093c-NIH-Crypto      BANGLADESH                     1                   0      353   730
6-24 months                   ki1017093c-NIH-Crypto      BANGLADESH                     1                   1       55   730
6-24 months                   ki1017093c-NIH-Crypto      BANGLADESH                     0                   0      281   730
6-24 months                   ki1017093c-NIH-Crypto      BANGLADESH                     0                   1       41   730
6-24 months                   ki1113344-GMS-Nepal        NEPAL                          1                   0        1     4
6-24 months                   ki1113344-GMS-Nepal        NEPAL                          1                   1        0     4
6-24 months                   ki1113344-GMS-Nepal        NEPAL                          0                   0        1     4
6-24 months                   ki1113344-GMS-Nepal        NEPAL                          0                   1        2     4


The following strata were considered:

* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months (no birth wast), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-24 months (no birth wast), studyid: ki1000108-IRC, country: INDIA
* agecat: 0-24 months (no birth wast), studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-24 months (no birth wast), studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 0-24 months (no birth wast), studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months (no birth wast), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-6 months (no birth wast), studyid: ki1000108-IRC, country: INDIA
* agecat: 0-6 months (no birth wast), studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-6 months (no birth wast), studyid: ki1017093c-NIH-Crypto, country: BANGLADESH
* agecat: 0-6 months (no birth wast), studyid: ki1113344-GMS-Nepal, country: NEPAL
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

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months (no birth wast), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months (no birth wast), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-24 months (no birth wast), studyid: ki1000108-IRC, country: INDIA
* agecat: 0-24 months (no birth wast), studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-24 months (no birth wast), studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months (no birth wast), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months (no birth wast), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-6 months (no birth wast), studyid: ki1000108-IRC, country: INDIA
* agecat: 0-6 months (no birth wast), studyid: ki1017093b-PROVIDE, country: BANGLADESH
* agecat: 0-6 months (no birth wast), studyid: ki1113344-GMS-Nepal, country: NEPAL
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
* agecat: 6-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness







# Results Detail

## Results Plots
![](/tmp/d51803d6-067e-4bcb-b5dd-056fd01b9d3a/11dbd2c7-a8eb-402c-a033-9888715c439d/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/d51803d6-067e-4bcb-b5dd-056fd01b9d3a/11dbd2c7-a8eb-402c-a033-9888715c439d/REPORT_files/figure-html/plot_rr-1.png)<!-- -->


## Results Table

### Parameter: TSM


agecat                        studyid                 country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------------------------  ----------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months (no birth wast)   ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                0.1457555   0.1108892   0.1806218
0-6 months (no birth wast)    ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                0.0367884   0.0182707   0.0553060
6-24 months                   ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                0.1083055   0.0764481   0.1401629


### Parameter: E(Y)


agecat                        studyid                 country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------------------------  ----------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months (no birth wast)   ki1017093c-NIH-Crypto   BANGLADESH   observed             NA                0.1432361   0.1182149   0.1682572
0-6 months (no birth wast)    ki1017093c-NIH-Crypto   BANGLADESH   observed             NA                0.0267023   0.0151493   0.0382553
6-24 months                   ki1017093c-NIH-Crypto   BANGLADESH   observed             NA                0.1315069   0.1069744   0.1560393


### Parameter: RR


agecat                        studyid                 country      intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------------------------  ----------------------  -----------  -------------------  ---------------  ----------  ----------  ----------
0-24 months (no birth wast)   ki1017093c-NIH-Crypto   BANGLADESH   observed             optimal           0.9827148   0.8245087   1.1712772
0-6 months (no birth wast)    ki1017093c-NIH-Crypto   BANGLADESH   observed             optimal           0.7258347   0.5461450   0.9646448
6-24 months                   ki1017093c-NIH-Crypto   BANGLADESH   observed             optimal           1.2142211   0.9677797   1.5234179


### Parameter: PAR


agecat                        studyid                 country      intervention_level   baseline_level      estimate     ci_lower    ci_upper
----------------------------  ----------------------  -----------  -------------------  ---------------  -----------  -----------  ----------
0-24 months (no birth wast)   ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                -0.0025194   -0.0280784   0.0230395
0-6 months (no birth wast)    ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                -0.0100861   -0.0211799   0.0010077
6-24 months                   ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                 0.0232013   -0.0017335   0.0481362


### Parameter: PAF


agecat                        studyid                 country      intervention_level   baseline_level      estimate     ci_lower     ci_upper
----------------------------  ----------------------  -----------  -------------------  ---------------  -----------  -----------  -----------
0-24 months (no birth wast)   ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                -0.0175893   -0.2128434    0.1462312
0-6 months (no birth wast)    ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                -0.3777242   -0.8310155   -0.0366510
6-24 months                   ki1017093c-NIH-Crypto   BANGLADESH   optimal              NA                 0.1764267   -0.0332931    0.3435813
