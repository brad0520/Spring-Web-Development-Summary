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

- 프로그래머스 자바 중급
  - 파트1. Object 클래스
    - Objcet클래스는 모든 클래스의 최상의 클래스
    - 아무것도 상속받지 않으면 자동으로 Object를 상속
    - Object가 가지고 있는 메소드는 모든 클래스에서 다 사용할 수 있다는 것을 의미
    
    - equals : 객체가 가진 값을 비교할 때 사용(사용목적에 맞게 오버라이딩해서 사용 가능)
    - toString : 객체가 가진 값을 문자열로 반환
    - hashCode : 객체의 해시코드 값 반환(자료구조에서 자주 사용)
    - Generate hashCode() and equals()로 자동 생성 가능
    
    
  - 파트2. java.lang 패키지 / 오토박싱
    - 자바는 기본적으로 다양한 패키지를 지원 그중에서 가장 중요한 패키지
      - java.lang패키지의 클래스는 import를 하지 않고도 사용할 수 있다.
      - java.lang패키지에는 기본형타입을 객체로 변환시킬때 사용하는 Wrapper클래스가 있다.
        - Boolean, Byte, Short, Integer, Long, Float, Double 클래스
      - 모든 클래스의 최상위 클래스인 Object도 java.lang패키지
      - 문자열과 관련된 String, StringBuffer, StringBuilder도 모두 java.lang패키지
      - 화면에 값을 출력할때 사용했던 System클래스도 java.lang패키지
      - 수학과 관련된 Math클래스도 java.lang패키지
      - Thread와 관련된 중요 클래스들이 java.lang패키지
      - 이외에도 다양한 클래스와 인터페이스가 java.lang패키지에 속해 있다.

```
    public class WrapperExam {
        public static void main(String[] args) {
            int i = 5; 
            Integer i2 = new Integer(5);
            Integer i3 = 5;     //오토박싱
            int i4 = i2.intValue();
            int i5 = i2;       //오토언박싱
        }
    }
```
- 
  - 
    - 오토박싱(Auto Boxing)
      - Integer i3 = 5; 숫자 5는 원래 기본형이지만 자동으로 Integer형태로 변환된다.
    - 오토 언박싱(Auto unboxing)
      - int i5 = i2; Integer객체타입의 값을 기본형 int로 자동으로 변환되어 값을 할당한다.
    - 오토박싱(Auto Boxing),오토 언박싱(Auto unboxing) 은 JAVA 5부터 지원한다. 이 때 내부적으로 Wrapper클래스들이 사용된다.
  
  - 파트3. java.util 패키지
    - Data, Calendar 클래스 
    - List, Set, Collection, Map 인터페이스 : 바로 사용하지 못하고 인터페이스를 구현한 클래스를 활용해 객체(인스턴스)를 생성하여 사용해야함
    - 메소드 체이닝(Method Chaing) : 자기 자신을 리턴하여 계속해서 자신의 메소드를 호출하는 방식
    - StringBuffer : 가지고 있는 메소드들은 대부분 자기 자신, this를 반환
      - StringBuffer클래스는 메소드 체인 방식으로 사용할 수 있도록 만들어져 있음
      
    - String 객체의 경우 불변클래스로 문자열끼리 더할 때 StringBuffer가 사용되어 매번 new로 Stringbuffer로 객체를 생성함. 자바에서는 객체를 생성할 때마다 메모리를 소모하므로 성능 저하에 영향을 줄 수 있음
    - 결론 : 문자열을 반복문 안에서 실행할 때는 성능상 문제가 발생할 수 있으므로 String 보다 StringBuffer를 사용하는 것이 좋음
    
    - 이터레이터 활용 : hasNext()의 불리언 값을 사용
    - Map 인터페이스 활용
      -  Map<String, String> map = new HashMap<>(); 과 같이 <Key, Value> 값을 지정하여 HashMap 인스턴스를 생성
  
  - 파트4. 날짜와 시간
    - Callendar
      - Calendar cal = Calendar.getInstance();
      
  - 파트5. IO
    - 입력과 출력
    - byte단위 입출력클래스는 모두 InputStream과 OutputStream이라는 추상클래스를 상속받아 만들어짐
    - byte단위로 읽어들일 때는 512바이트 씩 읽어오기 때문에 1바이트씩 읽는 것보다 512바이트씩 읽고 처리하는 것이 처리 속도가 빠름
    
    - 문자(char)단위 입출력클래스는 모두 Reader와 Writer라는 추상클래스를 상속받아 만들어짐
    - 파일로 부터 입력받고 쓰기 위한 클래스 : FileInputStream, FileOutputStream, FileReader, FileWriter
    
    - 배열로 부터 입력받고 쓰기 위한 클래스 : ByteArrayInputStream, ByteArrayOutputStream, CharReader, CharWriter
      - 해당 클래스들은 어디로부터, 어디에라는 대상을 지정할 수 있는 IO클래스로, 이런 클래스를 장식대상 클래스라고 함
      
    - DataInputStream, DataOutputStream같은 클래스를 보면 다양한 데이터 형을 입력받고 출력
    - PrintWriter는 다양하게 한줄 출력하는 pintln()메소드를 가짐
    - BufferedReader는 한줄 입력받는 readLine()메소드를 가짐
      - 이런 클래스들은 다양한 방식으로 입력하고, 출력하는 기능을 제공하며, 이런 클래스를 장식하는 클래스라고 함
      
    - IO의 모든 객체들은 사용이 끝나면 항상 닫아줘야함
      - 아래의 코드 참조
    
