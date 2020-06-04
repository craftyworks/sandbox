## https://developer.tradier.com/

> 15분 지연이긴 하지만 제대로 된 API 를 제공해 준다. 종목별 주가, 히스토리, 스파크라인용 Tick 데이터 모두 구할 수 있다. 

> 가입도 간편하고, 인증키도 심플, 문서화도 깔끔하게 잘 되어 있다. 

* 계정 : woodjigi@gmail.com

나름 유명한 것인지 NPM 에도 올라온 모듈이 있다.

* https://www.npmjs.com/package/tradier-api

### API

* quotes : 15분 지연된 현재 주가 정보를 리턴. 다 좋은데 `Market Cap` 이 없다.
* clock : 현재 장이 열렸는지 몇시에 열고 몇시에 닫는지 알 수 있다.
* calendar : 년,월을 파라미터로 던지면 해당 월의 각 일자별 장 열고 닫는 시간을 리턴해 준다.
* history : 일자별 주가, 거래량을 조회. 이력 마이그 용으로 좋을 것 같은데...아쉽게 `시가총액` 변동은 알 수 없다.
* timesales : 1분, 5분, 15분 간격으로 주가 변화 이력을 조회할 수 있다. 시계열 차트를 그릴 수 있겠다.
* search, lookup : 종목코드, 명으로 종목검색.

> REST API 라 편하기도 한데... `시가총액`이 없는 점은 아쉽다. 과거 주가 이력을 마이그 하는데 쓰면 될 것 같고, 당일 차트 그리기도 편할것 같다. 크롤링 전에 현재 장이 열린 상태인지 검사하는 데 쓰기도 좋겠다. 종목 검색 콤보 구성도 용하게 써먹을 수 있을 것 같다.

> 종목에 대한 기본정보와 `Secotr`, `배당금` 정보는 구할 수 없다.


## dividend.com

### JSON
* https://www.dividend.com/api/dividend/stocks/intc-intel-corp/

> 겁나 큰 json 데이터를 리턴해 준다. symbol 조회가 아니라 `slug` 로 조회해야 한다.
배당 관련 정보 외에도 종목의 sector 와 industry 조회도 되고, 심지어 추천정보도 보인다. 

> 종목별 조회인데 데이터가 너무 크다. 종목 코드가 검색 조건이 아닌것도 마음에 안든다.

> 그러나  `Sector` 와 `Industry` 가 포함되어 있고, 무엇보다 배당락일과 배당금(연합계가 아닌 이번에 주는 돈) 정보가 있다. API 가 미친거 같은게, 과거 모든 배당이력을 포함해서 데이터를 내려준다.

