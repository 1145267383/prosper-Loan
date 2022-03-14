# (Loan Data from Prosper)
## by (Mohamed Abd Al-mgyd)


## Dataset

> Dataset "https://www.google.com/url?q=https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv&sa=D&ust=1554484977406000".
>>This data set contains 113,937 loans with 81 variables on each 
loan, including loan amount, borrower rate (or interest rate), 
current loan status, borrower income, and many others.


>Variable                       Description
Listing Key                     Unique key for each listing, same value as the 'key' used in the listing object in the API.
Term                            The length of the loan expressed in months.
Loan Original Amount            The origination amount of the loan.
BorrowerAPR                     The Borrower's Annual Percentage Rate (APR) for the loan.
StatedMonthlyIncome             The monthly income the borrower stated at the time the listing was created.
Employment Status               The employment status of the borrower at the time they posted the listing.
Employment Status Duration      The length in months of the employment status at the time the listing was created.
Current Delinquencies           Number of accounts delinquent at the time the credit profile was pulled.
Recommendations                 Number of recommendations the borrower had at the time the listing was created.
Loan Status                     The current status of the loan: Cancelled,  Chargedoff, Completed, Current, Defaulted, FinalPaymentInProgress, PastDue. The PastDue status will be accompanied by a delinquency bucket.



## Summary of Findings

> A- Knowing the variables that affect acceptance or rejection of the loan request?
     Acceptance whth  {term=(36 manth) ,BorrowerAPR ,EmploymentStatus=(Employed)} ,
     Rejection whath {CurrentDelinquencies ,DelinquenciesLast7Years}

> B- Knowing the variables that affect the interest rate (borrower APR)?
     Approve weth {CurrentDelinquencies ,DelinquenciesLast7Years ,EmploymentStatus=(Not employed ,Retired)}
     Reverse weth {LoanOriginalAmount ,StatedMonthlyIncome}

>  C-ِ Are there  differences between loan sizes? yes
      Approve weth {StatedMonthlyIncome ,EmploymentStatusDuration}
     Reverse weth {BorrowerAPR ,CurrentDelinquencies ,DelinquenciesLast7Years}

## Key Insights for Presentation

### Univariate Exploration 
>for  Term ,LoanOriginalAmount ,BorrowerAPR ,StatedMonthlyIncome .EmploymentStatus ,EmploymentStatusDuration ,CurrentDelinquencies ,DelinquenciesLast7Years ,Recommendations ,LoanStatus.

>Convert Term into ordered categorical types
["12" then "36" then "60"]

> The APR distribution appears symmetric around the 0.2 point about. There is a maximum between 0.35 and 0.36, and there are outliers that have an APR above 0.41 and less than 0.005.

> (StatedMonthlyIncome) distribution appears right-skewed ,and there are outliers above 25 thousand.

>Convert EmploymentStatus into ordered categorical types.
['Employed','Self-employed','Full-time','Part-time','Retired','Other','Not employed', 'Not available']

> (EmploymentStatusDuration) distribution appears right-skewed ,and there are outliers above 500..

>Group all Past Due loans under an unique status ['Past Due (1-15 days)','Past Due (16-30 days)','Past Due (61-90 days)','Past Due (31-60 days)', 'Past Due (91-120 days)','Past Due (>120 days)'] to 1('Past Due')

> Convert LoanStatus to a categorical variable['Cancelled','Defaulted','Chargedoff', 'Past Due', 'Current', 'FinalPaymentInProgress', 'Completed']

### Bivariate Exploration

>BorrowerAPR VS [ 2) LoanOriginalAmount ,4) StatedMonthlyIncome ,6)EmploymentStatusDuration' ,7)CurrentDelinquencies' ,8)DelinquenciesLast7Years' ,9)Recommendations' ]

>3)LoanStatus VS
> [4) StatedMonthlyIncome ,6)EmploymentStatusDuration' ,7)CurrentDelinquencies',8)DelinquenciesLast7Years' ]

> LoanStatus VS [1)Term ,6)EmploymentStatus]

### Multivariate Exploration
>BorrowerAPR VS LoanOriginalAmount VS [1)Term ,6)EmploymentStatus,11)LoanStatus]