```
    public class ByteIOExam1 {
        public static void main(String[] args){     
            FileInputStream fis = null; 
            FileOutputStream fos = null;        
            try {
                fis = new FileInputStream("src/javaIO/exam/ByteExam1.java");
                fos = new FileOutputStream("byte.txt");

                int readData = -1; 
                while((readData = fis.read())!= -1){
                    fos.write(readData);
                }           
            } catch (Exception e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }finally{
                try {
                    fos.close();
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
                try {
                    fis.close();
                } catch (IOException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
        }
    }
```
- 
  - 
    - Char 단위 입출력(console)
      - char단위 입출력 클래스는 클래스 이름이 Reader나 Writer로 끝남
      - char단위 입출력 클래스를 이용해서 키보드로 부터 한줄 입력 받아서 콘솔에 출력
        - System.in - 키보드를 의미 (InputStream )
        - BufferedReader - 한줄씩 입력 받기위한 클래스
        - BufferedReader 클래스의 생성자는 InputStream을 입력받는 생성자가 없음
        - System.in은 InputStream 타입이므로 BufferedReader의 생성자에 바로 들어갈 수 없으므로 InputStreamReader 클래스를 이용해야함
    
```
    import java.io.BufferedReader;
    import java.io.FileWriter;
    import java.io.IOException;
    import java.io.InputStreamReader;
    import java.io.PrintWriter; 
    public class CharIOExam01 {
        public static void main(String[] args) {
            BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
            //키보드로 입력받은 문자열을 저장하기 위해 line변수를 선언               
            String line = null;     
            try {
                line = br.readLine()
            } catch (IOException e) {
                e.printStackTrace();
            }
            //콘솔에 출력 
            System.out.println(line);
        }
    }
```




---

## 2021-04-07 공부내용

### Java

- 프로그래머스 자바 중급

  - 파트5. IO
  
    - Char 단위 입출력(File)
      - char단위 입출력 클래스는 클래스 이름이 Reader나 Writer로 끝이 남
        - 파일에서 읽기위해서 FileReader 클래스 이용
        - 한 줄 읽어 들이기 위해서 BufferedReader 클래스 이용
          - BufferedReader 클래스가 가지고 있는 readLine() 메소드가 한줄씩 읽게 해줌
          - readLine()메소드는 읽어낼 때 더 이상 읽어 들일 내용이 없을 때 null을 리턴
        - 파일에 쓰게하기 위해서 FileWriter 클래스 이용
        - 편리하게 출력하기 위해서 PrintWriter 클래스 이용
        - 예시코드