```json

{
    "id": "INTC--NASDAQ",
    "symbol": "INTC",
    "slug": "intc-intel-corp",
    "exchange": "NASDAQ",
    "stock_name": "Intel Corp ",
    "market_cap_size": "large",
    "closest_payment_qualification": "Qualified",
    "industry": "semiconductor-broad-line",
    "sector": "technology",
    "security_category": "Common",
    "payment_amount_change_type": "No Change",
    "closest_payment_frequency_text": "Quarterly",
    "dars_overall_notes": "Avoid",
    "dars_rating_advice": "Based on our rating criteria, this stock has achieved an 'Avoid' rating. Stocks with an 'Avoid' rating are considered extremely risky investments.",
    "etf_alt_link": "View",
    "profile": "Intel Corporation (INTC) designs and manufactures integrated digital technology platforms. The company offers microprocessors that process system data and controls other devices in the system. Intel's products are used in personal computers, data centers, tablets, smartphones, automobiles, automated factory systems and medical devices. The company was founded in 1968, and is based in Santa Carla, CA.",
    "last_price": 60.35,
    "previous_close_price": 61.8,
    "open_price": 61.36,
    "low_price": 60.25,
    "high_price": 61.54,
    "low_price_52_week": 42.86,
    "high_price_52_week": 69.29,
    "price_change_today": -1.4499999999999957,
    "price_change_precent": -2.346278317152097,
    "price_change_precent_of_52_week_high": -12.902294703420413,
    "latest_yield": 0.02246808510638298,
    "annualized_payout": 1.32,
    "estimate_eps": 4.789977,
    "payout_ratio": 0.2755754359572081,
    "market_cap": 248747500000.0,
    "closest_payment_adjusted_amount": 0.33,
    "best_dividend_stock_recommanded_price": null,
    "price_6_month_ago": 56.34,
    "trend_6_month": 1.0,
    "average_days_to_recovery": 7.7,
    "yield_on_cost": 0.005339805825242718,
    "payment_amount_change": 0.0,
    "previous_payment_ajdusted_amount": 0.33,
    "next_year_estimate_eps": 4.856133,
    "pe_ratio": 12.265194592792408,
    "eps_growth": 0.013811339803928077,
    "ytd_return": 0.03258145363408521,
    "latest_special_payment_amount": null,
    "price_beginning_of_year": 59.85,
    "consective_year_of_growth": 5,
    "closest_payment_frequency": 4,
    "dow_30": 1,
    "best_dividend_stock": null,
    "volume": 3880939,
    "average_volume_20_day": 28164855,
    "best_dividend_capture": 0,
    "active": 1,
    "price_as_of": "2020-04-30T15:12:19.000+00:00",
    "closest_payment_ex_date": "2020-05-06T00:00:00.000+00:00",
    "closest_payment_payable_date": "2020-06-01T00:00:00.000+00:00",
    "closest_payment_declared_date": "2020-03-12T00:00:00.000+00:00",
    "closest_payment_record_date": "2020-05-07T00:00:00.000+00:00",
    "best_dividend_stock_recommanded_date": null,
    "latest_special_payment_payable_date": null,
    "latest_special_payment_ex_date": null,
    "all_payments": [
        {
            "symbol": "INTC",
            "is_yield_looking": true,
            "filed_at": "2020-03-12T22:00:00.000+00:00",
            "payment_end_date": "2020-06-01T00:00:00.000+00:00",
            "is_active_company": 1,
            "is_estimated": false,
            "payment_types": [
                "Income",
                "Qualified"
            ],
            "type": "Regular",
            "currency_code": "USD",
            "payable_date": "2020-06-01T00:00:00.000+00:00",
            "se": "INTC--NASDAQ",
            "adjusted_amount": 0.33,

```
### HTML
* https://www.dividend.com/dividend-stocks/services/business-services/intc-intel-corp/

HTML 페이지를 파싱해야 하는데... 사이즈가 역시 만만치 않다. 걍 `JSON`을 파싱하는게 낳겠다.

## investing.com

* https://www.investing.com/dividends-calendar/Service/getCalendarFilteredData

> 배당락일과 지급일만 수집할 목적이면 이쪽 캘린더가 쉬워 보인다. 기간을 주면 배당 정보만 뽑을 수 있다.

> 배당락일, 배당금, 지급일, 연배당율을 페이징 처리된 HTML 페이지로 제공한다. 문제는... `ETF` 가 없다는 점.

## etf.com

> 2000 여개 펀드 정보를 한방에 내려주는 json API 가 있다. 약 `5MB` 다. 데이터 마이그 용으로 써야 겠다. 아쉽게 배당 정보는 얻을 수 없다.

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

개별 종목 조회는 다음 URL 로 리턴되는 HTML 을 분석해서 얻을 수 있다. `배당일` 과 `배당금` 정보가 포함되어 있다.

* https://etfdb.com/etf/SPY/

## S&P 500

위키피디아가 가장 최신 정보로 보인다. 섹터와 산업 분류를 볼 수 있어 조으다.

* https://en.wikipedia.org/wiki/List_of_S%26P_500_companies

섹터까지만 구하면 된다고 보면, 아래 URL 로 리턴되는 csv 파일을 이용하는 것이 더 편하겠다.

* https://datahub.io/core/s-and-p-500-companies/r/constituents.csv

다우존스도 역시 위키피디아가 속편하다.

* https://en.wikipedia.org/wiki/Dow_Jones_Industrial_Average

* https://www.cnbc.com/dow-30/

## nasdaq.com

> 의외로 여기가 `개꿀` 이다.

* https://api.nasdaq.com/api/quote/QQQ/summary?assetclass=etf
* https://api.nasdaq.com/api/quote/QQQ/info?assetclass=etf

`주식`과 `ETF` 관한 정보를 REST API 로 제공한다. 배당락일, 연배당금, 연배당율 정보도 제공한다. 단 하나의 문제는 `배당 지급금`(이번 배당에 실제로 주는 금액) 만 빠져있다. 이 정보는 dividend.com 에서 구할 수 밖에 없는 것 같다. investing.com 도 있긴 한데(ETF 가 없다.)

> 역시; 세상에 공짜는 없다. DDOS 공격을 막는 것인지는 모르겠으나, 요청이 짧은 시간동안 반복될 경우에 `Access Denied` 오류를 뱉는다.