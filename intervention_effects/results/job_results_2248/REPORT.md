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

**Outcome Variable:** ever_stunted

## Predictor Variables

**Intervention Variable:** tr

**Adjustment Set:**

unadjusted

## Stratifying Variables

The analysis was stratified on these variable(s):

* mwtkg
* agecat
* studyid
* country

## Data Summary

mwtkg       agecat        studyid                     country                        tr          ever_stunted   n_cell       n
----------  ------------  --------------------------  -----------------------------  ---------  -------------  -------  ------
[42.5-50)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0       17      95
[42.5-50)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1        3      95
[42.5-50)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0       20      95
[42.5-50)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1        3      95
[42.5-50)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0       48      95
[42.5-50)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1        4      95
[50-57.5)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0        9      48
[50-57.5)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1        0      48
[50-57.5)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0       11      48
[50-57.5)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1        0      48
[50-57.5)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0       26      48
[50-57.5)   0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1        2      48
<42.5       0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0        9      72
<42.5       0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1        2      72
<42.5       0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0       27      72
<42.5       0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1        4      72
<42.5       0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0       26      72
<42.5       0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1        4      72
>=57.5      0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0        2      17
>=57.5      0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1        1      17
>=57.5      0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0        4      17
>=57.5      0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1        0      17
>=57.5      0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0       10      17
>=57.5      0-6 months    ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1        0      17
[42.5-50)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                0        8      30
[42.5-50)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        2      30
[42.5-50)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0       16      30
[42.5-50)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1        4      30
[50-57.5)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                0       16      35
[50-57.5)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        4      35
[50-57.5)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0       13      35
[50-57.5)   0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1        2      35
>=57.5      0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                0        8      19
>=57.5      0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        2      19
>=57.5      0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0        7      19
>=57.5      0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1        2      19
<42.5       0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                0        3      13
<42.5       0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        4      13
<42.5       0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0        5      13
<42.5       0-6 months    ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1        1      13
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                0       49     167
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                1       30     167
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  0       45     167
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  1       43     167
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                0      119     364
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                1       49     364
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  0      140     364
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  1       56     364
>=57.5      0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                0       23      64
>=57.5      0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                1        3      64
>=57.5      0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  0       35      64
>=57.5      0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  1        3      64
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                0       73     195
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control                1       20     195
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  0       85     195
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                  1       17     195
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                0       44     163
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                1        5     163
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  0      101     163
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  1       13     163
>=57.5      0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                0       27     117
>=57.5      0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                1        4     117
>=57.5      0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  0       80     117
>=57.5      0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  1        6     117
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                0       39     196
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                1        6     196
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  0      132     196
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  1       19     196
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                0       32     163
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control                1        9     163
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  0       96     163
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                  1       26     163
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0      318    1396
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       20    1396
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0      326    1396
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       16    1396
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0      673    1396
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       43    1396
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0      138     576
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       12     576
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0      129     576
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       12     576
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0      265     576
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       20     576
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0       49     196
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1        7     196
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0       47     196
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1        6     196
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0       73     196
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       14     196
<42.5       0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0        4      26
<42.5       0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1        1      26
<42.5       0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0        6      26
<42.5       0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1        0      26
<42.5       0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0       11      26
<42.5       0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1        4      26
[50-57.5)   0-6 months    ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0       11      12
[50-57.5)   0-6 months    ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1        1      12
>=57.5      0-6 months    ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0       12      13
>=57.5      0-6 months    ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1        1      13
[42.5-50)   0-6 months    ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0       10      13
[42.5-50)   0-6 months    ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1        3      13
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Control                0     4568    9939
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Control                1      282    9939
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               0     4816    9939
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               1      273    9939
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Control                0     1291    2819
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Control                1      103    2819
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               0     1325    2819
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               1      100    2819
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Control                0      227     527
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Control                1       32     527
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               0      243     527
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               1       25     527
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Control                0        9      32
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Control                1        5      32
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               0       12      32
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Maternal               1        6      32
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                0      552    2695
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                1      134    2695
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0     1575    2695
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      434    2695
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                0     1032    4641
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                1      139    4641
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0     3001    4641
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      469    4641
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                0      168    1040
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                1       81    1040
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0      589    1040
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      202    1040
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                0        8     101
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control                1        9     101
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0       59     101
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1       25     101
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                0       37     277
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                1        6     277
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      189     277
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1       45     277
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                0       51     475
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                1       23     475
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      296     475
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1      105     475
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                0       34     371
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                1       23     371
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      199     371
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1      115     371
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                0        5      68
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control                1        8      68
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0       33      68
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1       22      68
[50-57.5)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0        7      25
[50-57.5)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1        1      25
[50-57.5)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0       14      25
[50-57.5)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1        3      25
[42.5-50)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0        4      15
[42.5-50)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1        2      15
[42.5-50)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0        7      15
[42.5-50)   0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1        2      15
<42.5       0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0        2       5
<42.5       0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1        0       5
<42.5       0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0        2       5
<42.5       0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1        1       5
>=57.5      0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0        5      25
>=57.5      0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1        2      25
>=57.5      0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0       13      25
>=57.5      0-6 months    ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1        5      25
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control                0       13     101
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control                1        7     101
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    0       32     101
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    1       16     101
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  0       18     101
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  1       15     101
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control                0       22     108
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control                1        8     108
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    0       38     108
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    1       16     108
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  0       15     108
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  1        9     108
<42.5       0-6 months    ki1148112-LCNI-5            MALAWI                         Control                0        2      27
<42.5       0-6 months    ki1148112-LCNI-5            MALAWI                         Control                1        7      27
<42.5       0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    0        4      27
<42.5       0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    1        8      27
<42.5       0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  0        4      27
<42.5       0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  1        2      27
>=57.5      0-6 months    ki1148112-LCNI-5            MALAWI                         Control                0        6      35
>=57.5      0-6 months    ki1148112-LCNI-5            MALAWI                         Control                1        3      35
>=57.5      0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    0       19      35
>=57.5      0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                    1        5      35
>=57.5      0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  0        1      35
>=57.5      0-6 months    ki1148112-LCNI-5            MALAWI                         Other                  1        1      35
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0      284    1418
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1       65    1418
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0      314    1418
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1       49    1418
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      583    1418
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1      123    1418
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0       82     358
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1       10     358
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0       80     358
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1       13     358
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      159     358
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1       14     358
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0      211    1238
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1       78    1238
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0      271    1238
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1       67    1238
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      427    1238
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1      184    1238
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0      152     712
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1       28     712
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0      158     712
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1       13     712
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      310     712
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1       51     712
[42.5-50)   6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0       12      21
[42.5-50)   6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0        9      21
>=57.5      6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0       12      18
>=57.5      6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0        6      18
<42.5       6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0        3       5
<42.5       6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0        2       5
[50-57.5)   6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0       11      23
[50-57.5)   6-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0       12      23
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       25      94
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1       24      94
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0       26      94
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1       19      94
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       86     300
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1       49     300
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0      119     300
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1       46     300
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       20      69
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1        8      69
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0       33      69
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1        8      69
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       67     184
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1       17     184
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0       71     184
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1       29     184
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       39     142
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1        6     142
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       80     142
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       17     142
>=57.5      6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       24     103
>=57.5      6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1        2     103
>=57.5      6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       65     103
>=57.5      6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       12     103
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       23     148
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1       10     148
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       79     148
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       36     148
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       15     104
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1        7     104
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       53     104
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       29     104
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0      247    1158
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       33    1158
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0      256    1158
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       24    1158
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0      526    1158
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       72    1158
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0      108     484
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       18     484
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0      105     484
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       15     484
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0      200     484
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       38     484
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0       35     149
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       11     149
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0       33     149
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       12     149
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0       42     149
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       16     149
<42.5       6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0        3      21
<42.5       6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1        2      21
<42.5       6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0        3      21
<42.5       6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1        1      21
<42.5       6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0        9      21
<42.5       6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1        3      21
>=57.5      6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0     1305    1408
>=57.5      6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1      103    1408
[50-57.5)   6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0     1565    1742
[50-57.5)   6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1      177    1742
[42.5-50)   6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0      771     903
[42.5-50)   6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1      132     903
<42.5       6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0       58      72
<42.5       6-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1       14      72
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0      169     892
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1       26     892
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0      630     892
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1       67     892
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0      207    1109
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1       69    1109
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0      729    1109
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1      104    1109
<42.5       6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0       12      49
<42.5       6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1        4      49
<42.5       6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0       26      49
<42.5       6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1        7      49
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0      112     581
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1       30     581
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0      346     581
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1       93     581
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Control                0     4714   10160
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Control                1      213   10160
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0     5030   10160
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1      203   10160
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Control                0     1343    2846
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Control                1       60    2846
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0     1371    2846
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1       72    2846
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Control                0      237     525
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Control                1       14     525
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0      257     525
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1       17     525
<42.5       6-24 months   ki1119695-PROBIT            BELARUS                        Control                0       11      28
<42.5       6-24 months   ki1119695-PROBIT            BELARUS                        Control                1        1      28
<42.5       6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0       15      28
<42.5       6-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1        1      28
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0      537    2628
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1      118    2628
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0     1658    2628
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      315    2628
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0     1083    4708
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1      127    4708
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0     3082    4708
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      416    4708
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0      170     991
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1       57     991
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0      612     991
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      152     991
<42.5       6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0        9      90
<42.5       6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1        4      90
<42.5       6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0       61      90
<42.5       6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1       16      90
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0       41     331
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1       10     331
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      216     331
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1       64     331
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0       76     489
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1       18     489
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      306     489
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1       89     489
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0       44     331
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1        6     331
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      231     331
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1       50     331
<42.5       6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0        5      56
<42.5       6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1        3      56
<42.5       6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0       34      56
<42.5       6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1       14      56
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0      109     374
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1       28     374
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0      172     374
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1       65     374
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0       48     235
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1       29     235
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0      105     235
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1       53     235
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0       77     285
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1       13     285
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0      151     285
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1       44     285
<42.5       6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0        3      32
<42.5       6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1        4      32
<42.5       6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0       13      32
<42.5       6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1       12      32
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control                0       43     222
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control                1       13     222
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       79     222
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1       32     222
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0       39     222
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1       16     222
<42.5       6-24 months   ki1148112-LCNI-5            MALAWI                         Control                0        6      34
<42.5       6-24 months   ki1148112-LCNI-5            MALAWI                         Control                1        4      34
<42.5       6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       13      34
<42.5       6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1        6      34
<42.5       6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0        3      34
<42.5       6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1        2      34
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control                0       28     223
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control                1       22     223
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       75     223
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1       38     223
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0       40     223
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1       20     223
>=57.5      6-24 months   ki1148112-LCNI-5            MALAWI                         Control                0       25     109
>=57.5      6-24 months   ki1148112-LCNI-5            MALAWI                         Control                1        4     109
>=57.5      6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       41     109
>=57.5      6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1       14     109
>=57.5      6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0       17     109
>=57.5      6-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1        8     109
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0      278    1773
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1      151    1773
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0      311    1773
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1      131    1773
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      569    1773
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1      333    1773
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0       80     388
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1       18     388
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0       79     388
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1       22     388
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      159     388
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1       30     388
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0      202    1830
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1      231    1830
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0      260    1830
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1      211    1830
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      418    1830
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1      508    1830
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                0      151     826
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control                1       65     826
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    0      158     826
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                    1       39     826
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  0      307     826
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                  1      106     826
[50-57.5)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0       27      65
[50-57.5)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        9      65
[50-57.5)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0       25      65
[50-57.5)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1        4      65
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0       20      62
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        7      62
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0       25      62
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1       10      62
<42.5       0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0        6      22
<42.5       0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        5      22
<42.5       0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0        7      22
<42.5       0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1        4      22
>=57.5      0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                0       20      37
>=57.5      0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control                1        2      37
>=57.5      0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               0       13      37
>=57.5      0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal               1        2      37
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       21     195
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1       73     195
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0       26     195
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1       75     195
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       73     438
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1      127     438
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0      104     438
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1      134     438
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       19      77
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1       13      77
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0       30      77
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1       15      77
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                0       63     236
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control                1       49     236
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  0       65     236
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                  1       59     236
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       36     164
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1       13     164
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       78     164
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       37     164
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       25     117
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1        6     117
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       66     117
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       20     117
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       24     196
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1       21     196
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       81     196
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       70     196
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                0       16     163
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control                1       25     163
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  0       53     163
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                  1       69     163
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0      270    1405
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       69    1405
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0      286    1405
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       58    1405
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0      567    1405
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1      155    1405
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0      114     584
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       39     584
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0      107     584
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       35     584
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0      217     584
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       72     584
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0       38     199
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1       18     199
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0       32     199
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1       22     199
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0       54     199
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1       35     199
<42.5       0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                0        2      26
<42.5       0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control                1        3      26
<42.5       0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  0        4      26
<42.5       0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                  1        2      26
<42.5       0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   0        8      26
<42.5       0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                   1        7      26
>=57.5      0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0     1284    1670
>=57.5      0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1      386    1670
[50-57.5)   0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0     1540    2339
[50-57.5)   0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1      799    2339
[42.5-50)   0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0      753    1417
[42.5-50)   0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1      664    1417
<42.5       0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   0       54     134
<42.5       0-24 months   ki1112895-Burkina Faso Zn   BURKINA FASO                   Zinc                   1       80     134
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0      111     773
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1       88     773
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0      317     773
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1      257     773
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0      166     989
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1       52     989
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0      605     989
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1      166     989
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0      201    1333
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1      139    1333
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0      691    1333
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1      302    1333
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                0       12      82
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control                1       10      82
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    0       21      82
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                    1       39      82
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Control                0     4358   10289
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Control                1      637   10289
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0     4710   10289
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1      584   10289
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Control                0     1222    2901
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Control                1      214    2901
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0     1262    2901
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1      203    2901
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Control                0      208     545
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Control                1       58     545
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0      225     545
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1       54     545
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Control                0        9      32
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Control                1        5      32
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               0       12      32
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Maternal               1        6      32
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0      521    3330
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1      307    3330
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0     1548    3330
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      954    3330
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0     1058    5642
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1      361    5642
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0     3069    5642
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1     1154    5642
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0      156    1330
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1      170    1330
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0      557    1330
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1      447    1330
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                0        5     137
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control                1       18     137
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   0       55     137
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                   1       59     137
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0       39     606
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1       56     606
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      213     606
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1      298     606
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0       46     454
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1       26     454
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      239     454
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1      143     454
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0       71     761
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1       64     761
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0      329     761
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1      297     761
<42.5       0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                0        4     103
<42.5       0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control                1       13     103
<42.5       0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    0       32     103
<42.5       0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                    1       54     103
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0      105     458
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1       60     458
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0      162     458
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1      131     458
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0       46     311
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1       55     311
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0       97     311
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1      113     311
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0       73     328
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1       35     328
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0      148     328
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1       72     328
<42.5       0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                0        3      54
<42.5       0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control                1       12      54
<42.5       0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               0       11      54
<42.5       0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal               1       28      54
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control                0       44     306
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control                1       32     306
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       68     306
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1       86     306
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0       33     306
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1       43     306
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control                0       26     333
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control                1       53     333
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       67     333
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1       98     333
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0       32     333
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1       57     333
<42.5       0-24 months   ki1148112-LCNI-5            MALAWI                         Control                0        4      72
<42.5       0-24 months   ki1148112-LCNI-5            MALAWI                         Control                1       16      72
<42.5       0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       10      72
<42.5       0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1       26      72
<42.5       0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0        4      72
<42.5       0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1       12      72
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Control                0       22     127
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Control                1       11     127
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    0       34     127
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                    1       32     127
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  0       15     127
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Other                  1       13     127
[50-57.5)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         Control                0        7      16
[50-57.5)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         Control                1        1      16
[50-57.5)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         LNS                    0        7      16
[50-57.5)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         LNS                    1        1      16
[42.5-50)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         Control                0        4      10
[42.5-50)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         Control                1        2      10
[42.5-50)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         LNS                    0        3      10
[42.5-50)   0-6 months    iLiNS_DYADM_LNS             MALAWI                         LNS                    1        1      10
>=57.5      0-6 months    iLiNS_DYADM_LNS             MALAWI                         Control                0        5      14
>=57.5      0-6 months    iLiNS_DYADM_LNS             MALAWI                         Control                1        2      14
>=57.5      0-6 months    iLiNS_DYADM_LNS             MALAWI                         LNS                    0        4      14
>=57.5      0-6 months    iLiNS_DYADM_LNS             MALAWI                         LNS                    1        3      14
<42.5       0-6 months    iLiNS_DYADM_LNS             MALAWI                         Control                0        2       3
<42.5       0-6 months    iLiNS_DYADM_LNS             MALAWI                         LNS                    0        1       3
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0      153     697
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1       12     697
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0      477     697
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1       55     697
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0      183     833
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1       34     833
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0      546     833
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1       70     833
<42.5       6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0        8      33
<42.5       6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1        2      33
<42.5       6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0       18      33
<42.5       6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1        5      33
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0       77     439
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1       19     439
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0      269     439
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1       74     439
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0      109     257
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1       28     257
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0       87     257
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1       33     257
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0       77     185
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1       13     185
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0       72     185
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1       23     185
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0       48     148
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1       29     148
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0       44     148
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1       27     148
<42.5       6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0        3      23
<42.5       6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1        4      23
<42.5       6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0       10      23
<42.5       6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1        6      23
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0      149     771
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1       35     771
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0      456     771
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1      131     771
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0      172     993
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1       90     993
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0      519     993
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1      212     993
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0        6      60
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1       12      60
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0       15      60
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1       27      60
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                0       74     574
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control                1       51     574
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   0      243     574
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                   1      206     574
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0      105     313
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1       60     313
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0       83     313
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1       65     313
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0       73     218
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1       35     218
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0       71     218
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1       39     218
<42.5       0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0        3      36
<42.5       0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1       12      36
<42.5       0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0        9      36
<42.5       0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1       12      36
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                0       46     201
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control                1       55     201
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    0       41     201
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                    1       59     201


