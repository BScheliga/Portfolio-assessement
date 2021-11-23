# Portfolio assessement

## Abstract

This is script allow you to assess the performance, dividend yield and the sector and market distribution of your stock portfolio. 

London stock exchange is hard coded in the scripted at the moment
Check yahoo finance for the appropiate surfix for the stocks 

I try do make the script as generic as possible to increase the accessiblity for other users.


## Where to the time series data comes from?

Using quantmod

The historical stock records based in the EPIC from [https://www.alphavantage.co/](https://www.alphavantage.co/). The usage of Alpha Vantage requires an API-key, which can be requested here [https://www.alphavantage.co/support/#api-key](https://www.alphavantage.co/support/#api-key) 

## How to use it?
### API-key
### Input files
The script need two inputs file in .csv-format. 1) a file that details the **trading action history** of the portfolio, that you would like to assess. 2) A file that details the **dividend pay out history**. 

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






## Notes
### Known issues
### Planned changes

