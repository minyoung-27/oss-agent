# week09/tools.py 함수 정리 (수정 전)

## 개요

`tools.py`는 영화진흥위원회(KOBIS) 오픈 API로 박스오피스 정보를 가져오는 도구 모음이다.

- 외부 라이브러리: `requests`
- API 키: `secret.py`의 `API_KEY`를 import 해서 사용
- `BASE_URL`: KOBIS 일별 박스오피스 조회 API 주소 (`searchDailyBoxOfficeList.json`)

## 함수 목록

현재 함수는 **1개**다.

### `get_boxoffice_rank_1(data)`

그 날짜의 박스오피스 1위 영화 제목을 알려준다.

| 항목 | 내용 |
|---|---|
| 받는 것 | `data` (문자열) — 8자리 날짜. 예: `"20260824"` |
| 돌려주는 것 | (문자열) 1위 영화 제목. 예: `"오디세이"` |

**동작 순서**

1. `key`(API 키)와 `targetDt`(날짜)를 파라미터로 묶는다.
2. `requests.get`으로 `BASE_URL`에 요청한다. (timeout 10초)
3. 응답을 JSON으로 바꾼다.
4. `boxOfficeResult` → `dailyBoxOfficeList`에서 영화 목록을 꺼낸다.
5. 목록의 첫 번째(1위) 영화의 `movieNm`(제목)을 돌려준다.

## 눈에 띄는 점

- 매개변수 이름이 `data`인데 실제로는 날짜다. 함수 안에서 `data = response.json()`으로 같은 이름을 다시 써서 헷갈린다. (`date`나 `target_date`가 더 알맞아 보인다.)
- 에러 처리가 없다. 날짜 형식이 틀리거나 API 응답이 비어 있으면 `KeyError`/`IndexError`가 난다.
- `response.status_code`를 확인하지 않는다. 요청이 실패해도 그대로 JSON을 읽으려 한다.
- 1위만 돌려주므로 다른 순위나 관객 수 같은 정보는 얻을 수 없다.