The following strata were considered:

* mwtkg: [42.5-50), agecat: 0-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: [42.5-50), agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: [50-57.5), agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: <42.5, agecat: 0-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: <42.5, agecat: 0-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: <42.5, agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: >=57.5, agecat: 0-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: >=57.5, agecat: 0-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: >=57.5, agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: >=57.5, agecat: 6-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: >=57.5, agecat: 6-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI

### Dropped Strata

Some strata were dropped due to rare outcomes:

* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1000110-WASH-Bangladesh, country: BANGLADESH
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1000304b-SAS-CompFeed, country: INDIA
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1112895-Burkina Faso Zn, country: BURKINA FASO
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: <42.5, agecat: 0-6 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: >=57.5, agecat: 0-6 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1017093b-PROVIDE, country: BANGLADESH
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1112895-iLiNS-Zinc, country: BURKINA FASO
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1119695-PROBIT, country: BELARUS
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1126311-ZVITAMBO, country: ZIMBABWE
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: >=57.5, agecat: 6-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: >=57.5, agecat: 0-24 months, studyid: ki1000125-AgaKhanUniv, country: PAKISTAN
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1066203-TanzaniaChild2, country: TANZANIA, UNITED REPUBLIC OF
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1148112-iLiNS-DOSE, country: MALAWI
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1148112-iLiNS-DYAD-M, country: MALAWI
* mwtkg: <42.5, agecat: 0-24 months, studyid: ki1148112-LCNI-5, country: MALAWI
* mwtkg: [50-57.5), agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: [42.5-50), agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: >=57.5, agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: <42.5, agecat: 0-6 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: <42.5, agecat: 6-24 months, studyid: iLiNS-Zinc_ZvLNS, country: BURKINA FASO
* mwtkg: <42.5, agecat: 6-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI
* mwtkg: <42.5, agecat: 0-24 months, studyid: iLiNS_DYADM_LNS, country: MALAWI

