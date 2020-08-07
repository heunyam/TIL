# AWS S3 (Simple Store Service)



## AWS S3 생성 및 설정

1. 버킷 생성

2. S3 버킷 권한 설정 페이지에서 밑에 2개를 체크 해제 -> S3를 CDN으로 사용하고자 함

3. 생성 했으면 권한탭으로 이동

4. 버킷 정책 설정

   ```json
   {
       "Version": "2012-10-17",
       "Id": "Policy354648",
       "Statement": [
           {
               "Sid": "Stmt354648",
               "Effect": "Allow",
               "Principal": "*",
               "Action": "s3:GetObject",
               "Resource": "arn:aws:s3:::carat-gram/*"
           }
       ]
   }
   ```

5. CORS 구성 설정

   ```xml
   <CORSConfiguration>
       <CORSRule>
           <AllowedOrigin>*</AllowedOrigin>
           <AllowedMethod>GET</AllowedMethod>
           <MaxAgeSeconds>3000</MaxAgeSeconds>
       </CORSRule>
   </CORSConfiguration>
   ```



## AWS IAM 사용자 생성

1. IAM 검색
2. 사용자 추가 탭에서 사용자 추가
3. 이름 마음대로 정하고 **프로그래밍 방식 액세스** 선택
4. 다음, 권한은 **기존 정책 직접 연결**에 **AmazonS3FullAccess** 선택 (보안적으로 설정하기 위해서는 특정 버킷에 대한 권한만 주는게 좋음)
5. 태그 추가 X
6. 사용자 만들기
7. .csv 다운로드 -> (Secret access key, Access key ID)