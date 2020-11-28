# 크롤링 기초
## <u>크롤링(crawling)이란?</u>

무수히 많은 컴퓨터에 분산 저장되어 있는 문서를 수집하여 검색 대상의 색인으로 포함시키는 기술. 
- 어느 부류의 기술을 얼마나 빨리 검색 대상에 포함시키냐 하는 것이 우위를 결정하는 요소로서 최근 웹 검색의 중요성에 따라 발전되고 있다.
<br>[네이버 지식백과] 크롤링 [crawling] (IT용어사전, 한국정보통신기술협회)


**Beautifulsoup**: HTML과 XML 문서를 파씽하기 위한 파이썬 패키지.
<br>**bs4** : <u>Beautifulsoup</u>를 사용하기 위하여 bs4 모듈을 설치.

**requests** : 크롤링을 하기 위해 웹 사이트에 http 요청을 하기 위해 사용되는 모듈.

```python
import requests
from bs4 import BeautifulSoup
```
**requests.get("http-")**
"http-"의 웹페이지를 BeautifulSoup 객체로 반환

여기서 BeautifulSoup: <u>객체는 웹 문서를 파싱한 상태.</u>
 

(parsing:
문자열로 구성된 문서를 토큰으로 분해하고 토큰으로 구성된 파스 트리를 만드는 것)
```python
htmls = requests.get('https://namu.wiki/w/%EC%9E%94%EB%82%98%EB%B9%84').text
bs = BeautifulSoup(htmls, 'html.parser')

print(bs)#해당 웹페이지의 모든 문자열을 가져온다.
```
- 제목 가져오기
```python
print(bs.head.title)

ㄴ> <title>잔나비 - 나무위키</title>
#이렇게 제목을 가져 올 수 있다.
```
- 원하는 부분 추출하기
```python
Search_data = bs.find('a',class_='wiki-fn-content')
#html 태그와 class를 이용하여 데이터 추출하기 
print(Search_data)
print(Search_data.string)
print(Search_data.get_text()
