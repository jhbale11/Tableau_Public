# [Vizable]World Population <img alt="Tableau" src ="https://img.shields.io/badge/Tableau-E97627.svg?&style=for-the-badge&logo=Tableau&logoColor=white"/>

## [My Tableau Public Profile](https://public.tableau.com/app/profile/.67511519/)

## [Project Link](https://public.tableau.com/views/VizableWorldPopulation_JH/1_1?:language=ko-KR&:display_count=n&:origin=viz_share_link)
![]([Vizable]World_Population.png)

## How it's built

### Data

**(1) How To Get Data?**

Data Info
```
{
    "path": "https://www.worldometers.info/world-population/",
    "name": "world population",
    "data form" : "https://docs.google.com/spreadsheets/d/1uF8fUKZfHQvSCXWi89LTOEX4Pktj4qE1FocQbg5hRw4/edit#gid=0"
    "metaDescription": "Data of world population with Population Density, Fert. Rate, Land Area, etc.",
    "controller": "csv"
}
```
**(2) Features**
- **Country -** 국가
- **Population_20 -** 2020년 기준 인구 수
- **Yearly Change -** 년단위 변화율 (%)
- **Net Change -** 순 년단위 변화량 (수)
- **Density -** 전체 인구 수(per) / 국가 면적($km^2$)
- **Land Area -** 면적
- **Migrants -** 순 이민자 수
- **Fert.Rate -** 합계 출산율 (%)
- **Med.Age -** 나이 중위수
- **Urban Pop -** 도시 집중도 (%)
- **World Share_20 -** 2020년 기준 인구 수 차지 비율(%)
- **GDP** - 국내 총 생산($)

### Concept & Problem

인구수와 출산율을 기준으로 Clustering을 통해 Cluster 별로 국내 총 생산, 나이 중위수, 인구 순증가와 이민자 정책에 대한 인사이트를 얻고자 하였습니다! 

아래와 같은 질문에 답하고자 하였습니다.
**1. 인구가 많은 나라들은 출산에 대하여, 인구 증가에 대하여, 이민자에 대하여 어떤 접근을 하고 있을까?**
**2. 인구수와 출산율을 기준으로 Clustering 하였을 때, Cluster 별로 어떤 특징을 보이게 될까?**

### Methodology
``` bash
(1) Tableau Analysis 기능을 활용하여 인구수와 출산율을 기준으로 Clustering을 진행하였습니다.
(2) Cluster의 지리적 분포를 한눈에 보기 위하여 Cluster Map을 생성하였습니다.
(3) Cluster의 국가 별 나이 중위수의 특징을 보기 위하여 Histogram을 내림차순으로 정렬하였습니다.
(4) Cluster 별 GDP를 보기 위하여 트리맵을 생성하였습니다.
(5) 인구수 순증가와 이민자 순증가를 보기 위하여 이민자 순증가를 X축, 인구수를 Y축으로 설정하여 Scatter Plot을 생성하였습니다.
```
### Insight
- 출산율과 인구수에 대한 Clustering 분석을 통해 이민자 순증가, 출산율과의 관계에서 여러 인사이트를 얻을 수 있었습니다.
    - 중국과 인도로 묶인 Cluster는 매우 보수적인 출산 정책, 이민자 정책을 시행함을 확인할 수 있었습니다.
    - 중동-아프리카 내에서도 Cluster 별 출산율과 GDP의 음의 상관관계가 큼을 확인할 수 있었습니다.
    - OECD 국가 순위 상위 국가들의 고령화를 확인할 수 있었습니다.


