Hurrican Harvey Analysis
================
Sonya Hua
September 7, 2017

This is an automatically generated notebook for the `Hurricane Harvey Shelters in Texas and Louisiana` dataset found at: <https://data.world/jnolasco/harvey-shelters>, showcasing the use of the `data.world` R package.

Setup
-----

For first time users, before running any chunks in this notebook:

``` r
devtools::install_github("datadotworld/data.world-r", build_vignettes = TRUE, force = TRUE)
```

    ## Downloading GitHub repo datadotworld/data.world-r@master
    ## from URL https://api.github.com/repos/datadotworld/data.world-r/zipball/master

    ## Installing data.world

    ## "C:/PROGRA~1/R/R-34~1.1/bin/x64/R" --no-site-file --no-environ --no-save  \
    ##   --no-restore --quiet CMD build  \
    ##   "C:\Users\sonya\AppData\Local\Temp\RtmpiUDOzv\devtools5c1053f92e0f\datadotworld-data.world-r-2134122"  \
    ##   --no-resave-data --no-manual

    ## 

    ## "C:/PROGRA~1/R/R-34~1.1/bin/x64/R" --no-site-file --no-environ --no-save  \
    ##   --no-restore --quiet CMD INSTALL  \
    ##   "C:/Users/sonya/AppData/Local/Temp/RtmpiUDOzv/data.world_1.1.1.tar.gz"  \
    ##   --library="C:/Users/sonya/Documents/R/win-library/3.4" --install-tests

    ## 

-   Install the `data.world` R package: `install.packages("devtools")` `devtools::install_github("datadotworld/data.world-r", build_vignettes = TRUE, force = TRUE)`
-   Get your API authentication token at <https://data.world/settings/advanced>
-   Configure the `data.world` package: `data.world::set_config(data.world::save_config(auth_token = "YOUR TOKEN"))`

Configuration will be saved at `~/.dw/config` and automatically applied to all future R sessions.

### Try your first query

List all tables in the dataset:

``` r
library(data.world)
# Datasets are referenced by their URL or path
dataset_key <- "https://data.world/jnolasco/harvey-shelters"
# List tables available for SQL queries
tables_qry <- data.world::qry_sql("SELECT * FROM Tables")
tables_df <- data.world::query(tables_qry, dataset = dataset_key)
# See what is in it
tables_df$tableName
```

    ## [1] "attention_look_here" "copy_of_shelters"    "form_responses_1"   
    ## [4] "geocoded"            "needs"               "regional_resources" 
    ## [7] "resourcesshop"       "shelters"            "working"

Try a sample query, if any tables exist:

``` r
if (length(tables_df$tableName) > 0) {
  sample_qry <- data.world::qry_sql(sprintf("SELECT * FROM `%s`", tables_df$tableName[[1]]))
  sample_df <- data.world::query(sample_qry, dataset = dataset_key)
  sample_df
}
```

    ## # A tibble: 10 x 1
    ##                                                   houston_shelter_availability
    ##                                                                          <chr>
    ##  1                                                 This sheet is now read-only
    ##  2 If you're just here to see the data, please continue to use the sheet, but 
    ##  3                FOR UPDATES, PLEASE SUBMIT TO:  https://api.harveyneeds.org/
    ##  4                                       Thank you all for your contributions!
    ##  5                                              HOW TO USE API.HARVEYNEEDS.ORG
    ##  6 "Sign Up (Recommended)\nPlease sign up to help us identify you and expedite
    ##  7 If you have any questions about data validation/transfer, please contact @n
    ##  8                      3. Join us on slack at http://sketchcity.herokuapp.com
    ##  9                      --> Harvey related projects are in the #harvey channel
    ## 10 --> Slack is a real-time chat app where we are discussing various ways we c

Next Steps
----------

-   View our quickstart guide: `vignette("quickstart", package="data.world")`
-   Learn more at <https://github.com/datadotworld/data.world-r>

``` r
#vignette("quickstart", package="data.world")
```
