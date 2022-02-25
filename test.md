---
description: PARSER=GFM
---

# Choosing the Correct LOINC for Estimated Glomerular Filtration Rate

Author: David Baorto, MD, PhD\
Date Written: 2022-01-25

### Estimated Glomerular Filtration Rate

The glomerular filtration rate can be estimated based on the concentration of creatinine or cystatin C. Estimates are derived from equations that incorporate demographic variables such as age, sex and race. In August of 2020, the National Kidney Foundation and the American Society of Nephrology established a task force to reassess the inclusion of race. (A Unifying Approach for GFR Estimation: Recommendations of the NKF-ASN Task Force on Reassessing the Inclusion of Race in Diagnosing Kidney Disease, DOI: [https://doi.org/10.1053/j.ajkd.2021.08.003](https://doi.org/10.1053/j.ajkd.2021.08.003)). The outcome of this task force was the creation of new equations without a race-based variable ([New Creatinine- and Cystatin C–Based Equations to Estimate GFR without Race, DOI: 10.1056/NEJMoa2102953](https://www.nejm.org/doi/full/10.1056/NEJMoa2102953)). The task force recommends immediate implementation of these new equations in all United States laboratories. The American Association of Clinical Chemistry is publishing guidance on implementation [National Kidney Foundation Laboratory Engagement Working Group Recommendations for Implementing the CKD-EPI 2021 Race-Free Equations for Estimated Glomerular Filtration Rate: Practical Guidance for Clinical Laboratories](https://academic.oup.com/clinchem/advance-article/doi/10.1093/clinchem/hvab278/6463626).

### New equations

LOINC terms for the new equations refer either to the creatinine-based formula or the creatinine and cystatin C-based formula. To preserve historical integrity in medical records, it is advisable to create a new result field within the laboratory information system (LIS) when a calculation has changed. Distinct result fields allow for correct LOINC term(s) to be applied over time. The new test result will need to be mapped to a new LOINC code, depending on the type of formula used, the creatinine-only 2021 CKD formula or the creatinine-and-cystatin 2021 CKD formula.

| LOINC Code                           | Component                                      | Property | Timing | System       | Scale | Method                                              | Short Name                       |
| ------------------------------------ | ---------------------------------------------- | -------- | ------ | ------------ | ----- | --------------------------------------------------- | -------------------------------- |
| [98979-8](https://loinc.org/98979-8) | Glomerular filtration rate/1.73 sq M.predicted | ArVRat   | Pt     | Ser/Plas/Bld | Qn    | Creatinine-based formula (CKD-EPI 2021)             | eGFRcr SerPlBld CKD-EPI 2021     |
| [98980-6](https://loinc.org/98980-6) | Glomerular filtration rate/1.73 sq M.predicted | ArVRat   | Pt     | Ser/Plas/Bld | Qn    | Creatinine and Cystatin C-based formula (CKD-EPI 2) | eGFRcr-cys SerPlBld CKD-EPI 2021 |

#### Mapping Guidance

Consult with the clinical chemist, medical director, or pathologist to determine if the lab is using one of the equations recommended by the National Kidney Foundation-American Society of Nephrology Task Force in 2021, or an earlier equation.

If transitioning to the new 2021 calculations, note there are separate equations for male and female patients that need to be implemented. The same LOINC code is applied regardless of which sex-based equation is used to generate the result. Laboratories need to build each male and female equation within their LIS and validate per their accreditation requirements. Many LISs can support multiple equations (such as in this case) and apply the result value to a single laboratory result component. A new test result needs to be built within the LIS, EHR and any other information systems receiving the new calculated result values.

Laboratory processes will be similar to transitioning to a new test kit or method and similar laboratory compendium, LIS and interface updates. Changes need to be communicated to end users so updates can be made in their systems and communicated to all those using the results from the new eGFR formulas accordingly. Clinical decision making may be impacted as well.

While LOINC does not have a specific code for reporting the exact equation used to calculate eGFR, it may be appropriate for labs to transmit this information as part of the information contained in the result comment field. The individual laboratory should determine whether it is better to include the equation, or the author(s) of the equation, to identify the method used to perform the eGFR calculation.

### Earlier equations

The LOINC terms for eGFR with a specimen type of Ser/Plas/Bld are distinguished by the COMPONENT and METHOD attributes. The Committee acknowledges metabolic panel elements (Na, K, Glucose, etc) may use LOINC terms of Ser/Plas specimens alongside an eGFR term with specimen of Ser/Plas/Bld.

Existing LOINC content for this type of testing may be updated to have a status of discouraged to help guide users to the current NKF-ASN recommended equations. Please review the definition for the discouraged status in section 11.2 Classification of LOINC term status of the LOINC Users' Guide to better understand how the status value should be used in identifying the correct LOINC code based on the mapping use case.

#### Component attributes

* Is the patient value normalized by a standard 1.73 sq M body surface area? Use component of Glomerular filtration rate/1.73 sq M.predicted
* Is the result specific to a patient’s race (black/non black) or sex (female/male)? Note the new 2021 calculations have separate male/female calculations but there is only one LOINC term. Past methodology had separate LOINCs.

#### Method attributes

* Which equation does the laboratory use?
* Schwartz formula for Pediatrics - The original paper by G.F. Schwartz, et al, _A Simple Estimate of GFR in Children Using Body Length and Plasma Creatinine_, Pediatrics 1976;58:259-263, has become more relevant in the last few years because the Modification of Diet in Renal Disease (MDRD) formula below is specifically NOT applicable to patients under 18 years of age. The Schwartz formula depends on age, sex, and body height and serum creatinine. The Schwartz method LOINC uses the component attribute of Glomerular filtration rate.predicted

| LOINC Code                           | Component                                      | Property | Timing | System       | Scale | Method                              |
| ------------------------------------ | ---------------------------------------------- | -------- | ------ | ------------ | ----- | ----------------------------------- |
| [50384-7](http://loinc.org/50384-7/) | Glomerular filtration rate/1.73 sq M.predicted | ArVRat   | PT     | Ser/Plas/Bld | Qn    | Creatinine-based formula (Schwartz) |

* MDRD (4 or 6 variable) Modification of Diet in Renal Disease - Stoves J, Lindley E, Barnfield M, Burniston T, Newstead C. MDRD equation estimates of glomerular filtration rate in potential living kidney donors and renal transplant recipients with impaired graft function. Nephrol Dial Transplant.2002,17: 2036-2037

| LOINC Code                            | Component                                                | Property | Timing | System       | Scale | Method                          |
| ------------------------------------- | -------------------------------------------------------- | -------- | ------ | ------------ | ----- | ------------------------------- |
| [33914-3](http://loinc.org/33914-3/)  | Glomerular filtration rate/1.73 sq M.predicted           | ArVRat   | Pt     | Ser/Plas     | Qn    | Creatinine-based formula (MDRD) |
| [48642-3](http://loinc.org/48642-3/)  | Glomerular filtration rate/1.73 sq M.predicted.non black | ArVRat   | Pt     | Ser/Plas/Bld | Qn    | Creatinine-based formula (MDRD) |
| [48643-1](http://loinc.org/48643-1/)  | Glomerular filtration rate/1.73 sq M.predicted.black     | ArVRat   | Pt     | Ser/Plas/Bld | Qn    | Creatinine-based formula (MDRD) |
| [50044-7](https://loinc.org/50044-7/) | Glomerular filtration rate/1.73 sq M.predicted.female    | ArVRat   | Pt     | Ser/Plas/Bld | Qn    | Creatinine-based formula (MDRD) |

* Cystatin-based - _Estimating Glomerular Filtration Rate in Kidney Transplantation: A Comparison between Serum Creatinine and Cystatin C-Based Methods_, J Am Soc Nephrol 16: 3763–3770, 2005. This study demonstrates a comparison between the cystatin C–based prediction equations of Le Bricon, Filler, Hoek, and Larsson with the conventional creatinine-based equations of MDRD, Cockcroft-Gault, Nankivell, Walser, Jelliffe, and Mawer. Importantly, the Filler equation and, to a lesser degree, the Le Bricon equation performed well at GFR values both above and below 60 ml/min per 1.73 m2.

| LOINC Code                           | Component                                      | Property | Timing | System       | Scale | Method                 |
| ------------------------------------ | ---------------------------------------------- | -------- | ------ | ------------ | ----- | ---------------------- |
| [50210-4](http://loinc.org/50210-4/) | Glomerular filtration rate/1.73 sq M.predicted | ArVRat   | Pt     | Ser/Plas/Bld | Qn    | Cystatin-based formula |