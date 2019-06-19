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

**Outcome Variable:** ever_stunted

## Predictor Variables

**Intervention Variable:** month

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat                       studyid                    country                        month    ever_stunted   n_cell       n
---------------------------  -------------------------  -----------------------------  ------  -------------  -------  ------
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     1                   0        9     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     1                   1        9     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     2                   0        7     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     2                   1       11     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     3                   0        8     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     3                   1       12     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     4                   0       12     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     4                   1       10     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     5                   0        5     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     5                   1       12     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     6                   0        3     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     6                   1        2     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     7                   0        9     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     7                   1        8     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     8                   0       10     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     8                   1       10     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     9                   0        9     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     9                   1       11     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     10                  0       14     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     10                  1        6     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     11                  0        7     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     11                  1        8     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     12                  0       11     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BANGLADESH                     12                  1       14     217
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         1                   0       11     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         1                   1        2     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         2                   0       18     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         2                   1        5     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         3                   0       18     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         3                   1        2     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         4                   0        9     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         4                   1        1     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         5                   0       17     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         5                   1        2     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         6                   0        8     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         6                   1        1     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         7                   0       10     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         7                   1        5     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         8                   0       14     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         8                   1        3     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         9                   0       23     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         9                   1        4     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         10                  0       19     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         10                  1        3     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         11                  0       20     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         11                  1        0     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         12                  0       12     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          BRAZIL                         12                  1        1     208
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          1                   0        5     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          1                   1       13     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          2                   0       14     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          2                   1        7     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          3                   0       10     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          3                   1       11     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          4                   0        7     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          4                   1        8     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          5                   0        2     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          5                   1        4     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          6                   0       11     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          6                   1        7     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          7                   0       12     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          7                   1        8     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          8                   0        7     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          8                   1        8     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          9                   0        9     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          9                   1       10     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          10                  0       10     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          10                  1       11     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          11                  0        7     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          11                  1       14     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          12                  0        7     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          INDIA                          12                  1        7     209
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          1                   0       15     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          1                   1        4     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          2                   0       10     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          2                   1        5     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          3                   0       10     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          3                   1        8     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          4                   0       13     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          4                   1        4     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          5                   0       14     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          5                   1        8     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          6                   0       14     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          6                   1        2     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          7                   0       17     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          7                   1        3     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          8                   0       13     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          8                   1        3     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          9                   0       14     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          9                   1        2     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          10                  0       17     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          10                  1        2     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          11                  0       11     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          11                  1        8     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          12                  0        9     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          NEPAL                          12                  1        6     212
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           1                   0       19     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           1                   1       18     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           2                   0        8     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           2                   1       14     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           3                   0       10     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           3                   1        9     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           4                   0        7     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           4                   1       11     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           5                   0        9     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           5                   1       14     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           6                   0        7     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           6                   1       10     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           7                   0        5     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           7                   1       16     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           8                   0       10     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           8                   1       10     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           9                   0        9     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           9                   1       13     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           10                  0       15     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           10                  1        8     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           11                  0       10     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           11                  1       16     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           12                  0        6     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           12                  1       12     266
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0       15     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1       20     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   2                   0       15     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   2                   1       17     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   3                   0       12     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   3                   1        7     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   4                   0        8     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   4                   1        4     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   5                   0        9     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   5                   1        5     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   6                   0       12     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   6                   1        7     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   7                   0       13     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   7                   1       11     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   8                   0        4     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   8                   1        8     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   9                   0       14     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   9                   1        9     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   10                  0       10     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   10                  1       16     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   11                  0       12     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   11                  1       11     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   12                  0       19     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          SOUTH AFRICA                   12                  1       22     280
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        6     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1       13     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   0        6     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   1       18     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   0        3     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   1       16     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                   0        3     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                   1        7     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   5                   0        3     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   5                   1       11     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   6                   0        1     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   6                   1       16     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   7                   0        5     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   7                   1       17     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   8                   0        2     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   8                   1        9     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   9                   0        4     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   9                   1       12     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   10                  0        1     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   10                  1       14     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   11                  0        1     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   11                  1       24     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   12                  0        6     219
0-24 months (no birth st.)   ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   12                  1       21     219
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          1                   0        1     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          1                   1       16     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          2                   0        1     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          2                   1       14     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          3                   0        0     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          3                   1       21     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          4                   0        2     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          4                   1       22     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          5                   0        5     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          5                   1       37     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          6                   0        3     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          6                   1       28     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          7                   0        5     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          7                   1       25     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          8                   0        2     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          8                   1       30     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          9                   0        2     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          9                   1       14     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          10                  0        0     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          10                  1       13     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          11                  0        5     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          11                  1       28     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          12                  0        2     296
0-24 months (no birth st.)   ki1000108-CMC-V-BCS-2002   INDIA                          12                  1       20     296
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          1                   0       10     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          1                   1       19     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          2                   0        9     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          2                   1       16     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          3                   0        8     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          3                   1       17     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          4                   0        5     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          4                   1       15     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          5                   0        4     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          5                   1       16     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          6                   0       16     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          6                   1       15     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          7                   0       14     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          7                   1       17     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          8                   0       22     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          8                   1       19     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          9                   0        9     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          9                   1       16     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          10                  0       19     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          10                  1       14     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          11                  0       17     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          11                  1       18     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          12                  0       14     360
0-24 months (no birth st.)   ki1000108-IRC              INDIA                          12                  1       31     360
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       1                   0        5     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       1                   1       47     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       2                   0        9     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       2                   1       48     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       3                   0        5     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       3                   1       25     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       4                   0        2     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       4                   1       14     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       5                   0        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       5                   1        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       6                   0        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       6                   1        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       7                   0        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       7                   1        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       8                   0        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       8                   1        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       9                   0        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       9                   1        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       10                  0        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       10                  1        0     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       11                  0        4     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       11                  1       33     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       12                  0        8     249
0-24 months (no birth st.)   ki1000109-EE               PAKISTAN                       12                  1       49     249
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       1                   0        0     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       1                   1        7     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       2                   0        4     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       2                   1        5     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       3                   0        3     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       3                   1        8     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       4                   0       10     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       4                   1       11     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       5                   0       15     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       5                   1       12     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       6                   0       17     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       6                   1       21     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       7                   0       12     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       7                   1       10     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       8                   0       17     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       8                   1       17     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       9                   0       11     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       9                   1        9     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       10                  0        5     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       10                  1        2     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       11                  0        2     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       11                  1        2     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       12                  0        1     202
0-24 months (no birth st.)   ki1000109-ResPak           PAKISTAN                       12                  1        1     202
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          1                   0       32    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          1                   1       44    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          2                   0       34    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          2                   1       28    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          3                   0       32    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          3                   1       28    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          4                   0       22    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          4                   1       43    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          5                   0       27    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          5                   1       37    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          6                   0       40    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          6                   1       46    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          7                   0       32    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          7                   1       53    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          8                   0       36    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          8                   1       75    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          9                   0       68    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          9                   1       75    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          10                  0       49    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          10                  1       73    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          11                  0       51    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          11                  1       57    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          12                  0       50    1090
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          12                  1       58    1090
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          1                   0        5     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          1                   1       24     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          2                   0        9     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          2                   1       15     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          3                   0        8     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          3                   1       14     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          4                   0        4     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          4                   1       16     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          5                   0        6     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          5                   1       14     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          6                   0        9     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          6                   1       18     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          7                   0        3     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          7                   1        7     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          8                   0        0     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          8                   1        0     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          9                   0        1     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          9                   1        8     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          10                  0        4     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          10                  1       13     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          11                  0       11     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          11                  1       25     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          12                  0       12     257
0-24 months (no birth st.)   ki1000304b-SAS-FoodSuppl   INDIA                          12                  1       31     257
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     1                   0       21     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     1                   1       29     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     2                   0       22     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     2                   1       28     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     3                   0       27     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     3                   1       27     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     4                   0       16     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     4                   1       28     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     5                   0       17     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     5                   1       24     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     6                   0       15     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     6                   1       26     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     7                   0       15     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     7                   1       27     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     8                   0       13     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     8                   1       25     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     9                   0       14     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     9                   1       14     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     10                  0       19     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     10                  1       31     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     11                  0       13     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     11                  1       31     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     12                  0       19     530
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     12                  1       29     530
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                   0      152    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                   1       62    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                   0      108    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                   1       42    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                   0      132    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                   1       43    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                   0      100    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                   1       49    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   5                   0      128    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   5                   1       55    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   6                   0      111    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   6                   1       49    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   7                   0      107    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   7                   1       49    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   8                   0      123    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   8                   1       70    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   9                   0      163    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   9                   1       52    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   10                  0      144    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   10                  1       68    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   11                  0      142    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   11                  1       68    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   12                  0      157    2235
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   12                  1       61    2235
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      1                   0        9     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      1                   1        4     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      2                   0        9     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      2                   1        7     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      3                   0        6     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      3                   1       10     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      4                   0       14     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      4                   1       10     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      5                   0       17     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      5                   1       12     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      6                   0       17     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      6                   1       12     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      7                   0       12     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      7                   1        6     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      8                   0       10     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      8                   1        5     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      9                   0       18     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      9                   1        5     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      10                  0       15     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      10                  1        9     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      11                  0       16     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      11                  1        8     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      12                  0        5     239
0-24 months (no birth st.)   ki1112895-Guatemala BSC    GUATEMALA                      12                  1        3     239
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   1                   0      157    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   1                   1       28    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   2                   0      121    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   2                   1       24    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   3                   0      142    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   3                   1       32    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   4                   0      114    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   4                   1       29    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   5                   0      156    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   5                   1       32    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   6                   0      235    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   6                   1       53    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   7                   0      267    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   7                   1       61    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   8                   0      229    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   8                   1       52    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   9                   0      179    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   9                   1       44    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   10                  0      255    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   10                  1       45    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   11                  0      123    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   11                  1       27    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   12                  0      104    2533
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   12                  1       24    2533
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          1                   0        2     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          1                   1        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          2                   0        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          2                   1        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          3                   0        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          3                   1        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          4                   0        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          4                   1        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          5                   0        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          5                   1        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          6                   0        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          6                   1        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          7                   0       35     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          7                   1       80     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          8                   0       78     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          8                   1      132     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          9                   0       72     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          9                   1      120     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          10                  0        8     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          10                  1        3     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          11                  0        0     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          11                  1        4     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          12                  0        1     535
0-24 months (no birth st.)   ki1113344-GMS-Nepal        NEPAL                          12                  1        0     535
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     1                   0        2     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     1                   1       13     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     2                   0        6     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     2                   1       15     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     3                   0        6     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     3                   1       10     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     4                   0        3     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     4                   1       13     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     5                   0        4     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     5                   1       11     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     6                   0        1     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     6                   1        9     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     7                   0        2     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     7                   1        5     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     8                   0        2     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     8                   1       10     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     9                   0        2     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     9                   1        9     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     10                  0        3     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     10                  1        9     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     11                  0        2     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     11                  1        1     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     12                  0        8     168
0-24 months (no birth st.)   ki1114097-CMIN             BANGLADESH                     12                  1       22     168
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         1                   0        8     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         1                   1        5     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         2                   0        3     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         2                   1        4     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         3                   0       10     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         3                   1        3     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         4                   0        9     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         4                   1        1     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         5                   0        3     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         5                   1        2     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         6                   0        2     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         6                   1        4     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         7                   0        3     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         7                   1        1     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         8                   0       10     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         8                   1        2     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         9                   0        6     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         9                   1        3     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         10                  0       10     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         10                  1        4     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         11                  0       10     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         11                  1        2     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         12                  0        5     114
0-24 months (no birth st.)   ki1114097-CMIN             BRAZIL                         12                  1        4     114
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  1                   0       27    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  1                   1        9    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  2                   0       85    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  2                   1       50    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  3                   0       88    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  3                   1       50    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  4                   0      145    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  4                   1       72    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  5                   0      114    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  5                   1       44    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  6                   0       63    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  6                   1       21    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  7                   0       51    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  7                   1       23    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  8                   0       52    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  8                   1       18    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  9                   0       95    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  9                   1       39    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  10                  0       40    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  10                  1       13    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  11                  0       40    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  11                  1       14    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  12                  0       61    1245
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  12                  1       31    1245
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           1                   0       44     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           1                   1       10     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           2                   0       88     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           2                   1       39     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           3                   0       83     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           3                   1       26     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           4                   0       44     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           4                   1       27     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           5                   0       51     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           5                   1       27     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           6                   0       38     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           6                   1       13     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           7                   0       35     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           7                   1       16     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           8                   0       51     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           8                   1       20     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           9                   0       32     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           9                   1       10     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           10                  0       22     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           10                  1       13     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           11                  0       43     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           11                  1       26     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           12                  0       33     803
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           12                  1       12     803
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           1                   0        8     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           1                   1        0     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           2                   0       11     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           2                   1        2     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           3                   0       24     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           3                   1        3     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           4                   0        9     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           4                   1        9     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           5                   0       17     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           5                   1        4     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           6                   0        9     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           6                   1        4     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           7                   0       10     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           7                   1        6     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           8                   0       19     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           8                   1        4     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           9                   0       12     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           9                   1        2     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           10                  0       15     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           10                  1        7     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           11                  0       12     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           11                  1        3     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           12                  0        6     197
0-24 months (no birth st.)   ki1114097-CONTENT          PERU                           12                  1        1     197
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        1                   0      960   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        1                   1      211   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        2                   0      788   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        2                   1      204   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        3                   0      963   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        3                   1      211   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        4                   0      953   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        4                   1      167   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        5                   0      975   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        5                   1      167   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        6                   0     1050   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        6                   1      162   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        7                   0     1258   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        7                   1      206   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        8                   0     1382   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        8                   1      223   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        9                   0     1339   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        9                   1      235   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        10                  0     1498   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        10                  1      287   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        11                  0     1422   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        11                  1      272   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        12                  0     1479   16742
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        12                  1      330   16742
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       1                   0      811   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       1                   1      381   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       2                   0      617   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       2                   1      278   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       3                   0      677   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       3                   1      346   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       4                   0      619   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       4                   1      303   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       5                   0      574   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       5                   1      319   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       6                   0      661   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       6                   1      362   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       7                   0      710   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       7                   1      358   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       8                   0      743   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       8                   1      399   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       9                   0      868   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       9                   1      372   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       10                  0      674   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       10                  1      297   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       11                  0      740   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       11                  1      314   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       12                  0      783   12564
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       12                  1      358   12564
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         1                   0       22     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         1                   1       17     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         2                   0       46     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         2                   1       30     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         3                   0       33     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         3                   1       30     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         4                   0       32     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         4                   1       29     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         5                   0       40     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         5                   1       32     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         6                   0       30     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         6                   1       32     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         7                   0       25     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         7                   1       15     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         8                   0       16     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         8                   1       12     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         9                   0       11     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         9                   1        7     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         10                  0       16     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         10                  1        5     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         11                  0       23     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         11                  1        9     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         12                  0       11     531
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         12                  1        8     531
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     1                   0     1242   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     1                   1      397   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     2                   0     1093   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     2                   1      377   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     3                   0     1368   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     3                   1      388   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     4                   0     1048   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     4                   1      297   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     5                   0      748   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     5                   1      248   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     6                   0      708   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     6                   1      278   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     7                   0      819   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     7                   1      289   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     8                   0     1054   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     8                   1      347   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     9                   0     1396   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     9                   1      486   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     10                  0     1446   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     10                  1      507   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     11                  0     1391   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     11                  1      536   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     12                  0     1474   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     12                  1      532   18469
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     1                   0       26    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     1                   1       14    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     2                   0      150    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     2                   1       91    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     3                   0      183    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     3                   1      115    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     4                   0      362    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     4                   1      294    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     5                   0      243    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     5                   1      194    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     6                   0      184    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     6                   1      134    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     7                   0      365    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     7                   1      270    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     8                   0      232    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     8                   1      177    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     9                   0      247    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     9                   1      153    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     10                  0      162    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     10                  1       93    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     11                  0       86    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     11                  1       52    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     12                  0       39    3886
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     12                  1       20    3886
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     1                   0       16     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     1                   1        2     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     2                   0       13     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     2                   1        5     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     3                   0       13     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     3                   1        7     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     4                   0       21     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     4                   1        1     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     5                   0       12     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     5                   1        5     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     6                   0        4     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     6                   1        1     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     7                   0       14     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     7                   1        3     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     8                   0       15     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     8                   1        5     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     9                   0       16     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     9                   1        4     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     10                  0       17     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     10                  1        3     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     11                  0       11     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     11                  1        4     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     12                  0       19     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BANGLADESH                     12                  1        6     217
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         1                   0       12     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         1                   1        1     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         2                   0       20     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         2                   1        3     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         3                   0       18     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         3                   1        2     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         4                   0        9     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         4                   1        1     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         5                   0       18     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         5                   1        1     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         6                   0        8     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         6                   1        1     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         7                   0       13     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         7                   1        2     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         8                   0       14     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         8                   1        3     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         9                   0       24     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         9                   1        3     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         10                  0       20     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         10                  1        2     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         11                  0       20     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         11                  1        0     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         12                  0       12     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          BRAZIL                         12                  1        1     208
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          1                   0       12     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          1                   1        6     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          2                   0       19     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          2                   1        2     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          3                   0       15     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          3                   1        6     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          4                   0       12     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          4                   1        3     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          5                   0        5     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          5                   1        1     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          6                   0       16     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          6                   1        2     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          7                   0       15     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          7                   1        5     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          8                   0       13     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          8                   1        2     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          9                   0       17     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          9                   1        2     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          10                  0       14     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          10                  1        7     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          11                  0       16     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          11                  1        5     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          12                  0       11     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          INDIA                          12                  1        3     209
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          1                   0       17     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          1                   1        2     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          2                   0       15     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          2                   1        0     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          3                   0       17     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          3                   1        1     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          4                   0       15     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          4                   1        2     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          5                   0       19     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          5                   1        3     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          6                   0       16     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          6                   1        0     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          7                   0       19     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          7                   1        1     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          8                   0       16     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          8                   1        0     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          9                   0       15     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          9                   1        1     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          10                  0       19     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          10                  1        0     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          11                  0       16     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          11                  1        3     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          12                  0       14     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          NEPAL                          12                  1        1     212
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           1                   0       25     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           1                   1       12     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           2                   0       12     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           2                   1       10     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           3                   0       14     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           3                   1        5     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           4                   0       13     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           4                   1        5     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           5                   0       14     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           5                   1        9     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           6                   0       12     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           6                   1        5     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           7                   0       11     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           7                   1       10     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           8                   0       16     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           8                   1        4     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           9                   0       14     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           9                   1        8     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           10                  0       18     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           10                  1        5     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           11                  0       13     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           11                  1       13     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           12                  0       12     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          PERU                           12                  1        6     266
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0       25     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1       10     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   2                   0       25     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   2                   1        7     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   3                   0       14     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   3                   1        5     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   4                   0       11     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   4                   1        1     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   5                   0       10     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   5                   1        4     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   6                   0       16     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   6                   1        3     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   7                   0       15     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   7                   1        9     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   8                   0        5     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   8                   1        7     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   9                   0       19     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   9                   1        4     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   10                  0       18     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   10                  1        8     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   11                  0       15     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   11                  1        8     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   12                  0       28     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          SOUTH AFRICA                   12                  1       13     280
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0       15     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        4     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   0       17     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   1        7     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   0        8     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   1       11     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                   0        6     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                   1        4     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   5                   0       11     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   5                   1        3     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   6                   0       12     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   6                   1        5     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   7                   0       15     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   7                   1        7     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   8                   0        8     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   8                   1        3     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   9                   0       13     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   9                   1        3     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   10                  0        9     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   10                  1        6     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   11                  0       18     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   11                  1        7     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   12                  0       22     219
0-6 months (no birth st.)    ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   12                  1        5     219
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          1                   0        9     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          1                   1        8     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          2                   0        9     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          2                   1        6     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          3                   0       15     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          3                   1        6     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          4                   0       16     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          4                   1        8     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          5                   0       28     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          5                   1       13     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          6                   0       19     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          6                   1       10     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          7                   0       18     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          7                   1       12     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          8                   0       14     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          8                   1       17     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          9                   0       12     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          9                   1        4     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          10                  0        9     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          10                  1        4     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          11                  0       19     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          11                  1       14     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          12                  0       12     292
0-6 months (no birth st.)    ki1000108-CMC-V-BCS-2002   INDIA                          12                  1       10     292
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          1                   0       21     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          1                   1        8     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          2                   0       14     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          2                   1       11     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          3                   0       16     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          3                   1        9     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          4                   0       12     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          4                   1        8     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          5                   0       10     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          5                   1       10     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          6                   0       23     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          6                   1        8     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          7                   0       20     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          7                   1       11     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          8                   0       32     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          8                   1        9     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          9                   0       15     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          9                   1       10     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          10                  0       24     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          10                  1        9     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          11                  0       26     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          11                  1        9     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          12                  0       23     360
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          12                  1       22     360
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       1                   0       18     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       1                   1       34     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       2                   0       22     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       2                   1       35     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       3                   0       15     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       3                   1       15     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       4                   0        7     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       4                   1        9     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       5                   0        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       5                   1        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       6                   0        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       6                   1        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       7                   0        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       7                   1        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       8                   0        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       8                   1        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       9                   0        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       9                   1        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       10                  0        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       10                  1        0     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       11                  0       11     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       11                  1       26     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       12                  0       26     249
0-6 months (no birth st.)    ki1000109-EE               PAKISTAN                       12                  1       31     249
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       1                   0        2     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       1                   1        5     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       2                   0        6     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       2                   1        3     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       3                   0        4     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       3                   1        7     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       4                   0       11     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       4                   1       10     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       5                   0       16     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       5                   1       11     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       6                   0       19     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       6                   1       19     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       7                   0       13     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       7                   1        9     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       8                   0       22     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       8                   1       12     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       9                   0       12     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       9                   1        8     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       10                  0        6     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       10                  1        1     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       11                  0        2     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       11                  1        2     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       12                  0        1     202
0-6 months (no birth st.)    ki1000109-ResPak           PAKISTAN                       12                  1        1     202
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          1                   0       62    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          1                   1       14    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          2                   0       56    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          2                   1        6    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          3                   0       52    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          3                   1        8    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          4                   0       48    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          4                   1       17    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          5                   0       51    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          5                   1       13    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          6                   0       66    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          6                   1       19    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          7                   0       62    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          7                   1       23    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          8                   0       84    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          8                   1       27    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          9                   0      124    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          9                   1       19    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          10                  0      100    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          10                  1       22    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          11                  0       91    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          11                  1       17    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          12                  0       83    1089
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          12                  1       25    1089
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          1                   0       29     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          1                   1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          2                   0       24     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          2                   1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          3                   0       21     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          3                   1        1     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          4                   0       20     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          4                   1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          5                   0       19     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          5                   1        1     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          6                   0       26     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          6                   1        1     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          7                   0       10     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          7                   1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          8                   0        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          8                   1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          9                   0        9     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          9                   1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          10                  0       17     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          10                  1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          11                  0       36     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          11                  1        0     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          12                  0       43     257
0-6 months (no birth st.)    ki1000304b-SAS-FoodSuppl   INDIA                          12                  1        0     257
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     1                   0       35     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     1                   1       15     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     2                   0       40     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     2                   1       10     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     3                   0       48     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     3                   1        6     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     4                   0       36     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     4                   1        8     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     5                   0       35     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     5                   1        6     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     6                   0       28     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     6                   1       13     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     7                   0       26     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     7                   1       16     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     8                   0       29     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     8                   1        9     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     9                   0       23     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     9                   1        5     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     10                  0       38     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     10                  1       12     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     11                  0       29     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     11                  1       15     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     12                  0       42     530
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     12                  1        6     530
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                   0      186    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                   1       28    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                   0      134    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                   1       16    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                   0      160    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                   1       15    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                   0      133    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                   1       16    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   5                   0      160    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   5                   1       23    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   6                   0      136    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   6                   1       24    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   7                   0      135    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   7                   1       21    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   8                   0      154    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   8                   1       39    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   9                   0      183    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   9                   1       32    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   10                  0      183    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   10                  1       29    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   11                  0      170    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   11                  1       40    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   12                  0      195    2235
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   12                  1       23    2235
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      1                   0       13     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      1                   1        0     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      2                   0       15     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      2                   1        1     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      3                   0       13     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      3                   1        2     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      4                   0       18     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      4                   1        2     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      5                   0       21     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      5                   1        2     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      6                   0       26     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      6                   1        3     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      7                   0       17     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      7                   1        1     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      8                   0       12     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      8                   1        2     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      9                   0       19     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      9                   1        1     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      10                  0       20     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      10                  1        3     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      11                  0       22     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      11                  1        2     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      12                  0        6     223
0-6 months (no birth st.)    ki1112895-Guatemala BSC    GUATEMALA                      12                  1        2     223
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          1                   0        2     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          1                   1        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          2                   0        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          2                   1        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          3                   0        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          3                   1        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          4                   0        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          4                   1        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          5                   0        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          5                   1        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          6                   0        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          6                   1        0     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          7                   0       95     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          7                   1       20     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          8                   0      173     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          8                   1       37     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          9                   0      154     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          9                   1       38     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          10                  0        9     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          10                  1        2     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          11                  0        1     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          11                  1        3     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          12                  0        1     535
0-6 months (no birth st.)    ki1113344-GMS-Nepal        NEPAL                          12                  1        0     535
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     1                   0        9     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     1                   1        6     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     2                   0       16     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     2                   1        5     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     3                   0       12     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     3                   1        4     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     4                   0       10     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     4                   1        6     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     5                   0       13     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     5                   1        2     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     6                   0        8     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     6                   1        2     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     7                   0        6     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     7                   1        1     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     8                   0        9     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     8                   1        3     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     9                   0        7     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     9                   1        4     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     10                  0        7     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     10                  1        5     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     11                  0        2     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     11                  1        1     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     12                  0       21     168
0-6 months (no birth st.)    ki1114097-CMIN             BANGLADESH                     12                  1        9     168
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         1                   0       12     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         1                   1        1     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         2                   0        6     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         2                   1        1     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         3                   0       13     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         3                   1        0     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         4                   0       10     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         4                   1        0     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         5                   0        5     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         5                   1        0     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         6                   0        4     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         6                   1        2     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         7                   0        3     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         7                   1        1     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         8                   0       12     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         8                   1        0     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         9                   0        8     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         9                   1        1     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         10                  0       12     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         10                  1        2     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         11                  0       11     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         11                  1        1     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         12                  0        8     114
0-6 months (no birth st.)    ki1114097-CMIN             BRAZIL                         12                  1        1     114
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  1                   0       21     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  1                   1        0     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  2                   0       81     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  2                   1        5     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  3                   0       94     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  3                   1        1     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  4                   0      114     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  4                   1        0     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  5                   0      103     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  5                   1        1     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  6                   0       52     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  6                   1        3     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  7                   0       39     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  7                   1        2     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  8                   0       47     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  8                   1        1     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  9                   0      103     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  9                   1        3     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  10                  0       38     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  10                  1        2     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  11                  0       47     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  11                  1        0     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  12                  0       80     841
0-6 months (no birth st.)    ki1114097-CMIN             GUINEA-BISSAU                  12                  1        4     841
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           1                   0       49     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           1                   1        3     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           2                   0       57     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           2                   1        2     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           3                   0       69     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           3                   1        6     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           4                   0       57     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           4                   1        9     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           5                   0       65     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           5                   1        7     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           6                   0       44     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           6                   1        5     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           7                   0       42     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           7                   1        4     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           8                   0       49     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           8                   1        3     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           9                   0       39     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           9                   1        1     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           10                  0       30     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           10                  1        5     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           11                  0       63     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           11                  1        4     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           12                  0       45     658
0-6 months (no birth st.)    ki1114097-CMIN             PERU                           12                  1        0     658
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           1                   0        8     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           1                   1        0     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           2                   0       13     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           2                   1        0     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           3                   0       24     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           3                   1        3     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           4                   0       11     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           4                   1        7     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           5                   0       18     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           5                   1        3     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           6                   0       10     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           6                   1        3     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           7                   0       12     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           7                   1        4     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           8                   0       20     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           8                   1        3     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           9                   0       13     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           9                   1        1     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           10                  0       19     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           10                  1        3     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           11                  0       12     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           11                  1        3     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           12                  0        7     197
0-6 months (no birth st.)    ki1114097-CONTENT          PERU                           12                  1        0     197
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        1                   0     1053   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        1                   1      118   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        2                   0      888   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        2                   1      104   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        3                   0     1069   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        3                   1      105   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        4                   0     1024   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        4                   1       96   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        5                   0     1047   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        5                   1       95   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        6                   0     1126   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        6                   1       86   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        7                   0     1342   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        7                   1      122   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        8                   0     1476   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        8                   1      129   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        9                   0     1423   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        9                   1      150   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        10                  0     1612   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        10                  1      172   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        11                  0     1530   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        11                  1      164   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        12                  0     1622   16740
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        12                  1      187   16740
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       1                   0     1011   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       1                   1      177   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       2                   0      768   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       2                   1      125   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       3                   0      859   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       3                   1      163   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       4                   0      761   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       4                   1      160   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       5                   0      708   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       5                   1      185   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       6                   0      788   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       6                   1      235   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       7                   0      852   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       7                   1      216   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       8                   0      896   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       8                   1      246   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       9                   0     1054   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       9                   1      183   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       10                  0      823   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       10                  1      145   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       11                  0      902   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       11                  1      150   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       12                  0      985   12548
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       12                  1      156   12548
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         1                   0        5     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         1                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         2                   0       31     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         2                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         3                   0       37     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         3                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         4                   0       29     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         4                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         5                   0       17     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         5                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         6                   0       19     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         6                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         7                   0       18     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         7                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         8                   0        4     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         8                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         9                   0        2     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         9                   1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         10                  0        2     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         10                  1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         11                  0        9     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         11                  1        0     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         12                  0        2     175
0-6 months (no birth st.)    ki1148112-LCNI-5           MALAWI                         12                  1        0     175
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     1                   0     1429   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     1                   1      205   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     2                   0     1304   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     2                   1      165   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     3                   0     1559   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     3                   1      192   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     4                   0     1202   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     4                   1      136   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     5                   0      891   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     5                   1      100   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     6                   0      894   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     6                   1       86   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     7                   0     1003   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     7                   1      103   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     8                   0     1237   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     8                   1      163   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     9                   0     1599   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     9                   1      280   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     10                  0     1628   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     10                  1      321   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     11                  0     1587   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     11                  1      337   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     12                  0     1676   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     12                  1      328   18425
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     1                   0       35    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     1                   1        0    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     2                   0      212    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     2                   1       25    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     3                   0      270    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     3                   1       21    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     4                   0      599    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     4                   1       54    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     5                   0      395    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     5                   1       41    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     6                   0      295    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     6                   1       23    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     7                   0      594    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     7                   1       41    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     8                   0      372    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     8                   1       36    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     9                   0      234    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     9                   1       38    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     10                  0      178    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     10                  1       25    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     11                  0      110    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     11                  1        9    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     12                  0       52    3659
0-6 months (no birth st.)    kiGH5241-JiVitA-4          BANGLADESH                     12                  1        0    3659
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     1                   0        8     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     1                   1        7     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     2                   0        4     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     2                   1        6     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     3                   0        7     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     3                   1        5     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     4                   0       12     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     4                   1        9     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     5                   0        5     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     5                   1        7     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     6                   0        3     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     6                   1        1     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     7                   0        7     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     7                   1        5     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     8                   0       10     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     8                   1        5     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     9                   0        8     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     9                   1        7     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     10                  0       11     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     10                  1        3     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     11                  0        6     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     11                  1        4     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     12                  0       11     159
6-24 months                  ki0047075b-MAL-ED          BANGLADESH                     12                  1        8     159
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         1                   0       11     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         1                   1        1     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         2                   0       15     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         2                   1        2     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         3                   0       16     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         3                   1        0     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         4                   0        8     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         4                   1        0     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         5                   0       15     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         5                   1        1     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         6                   0        8     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         6                   1        0     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         7                   0        9     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         7                   1        3     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         8                   0       11     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         8                   1        0     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         9                   0       21     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         9                   1        1     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         10                  0       18     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         10                  1        1     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         11                  0       18     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         11                  1        0     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         12                  0        9     168
6-24 months                  ki0047075b-MAL-ED          BRAZIL                         12                  1        0     168
6-24 months                  ki0047075b-MAL-ED          INDIA                          1                   0        5     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          1                   1        7     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          2                   0       11     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          2                   1        5     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          3                   0       10     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          3                   1        5     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          4                   0        6     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          4                   1        5     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          5                   0        2     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          5                   1        3     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          6                   0       10     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          6                   1        5     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          7                   0       11     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          7                   1        3     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          8                   0        6     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          8                   1        6     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          9                   0        6     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          9                   1        8     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          10                  0       10     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          10                  1        4     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          11                  0        7     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          11                  1        9     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          12                  0        7     155
6-24 months                  ki0047075b-MAL-ED          INDIA                          12                  1        4     155
6-24 months                  ki0047075b-MAL-ED          NEPAL                          1                   0       15     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          1                   1        2     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          2                   0       10     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          2                   1        5     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          3                   0       10     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          3                   1        7     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          4                   0       13     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          4                   1        2     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          5                   0       13     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          5                   1        5     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          6                   0       14     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          6                   1        2     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          7                   0       16     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          7                   1        2     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          8                   0       13     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          8                   1        3     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          9                   0       13     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          9                   1        1     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          10                  0       17     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          10                  1        2     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          11                  0       11     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          11                  1        5     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          12                  0        9     195
6-24 months                  ki0047075b-MAL-ED          NEPAL                          12                  1        5     195
6-24 months                  ki0047075b-MAL-ED          PERU                           1                   0       15     149
6-24 months                  ki0047075b-MAL-ED          PERU                           1                   1        6     149
6-24 months                  ki0047075b-MAL-ED          PERU                           2                   0        6     149
6-24 months                  ki0047075b-MAL-ED          PERU                           2                   1        4     149
6-24 months                  ki0047075b-MAL-ED          PERU                           3                   0        9     149
6-24 months                  ki0047075b-MAL-ED          PERU                           3                   1        4     149
6-24 months                  ki0047075b-MAL-ED          PERU                           4                   0        6     149
6-24 months                  ki0047075b-MAL-ED          PERU                           4                   1        6     149
6-24 months                  ki0047075b-MAL-ED          PERU                           5                   0        7     149
6-24 months                  ki0047075b-MAL-ED          PERU                           5                   1        5     149
6-24 months                  ki0047075b-MAL-ED          PERU                           6                   0        6     149
6-24 months                  ki0047075b-MAL-ED          PERU                           6                   1        5     149
6-24 months                  ki0047075b-MAL-ED          PERU                           7                   0        4     149
6-24 months                  ki0047075b-MAL-ED          PERU                           7                   1        6     149
6-24 months                  ki0047075b-MAL-ED          PERU                           8                   0        7     149
6-24 months                  ki0047075b-MAL-ED          PERU                           8                   1        6     149
6-24 months                  ki0047075b-MAL-ED          PERU                           9                   0        9     149
6-24 months                  ki0047075b-MAL-ED          PERU                           9                   1        5     149
6-24 months                  ki0047075b-MAL-ED          PERU                           10                  0        8     149
6-24 months                  ki0047075b-MAL-ED          PERU                           10                  1        3     149
6-24 months                  ki0047075b-MAL-ED          PERU                           11                  0        9     149
6-24 months                  ki0047075b-MAL-ED          PERU                           11                  1        3     149
6-24 months                  ki0047075b-MAL-ED          PERU                           12                  0        4     149
6-24 months                  ki0047075b-MAL-ED          PERU                           12                  1        6     149
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   1                   0       12     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   1                   1       10     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   2                   0        8     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   2                   1       10     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   3                   0        9     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   3                   1        2     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   4                   0        7     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   4                   1        3     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   5                   0        7     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   5                   1        1     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   6                   0        9     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   6                   1        4     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   7                   0       10     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   7                   1        2     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   8                   0        2     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   8                   1        1     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   9                   0       10     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   9                   1        5     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   10                  0        7     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   10                  1        8     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   11                  0        8     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   11                  1        3     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   12                  0       12     159
6-24 months                  ki0047075b-MAL-ED          SOUTH AFRICA                   12                  1        9     159
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   0        5     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   1                   1        9     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   0        6     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   2                   1       11     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   0        2     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   3                   1        5     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                   0        2     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   4                   1        3     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   5                   0        2     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   5                   1        8     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   6                   0        1     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   6                   1       11     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   7                   0        5     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   7                   1       10     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   8                   0        2     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   8                   1        6     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   9                   0        3     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   9                   1        9     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   10                  0        1     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   10                  1        8     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   11                  0        1     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   11                  1       17     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   12                  0        2     145
6-24 months                  ki0047075b-MAL-ED          TANZANIA, UNITED REPUBLIC OF   12                  1       16     145
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          1                   0        1     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          1                   1        8     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          2                   0        1     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          2                   1        8     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          3                   0        0     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          3                   1       15     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          4                   0        2     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          4                   1       14     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          5                   0        5     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          5                   1       24     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          6                   0        3     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          6                   1       18     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          7                   0        5     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          7                   1       13     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          8                   0        2     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          8                   1       13     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          9                   0        2     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          9                   1       11     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          10                  0        0     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          10                  1        9     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          11                  0        5     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          11                  1       14     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          12                  0        2     185
6-24 months                  ki1000108-CMC-V-BCS-2002   INDIA                          12                  1       10     185
6-24 months                  ki1000108-IRC              INDIA                          1                   0       10     236
6-24 months                  ki1000108-IRC              INDIA                          1                   1       11     236
6-24 months                  ki1000108-IRC              INDIA                          2                   0        9     236
6-24 months                  ki1000108-IRC              INDIA                          2                   1        5     236
6-24 months                  ki1000108-IRC              INDIA                          3                   0        8     236
6-24 months                  ki1000108-IRC              INDIA                          3                   1        8     236
6-24 months                  ki1000108-IRC              INDIA                          4                   0        5     236
6-24 months                  ki1000108-IRC              INDIA                          4                   1        7     236
6-24 months                  ki1000108-IRC              INDIA                          5                   0        4     236
6-24 months                  ki1000108-IRC              INDIA                          5                   1        6     236
6-24 months                  ki1000108-IRC              INDIA                          6                   0       16     236
6-24 months                  ki1000108-IRC              INDIA                          6                   1        7     236
6-24 months                  ki1000108-IRC              INDIA                          7                   0       14     236
6-24 months                  ki1000108-IRC              INDIA                          7                   1        6     236
6-24 months                  ki1000108-IRC              INDIA                          8                   0       22     236
6-24 months                  ki1000108-IRC              INDIA                          8                   1       10     236
6-24 months                  ki1000108-IRC              INDIA                          9                   0        9     236
6-24 months                  ki1000108-IRC              INDIA                          9                   1        6     236
6-24 months                  ki1000108-IRC              INDIA                          10                  0       19     236
6-24 months                  ki1000108-IRC              INDIA                          10                  1        5     236
6-24 months                  ki1000108-IRC              INDIA                          11                  0       17     236
6-24 months                  ki1000108-IRC              INDIA                          11                  1        9     236
6-24 months                  ki1000108-IRC              INDIA                          12                  0       14     236
6-24 months                  ki1000108-IRC              INDIA                          12                  1        9     236
6-24 months                  ki1000109-EE               PAKISTAN                       1                   0        4      97
6-24 months                  ki1000109-EE               PAKISTAN                       1                   1       13      97
6-24 months                  ki1000109-EE               PAKISTAN                       2                   0        9      97
6-24 months                  ki1000109-EE               PAKISTAN                       2                   1       13      97
6-24 months                  ki1000109-EE               PAKISTAN                       3                   0        4      97
6-24 months                  ki1000109-EE               PAKISTAN                       3                   1       10      97
6-24 months                  ki1000109-EE               PAKISTAN                       4                   0        2      97
6-24 months                  ki1000109-EE               PAKISTAN                       4                   1        5      97
6-24 months                  ki1000109-EE               PAKISTAN                       5                   0        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       5                   1        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       6                   0        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       6                   1        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       7                   0        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       7                   1        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       8                   0        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       8                   1        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       9                   0        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       9                   1        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       10                  0        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       10                  1        0      97
6-24 months                  ki1000109-EE               PAKISTAN                       11                  0        4      97
6-24 months                  ki1000109-EE               PAKISTAN                       11                  1        7      97
6-24 months                  ki1000109-EE               PAKISTAN                       12                  0        8      97
6-24 months                  ki1000109-EE               PAKISTAN                       12                  1       18      97
6-24 months                  ki1000109-ResPak           PAKISTAN                       1                   0        0      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       1                   1        2      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       2                   0        4      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       2                   1        2      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       3                   0        3      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       3                   1        1      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       4                   0        6      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       4                   1        1      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       5                   0       14      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       5                   1        1      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       6                   0       12      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       6                   1        2      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       7                   0        9      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       7                   1        1      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       8                   0       11      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       8                   1        5      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       9                   0       11      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       9                   1        1      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       10                  0        5      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       10                  1        1      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       11                  0        2      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       11                  1        0      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       12                  0        1      95
6-24 months                  ki1000109-ResPak           PAKISTAN                       12                  1        0      95
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          1                   0       23     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          1                   1       31     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          2                   0       28     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          2                   1       22     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          3                   0       29     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          3                   1       20     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          4                   0       20     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          4                   1       27     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          5                   0       26     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          5                   1       24     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          6                   0       35     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          6                   1       27     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          7                   0       28     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          7                   1       30     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          8                   0       30     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          8                   1       48     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          9                   0       61     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          9                   1       56     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          10                  0       38     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          10                  1       51     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          11                  0       42     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          11                  1       40     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          12                  0       44     813
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          12                  1       33     813
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          1                   0        4     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          1                   1       25     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          2                   0        7     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          2                   1       16     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          3                   0        5     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          3                   1       13     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          4                   0        3     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          4                   1       16     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          5                   0        6     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          5                   1       13     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          6                   0        8     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          6                   1       17     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          7                   0        3     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          7                   1        7     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          8                   0        0     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          8                   1        0     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          9                   0        0     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          9                   1        8     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          10                  0        3     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          10                  1       13     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          11                  0        9     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          11                  1       25     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          12                  0       11     243
6-24 months                  ki1000304b-SAS-FoodSuppl   INDIA                          12                  1       31     243
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     1                   0       13     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     1                   1       14     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     2                   0       13     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     2                   1       18     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     3                   0       17     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     3                   1       21     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     4                   0       11     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     4                   1       20     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     5                   0       13     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     5                   1       18     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     6                   0        9     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     6                   1       13     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     7                   0       12     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     7                   1       11     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     8                   0        9     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     8                   1       16     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     9                   0       10     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     9                   1        9     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     10                  0       14     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     10                  1       19     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     11                  0       11     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     11                  1       16     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     12                  0       15     345
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     12                  1       23     345
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                   0      121    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   1                   1       34    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                   0       86    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   2                   1       26    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                   0      101    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   3                   1       28    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                   0       80    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   4                   1       33    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   5                   0       94    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   5                   1       32    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   6                   0       78    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   6                   1       25    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   7                   0       80    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   7                   1       28    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   8                   0      106    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   8                   1       31    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   9                   0      137    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   9                   1       20    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   10                  0      121    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   10                  1       39    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   11                  0      112    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   11                  1       28    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   12                  0      124    1602
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   12                  1       38    1602
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      1                   0        6     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      1                   1        5     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      2                   0        8     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      2                   1        6     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      3                   0        3     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      3                   1        8     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      4                   0        9     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      4                   1        8     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      5                   0       15     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      5                   1       10     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      6                   0       15     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      6                   1       11     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      7                   0       11     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      7                   1        5     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      8                   0       10     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      8                   1        3     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      9                   0       17     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      9                   1        5     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      10                  0       10     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      10                  1        6     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      11                  0       13     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      11                  1        6     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      12                  0        4     195
6-24 months                  ki1112895-Guatemala BSC    GUATEMALA                      12                  1        1     195
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   1                   0      157    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   1                   1       82    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   2                   0      121    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   2                   1       87    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   3                   0      142    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   3                   1       72    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   4                   0      114    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   4                   1       69    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   5                   0      156    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   5                   1      101    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   6                   0      235    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   6                   1      131    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   7                   0      267    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   7                   1      144    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   8                   0      229    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   8                   1      132    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   9                   0      179    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   9                   1      116    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   10                  0      255    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   10                  1      117    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   11                  0      123    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   11                  1       74    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   12                  0      104    3265
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   12                  1       58    3265
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          1                   0        2     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          1                   1        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          2                   0        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          2                   1        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          3                   0        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          3                   1        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          4                   0        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          4                   1        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          5                   0        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          5                   1        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          6                   0        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          6                   1        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          7                   0       32     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          7                   1       60     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          8                   0       76     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          8                   1       95     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          9                   0       68     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          9                   1       82     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          10                  0        8     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          10                  1        1     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          11                  0        0     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          11                  1        1     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          12                  0        1     426
6-24 months                  ki1113344-GMS-Nepal        NEPAL                          12                  1        0     426
6-24 months                  ki1114097-CMIN             BANGLADESH                     1                   0        2     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     1                   1        7     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     2                   0        3     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     2                   1       10     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     3                   0        6     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     3                   1        6     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     4                   0        2     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     4                   1        7     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     5                   0        3     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     5                   1        9     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     6                   0        1     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     6                   1        7     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     7                   0        2     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     7                   1        4     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     8                   0        2     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     8                   1        7     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     9                   0        1     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     9                   1        5     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     10                  0        2     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     10                  1        4     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     11                  0        0     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     11                  1        0     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     12                  0        8     111
6-24 months                  ki1114097-CMIN             BANGLADESH                     12                  1       13     111
6-24 months                  ki1114097-CMIN             BRAZIL                         1                   0        8     104
6-24 months                  ki1114097-CMIN             BRAZIL                         1                   1        4     104
6-24 months                  ki1114097-CMIN             BRAZIL                         2                   0        3     104
6-24 months                  ki1114097-CMIN             BRAZIL                         2                   1        3     104
6-24 months                  ki1114097-CMIN             BRAZIL                         3                   0       10     104
6-24 months                  ki1114097-CMIN             BRAZIL                         3                   1        3     104
6-24 months                  ki1114097-CMIN             BRAZIL                         4                   0        9     104
6-24 months                  ki1114097-CMIN             BRAZIL                         4                   1        1     104
6-24 months                  ki1114097-CMIN             BRAZIL                         5                   0        3     104
6-24 months                  ki1114097-CMIN             BRAZIL                         5                   1        2     104
6-24 months                  ki1114097-CMIN             BRAZIL                         6                   0        2     104
6-24 months                  ki1114097-CMIN             BRAZIL                         6                   1        2     104
6-24 months                  ki1114097-CMIN             BRAZIL                         7                   0        3     104
6-24 months                  ki1114097-CMIN             BRAZIL                         7                   1        0     104
6-24 months                  ki1114097-CMIN             BRAZIL                         8                   0       10     104
6-24 months                  ki1114097-CMIN             BRAZIL                         8                   1        2     104
6-24 months                  ki1114097-CMIN             BRAZIL                         9                   0        6     104
6-24 months                  ki1114097-CMIN             BRAZIL                         9                   1        2     104
6-24 months                  ki1114097-CMIN             BRAZIL                         10                  0       10     104
6-24 months                  ki1114097-CMIN             BRAZIL                         10                  1        2     104
6-24 months                  ki1114097-CMIN             BRAZIL                         11                  0       10     104
6-24 months                  ki1114097-CMIN             BRAZIL                         11                  1        1     104
6-24 months                  ki1114097-CMIN             BRAZIL                         12                  0        5     104
6-24 months                  ki1114097-CMIN             BRAZIL                         12                  1        3     104
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  1                   0       27    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  1                   1       13    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  2                   0       85    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  2                   1       56    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  3                   0       86    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  3                   1       57    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  4                   0      143    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  4                   1      111    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  5                   0      112    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  5                   1       56    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  6                   0       63    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  6                   1       23    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  7                   0       50    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  7                   1       40    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  8                   0       51    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  8                   1       28    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  9                   0       90    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  9                   1       50    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  10                  0       39    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  10                  1       18    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  11                  0       39    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  11                  1       16    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  12                  0       61    1346
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  12                  1       32    1346
6-24 months                  ki1114097-CMIN             PERU                           1                   0       34     797
6-24 months                  ki1114097-CMIN             PERU                           1                   1        8     797
6-24 months                  ki1114097-CMIN             PERU                           2                   0       84     797
6-24 months                  ki1114097-CMIN             PERU                           2                   1       78     797
6-24 months                  ki1114097-CMIN             PERU                           3                   0       78     797
6-24 months                  ki1114097-CMIN             PERU                           3                   1       43     797
6-24 months                  ki1114097-CMIN             PERU                           4                   0       42     797
6-24 months                  ki1114097-CMIN             PERU                           4                   1       19     797
6-24 months                  ki1114097-CMIN             PERU                           5                   0       50     797
6-24 months                  ki1114097-CMIN             PERU                           5                   1       24     797
6-24 months                  ki1114097-CMIN             PERU                           6                   0       37     797
6-24 months                  ki1114097-CMIN             PERU                           6                   1        8     797
6-24 months                  ki1114097-CMIN             PERU                           7                   0       34     797
6-24 months                  ki1114097-CMIN             PERU                           7                   1       15     797
6-24 months                  ki1114097-CMIN             PERU                           8                   0       47     797
6-24 months                  ki1114097-CMIN             PERU                           8                   1       21     797
6-24 months                  ki1114097-CMIN             PERU                           9                   0       30     797
6-24 months                  ki1114097-CMIN             PERU                           9                   1       13     797
6-24 months                  ki1114097-CMIN             PERU                           10                  0       18     797
6-24 months                  ki1114097-CMIN             PERU                           10                  1       11     797
6-24 months                  ki1114097-CMIN             PERU                           11                  0       39     797
6-24 months                  ki1114097-CMIN             PERU                           11                  1       23     797
6-24 months                  ki1114097-CMIN             PERU                           12                  0       29     797
6-24 months                  ki1114097-CMIN             PERU                           12                  1       12     797
6-24 months                  ki1114097-CONTENT          PERU                           1                   0        8     167
6-24 months                  ki1114097-CONTENT          PERU                           1                   1        0     167
6-24 months                  ki1114097-CONTENT          PERU                           2                   0       11     167
6-24 months                  ki1114097-CONTENT          PERU                           2                   1        2     167
6-24 months                  ki1114097-CONTENT          PERU                           3                   0       24     167
6-24 months                  ki1114097-CONTENT          PERU                           3                   1        0     167
6-24 months                  ki1114097-CONTENT          PERU                           4                   0        9     167
6-24 months                  ki1114097-CONTENT          PERU                           4                   1        2     167
6-24 months                  ki1114097-CONTENT          PERU                           5                   0       17     167
6-24 months                  ki1114097-CONTENT          PERU                           5                   1        1     167
6-24 months                  ki1114097-CONTENT          PERU                           6                   0        9     167
6-24 months                  ki1114097-CONTENT          PERU                           6                   1        1     167
6-24 months                  ki1114097-CONTENT          PERU                           7                   0       10     167
6-24 months                  ki1114097-CONTENT          PERU                           7                   1        2     167
6-24 months                  ki1114097-CONTENT          PERU                           8                   0       19     167
6-24 months                  ki1114097-CONTENT          PERU                           8                   1        1     167
6-24 months                  ki1114097-CONTENT          PERU                           9                   0       12     167
6-24 months                  ki1114097-CONTENT          PERU                           9                   1        1     167
6-24 months                  ki1114097-CONTENT          PERU                           10                  0       15     167
6-24 months                  ki1114097-CONTENT          PERU                           10                  1        4     167
6-24 months                  ki1114097-CONTENT          PERU                           11                  0       12     167
6-24 months                  ki1114097-CONTENT          PERU                           11                  1        0     167
6-24 months                  ki1114097-CONTENT          PERU                           12                  0        6     167
6-24 months                  ki1114097-CONTENT          PERU                           12                  1        1     167
6-24 months                  ki1119695-PROBIT           BELARUS                        1                   0      929   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        1                   1       93   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        2                   0      775   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        2                   1      100   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        3                   0      950   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        3                   1      107   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        4                   0      944   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        4                   1       71   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        5                   0      957   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        5                   1       72   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        6                   0     1022   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        6                   1       76   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        7                   0     1242   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        7                   1       84   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        8                   0     1353   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        8                   1       94   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        9                   0     1312   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        9                   1       85   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        10                  0     1466   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        10                  1      116   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        11                  0     1394   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        11                  1      108   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        12                  0     1458   14951
6-24 months                  ki1119695-PROBIT           BELARUS                        12                  1      143   14951
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       1                   0      584    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       1                   1      206    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       2                   0      446    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       2                   1      153    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       3                   0      476    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       3                   1      183    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       4                   0      456    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       4                   1      143    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       5                   0      396    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       5                   1      135    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       6                   0      465    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       6                   1      127    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       7                   0      490    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       7                   1      142    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       8                   0      494    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       8                   1      153    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       9                   0      616    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       9                   1      189    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       10                  0      457    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       10                  1      153    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       11                  0      524    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       11                  1      165    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       12                  0      584    7940
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       12                  1      203    7940
6-24 months                  ki1148112-LCNI-5           MALAWI                         1                   0       22     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         1                   1       31     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         2                   0       45     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         2                   1       53     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         3                   0       30     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         3                   1       45     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         4                   0       29     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         4                   1       58     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         5                   0       38     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         5                   1       61     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         6                   0       29     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         6                   1       52     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         7                   0       24     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         7                   1       36     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         8                   0       16     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         8                   1       25     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         9                   0       11     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         9                   1       16     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         10                  0       16     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         10                  1       16     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         11                  0       21     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         11                  1       25     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         12                  0       11     730
6-24 months                  ki1148112-LCNI-5           MALAWI                         12                  1       20     730
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     1                   0      624   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     1                   1      195   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     2                   0      550   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     2                   1      213   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     3                   0      741   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     3                   1      197   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     4                   0      639   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     4                   1      162   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     5                   0      631   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     5                   1      153   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     6                   0      604   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     6                   1      193   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     7                   0      675   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     7                   1      187   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     8                   0      771   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     8                   1      187   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     9                   0      775   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     9                   1      206   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     10                  0      785   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     10                  1      188   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     11                  0      727   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     11                  1      201   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     12                  0      716   10526
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     12                  1      206   10526
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     1                   0       26    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     1                   1       15    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     2                   0      150    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     2                   1       67    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     3                   0      183    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     3                   1       97    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     4                   0      360    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     4                   1      244    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     5                   0      240    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     5                   1      154    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     6                   0      184    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     6                   1      111    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     7                   0      363    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     7                   1      231    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     8                   0      232    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     8                   1      145    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     9                   0      247    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     9                   1      154    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     10                  0      162    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     10                  1       83    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     11                  0       85    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     11                  1       52    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     12                  0       38    3649
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     12                  1       26    3649


