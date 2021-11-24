# Portfolio assessement


## Abstract

This is RMarkdown script allow you to assess the performance, dividend yield as well as the sector and market distribution of your stock portfolio. I created this script as a pet project because my broker does not offer this kind of visualisation for my portfolio and I am tired using excels for it.

I try do make the script as generic as possible to increase the accessibility for other users.

## Notes
- currently the script is hard coded to retrieve historical stock records for stocks traded at the London stock exchange using the suffix "*.L*" after the *EPIC* in the *getSymbol()*-function. Without the suffix, *getSymbol()* would retrieve historical stock records for companies listed under used EPICs at the American stock exchange (Note:*not sure exchange. I don't really care, as it is not relevant for me at the moment*)

### Known issues
- some historical stock records are in GB pence and other in GBP. Generally, they should be in GB pence. However, if the plot looks funny and don't add up. It is worth investigating the historical stock records.

### Planned changes
- make changing the stock exchange suffix for retrieving historical stock records (**getSymbol()**) more accessible
- use here-package

## Where to the time series data comes from?

The core R library in this script is [quantmod](https://cran.r-project.org/web/packages/quantmod/quantmod.pdf), it allows you to pull the historical stock records from various sources. Quantmod requires the EPIC of a stock and a suffix (e.g. ".L" for London stock change) to pull the data. I chose [https://www.alphavantage.co/](https://www.alphavantage.co/) as a data supplier. Some data for [yahoo finance](https://uk.finance.yahoo.com/) would need more hands-on interrogation and cleaning. The usage of Alpha Vantage requires an API-key, which can be requested here [https://www.alphavantage.co/support/#api-key](https://www.alphavantage.co/support/#api-key) 

## How to use it?

1. Install R 
2. Instal RStudio 
3. Install all required R packages (libraries) in RStudio
4. Request your own API-Key [https://www.alphavantage.co/support/#api-key](https://www.alphavantage.co/support/#api-key) and replace it with the one in the script.  


### Warning & Disclaimer
1. Make sure you are not **accidentally and unintentionally** uploading your trading action history to GitHub when cloning and using this script.  
2. It **does not** give you financial advise  
### API-key
API-KEY limits: 5 API requests per minute and 500 requests per day

### Change stock exchange from London to some other place?

You could try to use [https://uk.finance.yahoo.com/](https://uk.finance.yahoo.com/) to identify the correct suffix after the EPIC and change the code in the script accordingly.

### Input files
The script needs two inputs file in .csv-format. 1) a file that details the **trading action history** of the portfolio, that you would like to assess. 2) A file that details the **dividend pay out history**. Both files [ETF_Share.csv](https://github.com/BScheliga/Portfolio-assessement/blob/main/ETF_Share.csv) and [dividend.csv](https://github.com/BScheliga/Portfolio-assessement/blob/main/dividend.csv) are in the repository with the example data below.

#### 1) ETF and Share trading action history
Filename: ETF_Share.csv  
Example layout: 

|EPIC|Name|Buy_Sell|Aver_cost|Volume|Date|Type|Trad_cost|Sector|Market|
|----|----|--------|---------|------|----|----|---------|------|------|
|VUSA|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS|	BUY	|4,990.26|	20	|11/09/2020|	ETF|	5|	Mixed	|Developed Markets|
|HSBA|	HSBC HOLDINGS PLC ORD USD0.50UK REG|	BUY|	335.4|	60|	05/11/2020|	Share|	5|	Banking|	Developed Markets|
|HMEF|HSBC ETFS PLC MSCI EMERGING MKT UCITS ETF|	BUY|	924.73|	90|	01/12/2020|	ETF	|5|	Mixed|	Emerging Market|
|VOD|	VODAFONE GROUP ORD USD0.2095238|	BUY|	132.7|	100|	21/04/2021|	Share|	5|	Tech|	Developed Markets|
|HSBA|	HSBC HOLDINGS PLC ORD USD0.50UK REG|	BUY|	378.6|	60|	05/01/2021|	Share|	5|	Banking|	Developed Markets|  

Variable definition:

|Variable name| Definition | Format|
|-------------|------------|-------|
|EPIC|Exchange Price Information Code of the stock |*character*|
|Name| Long name of the (company) stock|*character*|
|Buy_Sell| Use **BUY** or **SELL** to indicate the trade action|*character*|
|Aver_cost| Average costs per share for the trade action|*numeric*|
|Volume| Amount of shares that were traded in the trade action|*numeric*|
|Date| Date of the trade action|DD/MM/YYYY|
|Type| Use **ETF** or **Share**|*character*|
|Trad_Cost| Trading costs for executing the trade action|*numeric*|
|Sector| The commercial or industrial sector the company is in. *Note:* For ETFs like MSCI World use **Mixed**|*character*|
|Market| Use **Developed Markekt** or **Emerging Market**|*character*| 
  
  
  
#### 2) dividend pay out history
Filename: dividend.csv  
Example layout: 

|EPIC|Name|Issue_Date|XD_Date|Shares_held_XD_date|Amount_Payable|Type|
|----|----|--------|---------|------|----|----|
|VUSA	|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS	|09-Oct-20|	24-Sep-20	|20	|0.97|	ETF|
|VUSA	|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS	|05-Jan-21|	17-Dec-20	|20	|0.79|	ETF|
|VUSA	|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS	|01-Apr-21|	18-Mar-21	|20	|0.87|	ETF|
|VUSA	|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS	|06-Jul-21|	17-Jun-21	|20	|0.82|	ETF|
|VUSA	|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS	|06-Oct-21|	16-Sep-21	|20|	0.94|	ETF|
|VOD	|VODAFONE GROUP ORD USD0.2095238	|06-Aug-21|	24-Jun-21|	100	|8.9|	Share|
|HSBA	|HSBC HOLDINGS PLC ORD USD0.50UK REG	|29-Apr-21|	11-Mar-21|	120|	9.39	|Share|
|HSBA	|HSBC HOLDINGS PLC ORD USD0.50UK REG	|30-Sep-21|	19-Aug-21|	120|	4.45|	Share|
|HMEF|	HSBC ETFS PLC MSCI EMERGING MKT UCITS ETF	|15-Nov-21|	21-Oct-21|	90|	12.04	|ETF|

Variable definition:

|Variable name| Definition | Format|
|-------------|------------|-------|
|EPIC|Exchange Price Information Code of the stock |*character*|
|Name| Long name of the (company) stock|*character*|
|Issue_Date| Date the dividends were issued |DD/MM/YYYY|
|XD_Date| dividend ex-date|DD/MM/YYYY|
|Shares_held_XD_date| number of share held on the dividend ex-date|*numeric*|
|Type| Use **ETF** or **Share**|*character*|
