### 1. API gateway란?  
- 서버 최앞단에서 모든 API 호출을 받고 인증 한 후, 적절한 서비스에게 메시지를 전달
- 메시지의 내용에 따라 어플리케이션 내부의 마이크로서비스로 라우팅
- 모든 클라이언트 요청에 대한 엔드 포인트를 단일화  

=> 즉 클라이언트는 각각의 마이크로서비스들과 통신하지 않고, API gateway와 통신!  

#### 필요한 이유
- 각각의 서비스마다 공통된 로직을 구현해야해서 번거로움
- 수많은 API 호출을 기록, 관리하기 어려움
- 내부의 비즈니스 로직이 드러나 보안에 취약함  

#### 주요 기능 
- 인증 및 인가
- 요청 절차의 단순화
- 라우팅 및 로드밸런싱
- 서비스 오케스트레이션
- 서비스 디스커버리  

#### 고려사항
- 병목 현상 (적절한 scale-out 필요)
- 네트워크 Latency

### 2. Spring Cloud Gateway
- build.gradle (의존성 추가)
```
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-actuator'
    implementation 'org.springframework.cloud:spring-cloud-starter-circuitbreaker-resilience4j'
    implementation 'org.springframework.cloud:spring-cloud-starter-gateway'
    implementation 'org.springframework.cloud:spring-cloud-starter-netflix-eureka-client'
    compileOnly 'org.projectlombok:lombok'
    annotationProcessor 'org.projectlombok:lombok'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```

- application.yml
```
server:
  port: 8080
spring:
  application:
    name: apigateway-service
  cloud:
    gateway:
      httpclient:
        connect-timeout: 2000
        response-timeout: 2s
      routes:
        - id: auth-service
          uri: lb://AUTH-SERVICE
          predicates:
            - Path=/auth-service/**

eureka:
  client:
    register-with-eureka: true
    fetch-registry: true
    service-url:
      defaultZone: http://localhost:8761/eureka
  instance:
    instance-id: ${spring.application.name}:${spring.application.instance_id:${random.value}}

```

여기까지 하면 eureka server에 api gateway가 instance로 등록되는 것을 확인할 수 있음  
