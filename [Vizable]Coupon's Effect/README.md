# [Vizable]Coupon's Effect <img alt="Tableau" src ="https://img.shields.io/badge/Tableau-E97627.svg?&style=for-the-badge&logo=Tableau&logoColor=white"/>

## [My Tableau Public Profile](https://public.tableau.com/app/profile/.67511519/)

## [Project Link](https://public.tableau.com/app/profile/.67511519/viz/VizableCouponsEffect/1?publish=yes)
![](https://github.com/jhbale11/Tableau_Public/blob/a95aca0e71ed191aa594b6c2316b5df3e378d0a2/%5BVizable%5DJH%23WOW2022w03/%5BVizable%5DJH%23WOW2022w03.png)

## How it's built

### Data

**(1) How To Get Data?**

Data Info
```
{
    "path": "https://data.world/markbradbourne/rwfd-real-world-fake-data/workspace/file?filename=Retail+Transactions.csv",
    "name": "Retail Transaction",
    "data form" : "Retail Transaction.csv"
    "metaDescription": "Retail Transaction Data with Coupon Usage, Rewards Flag in Alabama, Florida, Georgia, Mississippi, South Carolina",
    "format": "csv"
}
```
**(2) Features**
- **Transaction Date** : 거래일 (년.월.일)
- **Transaction Hour** : 거래시각 (HH:MM PM/AM)
- **Location State** : 거래 장소 (state 기준)
- **Location City** : 거래 장소 (city 기준)
- **Rewards Number** : 멤버십 번호
- **Rewards Member** : 멤버십 가입 여부
- **Num of Items** : 거래한 상품의 개수
- **Coupon Flag** : 발급한 쿠폰 사용여부 (Yes/Null의 이진값)
- **Discount Amt** : 쿠폰을 사용했을 때 받은 할인율
- **Order Amt** : 총 결제액

### Concept & Problem

유통 산업에서 `쿠폰`은 하나의 중요한 영역입니다. 이에 따라 C기업의 리더들은 발행한 쿠폰에 의한 전반적인 성과를 확인하고 싶어합니다.

1. 쿠폰의 영향을 중심으로 비즈니스 대시보드 만들기
2. 예시) % of Transactions done using Coupons, Regional differences in the usage of Coupons, Sales Trend on a Weekly/Monthly basis, Relation of Reward/Non-Reward Members to the usage of Coupons, etc.
3. 해당 데이터를 토대로 비즈니스 인사이트를 도출하여 작성 (가능하다면 데이터를 통한 비즈니스적 아이디어를 제안하기)
4. 예시) 오후 5시~7시 사이의 transaction에서의 discount amt%가 시간 평균 discount amt% 보다 N% 더 높게 보여진다. 더 많은 customer을 유치하기 위해 customer transaction이 적은 시간대에 높은 할인 쿠폰을 준다.

### Methodology
**(1) 매개 변수 : Selected Date**
```bash
Selected Date를 매개변수로 만들어서 해당 시점에서 현재까지의 수익률 계산에 사용하였습니다. Selected Date를 여러 시트에 동작으로 연동하여 Selected Date의 변화에 따라 생성한 여러 계산된 필드가 변화할 수 있도록 설정하였습니다.
```
**(2) 계산된 필드 : Sales on Selected Date, Volume on Selected Date**
```SQL
IF  MONTH([Date]) = MONTH([Selected Date]) THEN [Sales] END
IF  MONTH([Date]) = MONTH([Selected Date]) THEN [Volume] END
```

**(3) Look Up 함수 : Value on Selected Date**
Selected Date로부터 이후의 날짜에 대한 Date Range에 따른 종가의 평균값을 반환하도록 하였습니다.
```SQL
LOOKUP(AVG([Close]), AVG(DATEDIFF('month',DATETRUNC('month', [Date]), DATETRUNC('month',[Selected Date]))))
```
**(4) 동작**
```bash
매개 변수를 기준으로 한 동작 생성을 통해 시트와 시트 간 대화형 관계를 만들 수 있었습니다. Selected Date의 변화에 따라 모든 시트가 Dynamic하게 달라지도록 구현하였습니다.
```

### Insight
- 특정 시점과 현재 시점과의 차이를 시각화할 수 있는 방법론을 구현하였습니다.
- 주식 뿐만 아니라 펀드나 ETF 등 금융 시계열 데이터를 시각화하는데 활용하면 강력할 것 같습니다.