The following strata were considered:

* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months (no birth st.), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki1000108-IRC, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-24 months (no birth st.), studyid: ki1000109-ResPak, country: PAKISTAN
* agecat: 0-24 months (no birth st.), studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki1017093-NIH-Birth, country: BANGLADESH
* agecat: 0-24 months (no birth st.), studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months (no birth st.), studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 0-24 months (no birth st.), studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* agecat: 0-24 months (no birth st.), studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CMIN, country: BRAZIL
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CMIN, country: GUINEA-BISSAU
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CMIN, country: PERU
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-24 months (no birth st.), studyid: ki1119695-PROBIT, country: BELARUS
* agecat: 0-24 months (no birth st.), studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* agecat: 0-24 months (no birth st.), studyid: ki1148112-LCNI-5, country: MALAWI
* agecat: 0-24 months (no birth st.), studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 0-24 months (no birth st.), studyid: kiGH5241-JiVitA-4, country: BANGLADESH
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months (no birth st.), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki1000108-IRC, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-6 months (no birth st.), studyid: ki1000109-ResPak, country: PAKISTAN
* agecat: 0-6 months (no birth st.), studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki1017093-NIH-Birth, country: BANGLADESH
* agecat: 0-6 months (no birth st.), studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months (no birth st.), studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 0-6 months (no birth st.), studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: BRAZIL
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: GUINEA-BISSAU
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: PERU
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-6 months (no birth st.), studyid: ki1119695-PROBIT, country: BELARUS
* agecat: 0-6 months (no birth st.), studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* agecat: 0-6 months (no birth st.), studyid: ki1148112-LCNI-5, country: MALAWI
* agecat: 0-6 months (no birth st.), studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 0-6 months (no birth st.), studyid: kiGH5241-JiVitA-4, country: BANGLADESH
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
* agecat: 6-24 months, studyid: ki1000109-ResPak, country: PAKISTAN
* agecat: 6-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 6-24 months, studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 6-24 months, studyid: ki1017093-NIH-Birth, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 6-24 months, studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 6-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* agecat: 6-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1114097-CMIN, country: BRAZIL
* agecat: 6-24 months, studyid: ki1114097-CMIN, country: GUINEA-BISSAU
* agecat: 6-24 months, studyid: ki1114097-CMIN, country: PERU
* agecat: 6-24 months, studyid: ki1114097-CONTENT, country: PERU
* agecat: 6-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* agecat: 6-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-3, country: BANGLADESH
* agecat: 6-24 months, studyid: kiGH5241-JiVitA-4, country: BANGLADESH

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-24 months (no birth st.), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-24 months (no birth st.), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki1000108-IRC, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-24 months (no birth st.), studyid: ki1000109-ResPak, country: PAKISTAN
* agecat: 0-24 months (no birth st.), studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 0-24 months (no birth st.), studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 0-24 months (no birth st.), studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CMIN, country: BRAZIL
* agecat: 0-24 months (no birth st.), studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BANGLADESH
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: BRAZIL
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: NEPAL
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: PERU
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: SOUTH AFRICA
* agecat: 0-6 months (no birth st.), studyid: ki0047075b-MAL-ED, country: TANZANIA, UNITED REPUBLIC OF
* agecat: 0-6 months (no birth st.), studyid: ki1000108-CMC-V-BCS-2002, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki1000109-EE, country: PAKISTAN
* agecat: 0-6 months (no birth st.), studyid: ki1000109-ResPak, country: PAKISTAN
* agecat: 0-6 months (no birth st.), studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 0-6 months (no birth st.), studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 0-6 months (no birth st.), studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: BRAZIL
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: GUINEA-BISSAU
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CMIN, country: PERU
* agecat: 0-6 months (no birth st.), studyid: ki1114097-CONTENT, country: PERU
* agecat: 0-6 months (no birth st.), studyid: ki1148112-LCNI-5, country: MALAWI
* agecat: 0-6 months (no birth st.), studyid: kiGH5241-JiVitA-4, country: BANGLADESH
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
* agecat: 6-24 months, studyid: ki1000109-ResPak, country: PAKISTAN
* agecat: 6-24 months, studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 6-24 months, studyid: ki1112895-Guatemala BSC, country: GUATEMALA
* agecat: 6-24 months, studyid: ki1113344-GMS-Nepal, country: NEPAL
* agecat: 6-24 months, studyid: ki1114097-CMIN, country: BANGLADESH
* agecat: 6-24 months, studyid: ki1114097-CMIN, country: BRAZIL
* agecat: 6-24 months, studyid: ki1114097-CONTENT, country: PERU

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness



