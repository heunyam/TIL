# AWS에 배포하기

- AWS
- AWS EC2
- AWS RDS
- AWS ALB
- deploy



## AWS RDS

AWS에서 제공하는 데이터베이스 서비스 

### RDS 설정 후 데이터베이스 만들기

1. rds 서비스 검색

2. AWS 지역 Seoul로 설정

3. MySQL 설정 파일 생성

   1. 인코딩을 'UTF-8'로 설정하기 위해 파라미터 그룹으로 이동

   2. 파라미터 그룹 생성 클릭
   3. mysql버전(mysql5.7), 이름 설정
   4. 방금 생성한 파라미터 선택 후 편집
   5. character_set_ 값들을 모두 utf8mb4로 설정(character_set_filesystem 제외)
   6. collation_conntion 값을 utf8mb4_general_ci 로, 
   7. collation_server 값을 utf8mb4_unicode_ci 로 변경

4. 이제 옆 dashboard에서 데이터베이스 생성 누르기

5. mysql 선택, 프리티어 템플릿 선택, DB이름, 마스터 사용자 이름, 마스터 암호는 설정 필수 

6. "연결"의 "퍼블릭 엑세스 가능" 옵션을 "예"로 설정 -> 인터넷을 통해 DB서버에 접속가능, 실제 서비스는 "아니요"로 해주는게 좋음, 정해진 서버나 관계자만 접속 가능하게 해서 보안적으로 안전

7. 추가 구성에서 DB 파라미터 그룹을 앞서 만든 파라미터로 설정

8. 끝, 생성 누르기

### AWS RDS 인스턴스 

1. 데이터베이스 생성 완료 후 데이터베이스의 엔드포인트 주소 확인

   python-backend.cqx4sjwzw0mp.ap-northeast-2.rds.amazonaws.com

2. 보안 그룹에서 인바인드 규칙을 모든 TCP(3306), 위치무관 로 수정 -> 어디서든 접근 가능

### AWS EC2

1. 운영체제 선택

2. t2_micro 선택, 다음 선택

3. 인스턴스 개수(2) 정해주고 퍼블릭 IP 자동 할당 활성화로 설정

4. 완료하면, key pair 생성하라고 함, 적당히 생성후 .pem 파일은 잘 보관

5. 인스턴스 생성 했으면 Public DNS와 Public IP 주소 확인

   ```
   ec2-13-124-49-155.ap-northeast-2.compute.amazonaws.com
   13.124.49.155
   ec2-54-180-9-90.ap-northeast-2.compute.amazonaws.com
   54.180.9.90
   ```

6. ubuntu 

   ```
   bash -i <pemkey 경로> ubuntu@<ec2 instance public ip 주소>
   ```

   

