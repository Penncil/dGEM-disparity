
A One-shot Federated Learning algorithm to quantify racial disparities in mortality rates with kidney transplant using US registry data from 35,497 patients across 201 hospitals
==============================================


## Outline
1. Description
2. dGEM-disparity workflow


## Description
Kidney transplant is a renal replacement therapy for eligible patients with end-stage renal disease (ESRD)1–3. Unfortunately, the racial disparities in receipt of a transplanted kidney are observed for the Black across states4. Black patients are recognized to have lower graft survival rates compared with White patients5–8. Therefore, there is a great need in understanding, quantifying, and reducing the racial disparities in access to transplant and post-transplant outcomes for kidney transplant patients. 

Site of care has been considered as a major contributor to disparities in kidney transplants due to differences in time on the transplant waiting list, access to live donor kidney transplants, care coordination with the donor organ procurement system, and acute rejection rates9. Since racial groups tend to live in certain areas, they may be subject to varying transplant care, leading to the difference in the outcomes (e.g., kidney graft failure)10. 

To study the potential association between the site of care and racial disparity in kidney transplant graft failure with multi-site data, a counterfactual modeling method can be implemented11. By considering the underlying distribution in which patients of different races receive care, we can use a counterfactual model to simulate patients from a certain transplant center getting admitted to another. For example, with the proportions of White patients at the studied centers, we can simulate the reassignments for Black patients with the same proportions within the hospitals hypothetically. Under this scenario, the Black patients are pretended to attend the hospitals in the same distribution as the White patients. The observed and counterfactual kidney graft failure rates can be calculated, and the hypothesis is that the counterfactual graft failure rates would be lower than the observed graft failure rates for the Black patients if there exist site-of-care-associated racial disparities for the Black patients in kidney transplants.

This counterfactual modeling has been recently implemented in the study by Asch et al (2020)12 to explore racial disparities for patients hospitalized with COVID-19 infection. In this study, a Health Quality Forum certified generalized linear mixed model (GLMM) was fitted on a centralized multi-site data to characterize the odds of the event with the adjustments for both fixed (e.g., the effects of patient- and hospital-level factors) and random effects (e.g., hospital-specific effects). In studying the effect of site of care on an event rate (e.g., COVID-19 mortality rate, kidney graft failure rate), the hospital-specific effects are essential in the calculation of counterfactual event rate. However, when the multi-site data cannot be centralized, the utilization of centralized modeling is not achievable, leading to challenges in estimating the hospital-specific effects. When the patient-level data are stored in a decentralized format and only aggregated data are allowed to be shared across hospitals, a decentralized algorithm for GLMM is in critical need.

We proposed a framework of federated learning algorithm to investigate the association between the site of care and racial disparities in kidney graft failure for Black patients. We termed this framework as dGEM-disparity, which stands for decentralized algorithm for Generalized linear mixed Effect Model for disparity quantification. dGEM-disparity is a federated learning framework to effectively integrate heterogeneous multi-site data by fitting generalized mixed effect models. It allows us to investigate the site-of-care-associated racial disparity by considering the patients who are hypothetically admitted to other hospitals.


## dGEM-disparity workflow 
<img width="800" alt="image" src="https://user-images.githubusercontent.com/38872447/174927996-2a4045fa-701e-4a89-b195-401f31da9a42.png">

