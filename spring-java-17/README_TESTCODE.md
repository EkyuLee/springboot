# 테스트 코드

## 01. 테스트 코드 분류 (참조 : https://tech.inflab.com/20230404-test-code/)
> 3가지 (e2e, integration, unit) 

> > 1. e2e (End to end) 
> > > - 최종 사용자의 흐름에 대한 테스트 이며, 외부로부터의 요청부터 응답까지 기능이 잘 동작하는지 ? 

> > 2. integration (integration test)
> > > - 코드의 주요 흐름들을 통합적으로 테스트 하며, 주요 외부 의존성(ex: database) 에 대해서 테스트 한다.

> > 3. unit (unit tests)
> > > - 도메인 모델과 비즈니스 로직 테스트, 작은 단위의 코드 및 알고리즘 테스트
 
## 02. 테스트가 필요한 이유.
> 회귀 이슈에 대한 처리
> > 프로그램을 수정하면, 예상치 못했던 곳에서 추가적인 이슈가 발생하는 경우가 있다. 그런경우를 회귀 버그라고 한다. 따라서 이런 이슈를 방지하기 위해서라도 테스트코드는 반드시 필요하다.
> 가독성 향상
> 안정감 (불안감 해소)

## 03. 테스트 코드의 패턴 
> GWT패턴 (given-when-then) - 행위 주석 구분
> > 1. given : 테스트 실행을 준비
> > 2. when : 테스트 진행
> > 3. then : 테스트 결과를 검증

> AAA 패턴 (Arrange-Act-Assert) - 주석 구분
> > 1. Arrange : 테스팅 환경과 값을 정의함
> > 2. Act : 테스트 되어야할 코드를 실행함
> > 3. Assert : 실행 결과값을 평가함 / 예상되어야 하는 결과 혹은 값에 부합하는지 비교
 
## 04. spring boot starter test 목록
1. JUnit : 자바 프로그래밍 언어용 단위 테스트 프레임워크 이다.
> > [JUnit 특징]
> > > 1. 테스트 방식을 구분할 수 있는 annotation 제공
> > > 2. @Test 어노테이션으로 매서드를 호출할때마다 새 인스턴스를 생성, 독립 테스트 가능
> > > 3. 예상 결과를 검증하는 어설션 메서드 제공
> > > 4. 사용 방법이 단순, 테스트 코드 작성 시간이 적음
> > > 5. 자동실행, 자체 결과를 확인하고 즉각적인 피드백을 제공한다. 
2. Spring Test & Spring Boot Test : 스프링 부트 어플리케이션을 위한 통합 테스트 지원
3. AssertJ : 검증문인 어설션을 작성하는 데 사용되는 라이브러리
4. Hamcrest : 표현식을 이해하기 쉽게 만드는 데 사용되는 Matcher 라이브러리
5. Mockito : 테스트에 사용할 가짜 객체인 목을 쉽게 만들고 관리하고 검증할 수 있는 테스트 프레임 워크
6. JSONassert : JSON용 어설션 라이브러리
7. JsonPath : JSON 데이터에서 특정 데이터를 선택하고 검색하기 위한 라이브러리

## 05. TestAnnotation에 대한 설명
> 1. @SpringBootTest
> > - @SpringBootApplication 을 찾고, 그 클래스에 포함되어 있는 Bean을 찾은다음 테스트용 application context를 생성한다. 
> 2. @AutoConfigureMockMvc
> > - MockMvc를 생성하고 자동으로 구성한다. 어플리케이션을 서버에 배포하지 않고도 테스트용 MVC를 만들어 요청, 전송, 응답 기능을 제공하는 유틸리티 클래스 이다.
> > - 컨트롤러를 테스트 할때 사용하는 클래스 이다.
> 3. @BeforeEach, @AfterEach
> > - @BeforeEach : 각 테스트가 실행 전에 실행 됨
> > - @AfterEach : 각 테스트가 종료 되고 실행 됨


## 06. Test시 lombok dependencies 추가하기
> 1. compileOnly 'org.projectlombok:lombok' 
> 2. anotationProcessor 'org.projectlombok:lombok' 
> 3. tetCompileOnly 'org.projectlombok:lombok' 
> 4. tesAnnotationProcessor 'org.projectlombok:lombok'


## @AutoWired
1. 필요한 의존객체 의 타입에 해당하는 Bean을 찾아서 주입한다. 