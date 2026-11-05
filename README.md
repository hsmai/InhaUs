
![버전2](https://github.com/real-estate-index/real-estate-index-web/assets/99078115/bb4d12fd-0b03-4574-b1db-96c6358bea4e)

# InhaUs · 부동산 공포-탐욕 지수 웹 서비스

주식 시장의 공포-탐욕 지수를 부동산에 맞게 다시 설계해, 부동산 입문자가 시장 분위기를 한눈에 볼 수 있게 만든 웹 서비스입니다.<br>
2024-1 파이썬 기반 응용 프로그래밍 수업 프로젝트 (5인 팀)

### 주요 기능

- **공포-탐욕 게이지**: 부동산 지표 5종(심리지수, 검색량, 거래량, 거래 변동성, 모멘텀)을 같은 범위로 맞춘 뒤 가중 평균한 월별 지수 (2015.12 – 2024.02)
- **전국 지도 / 서울 구별 정보**: 지역을 고르면 그 지역의 지표를 조회
- **지표 그래프**: 거래량, 모멘텀, 심리지수, 평당 거래가
- **뉴스 / 이슈**: 부동산 관련 뉴스와 기관 자료를 한곳에

### 구조

- **백엔드**: Django, Django REST Framework (`/api/fear-greed-index`, `/api/news-and-issues/`)
- **데이터 처리**: Pandas로 국토교통부/한국부동산원 거래 자료를 서울 구별·월별로 요약하고 지수 산출 (`back_end/real_estate_project/data_preprocessing/`)
- **프론트엔드**: React

### 내 역할 (한상민)

- 백엔드와 지수 산출 파이프라인 담당: 거래 자료 요약, 지표 5종 정규화와 가중 평균, Django API로 지수와 뉴스·이슈 데이터를 프론트엔드에 제공

<br>

## 실행 방법

### 백엔드 실행하기

```terminal
# 가상 환경 생성
python -m venv venv

# 가상 환경 활성화
# Windows
.\venv\Scripts\activate

# macOS/Linux
source venv/bin/activate

# 장고 설치
pip install django djangorestframework

# 서버 실행 (back_end 폴더에서)
cd back_end
python manage.py runserver
```

### 프론트엔드 구성

```
front_end/
├── src/
│   ├── components/
│   │   ├── Map.js              # 한국 지도를 보여주는 컴포넌트
│   │   ├── FearGreedIndex.js   # Fear & Greed Index 보여주는 컴포넌트
│   │   ├── RegionDetails.js    # 선택된 지역의 세부 정보를 보여주는 컴포넌트
│   │   ├── Graph.js            # 그래프를 보여주는 컴포넌트
│   │   ├── NewsAndIssues.js    # 뉴스와 이슈를 보여주는 컴포넌트
│   ├── App.js                  # 주요 애플리케이션 컴포넌트
│   ├── index.js                # 애플리케이션 진입점
├── public/
│   ├── index.html              # 주요 HTML 파일
├── package.json                # 프로젝트 의존성과 스크립트
```

### 프론트엔드 실행하기

1. npm은 front_end 폴더 위치에서 실행해야 합니다.

    ```
    cd front_end
    ```

2. 패키지를 설치합니다.

    ```
    npm install --legacy-peer-deps
    ```

3. 프론트 서버를 실행합니다.

    ```
    npm start
    ```
