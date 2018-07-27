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
        value: FALSE        
      baseline_level:
        input: 'character'
        value: "[1,2)"
  output_directory:
    value: ''

---







## Methods
## Outcome Variable

**Outcome Variable:** stunted

## Predictor Variables

**Intervention Variable:** tr

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* perdiar6
* agecat
* studyid
* country

## Data Summary

perdiar6   agecat      studyid              country      tr         stunted   n_cell    n
---------  ----------  -------------------  -----------  --------  --------  -------  ---
Q1         6 months    ki1017093b-PROVIDE   BANGLADESH   Control          0        8   46
Q1         6 months    ki1017093b-PROVIDE   BANGLADESH   Control          1        2   46
Q1         6 months    ki1017093b-PROVIDE   BANGLADESH   Other            0       28   46
Q1         6 months    ki1017093b-PROVIDE   BANGLADESH   Other            1        8   46
Q1         24 months   ki1017093b-PROVIDE   BANGLADESH   Other            0        2    2


The following strata were considered:

* perdiar6: Q1, agecat: 24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* perdiar6: Q1, agecat: 6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH

### Dropped Strata

Some strata were dropped due to rare outcomes:

* perdiar6: Q1, agecat: 6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* perdiar6: Q1, agecat: 24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH


ALL STRATA DROPPED. JOB FINISHED















