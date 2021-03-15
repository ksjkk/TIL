# DDD
## Domain Driven Design

프로젝트를 페키징 하는 것은 향후 유지보수화 소수 가독성을 위해 잘 고려될 필요가 있다. 각 레이어별 기능을 정의하는데 Package 단위로 정의하게될 가능성이 높기 때문이다.

일반적으로 스프링 프레임워크를 사용해 자바 프로젝트의 프로젝트 패키지를 설계할 때, 도메인 레이어의 핵심 비즈니스 로직을 포함하는 domain, 핵심 서비스 기능을 구현하는 application, domain과 application 패키지의 백업 기능을 구현하는 infrastructure, API 등 핵심 서비스 인터페이스를 구현하는 interfaces 로 구분할 수 있다.


***
+ domain
    + model
    + service
+ infrastructure
    + config
    + service-name-on-domain
+ interfaces (-> 이부분은 경우의 수가 있는듯하다)
    + controller
    + facade
+ application
***

domain 패키지 부터 보면, 크게 저장 데이터를 제어하는 model 패키지와 기능을 제어하는 service 패키지로 나누어 볼 수 있다. model 같은 경우 @Entity 와 같은 hibernate class를 직접 넣어주거나, Domain class를 넣어 domain 기능을 class에 넣어주고 실제 디비 데이터는 infrastructure에서 저장해주는 방법을 쓸 수 있다. service 패키지는 DDD 설계중 서비스 파트 Interface들이 들어갈 수 있다.

infrastructure 패키지에서는 spring의 @Configuration 파일들을 넣어주고, Spring의 Injection 기능을 사용해 domain layer나 application layer에 존재하는 Interface의 실제 구현체들을 넣어주고, 해당 구현체 기능을 구현한다. 이때 패키지명을 각 service나 application의 이름을 활용해 infrastructure에서 구현하는 interface가 어떤 것인지 패키지명으로 확인할 수 있도록 하면 좋다.

interfaces 패키지에는 스프링의 controller와 각동 데이터 제어를 위한 facade를 패키지명으로 사용할 수 있다. controller의 기능인 validation 이나 view mapping, object converting 등을 interfaces 패키지에 넣어주자.

마지막으로 application 패키지의 구조는 각 기능에 맞게 다양한 형태로 설계 가능하다.