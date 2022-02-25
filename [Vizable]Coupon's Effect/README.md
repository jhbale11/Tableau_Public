# [Vizable]Coupon's Effect <img alt="Tableau" src ="https://img.shields.io/badge/Tableau-E97627.svg?&style=for-the-badge&logo=Tableau&logoColor=white"/>

## [My Tableau Public Profile](https://public.tableau.com/app/profile/.67511519/)

## [Project Link](https://public.tableau.com/app/profile/.67511519/viz/VizableCouponsEffect/1?publish=yes)
![](https://github.com/jhbale11/Tableau_Public/blob/639de3dae2c7e2449e677e3d84a13ea407c93cb4/%5BVizable%5DCoupon's%20Effect/%5BVizable%5DCoupon's%20Effect.png)

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
**(1) 매개 변수 : Coupon**

> Coupon 매개변수로 만들어서 선택한 Coupon Discount Rate에 따라 여러 자료를 볼 수 있도록 하였습니다. Coupon을 여러 시트에 동작으로 연동하여 Coupon 선택의 변화에 따라 생성한 여러 계산된 필드가 변화할 수 있도록 설정하였습니다.

**(2) 계산된 필드1,2 : Coupon Order, Coupon Items, Coupon Usage**
```SQL
AVG(IF [Coupon] = [Coupon Discount] THEN [Order Amt Float] END)
AVG(IF [Coupon] = [Coupon Discount] THEN [Num Of Items] END)
```

**(3) 계산된 필드3,4 : Coupon Usage, Coupon Reward**
```SQL
COUNT(IF [Coupon] = [Coupon Discount] THEN [Coupon Discount] END)
COUNT(IF [Coupon] = [Coupon Discount] THEN [rewards_member] END)
```


**(3) Weekly Count**
주를 열로, 요일을 행으로 설정하여 Git Commit Trend Graph와 같은 형태의 차트를 생성하였습니다.
![]()

**(4) 동작**
>> 매개 변수를 기준으로 한 동작 생성을 통해 시트와 시트 간 대화형 관계를 만들 수 있었습니다. Coupon의 변화에 따라 모든 시트가 Dynamic하게 달라지도록 구현하였습니다.

### Insight
- Coupon에 따라 달라지는 매출, 쿠폰 사용량, 판매 아이템 수를 시각화하고, 몇 퍼센트의 쿠폰에 민감하게 반응하는지 알아보고자 하였습니다. 데이터의 문제일 수 있으나 전반적으로 13%, 23%, 35%, 45% 등 각 십의 자리에서 중간 정도의 쿠폰의 사용량이 높았고, 매출, 판매 아이템 수도 높았음을 확인할 수 있었습니다.




