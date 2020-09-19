# Ruby-on-Rails-tuto

### 출처 : https://rubykr.github.io/rails_guides/getting_started.html
---
### 미리 준비해야 하는 것들
- [루비](http://www.ruby-lang.org/en/downloads)언어 버전 1.8.7 이상
- [루비젬](https://rubyforge.org/frs/?group_id=126) 패키징 시스템
- [SQLite3 데이터베이스](http://www.sqlite.org/)

### 루비언어를 배룰 수 있는 무료 문서들
- [Mr. Neighborly’s Humble Little Ruby Book](https://www.humblelittlerubybook.com/)
- [Programming Ruby](https://www.ruby-doc.org/docs/ProgrammingRuby/)
- [Why’s (Poignant) Guide to Ruby](https://mislav.uniqpath.com/poignant-guide/)

---
### 레일즈의 철학
- DRY - 반복하지 말 것 : 같은 코드가 존재한다면 좋지 않다.
- Convention Over Configuration - 설정보다는 관습 : 작은 단위의 끝없는 설정 파일을 줄여준다. (아직 잘 모르겠습니다.)
- REST 는 웹 어플리케이션의 최고의 패턴 : 리소스와 표준 HTTP 요청(HTTP verb)에 적합한 웹 어플리케이션 개발은 가장 빠른 방법이다.

### [MVC](https://ko.wikipedia.org/wiki/%EB%AA%A8%EB%8D%B8-%EB%B7%B0-%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC) 아키텍쳐
- 유저 인터페이스와 비지니스 로직 분리
- DRY 유지 편이성
- 유지보수를 위한 코드 관리 편이성

### 레일즈의 컴포넌트
 레일즈는 많은 개발 컴포넌트와 함께 제공됩니다.
- Action Pack - MVC 에서 VC 부분
  - Action Controller
  - Action Dispatch
  - Action View
- Action Mailer
- Active Model
- Active Record
- Active Resource
- Active Support
- Railties
