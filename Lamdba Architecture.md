# Lambda Architecture

## 람다 아키텍쳐?

오래된 데이터를 보관하는 Batch 테이블과  실시간 데이터를 가진 실시간 테이블을 서로 조인하여 결과값을 얻을 수 있도록 구성한 아키텍처이다.

Lambda라는 이름은 모양이 입구가 두개이고 출구가 하나인 모양이 해당 아키텍쳐의 개념과 비슷하다고 하여 붙여졌다.

### Why?

대용량 데이터는 쿼리에 많은 시간이 소요된다.

람다 아키텍쳐는 Speed Layer + Batch Layer의 조합으로 어느정도의 실시간 분석을 지원할 수 있다

![lamdbda](https://images.ctfassets.net/vrkkgjbn4fsk/2HqTWS8VBSyMUKkiEeO02s/82ec09adbce476a0b31dcba6d9f61013/lambda-architecture.png)

### Batch Layer

데이터 조회에 걸리는 시간을 최소화 하기 위해 Batch를 이용하여 데이터를 미리 계산해 놓는 방법이 있다.

> Batch : 특정 시간마다 주기적으로 계산을 수행하는 것 -> 즉, 실시간이 아닌 특정 시간에만 데이터가 업데이트 된 상태이다

### Speed Layer

Batch 레이어를 사용해서 조회 속도 이슈를 해결했다.

하지만 Batch 사이에 있는 데이터를 조회하고 싶을 때 해당 데이터를 조회할 수 없다는 이슈가 있다.

이런 문제를 해결하기 위해서 Batch 간격을 하루로 잡았다면 당일 데이터를 실시간으로 별도의 테이블에 집계한다.

### Serving Layer

Batch 레이어 및 Speed 레이어의 출력을 저장한다.

클라이언트는 해당 레이어에서 데이터를 조회해서 빠른 응답이 가능하다.

