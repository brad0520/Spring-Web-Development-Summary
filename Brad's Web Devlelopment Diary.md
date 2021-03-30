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
