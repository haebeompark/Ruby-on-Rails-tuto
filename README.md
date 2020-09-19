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

### REST
 REST는 Representational State Transfer를 의미하고 RESTful 아키텍쳐의 근간이 됩니다.
- REST의 두가지 중요한 원리
  - 자원 표현을 위해 자원 식별자 사용 (가령 URL)
  - 시스템 컴포넌트 간에 자원 상태 교환

### 레일즈 어플리케이션에서 요청 예시
```
DELETE /photos/17
```
photo 리소스 ID 17번을 삭제하는 액션

---
## 새로운 레일즈 프로젝트 만들기

### 레일즈 설치하기
 대부분의 경우, 가장 쉬운 레일즈 설치는 RubyGem을 통하는 방법입니다.
 
 root에서 실행 - Unix 환경에서 이루어지기 때문에 가능하다면 Windows대신 Linux 가상 머신에 레일즈를 설치하고 사용하는 것을 권장합니다.
```
# gem install rails
```

### 블로그 어플리케이션 만들기
 시작하기 위해 터미널을 열고 만들고자 하는 폴더로 이동한 뒤 다음을 입력합니다.
```
$ rails new blog
```
 이 명령은 "blog 디렉토리" 에 "블로그(Blog) 레일즈 어플리케이션" 을 만듭니다. - rails new -h로 레일즈 어플리케이션 생성에 대한 옵션을 확인 할 수 있습니다.

 blog 어플리케이션을 만들었다면 해당 폴더로 이동합니다.
```
$ cd blog
```

| 파일 / 폴더                                   | 목적                  |
| ------------------------------------------ | ------------------------ |
| Gemfile                                    | 이 파일은 여러분의 레일즈 어플리케이션에게 필요한 젬의 의존성 정보를 기술하는데 사용됩니다. |
| README                                     | 어플리케이션에 대한 짤막한 설명       |
| Rakefile                                   | 터미널에서 실행할 수 있는 배치잡 |
| app/                                       | 어플리케이션을 위한 컨트롤러, 모델, 뷰를 포함합니다 이 튜토리얼에서 주로 다룰 예정       |
| config/                                    | 어플리케이션의 실행 시간의 규칙, 라우팅, 데이터베이스 등의 설정을 저장 |
| config.ru                                  | 랙(Rack) 기반의 서버들이 시작할때 필요한 설정 |
| db/                                        | 현재 데이터베이스의 스키마       |
| doc/                                       | 어플리케이션에 대한 자세한 설명 문서 |
| lib/                                       | 어플리케이션을 위한 확장 모듈       |
| log/                                       | 어플리케이션의 로그 파일 |
| public/                                    | 외부에서 볼수 있는 유일한 폴더 입니다.이미지, 자바스크립트, 스타일시트나 그외 정적인 파일들은 이곳에 두세요.       |
| script/                                    | 레일즈 스크립트를 포함합니다. 여러분의 어플리케이션을 실행시키거나, 배포, 실행 관련한 스크립트를 두세요. |
| test/                                      | 유닛 테스트, 픽스쳐, 그와 다른 테스트 도구들 입니다. 이 부분은 [레일즈 어플리케이션 테스트하기](https://rubykr.github.io/rails_guides/testing.html) 가 담당합니다.       |
| tmp/                                       | 임시 파일       |
| vendor/                                    | 서드 파티 코드들을 위한 공간입니다. 일반적인 레일즈 어플리케이션은 루비 젬과 레일즈 소스-프로젝트 내에 설치시-와 미리 패키징된 추가 플러그인들이 위치합니다.      |

### 필요한 젬 설치하기
```
# bundle install
```

### 데이터베이스 설정
 config/database.yml의 development 환경
 - SQLite3 데이터베이스 설정하기
 ```
 development:
  adapter: sqlite3
  database: db/development.sqlite3
  pool: 5
  timeout: 5000
 ```
 - MySQL 데이터베이스 설정
 ```
 development:
  adapter: mysql2
  encoding: utf8
  database: blog_development
  pool: 5
  username: root
  password:
  socket: /tmp/mysql.sock
 ```
 - Postgre SQL 데이터베이스 설정
 ```
 development:
  adapter: postgresql
  encoding: unicode
  database: blog_development
  pool: 5
  username: blog
  password:
 ```
 
### 데이터베이스 생성
  rake명령어로 db생성
  ```
  $ rake db:create
  ```
  이 명령어는 개발(development)과 테스트를 위한 SQLite3 데이터베이스를 db 폴더에 만들 것입니다
  
---

## Hello, Rails!
  헬로월드 레일버전인듯 합니다

### 웹서버 시작하기
 명령어로 서버 실행
 ```
 $ rails server
 ```
 이후 http://localhost:3000 으로 시도해보기
 [이런 페이지가 나와야함](https://rubykr.github.io/rails_guides/images/rails_welcome.png)
 
### hello rails 하기
  컨트롤러와 뷰정도는 있어야한다고 함. 아래 명령어로도 충분히 창을 띄울수 있다고 합니다.
  ```
  $ rails generate controller home index
  ```
  윈도우즈나 루비가 비표준의 방법으로 설치되어 있다면, 아마도 레일즈의 rails 커멘드에 대한 정확한 패스 정보를 루비에게 넘겨야 합니다. :ruby \path\to\your\application\script\rails generate controller home index.
  
  레일즈는 app/views/home/index.html.erb 포함해서 몇가지 파일을 만들겁니다. 아 파일은 home 컨트롤러의 index 액션(메소드)를 위한 템플릿으로 이용됩니다. 이 파일을 텍스트 에디터로 열어서 이 한줄을 포함하도록 수정해 주세요.

<h1>Hello, Rails!</h1>