## Methods Detail

We're interested in the causal parameters $E[Y_a]$ for all values of $a \in \mathcal{A}$. These parameters represent the mean outcome if, possibly contrary to fact, we intervened to set all units to have $A=a$. Under the randomization and positivity assumptions, these are identified by the statistical parameters $\psi_a=E_W[E_{Y|A,W}(Y|A=a,W)]$.  In addition, we're interested in the mean of $Y$, $E[Y]$ under no intervention (the observed mean). We will estimate these parameters by using SuperLearner to fit the relevant likelihood factors -- $E_{Y|A,W}(Y|A=a,W)$ and $p(A=a|W)$, and then updating our likelihood fit using a joint TMLE.

For unadjusted analyses ($W=\{\}$), initial likelihoods were estimated using Lrnr_glm to estimate the simple $E(Y|A)$ and Lrnr_mean to estimate $p(A)$. For adjusted analyses, a small library containing Lrnr_glmnet, Lrnr_xgboost, and Lrnr_mean was used.

Having estimated these parameters, we will then use the delta method to estimate relative risks and attributable risks relative to a prespecified baseline level of $A$.

todo: add detail about dropping strata with rare outcomes, handling missingness



```
##           ever_stunted
## tr          0  1
##   Control   0  0
##   LNS       0  0
##   Maternal  0  0
##   Other     0  0
##   VitA      0  0
##   Zinc     54 80
##           ever_stunted
## tr          0  1
##   Control   0  0
##   LNS       0  0
##   Maternal  0  0
##   Other     0  0
##   VitA      0  0
##   Zinc     58 14
##           ever_stunted
## tr            0    1
##   Control     0    0
##   LNS         0    0
##   Maternal    0    0
##   Other       0    0
##   VitA        0    0
##   Zinc     1284  386
##           ever_stunted
## tr          0
##   Control  12
##   LNS       0
##   Maternal  6
##   Other     0
##   VitA      0
##   Zinc      0
##           ever_stunted
## tr            0    1
##   Control     0    0
##   LNS         0    0
##   Maternal    0    0
##   Other       0    0
##   VitA        0    0
##   Zinc     1305  103
##           ever_stunted
## tr           0   1
##   Control    0   0
##   LNS        0   0
##   Maternal   0   0
##   Other      0   0
##   VitA       0   0
##   Zinc     753 664
##           ever_stunted
## tr          0
##   Control  12
##   LNS       0
##   Maternal  9
##   Other     0
##   VitA      0
##   Zinc      0
##           ever_stunted
## tr           0   1
##   Control    0   0
##   LNS        0   0
##   Maternal   0   0
##   Other      0   0
##   VitA       0   0
##   Zinc     771 132
##           ever_stunted
## tr            0    1
##   Control     0    0
##   LNS         0    0
##   Maternal    0    0
##   Other       0    0
##   VitA        0    0
##   Zinc     1540  799
##           ever_stunted
## tr          0
##   Control  11
##   LNS       0
##   Maternal 12
##   Other     0
##   VitA      0
##   Zinc      0
##           ever_stunted
## tr            0    1
##   Control     0    0
##   LNS         0    0
##   Maternal    0    0
##   Other       0    0
##   VitA        0    0
##   Zinc     1565  177
```




# Results Detail

## Results Plots
![](/tmp/50ef6160-b473-4246-bc7f-dc5491a9d163/REPORT_files/figure-html/plot_tsm-1.png)<!-- -->