```java
    import java.io.BufferedReader;
    import java.io.FileReader;
    import java.io.FileWriter;
    import java.io.IOException;
    import java.io.PrintWriter; 
    public class CharIOExam02 {
        public static void main(String[] args) {
            BufferedReader br = null; 
            PrintWriter pw = null;
            try{        
                br = new BufferedReader(new FileReader("src/javaIO/exam/CharIOExam02.java"));
                pw = new PrintWriter(new FileWriter("test.txt"));
                String line = null;
                while((line = br.readLine())!= null){
                    pw.println(line);
                }
            }catch(Exception e){
                e.printStackTrace();
            }finally {
                pw.close();
                try {
                    br.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
```


  - 파트6. 어노테이션
    - 어노테이션은 클래스나 메소드위에 붙으며, @(at)기호로 이름이 시작
    - 어노테이션을 클래스나 메타코드에 붙인 후, 클래스가 컴파일되거나 실행될 때 어노테이션의 유무나 어노테이션에 설정된 값을 통하여 클래스가 좀 더 다르게 실행되게 할 수 있어, 이런 이유로 어노테이션을 일정의 설정파일처럼 설명하는 경우도 있음
    - 어노테이션은 자바가 기본으로 제공해주는 것도 있고, 사용자가 직접 만들 수도 있음
      - 사용자가 직접 작성하는 어노테이션 : Custom 어노테이션
    - 커스텀 어노테이션을 이용하는 방법
      1. 어노테이션을 정의
      2. 어노테이션을 클래스에서 사용 (타겟에 적용)
      3. 어노테이션을 이용하여 실행
      
    - 패키지 익스플로러에서 [new - Annotation]을 이용하여 Count100이라는 어노테이션 생성 (예제)
      - Count100어노테이션을 JVM실행시에 감지할 수 있도록 하려면 @Retention(RetentionPolicy.RUNTIME)를 붙여줘야 함
      
```
  import java.lang.annotation.Retention;
  import java.lang.annotation.RetentionPolicy;

  @Retention(RetentionPolicy.RUNTIME) public @interface Count100 {

  }
```
- -       
  - "hello"를 출력하는 hello()메소드를 가지는 MyHello라는 클래스를 작성
    - hello메소드 위에 @Count100 어노테이션을 붙임
  
```
    public class MyHello {
        @Count100
        public void hello(){
            System.out.println("hello");
        }
    }
```

- -       
  - MyHello클래스를 이용하는 MyHelloExam클래스를 작성
    - MyHello의 hello메소드가 @Count100어노테이션이 설정되어 있을 경우, hello()메소드를 100번 호출
```
    import java.lang.reflect.Method;

    public class MyHelloExam {
        public static void main(String[] args) {
            MyHello hello = new MyHello();

            try{
                Method method = hello.getClass().getDeclaredMethod("hello");
            if(method.isAnnotationPresent(Count100.class)){
                    for(int i = 0; i < 100; i++){
                        hello.hello();
                    }
                }else{
                    hello.hello();
                }
            }catch(Exception ex){
                ex.printStackTrace();
            }       
        }
    }
```

  
  - 파트7. 쓰레드
    - Thread : 워드프로세서가 하나의 프로세스라면, 하나의 프로세스 안에서도 여러개의 흐름이 동작할 수 있게 해줌 
    
    - 쓰레드 예제 1)
      - Thread를 상속 받아서 쓰레드를 생성하는 방법
        - java.lang.Thread클래스를 상속받는다. 그리고 Thread가 가지고 있는 run()메소드를 오버라이딩
        - 10번 반복하면서 str을 출력
```
    public class MyThread1 extends Thread {
        String str;
        public MyThread1(String str){
            this.str = str;
        }

        public void run(){
            for(int i = 0; i < 10; i ++){
                System.out.print(str);
                try {
                    //컴퓨터가 너무 빠르기 때문에 수행결과를 잘 확인 할 수 없어서 Thread.sleep() 메서드를 이용해서 조금씩 
                    //쉬었다가 출력할 수 있게한다. 
                    Thread.sleep((int)(Math.random() * 1000));
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            } 
        } 
    }
```
- 
  - 
    - Thread 클래스를 상속받은 MyThread1을 사용하는 클래스
      - Thread를 상속 받았으므로 MyThread1은 Thread
      - 쓰레드를 생성하고, Thread 클래스가 가지고 있는 start() 메소드를 호출
      
```
    public class ThreadExam1 {
        public static void main(String[] args) {
            // MyThread인스턴스를 2개 만듭니다. 
            MyThread1 t1 = new MyThread1("*");
            MyThread1 t2 = new MyThread1("-");

            t1.start();
            t2.start();
            System.out.print("!!!!!");  
        }   
    }
```

- 
  -        
    - 쓰레드 예제 2)
      - Runnable인터페이스를 구현해서 쓰레드를 만드는 방법
        - Runable 인터페이스가 가지고 있는 run()메소드를 구현
