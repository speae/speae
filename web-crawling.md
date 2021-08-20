### 🤔

web-crawling
=====================================================================================================================================

직장인을 위한 데이터분석 실무 [07. 어떤 무선청소기가 인기가 좋을까?]에 대한 생각① 
-------------------------------------------------------------------------------------

  '직장인을 위한 데이터분석 실무'는 분명 나같은 웹 크롤링에 입문하는 사람들에게 좋은 책인건 확실하다. 단 하나, 아쉬운 점은 거슬리는 오타와 설명이 필요한 부분들은 생략됐다는 점이다.
 
 이를테면, 
 
```python
  
from selenium import webdriver
browser = webdriver.Chrome('C:/playwithdata/chromedriver.exe')
url = "http://search.danawa.com/dsearch.php?query=무선청소기&tab=main"  
driver.get(url)

```

위 코드처럼 browser와 driver 각기 다른 변수명을 사용하여 독자들에 혼란을 주고 있다는 것이다. 위의 예시를 단순 오타로 봐야 할지 다른 생각이 있어서 다른 객체를 사용했는데 그에 대한 설명이 부족했다고 봐야 할지 판단할 수 없었지만, 필자는 아무리 생각해봐도 굳이 다른 객체를 쓸 이유가 없다고 판단하고 오타의 예시로 들었다.

 설명이 부족한 부분은 무엇일까...
 
```python
 
!pip3 install openpyxl
  
```
 
 to_excel(), read_excel()과 같은 엑셀관련 메소드들은 pandas 패키지뿐 아니라 의존성 패키지인 openpyxl 패키지를 요구한다. 즉 이 메소드들을 사용하려면 openpyxl를 별도로 설치해주어야 한다는 것이다. 
 
  그런데 이 책에서는 pandas의 to_excel(), read_excel() 함수를 통해 엑셀 파일로 저장하고 읽는다고 설명하고 있다. openpyxl 패키지 설치에 대한 설명이 없는 탓에 중간 과정없이 정보를 전달한 것이다. 우리는 openpyxl 패키지를 추가로 설치함으로써, pandas 자체나 pandas의 데이터프레임을 가지고 openpyxl 내부의 클래스를 통해 엑셀 파일을 만들어 저장하거나 읽는다는 것을 추측할 수 있다.  
 
 그리고 데이터 분포 그래프 설명 부분에서 mean()메소드를 사용하여 평균값을 가져와 기준선으로 그린다고 했는데, 코드 설명에는 최소값 정리, 최소값이라고만 나와서 혼란이 생길 수 있다. 엄연히 최소값은 따로 있고 어디까지나 평균을 기준으로 삼겠다는 것을 바로 '최소값 구하기'라고 하면 의아하다는 생각이 들 수 있다. 
 
 x축 기준선의 y절편에 똑같은 값을 넣고 반대편도 똑같이 해서 증가량 = 0 = 기울기 -> 기준선으로 만들었다는 설명까진 굳이 안 넣어도 되지만, 바로 평균값을 구하는 코드에 최소값 구하기라고 하면 너무 설명을 축소하고 잘못된 정보를 전달하는 것처럼 느껴진다.  

직장인을 위한 데이터분석 실무 [07. 어떤 무선청소기가 인기가 좋을까?]에 대한 생각②
-------------------------------------------------------------------------------------

  코드 실행 부분을 보면 아쉬운 점이 있다. 반복문으로 검색 결과의 1페이지에 대한 상품 정보를 추출 시 각 셀 별 데이터마다 예외처리를 했다는 점이다. 
  
```python

def get_prod_items(prod_items): 
  prod_data = []
  
  for prod_item in prod_items: 
    # ① 상품명 가져오기 
    try: 
      title = prod_item.select('p.prod_name > a')[0].text.strip() 
    except: 
      title = ''
    # ② 스펙 목록 가져오기 
    try: 
      spec_list = prod_item.select('div.spec_list')[0] text.strip() 
    except: 
      spec_list = '' 
    # ③ 가격 정보 가져오기 
    try: 
      price = prod_item.select('li.rank_one > p.price_sect > a > strong')[0].text.strip().replace(",", "") 
    except: 
      price = 0 
    
    prod_data.append([title , spec_list, price]) 

return prod_data
```
 
 평상시 try문을 실행하다가 에러 발생 시 except문을 실행하는 것이 try~except문의 특징인데, 여기선 if~elif문처럼 작성돼있다. 결국 title이든 spec_list이든 price이든 한 곳에서 에러 발생시 일괄적으로 처리하는 것이 맞는 방법이 아닐까 생각한다. 
 
 title에서 에러 발생시 title을 Nonetype('')으로 처리하여 실제 엑셀 파일에서 볼 때 빈 셀로 출력하도록 한다면 당연히 나머지 셀들에 무슨 값이 들어오건 절대 저장되선 안되는 값이다. 그런 의미에서 나머지 셀 들에 들어갈 데이터들도 모두 None으로 처리하는 것이 바람직하다고 본다.

