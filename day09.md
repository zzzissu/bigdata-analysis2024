## 9일차

- 빅데이터 실습
  - OpenAPI 기반 크롤링 실습
  - 통계 분석 리뷰
  - 머신러닝 실습

### 빅데이터 학습

#### OpenAPI 기반 크롤링 실습

- ![공공데이터포털](https://data.go.kr)
  - 국가 공공기관에서 무료로 제공하는 데이터 API 서비스 포털
  - 한국관광공사 관광빅데이터 GW API 사용
  - http 프로토콜로 요청해야함. https로 요청하면 ssl 오류발생

```python
# 반복해서 재처리
touristDatas = []
year = 2023
month = 12
# totalList = []
for day in tqdm(range(1, 32)):
    reqYmd = f'{year}{month}{day:02d}'
    data = getTouristDataService(reqYmd)
    if xmltodict.parse(data)['response']['body']['items'] == None:  # 해당날짜에 데이터가 없을 수 있음
        resList = []
    else:
        resList = xmltodict.parse(data)['response']['body']['items']['item']

    touristDatas = touristDatas + resList
```

100%|██████████| 31/31 [01:03<00:00, 2.06s/it]

#### 통계 분석 리뷰

- 그래프를 사용한 기술 통계 분석
- 히트맵을 사용한 상관분석