```
## Warning in fold_fun(n, ...): n <= V so using leave-one-out CV

## Warning in fold_fun(n, ...): n <= V so using leave-one-out CV

## Warning in fold_fun(n, ...): n <= V so using leave-one-out CV
```




# Results Detail

## Results Plots
![](/tmp/a696d29e-131c-4ec7-824d-a28076dd1908/2b76e935-43d4-439e-9750-2e5f4a449d8b/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/a696d29e-131c-4ec7-824d-a28076dd1908/2b76e935-43d4-439e-9750-2e5f4a449d8b/REPORT_files/figure-html/plot_rr-1.png)<!-- -->


## Results Table

### Parameter: TSM


agecat                       studyid                    country                        intervention_level   baseline_level     estimate    ci_lower    ci_upper
---------------------------  -------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  ----------
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           optimal              NA                0.3654762   0.1555046   0.5754479
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                0.6148143   0.4776169   0.7520116
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                0.6489424   0.5046553   0.7932296
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                0.2871958   0.2223132   0.3520784
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   optimal              NA                0.2356351   0.1689201   0.3023501
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  optimal              NA                0.4328104   0.2821374   0.5834835
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           optimal              NA                0.1899153   0.0821592   0.2976713
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        optimal              NA                0.1472722   0.1160138   0.1785306
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                0.3158206   0.2886175   0.3430236
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         optimal              NA                0.2440617   0.0530541   0.4350694
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                0.2340255   0.2116629   0.2563881
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     optimal              NA                0.4664294   0.3779261   0.5549326
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          optimal              NA                0.3280861   0.1711432   0.4850290
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                0.1769937   0.0585196   0.2954678
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                0.1950913   0.0705574   0.3196252
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                0.0858874   0.0440124   0.1277624
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        optimal              NA                0.0711717   0.0508466   0.0914969
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                0.1622459   0.1399434   0.1845484
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                0.0878676   0.0662001   0.1095352
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                0.6061265   0.4719180   0.7403349
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                0.6811087   0.5009018   0.8613155
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                0.1270645   0.0744966   0.1796324
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   optimal              NA                0.3395674   0.0050874   0.6740473
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  optimal              NA                0.3405587   0.2351208   0.4459965
6-24 months                  ki1114097-CMIN             PERU                           optimal              NA                0.2499580   0.1135081   0.3864080
6-24 months                  ki1119695-PROBIT           BELARUS                        optimal              NA                0.0787967   0.0566865   0.1009070
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                0.2243028   0.1904307   0.2581748
6-24 months                  ki1148112-LCNI-5           MALAWI                         optimal              NA                0.5889915   0.4133531   0.7646299
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                0.2323445   0.2024400   0.2622491
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     optimal              NA                0.3105803   0.2443270   0.3768336


