# [Vizable]World Population <img alt="Tableau" src ="https://img.shields.io/badge/Tableau-E97627.svg?&style=for-the-badge&logo=Tableau&logoColor=white"/>

## [My Tableau Public Profile](https://public.tableau.com/app/profile/.67511519/)

## [Project Link](https://public.tableau.com/app/profile/.67511519/viz/VizableJHWOW2022w03/2_1)
![](https://github.com/jhbale11/Tableau_Public/blob/a95aca0e71ed191aa594b6c2316b5df3e378d0a2/%5BVizable%5DJH%23WOW2022w03/%5BVizable%5DJH%23WOW2022w03.png)

## How it's built

### Data

**(1) How To Get Data?**

Data Info
```
{
    "path": "https://data.world/missdataviz/wow22w3-stocks-jan22",
    "name": "US_Stocks",
    "data form" : "Stocks.csv"
    "metaDescription": "Data of NASDAQ Major IT Stocks : Google, Tesla, Facebook, Netflix",
    "controller": "csv"
}
```
**(2) Features**
- **Sales -** 매도가
- **Close -** 종가
- **High -** 일 최고가
- **Low -** 일 최저가
- **Open -** 시가
- **Volume -** 거래량

### Concept & Problem

Looking at how a metric has changed from the value at a specified reference date

**Requirements
1. Create a line chart showing percent change of the close price from a selected date.
2. Use a slicer or other visual to allow users to change the reference date.
3. Use conditional formatting to display the selected reference date in the title of the line chart.
4. Instead of a legend, display the series label at the end of each line.
5. Add a vertical reference line to the line chart that marks the selected reference date.

**+ 추가적으로 구현한 부분**
6. Selected date에 따라 변화하는 Company 별 Stock Volume
7. Selected date에 따라 변화하는 Company 별 Stock Sales

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



