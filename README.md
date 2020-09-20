# Ruby-on-Rails-tuto

### 출처 : https://rubykr.github.io/rails_guides/getting_started.html
---
### 미리 준비해야 하는 것들
- [루비](http://www.ruby-lang.org/en/downloads)언어 버전 1.8.7 이상
- [루비젬](https://rubygems.org/gems/rubyforge/versions/2.0.4) 패키징 시스템
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
 - windows 환경에서 실했했더니 Yarn을 설치해 달라고 나와서 [여기](https://yarnpkg.com/lang/en/docs/install/)에서 설치를 했습니다.
 - webpacker설치
 ```
 $ rails webpacker:install
 ```

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
 [이런 페이지가 나와야한다고](https://rubykr.github.io/rails_guides/images/rails_welcome.png) 하지만 다른 이미지가 나옵니다. 윈도우즈라서 그런지도 모릅니다. 아무튼 동산위에 사람들이 서서 축하해주는 이미지가 나왔음.
 
### hello rails 하기
  컨트롤러와 뷰정도는 있어야한다고 함. 아래 명령어로도 충분히 창을 띄울수 있다고 합니다.
  ```
  $ rails generate controller home index
  ```
  윈도우즈나 루비가 비표준의 방법으로 설치되어 있다면, 아마도 레일즈의 rails 커멘드에 대한 정확한 패스 정보를 루비에게 넘겨야 합니다. :ruby \path\to\your\application\script\rails generate controller home index.
  
  레일즈는 app/views/home/index.html.erb 포함해서 몇가지 파일을 만들겁니다. 아 파일은 home 컨트롤러의 index 액션(메소드)를 위한 템플릿으로 이용됩니다. 이 파일을 텍스트 에디터로 열어서 이 한줄을 포함하도록 수정해 주세요.
```
<h1>Hello, Rails!</h1>
```

### 어플리케이션 홈페이지 설정
 컨트롤러와 뷰를 만들었습니다. "Hello Rails" 를 보기위해 레일즈에게 요청을 해야합니다.
 이번 경우에는 root URL 에다가 “Welcome Aboard” 스모트 테스트 데신에 http://localhost:3000 에서 나타나게 해보죠.
 
 첫 단계 : 기본 페이지를 어플리케이션에서 삭제합니다.
 ```
 $ rm public/index.html
 ```
 레일즈는 컨트롤러가 생성하는 동적인 내용들보다, public 디렉토리내의 정적인 파일을 보여주는 것을 우선시합니다. 그래서 이 파일을 삭제해야하죠.
 
 이제, 홈페이지의 위치를 레일즈에게 알려주어야 합니다. config/routes.rb 를 에디터로 여세요.
 root :to 를 포함한 줄을 찾아서 주석을 해제하고 다음과 같이 변경하세요.:
 
 ```
 Blog::Application.routes.draw do
 
  #...
  # You can have the root of your site routed with "root"
  # just remember to delete public/index.html.
  root :to => "home#index"
 ```
이제 http://localhost:3000 에 브라우저로 접속하면, Hello, Rails! 를 볼수 있습니다.

### Scaffolding
 레일즈 발판(scaffolding)은 어플리케이션의 주요 요소를 빠르게 만드는 방법입니다. 새로운 리소스를 위해 모델, 뷰, 컨트롤러를 만들기 원하면, 발판(scaffolding)은 적합합니다.
 
### 리소스 만들기
 블로그(blog) 어플리케이션의 사례에서 여러분은 발판(Scaffolding)을 이용해서 Post 리소스를 만들수 있습니다. (이 Post 리소스는 블로그에서 하나의 글을 표현합니다.) 이 작업을 위하여 터미널에서 다음을 입력하세요.
 ```
 $ rails generate scaffold Post name:string title:string content:text
 ```
 
### 마이그레이션 실행하기
 db/migrate/{date}_create_posts.rb 파일에서 다음을 발견할 수 있습니다.
 ```
 class CreatePosts < ActiveRecord::Migration
  def self.up
    create_table :posts do |t|
      t.string :name
      t.string :title
      t.text :content
 
      t.timestamps
    end
  end
 
  def self.down
    drop_table :posts
  end
 end
 ```
 
 위 migration파일은 migration 작업을 수행하는 Up과 나중에 적용된 migration을 되돌리는 down 이렇게 두가지의 메소드를 가집니다.
 
 이 시점에서 다음의 rake 명령을 통해 migration을 실행 할 수 있습니다.
 ```
 $ rake db:migrate
 ```
 
### 링크 추가
 생성된 홈페이지에 posts 쓰기를 추가하려면, 링크를 추가해야 합니다. app/views/home/index.html.erb 을 열고 다음과 같이 수정하세요.
 ```
 <h1>Hello, Rails!</h1> <%= link_to "My Blog", posts_path %>
 ```
 link_to는 레일즈의 뷰 헬퍼로 내장된 메소드 입니다. 이 메소드는 텍스트를 기반으로한 링크를 생성합니다. – 이 경우에는 posts 의 경로 입니다
 
### 브라우저에서 Posts 작업
 이제 posts 작업을 할 준비가 되었습니다. 이를 위해서 http://localhost:3000 로 이동한 후에 “My Blog” 링크를 클릭하세요.
 
 레일즈는 여러분의 posts를 위한 index 뷰를 보여줄 겁니다. 현재는 데이터베이스에는 posts 가 저장되어 있지 않지만, New Post를 클릭하고 하나 만들수 있습니다. 그후에 수정하거나, 자세한 내용을 조회하거나, 삭제할 수 있는 posts(글)을 볼 수 있습니다. 모든 로직과 HTML은 단지 rails generate scaffold 명령어 한줄로 생성됩니다.
