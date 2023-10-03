#  GDSC 백엔드 스터디 3주차
### Spring Bean
스프링 IoC 컨테이너가 관리하는 자바 객체. 기존의 프로그래밍에서는 클래스를 생성하고 new를 입력하여 원하는 객체를 직접 생성한 후에 사용했었지만, 스프링에서는 스프링에 의하여 관리당하는 자바 객체를 사용한다.
### IoC 컨테이너  
> IoC : **제어의 역전** . 프로그램의 일부 또는 객체에 대한 제어를 외부로 이전하는 소프트웨어 엔지니어링 원칙.   

빈을 관리하는 객체로, ApplicationContext라는 인터페이스가 IoC 컨테이너를 대표한다. 이는 여러 인터페이스를 상속받아(BeanFactory) 만들어지고, 빈 조회, 이벤트 발행, 환경변수 조회 등 다양한 기능을 구현할 수 있다.   
![img1](https://velog.velcdn.com/images/rg970604/post/37074976-7406-42a2-a1cd-72b1fb355e49/image.png)
<br>

### Spring Bean 등록 방법(Component Scan)
클래스 선언부 위에 @Component 어노테이션을 사용한다. 스프링은 이 어노테이션이 붙은 클래스를 자동으로 검색하고 빈으로 등록한다.   
@Controller, @RestController, @Service, @Repository, @Configuration 등의 어노테이션이 @Component 어노테이션을 포함하고 있다.   
<br>
@Component 를 붙인 클래스를 스프링이 찾도록 하기 위해서 @ComponentScan 어노테이션을 사용한다. 스프링이 어느패키지에서 클래스 검색을 시작할지 및 검색할 패키지의 범위를 설정할 수 있다. @ComponentScan 이 붙은 설정 정보 클래스의 패키지가 시작 위치가 된다.