![](/tmp/50ef6160-b473-4246-bc7f-dc5491a9d163/REPORT_files/figure-html/plot_rr-1.png)<!-- -->



![](/tmp/50ef6160-b473-4246-bc7f-dc5491a9d163/REPORT_files/figure-html/plot_paf-1.png)<!-- -->

![](/tmp/50ef6160-b473-4246-bc7f-dc5491a9d163/REPORT_files/figure-html/plot_par-1.png)<!-- -->

## Results Table

### Parameter: TSM


mwtkg       agecat        studyid                     country                        intervention_level   baseline_level     estimate     ci_lower    ci_upper
----------  ------------  --------------------------  -----------------------------  -------------------  ---------------  ----------  -----------  ----------
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                0.3240741    0.2800414   0.3681067
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  NA                0.3545455    0.3092385   0.3998524
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                0.1902174    0.0716387   0.3087961
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 NA                0.2231687    0.1067908   0.3395465
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.1836735    0.1069107   0.2604362
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.2178218    0.1372188   0.2984248
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.1587302    0.1065657   0.2108946
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.4062500    0.2507776   0.5617224
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.3333333    0.3065054   0.3601613
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.1935484    0.1565408   0.2305560
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.2325581    0.1666462   0.2984701
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.2035398    0.1606643   0.2464154
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.1686047    0.1290259   0.2081834
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.2146814    0.1847206   0.2446423
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                0.2385321    0.2176174   0.2594468
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  NA                0.2153048    0.1383150   0.2922946
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                0.1275275    0.1133015   0.1417535
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             NA                0.1103136    0.1003943   0.1202329
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.2544045    0.2487047   0.2601043
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.2732655    0.2632044   0.2833265
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.3611111    0.3434966   0.3787256
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.3743455    0.3334660   0.4152251
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                0.3240741    0.2948764   0.3532718
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             NA                0.3272727    0.2855407   0.3690047
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                0.3333333    0.1718598   0.4948069
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  NA                0.4848485    0.3637989   0.6058980
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Other                NA                0.4642857    0.2788280   0.6497434
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.0591716    0.0340089   0.0843343
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.0467836    0.0243947   0.0691726
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.0600559    0.0426468   0.0774650
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                0.0581443    0.0495050   0.0667837
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             NA                0.0536451    0.0468871   0.0604031
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.1187020    0.1140273   0.1233766
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.1351585    0.1266523   0.1436647
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.1395349    0.1234286   0.1556412
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.1923077    0.1495728   0.2350426
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                0.1444444    0.1088232   0.1800657
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  NA                0.2421053    0.1975861   0.2866244
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                0.0727273   -0.0860546   0.2315091
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 NA                0.1033835    0.0608473   0.1459196
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.1086957    0.0450043   0.1723870
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.1397849    0.0692105   0.2103594
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.0809249    0.0402291   0.1216206
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.2857143    0.1295479   0.4418806
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.1951220    0.1106337   0.2796102
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.1178571    0.0800735   0.1556408
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.0857143    0.0529105   0.1185181
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.1204013    0.0943072   0.1464955
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                0.1333333    0.1196487   0.1470179
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  NA                0.0961263    0.0621106   0.1301420
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                0.0432312    0.0340178   0.0524445
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Maternal             NA                0.0387923    0.0340574   0.0435271
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.1049587    0.1005197   0.1093976
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.1189251    0.1109541   0.1268961
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.1200000    0.1063732   0.1336268
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.1779359    0.1399157   0.2159562
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                0.1444444    0.1213880   0.1675008
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             NA                0.2256410    0.1853167   0.2659654
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                0.6666667    0.4705146   0.8628188
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 NA                0.6428571    0.4572311   0.8284832
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.5334873    0.4864853   0.5804893
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.4479830    0.4030606   0.4929055
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.5485961    0.5165356   0.5806566
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.7765957    0.7595857   0.7936058
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.7425743    0.6330228   0.8521257
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.6097561    0.5720827   0.6474295
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.5655738    0.4995380   0.6316096
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                0.4545455    0.3913727   0.5177183
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  NA                0.6500000    0.5459865   0.7540135
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                0.3571429    0.2164227   0.4978630
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             NA                0.3333333    0.1804791   0.4861876
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.7826087    0.7542049   0.8110124
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.5175439    0.4409360   0.5941517
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.3797468    0.3563743   0.4031194
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.4886364    0.4158401   0.5614326
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.2195122    0.1875453   0.2514791
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.2131148    0.1585592   0.2676703
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                0.3571429    0.2164227   0.4978630
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             NA                0.3333333    0.1804791   0.4861876
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.5294118    0.4892762   0.5695473
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.2976190    0.2158961   0.3793419
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.6153846    0.5644498   0.6663194
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.4000000    0.2945022   0.5054978
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.2698962    0.2186967   0.3210956
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.1982249    0.1557071   0.2407426
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.3011457    0.2647554   0.3375359
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.4897959    0.4346716   0.5449202
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.4222222    0.2999529   0.5444915
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.3181818    0.2768108   0.3595528
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.3536585    0.2716719   0.4356451
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                0.5445545    0.4956290   0.5934799
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  NA                0.5900000    0.5419213   0.6380787
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                0.4080000    0.2544103   0.5615897
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 NA                0.4587973    0.3740702   0.5435245
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.3519814    0.3067754   0.3971873
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.2963801    0.2537954   0.3389647
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.3691796    0.3376775   0.4006817
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control              NA                0.2592593    0.1866872   0.3318313
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal             NA                0.2857143    0.2005371   0.3708915
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.6350000    0.5875740   0.6824260
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.5630252    0.5473181   0.5787323
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.4666667    0.4331152   0.5002182
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.4635762    0.4021426   0.5250097
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.3214286    0.1988010   0.4440561
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.4074074    0.2760248   0.5387900
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.3932584    0.2915193   0.4949975
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                0.4422111    0.4244376   0.4599845
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  NA                0.4477352    0.3976849   0.4977855
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                0.2180451    0.1847755   0.2513147
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             NA                0.1935484    0.1615113   0.2255855
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.5214724    0.5081759   0.5347689
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.4452191    0.4220038   0.4684344
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.5894737    0.5739534   0.6049939
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.5831703    0.5470940   0.6192465
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                0.5445545    0.5129618   0.5761471
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             NA                0.5380952    0.4924913   0.5836992
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                0.6708861    0.5671129   0.7746593
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  NA                0.5939394    0.5188937   0.6689851
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                NA                0.6404494    0.5406039   0.7402950
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.2916667    0.2640173   0.3193161
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.2857143    0.2509961   0.3204325
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.1333333    0.1104718   0.1561948
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.1258278    0.0849697   0.1666859
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.1250000    0.0381592   0.2118408
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.1132075    0.0276872   0.1987279
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.1609195    0.0835081   0.2383310
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                0.1235521    0.0964983   0.1506060
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             NA                0.0932836    0.0772551   0.1093121
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.3253012    0.3113625   0.3392399
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.2553729    0.2322486   0.2784973
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.4035088    0.3839146   0.4231029
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.3662420    0.3210803   0.4114038
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              NA                0.3500000    0.1399201   0.5600799
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                  NA                0.3333333    0.1993095   0.4673571
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                NA                0.4545455    0.2838116   0.6252794
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                0.3766234    0.3201254   0.4331213
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  NA                0.3802817    0.3259269   0.4346365
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                0.1979167    0.0744613   0.3213721
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 NA                0.2157434    0.1487728   0.2827141
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.1862464    0.1453882   0.2271046
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.1349862    0.0998217   0.1701507
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.1742210    0.1462324   0.2022096
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.3629630    0.3068956   0.4190303
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.2787879    0.2558379   0.3017379
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.3030303    0.2679498   0.3381108
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.3130435    0.2469628   0.3791241
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.2391304    0.1154492   0.3628117
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.2666667    0.1370266   0.3963067
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.2758621    0.1604495   0.3912746
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                0.2112676    0.1941905   0.2283447
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  NA                0.2118451    0.1720777   0.2516125
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                0.0557769    0.0420221   0.0695317
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal             NA                0.0620438    0.0473242   0.0767634
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.2511013    0.2381730   0.2640297
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.1989529    0.1771183   0.2207874
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.1960784    0.1792639   0.2128929
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.2285714    0.1869022   0.2702406
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                0.3766234    0.3410864   0.4121604
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             NA                0.3354430    0.2858398   0.3850463
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                0.4400000    0.3021015   0.5778985
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  NA                0.3362832    0.2489803   0.4235861
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                NA                0.3333333    0.2137854   0.4528813
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                0.3636364    0.3248814   0.4023913
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  NA                0.4391892    0.4013220   0.4770564
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                0.3435115    0.2574037   0.4296192
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 NA                0.2900137    0.2315430   0.3484844
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.3009259    0.2397225   0.3621293
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.1979695    0.1422930   0.2536461
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.2566586    0.2145076   0.2988096
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.4375000    0.3838211   0.4911789
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.4758065    0.4088834   0.5427295
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.2653061    0.2282588   0.3023535
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.3217391    0.2616866   0.3817917
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.2549020    0.1857877   0.3240162
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.2464789    0.1755352   0.3174225
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.2491349    0.1992270   0.2990429
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                0.4088235    0.3937973   0.4238498
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  NA                0.3041289    0.2693062   0.3389516
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                0.1490251    0.1329760   0.1650741
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             NA                0.1385666    0.1259096   0.1512235
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.3707729    0.3625913   0.3789546
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.3812950    0.3669933   0.3955966
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.4740741    0.4591220   0.4890261
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.4744409    0.4422422   0.5066396
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                0.3636364    0.3371644   0.3901083
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             NA                0.4470990    0.4106390   0.4835590
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                0.4210526    0.3098693   0.5322360
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  NA                0.5584416    0.4798852   0.6369979
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                NA                0.5657895    0.4541726   0.6774063
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.2150538    0.2027879   0.2273196
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.1666667    0.1576492   0.1756841
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.1020408    0.0764838   0.1275978
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.1140351    0.0731018   0.1549684
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.0800000    0.0365471   0.1234529
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.0851064    0.0390084   0.1312044
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.0701754    0.0404932   0.0998576
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                0.0738881    0.0607753   0.0870009
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             NA                0.0701754    0.0585463   0.0818046
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.1953353    0.1877821   0.2028885
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.2160279    0.2026106   0.2294452
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.3108108    0.2943654   0.3272562
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.2618454    0.2254807   0.2982101
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              NA                0.2666667    0.1076867   0.4256467
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                  NA                0.2962963    0.1739392   0.4186534
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                NA                0.3750000    0.1804111   0.5695889
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                0.2043796    0.1683139   0.2404452
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  NA                0.2750000    0.2376245   0.3123755
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                0.1566820    0.0984165   0.2149476
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 NA                0.1136364    0.0863735   0.1408992
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                0.1555556    0.1025715   0.2085396
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  NA                0.0760234    0.0362714   0.1157754
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                NA                0.1412742    0.1053193   0.1772292
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                0.2023810    0.1458875   0.2588745
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                NA                0.2900000    0.2432755   0.3367245
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                0.1333333    0.1017472   0.1649194
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                NA                0.1752577    0.1233923   0.2271232
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                0.1428571    0.0816940   0.2040202
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                NA                0.1250000    0.0657667   0.1842333
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 NA                0.1596639    0.1130797   0.2062481
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                0.2500000    0.2318119   0.2681881
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  NA                0.1248499    0.1039115   0.1457884
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                0.0427655    0.0296020   0.0559290
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal             NA                0.0498961    0.0444074   0.0553847
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                0.1801527    0.1728158   0.1874896
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 NA                0.1596553    0.1475190   0.1717917
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                0.1914894    0.1761833   0.2067954
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  NA                0.2253165    0.1920014   0.2586315
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                0.2043796    0.1796116   0.2291475
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             NA                0.2742616    0.2382200   0.3103032
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                0.2321429    0.1213141   0.3429716
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  NA                0.2882883    0.2038319   0.3727447
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                NA                0.2909091    0.1706060   0.4112122


