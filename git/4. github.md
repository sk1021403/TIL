### remote 저장소 연결   
- git remote add origin 주소  
-> git ls-remote로 연결 확인  
- git push origin master (업로드+머지)  

### remote 저장소 삭제  
- git remote rm origin

### 저장소에서 내려받기  
- git pull origin master (다운로드+머지)  

### git clone  
- init, remote, pull 한번에, master 브랜치 받아옴  
- git clone 주소  

### 브랜치 만들고 내려받기  
1. git checkout -b topic  
   git fetch origin  
   git merge origin/topic
    
2. git checkout -b topic (topic 브랜치 생성)  
   git pull origin topic (topic 브랜치 다운로드 및 머지)  
    
3. git fetch origin (모든 브랜치를 remote branch로 다운로드 = remote 브랜치 동기화)  
   git checkout -b topic origin/topic (브랜치 생성 및 머지)    
   
### Git merge --squash topic
- 토픽 브랜치의 여러개의 커밋을 하나의 커밋으로 합친 후 merge  

### 팁 
- 처음엔 git clone으로 master 브랜치 가져오기  
- git checkout -b dev origin/dev로 다른 브랜치도 가져왓  
