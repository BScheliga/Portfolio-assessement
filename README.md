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
The script need two inputs file in .csv-format. 1) a file that details the trading action history of the portfolio, that you would like to assess. 2) A file that details the dividend pay out history. 

#### 1) ETF and Share trading action history
Filename: ETF_Share.csv  
Example layout: 

|EPIC|Name|Buy_Sell|Aver_cost|Volume|Date|Type|Trad_cost|Sector|Market|
|----|----|--------|---------|------|----|----|---------|------|------|
|VUSA|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS|	BUY	|4,990.26|	20	|11/09/2020|	ETF|	5|	Mixed	|Developed Markets|
|HSBA|	HSBC HOLDINGS PLC ORD USD0.50UK REG|	BUY|	335.4|	60|	05/11/2020|	Share|	5|	Banking|	Developed Markets|
|HMEF|HSBC ETFS PLC MSCI EMERGING MKT UCITS ETF|	BUY|	924.73|	90|	01/12/2020|	ETF	|5|	Mixed|	Emerging Market|
|VOD|	VODAFONE GROUP ORD USD0.2095238|	BUY|	132.7|	100|	21/04/2021|	Share|	5|	Tech|	Developed Markets|

#### 2) dividend pay out history
Filename: dividend.csv  
Example layout: 

|EPIC|Name|Buy_Sell|Aver_cost|Volume|Date|Type|Trad_cost|Sector|Market|
|----|----|--------|---------|------|----|----|---------|------|------|
|VUSA|VANGUARD FUNDS PLC SP 500 UCITS ETF USD DIS|	BUY	|4,990.26|	20	|11/09/2020|	ETF|	5|	Mixed	|Developed Markets|
|HSBA|	HSBC HOLDINGS PLC ORD USD0.50UK REG|	BUY|	335.4|	60|	05/11/2020|	Share|	5|	Banking|	Developed Markets|
|HMEF|HSBC ETFS PLC MSCI EMERGING MKT UCITS ETF|	BUY|	924.73|	90|	01/12/2020|	ETF	|5|	Mixed|	Emerging Market|
|VOD|	VODAFONE GROUP ORD USD0.2095238|	BUY|	132.7|	100|	21/04/2021|	Share|	5|	Tech|	Developed Markets|


## Notes
### Known issues
### Planned changes

