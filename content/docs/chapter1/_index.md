---
# Title, summary, and page position.
linktitle: Chapter 1
summary: Learn how to use Wowchemy's docs layout for publishing online courses, software documentation, and tutorials.
weight: 1
icon: book
icon_pack: fas

# Page metadata.
title: Chapter 1
date: '2018-09-09T00:00:00Z'
type: book # Do not modify.
---

## Introduction

  - In general, when we model time dependent data we don't usually have to worry about having errors in the time variable
  
  - But that is not the case when the time dependent data is a reconstruction (e.g., a sea level reconstruction)

  - In my research, usually on the analysis of sea-level reconstructions, I use the output from age-depth models (e.g., Bchron, Bacon) which provide age estimates with uncertainty for core sediment samples.
  
  - So, here I will explore the impact of this age uncertainty in the statistical modelling of time dependent data. 
  
  

## Model Specification 

I use a Bayesian approach to statistical modelling and when it comes to the specifying the Bayesian model recipe, the ingredients are

1. The process model
2. The data model (likelihood)
3. The priors

Combining the priors and the data model gives us the posterior. The posterior tells us everything we need to know about what we are trying to estimate. 


## Model Specification Cont. 
  
  - The process model relates to the expectation of what’s underlying the observed data (i.e., "the truth"). The process model will be governed by a set of explanatory variables and parameters that need to be estimated.
  
 <span style="color: #E69F00;"> __Expected Y = f(parameters,x)__</span>

  - The data model contains assumptions about how the data are generated and incorporates data uncertainty. The data model links the observed data to the underlying process.
  
  <span style="color: #009E73;"> __Uncertain Data (Y) = Expected Y + error__</span>
  
  - The priors contain assumptions about the parameters we are estimating. Priors can be used to impose constraints on model parameters based on apriori information.

<span style="color: #CC79A7;"> __Priors = Constraints__</span>

## A Modelling Option: Simple Linear Regression
\footnotesize


<!-- <font size="3"> -->

<span style="color: #E69F00;"> __Expected Y = f(parameters,x), where f = linear__</span>


  $$\text{Expected} Y = \alpha + \beta Age$$

<span style="color: #009E73;"> __Y = Expected Y + error, where error $\sim$ Normal__</span>


$$Y = \alpha + \beta Age + error$$

$$error \sim Normal(0, \sigma_{Y})$$


<span style="color: #CC79A7;"> __Priors = Constraints__</span>

  - We might assume we don't know much about $\alpha$ and $\beta$
   
  - $\sigma_{Y}$ must be positive

<!-- </font> -->


## What happens when x has associated errors? 
\footnotesize
Instead of 
$$\text{Expected } Y  = \alpha + \beta Age$$
What we want is 
$$\text{Expected } Y = \alpha + \beta Age^{TRUE}$$

But we don't know $Age^{TRUE}$ `r emo::ji("sad")`


## We can use an Errors-in-Variables (EIV) approach `r emo::ji("happy")`

We can again assume that

 <span style="color: #009E73;"> __X = Expected X + error, where error $\sim$ Normal__</span>

$$Age = Age^{TRUE} + error$$

$$error \sim Normal(0, \sigma_{Age})$$

<span style="color: #CC79A7;"> __Priors = Constraints__</span>

We need a prior for $Age^{TRUE}$ with a plausible range.
  
This is called an __Errors-in-Variables__ model. 