### Parameter: E(Y)


mwtkg       agecat        studyid                     country                        intervention_level   baseline_level     estimate    ci_lower    ci_upper
----------  ------------  --------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  ----------
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         NA                   NA                0.3394495   0.2762309   0.4026682
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   NA                   NA                0.2153048   0.1106253   0.3199843
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.1804124   0.1421014   0.2187234
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.3636364   0.2044633   0.5228095
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.2222222   0.1465667   0.2978777
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.2007117   0.1797608   0.2216626
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   NA                   NA                0.2204247   0.1408419   0.3000075
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        NA                   NA                0.1186704   0.1004409   0.1369000
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.2685218   0.2569564   0.2800872
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.3722467   0.3277314   0.4167620
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         NA                   NA                0.3262195   0.2752870   0.3771520
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         NA                   NA                0.4409449   0.3542522   0.5276375
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.0565903   0.0444653   0.0687153
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        NA                   NA                0.0558406   0.0447229   0.0669583
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.1310062   0.1212979   0.1407146
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.1841155   0.1383906   0.2298405
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         NA                   NA                0.1945946   0.1371186   0.2520706
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   NA                   NA                0.0961263   0.0496117   0.1426408
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.1033520   0.0717740   0.1349299
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.2318841   0.0504777   0.4132904
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.1113990   0.0932699   0.1295280
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   NA                   NA                0.1042601   0.0673619   0.1411582
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        NA                   NA                0.0409449   0.0304456   0.0514441
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.1153356   0.1062103   0.1244609
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.1691843   0.1287338   0.2096348
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         NA                   NA                0.2000000   0.1533355   0.2466645
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   NA                   NA                0.6500000   0.5054531   0.7945469
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.5191257   0.4962279   0.5420235
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.7589744   0.6482416   0.8697072
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.5766871   0.5006034   0.6527708
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   NA                   NA                0.5975610   0.4737983   0.7213237
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        NA                   NA                0.3437500   0.1360416   0.5514584
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.5620438   0.4786605   0.6454271
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.4371257   0.3488352   0.5254163
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.2147239   0.1514912   0.2779567
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        NA                   NA                0.3437500   0.1360416   0.5514584
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.3366337   0.2440139   0.4292534
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.4411765   0.3222840   0.5600689
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.2657512   0.2411349   0.2903675
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.4574468   0.3254902   0.5894035
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.3461538   0.2542779   0.4380298
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         NA                   NA                0.5671642   0.4984970   0.6358313
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   NA                   NA                0.4477352   0.3787522   0.5167182
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.3468697   0.3247082   0.3690312
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       NA                   NA                0.2741935   0.1622440   0.3861431
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.5958904   0.5385114   0.6532694
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.4642857   0.3942870   0.5342844
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.3768844   0.3093844   0.4443844
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   NA                   NA                0.4463131   0.3932231   0.4994031
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        NA                   NA                0.2055046   0.1593713   0.2516378
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.4639098   0.4370983   0.4907213
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.5841584   0.5448849   0.6234319
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         NA                   NA                0.5401929   0.4847138   0.5956720
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         NA                   NA                0.6246246   0.5725386   0.6767107
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.2884615   0.2440939   0.3328291
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.1275510   0.0807298   0.1743722
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.1377551   0.0893824   0.1861278
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        NA                   NA                0.1081594   0.0764508   0.1398680
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.2721154   0.2450541   0.2991767
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.3719677   0.3227194   0.4212159
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         NA                   NA                0.3762376   0.2812890   0.4711863
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         NA                   NA                0.3783784   0.2999785   0.4567783
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   NA                   NA                0.2118451   0.1571693   0.2665209
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.1671368   0.1477107   0.1865629
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.3166667   0.2455199   0.3878135
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.3108108   0.2359927   0.3856289
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.2617450   0.1909244   0.3325656
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   NA                   NA                0.2117040   0.1689751   0.2544328
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        NA                   NA                0.0590476   0.0393860   0.0787092
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.2108981   0.1854864   0.2363098
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.2235650   0.1786133   0.2685166
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         NA                   NA                0.3489362   0.2878666   0.4100058
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         NA                   NA                0.3587444   0.2956516   0.4218372
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         NA                   NA                0.3993610   0.3450159   0.4537061
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   NA                   NA                0.3041289   0.2560624   0.3521954
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.2542373   0.2245247   0.2839499
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.4576271   0.3705197   0.5447346
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.3048780   0.2342060   0.3755501
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.2500000   0.2148509   0.2851491
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   NA                   NA                0.3308327   0.2900097   0.3716557
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        NA                   NA                0.1437435   0.1225029   0.1649842
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.3786787   0.3622014   0.3951559
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.4743758   0.4388749   0.5098768
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         NA                   NA                0.4170306   0.3718245   0.4622366
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         NA                   NA                0.5261438   0.4701069   0.5821806
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.1897436   0.1663377   0.2131495
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.1104294   0.0621655   0.1586934
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.0763889   0.0546782   0.0980996
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        NA                   NA                0.0720114   0.0543215   0.0897012
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.2107607   0.1953597   0.2261617
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.2694737   0.2295312   0.3094162
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         NA                   NA                0.3055556   0.2182745   0.3928366
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         NA                   NA                0.2373541   0.1852361   0.2894721
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   NA                   NA                0.1248499   0.0963665   0.1533333
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     NA                   NA                0.1292135   0.1045575   0.1538695
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          NA                   NA                0.2500000   0.1682774   0.3317226
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     NA                   NA                0.1619718   0.1011601   0.2227836
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   NA                   NA                0.1466942   0.1151417   0.1782467
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   NA                   NA                0.1559964   0.1225386   0.1894542
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        NA                   NA                0.0463809   0.0321742   0.0605876
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       NA                   NA                0.1647641   0.1505783   0.1789499
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         NA                   NA                0.2188139   0.1821319   0.2554959
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         NA                   NA                0.2486631   0.2047982   0.2925280
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         NA                   NA                0.2747748   0.2159207   0.3336289


