# boxoffice — KOBIS 박스오피스 조회 스킬

## 하는 일
영화진흥위원회(KOBIS) 일별 박스오피스를 조회한다. 특정 날짜의 1위 영화나 관객 수를 물을 때 사용한다.

## 들어 있는 파일
- .claude/skills/boxoffice/SKILL.md
- .claude/skills/boxoffice/scripts/boxoffice.py
- .claude/skills/boxoffice/LICENSE

## 필요한 것
secret.py — API KEY
tools.py — 박스오피스 정보를 가져오는 도구 모음

## 설치
.claude\skills\boxoffice
reload-skills 할 것.

## 바깥으로 요청하는 곳
"https://www.kobis.or.kr/kobisopenapi/webservice/rest/"
            "boxoffice/searchDailyBoxOfficeList.json"

## 키
secret.py에 키를 저장할 것.

## 권한
allowed-tools가 따로 없고, 명령할때 권한 요청만 하면 가능.

## 라이선스
MIT License
.claude\skills\boxoffice\LICENSE