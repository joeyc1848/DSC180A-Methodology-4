---
layout: default
title: Methodology Assignment 4
---

# Joseph Calderon

**UCSD email:** [jscalderon@ucsd.edu](mailto:jscalderon@ucsd.edu)  
**Section:** D10  
**Mentors:** Jeff Candy, Emily Belli, and Igor Sfiligoi

## Quarter 2 project reflections

**What is the most interesting topic covered in your domain this quarter?**

The topic I find most interesting is how to tell when a fast plasma-transport surrogate can be trusted. Our Quarter 1 project approximates TGLF's ion heat, electron heat, and electron particle fluxes with machine learning models. The uncertainty work makes this more interesting than simply minimizing prediction error: models can agree with one another and still make the same mistake, especially under a change in plasma conditions. The DIII-D case study also shows why matching trends and matching the magnitude of fluxes are separate goals. I am interested in the connection between training-data coverage, ensemble disagreement, and the physical behavior of the predicted fluxes.

**Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

I would investigate whether active learning can improve a TGLF surrogate more efficiently than adding randomly selected training cases. Starting from a fixed initial subset of the DIII-D database, I would compare random acquisition with acquisition based on ensemble disagreement and with a strategy that combines disagreement and input-space diversity. Each strategy would receive the same number of additional TGLF evaluations. For an initial, affordable experiment, I would hide labels in the existing database and reveal them only when a strategy selects a case. I would keep a separate test set fixed and compare per-flux error, signed bias, interval coverage and width, and training and prediction time as the labeled-data budget grows. Repeated seeds would show whether an advantage is consistent. The main output would be a reproducible comparison and a report on when targeted sampling helps; running new simulations would be an extension after checking compute access and cost. This would test a new data-selection question beyond the current fixed-dataset comparisons.

**What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

I would make a shared evaluation protocol the starting point for all model comparisons. Our current experiments use different splits, model settings, and interval methods, which limits how confidently we can attribute a difference to the model itself. I would reserve fresh assessment cases, fit transformations only on training data, and use distinct tuning and uncertainty-calibration subsets. Alongside a random split, I would include a blocked test that withholds a radial region or a plasma-parameter regime, with nearby cases kept together. I would report errors and calibration by flux and regime, including low-flux behavior and the sign of particle flux, rather than relying on a single average score. This would make the comparison more useful for deciding where a surrogate needs more training data or a direct TGLF check.

**What other techniques would you be interested in using in your project?**

I would be interested in conformal calibration, input-domain diagnostics, and sensitivity analysis. Conformal calibration could turn held-out residuals into an explicit interval-calibration baseline, which I would compare with our ensemble and quantile intervals. Its usual coverage guarantee depends on exchangeability, so I would measure coverage separately on shifted plasma conditions rather than assume the guarantee transfers. A nearest-neighbor distance or density estimate in standardized input space could provide a second warning signal when ensemble disagreement is small. Finally, controlled gradient scans and sensitivity analysis could test whether the surrogate responds plausibly to changes in temperature and density gradients. I would prioritize these checks before adding a much larger network, because they address reliability and help explain where new simulations would be most valuable.

## Project context

These reflections build on our [Quarter 1 project repository](https://github.com/lindbergryan04/dsc180a-project-1) and its [checkpoint report](https://github.com/lindbergryan04/dsc180a-project-1/blob/main/report/report.tex). The proposed investigation is a possible extension, with feasibility to be discussed with the mentors. I reviewed the [Quarter 2 proposal specifications](https://dsc-capstone.org/2026-27/assignments/projects/q2-proposal/) when choosing a bounded research question and deliverable.
