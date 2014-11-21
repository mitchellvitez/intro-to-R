intro-to-R
==========

*Based on my notes after using and learning about R for only a few weeks*

R has lots of statistical packages. It's good for graphing, matrix math, data tables, and the like.

It has somewhat poor error handling. Rather than breaking, it will tend to do *something*, even if that something makes no sense.

Naming
------
R variables can contain alphanumeric characters plus `.` and `_`

Data Types
----------
* Strings
* Numerics
* Factors
  * Has levels for each item
  ```
    xyxxyxx
    1211211
    
    levels: x = 1, y = 2
  ```
* Matrices
  * 1d or 2d
  * Vector is 1d matrix made by 
    ```
    c(x, y, z...)
    ```
* Data Frames
  * Unlike matrices, can have different data types per column

Indexing
--------
Indexing starts at 1 (as in matlab/octave), not at 0 like in many other programming languages

`mat[2, 1]` row 2, column 1

`mat[3,]` row 3, all columns

`vec[-5]` Give me everything in vec except the fifth item

`rownames()  colnames()  names()` Can get or set headers for rows, columns, or items in a matrix/vector/frame

`mat["row2name", "col4"]` Can index by strings using row/col names instead of numbers

`df$col1   df$col3[4]` No quotes needed, index columns with $ after data frame name. Only works on data frames

Assignment
----------
Use `=` only in parameters

Use `<-` everywhere else

:warning:`if(x<-5)` returns true. It is an assignment, and not the same as `if(x < -5)`

Correlation
-----------
The cor() function is a good example, so we'll use it here.

`cor.test()` returns an object. To get values, you must index in using `$estimate` or `$p.value`

Functions
---------
```R
mult <- function (a, b, c) {
  return(a * b * c)
}
```

Load Data
---------
Use `read.table()` to read in spreadsheets in .csv, tab separated, etc.

Use flags `strip.white=TRUE` and `stringsAsFactors=FALSE` to remove extra whitespace and avoid using those pesky factors (see [Data Types]())

Join Data
---------
`rbind()` and `cbind()` join by rows and columns, respectively

Error Handling
----------
Use `stopifnot(a == 1)` to test your assumptions (like `assert()` in other languages)

`source("functions.R")` lets you use things in `functions.R` elsewhere. This helps you break up files for easier testability

Use `NA.rm=TRUE` to ignore results that are `NA`

Sorting
-------
`order()` gives the sorted indices of items (first the index of the lowest, then the index of the second lowest, etc.)

Also `sort()` and `rank()`

`x[order(x)]` returns x in sorted order

`rev()` reverse order
