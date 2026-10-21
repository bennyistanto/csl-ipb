---
title         : A Hybrid Bias Correction Framework for Daily Satellite Precipitation
subtitle      : Excerpt, rendered with ipb_en.csl
author        : Benny Istanto
date          : 2026
bibliography  : references.json
csl           : ../ipb_en.csl
link-citations: true
css           : https://cdn.jsdelivr.net/gh/kognise/water.css@latest/dist/light.min.css
---

> This is an excerpt from the author's MSc thesis at IPB University: the opening of the Summary and section 1.1
> (Background) of the Introduction. It shows `ipb_en.csl` on real thesis text. The full thesis is at
> [doi:10.5281/zenodo.21996372](https://doi.org/10.5281/zenodo.21996372), licensed under
> [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The references were taken from the thesis and cleaned for
> CSL: access dates in ISO form and journal-article titles in sentence case, as the guide asks.

# Summary {#summary .unnumbered}

Daily satellite precipitation underpins flood early warning, drought monitoring, and water-budget analysis, but the Integrated Multi-satellitE Retrievals for Global Precipitation Measurement Late Run (IMERG-L) carries systematic biases over the Indonesian Maritime Continent. This thesis evaluates a four-stage hybrid bias correction pipeline: Linear Scaling (LS), Empirical Quantile Mapping (EQM) with a Gamma fit, Generalized Pareto Distribution (GPD) tail adjustment, and a station-density-aware Convolutional Neural Network (CNN) refinement, a Deep Learning (DL) architecture, denoted LSEQM+DL. The pipeline is applied to IMERG-L over Indonesia across 2001 to 2025, with gauge validation against 172 out-of-sample stations of Indonesia's Meteorological, Climatological, and Geophysical Agency (BMKG) over 2001 to 2021.

**Keywords:** daily satellite precipitation, gauge validation, hybrid bias correction, IMERG, reproducibility

# Background {#background .unnumbered}

Daily-scale precipitation estimates underpin flash-flood early warning, reservoir release scheduling, drought monitoring, crop water budgeting, and disaster risk assessment. For most of the global land surface, the only source of spatially continuous daily precipitation is the satellite family of products. The Integrated Multi-satellitE Retrievals for the Global Precipitation Measurement mission (IMERG) is the flagship multi-satellite product of the GPM era [@ref:hou2014; @ref:huffman2020]. Its version 7 (V07) release is the current recommended version, used here; it succeeds the version 6 generation that the published algorithm documentation describes. Among its variants, the Late Run (IMERG-L) is the one suited to near-real-time use: its latency of approximately 14 hours fits within the same-day decision window of operational flood and drought services, where the gauge-merged Final Run, released months later, is not yet available. Because IMERG-L relies on satellite observations without gauge assimilation, it also provides an uncontaminated baseline against which a bias correction can be evaluated.

IMERG-L carries systematic biases against gauge observations. Three modes recur across validation studies: over-detection of light rain, in which the satellite reports drizzle on days the gauge records as dry; under-detection of heavy events, in which the satellite truncates the upper tail that drives flood thresholds; and a full distributional mismatch in which the shape of the daily rainfall distribution departs from the gauge distribution [@ref:maggioni2016; @ref:tang2020]. These biases are consequential everywhere, but they are acute over the tropical Maritime Continent, where convective rainfall dominates the seasonal cycle and the contributing gauge network is dense only over Java and southern Sumatra, thinning sharply toward Maluku and Papua [@ref:chen2008; @ref:rahmawati2021; @ref:ramadhan2022; @ref:mashuri2025].

Four families of statistical and machine-learning methods have been developed to correct these biases, each addressing a distinct dimension. Linear Scaling corrects the mean through a single multiplicative factor [@ref:teutschbein2012]; Empirical Quantile Mapping with a parametric fit aligns the full marginal distribution [@ref:gudmundsson2012; @ref:themessl2012]; Generalized Pareto Distribution tail adjustment grafts an extreme-value model onto the upper tail [@ref:coles2001]; and Convolutional Neural Networks refine the residual spatial structure of extreme pixels [@ref:pan2019; @ref:banomedina2020]. A hybrid pipeline that integrates all four in sequence, denoted LSEQM+DL (Linear Scaling (LS), Empirical Quantile Mapping (EQM), Generalized Pareto Distribution (GPD), and Convolutional Neural Network (CNN) refinement, a Deep Learning (DL) architecture), has been applied to IMERG-L over Indonesia in a parallel paper [@ref:istanto2026mdpi] and is the subject of this thesis. The detailed review of these method families and their known limits is given in Chapter II of the thesis.

Two gaps in the bias correction literature motivate the present study. The first is a verification gap. Most bias correction studies report an aggregate skill improvement and stop there, without attributing the movement of individual metrics to the specific correction stage responsible, and without testing the result against gauges that are independent of the correction reference. As a consequence, it is often unclear which bias dimension a given pipeline actually corrects, and whether the reported skill survives a comparison against truly out-of-sample observations.

The second is a reproducibility gap. Independent verifiability has become a methodological expectation in computational science [@ref:peng2011; @ref:stodden2014; @ref:wilkinson2016], but the bias correction literature has adopted it unevenly: many influential studies publish a method without releasing the code or data. This thesis is organised around closing both gaps at once.

Within the first of these gaps, one bias dimension is especially prone to being hidden by an aggregate score, and it is the focus of a specific contribution here. Bias correction and gauge merging are most established at the monthly scale, where satellite and gauge totals correlate strongly; at the daily scale the day-to-day correlation is markedly lower and is repeatedly cited as the limiting factor [@ref:tang2020; @ref:ramadhan2022ts; @ref:ramadhan2023]. Part of that low daily correlation is not a deficiency of the satellite but a mismatch of accumulation windows: the satellite archive accumulates over the UTC day, whereas gauges report over the local day ending at a fixed morning observation. The mismatch is recognised in validation studies, which align the accumulation period to the gauge convention [@ref:salio2015; @ref:li2018; @ref:tan2019; @ref:xie2022]. Yet to our knowledge it has not been carried into the bias-correction step: satellite-precipitation bias corrections over Southeast Asia, including the Indonesian archipelago [@ref:wang2026], and across the wider region [@ref:yang2022; @ref:iqbal2022; @ref:wei2022] adjust rainfall magnitudes against a fixed daily window without re-aligning it to the gauge reporting convention.

# References {.unnumbered}