```
    public class MyThread2 implements Runnable {
        String str;
        public MyThread2(String str){
            this.str = str;
        }

        public void run(){
            for(int i = 0; i < 10; i ++){
                System.out.print(str);
                try {
                    Thread.sleep((int)(Math.random() * 1000));
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            } 
        } 
    }
```
- 
  - 
    - Runable 인터페이스를 구현한 MyThread2 사용하는 방법
      - MyThread2는 Thread를 상속받지 않았기 때문에 Thread가 아님
      - Thread를 생성하고, 해당 생성자에 MyThread2를 넣어서 Thread를 생성
      - Thread 클래스가 가진 start()메소드를 호출
      
```
    public class ThreadExam2 {  
        public static void main(String[] args) {
            MyThread2 r1 = new MyThread2("*");
            MyThread2 r2 = new MyThread2("-");

            Thread t1 = new Thread(r1);
            Thread t2 = new Thread(r2);

            t1.start();
            t2.start();
            System.out.print("!!!!!");  
        }   
    }
```
- 
  - 동기화 메소드와 동기화 블록
    - 공유객체가 가진 메소드를 동시에 호출 되지 않도록 하는 방법
      - 메소드 앞에 synchronized 를 붙임
      - 여러개의 Thread들이 공유객체의 메소드를 사용할 때 메소드에 synchronized가 붙어 있을 경우 먼저 호출한 메소드가 객체의 사용권(Monitoring Lock)을 얻음
      
  - 쓰레드와 상태제어
    - 쓰레드는 실행가능상태인 Runnable과 실행상태인 Running상태로 나뉜다.
    - 실행되는 쓰레드 안에서 Thread.sleep()이나 Object가 가지고 있는 wait()메소드가 호출이 되면 쓰레드는 블록상태가 된다.
    - Thread.sleep()은 특정시간이 지나면 자신 스스로 블록상태에서 빠져나와 Runnable이나 Running상태가 된다.
    - Object가 가지고 있는 wait()메소드는 다른 쓰레드가 notify()나 notifyAll()메소드를 호출하기 전에는 블록상태에서 해제되지 않는다.
    - wait()메소드는 호출이 되면 모니터링 락을 놓게 된다. 그래서 대기중인 다른 메소드가 실행한다.
    - 쓰레드의 run메소드가 종료되면, 쓰레드는 종료된다. 즉 Dead상태가 된다.
    - Thread의 yeild메소드가 호출되면 해당 쓰레드는 다른 쓰레드에게 자원을 양보하게 된다.
    - Thread가 가지고 있는 join메소드를 호출하게 되면 해당 쓰레드가 종료될 때까지 대기하게 된다.      
    
  - 파트8. 람다
    - 익명 메소드
    - 메서드를 하나만 가지고 있는 인터페이스를 함수형 인터페이스라고 하는데, 이런 경우 메서드 하나를 전달하기 위해서도 객체를 생성해야하는 자바의 불편함을 해결하는 방법으로 람다표현식을 사용할 수 있음
    

### 자바 웹을 다루는 기술[Book Study]

- Servlet
  - 서블릿의 생명주기 메서드
    - 초기화 : init() 
    - 작업수행 : doGet(), doPost()
    - 종료 : destroy()
    
  - 사용자 정의 서블릿 만들기
    - HttpServlet 클래스를 상속받아서 만들며, init(), doGet(), destroy() 메서드를 오버라이딩해서 기능을 구현
  - 사용자 정의 서블릿 형식
  
```
  public class FirstServlet extends HttpServlet {
    @Override
    public void init() {
      ...
    }
    
    @Override
    public void doGet(HttpServletRequest req, HttpServletResponse resp) {
      ...
    }
    
    @Override
    public void destroy() {
      ...
    }
    
  }
```
- 
  - 톰갯의 servlet-api.jar 클래스 패스 설정하기
      - 이클립스 상단의 New 아이콘을 클릭한 후 Dynamic Web Project를 선택
      - 경로확인 후 Generate web.xml deployment descriptor 옵션의 체크박스에 체크한 후 Finish 클릭
      - Build path > Configure Build Path... 선택 / Libraries > Classpath > Add external JARs... 선택 / CATALINA_HOME(톰갯 루트 디렉터리)의 lib 디렉터리에 있는 servlet-api.jar 선택 후 열기 / 클랙스 패스의 설정을 확인한 후 종료
      
      
### HTML, CSS 정리

- a 태그의 호버 범위 조정 
  - 링크를 주고자 할 때 a 태그를 적용(기존 태그 안쪽에)
  - a 태그의 display 속성을 block으로 지정하면 둘러싼 태그를 기준으로 전체를 사용
  - 패딩 적용해서 여백을 적절히 조절 가능
  