### Parameter: RR


mwtkg       agecat        studyid                     country                        intervention_level   baseline_level     estimate    ci_lower     ci_upper
----------  ------------  --------------------------  -----------------------------  -------------------  ---------------  ----------  ----------  -----------
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  Control           1.0940260   0.9078650    1.3183599
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 Control           1.1732295   0.6340911    2.1707724
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           1.1859186   0.6786223    2.0724384
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           0.8641975   0.5078247    1.4706599
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.8205128   0.5549290    1.2132026
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                Control           1.2015504   0.8536149    1.6913052
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           0.8283620   0.6042874    1.1355253
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           1.0547393   0.8192286    1.3579541
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  Control           0.9026240   0.6250086    1.3035501
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             Control           0.8650177   0.7502751    0.9973083
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           1.0741376   1.0288268    1.1214439
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           1.0366492   0.9197915    1.1683534
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             Control           1.0098701   0.8638897    1.1805184
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  Control           1.4545455   0.8434287    2.5084543
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Other                Control           1.3928571   0.7434055    2.6096807
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           0.7906433   0.4168155    1.4997446
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           1.0149441   0.6066397    1.6980615
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             Control           0.9226199   0.7597362    1.1204250
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           1.1386374   1.0571652    1.2263885
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           1.3782051   1.0729051    1.7703797
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  Control           1.6761134   1.2322717    2.2798186
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 Control           1.4215226   0.1473917   13.7099108
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           1.2860215   0.5933833    2.7871551
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           0.7445087   0.3439712    1.6114524
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.6829268   0.3397969    1.3725524
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           0.7272727   0.4414467    1.1981642
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           1.0215871   0.6937701    1.5043028
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  Control           0.7209469   0.4987840    1.0420634
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Maternal             Control           0.8973219   0.7024124    1.1463160
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           1.1330659   1.0467335    1.2265189
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           1.4827995   1.1641107    1.8887331
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             Control           1.5621302   1.2292860    1.9850960
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 Control           0.9642857   0.6435416    1.4448901
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           0.8397257   0.7347956    0.9596401
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           1.0283209   0.9251525    1.1429941
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.9561915   0.8238404    1.1098050
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                Control           0.9275410   0.8127623    1.0585288
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  Control           1.4300000   1.1562095    1.7686241
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             Control           0.9333333   0.5095246    1.7096548
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           0.6613060   0.5678233    0.7701792
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                Control           1.2867424   1.0951445    1.5118609
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                Control           0.9708561   0.7231839    1.3033498
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             Control           0.9333333   0.5095246    1.7096548
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           0.5621693   0.4228176    0.7474484
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           0.6500000   0.4930179    0.8569668
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           0.7344485   0.5515734    0.9779561
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           1.1157833   0.8910435    1.3972071
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.8620370   0.6340890    1.1719299
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                Control           1.1114983   0.8520680    1.4499175
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  Control           1.0834545   0.9596938    1.2231753
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 Control           1.1245033   0.7183367    1.7603271
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           0.8420335   0.6944383    1.0209985
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           1.0488613   0.8989839    1.2237260
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Maternal             Control           1.1020408   0.7321459    1.6588141
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.8866539   0.8187263    0.9602173
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                Control           0.9933775   0.8543519    1.1550262
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           1.2674897   0.7691218    2.0887852
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           1.2234707   0.7716209    1.9399169
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  Control           1.0124921   0.8991829    1.1400798
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             Control           0.8876529   0.7067774    1.1148175
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           0.8537731   0.8056276    0.9047959
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           0.9893067   0.9249801    1.0581068
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             Control           0.9881385   0.8916886    1.0950210
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  Control           0.8853059   0.7250247    1.0810204
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                Control           0.9546322   0.7664054    1.1890869
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.9795918   0.8397011    1.1427878
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                Control           0.9437086   0.6536775    1.3624240
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           0.9056604   0.3245212    2.5274794
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           1.2873563   0.5529817    2.9970003
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             Control           0.7550140   0.5706045    0.9990215
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           0.7850354   0.7102034    0.8677521
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           0.9076433   0.7949852    1.0362664
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                  Control           0.9523810   0.4624388    1.9614044
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                Control           1.2987013   0.6397337    2.6364485
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  Control           1.0097135   0.8207497    1.2421829
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 Control           1.0900721   0.5174748    2.2962612
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           0.7247722   0.5155768    1.0188487
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           0.9354326   0.7127279    1.2277253
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.7680891   0.6450779    0.9145575
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                Control           1.0330435   0.8120106    1.3142424
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           1.1151515   0.5483540    2.2678106
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           1.1536050   0.5931268    2.2437099
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  Control           1.0027335   0.8152711    1.2333007
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal             Control           1.1123566   0.7839474    1.5783422
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           0.7923211   0.7018659    0.8944340
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           1.1657143   0.9530093    1.4258935
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             Control           0.8906591   0.7473609    1.0614331
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  Control           0.7642800   0.5087560    1.1481416
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                Control           0.7575758   0.4705195    1.2197603
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  Control           1.2077703   1.0530495    1.3852236
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 Control           0.8442620   0.6078074    1.1727044
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           0.6578680   0.4649506    0.9308308
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           0.8528963   0.6566989    1.1077101
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           1.0875576   0.9019614    1.3113439
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                Control           1.2127090   0.9605518    1.5310608
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           0.9669556   0.6511405    1.4359467
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           0.9773756   0.6976760    1.3692072
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  Control           0.7439124   0.6593454    0.8393260
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Maternal             Control           0.9298204   0.8087486    1.0690170
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           1.0283786   0.9845858    1.0741192
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           1.0007738   0.9286125    1.0785426
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             Control           1.2295222   1.1022036    1.3715477
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  Control           1.3262987   0.9833399    1.7888710
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Other                Control           1.3437500   0.9664260    1.8683934
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Other                Control           0.7750000   0.7163010    0.8385093
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Other                Control           1.1175438   0.7213996    1.7312239
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           1.0638298   0.4940079    2.2909227
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           0.8771930   0.4406726    1.7461207
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Maternal             Control           0.9497530   0.7455732    1.2098488
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           1.1059337   1.0279100    1.1898799
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           0.8424591   0.7261150    0.9774447
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         LNS                  Control           1.1111111   0.5380153    2.2946705
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Other                Control           1.4062500   0.6379827    3.0996750
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         LNS                  Control           1.3455357   1.0768673    1.6812344
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Zinc                 Control           0.7252674   0.4919688    1.0691995
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     LNS                  Control           0.4887218   0.2618438    0.9121813
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Other                Control           0.9081915   0.5936337    1.3894291
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Other                Control           1.4329412   1.0368353    1.9803729
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Other                Control           1.3144330   0.8997206    1.9203007
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Other                Control           0.8750000   0.4620112    1.6571568
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Zinc                 Control           1.1176471   0.6657252    1.8763521
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   LNS                  Control           0.4993998   0.4149622    0.6010189
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Maternal             Control           1.1667359   0.8421516    1.6164223
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       VitA                 Control           0.8862225   0.8129988    0.9660412
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         LNS                  Control           1.1766526   0.9946068    1.3920188
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Maternal             Control           1.3419228   1.1222577    1.6045841
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              Control           1.0000000   1.0000000    1.0000000
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         LNS                  Control           1.2418572   0.7092648    2.1743774
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Other                Control           1.2531469   0.6663359    2.3567348


