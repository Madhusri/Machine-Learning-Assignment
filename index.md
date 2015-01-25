---
title       : Developing Data Products Course Project 
subtitle    : 
author      : Madhuri
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : standalone # {selfcontained, draft}
knit        : slidify::knit2slides
---

## Slidify Presentation



The aim of the presentation is to use slidify and Rstudio presenter to pitch the Shiny App that was created as part of the Course Project.

--- .class #id 

## About the Application



The Shiny App developed shows the Histograms for Normal and Exponential Distributions where the mean and standard deviations are given and set to defualt. The sample size range from 100 to 10000, with a step increase of 1000 per sample.

---.class #id

## How it works

For the Normal Distribution,as the sample size increases the data tends to be around a central value, here mean = 10, So Symmetry is around the center with 50% of the values below the mean and 50% of the values above the mean.

For the Exponential Distribution, the values are more streched out as the mean value decreases. The mean here is defualt to 1.

The application can be accessed here:
https://madhusri.shinyapps.io/APP1/

--- .class #id


## Underlying Code


```r
 function(input, output, session){
    
    output$myplot <- renderPlot({
            
      distType <- input$Distribution
      size <- input$sampleSize
      
      if(distType == "Normal"){
      randomVec <- rnorm(size, mean = as.numeric(input$mean), sd = as.numeric(input$sd))
       
      }
      else {
        randomVec <- rexp(size, rate = 1/ as.numeric(input$lambda))
      }
      
      hist(randomVec, col = "blue")
    })
  }
```

```
## function(input, output, session){
##     
##     output$myplot <- renderPlot({
##             
##       distType <- input$Distribution
##       size <- input$sampleSize
##       
##       if(distType == "Normal"){
##       randomVec <- rnorm(size, mean = as.numeric(input$mean), sd = as.numeric(input$sd))
##        
##       }
##       else {
##         randomVec <- rexp(size, rate = 1/ as.numeric(input$lambda))
##       }
##       
##       hist(randomVec, col = "blue")
##     })
##   }
## <environment: 0x000000001bcdbb30>
```