- hover 적용
  - 가급적 html 태그의 좌측에 붙이는 것이 좋음
  
- inline : 글자화!! => 최소한의 너비를 갖으며, 너비와 높이를 지정해도 적용이 되지 않음
- inline-blcok : inline에 block 속성을 추가, 너비와 높이를 지정하면 적용이 됨
- inline 계열은 문자 취급하기에 부모 요소에서 text-align:center; 로 조절 => 스스로 정렬 불가능

- block : 무조건 한 줄을 사용, 기본값으로 너비를 가로 전체, 높이는 최소로 설정이 되어있음
- block 계열은 margin: 0 auto;로 가운데 정렬 => 스스로 정렬 가능      
- 태그는 부모, 자식 관계를 활용해서 작성 / 요소를 확정할 수 있음, 다른 요소와 설정이 겹치지 않게

- background-color 속성은 주고 시작하는게 레이아웃을 보다 빠르게 완성할 수 있음

- object-fit:cover; 주어진 너비, 높이에 이미지를 맞춤

- 이미지는 고유의 가로, 세로 비율을 유지하려는 속성을 가지고 있음
- 이미지는 부모의 가로, 세로 크기에 영향을 받지 않고 원래 크기를 기본적으로 유지함
- 부모 태그의 너비값을 설정하지 않고 이미지의 가로를 100%로 지정하면 반응형에서 부모의 크기에 따라 이미지의 크기가 자동 조절이 됨

- 코드펜 학습내용 블로그 올리는 방법
  - 코드펜에 저장한 다음 Embed / iframe 으로 복사한 후 블로그의 입력창의 html모드에서 붙여넣기 하면 손쉽게 공유 가능

- a 노멀라이즈 : color:inherit; => 텍스트 계열의 기본 컬러 속성은 black이 아닌 inherit이므로 주의 요망

- h1, h2, ... h태그들은 기본적으로 margin 속성을 갖기에 노멀라이즈에서 margin:0; 을 줌

- 상황에 맞는 태그가 있는 경우 

- body, ul, li 노멀라이징 : div와 차이가 없도록 일반화 시켜줌
  - margin:0;
  - padding:0;
  - list-style:none;
  
- 대부분 공통 서식을 쓰지만 일부만 변경이 되는 경우 기존 css를 활용하기 위해 html태그에 class를 추가하여 필요한 부분만 변경

- position:absolute; 인 경우 너비가 inline 요소처럼 줄어듬


---

## 2021-04-08 공부내용

### CSS, HTML

- n차 메뉴
  - 2차, 3차 메뉴 등은 항상 a태그의 형제인 ul로 구성 
  - 선택자에서 사용 용도에 따라 > 를 사용하여 자식요소만 선택하거나 일괄 적용이 필요한 경우는 > 를 생략한 후손 선택자를 활용하여 모두 하위 메뉴를 선택할 수 있음
  
  - 메뉴별로 호버시에 하위 메뉴가 보이게 할 때는 아래와 같이 작성
    ``` 
    .menu-box ul ul {
        display: none;   
        position: absolute; // 펼쳐졌을 때 주변에 영향을 주지 않게 하기 위함
    }
    
    .menu-box ul > li:hover > ul {
        display: block;
      }
    ```
    
  - 클래스 작명 규칙 : BEM
  - text-overflow: ellipsis;  => 잘린 글을 ... 으로 표시
  
- HTML 초기 메뉴 구성
  - con-min-with : 너비를 줄여도 더 이상 줄지 않는 한계 너비를 지정
  - con : 너비를 늘여도 콘텐츠가 담긴 부분이 더 이상 늘어나지 않는 한계 너비를 지정
  
  
### Sprin 복습
- 메뉴바에서 게시판 클릭시 해당 게시판으로 이동 : 컨트롤러에서 showList 기능 구현시 리턴값이 String 인 이유 =>  @ResponseBody 를 삭제하고 해당 화면을 보여줄 JSP파일로 연결을 해줘야하기에 해당 주소를 ""에 담아 리턴
  - 브라우저에 일반적인 홈페이지 형식으로 클라이언트에게 보여주기 위해 jsp로 그 기능을 넘김
  - 출력에 필요한 값들은 서블릿을 통해 변수로 담아 jsp로 전달