### Parameter: E(Y)


agecat                       studyid                    country                        intervention_level   baseline_level     estimate    ci_lower    ci_upper
---------------------------  -------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  ----------
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           observed             NA                0.5676692   0.5080232   0.6273151
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          observed             NA                0.5660550   0.5086421   0.6234680
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     observed             NA                0.6018868   0.5601729   0.6436007
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   observed             NA                0.2988814   0.2798990   0.3178639
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   observed             NA                0.1780497   0.1518612   0.2042383
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  observed             NA                0.3084337   0.2827691   0.3340984
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           observed             NA                0.2976339   0.2659904   0.3292773
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        observed             NA                0.1597778   0.1408215   0.1787342
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       observed             NA                0.3252945   0.3171024   0.3334866
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         observed             NA                0.4256121   0.3835181   0.4677060
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     observed             NA                0.2535059   0.2457125   0.2612993
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     observed             NA                0.4135358   0.3953404   0.4317312
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          observed             NA                0.3444444   0.2952897   0.3935992
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          observed             NA                0.1928375   0.1691727   0.2165022
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     observed             NA                0.2283019   0.1925336   0.2640702
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   observed             NA                0.1369128   0.1226581   0.1511674
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        observed             NA                0.0912784   0.0781588   0.1043979
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       observed             NA                0.1706248   0.1640425   0.1772071
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     observed             NA                0.1311262   0.1254945   0.1367579
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          observed             NA                0.5030750   0.4588491   0.5473009
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     observed             NA                0.5739130   0.5216565   0.6261696
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   observed             NA                0.2259675   0.2054816   0.2464534
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   observed             NA                0.3623277   0.3130786   0.4115769
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  observed             NA                0.3714710   0.3456477   0.3972943
6-24 months                  ki1114097-CMIN             PERU                           observed             NA                0.3450439   0.3120195   0.3780683
6-24 months                  ki1119695-PROBIT           BELARUS                        observed             NA                0.0768510   0.0628857   0.0908164
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       observed             NA                0.2458438   0.2363722   0.2553155
6-24 months                  ki1148112-LCNI-5           MALAWI                         observed             NA                0.6000000   0.5644377   0.6355623
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     observed             NA                0.2173665   0.2079947   0.2267384
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     observed             NA                0.3779118   0.3593176   0.3965059


