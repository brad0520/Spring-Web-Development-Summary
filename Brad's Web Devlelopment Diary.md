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
- DataBase(DB)

  - 공유되어 사용될 목적으로 통합 저장, 관리되는 데이터.
  - 검색과 갱신등을 효율적으로 하기 위해 구조화된 데이터.
  - 관련된 테이블들의 집합.(테이블 폴더)

- 테이블(Table)

  - 사물이나 개념의 본질적인 속성을 모아서 표로 만든것.
  - 사물이나 개념을 표현하는 단위
    ex) 학생(사물, 개념) - 학번, 이름, 전공 (속성)
  - 테이블은 엑셀 파일과 비슷하다.

- DBMS(DataBase Management System)

  - 데이터베이스를 체계적으로 관리할 수 있도록 기능을 제공하는 프로그램
  - 대표적인 DBMS : Oracle, MySql, MsSql

- SQL(Structed Query Language)

  - DBMS를 다루기 위한 표준화된 언어 체계.

  - [xampp](https://www.apachefriends.org/index.html) 설치
  - [SQlyog](https://formac.informer.com/sqlyog) 설치
  - mysql 기본 문법

### Spring

- [STS](https://spring.io/tools) setting
- Spring Boot 이론 학습
- [lombok](https://projectlombok.org/download) 설치
- [maven](https://mvnrepository.com/) 활용 방법
- 개발 환경 세팅
  - 이클립스 Emmet : http://emmet.io/eclipse/updates
- [git](https://git-scm.com/) 연동
  - ssh키 활용하여 깃허브 등록, 연결 및 확인
- [github](https://github.com/) clone, pull, push 완료

### UsrHomeCtroller

- @RequestMapping

  - 주소창의 쿼리와 메서드를 연결해줌

- @ResponseBody
  - 메서드의 결과를 브라우저에 출력
- 쿼리를 통해 브라우저에 출력 구현
- 브라우저와 java 프로그램의 인식의 범위 차이 확인

---

## 2021-03-28 공부내용

### DB

- mySQL 기본 문법
- DDL, DML 차이점

- 데이터 정의 언어(DDL)

  - 데이터베이스, 테이블 생성 : CREATE

    - 데이터베이스 생성 : CREATE DATABASE 데이터베이스명
    - 테이블 생성 : CREATE TABLE 테이블명

  - 테이블 구조 변경 : ALTER TABLE
    - 칼럼 추가 : ALTER TABLE 테이블명 ADD COLUMN 칼럼명 타입(크기) 제약조건
    - 칼럼 수정 : ALTER TABLE 테이블명 MODIFY COLUMN 칼럼명 타입(크기) 제약조건
    - 칼럼 삭제 : ALTER TABLE 테이블명 DROP COLUMN 칼럼명
    - 칼럼명 변경 : ALTER TABLE 테이블명 CHANGE 칼럼명 새칼럼명 타입(크기)
      - 제약의 종류 :
        - PRIMARY KEY : 주키 설정(데이터 중복 허용X + not null)
        - NOT NULL : NULL데이터 허용 안함. 무조건 데이터 들어와야함.
        - AUTO_INCREMENT : 자동증가. int형이고 주키인 컬럼에만 사용.
        - UINSIGNED : 음수 표현 제거.
        - UNIQUE : 중복데이터 허용 X
    - 테이블, 데이터베이스 삭제 : DROP
      - 데이터베이스 삭제 : DROP DATABASE 데이터베이스명
      - 테이블 삭제 : DROP TABLE 테이블명
    - 테이블 내 모든 데이터 삭제 : TRUNCATE
      - TRUNCATE TABLE 테이블명

- 데이터 조작 언어(DML)
  - 데이터 조회 : SELECT
    - SELECT 칼럼 FROM 테이블 WHERE 조건
  - 데이터 수정 : UPDATE
    - UPDATE 테이블 SET 칼럼 = 값, .... WHERE 조건
  - 데이터 삽입 : INSERT
    - INSERT INTO 테이블 SET 칼럼 = 값, ...
  - 데이터 삭제 : DELETE
    - DELETE FROM 테이블 WHERE 조건

### Spring

- JSON Formatter : 크롬에 설치하여 웹에서 json형식 확인
- dto, dao, service 구축
- lombok 활용 : 반복적인 코드 작성을 대신해줌
  - 생성자, getter, setter, toString 등을 자동 생성
- controller, service, dao의 상호작용 이해를 통한 구축

- article, articleDao, articleService, articleController 는 스스로 구축가능하게 이해 및 구축 연습 필요

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
  - GRANT ALL PRIVILEGES ON _._ TO 계정명(sbsst)@`%` IDENTIFIED BY 계정비밀번호('sbs!123414');

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
  - 콘트롤러에 추가 => 서비스에 클래스 생성 및 구현 => => DAO에 클래스 생성 및 구현 => XML 소스에 쿼리 추가 =>객체 클래스 구현(필요한 경우)
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

#### 지난 주 복습 파트

- Spring 프레임워크와 lombok을 활용한 Controller, Service, Dao, Dto 작성 복습
- Util class들의 메서드 이해(현재까지는 위 프로그램 작성시 util은 기존 코드 활용)

#### Web Project

1. JSP, JSTL 설정

   - application.yml 파일에 환경 설정 소스를 추가하여 mybatis, jsp, mysql 등을 활성화 시킴
   - pom.xml 파일에도 사용하고자 하는 라이브러리를 추가해야 함
   - maven project의 핵심인 pom.xml 파일로 이 파일을 잘 설정하면 프로젝프 실행과 배포를 위한 설정을 완료할 수 있음
   - maven project의 dependencies(필수사항) : 라이브러리를 불러오는 부분
   - src/main/webapp/WEB-INF/jsp/adm/member/login.jsp => jsp 파일 생성은 필수
   - @responseBody 를 하지 않는 경우 폴더 경로를 찾아서 실행함

2. CSS 작업환경 세팅

   - [테일윈드](https://tailwindcss.com/)로 css 작업을 하면 효율적 : 추후 학습이 필요
   - 직접 css파일을 조작하지 않고 html태그에 입력하여 화면 구성요소를 꾸밀 수 있음
   - 사용하고자 하는 디자인을 선택하고 적용된 테일윈드 클래스명을 복사해서 붙여넣기로 간단하게 구현 가능
   - 직접구현하는 것보다 UI구현에 시간을 절약할 수 있음

3. 인터셉터

   - beforeActionInterceptor
     - 필터링(X)
     - 정보강화 표준화
     - req.set
   - needAdminInterceptor

   - needLoginInterceptor

   - needLogoutInterceptor

- 4개의 인터셉터의 역할로 인해 컨트롤러의 일이 많이 줄어듬

4. JSP
   - header, footer 등으로 나누고 include
   - common.css 등의 파일 작성 및 폴더 생성 및 정리

---

## 2021-04-03 공부내용

### Java Dao 구조

- MVC 구조 개념

  - Model : 어플리케이션의 핵심
    - Service : 어플리케이션의 핵심로직
    - DAO : 데이터 관리자
    - DTO : 데이터 단위
  - Controller : 사용자의 요청을 받아서 해석한 후 Model에게 다시 요청한다.
  - View : 사용자가 보는 화면을 의미한다.

- MVC 구조를 은행에 비유
  - APP은 청원경찰이다.
    - 이 분은 고객이 대출업무인지, 일반금융업무인지만 판단해서 올바른 컨트롤러(창구직원)에게 보내준다.
  - 컨트롤러는 창구직원이다.
    - 이 분은 고객이 어떠한 일을 하기 위해서, 필요한 정보를 챙겨왔는지, 혹은 그 일을 예전에 이미 했는지, 그 일을 하는게 가능한지 등을 판단하고, 조금이라도 부족하면 고객의 요청을 거절하는 역할을 한다.
    - 고객이 올바른 데이터를 챙겨왔고, 현재 그일을 수행하는게 가능한 상태라면, 컨트롤러는 서비스(과장)에게 고객의 요구를 토스한다.
  - 서비스는 과장급 직원이다.
    - 이 분은 고객을 직접 만나지는 않는다. 컨트롤러가 고객의 요구를 깔끔하게 정리해서 보내주면 그것을 판단해서 가/부를 결정하고 가능하다면 처리한다음, 그 결과를 컨트롤러에게 알려준다.
    - 단 이 분이 일을 하면서, 데이터를 저장하고, 검색하고, 수정하고, 삭제하는 일도 해야한다면 그런일만 따로 DAO(데이터 창고지기)에게 요청한다.
    - 오직 서비스만이 해당 어플리케이션의 핵심로직을 알고 있다.
  - DAO는 과장님의 하인인 창고지기이다.
    - 이 분은 이 애플리케이션의 핵심로직이 뭔지 모른다.
    - 다만 과장님이 시키는 아주아주 단순한 일들만 한다.

### JDBC

- java에서 mySQL을 사용하기 위해 사용하는 JDBC

```
		// JDBC
		// 1. Driver 찾기 - 찾은 드라이버는 DriverManager로 사용 가능
		Class.forName("com.mysql.cj.jdbc.Driver");

		// 2. DBMS에 연결

		String url = "jdbc:mysql://localhost:3306/board?serverTimezone=UTC";
		String id = "sbsst"; // root
		String pw = "sbs123414"; // "";

		Connection conn = DriverManager.getConnection(url, id, pw); // 연결.

		// 3. sql 문을 실행.
		// 3.1 - 실행할 sql문
		String sql = "SELECT * FROM article";

		// 3.2 - 작성된 sql문을 DBMS에 전달.
		// Connection - 팀장.  실무자 - Statement
		// sql처리 실무자 파견

		// 자동임포트 : ctrl + shift + o
		Statement stmt = conn.createStatement();

		// 3.3 - DBMS에서 가져온 데이터를 ResultSet으로 담아 옴.
		// ResultSet -> 조회 결과물(데이터)을 담는 상자.
		ResultSet rs = stmt.executeQuery(sql); // 조회 결과가 있는 경우 => select 문
		// stmt.executeUpdate(sql); // 조회 결과 없이 DB에 반영만 하는 경우 => insert, update, delete


		// 4. next메서드로 커서를 이동시켜 각 row들의 데이터를 읽어옴
		while(rs.next()) {
			String title = rs.getString("title"); // 해당 커서가 위치한 row의 title 컬럼 데이터를 반환.
			System.out.println(title);
		}

		// 사용한 자원들 반납
		if(rs != null) {
			rs.close();
		}
		if(stmt != null) {
			stmt.close();
		}
		if(conn != null) {
			conn.close();
		}
```

- 반복적으로 사용하는 부분은 묶어서 재사용하면 반복되는 부분이 많아 생각보다 사용하기가 쉬움
- sql 쿼리를 잘 작성해야 원하는 결과를 도출할 수가 있음

### Spring Web project

- DBMS 연결
- DB 스키마 생성
  - 기능 혹은 라이브러리 적용 등 설정 값에 변화가 생기면 application.yml 파일과 pom.xml 파일을 반드시 수정 적용해야함
  - 필요한 jar 파일의 경우도 라이브러리 추가 확인 필요
- Dao에 MyBatis 적용

  - lombok과 마찬가지로 간결한 코드작성에 큰 도움이 됨
  - 작성 규칙을 숙지해야함
  - DAO를 인터페이스(interface)로 만들고 내부의 메서드들도 모두 public을 붙이지 않아도 됨
  - DAO의 변수는
    - @Param("id") int id 와 같이 작성
  - @Mapper 로 변경

  - sql 쿼리는 DAO와 동일한 이름의 xml파일에 작성
  - 변수는 #{}안에 표기
  - 코드 예시

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.sbs.untact.dao.ArticleDao">

<select id="getArticleById" resultType="Article">
		SELECT *
		FROM article AS A
		WHERE A.id = #{id}
		AND A.delStatus = 0
	</select>

	<select id="getLastInsertId" resultType="int">
		SELECT LAST_INSERT_ID()
	</select>

	<update id="modifyArticle">
		UPDATE article
		SET updateDate = NOW(),
		title =
		#{title},
		body = #{body}
		WHERE id = #{id}
	</update>

	<insert id="writeArticle">
		INSERT INTO article
		SET regDate = NOW(),
		updateDate = NOW(),
		boardId = #{boardId},
		memberId = #{memberId},
		title = #{title},
		body = #{body}
	</insert>

	<update id="deleteArticleById">
		UPDATE article
		SET delStatus = 1,
		delDate = NOW()
		WHERE id = #{id}
	</update>

</mapper>
```

- jsp 연결
  - MpaUsrHomeController를 통해 메인페이지 구현
  - 기본폴더 설정에 유의 : css, js 파일을 위치시킬 폴더와 MpaUsrHomeController 내의 jsp파일의 경로는 다름
- css, html 직접 작성 대신 라이브러리 활용

  - 테일윈드 등의 라이브러리로 UI는 빠르게 구현하고 필요한 부분만 커스터마이징

  ***

## 2021-04-04 공부내용

### DATABASE

- DB와 DAO, DTO 중에서 한 곳에서만 int나 date관련 기능을 수행하면 되기 때문에 핸드폰번호나 날짜 관련 변수는 한 곳에서만 해당 유형의 데이터 타입으로 처리하고 나머지는 String으로 처리

- rs, stmt, conn는 선언된 순서에 관련하여 닫는 순서는 가장 나중에 선언된 rs부터 conn순으로 함

- 컨트롤러(해당 소스)에서 입력값과 관련된 기능을 모두 수행, 오류체크, 변수 입력 등의 작업 : MVC 패턴을 유지하여 유지, 보수가 용이해짐

- mySQL
  - inner join 으로 분리한 데이터 테이블을 조합하여 검색

### Spring

- DBMS 사용자 계정 추가
  - GRANT ALL PRIVILEGES ON . TO 'sbsst'@`%` IDENTIFIED BY 'sbs123414';
  - 개인 PC에서는 사용할 아이디와 비번을 설정하여 마스터 계정을 생성
  - 마스터 계정은 로컬이나 원격 모두 접근 권한을 가짐
- DB 스키마 생성
  - SQL에서 DEFAULT 0 으로 초기값 설정이 가능함
  - delStatus : 논리적 삭제와 물리적 삭제 중에서 관리자는 삭제된 데이터를 확인할 수 있게 논리적 삭제를 구현
  - SELECT LAST_INSERT_ID(); => 마지막 추가된 아이디를 바로 구할 수 있는 쿼리
  - 삭제된 데이터는 검색이 되지 않도록 쿼리에 and delStatus = 0 을 추가
  - sql 로거를 활용해서 콘솔을 통해 실행되는 쿼리를 확인할 수 있음
- JSP 연결 및 css, js 세팅

  - [JavaScript 편집툴 활성화 방법](https://creampuffy.tistory.com/66)
  - css 포매팅은 코드펜 css의 드롭다운 메뉴 중 Format css기능을 활용하여 해결하거나 vs code와 같은 다른 편집툴 활용
  - 이클립스의 포매팅을 사용하면 개발자가 의도한 변수 정의가 틀어질 가능성이 높음
  - css, js 파일에서 주석의 중요성 : 코드의 재활용을 위해서는 필수!!!
  - 디자인 시스템 동영상 참고 예정
  - 메뉴바에서 게시판 클릭시 해당 게시판으로 이동 : 컨트롤러에서 showList 기능 구현시 리턴값이 String 인 이유????? (jsp가 나와야한다는데 궁금...)
    => 나름의 정리 : @ResponseBody 를 삭제하고 해당 화면을 보여줄 JSP파일로 연결을 해줘야하기에 해당 주소를 ""에 담아 리턴

  - `+` : 인접 형제 선택자로 선행하는 요소 뒤를 따르는 형제 요소를 선택

  - list.jsp 파일이 하나인데 두 개의 게시판을 보여줄 수 있는 과정이 궁금...

  - 공통되는 부분 header, footer 등은 사용할 모든 페이지에서 include로 사용하면 유지, 보수가 쉬움
  - 카페24에서 홈페이지 작업시 제공하는 모듈과 같은 개념

---

## 2021-04-05 공부내용

### git 사용법 정리

- CMD git 명령어

  - git 프로그램 그 자체를 최신버전으로 업데이트
    - git update-git-for-windows
  - git 로그인 정보 없애기
    - git config --global credential.helper manager
    - git credential-manager delete https://github.com
  - git 설치 직후 사용자 정보 세팅
    - git config --global user.name "깃허브 계정 ID"
    - git config --global user.email "이메일"
  - 로컬 리포지터리 생성
    - git init
  - 원격 저장소와 연결
    - git remote add origin 저장소주소
  - 원격 저장소와 연결 삭제
    - git remote remove origin
  - 커밋할 파일 장바구니에 담기
    - git add .
  - 커밋
    - git commit -m "커밋 메시지"
  - 푸시
    - git push origin master
  - 과거로 돌아가기
    - git checkout -f 커밋번호
  - 현재로 돌아오기
    - git checkout -f master

- Github Desktop
  - 커멘드라인 인터페이스로 깃을 관리하는 것보다 직관적이고 자동으로 해결해주는 부분이 많음
  - push, pull이 필요한 내용을 알아서 알림으로 안내해주고, 히스토리 제공

### JDK 버전이 상이한 경우 해결 방법

- cmd에서 자바 버전 확인
- sts4.9 이상 버전은 내장 openjdk가 깔려있어서 사용하는 자바 버전이 상관이 없음 : 컴퓨터에 설치된 자바의 버전과 상관없이 구동이 가능함

- 컴퓨터에 기본적으로 설치된 자바의 버전과 sts에서 프로젝트가 요구하는 자바의 버전이 상이할 수 있음 : sts4.9 미만 버전인 경우 실행 오류가 발생할 수 있음
- 프로젝트의 pom.xml 파일의 자바 버전을 확인 : 11인 경우 프로젝트가 수행되기 위해 필요한 자바 버전이 11임을 나타냄
- 컴퓨터에 설치된 자바가 1.8(8버전)인 경우 빨간색 느낌표 오류 메세지가 발생함
- 해결 방법
  - pom.xml 파일의 자바 버전을 8로 수정
  - 환경설정 / Project Facets / Java 버전을 8로 수정(컴퓨터에 깔린 자바와 일치시킴)

### JSTL

- html에서 Java코드가 갖는 단점을 보완할 수 있는 el, jstl
- java에서 개발한 C버전으로 사용
- jsp 파일에 아래의 코드 추가

```
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
```

- pom.xml에 아래의 코드 추가

```
		<!-- SQL 로거 -->
		<dependency>
			<groupId>org.bgee.log4jdbc-log4j2</groupId>
			<artifactId>log4jdbc-log4j2-jdbc4.1</artifactId>
			<version>1.16</version>
		</dependency>

```

- 자바문법과 JSTL 코드 비교

```
<%@ page language="java" contentType="text/html; charset=UTF-8"
	pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1> EL/JSTL 연습</h1>

<!-- 변수 선언 -->
<%
	int num = 21;
%>
<c:set var="num2" value="11" />

<!-- 변수 출력 -->
<%
	out.println("jsp : " + num);
%>
<br>
<c:out value="jstl : ${num2}" />
<br>
<!-- 조건문 -->
<%
	if(num % 2 == 0) {
		out.println("even");
	}
	if(num % 2 == 1){
		out.println("odd");
	}

	if(num % 2 == 0) {
		out.println("even");
	} else {
		out.println("odd");
	}
%>
<c:if test ="${num2 % 2 == 0}">
	even
</c:if>
<c:if test ="${num2 % 2 == 1}">
	even
</c:if>

<c:choose>
	<c:when test="${num2 % 2 == 0}">
		even
	</c:when>
	<c:otherwise>
		odd
	</c:otherwise>
</c:choose>
<br>
<!-- 반복문 -->
<%
	for(int i = 1; i <= 10; i++) {
		out.println(i + " ");
	}
%>
<br>
<c:forEach var="i" begin="1" end="10" step="1">
	${i}
</c:forEach>

</body>
</html>
```

- Model model, model.addAttribute("", ) => 관련 내용 확인 필요 / ""안의 변수를 jsp에서 사용 가능하게 해줌

- Servlet 사용도 가능
  - HttpsServletRequest로도 가능
  - Servlet 정리 요망

```
import javax.servlet.http.HttpServletRequest;
```

- jsp에서 java controller에서 얻은 결과가 담긴 변수를 활용할 수 있게 해줌
- jsp에서는 변수를 ${변수}와 같이 표현식에 담아야 함
- JSP가 java로 만드는 html이기에 소스코드로 JavaScript 소스를 작성하여 활용할 수 있음
  - Vue나 React 같은 경우는 어떻게 함께 활용할 수 있을까?

### [HTLM, CSS 내용 정리](https://codepen.io/jangka44/live/BazXNEL)
- emmet 활용한 젠코딩 활용 
- inline은 높이 넓이 적용불가지만 inline-block은 가능
- [] : 속성, {} : 내용
- 

### 참고자료

- 여러 개의 데이터 출력시 마지막에는 콤마가 출력되지 않게 하는 코드

```
        for(int i=0; i< interest.length;i++)
        {
            if(i+1 == interest.length) {
                out.println(interest[i]);
            }else {
                out.println(interest[i]+",");
            }
        }
```

---

## 2021-04-06 공부내용

### Java

- 프로그래머스 자바 문제 풀이

### Spring

- 
