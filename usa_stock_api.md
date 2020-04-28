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
```

## investing.com

> 배당락일과 지급일만 수집할 목적이면 이쪽 캘린더가 쉬워 보인다. 기간을 주면 배당 정보만 뽑을 수 있다.
