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

**Outcome Variable:** wasted

## Predictor Variables

**Intervention Variable:** fhtcm

**Adjustment Set:**

* arm
* W_mage
* W_fage
* meducyrs
* feducyrs
* W_mhtcm
* W_mwtkg
* W_mbmi
* single
* delta_W_mage
* delta_W_fage
* delta_meducyrs
* delta_feducyrs
* delta_W_mhtcm
* delta_W_mwtkg
* delta_W_mbmi
* delta_single

## Stratifying Variables

The analysis was stratified on these variable(s):

* agecat
* studyid
* country

## Data Summary

agecat      studyid                    country     fhtcm           wasted   n_cell       n
----------  -------------------------  ----------  -------------  -------  -------  ------
Birth       ki1000304b-SAS-CompFeed    INDIA       >=167 cm             0       46      90
Birth       ki1000304b-SAS-CompFeed    INDIA       >=167 cm             1        0      90
Birth       ki1000304b-SAS-CompFeed    INDIA       <162 cm              0       20      90
Birth       ki1000304b-SAS-CompFeed    INDIA       <162 cm              1        0      90
Birth       ki1000304b-SAS-CompFeed    INDIA       [162-167) cm         0       24      90
Birth       ki1000304b-SAS-CompFeed    INDIA       [162-167) cm         1        0      90
Birth       ki1101329-Keneba           GAMBIA      >=167 cm             0      693    1079
Birth       ki1101329-Keneba           GAMBIA      >=167 cm             1       17    1079
Birth       ki1101329-Keneba           GAMBIA      <162 cm              0       80    1079
Birth       ki1101329-Keneba           GAMBIA      <162 cm              1        1    1079
Birth       ki1101329-Keneba           GAMBIA      [162-167) cm         0      285    1079
Birth       ki1101329-Keneba           GAMBIA      [162-167) cm         1        3    1079
Birth       ki1119695-PROBIT           BELARUS     >=167 cm             0     9273   12474
Birth       ki1119695-PROBIT           BELARUS     >=167 cm             1     2411   12474
Birth       ki1119695-PROBIT           BELARUS     <162 cm              0      130   12474
Birth       ki1119695-PROBIT           BELARUS     <162 cm              1       38   12474
Birth       ki1119695-PROBIT           BELARUS     [162-167) cm         0      478   12474
Birth       ki1119695-PROBIT           BELARUS     [162-167) cm         1      144   12474
Birth       ki1135781-COHORTS          GUATEMALA   >=167 cm             0       22     192
Birth       ki1135781-COHORTS          GUATEMALA   >=167 cm             1        4     192
Birth       ki1135781-COHORTS          GUATEMALA   <162 cm              0       92     192
Birth       ki1135781-COHORTS          GUATEMALA   <162 cm              1       20     192
Birth       ki1135781-COHORTS          GUATEMALA   [162-167) cm         0       42     192
Birth       ki1135781-COHORTS          GUATEMALA   [162-167) cm         1       12     192
6 months    ki1000304b-SAS-CompFeed    INDIA       >=167 cm             0      332     807
6 months    ki1000304b-SAS-CompFeed    INDIA       >=167 cm             1       38     807
6 months    ki1000304b-SAS-CompFeed    INDIA       <162 cm              0      170     807
6 months    ki1000304b-SAS-CompFeed    INDIA       <162 cm              1       23     807
6 months    ki1000304b-SAS-CompFeed    INDIA       [162-167) cm         0      212     807
6 months    ki1000304b-SAS-CompFeed    INDIA       [162-167) cm         1       32     807
6 months    ki1000304b-SAS-FoodSuppl   INDIA       >=167 cm             0       88     371
6 months    ki1000304b-SAS-FoodSuppl   INDIA       >=167 cm             1       14     371
6 months    ki1000304b-SAS-FoodSuppl   INDIA       <162 cm              0      115     371
6 months    ki1000304b-SAS-FoodSuppl   INDIA       <162 cm              1       33     371
6 months    ki1000304b-SAS-FoodSuppl   INDIA       [162-167) cm         0      101     371
6 months    ki1000304b-SAS-FoodSuppl   INDIA       [162-167) cm         1       20     371
6 months    ki1101329-Keneba           GAMBIA      >=167 cm             0      923    1510
6 months    ki1101329-Keneba           GAMBIA      >=167 cm             1       56    1510
6 months    ki1101329-Keneba           GAMBIA      <162 cm              0      104    1510
6 months    ki1101329-Keneba           GAMBIA      <162 cm              1        9    1510
6 months    ki1101329-Keneba           GAMBIA      [162-167) cm         0      397    1510
6 months    ki1101329-Keneba           GAMBIA      [162-167) cm         1       21    1510
6 months    ki1119695-PROBIT           BELARUS     >=167 cm             0    11053   11892
6 months    ki1119695-PROBIT           BELARUS     >=167 cm             1       90   11892
6 months    ki1119695-PROBIT           BELARUS     <162 cm              0      155   11892
6 months    ki1119695-PROBIT           BELARUS     <162 cm              1        1   11892
6 months    ki1119695-PROBIT           BELARUS     [162-167) cm         0      592   11892
6 months    ki1119695-PROBIT           BELARUS     [162-167) cm         1        1   11892
6 months    ki1135781-COHORTS          GUATEMALA   >=167 cm             0       44     336
6 months    ki1135781-COHORTS          GUATEMALA   >=167 cm             1        0     336
6 months    ki1135781-COHORTS          GUATEMALA   <162 cm              0      190     336
6 months    ki1135781-COHORTS          GUATEMALA   <162 cm              1        8     336
6 months    ki1135781-COHORTS          GUATEMALA   [162-167) cm         0       89     336
6 months    ki1135781-COHORTS          GUATEMALA   [162-167) cm         1        5     336
24 months   ki1101329-Keneba           GAMBIA      >=167 cm             0      743    1298
24 months   ki1101329-Keneba           GAMBIA      >=167 cm             1       80    1298
24 months   ki1101329-Keneba           GAMBIA      <162 cm              0       79    1298
24 months   ki1101329-Keneba           GAMBIA      <162 cm              1       17    1298
24 months   ki1101329-Keneba           GAMBIA      [162-167) cm         0      344    1298
24 months   ki1101329-Keneba           GAMBIA      [162-167) cm         1       35    1298
24 months   ki1119695-PROBIT           BELARUS     >=167 cm             0     3352    3609
24 months   ki1119695-PROBIT           BELARUS     >=167 cm             1       35    3609
24 months   ki1119695-PROBIT           BELARUS     <162 cm              0       50    3609
24 months   ki1119695-PROBIT           BELARUS     <162 cm              1        2    3609
24 months   ki1119695-PROBIT           BELARUS     [162-167) cm         0      168    3609
24 months   ki1119695-PROBIT           BELARUS     [162-167) cm         1        2    3609
24 months   ki1135781-COHORTS          GUATEMALA   >=167 cm             0       69     532
24 months   ki1135781-COHORTS          GUATEMALA   >=167 cm             1        3     532
24 months   ki1135781-COHORTS          GUATEMALA   <162 cm              0      292     532
24 months   ki1135781-COHORTS          GUATEMALA   <162 cm              1       19     532
24 months   ki1135781-COHORTS          GUATEMALA   [162-167) cm         0      140     532
24 months   ki1135781-COHORTS          GUATEMALA   [162-167) cm         1        9     532