```python3

# 상품 정보 태그에서 원하는 정보를 추출하는 함수
def get_prod_items(prod_items):
    prod_data = []
    none_data = []
    
    for prod_item in prod_items:
        try: 
            # 상품명 가져오기
            title = prod_item.select('p.prod_name > a')[0].text.strip()
            # 스펙 목록 가져오기
            spec_list = prod_item.select('div.spec_list')[0].text.strip()
            # 가격 정보 가져오기
            price = prod_item.select('li.rank_one > p.price_sect > a > strong')[0].text.strip().replace(",", "")
        
        # prod_name에서 상품명, 스펙 목록, 가격 정보 없이 빈 박스 상태만 있는 경우 존재 -> 쓰레기 데이터 버리기
        except Exception as ex:
            print(ex)
            title = None
            spec_list = None
            price = None
            none_data.append([title, spec_list, price])
            
        # Nonetype error 방지와 '/'이 있는 데이터만 저장
        if spec_list is not None and '/' in spec_list:   
            if not price.isdigit():
                price = 0
            prod_data.append([title, spec_list, int(price)])
            
    return prod_data
    
 ```
  none_data라는 배열을 만들어서 그 안에 None 데이터들을 모아 넣을 것이다. 이렇게 되면 함수 내에서만 none_data에 None type의 데이터들만이 들어가는걸 반복하고 어느 곳에서도 쓰이지 않고 끝날 것이다. 

![prod_item_1](https://user-images.githubusercontent.com/43712685/130160921-5961a5ab-a664-4ff8-99e6-dd66115201d4.png)
<1. prod_item ① : p 태그의 class가 있는 상품1>

![prod_item_2](https://user-images.githubusercontent.com/43712685/130225210-c2b51eef-8594-44b7-9770-29d53e509f54.png)
<2. prod_item ② : p 태그의 class가 있는 상품2>

![spec_list](https://user-images.githubusercontent.com/43712685/130225288-7047895b-8ba8-4502-a323-bd19677aaba2.png)
<3. spec_list : div 태그의 class가 있는 상품>

![prod_item_None](https://user-images.githubusercontent.com/43712685/130225559-59740ce8-2702-4138-9f04-8903157e1599.png)

<4. prod_item is None : p 태그의 class인 prod_name이 존재하지만, spec_list 등이 없는 쓸모없는 정보>

1 ~ 3번의 상품들은 prod_name, spec_list, 가격 등에 대한 정보들을 갖고 있지만, 4번 이미지와 같이 prod_name 정보만 갖고 나머지 데이터들은 전부 갖고 있지 않은 상태이므로
[list index out of range] 에러를 일으킨다. 이 에러는 해당 요소를 찾을 수 없거나 배열 내에 없는 요소를 찾으려 하는 경우(=어떤 요소의 인덱스가 배열에 할당된 크기를 초과할 때; 배열 내에 없는 요소를 찾는 것과 같음) 발생한다. 

 원문의 코드는 이런 데이터들을 '', '', 0의 값들로 바꾸어 prod_data에 저장하게 된다. 이는 엑셀에 원하지 않는 데이터들을 저장하게 된다는 것이다. 따라서 none_data배열을 일종의 휴지통처럼 만든다면 데이터 전처리와 같은 효과를 낼 수 있다.
 
----------------------------------------------------------------------------------------------------------------

 저자들이 한 사이트 내에서 유의미한 데이터가 무엇인지, 어떤 데이터를 사용해야 데이터 시각화를 통해 해석할 수 있는지에 대한 깊은 고찰이 느껴진다. 나같은 초보도 쉽게 이해할 수 있었다. 그러나 자세하게 설명해야 할 것들이 너무 많이 생략된 것은 아쉬운 부분이다.