### Parameter: RR


agecat                       studyid                    country                        intervention_level   baseline_level     estimate    ci_lower    ci_upper
---------------------------  -------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  ----------
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           observed             optimal           1.5532314   0.8925023   2.7031052
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          observed             optimal           0.9206927   0.7485396   1.1324385
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     observed             optimal           0.9274888   0.7489312   1.1486173
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   observed             optimal           1.0406887   0.8388843   1.2910398
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   observed             optimal           0.7556164   0.6020741   0.9483155
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  observed             optimal           0.7126301   0.5078653   0.9999534
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           observed             optimal           1.5671930   0.9007726   2.7266526
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        observed             optimal           1.0849148   0.9216347   1.2771222
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       observed             optimal           1.0299978   0.9485404   1.1184505
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         observed             optimal           1.7438706   0.8059147   3.7734573
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     observed             optimal           1.0832405   0.9903067   1.1848954
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     observed             optimal           0.8865989   0.7340951   1.0707844
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          observed             optimal           1.0498600   0.6678540   1.6503697
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          observed             optimal           1.0895160   0.5408153   2.1949180
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     observed             optimal           1.1702311   0.6380381   2.1463308
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   observed             optimal           1.5940953   0.9915466   2.5628043
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        observed             optimal           1.2825088   1.0037428   1.6386956
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       observed             optimal           1.0516430   0.9217216   1.1998774
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     observed             optimal           1.4923149   1.1722256   1.8998082
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          observed             optimal           0.8299836   0.6619977   1.0405969
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     observed             optimal           0.8426160   0.6484007   1.0950045
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   observed             optimal           1.7783685   1.1910611   2.6552749
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   observed             optimal           1.0670275   0.4429999   2.5700856
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  observed             optimal           1.0907695   0.8068470   1.4746018
6-24 months                  ki1114097-CMIN             PERU                           observed             optimal           1.3804074   0.8102814   2.3516826
6-24 months                  ki1119695-PROBIT           BELARUS                        observed             optimal           0.9753078   0.7895416   1.2047817
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       observed             optimal           1.0960356   0.9475998   1.2677230
6-24 months                  ki1148112-LCNI-5           MALAWI                         observed             optimal           1.0186904   0.7616343   1.3625044
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     observed             optimal           0.9355353   0.8299112   1.0546024
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     observed             optimal           1.2167924   0.9894241   1.4964096


