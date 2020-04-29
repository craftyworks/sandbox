## https://developer.tradier.com/

> 15분 지연이긴 하지만 제대로 된 API 를 제공해 준다. 종목별 주가, 히스토리, 스파크라인용 Tick 데이터 모두 구할 수 있다. 

> 가입도 간편하고, 인증키도 심플, 문서화도 깔끔하게 잘 되어 있다. 

* 계정 : woodjigi@gmail.com

나름 유명한 것인지 NPM 에도 올라온 모듈이 있다.

* https://www.npmjs.com/package/tradier-api

## dividend.com

* https://www.dividend.com/api/dividend/stocks/intc-intel-corp/

> 300KB 가까운 json 데이터를 리턴해 준다. symbol 조회가 아니라 `slug` 로 조회해야 한다.

배당 관련 정보 외에도 종목의 sector 와 industry 조회도 되고, 심지어 추천정보도 보인다.

```json
{
symbol	"INTC"
slug	"intc-intel-corp"
exchange	"NASDAQ"
stock_name	"Intel Corp "
closest_payment_qualification	"Qualified"
industry	"semiconductor-broad-line"
sector	"technology"
closest_payment_frequency_text	"Quarterly"
dars_overall_notes	"Avoid"
dars_rating_advice	"Based on our rating crit…mely risky investments."
last_price	58.97
previous_close_price	59.47
open_price	59.99
low_price	58.9
high_price	60.22
low_price_52_week	42.86
high_price_52_week	69.29
price_change_today	-0.5
price_change_precent	-0.8407600470825626
price_change_precent_of_52_week_high	-14.893924087169875
latest_yield	0.022196065242979655
annualized_payout	1.32
estimate_eps	4.789977
payout_ratio	0.2755754359572081
market_cap	253663812500
closest_payment_adjusted_amount	0.33
best_dividend_stock_recommanded_price	null
price_6_month_ago	56.46
trend_6_month	1
average_days_to_recovery	7.7
yield_on_cost	0.005549016310744914
payment_amount_change	0
previous_payment_ajdusted_amount	0.33
next_year_estimate_eps	4.856133
pe_ratio	12.37166692032133
eps_growth	0.013811339803928077
ytd_return	-0.006349206349206349
latest_special_payment_amount	null
price_beginning_of_year	59.85
consective_year_of_growth	5
closest_payment_frequency	4
dow_30	1
best_dividend_stock	null:

volume	5848571
average_volume_20_day	29190432
best_dividend_capture	0
active	1
price_as_of	"2020-04-28T15:47:12.000+00:00"
closest_payment_ex_date	"2020-05-06T00:00:00.000+00:00"
closest_payment_payable_date	"2020-06-01T00:00:00.000+00:00"
closest_payment_declared_date	"2020-03-12T00:00:00.000+00:00"
closest_payment_record_date	"2020-05-07T00:00:00.000+00:00"
best_dividend_stock_recommanded_date	null
latest_special_payment_payable_date	null
latest_special_payment_ex_date	null
}
```

## investing.com

> 배당락일과 지급일만 수집할 목적이면 이쪽 캘린더가 쉬워 보인다. 기간을 주면 배당 정보만 뽑을 수 있다.

## etf.com

> 2000 여개 펀드 정보를 한방에 내려주는 json API 가 있다.

> https://api.etf.com/private/finder/funddata

컬럼명이 암호스럽긴 한데 찾아낸 매핑은 다음과 같다.

```json
 "ticker": "SPY",	
        "fund": "SPDR S&P 500 ETF Trust",	Name
        "eab5bcd750dc": "1993-01-22T00:00:00.000Z",	Inception Date
        "e45447c2f507": "Developed Markets",	
        "e7cbb2ab023d": "State Street Global Advisors",	Issuer
        "eecb5332c91d": "Equity: U.S.  -  Large Cap",	Segment
        "assetClass": "Equity",	
        "region": "North America",	
        "geography": "U.S.",	
        "category": "Size and Style",	
        "focus": "Large Cap",	
        "niche": "Broad-based",	
        "ec5a9a10d548": "Committee",	
        "e1c27c88f074": "Market Cap",	
        "e8f1eb14319c": "S&P 500",	
        "e0b96b7a587d": "Unit Investment Trust",	Legal Structure
        "eb24949c8d6e": 9.45,	Expense Ratio (x/100)%
        "aum": 253753950000,	AUM
        "ee92be7592ed": 0.163767,	1Month
        "ed25a78c6810": -0.13402,	3Month
        "ebe84f6571f5": -0.115428,	YTD
        "e4ce45f2c38d": -0.011639,	1Year
        "eb355c900989": 0.081456,	3Year
        "e440ef02dc06": 0.081316,	5Year
        "e0bc5b56c458": 0.110208,	10Year
        "ea490851d279": "A",	Grade
        "ed0802c77a4d": 97.968833,	Efficiency
        "e765c4d93059": 99.468031,	Tradability
        "e8f684837ff7": 96.146466,	Fit
        "e0bd71b63cc4": 51670318795.004974,	Average Daily $ Volume
        "e5c6b14c612c": 22.339035,	P/E
        "e0936b1e4da7": 3.3963,	P/B
        "e6b76ba7e6a7": 0.018953,	Dividend Yield (x * 100)%
        "ec7180c2f248": 5.893,	Quality Score
        "e59b76f78491": 60.7479,	Score Global Rank
        "ea0fcdb4db01": 67.4393,	Score Peer Rank
        "eff8cac7958a": 178.82,	Carbon Intensity
        "e882560b66d6": "A",	ESG Rating
        "edca02710910": -9675.097399999999,	1Month
        "e44d115870cc": -15577.422663,	3Month
        "ea9752743207": -16337.669737,	YTD
        "e2fdee6d3a4a": -14921.589819,	1Year
        "eb3786e7dcc2": -19038.285594,	3Year
        "e87f910b99f1": "2020-04-24T00:00:00.000Z",	As of Date
```

개별 종목 조회는 다음 URL 로 리턴되는 HTML 을 분석해서 얻을 수 있다.

* https://etfdb.com/etf/SPY/

## S&P 500

위키피디아가 가장 최신 정보로 보인다. 섹터와 산업 분류를 볼 수 있어 조으다.

* https://en.wikipedia.org/wiki/List_of_S%26P_500_companies

섹터까지만 구하면 된다고 보면, 아래 URL 로 리턴되는 csv 파일을 이용하는 것이 더 편하겠다.

* https://datahub.io/core/s-and-p-500-companies/r/constituents.csv

다우존스도 역시 위키피디아가 속편하다.

* https://en.wikipedia.org/wiki/Dow_Jones_Industrial_Average

* https://www.cnbc.com/dow-30/

