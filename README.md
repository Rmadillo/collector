
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Collector <img alt="Collector Logo" title="Collector" align="right" src="man/figures/collector_logo.png" width="100" style="float:right;width:100px;"/>

[![Travis Build
Status](https://travis-ci.org/davidski/collector.svg?branch=master)](https://travis-ci.org/collector/evaluator)
[![AppVeyor Build
Status](https://ci.appveyor.com/api/projects/status/github/davidski/collector?branch=master&svg=true)](https://ci.appveyor.com/project/collector/evaluator)
[![Coverage
Status](https://codecov.io/gh/davidski/collector/branch/master/graph/badge.svg)](https://codecov.io/github/davidski/collector?branch=master)
[![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/collector)](https://cran.r-project.org/package=colector)
![downloads](https://cranlogs.r-pkg.org/badges/grand-total/collector)

**collector** is an R package for conducting interviews with subject
matter experts (SMEs) on the risk scenarios facing an organization. It
offers functions for the following stages of input collection:

  - generate scenario and capability questions
  - building interview artifacts, including progress card, slide decks,
    and handouts
  - calibration testing, similar to that promoted by Doug Hubbard and
    the FAIR Institute
  - opinion pooling
  - distribution fitting
  - generating quantitative data structures for simulation and further
    reporting by [Evaluator](https://evaluator.severski.net)

## Installation

Collector is not currently on CRAN. The following sample code to install
will not work until a release is made to CRAN.

``` r
install.packages("collector")
```

If you wish to run the development (and potentially bleeding edge)
version of Collector, you can install directly from Github via the
following `devtools` command.

``` r
# install.pacakges("devtools")
devtools::install_github("davidski/collector", dependencies = TRUE)
```

## Basic Flow

Documentation is still very much a pending To Do. Until documentation is
authored, use the [package website](https://collector.severski.net) for
reference. The flow for running interviews and sending along to
[evaulator](https://evaluator.severski.net) is:

1.  Build questions and define SME expertise

2.  Read in the data
    
    ``` r
    library(collector)
    
    dat <- read_data(source_dir)
    calibration <- dat$calibration
    domains <- dat$domains
    scenarios <- dat$scenarios
    capabilities <- dat$capabilities
    expertise <- dat$expertise
    ```

3.  Generate
    slides
    
    ``` r
    make_handouts("Leader Name", calibrarion, domains, expertise, scenarios, capabilities, output_dir)
    make_bingo("Leader Name", domains, expertise, output_dir)
    make_slides("Leader Name", source_dir, output_dir)
    ```

4.  Input answers

5.  Fit SME answers
    
    ``` r
    scenario_answers_fitted <- fit_scenarios(scenario_answers)
    capability_answers_fitted <- (capability_answers)
    ```

6.  Combined distributions into final
    parameters
    
    ``` r
    scenario_parameters <- combine_scenario_parameters(scenario_answers_fitted)
    capability_parameters <- combine_capability_parameters(capability_answers_fitted)
    ```

7.  Build quantitative parameters for
    `Evaluator`
    
    ``` r
    prepare_data(scenario_parameters, capability_parameters, threat_parameters, 
                 scenarios, domains)
    ```

## Contributing

This project is governed by a [Code of Conduct](CODE_OF_CONDUCT.md). By
participating in this project you agree to abide by these terms.

## License

The [MIT License](LICENSE) applies.
