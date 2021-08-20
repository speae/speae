### 🤔

web-crawling 1부
=====================================================================================================================================

직장인을 위한 데이터분석 실무 [07. 어떤 무선청소기가 인기가 좋을까?]에 대한 고찰① 
-------------------------------------------------------------------------------------

  '직장인을 위한 데이터분석 실무'는 분명 웹 크롤링에 입문하는 사람들에게 좋은 책임은 확실하다. 단 하나, 아쉬운 점은 거슬리는 오타와 설명이 필요한 부분들은 생략됐다는 점이다.
 이를테면, 
 
 This is a normal paragraph:
  from selenium import webdriver
  browser = webdriver.Chrome('C:/playwithdata/chromedriver.exe')
  url = "http://search.danawa.com/dsearch.php?query=무선청소기&tab=main"  
  driver.get(url)
end code block.

위 코드처럼 browser와 driver 각기 다른 변수명을 사용하여 독자들에 혼란을 주고 있다는 것이다. 위의 예시를 단순 오타로 봐야 할지 다른 생각이 있어서 다른 객체를 사용했는데 그에 대한 설명이 부족했다고 봐야 할지 판단할 수 없었지만, 필자는 아무리 생각해봐도 굳이 다른 객체를 쓸 이유가 없다고 판단하고 오타의 예시로 들었다.

 설명이 부족한 부분은 무엇일까..
to_excel(), read_excel()과 같은 엑셀관련 메소드들은 pandas 패키지뿐 아니라 의존성 패키지인 openpyxl 패키지를 요구한다. 즉 이 메소드들을 사용하려면 openpyxl를 별도로 설치해주어야 한다는 것이다. 그런데 이 책에서는 pandas의 to_excel(), read_excel() 함수를 통해 엑셀 파일로 저장하고 읽는다고 설명하고 있다. openpyxl 패키지 설치에 대한 설명이 없는 탓에 중간 과정없이 정보를 전달한 것이다. 우리는 openpyxl 패키지를 추가로 설치함으로써, pandas 자체나 pandas의 데이터프레임을 가지고 openpyxl 내부의 클래스를 통해 엑셀 파일을 만들어 저장하거나 읽는다는 것을 추측할 수 있다.  

![prod_item_1](https://user-images.githubusercontent.com/43712685/130160921-5961a5ab-a664-4ff8-99e6-dd66115201d4.png)