The following strata were considered:

* agecat: 24 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 24 months, studyid: ki1119695-PROBIT, country: BELARUS
* agecat: 24 months, studyid: ki1135781-COHORTS, country: GUATEMALA
* agecat: 6 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: 6 months, studyid: ki1000304b-SAS-FoodSuppl, country: INDIA
* agecat: 6 months, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: 6 months, studyid: ki1119695-PROBIT, country: BELARUS
* agecat: 6 months, studyid: ki1135781-COHORTS, country: GUATEMALA
* agecat: Birth, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: Birth, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: Birth, studyid: ki1119695-PROBIT, country: BELARUS
* agecat: Birth, studyid: ki1135781-COHORTS, country: GUATEMALA

### Dropped Strata

Some strata were dropped due to rare outcomes:

* agecat: Birth, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* agecat: Birth, studyid: ki1101329-Keneba, country: GAMBIA
* agecat: Birth, studyid: ki1135781-COHORTS, country: GUATEMALA
* agecat: 6 months, studyid: ki1119695-PROBIT, country: BELARUS
* agecat: 6 months, studyid: ki1135781-COHORTS, country: GUATEMALA
* agecat: 24 months, studyid: ki1119695-PROBIT, country: BELARUS
* agecat: 24 months, studyid: ki1135781-COHORTS, country: GUATEMALA

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
![](/tmp/c62c9e40-f9af-4a04-990f-6092969f6a00/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/c62c9e40-f9af-4a04-990f-6092969f6a00/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/c62c9e40-f9af-4a04-990f-6092969f6a00/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/c62c9e40-f9af-4a04-990f-6092969f6a00/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


agecat      studyid                    country   intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  -------------------------  --------  -------------------  ---------------  ----------  ----------  ----------
Birth       ki1119695-PROBIT           BELARUS   >=167 cm             NA                0.2062289   0.1404124   0.2720453
Birth       ki1119695-PROBIT           BELARUS   <162 cm              NA                0.1351255   0.1030549   0.1671961
Birth       ki1119695-PROBIT           BELARUS   [162-167) cm         NA                0.2390279   0.1766092   0.3014467
6 months    ki1000304b-SAS-CompFeed    INDIA     >=167 cm             NA                0.0995400   0.0734468   0.1256332
6 months    ki1000304b-SAS-CompFeed    INDIA     <162 cm              NA                0.0997044   0.0417606   0.1576481
6 months    ki1000304b-SAS-CompFeed    INDIA     [162-167) cm         NA                0.1207916   0.0796225   0.1619607
6 months    ki1000304b-SAS-FoodSuppl   INDIA     >=167 cm             NA                0.1375656   0.0712758   0.2038554
6 months    ki1000304b-SAS-FoodSuppl   INDIA     <162 cm              NA                0.2236554   0.1571259   0.2901850
6 months    ki1000304b-SAS-FoodSuppl   INDIA     [162-167) cm         NA                0.1642904   0.0978346   0.2307463
6 months    ki1101329-Keneba           GAMBIA    >=167 cm             NA                0.0572012   0.0426496   0.0717529
6 months    ki1101329-Keneba           GAMBIA    <162 cm              NA                0.0796460   0.0297102   0.1295818
6 months    ki1101329-Keneba           GAMBIA    [162-167) cm         NA                0.0502392   0.0292917   0.0711867
24 months   ki1101329-Keneba           GAMBIA    >=167 cm             NA                0.0992982   0.0787090   0.1198875
24 months   ki1101329-Keneba           GAMBIA    <162 cm              NA                0.2118744   0.1467184   0.2770303
24 months   ki1101329-Keneba           GAMBIA    [162-167) cm         NA                0.1023423   0.0718148   0.1328699


### Parameter: E(Y)


agecat      studyid                    country   intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  -------------------------  --------  -------------------  ---------------  ----------  ----------  ----------
Birth       ki1119695-PROBIT           BELARUS   NA                   NA                0.2078724   0.1422510   0.2734938
6 months    ki1000304b-SAS-CompFeed    INDIA     NA                   NA                0.1152416   0.0868962   0.1435870
6 months    ki1000304b-SAS-FoodSuppl   INDIA     NA                   NA                0.1805930   0.1413965   0.2197895
6 months    ki1101329-Keneba           GAMBIA    NA                   NA                0.0569536   0.0452605   0.0686468
24 months   ki1101329-Keneba           GAMBIA    NA                   NA                0.1016949   0.0852459   0.1181439


### Parameter: RR


agecat      studyid                    country   intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  -------------------------  --------  -------------------  ---------------  ----------  ----------  ----------
Birth       ki1119695-PROBIT           BELARUS   >=167 cm             >=167 cm          1.0000000   1.0000000   1.0000000
Birth       ki1119695-PROBIT           BELARUS   <162 cm              >=167 cm          0.6552211   0.4837150   0.8875364
Birth       ki1119695-PROBIT           BELARUS   [162-167) cm         >=167 cm          1.1590421   0.9786604   1.3726709
6 months    ki1000304b-SAS-CompFeed    INDIA     >=167 cm             >=167 cm          1.0000000   1.0000000   1.0000000
6 months    ki1000304b-SAS-CompFeed    INDIA     <162 cm              >=167 cm          1.0016511   0.5399695   1.8580769
6 months    ki1000304b-SAS-CompFeed    INDIA     [162-167) cm         >=167 cm          1.2134976   0.8049315   1.8294432
6 months    ki1000304b-SAS-FoodSuppl   INDIA     >=167 cm             >=167 cm          1.0000000   1.0000000   1.0000000
6 months    ki1000304b-SAS-FoodSuppl   INDIA     <162 cm              >=167 cm          1.6258094   0.9250531   2.8574103
6 months    ki1000304b-SAS-FoodSuppl   INDIA     [162-167) cm         >=167 cm          1.1942699   0.6370964   2.2387204
6 months    ki1101329-Keneba           GAMBIA    >=167 cm             >=167 cm          1.0000000   1.0000000   1.0000000
6 months    ki1101329-Keneba           GAMBIA    <162 cm              >=167 cm          1.3923831   0.7077955   2.7391114
6 months    ki1101329-Keneba           GAMBIA    [162-167) cm         >=167 cm          0.8782895   0.5389064   1.4314033
24 months   ki1101329-Keneba           GAMBIA    >=167 cm             >=167 cm          1.0000000   1.0000000   1.0000000
24 months   ki1101329-Keneba           GAMBIA    <162 cm              >=167 cm          2.1337172   1.4738782   3.0889589
24 months   ki1101329-Keneba           GAMBIA    [162-167) cm         >=167 cm          1.0306557   0.7175964   1.4802907


### Parameter: PAR


agecat      studyid                    country   intervention_level   baseline_level      estimate     ci_lower    ci_upper
----------  -------------------------  --------  -------------------  ---------------  -----------  -----------  ----------
Birth       ki1119695-PROBIT           BELARUS   >=167 cm             NA                 0.0016435   -0.0001790   0.0034660
6 months    ki1000304b-SAS-CompFeed    INDIA     >=167 cm             NA                 0.0157016   -0.0102637   0.0416670
6 months    ki1000304b-SAS-FoodSuppl   INDIA     >=167 cm             NA                 0.0430274   -0.0159614   0.1020162
6 months    ki1101329-Keneba           GAMBIA    >=167 cm             NA                -0.0002476   -0.0088444   0.0083492
24 months   ki1101329-Keneba           GAMBIA    >=167 cm             NA                 0.0023967   -0.0106367   0.0154300


### Parameter: PAF


agecat      studyid                    country   intervention_level   baseline_level      estimate     ci_lower    ci_upper
----------  -------------------------  --------  -------------------  ---------------  -----------  -----------  ----------
Birth       ki1119695-PROBIT           BELARUS   >=167 cm             NA                 0.0079064   -0.0014747   0.0171996
6 months    ki1000304b-SAS-CompFeed    INDIA     >=167 cm             NA                 0.1362494   -0.1003060   0.3219477
6 months    ki1000304b-SAS-FoodSuppl   INDIA     >=167 cm             NA                 0.2382563   -0.1651968   0.5020124
6 months    ki1101329-Keneba           GAMBIA    >=167 cm             NA                -0.0043471   -0.1672214   0.1357996
24 months   ki1101329-Keneba           GAMBIA    >=167 cm             NA                 0.0235673   -0.1132822   0.1435946