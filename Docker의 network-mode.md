# Docker의 network_mode 옵션에 대해서

1. bridge
2. host
3. container
4. none

## 1. bridge

- 같은 네트워크 대역만 통신 가능???? 아직 모름
- 포트 포워딩 필요 O

## 2. host

- 호스트의 네트워크 환경을 그대로 사용함
- 포트 포워딩 필요 O

## 3. container

- 다른 컨테이너의 네트워크 환경 공유



## 4. none

- 네트워크 사용 안함 
- 컨테이너는 외부와 단절됨

