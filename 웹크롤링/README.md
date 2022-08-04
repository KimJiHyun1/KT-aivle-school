# 웹크롤링


## 교육 일자
2022년 8월 3일 ~ 5일  


## 목차  

### day 1  
  * 네이버 주식, 환율 크롤링 (requests json)
  * 네이버 papago API (requests api) 
  * 다음 환율 크롤링
  
### day 2 
  * 네이버 API (네이버 검색어 트렌드 수집)  
  * 직방 원룸 매물 정보 수집 (geohash2)
  * html, css-selector                  // 나중에 text로 정리...
  * 네이버 연관 검색어 (BeautifulSoup)
  * 지마켓 best 상품 200개 수집  
  
### day 3 
  * 지마켓 best 상품 200개 수집 + 이미지
  * crawling using selenium
  * xpath
  * scrapy (파이썬 웹크롤링 framework)
  
  
## 요약  
  * 동적 페이지 : URL 변경 없이 웹페이지 데이터 변경 : JSON : API
  * 정적 페이지 : URL 변경 해서 웹페이지 데이터 변경 : HTML : BeautifulSoup
    
  * 동적 페이지 데이터 수집 프로세스
    1. 웹페이지 분석 (개발자 도구) : URL 찾기 
    2. request(url, prams, headers) > response(json) => JSON(str)
    3. JSON(str) > list, dict > DataFrame  
     
  * API를 이용한 데이터 수집
    1. APP 등록 : application key 가져오기
    2. api 문서 (document) : url, params, headers
    3. request(url, prams, headers > response(json) => JSON(str)
    4. JSON(str) > preprocessing : list, dict > DataFrame  
      
  * 정적 페이지 데이터 수집 프로세스 
    1. 웹서비스 분석 : URL
    2. request(url) > response(html) => HTML(str)
    3. HTML(str) > BeautifulSoup Object > css-selector > Data
