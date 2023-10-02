# Homework_5

## Question 1

``` r
library(tidyverse)
students <- read_csv("data/r4ds_main_data_students.csv")
students <- read_csv("data/r4ds_main_data_students.csv", na = c("N/A",""))
glimpse(students)
```

    Rows: 6
    Columns: 5
    $ `Student ID`   <dbl> 1, 2, 3, 4, 5, 6
    $ `Full Name`    <chr> "Sunil Huffmann", "Barclay Lynn", "Jayendra Lyne", "Leo…
    $ favourite.food <chr> "Strawberry yoghurt", "French fries", NA, "Anchovies", …
    $ mealPlan       <chr> "Lunch only", "Lunch only", "Breakfast and lunch", "Lun…
    $ AGE            <chr> "4", "5", "7", NA, "five", "6"

``` r
students |> 
  rename(student_id = 'Student ID',
         full_name = 'Full Name')
```

    # A tibble: 6 × 5
      student_id full_name        favourite.food     mealPlan            AGE  
           <dbl> <chr>            <chr>              <chr>               <chr>
    1          1 Sunil Huffmann   Strawberry yoghurt Lunch only          4    
    2          2 Barclay Lynn     French fries       Lunch only          5    
    3          3 Jayendra Lyne    <NA>               Breakfast and lunch 7    
    4          4 Leon Rossini     Anchovies          Lunch only          <NA> 
    5          5 Chidiegwu Dunkel Pizza              Breakfast and lunch five 
    6          6 Güvenç Attila    Ice cream          Lunch only          6    

``` r
students |> mutate(mealPlan = factor(mealPlan))
```

    # A tibble: 6 × 5
      `Student ID` `Full Name`      favourite.food     mealPlan            AGE  
             <dbl> <chr>            <chr>              <fct>               <chr>
    1            1 Sunil Huffmann   Strawberry yoghurt Lunch only          4    
    2            2 Barclay Lynn     French fries       Lunch only          5    
    3            3 Jayendra Lyne    <NA>               Breakfast and lunch 7    
    4            4 Leon Rossini     Anchovies          Lunch only          <NA> 
    5            5 Chidiegwu Dunkel Pizza              Breakfast and lunch five 
    6            6 Güvenç Attila    Ice cream          Lunch only          6    

``` r
students |> mutate(AGE = parse_number(if_else(AGE == "five", "5", AGE)))
```

    # A tibble: 6 × 5
      `Student ID` `Full Name`      favourite.food     mealPlan              AGE
             <dbl> <chr>            <chr>              <chr>               <dbl>
    1            1 Sunil Huffmann   Strawberry yoghurt Lunch only              4
    2            2 Barclay Lynn     French fries       Lunch only              5
    3            3 Jayendra Lyne    <NA>               Breakfast and lunch     7
    4            4 Leon Rossini     Anchovies          Lunch only             NA
    5            5 Chidiegwu Dunkel Pizza              Breakfast and lunch     5
    6            6 Güvenç Attila    Ice cream          Lunch only              6

## Question 2

``` r
Employee <- read_csv("data/Employee data.csv")
view(Employee)
glimpse(Employee)
```

    Rows: 474
    Columns: 10
    $ id       <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18…
    $ gender   <chr> "m", "m", "f", "f", "m", "m", "m", "f", "f", "f", "f", "m", "…
    $ bdate    <chr> "2/3/1952", "5/23/1958", "7/26/1929", "4/15/1947", "2/9/1955"…
    $ educ     <dbl> 15, 16, 12, 8, 15, 15, 15, 12, 15, 12, 16, 8, 15, 15, 12, 12,…
    $ jobcat   <dbl> 3, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 3, 1, 1, 1…
    $ salary   <dbl> 57000, 40200, 21450, 21900, 45000, 32100, 36000, 21900, 27900…
    $ salbegin <dbl> 27000, 18750, 12000, 13200, 21000, 13500, 18750, 9750, 12750,…
    $ jobtime  <dbl> 98, 98, 98, 98, 98, 98, 98, 98, 98, 98, 98, 98, 98, 98, 97, 9…
    $ prevexp  <dbl> 144, 36, 381, 190, 138, 67, 114, 0, 115, 244, 143, 26, 34, 13…
    $ minority <dbl> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0…

``` r
Employee |> 
  rename(Birth_date = 'bdate',
         job_category = 'jobcat',
         sal_begin = 'salbegin',
         job_time = 'jobtime',
         previous_exp = 'prevexp')
```

    # A tibble: 474 × 10
          id gender Birth_date  educ job_category salary sal_begin job_time
       <dbl> <chr>  <chr>      <dbl>        <dbl>  <dbl>     <dbl>    <dbl>
     1     1 m      2/3/1952      15            3  57000     27000       98
     2     2 m      5/23/1958     16            1  40200     18750       98
     3     3 f      7/26/1929     12            1  21450     12000       98
     4     4 f      4/15/1947      8            1  21900     13200       98
     5     5 m      2/9/1955      15            1  45000     21000       98
     6     6 m      8/22/1958     15            1  32100     13500       98
     7     7 m      4/26/1956     15            1  36000     18750       98
     8     8 f      5/6/1966      12            1  21900      9750       98
     9     9 f      1/23/1946     15            1  27900     12750       98
    10    10 f      2/13/1946     12            1  24000     13500       98
    # ℹ 464 more rows
    # ℹ 2 more variables: previous_exp <dbl>, minority <dbl>