### Parameter: PAR


mwtkg       agecat        studyid                     country                        intervention_level   baseline_level      estimate     ci_lower     ci_upper
----------  ------------  --------------------------  -----------------------------  -------------------  ---------------  -----------  -----------  -----------
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0153755   -0.0299867    0.0607376
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.0250874   -0.0704680    0.1206428
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0032611   -0.0694700    0.0629478
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0426136   -0.0807964   -0.0044308
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0286738   -0.0373125    0.0946602
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0028281   -0.0401128    0.0344567
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.0181074   -0.0948026    0.0585877
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0088571   -0.0195349    0.0018207
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0141173    0.0040540    0.0241806
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0111356   -0.0297464    0.0520176
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.0021454   -0.0395872    0.0438780
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                 0.1076115   -0.0339484    0.2491715
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0025813   -0.0243431    0.0191804
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.0023037   -0.0091582    0.0045508
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0123043    0.0037956    0.0208130
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0445806    0.0017863    0.0873750
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0501502    0.0050434    0.0952569
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.0233990   -0.1060075    0.1528054
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0053437   -0.0598305    0.0491431
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0538302   -0.1434442    0.0357837
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0064582   -0.0391061    0.0261898
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.0290732   -0.0635069    0.0053604
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0022863   -0.0071638    0.0025913
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0103769    0.0024041    0.0183498
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0491843    0.0110982    0.0872704
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.0555556    0.0149849    0.0961262
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                -0.0166667   -0.2019755    0.1686422
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0143616   -0.0554476    0.0267244
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0176214   -0.1271676    0.0919248
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0330690   -0.0991707    0.0330328
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                 0.1430155    0.0330752    0.2529558
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0133929   -0.1661458    0.1393601
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.2205649   -0.2989613   -0.1421685
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                 0.0573789   -0.0278939    0.1426517
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0047883   -0.0593455    0.0497690
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.0133929   -0.1661458    0.1393601
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.1927781   -0.2762500   -0.1093062
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.1742081   -0.2816375   -0.0667788
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0041450   -0.0489051    0.0406151
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0323491   -0.1523753    0.0876770
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0279720   -0.0540623    0.1100063
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0226097   -0.0255720    0.0707915
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.0397352   -0.1063242    0.1857946
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0051116   -0.0444279    0.0342046
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control              NA                 0.0149343   -0.0703065    0.1001751
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0391096   -0.0707675   -0.0074517
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0023810   -0.0638148    0.0590529
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.0554559   -0.0500451    0.1609568
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                 0.0041020   -0.0458841    0.0540881
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0125405   -0.0458085    0.0207275
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.0575626   -0.0808448   -0.0342804
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.0053153   -0.0413920    0.0307615
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                -0.0043615   -0.0499667    0.0412437
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                -0.0462615   -0.1377616    0.0452387
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0032051   -0.0379760    0.0315658
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0057823   -0.0466428    0.0350782
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.0127551   -0.0618901    0.0874003
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.0153927   -0.0330200    0.0022345
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.0531858   -0.0763812   -0.0299904
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.0315411   -0.0767236    0.0136414
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              NA                 0.0262376   -0.1626279    0.2151031
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0017550   -0.0526006    0.0561106
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.0139284   -0.1033346    0.1311914
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0191096   -0.0541099    0.0158907
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0462963   -0.0865909   -0.0060017
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0077805   -0.0583036    0.0738646
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.0226145   -0.0816325    0.1268616
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                 0.0004364   -0.0393215    0.0401942
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                 0.0032707   -0.0112201    0.0177616
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.0402032   -0.0620804   -0.0183260
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0274865   -0.0142019    0.0691749
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                -0.0276872   -0.0773523    0.0219778
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                -0.0812556   -0.2015442    0.0390330
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0357247   -0.0023732    0.0738225
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                -0.0393825   -0.1175405    0.0387754
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0466886   -0.0983569    0.0049796
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                 0.0201271   -0.0494218    0.0896760
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0395719   -0.0206114    0.0997553
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0049020   -0.0641417    0.0543377
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.0779908   -0.1173008   -0.0386809
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0052815   -0.0182494    0.0076864
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0079057   -0.0063967    0.0222082
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0003017   -0.0318969    0.0325004
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.0533942    0.0167496    0.0900388
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                 0.1050912    0.0083368    0.2018455
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0253102   -0.0458901   -0.0047303
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0083886   -0.0325534    0.0493307
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0036111   -0.0407069    0.0334846
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.0018767   -0.0135508    0.0097974
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0154254    0.0020038    0.0288470
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.0413371   -0.0777370   -0.0049373
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              NA                 0.0388889   -0.0984106    0.1761884
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0329745   -0.0046494    0.0705984
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                -0.0318321   -0.0738538    0.0101896
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0263421   -0.0710165    0.0183324
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                 0.0476190   -0.0134940    0.1087321
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0286385   -0.0233268    0.0806038
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.0038371   -0.0489713    0.0566455
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.0940036   -0.1249480   -0.0630592
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                 0.0036154   -0.0019084    0.0091391
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.0153886   -0.0275297   -0.0032475
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0273245   -0.0060115    0.0606606
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.0442835    0.0080803    0.0804868
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                 0.0426319   -0.0550921    0.1403559


### Parameter: PAF


