### 1. Eureka란?
넷플릭스에서 공개한 Service Registry 서버(인스턴스 상태를 동적으로 관리), REST 기반 미들웨어 서버    

서비스들의 정보를 레지스트리에 등록하고 동적인 탐색, 로드 밸런싱을 제공  
서비스 인스턴스들이 동적으로 변경되어도 인스턴스의 상태를 하나의 서비스로 관리 가능  

Eureka Client, Eureka Server로 구성  

* Eureka Client 서비스가 시작될 때 Eureka Server에 자신의 정보를 등록
*  Eureka Client는 Eureka Server로부터 Registry를 받아 자신의 로컬에 저장  
*  30초마다 Eureak Server로부터 변경 사항을 갱신받음
*  30초마다 ping을 통해 자신이 가용 상태임을 알리는 신호를 보냄   
   -> 신호 안 보내면 Eureka Server가 해당 client를  Registry에서 제외

### 2. Load Balancing
여러 대의 서버에 트래픽을 골고루 분산해주는 기술  
MSA에서는 서비스의 IP, Port가 지속적으로 변화하고 이때마다 정보 새롭게 등록해야함 -> Eureka 등장  

클라이언트 측 로드 밸런서 - Ribbon

