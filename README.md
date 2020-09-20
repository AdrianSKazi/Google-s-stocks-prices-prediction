# Google-s-stocks-prices-prediction

### Table of contents:
1. Importing libraries
2. Importing dataset
3. Handling categorical data
4. Handling missing values
5. Traing test split
6. Multivariate Linear Regression modeling
  - Training
  - Testing
7. Improving dataset
  - Effective Federal Funds Rate
  - Data adjustment due to Corona Virus crisis
8. Renewed Multivariate Regression modeling
  - Cleaning
  - Splitting the dataset
  - Training
  - Testing
9. Price predictions table for year 2020 and 2021
  - Creating 2020 and 2021 whole years Data Frame
  - Adding EFFR column
    - Preparing whole_year dataset for modeling
    - Preparing EFFR dataset for data modeling
      - Creating 'fake rate' DataFrame
      - Reindexing and cleaning
    - Extracting proper data rows
  - Predictions dataset
  - Final multivariate linear regression modeling
    - Fitting to lm_renewed model
  - Whole dataset
10. Data visualization
  - To datetime
  - Final plot
<hr>


### Datasets:
* GOOGL.csv
* EffectiveFederalFundsRate.csv

### Model
* Model: Multivariate Linear Regression
* Independent variables: Year, Day, Month, Effective Federal Funds Rate (EFFR)
* Dependent variable: Closing price (for each day)

## COVID-19 outbreak
Stocks' prices prediction for year 2020 and 2021 for Google. Including distortion of demand due to COVID-19.

Our data reaches date of 2020-04-01. Our model wouldn't be good representation for predictions because of Corona Crisis. Check out below information.

On day 14th February prices started to decline, two weeks after WHO declared the outbreak of COVID-19 to be a Public Health Emergency of International Concern and issued a set of Temporary Recommendations.

After seven weeks of first confusion and fear on the market prices started increases on April 3rd. Unfortunately our dataset includes this specific period of time, what surely will distort our predictions. Thats why I cut the tail of our dataset until the date on which COVID-19 had too big impact on our dataset. But to be prevent underfitting of our model I left some market slump period.

## Adding Effective Federal Funds Rate

As far as US government will keep their announcement about holding interest rate near 0% through year 2022 - because of COVID crisis - I've decided to set interest rate for Q4 2020 (from 19.02.2020) and 2021 from 0,08% gradually decreasing by 0,1% each day.

###### Sources:
###### https://finance.yahoo.com/quote/GOOGL/chart?p=GOOGL#eyJpbnRlcnZhbCI6ImRheSIsInBlcmlvZGljaXR5IjoxLCJ0aW1lVW5pdCI6bnVsbCwiY2FuZGxlV2lkdGgiOjMuNTIxODc1LCJmbGlwcGVkIjpmYWxzZSwidm9sdW1lVW5kZXJsYXkiOnRydWUsImFkaiI6dHJ1ZSwiY3Jvc3NoYWlyIjp0cnVlLCJjaGFydFR5cGUiOiJsaW5lIiwiZXh0ZW5kZWQiOmZhbHNlLCJtYXJrZXRTZXNzaW9ucyI6e30sImFnZ3JlZ2F0aW9uVHlwZSI6Im9obGMiLCJjaGFydFNjYWxlIjoibGluZWFyIiwic3R1ZGllcyI6eyLigIx2b2wgdW5kcuKAjCI6eyJ0eXBlIjoidm9sIHVuZHIiLCJpbnB1dHMiOnsiaWQiOiLigIx2b2wgdW5kcuKAjCIsImRpc3BsYXkiOiLigIx2b2wgdW5kcuKAjCJ9LCJvdXRwdXRzIjp7IlVwIFZvbHVtZSI6IiMwMGIwNjEiLCJEb3duIFZvbHVtZSI6IiNmZjMzM2EifSwicGFuZWwiOiJjaGFydCIsInBhcmFtZXRlcnMiOnsid2lkdGhGYWN0b3IiOjAuNDUsImNoYXJ0TmFtZSI6ImNoYXJ0In19fSwicGFuZWxzIjp7ImNoYXJ0Ijp7InBlcmNlbnQiOjEsImRpc3BsYXkiOiJHT09HTCIsImNoYXJ0TmFtZSI6ImNoYXJ0IiwiaW5kZXgiOjAsInlBeGlzIjp7Im5hbWUiOiJjaGFydCIsInBvc2l0aW9uIjpudWxsfSwieWF4aXNMSFMiOltdLCJ5YXhpc1JIUyI6WyJjaGFydCIsIuKAjHZvbCB1bmRy4oCMIl19fSwic2V0U3BhbiI6bnVsbCwibGluZVdpZHRoIjoyLCJzdHJpcGVkQmFja2dyb3VuZCI6dHJ1ZSwiZXZlbnRzIjp0cnVlLCJjb2xvciI6IiMwMDgxZjIiLCJzdHJpcGVkQmFja2dyb3VkIjp0cnVlLCJldmVudE1hcCI6eyJjb3Jwb3JhdGUiOnsiZGl2cyI6dHJ1ZSwic3BsaXRzIjp0cnVlfSwic2lnRGV2Ijp7fX0sInJhbmdlIjpudWxsLCJzeW1ib2xzIjpbeyJzeW1ib2wiOiJHT09HTCIsInN5bWJvbE9iamVjdCI6eyJzeW1ib2wiOiJHT09HTCIsInF1b3RlVHlwZSI6IkVRVUlUWSIsImV4Y2hhbmdlVGltZVpvbmUiOiJBbWVyaWNhL05ld19Zb3JrIn0sInBlcmlvZGljaXR5IjoxLCJpbnRlcnZhbCI6ImRheSIsInRpbWVVbml0IjpudWxsLCJzZXRTcGFuIjpudWxsfV19
###### https://fred.stlouisfed.org/series/FEDFUNDS
###### https://www.cnbc.com/2020/06/10/fed-holds-rates-near-zero-heres-what-that-means-for-your-wallet.html
