# Brad's Web Devlelopment Diary
## 페이지 소개
- 주소 : [https://to2.kr/cfB](https://to2.kr/cfB)
- 내용 : Spring Web Development Study
- 공부 Vlog
  링크예시) 박병규, 21-03-27, 공부 Vlog https://...(유튜브 업로드 영상 링크)
  
  - mac 화면 녹화 동영상 인코딩은 finder를 통해 빠르게 가능

---
## 2021-03-27 공부내용
### DB
  - Database 개론
  - [xampp](https://www.apachefriends.org/index.html) 설치
  - [SQlyog](https://formac.informer.com/sqlyog) 설치 
  - mysql 기본 문법
  
### Spring
  - [STS](https://spring.io/tools) setting
  - Spring Boot 이론 학습
  - [lombok](https://projectlombok.org/download) 설치
  - [maven](https://mvnrepository.com/) 활용 방법
  - 개발 환경 세팅
  - [git](https://git-scm.com/) 연동
    - ssh키 활용하여 깃허브 등록, 연결 및 확인
    
  - [github](https://github.com/) clone, pull, push 완료

#### UsrHomeCtroller
- @RequestMapping
- @ResponseBody
- 쿼리를 통해 브라우저에 출력 구현
- 브라우저와 java 프로그램의 인식의 범위 차이 확인
---
## 2021-03-28 공부내용
### DB
  - mySQL 기본 문법
    - DDL, DML 차이점
    - drop, create, alter
    - selecet, insert, update, delete 

### Spring
  - JSON Formatter : 크롬에 설치하여 웹에서 json형식 확인
  - dto, dao, service 구축
  - lombok 활용 : 반복적인 코드 작성을 대신해줌
    - 생성자, getter, setter, toString 등을 자동 생성
    
  - controller, service, dao의 상호작용 이해를 통한 구축
  
  - article, articleDao, articleService, articleController
 는 스스로 구축가능하게 이해 및 구축 연습 필요
 
  - util은 참고해서 작성해도 무방한 부분


### Spring boot 학습내용
  - @Controller : 소스파일이 컨트롤러임을 알게 해주는 어노테이션
  
  - @Autowired : 스프링 프레임워크에서 관리하는 Bean 객체와 같은 타입의 객체를 찾아서 자동으로 주입해주는 것
  
  - 입력값이 없는 경우 int는 null을 받을 수 없지만 Integer는 받을 수 있음. 처리할 수 있는 데이터의 범위가 int가 Integer보다 좁음.
  
  ---
## 2021-03-29 공부내용
### Spring

  - Board Application Structure Rebuilding
  
  - Today's goal : Build below
  
    - Controller : 구현 기능 => 게시글 작성, 수정, 삭제, 열람
      - 입력된 데이터의 유효성 체크와 같은 작업을 수행한 후 서비스에게 전달
      - 서비스가 전달받은 데이터에 대한 검증을 하지 않아도 되도록 하기 위함
      - Controller, Service, DAO가 역할을 분담하여 현업에서 유지, 보수가 쉽게 프로그래밍
    
    - 4가지 쿼리문 작동 : doWrite, doModify, doDelete, getArticle
    
    - DAO : 컨트롤러의 주문을 받아 데이터 관련 단순 업무를 수행하는 메서드 구현
      - 서비스의 요청에 맞는 return 값을 설정하고 구현이 필요 
      
    - DTO : 객체 정보를 구현 / 객체 정의시 생성자, getter, setter, toString 등은 lombok을 활용하여 간단하게 구현 가능
      - 아래와 같은 어노테이션을 통해 구현
      - 정상 처리 여부는 Outline으로 확인이 가능
      - @AllArgsConstructor
      - @Data
      
    - Service : ResultData 의 형식으로 return 값을 컨트롤러에게 반환
    
    - 컨트롤러 => 서비스 => DAO 
      - @Autowired 어노테이션으로 객체 자동 연결 : 컨트롤러는 서비스와, 서비스는 DAO와 연결
      
      - @Autowired로 연결되기 위해서는 연결되는 클래스에 @Component가 반드시 있어야함
      - Service만 예외적으로 @Component가 대신 @Service를 사용
      - 컨트롤러에서는 서비스로만 요청하고, 서비스는 DAO로만 요청
      - 소스파일에서도 위와 같이 구현
      - 현업에서 대부분 사용하는 MVC패턴([Head First Design Patterns](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=582754) 참고 예정)
    
  - DB connection(차시 학습 예정)
    - DB 수업 예습과 더불어 지난 기수 학습 내용 공유 자료를 통해 학습 필요

### Java

  - HashMap, LinkedHashMap
    - LinkedHashMap은 입력 순서의 차이를 고려함 
    - util로 사용하는 mapOf의 구현 과정 : [2021 01 30 스프링부트, bY9, 22강, Util mapOf 구현연습](https://www.youtube.com/watch?v=xNzH40ZYDkg)
    
    - map vs DTO [[참고영상]](https://www.youtube.com/watch?v=67_Qp0lW-dM) 
      - map으로 데이터를 입력하는 경우는 구성의 자유도가 높음
      - DTO를 활용하는 경우가 국내에서는 다수이며, 입력하는 개발자의 실수를 클래스 구성을 통해 방지하며 효율적인 방법
      - DTO 클래스 구성시 lombok을 활용하면 간단하게 구현 가능
      
    - ResultData 구현[[참고영상]](https://www.youtube.com/watch?v=zZE13aJAaZY)
      - 프로그래밍에 있어 2번 이상 반복이 되는 경우 공통되는 부분을 모듈화(클래스)하는 것이 중요
      - mapOf를 활용하는 것에서 중복된 부분을 정의한 ResultData 구현
    

### STS 활용 팁 (사이드 메뉴 폰트가 작아 안보이는 문제 해결)
- Package Explore 등 폰트 크기가 너무 작은 경우 해법
  - 프로그램의 CSS 폴더에서 폰트 사이즈 변경 + sts4.0 preferences/General/Appearance/Colors and Font/Veiw and Editor Folders/Tree and Table font for views 에서 폰트 사이즈 변경[(참조 링크)](https://stackoverflow.com/questions/47731327/change-project-explorer-tree-view-font-size-in-eclipse-oxygen/62838294#62838294?newreg=da90dd46ca2d4c229df3f020a7891933)
  
  - 전제적인 폰트 사이즈를 크게 하고 싶은 경우 : CSS 폴더 내에서 사용중인 테마의 모든 CSS 파일의 폰트 사이즈 변경(QHD 환경에서 14~16포인트 정도면 괘적함)
  
- 변수명 일괄 선택 단축키 : ctr + shift + R
- 소스파일 실행 단축키: ctr + R

---

## 2021-03-30 공부내용
### Spring
  - ForPrint : 게시물 내용에서 출력을 위한 내용을 정해서 요청할 때 사용
    - 예) getForPrintArticle();
  - 인터셉터를 추가해서 로그인 여부 등을 매번 확인하지 않도록 효율성을 높일 수 있음
    - 관련 소스는 검색해서 추가 가능 : 필요한 부분만 편집해서 사용
  - Mybatis : 현업에서 가장 많이 사용
  - 새 프로젝트 생성시 Mybatis Framework, MySQL Driver 선택
  - DB 연결을 위해서 MySQL Driver는 필수
  - pom.xml 도 체크
  
  - Mybatis 적용시 @Mapper 어노테이션 사용
  
    - ArticleDao의 내용을 모두 삭제하고 interface로 수정
    
    - Dao를 참조하던 소스파일의 메서드를 다시 생성하면 인터페이스이기에 추상메서드로 생성이 됨
    
    - ArticleDao와 쌍으로 ArticleDao.xml파일 작성이 필수
    - 지정 양식으로 쿼리 작성하면 이전과 같이 정상 작동
    - xml 파일 작성 예시([참고자료](https://github.com/jhs512/untactTeacher/commit/435d48acb44986325e9afc1696fc53ac4e3c6ce8))
    
```sql
 <insert id="ad Article" seGeneratedKeys="true" keyProperty="id">
		 INSERT INTO article
		 SET regDate = NOW(),
		 updateDate = NOW(),
		 title = #{title},
		 title = #{title},
		 `body` = #{body} 
 </insert>
```
  - xml에서도 if문 사용 가능

```sql
	<select id="getArticles" resultType="Article">
		SELECT *
		FROM article
		WHERE 1
		<if test="searchKeywordType == 'title'">
			AND title LIKE CONCAT('%', #{searchKeyword}, '%')
		</if>
		<if test="searchKeywordType == 'body'">
			AND `body` LIKE CONCAT('%', #{searchKeyword}, '%')
		</if>
		<if test="searchKeywordType == 'titleAndBody'">
			AND (title LIKE CONCAT('%', #{searchKeyword}, '%') OR `body` LIKE CONCAT('%', #{searchKeyword}, '%'))
		</if>
		ORDER BY id DESC
	</select>
```
    
  - 쿼리로거 적용하여, 콘솔에 실행되는 쿼리가 출력되도록 세팅 가능[[참고자료](https://www.youtube.com/watch?v=kbE_fOR4aD4)]
  
### MySQL
  - 사용자 권한 부여를 먼저 해야 DB 접근 권한이 생김 
  
  - 권한 부여 과정
    - XAMPP 최신 버전 필요[[xampp-osx-8.0.3-0-installer.dmg]](https://sourceforge.net/projects/xampp/files/XAMPP%20Mac%20OS%20X/8.0.3/xampp-osx-8.0.3-0-installer.dmg/download)
    - root 접속 후 계정 생성 및 권한 부여
    - root 계정 접속정보 : root/패스워드 없음
    - GRANT ALL PRIVILEGES ON *.* TO 계정명(sbsst)@`%` IDENTIFIED BY 계정비밀번호('sbs!123414');
    
    - 이후부터는 [계정명/계정비밀번호]로 사용 가능
    
  - inner join, left join 은 필수적으로 완벽히 이해하고 사용해야 함
    - 예) inner join 사용시에는 탈퇴한 회원이 작성한 글을 조회할 수 없지만, left join을 사용하면 조회 가능
    
  - IFNULL : NULL인 경우 처리 가능
  
  ### Java
  
  - 인터페이스 : 서로 관계가 없는 물체들이 상호 작용을 하기 위해서 사용하는 장치나 시스템
  
    - 인터페이스 정의하는 방법
      - 추상 메소드와 상수를 정의 가능
      
      - 인터페이스에서 변수를 선언하면 컴파일시 자동으로 상수로 변환해줌(final을 붙이지 않아도 됨)

    - 인터페이스 사용하는 방법
      - 인터페이스는 사용할때 해당 인터페이스를 구현하는 클래스에서 implements 키워드를 이용
      
      - 인터페이스가 가지고 있는 메소드를 하나라도 구현하지 않는다면 해당 클래스는 추상클래스가 됨(추상클래스는 인스턴스를 만들 수 없음)
      
---
## 2021-03-31 공부내용
### Spring
- 인터셉터를 활용하면 로그인 관련 정보를 모두 처리해두기 때문에 관련 메서드에서 일일히 처리하는 과정이 필요하지 않게 됨

- 기능 추가
  - 콘트롤러에 추가 => 서비스에 클래스 생성 및 구현 =>  => DAO에 클래스 생성 및 구현 => XML 소스에 쿼리 추가 =>객체 클래스 구현(필요한 경우) 
  - lombok, MyBatis 덕분에 구현이 간단해짐
  - 비슷한 기능을 가진 새로운 기능의 추가인 경우 기존에 구현한 메서드를 활용하여 구현
  
- SESSION 에서 로그인 정보를 기억하고 있으며, 이를 활용하여 로그인 이후 필요한 기능 구현 
- REQUEST는 요청 후 데이터를 삭제하기 때문에 로그인이 유지되는 동안 처리가 필요한 경우 해당 정보를 SESSION에 저장

  
### MySQL
- SELECT 문의 경우 뒤에 FROM ARTICLE이 없는 경우 SELECT 1 과 같이 입력하면 1이 입력된 데이터가 생성이 됨

- INSERT의 경우 아래와 같이 한번에 입력이 가능

```sql
insert into article
(regDate, updateDate, memberId, title, `body`)
SELECT NOW(), NOW(), FLOOR(RAND() * 2) + 1, CONCAT('제목_', FLOOR(RAND() * 1000) + 1), CONCAT('내용_', FLOOR(RAND() * 1000) + 1)
from article;
```

- 동적 SQL
- LIMIT 구문
  - LIMIT a; => 위에서부터 a개
  - LIMIT a, b; => a에서부터 b개 (a는 시작위치, b는 반환 갯수)
 - 게시판별 조회 및 출력
   - 게시판별로 다른 값을 입력하는 컬럼 추가 (예> 공지사항:1, 자유게시판:2)
   - 쿼리에서 boardId로 선택하여 출력
   - 조건 추가하여 원하는 조회화면 제공 가능
   
 - DB에 게시물과 댓글이 매우 많은 경우 관련 데이터를 모아서 제공하는데 검색 시간이 많이 걸릴 수 있는 문제점은 인덱스를 활용하여 해결
 - 인덱스에 조건을 걸어둔 순서대로 WHERE 문에 적용해야 올바로 인덱스 활용 가능
 - 최근에는 순서가 바뀐 쿼리도 자동으로 보정해서 검색을 해주기도 하지만, 그래도 순서를 지키는 것이 중요
 
 
       
---
## 2021-04-01 공부내용

### Java

- 객체 저장 복습
  - [배열없이 실습](https://replit.com/@brad0135/2021-03-31inryeoggwanriso-baeyeoleobsi-guhyeon#Main.java)
    - 생성하는 객체마다 변수 생성 후 저장
    
  - [배열로 실습](https://replit.com/@brad0135/2021-03-31inryeoggwanriso-baeyeolsayong#Main.java)
    - 리모컨을 담는 배열 생성하여 객체 관리
    
  - [리스트로 실습](https://replit.com/@brad0135/2021-03-31inryeoggwanriso-ArrayList-sayong#Main.java)
    - 저장공간에 제약을 받지 않는 리스트로 간편하게 구현
    
    
### Spring

- Java update 후 STS 혹은 이클립스 실행 오류 발생 이슈

- vm 파일 수정으로 해결하는 방법
  - 대부분 위와 같은 방법으로 해결이 되었으나 최근의 경우 해결이 되지 않는 문제점
- lombok이 설치되었으나 실행이 되지 않는 문제의 경우 ini 파일의 lombok 경로를 수정해서 해결
- 깃허브에 작업물이 보존되어 있기에 STS는 새로 설치하여 설치 안되는 문제점을 해결
- STS 세팅의 경우 다시 설정해줘야하는 번거로움과 필요한 프로그램의 다운로드 및 설정을 하는데 생각보다 시간이 소요됨
- 자바 업데이트 알림을 확인하고 가급적이면 해당업데이트로 인한 이슈가 정리된 다음에 업데이트를 하는 것이 좋지 않을까 함.
- 현재 m1 macbook의 경우 이슈가 발생하면 정리되는데 시간이 필요한 듯

### Postman

- 개발 중에 프로그램을 매번 쿼리를 작성하여 실행하는데 있어 불편함을 획기적으로 줄여주는 프로그램!!!
- 기능의 정상작동여부를 확인할 수 있는 명령어를 저장해두고 단축키로 실행하고 확인할 수 있음
- 명령어의 경우 계정으로 관리가 되기에 다른 기기에서도 로그인하면 바로 사용이 가능

### Vue 3.0

- [Vue 3.0 Study](https://codepen.io/NTL-design/pen/poRNezd?editors=1000)
- 위 링크에 학습 내용을 따로 정리
- 다이나믹 웹 구현을 위한 양방향 데이터 바인딩 프레임워크
- 게시판을 실제 웹으로 구현함에 있어 UI 구현을 쉽고 효율적으로 할 수 있게 도와주는 기능들 포함

---
## 2021-04-02 공부내용

### Java

- list, arrayList 차이점
- list는 인터페이스로 arrayList보다 큰 개념
- 따라서 실무에서는 list를 대부분 사용하여 융통성을 줄 수 있게 운영
  - 예시
```
list<article> articles = new arrayList<>();
```

- <>안은 Generic으로 생성할 타입을 선언
- list에 추가되는 객체들의 타입을 확인하여 오류 검출

- 컴파일 오류 vs 런타임 오류
- try, catch, finally 구문을 활용하여 오류를 처리하여 프로그램이 실행중지 되지 않도록 처리할 수 있음

### Spring

- Spring 프레임워크와 lombok을 활용한 Controller, Service, Dao, Dto 작성 복습
- Util class 들의 메서드 이해(현재까지는 위 프로그램 작성시 util은 기존 코드 활용)
- 