### Parameter: PAR


agecat                       studyid                    country                        intervention_level   baseline_level      estimate     ci_lower     ci_upper
---------------------------  -------------------------  -----------------------------  -------------------  ---------------  -----------  -----------  -----------
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           optimal              NA                 0.2021929    0.0007814    0.4036045
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                -0.0487592   -0.1757295    0.0782110
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                -0.0470556   -0.1857394    0.0916281
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                 0.0116856   -0.0502137    0.0735850
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   optimal              NA                -0.0575853   -0.1126373   -0.0025334
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  optimal              NA                -0.1243767   -0.2712664    0.0225130
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           optimal              NA                 0.1077186    0.0023063    0.2131310
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        optimal              NA                 0.0125056   -0.0113937    0.0364048
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                 0.0094739   -0.0165470    0.0354949
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         optimal              NA                 0.1815503   -0.0068805    0.3699812
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                 0.0194804   -0.0015044    0.0404652
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     optimal              NA                -0.0528936   -0.1407460    0.0349588
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          optimal              NA                 0.0163584   -0.1319977    0.1647144
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                 0.0158438   -0.1087893    0.1404768
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                 0.0332106   -0.0848267    0.1512479
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                 0.0510253    0.0099786    0.0920721
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        optimal              NA                 0.0201066    0.0024596    0.0377537
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                 0.0083789   -0.0130177    0.0297754
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                 0.0432585    0.0220245    0.0644926
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                -0.1030515   -0.2381661    0.0320631
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                -0.1071956   -0.2844925    0.0701012
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                 0.0989030    0.0474605    0.1503455
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   optimal              NA                 0.0227604   -0.2734299    0.3189506
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  optimal              NA                 0.0309123   -0.0717842    0.1336089
6-24 months                  ki1114097-CMIN             PERU                           optimal              NA                 0.0950859   -0.0379435    0.2281153
6-24 months                  ki1119695-PROBIT           BELARUS                        optimal              NA                -0.0019457   -0.0186041    0.0147128
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                 0.0215411   -0.0111000    0.0541822
6-24 months                  ki1148112-LCNI-5           MALAWI                         optimal              NA                 0.0110085   -0.1602595    0.1822764
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                -0.0149780   -0.0428426    0.0128866
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     optimal              NA                 0.0673315    0.0030509    0.1316120