mwtkg       agecat        studyid                     country                        intervention_level   baseline_level      estimate     ci_lower     ci_upper
----------  ------------  --------------------------  -----------------------------  -------------------  ---------------  -----------  -----------  -----------
>=57.5      0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0452953   -0.0913581    0.1648378
>=57.5      0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.1165204   -0.4376288    0.4570670
>=57.5      0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0180758   -0.4599092    0.2900392
>=57.5      0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.1171875   -0.2510326    0.0023379
>=57.5      0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.1290323   -0.1732894    0.3534547
>=57.5      0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0140903   -0.2179519    0.1556489
>=57.5      0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.0821480   -0.5326469    0.2359334
>=57.5      0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0746361   -0.1767763    0.0186386
>=57.5      0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0525741    0.0163757    0.0874404
>=57.5      0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0299145   -0.0827062    0.1308207
>=57.5      0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.0065767   -0.1289985    0.1258714
>=57.5      0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                 0.2440476   -0.1569820    0.5060736
>=57.5      0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0456146   -0.5102495    0.2760734
>=57.5      0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.0412549   -0.1775463    0.0792618
>=57.5      0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0939214    0.0330175    0.1509893
>=57.5      0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.2421341    0.0422249    0.4003177
>=57.5      6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.2577160    0.0560384    0.4163052
>=57.5      6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.2434193   -3.8871715    0.8828741
>=57.5      6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0517039   -0.7358885    0.3628156
>=57.5      6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.2321429   -0.8545005    0.1813558
>=57.5      6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0579734   -0.3955139    0.1979243
>=57.5      6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.2788530   -0.7809038    0.0816657
>=57.5      6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0558383   -0.1903626    0.0634832
>=57.5      6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0899715    0.0247361    0.1508434
>=57.5      6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.2907143    0.1095009    0.4350514
>=57.5      6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.2777778    0.1111082    0.4131964
<42.5       0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                -0.0256410   -0.3567199    0.2246450
<42.5       0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0276650   -0.1099493    0.0485193
<42.5       0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0232174   -0.1820894    0.1143024
<42.5       0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0573430   -0.1858231    0.0572167
<42.5       0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                 0.2393321    0.0813137    0.3701706
<42.5       0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0389610   -0.6207047    0.3339687
<42.5       0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.3924337   -0.6020161   -0.2102697
<42.5       0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                 0.1312641   -0.0560894    0.2853805
<42.5       0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0222997   -0.3180539    0.2070912
<42.5       0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.0389610   -0.6207047    0.3339687
<42.5       0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.5726644   -1.0228427   -0.2226721
<42.5       0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.3948718   -0.7833480   -0.0910194
<42.5       6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0155972   -0.1987954    0.1396049
<42.5       6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0707167   -0.3920982    0.1764704
<42.5       6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0808081   -0.1652789    0.2749257
[42.5-50)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0398645   -0.0453446    0.1181280
[42.5-50)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.0887471   -0.3014797    0.3619710
[42.5-50)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.0147365   -0.1346556    0.0925087
[42.5-50)   0-24 months   ki1000125-AgaKhanUniv       PAKISTAN                       Control              NA                 0.0544662   -0.2907792    0.3073687
[42.5-50)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0656322   -0.1241052   -0.0102008
[42.5-50)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0051282   -0.1473268    0.1194464
[42.5-50)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.1471429   -0.1842479    0.3857998
[42.5-50)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                 0.0091909   -0.1082302    0.1141708
[42.5-50)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0610231   -0.2473568    0.0974756
[42.5-50)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.1240815   -0.1820530   -0.0689531
[42.5-50)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.0090990   -0.0733846    0.0513364
[42.5-50)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                -0.0080740   -0.0968767    0.0735393
[42.5-50)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                -0.0740628   -0.2313944    0.0631670
[42.5-50)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.0111111   -0.1406414    0.1037099
[42.5-50)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                -0.0453333   -0.4401919    0.2412665
[42.5-50)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.0925926   -0.6474593    0.5002073
[42.5-50)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.1423152   -0.3468743    0.0311760
[42.5-50)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.1954532   -0.3023584   -0.0973234
[42.5-50)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.0847953   -0.2249868    0.0393522
[42.5-50)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              NA                 0.0697368   -0.5957892    0.4577043
[42.5-50)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0046382   -0.1491318    0.1378316
[42.5-50)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                 0.0657482   -0.6864570    0.4824497
[42.5-50)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.1143351   -0.3444341    0.0763826
[42.5-50)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.1461988   -0.3062074   -0.0057911
[42.5-50)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0250329   -0.2059728    0.2117892
[42.5-50)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.0863991   -0.4124366    0.4090591
[42.5-50)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                 0.0020611   -0.2041111    0.1729318
[42.5-50)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                 0.0553913   -0.2083254    0.2615520
[42.5-50)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.1906288   -0.3213822   -0.0728136
[42.5-50)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.1229465   -0.0571553    0.2723653
[42.5-50)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                -0.0793475   -0.2446896    0.0640309
[42.5-50)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                -0.2265000   -0.6132729    0.0675463
[50-57.5)   0-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.0894545   -0.0021631    0.1726965
[50-57.5)   0-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                -0.1294929   -0.4225025    0.1031620
[50-57.5)   0-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.1836420   -0.4051004    0.0029123
[50-57.5)   0-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                 0.0439815   -0.1131450    0.1789287
[50-57.5)   0-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.1297959   -0.0609919    0.2862762
[50-57.5)   0-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0196078   -0.2863579    0.1918267
[50-57.5)   0-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.2357410   -0.3910241   -0.0977924
[50-57.5)   0-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                -0.0367428   -0.1349939    0.0530032
[50-57.5)   0-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0208772   -0.0168138    0.0571710
[50-57.5)   0-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.0006361   -0.0695517    0.0662179
[50-57.5)   0-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.1280343    0.0474778    0.2017779
[50-57.5)   0-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                 0.1997385   -0.0082000    0.3647902
[50-57.5)   0-6 months    ki1000304b-SAS-CompFeed     INDIA                          Control              NA                -0.1333915   -0.2630744   -0.0170234
[50-57.5)   0-6 months    ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.0759637   -0.3394204    0.3625280
[50-57.5)   0-6 months    ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                -0.0472727   -0.6648575    0.3412168
[50-57.5)   0-6 months    ki1119695-PROBIT            BELARUS                        Control              NA                -0.0260617   -0.2068088    0.1276144
[50-57.5)   0-6 months    ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                 0.0731891    0.0121863    0.1304247
[50-57.5)   0-6 months    ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                -0.1533995   -0.3205323   -0.0074198
[50-57.5)   0-6 months    ki1148112-LCNI-5            MALAWI                         Control              NA                 0.1272727   -0.4598737    0.4782748
[50-57.5)   6-24 months   iLiNS_DYADM_LNS             MALAWI                         Control              NA                 0.1389255   -0.0108830    0.2665329
[50-57.5)   6-24 months   iLiNS-Zinc_ZvLNS            BURKINA FASO                   Control              NA                -0.2549628   -0.6212569    0.0285737
[50-57.5)   6-24 months   ki1000110-WASH-Bangladesh   BANGLADESH                     Control              NA                -0.2038647   -0.6024905    0.0956013
[50-57.5)   6-24 months   ki1000304b-SAS-CompFeed     INDIA                          Control              NA                 0.1904762   -0.0415564    0.3708178
[50-57.5)   6-24 months   ki1017093b-PROVIDE          BANGLADESH                     Control              NA                 0.1768116   -0.1376691    0.4043618
[50-57.5)   6-24 months   ki1066203-TanzaniaChild2    TANZANIA, UNITED REPUBLIC OF   Control              NA                 0.0261569   -0.4093432    0.3270835
[50-57.5)   6-24 months   ki1112895-iLiNS-Zinc        BURKINA FASO                   Control              NA                -0.6026012   -0.9508230   -0.3165369
[50-57.5)   6-24 months   ki1119695-PROBIT            BELARUS                        Control              NA                 0.0779498   -0.0414866    0.1836894
[50-57.5)   6-24 months   ki1126311-ZVITAMBO          ZIMBABWE                       Control              NA                -0.0933977   -0.1771262   -0.0156248
[50-57.5)   6-24 months   ki1148112-iLiNS-DOSE        MALAWI                         Control              NA                 0.1248757   -0.0194734    0.2487862
[50-57.5)   6-24 months   ki1148112-iLiNS-DYAD-M      MALAWI                         Control              NA                 0.1780865    0.0477596    0.2905764
[50-57.5)   6-24 months   ki1148112-LCNI-5            MALAWI                         Control              NA                 0.1551522   -0.2862157    0.4450637