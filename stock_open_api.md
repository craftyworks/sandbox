## Open API

### Naver Api | 종목 요약

* https://api.finance.naver.com/service/itemSummary.nhn?itemcode=097520

```json
{"marketSum":552874,"per":6.47,"eps":4787.0,"pbr":2.43,"now":30950,"diff":850,"rate":2.82,"quant":1097396,"amount":34173057,"high":31850,"low":30700,"risefall":2}
```
  * marketSum: 시가총액(단위 : 백만원)
  * now: 시가
  * diff: 전일대비
  * rate: 등락율
  * quant: 거래량
  * amount: 거래금액()

### Naver API | KOSPI 200 편입종목

> 10개 종목씩 20페이지만 파싱하면 200 개 종목 조회 가능. `종목명, 현재가, 전일비, 등락률, 거래량, 거래대금(백만), 시가총액(억)` 제공. HTML 파싱 필요

* https://finance.naver.com/sise/entryJongmok.nhn?&page=1

### Naver API | 일별시세

> 종목코드, 페이지번호로 `날짜, 종가, 전일비, 시가, 고가, 저가, 거래량` 제공. HTML 파싱 필요

* https://finance.naver.com/item/sise_day.nhn?code=097520&page=1

### Naver API | 시간별 시세

> 종목코드, 시각, 페이지번호로 `체결시각, 체결가, 전일비, 매도, 매수, 거래량, 변동량` 제공. HTML 파싱 필요

### Kakao Stock | 종목정보

> REST, JSON

* https://stockplus.com/api/securities/KOREA-A097520.json
```json
{
    "recentSecurity": {
        "accTradeVolume": 1097396,
        "board": "QUOTATION_REGULAR_HOURS",
        "change": "RISE",
        "changePrice": 850.0,
        "changePriceRate": 0.0282392026578073,
        "code": "KR7097520001",
        "currency": "KRW",
        "date": "2020-04-17",
        "dayChartUrl": "https://fn-chart.dunamu.com/images/kr/stock/d/A097520.png",
        "delayedMinutes": 0,
        "displayedPrice": 30950.0,
        "eps": 2161,
        "exchangeCountry": "KOREA",
        "exchangeCountryName": "",
        "foreignRatio": "0.1776",
        "globalAccTradePrice": 34173057500,
        "high52wPrice": 44150.0,
        "highPrice": 31850.0,
        "id": "KOREA-A097520",
        "isIndex": false,
        "isVi": false,
        "low52wPrice": 17800.0,
        "lowPrice": 30700.0,
        "market": "KOSDAQ",
        "marketCapRank": 73,
        "marketName": "코스닥",
        "marketWarningMsg": "",
        "miniDayChartUrl": "https://fn-chart.dunamu.com/images/kr/stock/d/mini/A097520.png",
        "miniDayGuidedChartUrl": null,
        "name": "엠씨넥스",
        "openingPrice": 30950.0,
        "per": 13.93,
        "prevClosingPrice": 30100.0,
        "regularHoursStatus": "CLOSING",
        "sectorName": null,
        "securityGroup": "STOCK",
        "isSecurity": true,
        "shortCode": "A097520",
        "signedChangePrice": 850.0,
        "signedChangeRate": 0.0282392027,
        "totalMarketValue": 552874767900.0,
        "tradePrice": 30950.0,
        "tradeStrength": 80.9027519083194,
        "tradeTime": "180013"
    }
}
```
### Kakao Stock | 일별 시세변동

> REST, JSON

* https://stockplus.com/api/securities/KOREA-A097520/day_candles.json?limit=200

```json
{
    "dayCandles": [{
        "id": 607561535,
        "date": "2020-04-17T00:00:00.000+00:00",
        "tradePrice": 30950.0,
        "changePrice": 850.0,
        "changePriceRate": 0.0282392026578073,
        "change": "RISE"
    },
    ...
```

### Kakao Stock | 증시동향

> 시가총액 상위종목 조회

* https://stockplus.com/api/trends/ordered_stocks.json?key=top_market_value&market=kospi&limit=20&cursor=0



### KRX XML 조회 서비스

> 공짜인거 같고, 별도 가입이나 인증도 없다. XML 로 결과 조회  가능

* [KRX XML 조회 서비스](https://kasp.krx.co.kr/contents/02/02010000/ASP02010000.jsp)
* [실시간시세](view-source:http://asp1.krx.co.kr/servlet/krx.asp.XMLSise?code=035420)
* [재무종합](view-source:http://asp1.krx.co.kr/servlet/krx.asp.XMLJemu?code=035420)

### 한국예탁결제원_주식정보서비스

> 무료, REST

* http://api.seibro.or.kr/openapi/service/StockSvc?_wadl&type=xml

## 산업분류현황

* [GICS 산업분류](http://marketdata.krx.co.kr/mdi#document=03030204)
* [KRX 지수산업분류](http://marketdata.krx.co.kr/mdi#document=03030103)

## KOSPI 200

* [KRX KOSPI 200 종목](http://marketdata.krx.co.kr/mdi#document=030402&a110dc6b3a1678330158473e0d0ffbf0=3)

### 금융위원회_주식배당정보

> 기준일자, 법인등록번호, 주식발행회사명을 통하여 배당기준일자, 현금배당지급일자, 주식교부일자, 주식일반배당금액, 주식차등배당금액 등을 조회하는 배당정보조회 기능

* https://www.data.go.kr/dataset/15043284/openapi.do

### 금융위원회_기업 재무정보

> 법인등록번호, 사업연도를 조회하여 요약재무제표, 재무상태표, 손익계산서를 제공하는 재무정보조회서비스

* https://www.data.go.kr/dataset/15043459/openapi.do