- list.jsp 파일이 하나인데 두 개의 게시판을 보여줄 수 있는 과정
  - [강의링크](https://youtu.be/aJqNiWmPsTc) 참조하여 확인
  - 서블릿으로 입력받은 보드아이디를 변수로 jsp에 넘겨서 요청값에 따라 결과 화면이 다르게 출력
  - 정적인 웹페이지가 아닌 동적인 웹페이지 구현
  
- Header, Footer 등으로 공통부분을 나눌 때 html 태그의 열리고 닫힘은 신경쓰지 않아도 공통부분이 정확히 나뉘도록 하면 오류가 발생하지 않음

- JSTL, Servlet 문법 정리 필요


---

## 2021-04-09 공부내용

### Spring

- @JsonIgnore 어노테이션을 통해 멤버의 정보중에서 로그인 비번이나 authKey와 같은 정보는 json 파일로 출력되지 않게 할 수 있음

- magAndReplace() 에서 사용하는 replace의 경우 화면 이동 후 이전 히스토리를 삭제하기에 백스페이스 등으로 이전 화면 진입 시도시 실행을 막을 수 있음
  - 중복으로 처리되는 오류를 사전에 막을 수 있음
  
- 로그인 후 원래 가려던 페이지로 리다이렉팅하는데 필요한 기술 : URL Encoder
  - url에 담긴 쿼리에 &가 포함되면 컴퓨터가 이를 구분하여 인식할 수 없기에 인코딩된 부분은 주소로 인식할 수 있게끔 해줌
  
- 함수를 잘 활용하면 똑같은 기능을 구현하더라도 전체적으로 간결한 코드로 구현이 가능
  - 두 번 이상 반복이 되는 경우라면 메서드(함수)로 만들어서 활용해보는 연습을 하면 실력 향상에 도움이 될 것으로 예상
  - 현재 프로젝트에 사용되는 Util 패키지의 util들이 만들어지는 과정이 1월 교육과정 강의에서 확인할 수 있음
  - java 기본 수업의 내용에서 직접 구현하던 경험을 바탕으로 자주 사용하거나 너무 길어 가독성이 떨어지는 메서드는 util의 형태로 가공하는 연습 필요

- jsp가 html의 역할을 하며 동적인 부분을 구현할 수 있게 spring 프레임워크의 도움을 받으며, web에 보여지는 부분을 담당하는 css는 일반적인 웹 개발시와 같은 폴더 구성에 직접 css 코드를 작성하여 디자인할 수도 있지만 jsp 태그에 직접 적용해서 손쉽게 구현할 수 있는 css 프레임워크를 활용하면 전체적인 개발의 속도를 높일 수 있음
  - 동적인 웹 구현과 백앤드 구현 : java와 관련 프레임워크
  - 프론트앤드 단의 작업 : 프론트앤드 프레임워크 활용(테일윈드 등)
  
   

#### POST MAN 사용법
  - GET : 파라미터에 쿼리가 담김
  - POST : 바디에 쿼리가 담김
  - postman 에서 post인 쿼리는 수정이 필요 : 바디에 쿼리가 담길 수 있게 변경

#### 초기 STS 설정시 유의 사항
- 깃허브에서 클론한 프로젝트를 임포트 하기 전에 pom.xml 의 자바 버전 정보를 확인하고, 설치된 sts에서 사용하는 자바환경과 일치하도록 수정 후 import 시킴

#### [테일윈드](https://tailwindcss.com/docs) 
- html 태그 입력으로 간단하게 css작업을 할 수 있음
- 생각보다 훨씬 쉬운 적용이 가능하고, 치트시트를 활용하거나 공식문서를 활용하면 UI를 꾸미는데 있어 시간 절약을 상당히 많이 할 수 있을 것으로 보임

#### css flex
- div를 세로로 정렬할 때 있어 flex-coloum을 사용하기 보다 flex-item안에 세로로 정렬할 div들을 넣어서 처리하는 것이 더 좋음
- 반응형을 구현할 때 세로로 정렬된 div들은 inline-blcok 속성을 토글해서 가로로도 정렬이 가능
- flex의 자식은 항상 부모의 높이를 물려받음
- 


<질문사항>
- 현업에서 현재 교육중에 사용한 코드를 재활용 참고해서 프로젝트를 진행해도 되는지, 필요한 함수를 구글링해서 사용되도 실력을 어떻게 평가 받는지...

- Type safety: Unchecked cast from Object to T