``` r
Employee |> mutate(gender = factor(gender))
```

    # A tibble: 474 × 10
          id gender bdate      educ jobcat salary salbegin jobtime prevexp minority
       <dbl> <fct>  <chr>     <dbl>  <dbl>  <dbl>    <dbl>   <dbl>   <dbl>    <dbl>
     1     1 m      2/3/1952     15      3  57000    27000      98     144        0
     2     2 m      5/23/1958    16      1  40200    18750      98      36        0
     3     3 f      7/26/1929    12      1  21450    12000      98     381        0
     4     4 f      4/15/1947     8      1  21900    13200      98     190        0
     5     5 m      2/9/1955     15      1  45000    21000      98     138        0
     6     6 m      8/22/1958    15      1  32100    13500      98      67        0
     7     7 m      4/26/1956    15      1  36000    18750      98     114        0
     8     8 f      5/6/1966     12      1  21900     9750      98       0        0
     9     9 f      1/23/1946    15      1  27900    12750      98     115        0
    10    10 f      2/13/1946    12      1  24000    13500      98     244        0
    # ℹ 464 more rows

## Question 3a

``` r
read_csv("data/colloquium_assessment.csv")
```

    # A tibble: 36 × 25
       StartDate             EndDate Status Progress Duration (in seconds…¹ Finished
       <chr>                 <chr>   <chr>  <chr>    <chr>                  <chr>   
     1  <NA>                  <NA>    <NA>   <NA>     <NA>                   <NA>   
     2 "Start Date"          "End D… "Resp… "Progre… "Duration (in seconds… "Finish…
     3  <NA>                  <NA>    <NA>   <NA>     <NA>                   <NA>   
     4 "{\"ImportId\":\"sta… "{\"Im… "{\"I… "{\"Imp… "{\"ImportId\":\"dura… "{\"Imp…
     5  <NA>                  <NA>    <NA>   <NA>     <NA>                   <NA>   
     6 "11/11/22 9:01"       "11/11… "0"    "100"    "18"                   "1"     
     7  <NA>                  <NA>    <NA>   <NA>     <NA>                   <NA>   
     8 "11/11/22 9:02"       "11/11… "0"    "100"    "31"                   "1"     
     9  <NA>                  <NA>    <NA>   <NA>     <NA>                   <NA>   
    10 "11/11/22 9:03"       "11/11… "0"    "100"    "109"                  "1"     
    # ℹ 26 more rows
    # ℹ abbreviated name: ¹​`Duration (in seconds)`
    # ℹ 19 more variables: RecordedDate <chr>, ResponseId <chr>,
    #   RecipientLastName <chr>, RecipientFirstName <chr>, RecipientEmail <chr>,
    #   ExternalReference <chr>, LocationLatitude <chr>, LocationLongitude <chr>,
    #   DistributionChannel <chr>, UserLanguage <chr>, Q4 <chr>, Q5 <chr>,
    #   Q6 <chr>, Q7 <chr>, Q8 <chr>, Q9 <chr>, Q10 <chr>, Q11 <chr>, Q12 <chr>

``` r
header <- read_csv("data/colloquium_assessment.csv", n_max = 1)
Colloquium <- read_csv("data/colloquium_assessment.csv", skip = 5, col_names = FALSE)
names(Colloquium) <- names(header)
colloquium_no_na<- na.omit(Colloquium)
Colloquium <- Colloquium |>
  filter(!is.na(Colloquium[[1]]))|>
  rename(duration_in_seconds = 'Duration (in seconds)')
Colloquium |> 
  pivot_longer(cols = LocationLatitude:LocationLongitude,
               names_to = "Location", 
               values_to = "value")
```

    # A tibble: 32 × 25
       StartDate   EndDate Status Progress duration_in_seconds Finished RecordedDate
       <chr>       <chr>    <dbl>    <dbl>               <dbl>    <dbl> <chr>       
     1 11/11/22 9… 11/11/…      0      100                  18        1 11/11/22 9:…
     2 11/11/22 9… 11/11/…      0      100                  18        1 11/11/22 9:…
     3 11/11/22 9… 11/11/…      0      100                  31        1 11/11/22 9:…
     4 11/11/22 9… 11/11/…      0      100                  31        1 11/11/22 9:…
     5 11/11/22 9… 11/11/…      0      100                 109        1 11/11/22 9:…
     6 11/11/22 9… 11/11/…      0      100                 109        1 11/11/22 9:…
     7 11/11/22 9… 11/11/…      0      100                  40        1 11/11/22 9:…
     8 11/11/22 9… 11/11/…      0      100                  40        1 11/11/22 9:…
     9 11/11/22 9… 11/11/…      0      100                 243        1 11/11/22 9:…
    10 11/11/22 9… 11/11/…      0      100                 243        1 11/11/22 9:…
    # ℹ 22 more rows
    # ℹ 18 more variables: ResponseId <chr>, RecipientLastName <lgl>,
    #   RecipientFirstName <lgl>, RecipientEmail <lgl>, ExternalReference <lgl>,
    #   DistributionChannel <chr>, UserLanguage <chr>, Q4 <dbl>, Q5 <dbl>,
    #   Q6 <dbl>, Q7 <dbl>, Q8 <dbl>, Q9 <dbl>, Q10 <dbl>, Q11 <dbl>, Q12 <chr>,
    #   Location <chr>, value <dbl>

## Question 3b

``` r
Colloquium |>
  summarise(Mean_Q7 = mean(Q7, na.rm = TRUE), Mean_Q8 = mean(Q8, na.rm = TRUE), Mean_Q9 = mean(Q9, na.rm = TRUE), Mean_Q10 = mean(Q10, na.rm = TRUE))
```

    # A tibble: 1 × 4
      Mean_Q7 Mean_Q8 Mean_Q9 Mean_Q10
        <dbl>   <dbl>   <dbl>    <dbl>
    1     4.5    4.62    4.31     4.44
