### 네이버 로그인 API 연동 과정  

- application-oauth.yml
```
spring:
  security:
    oauth2:
      client:
        registration:
          naver:
            client-id: 클라이언트 ID
            client-secret: 클라이언트 Secret
            redirect-uri: "{baseUrl}/{action}/oauth2/code/{registrationId}" 
            authorization-grant-type: authorization_code
            scope: name, email, profile_image
            client-name: Naver
        provider:
          naver:
            authorization_uri: https://nid.naver.com/oauth2.0/authorize
            token_uri: https://nid.naver.com/oauth2.0/token
            user-info-uri: https://openapi.naver.com/v1/nid/me
            user_name_attribute: response
```

  

1) 네이버 로그인 연동 url 생성 (https://nid.naver.com/oauth2.0/authorize)
2) 네이버 로그인 연동 결과 callback 정보
3) 접근 토큰 발급 요청
4) 접근 토큰을 이용하여 프로필 api 호출
5) 접근 토큰을 이용하여 사용자 허용 프로필 권한 확인
