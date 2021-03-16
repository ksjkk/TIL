# Spring
### Spring boot, gradle, thymeleaf 기초

controller
-> viewResolver

controller(responsebody)
-> HttpMessageConverter
-> @ResponseBody 가 있으면 http body 부분에 데이터 직접 넘겨줌

## repository
-> 저장소(DB)가 정해지지 않은 상태에서 개발이 시작했다고 가정시
-> repository를 통해서 비즈니스 로직을 먼저 개발할 수 있음
-> 추후 repository 변경을 통해 자바에서 코드 한줄로 저장소를 바꿀수있음
```bash
cd /c/'Program Files (x86)'/H2/bin
./h2.bat
```

@SpringBootTest : 스프링 컨테이너와 테스트를 함께 실행한다.
@Transactional : 테스트 케이스에 이 애노테이션이 있으면, 테스트 시작 전에 트랜잭션을 시작하고, 테스트 완료 후에 항상 롤백한다. 이렇게 하면 DB에 데이터가 남지 않으므로 다음 테스트에 영향을 주지 않는다.

@Test
단위단위로 쪼개서 테스트 하는게 가장 좋음
Spring boot container 까지 올려서 테스트하는 것은 테스트 설계가 잘못됐을 확률이 높다.

JdbcTemplate
-> Design 패턴중 Template 패턴이 많이 들어가있음.