### Parameter: PAF


agecat                       studyid                    country                        intervention_level   baseline_level      estimate     ci_lower     ci_upper
---------------------------  -------------------------  -----------------------------  -------------------  ---------------  -----------  -----------  -----------
0-24 months (no birth st.)   ki0047075b-MAL-ED          PERU                           optimal              NA                 0.3561809   -0.1204453    0.6300551
0-24 months (no birth st.)   ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                -0.0861387   -0.3359346    0.1169498
0-24 months (no birth st.)   ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                -0.0781802   -0.3352361    0.1293880
0-24 months (no birth st.)   ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                 0.0390979   -0.1920595    0.2254305
0-24 months (no birth st.)   ki1112895-iLiNS-Zinc       BURKINA FASO                   optimal              NA                -0.3234228   -0.6609252   -0.0545014
0-24 months (no birth st.)   ki1114097-CMIN             GUINEA-BISSAU                  optimal              NA                -0.4032526   -0.9690262   -0.0000466
0-24 months (no birth st.)   ki1114097-CMIN             PERU                           optimal              NA                 0.3619165   -0.1101582    0.6332499
0-24 months (no birth st.)   ki1119695-PROBIT           BELARUS                        optimal              NA                 0.0782686   -0.0850286    0.2169896
0-24 months (no birth st.)   ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                 0.0291241   -0.0542514    0.1059059
0-24 months (no birth st.)   ki1148112-LCNI-5           MALAWI                         optimal              NA                 0.4265630   -0.2408261    0.7349910
0-24 months (no birth st.)   kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                 0.0768439   -0.0097881    0.1560437
0-24 months (no birth st.)   kiGH5241-JiVitA-4          BANGLADESH                     optimal              NA                -0.1279058   -0.3622213    0.0661052
0-6 months (no birth st.)    ki1000108-IRC              INDIA                          optimal              NA                 0.0474920   -0.4973333    0.3940751
0-6 months (no birth st.)    ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                 0.0821613   -0.8490602    0.5444021
0-6 months (no birth st.)    ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                 0.1454679   -0.5673046    0.5340886
0-6 months (no birth st.)    ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                 0.3726849   -0.0085255    0.6098024
0-6 months (no birth st.)    ki1119695-PROBIT           BELARUS                        optimal              NA                 0.2202783    0.0037288    0.3897585
0-6 months (no birth st.)    ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                 0.0491070   -0.0849262    0.1665815
0-6 months (no birth st.)    kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                 0.3299001    0.1469219    0.4736311
6-24 months                  ki1000304b-SAS-CompFeed    INDIA                          optimal              NA                -0.2048431   -0.5105793    0.0390131
6-24 months                  ki1017093-NIH-Birth        BANGLADESH                     optimal              NA                -0.1867803   -0.5422563    0.0867618
6-24 months                  ki1066203-TanzaniaChild2   TANZANIA, UNITED REPUBLIC OF   optimal              NA                 0.4376869    0.1604125    0.6233912
6-24 months                  ki1112895-iLiNS-Zinc       BURKINA FASO                   optimal              NA                 0.0628170   -1.2573368    0.6109079
6-24 months                  ki1114097-CMIN             GUINEA-BISSAU                  optimal              NA                 0.0832160   -0.2393923    0.3218508
6-24 months                  ki1114097-CMIN             PERU                           optimal              NA                 0.2755762   -0.2341392    0.5747725
6-24 months                  ki1119695-PROBIT           BELARUS                        optimal              NA                -0.0253173   -0.2665577    0.1699741
6-24 months                  ki1126311-ZVITAMBO         ZIMBABWE                       optimal              NA                 0.0876209   -0.0552978    0.2111841
6-24 months                  ki1148112-LCNI-5           MALAWI                         optimal              NA                 0.0183474   -0.3129662    0.2660574
6-24 months                  kiGH5241-JiVitA-3          BANGLADESH                     optimal              NA                -0.0689067   -0.2049482    0.0517753
6-24 months                  kiGH5241-JiVitA-4          BANGLADESH                     optimal              NA                 0.1781671   -0.0106889    0.3317338