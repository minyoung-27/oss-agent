# week09 - 박스오피스 1위 조회

## 무엇을 하는 코드인가
영화진흥위원회(KOBIS) 오픈 API로 특정 날짜의 일별 박스오피스 1위 영화 제목을 가져옵니다.
`tools.py`의 `get_boxoffice_rank_1("YYYYMMDD")`가 영화 제목을 돌려줍니다.

## 설치
```bash
pip install -r requirements.txt
```
그리고 이 폴더에 `secret.py`를 만들고 KOBIS에서 발급받은 키를 넣습니다.
```python
API_KEY = "발급받은_키"
```

## 실행
```bash
cd week09
python main.py
```
2026년 8월 24일 박스오피스 1위 영화 제목과 함수 설명(docstring)이 출력됩니다.
