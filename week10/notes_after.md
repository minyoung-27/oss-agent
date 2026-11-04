작성: Claude Code / 확인: 이민영

# week09/tools.py 함수 정리

## 개요

- `tools.py`는 영화진흥위원회 KOBIS 오픈 API(Open API, 공개 응용 프로그램 인터페이스)로 박스오피스(box office, 영화 흥행 순위) 정보를 가져오는 도구 모음임
- 외부 라이브러리(library, 남이 만든 코드 묶음): `requests` 사용함
- API 키(API key, 인증 열쇠): `secret.py`의 `API_KEY`를 import(가져오기)해서 사용함
- `BASE_URL`(기본 주소): KOBIS 일별 박스오피스 조회 API 주소(`searchDailyBoxOfficeList.json`)임

## 함수(function) 목록

- 현재 함수는 **1개**임

### `get_boxoffice_rank_1(data)`

- 그 날짜의 박스오피스 1위 영화 제목을 알려줌

| 항목 | 내용 |
|---|---|
| 받는 것 | `data` (문자열, string) — 8자리 날짜. 예: `"20260824"` |
| 돌려주는 것 | (문자열, string) 1위 영화 제목. 예: `"오디세이"` |

**동작 순서**

1. `key`(API 키)와 `targetDt`(target date, 조회 날짜)를 파라미터(parameter, 요청 값)로 묶음
2. `requests.get`으로 `BASE_URL`에 요청(request)을 보냄. timeout(제한 시간)은 10초임
3. 응답(response)을 JSON(데이터 형식)으로 바꿈
4. `boxOfficeResult` → `dailyBoxOfficeList`에서 영화 목록을 꺼냄
5. 목록의 첫 번째(1위) 영화의 `movieNm`(movie name, 영화 제목)을 돌려줌

## 눈에 띄는 점

- 매개변수(parameter) 이름이 `data`인데 실제로는 날짜임. 함수 안에서 `data = response.json()`으로 같은 이름을 다시 써서 헷갈림. `date`(날짜)나 `target_date`(조회 날짜)가 더 알맞아 보임
- 에러 처리(error handling, 오류 대비)가 없음. 날짜 형식이 틀리거나 API 응답이 비어 있으면 `KeyError`(키 없음 오류)나 `IndexError`(위치 범위 오류)가 남
- `response.status_code`(응답 상태 코드)를 확인하지 않음. 요청이 실패해도 그대로 JSON을 읽으려 함
- 1위만 돌려주므로 다른 순위나 관객 수 같은 정보는 얻을 수 없음
