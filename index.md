---
title: "Pitch presentation Shiny App"
author: "David Clijsters"
highlighter: highlight.js
output: html_document
job: Coursera Student
knit: slidify::knit2slides
mode: selfcontained
hitheme: tomorrow
subtitle: Visual regression analysis of mtcars
framework: io2012
widgets: {rCharts: [libraries/nvd3]}
---

## Where did the idea come from

The course project in Regression models made me think about the analysing I was doing on the **mtcars** dataset.

There should be a more intuitive, automated way of doing the same analysis.

So that's where the App was born...

<div style='text-align: center;'>
  <img class="alignnone size-full wp-image-1760" src="http://donpower.me/wp-content/uploads/2013/01/Eureka-Idea-Light-Bulb1.jpg" width="550" height="335">
</div>

---

## What does the Shiny App do

The application builds a **pairs plot** and performs a short **regression analysis based** on the selected variables (at least 2) in the checkboxes.

Pairs plots are particularly usefull to analyse in a visual way the relation between 2 or more variables. It gives an indication of which variables to include in the regression model.

The outcome of the regression is always 'mpg', whether selected or not.

The regression analysis consists of calculating R² and determining the estimated values of the intercept and multipliers for the selected variables.
The higher the R², the better the fit... but be thoughtful on this...an small increase of R² by adding another variable might not be worth incorporating the variable.

---

## An example

When selecting wt and hp in the checkboxes, the following calculations are done in the background. R² and the estimated coefficients are calculated.


```r
data(mtcars)
fit <- lm(mpg ~ wt+hp, data=mtcars)
summary(fit)$r.squared
```

```
## [1] 0.8268
```

```r
summary(fit)$coef
```

```
##             Estimate Std. Error t value  Pr(>|t|)
## (Intercept) 37.22727    1.59879  23.285 2.565e-20
## wt          -3.87783    0.63273  -6.129 1.120e-06
## hp          -0.03177    0.00903  -3.519 1.451e-03
```


---

## Further development opportunities

* Loading other datasets
* Make interaction between variables possible
* Using other models, reporting more statistics, better layout
* Adding Graphical reporting (residual plots, ...)

<iframe src=' assets/fig/unnamed-chunk-2.html ' scrolling='yes' frameBorder='0' seamless class='rChart polycharts ' id=iframe- chart1efc3d5a28ec ></iframe> <style>iframe.rChart{ width: 100%; height: 400px;}</style>


---

## Going to the App: happy exploring!

<div align="center">
<iframe 
src="http://clijda.shinyapps.io/mtcars_reganal/" >
  </iframe></div>


