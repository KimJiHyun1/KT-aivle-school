# 웹크롤링


## 교육 일자
2022년 8월 3일 ~ 5일<br/><br/>


## 목차  

### day 1  
  * 네이버 주식, 환율 크롤링 (requests json)
  * 네이버 papago API (requests api) 
  * 다음 환율 크롤링
  
### day 2 
  * 네이버 API (네이버 검색어 트렌드 수집)  
  * 직방 원룸 매물 정보 수집 (geohash2)
  * html, css-selector ////////// 나중에 text로 정리...
  * 네이버 연관 검색어 (BeautifulSoup)
  * 지마켓 best 상품 200개 수집  
  
### day 3 
  * 지마켓 best 상품 200개 수집 + 이미지
  * 중고나라 게시글 데이터 수집 (crawling using selenium)
  * xpath
  * iterator, generator
  * scrapy (파이썬 웹크롤링 framework)<br/><br/><br/>
  
  
## 요약  
  * 동적 페이지 : URL 변경 없이 웹페이지 데이터 변경 : JSON : API
  * 정적 페이지 : URL 변경 해서 웹페이지 데이터 변경 : HTML : BeautifulSoup<br/><br/>
    
  * 동적 페이지 데이터 수집 프로세스
    1. 웹페이지 분석 (개발자 도구) : URL 찾기 
    2. request(url, prams, headers) > response(json) => JSON(str)
    3. JSON(str) > list, dict > DataFrame<br/><br/>
     
  * API를 이용한 데이터 수집
    1. APP 등록 : application key 가져오기
    2. api 문서 (document) : url, params, headers
    3. request(url, prams, headers > response(json) => JSON(str)
    4. JSON(str) > preprocessing : list, dict > DataFrame<br/><br/>
      
  * 정적 페이지 데이터 수집 프로세스 
    1. 웹서비스 분석 : URL
    2. request(url) > response(html) => HTML(str)
    3. HTML(str) > BeautifulSoup Object > css-selector > Data<br/><br/>
  
  
  * **HTML** : 웹페이지의 레이아웃, 텍스트 등의 데이터를 작성하는 언어
    * 구성요소 : document, element, tag, attr, text
    * tag의 종류 : p, span, ul, li, table, a, img, iframe, div<br/><br/>
  
    * **css selector** : html의 element에 스타일을 적용시킬 때, element를 선택하는 방법
      * element : tag 이름 (span), class (.class name), id (#id), attr ([value='_'])<br/><br/>
  
      * n번째 element를 선택하는 방법 : .py:nth-child(n) : nth-child(n) > .py : n번째 element 중 class가 py인 element 선택
      * 모든 하위 element (공백) : .wrap p = wrap class 안에 있는 p tag를 갖는 모든 element
      * 한단계 하위 element (>) : .wrap > p = wrap class 안에 있는 바로 아래 있는 p tag
      * 여러 개 (,) : .no1, .no2<br/><br/>


    * **xpath** : css selector와 같은 역할, scrapy의 기본 selector<br/>
      `//*[@id="nx_footer_related_keywords"]/div/div[2]/ul/li[1]/a/div`
      - // : 최상위 element
      - \* : 모든 하위 element : = .wrap p
      - [@id="nx_footer_related_keywords"] : 속성값으로 element 선택
      - / : 한단계 하위 element = .wrap > p
      - [n] : n번째 element
