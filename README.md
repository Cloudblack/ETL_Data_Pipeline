
<div align="center">
  <h1> 데이터 엔지니어링 Project </h1>
  AWS를 이용한 실시간 데이터 파이프라인 구성
 
  ### 프로젝트 발표 영상
  [프로젝트 발표 영상](https://drive.google.com/file/d/1I8L_jjILvb9z2wMtBbQnd5s9IasxDG9O/view?usp=sharing)
  
  
  ### 👤 팀원 소개
  |김석재|김예린|노지훈|
  |:---:|:---:|:---:|
  |<img src="https://avatars.githubusercontent.com/u/86823305?v=4" width="100"/> | <img src="https://avatars.githubusercontent.com/u/86868063?v=4" width="100"/> | <img src="https://avatars.githubusercontent.com/u/86717381?v=4" width="100"/> |
  |[Github](https://github.com/Cloudblack)|[Github](https://github.com/yello-ow)|[Github](https://github.com/nojihun)|
  <br>
  
 
  
</div> 

  ### 프로젝트 배경 
   - 기업의 M/L팀에서 로그 분석을 위해 필요한 데이터를 불러오는 API가 필요해, 실시간으로 들어오는 데이터를 처리하고 저장 할 수 있는 ETL DATA PIPELINE을 구축하는 프로젝트이다. 
   - 기업 로그 데이터는 고객의 데이터이기 때문에 유출 할 수 없어 샘플 데이터만으로 진행했으며 가능한 비용을 줄여야 한다.
  <br>
  
  ### 파이프라인 동작 순서
  <img width="600" src="https://user-images.githubusercontent.com/86823305/154409477-f5d3b334-498d-4eb7-86b5-9d6c847fac3b.png">   
  
  ###
  1. 데이터를 실시간으로 AWS kinesis에서 받아 인코딩, 압축을 해 S3에 저장한다
  2. Crawler를 통해 S3에 입력된 data를 읽어 Data Catalog로 만들어지게 된다
  3. ML팀에서 query가 포함된 api (AWS API gateway사용)를 요청한다
  4. 요청받은 api는 AWS Lambda에서 처리됩니다. AWS Athena를 통해 query된 data catalog를 가져오게됩니다. 
  5. 압축을 풀고 디코딩을해 원본과 똑같이 만들어진 결과를 ML팀에서 받을수 있게 된다.
  <br>
  
  ### 프로젝트 내 나의 기여
  - 실제 기업의 실시간 데이터를 사용 할 수 없어 kinesis를 활용해 유사 실시간 환경을 구축
  - S3와 연계 할 수 있는 다른 AWS 서비스를 추가로 사용
  - 데이터를 변환 및 압축하여 S3에 저장
  - AWS lambda에서 s3와 athena를 연결
  - 입력된 SQL 쿼리문을 데이터를 불러와 복원해 제공하는 API 구현  
  <br>
  
  ## 프로젝트 결과
  - 실시간 ETL data pipeline 구축
  - 입력되는 데이터 중 미리 설정된 필요한 데이터만 클라우드(S3)에 저장할 수 있다.
  - 데이터 변환 및 압축을 통해 89.6%의 데이터 용량 감소로 비용을 절약 할 수 있다.
    - Original data 2495kb ⇒ trans data 261kb
  - SQL 쿼리를 이용 해 압축된 데이터를 복원하여 제공하는 API 구현했다.
  <br>
  
  ### 기술 스택
  - python, aws-lambda, aws-s3, aws-apigateway, aws-glue, aws-kinesis
  
  ### 파일
  - pipeline.py : 변환, 압축 등에 사용된 코드 모음 
  - kinesis_producer.py : kinesis를 통해 샘플 데이터를 보내는 역할
  - kinesis_consumer.py : kinesis로 데이터를 받아 S3에 올려주는 역할
  - lambda_test.py : lambda에 들어가는 코드 (pipeline.py 필요)



