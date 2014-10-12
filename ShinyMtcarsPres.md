ShinyMtcars
========================================================
author: Cristian Vlad
date: 2014-10-12
transition: rotate

Description
========================================================
The application aims to filter the mtcars dataset based on selections that the user makes in the left sidebar controls:
- a slider on Miles Per Gallon
- and a combo box on the number of carburetors, dynamically fed as result of slider's selection


ui.R
========================================================
transition: fade

The page layout defined in the ui.R file is based on the function pageWithSidebar.

In order to populate the carburetors' combo box as a function of the mpg selected by the slider, the function used in this file is uiOutput.


server.R
========================================================

The server.R file contains code to be evaluated server side.

The logic that it implements consists in two pieces:
1. refreshes the carburetor's combo box in function of the selected mpg
2. filters the mtcars dataset in function of the selection in the two controls on the left.

The combo box control is generated using the renderUI function, while the result table is rendered through the renderTable function.


Dynamic selection of the values in the combo box
========================================================
<small>
The values in the carburetors' combo box are filtered in function of the slider's vector of values.

The function used in this sense is 


```r
carbs <- function(sliderMpg){
    return(sort(unique(subset(mtcars, mpg >= sliderMpg[1] & mpg <= sliderMpg[2], carb))[,1]))
}
```

For example, for a slider value of c(20, 37) it returns

```r
sliderMpg <- c(20, 27)
sort(unique(subset(mtcars, mpg >= sliderMpg[1] & mpg <= sliderMpg[2], carb))[,1])
```

```
[1] 1 2 4
```
</small>
