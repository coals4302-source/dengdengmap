# DengDengMap (댕댕맵)

> 전국 반려견 동반 관광 맞춤 추천 플랫폼 — 2026 한국관광공사 공모전 출품작

반려견과 함께 어디든 갈 수 있도록, 전국 반려견 동반 가능 장소를 지도 위에서 탐색하고 AI가 맞춤 코스를 추천해드립니다.

**[앱 바로가기](https://dengdengmap-zivnmzwjby6rszjmrtegwc.streamlit.app/)**

---

## 주요 기능

| 기능 | 설명 |
|------|------|
| 지도 통합 | 반려견 동반 가능 장소를 클러스터링 마커로 시각화 (카카오맵) |
| 견종 크기 필터 | 소형견 / 중형견 / 대형견 별 입장 가능 장소 필터링 |
| 카테고리 필터 | 관광지, 애견카페, 카페, 음식점, 문화시설, 레포츠, 숙박, 쇼핑 |
| 지역 필터 | 시도 / 자치구 단위 필터링 (전국 17개 시도) |
| 날씨 기반 산책 적합도 | 기상청 초단기예보 연동 — 온도, 강수, 풍속 기반 산책 추천 여부 표시 |
| AI 코스 추천 | 반려견 이름, 견종 크기, 현재 날씨를 고려한 맞춤 코스 생성 |
| 전체 장소 목록 | 필터 결과를 테이블로 확인 및 카카오맵, 홈페이지 링크 제공 |

---

## 기술 스택

- **Frontend**: [Streamlit](https://streamlit.io)
- **지도**: Kakao Maps JavaScript API (클러스터링 + 인포윈도우)
- **날씨**: 기상청 초단기예보 API
- **AI 추천**: ENNOEIA API
- **데이터**: 한국관광공사 반려동물 동반 여행지 데이터 (전처리 완료)
- **라이브러리**: `pandas`, `requests`, `python-dotenv`

---

## 실행 방법

### 1. 패키지 설치

```bash
pip install -r requirements.txt
```

### 2. 환경 변수 설정

프로젝트 루트에 `.env` 파일을 생성하고 아래 키를 입력합니다.

```
KAKAO_JS_KEY=카카오_JavaScript_앱키
KMA_API_KEY=기상청_공공데이터포털_API_키
ENNOEIA_API_KEY=ENNOEIA_API_키
```

> Streamlit Cloud 배포 시에는 `.env` 대신 **Secrets** 에 동일한 키를 등록합니다.

### 3. 앱 실행

```bash
streamlit run app.py
```

---

## 파일 구조

```
.
├── app.py                         # 메인 Streamlit 앱
├── requirements.txt               # 의존 패키지
├── .streamlit/
│   └── config.toml                # Streamlit 테마 설정
└── data/
    └── pet_tour_preprocessed.csv  # 전처리된 반려동물 동반 여행지 데이터
```

---

## API 키 발급

| 키 | 발급처 |
|----|--------|
| `KAKAO_JS_KEY` | [Kakao Developers](https://developers.kakao.com) 앱 생성 후 JavaScript 키 복사 |
| `KMA_API_KEY` | [공공데이터포털](https://www.data.go.kr) 기상청 단기예보 조회서비스 신청 |
| `ENNOEIA_API_KEY` | ENNOEIA 플랫폼 |

---

## 데이터 출처

한국관광공사 반려동물 동반 여행지 데이터 (공공데이터포털)