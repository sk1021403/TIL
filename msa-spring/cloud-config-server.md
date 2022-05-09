### 1. Spring Cloud Config란?
분산 환경에서 설정 정보를 외부에 보관할 수 있도록 지원해주는 서비스   
설정을 위한 별도의 서버를 구성 -> 설정이 바뀔 때마다 배포가 필요 없음    

client가 server에게 설정값을 요청하면 server는 저장소에 접근해 최신 설정값을 client에게 전달해줌   

* 구성 요소   
  - 설정 파일이 저장되는 Config 저장소 (git repository)   
  - 저장소와 연결되어 이를 관리해주는 Spring Cloud Config Server   
  - Spring Cloud Config를 이용하는 Client들   
  
  
### 2. Spring Cloud Config Server

* dependency 추가
```
dependencies {
	implementation 'org.springframework.cloud:spring-cloud-config-server'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```
* @EnalbeConfigServer 선언
```
@EnableConfigServer
@SpringBootApplication
public class ConfigApplication {

	public static void main(String[] args) {
		SpringApplication.run(ConfigApplication.class, args);
	}
}
```
* 설정 정보 입력 (application.yml)
```
server:
  port: 8888

spring:
  cloud:
    config:
      server:
        git:
          uri: {Config 저장소 연동}
```

