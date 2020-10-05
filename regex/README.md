# 손에 잡히는 정규 표현식: Regular Expressions in 10 minutes

## 문자 하나 찾기

### 문자 그대로 찾기

```
(TEXT)
Hello, my name is Ben. Please visit
my website at http://www.forta.com/
```
```
(SEARCH)
Ben
```
```
(RESULT)
                  Ben              
                                   
```
---

```
(TEXT)
Hello, my name is Ben. Please visit
my website at http://www.forta.com/
```
```
(SEARCH)
my
```
```
(RESULT)
       my                          
my                                 
```

### 모든 문자 찾기

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
na1.xls
na2.xls
sa1.xls
```
```
(SEARCH)
sales.
```
```
(RESULT)
sales1    
          
sales2    
sales3    
         
           
       
       
       
```
---

```
(TEXT)
sales.xls
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
na1.xls
na2.xls
sa1.xls
```
```
(SEARCH)
sales.
```
```
(RESULT)
sales.   
sales1    
          
sales2    
sales3    
         
           
       
       
       
```
---

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
na1.xls
na2.xls
sa1.xls
```
```
(SEARCH)
.a.
```
```
(RESULT)
sal       
          
sal       
sal       
 pac     
           
na1    
na2    
sa1    
```
---

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
na1.xls
na2.xls
sa1.xls
```
```
(SEARCH)
.a..
```
```
(RESULT)
sale      
          
sale      
sale      
 pac1    
           
na1.   
na2.   
sa1.   
```

### 특수 문자 찾기

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
na1.xls
na2.xls
sa1.xls
```
```
(SEARCH)
.a.\.xls
```
```
(RESULT)
          
          
          
          
         
           
na1.xls
na2.xls
sa1.xls
```

## 문자 집합으로 찾기

### 여러 문자 중 하나와 일치시키기

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
na1.xls
na2.xls
sa1.xls
ca1.xls
```
```
(SEARCH)
[ns]a.\.xls
```
```
(RESULT)
          
          
          
          
         
           
na1.xls
na2.xls
sa1.xls
       
```
---

```
(TEXT)
The phrase "regular expression" is often
abbreviated as RegEx or regex.
```
```
(SEARCH)
[Rr]eg[Ee]x
```
```
(RESULT)
                                        
               RegEx    regex 
```

### 문자 집합 범위 사용하기

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
sam.xls
na1.xls
na2.xls
sa1.xls
ca1.xls
```
```
(SEARCH)
[ns]a[0123456789]\.xls
```
```
(RESULT)
          
          
          
          
         
           
       
na1.xls
na2.xls
sa1.xls
       
```
---

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
sam.xls
na1.xls
na2.xls
sa1.xls
ca1.xls
```
```
(SEARCH)
[ns]a[0-9]\.xls
```
```
(RESULT)
          
          
          
          
         
           
       
na1.xls
na2.xls
sa1.xls
       
```
---

```
(TEXT)
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
      MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
      LEFTMARGIN="0">
```
```
(SEARCH)
#[0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f]
```
```
(RESULT)
               #336633        #FFFFFF 
                                                    
                     
```

### 제외하고 찾기

```
(TEXT)
sales1.xls
order3.xls
sales2.xls
sales3.xls
apac1.xls
europe2.xls
sam.xls
na1.xls
na2.xls
sa1.xls
ca1.xls
```
```
(SEARCH)
[ns]a[^0-9]\.xls
```
```
(RESULT)
          
          
          
          
         
           
sam.xls
       
       
       
       
```

## 메타 문자 사용하기

### 이스케이프 다시 살펴보기

```
(TEXT)
var myArray = new Array();
...
if (myArray[0] == 0) {
}
...
```
```
(SEARCH)
myArray[0]
```
```
(RESULT)
                          
   
                      
 
   
```
---

```
(TEXT)
var myArray = new Array();
...
if (myArray[0] == 0) {
}
...
```
```
(SEARCH)
myArray\[0\]
```
```
(RESULT)
                          
   
    myArray[0]        
 
   
```
---

```
(TEXT)
\home\ben\sales\
```
```
(SEARCH)
\\
```
```
(RESULT)
\    \   \     \
```

### 공백 문자 찾기

| 메타 문자 | 설명 |
|-------|--------|
| `[\b]` | 역스페이스 |
| `\f`   | 페이지 넘김 (form feed) |
| `\n`   | 줄바꿈 |
| `\r`   | 캐리지 리턴 |
| `\t`   | 탭 |
| `\v`   | 수직 탭 |
---

```
(TEXT)
"101", "Ben", "Forta"
"102", "Jim", "James"

"103", "Roberta", "Robertson"
"104", "Bob", "Bobson"
```
```
(SEARCH)
\r\n\r\n
```
```
(RESULT)
                     
                     

                             
                      
```

### 특정한 문자 형태와 일치시키기


| 메타 문자 | 설명 |
|-------|--------|
| `\d` | 숫자 하나 ([0-9]와 같다) |
| `\D` | 숫자를 제외한 문자 하나 ([^0-9]와 같다) |
---

```
(TEXT)
var myArray = new Array();
...
if (myArray[0] == 0) {
}
...
```
```
(SEARCH)
myArray\[\d\]
```
```
(RESULT)
                          
   
    myArray[0]        
 
   
```
---

| 메타 문자 | 설명 |
|-------|--------|
| `\w` | 대소문자와 밑중릉 포함하는 모든 영숫자 ([a-zA-Z0-9_]와 같다) |
| `\W` | 영숫자나, 밑줄이 아닌 모든 문자 ([^a-zA-Z0-9_]와 같다) |
---

```
(TEXT)
11213
A1C2E3
48075
48237
M1B4F2
90046
H1H2H2
```
```
(SEARCH)
\w\d\w\d\w\d
```
```
(RESULT)
     
A1C2E3
     
     
M1B4F2
     
H1H2H2
```
---

| 메타 문자 | 설명 |
|-------|--------|
| `\s` | 모든 공백 문자 ([\f\n\r\t\v]와 같다) |
| `\S` | 공백 문자가 아닌 모든 문자 ([^\f\n\r\t\v]와 같다) |

### 포직스 문자 클래스 사용하기

| 분류 | 내용 |
|-------|--------|
| `[:alnum:]`  | 모든 영숫자 ([a-zA-Z0-9]와 같다) |
| `[:alpha:]`  | 모든 영문자 ([a-zA-Z]와 같다) |
| `[:blank:]`  | 빈칸(space)이나 탭 문자 ([\t ]와 같다) |
| `[:cntrl:]`  | 아스키 제어문자 (아스키 0번부터 31, 127번) |
| `[:digit:]`  | 모든 한 자리 숫자 ([0-9]와 같다) |
| `[:graph:]`  | [:print:]와 동일하나 빈칸(space)은 제외 |
| `[:lower:]`  | 모든 소문자 ([a-z]와 같다) |
| `[:print:]`  | 출력 가능한 모든 문자 |
| `[:punct:]`  | [:alnum:]이나 [:cntrl:]가 포함되지 않은 모든 문자 |
| `[:space:]`  | 빈칸을 포함한 모든 공백 문자 ([\f\n\r\t\v ]와 같다) |
| `[:upper:]`  | 모든 대문자 ([A-Z]와 같다) |
| `[:xdigit:]` | 모든 16진수 숫자 ([a-fA-F0-9]와 같다) |
---

```
(TEXT)
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
      MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
      LEFTMARGIN="0">
```
```
(SEARCH)
#[[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]]
```
```
(RESULT)
      
               #336633        #FFFFFF 
                                                    
                     
```

## 반복 찾기

### 몇 번 일치하는가?

```
(TEXT)
Send personal email to ben@forta.com. For questions
about a book use support@forta.com. Feel free to send
unsolicited email to spam@forta.com (wouldn't it be
nice if it were than simple, huh?).
```
```
(SEARCH)
\w+@\w+\.\w+
\w\+@\w\+\.\w\+
```
```
(RESULT)
                       ben@forta.com               
                 support@forta.com                   
                     spam@forta.com                
                                   
```
---

```
(TEXT)
Send personal email to ben@forta.com or
ben.forta@forta.com. For questions about a
book use support@forta.com. If your message
is urgent try ben@urgent.forta.com. Feel
free to send unsolicited email to
spam@forta.com (wouldn't it be nice if
it were that simple, huh?)
```
```
(SEARCH)
\w+@\w+\.\w+
\w\+@\w\+\.\w\+
```
```
(RESULT)
                       ben@forta.com   
    forta@forta.com                       
         support@forta.com                 
              ben@urgent.forta          
                                 
spam@forta.com                        
                          
```
---

```
(TEXT)
Send personal email to ben@forta.com or
ben.forta@forta.com. For questions about a
book use support@forta.com. If your message
is urgent try ben@urgent.forta.com. Feel
free to send unsolicited email to
spam@forta.com (wouldn't it be nice if
it were that simple, huh?)
```
```
(SEARCH)
[\w.]+@[\w.]+\.\w+
/[[:alnum:].]\+@[[:alnum:].]\+\.\w\+
```
```
(RESULT)
                       ben@forta.com   
ben.forta@forta.com                       
         support@forta.com                 
              ben@urgent.forta.com      
                                 
spam@forta.com                        
                          
```

([Vim regex with metacharacters inside bracket - Stack Overflow](https://stackoverflow.com/questions/7341322/vim-regex-with-metacharacters-inside-bracket)) Inside a collection, you have to use special character classes. 

---

```
(TEXT)
Hello .ben@forta.com is my email address.
```
```
(SEARCH)
[\w.]+@[\w.]+\.\w+
/[[:alnum:].]\+@[[:alnum:].]\+\.\w\+
```
```
(RESULT)
      .ben@forta.com                     
```
---

```
(TEXT)
Hello .ben@forta.com is my email address.
```
```
(SEARCH)
\w+[\w.]+@[\w.]+\.\w+
/\w\+[[:alnum:].]\+@[[:alnum:].]\+\.\w\+
```
```
(RESULT)
       ben@forta.com                     
```
---

```
(TEXT)
The URL is http://www.forta.com/, to connect
securely use https://www.forta.com/ instead.
```
```
(SEARCH)
http://[\w./]+
http:\/\/[[:alnum:]./]\+
```
```
(RESULT)
           http://www.forta.com/            
                                            
```
---

```
(TEXT)
The URL is http://www.forta.com/, to connect
securely use https://www.forta.com/ instead.
```
```
(SEARCH)
https?://[\w.\]+
https\?:\/\/[[:alnum:]./]\+
```
```
(RESULT)
           http://www.forta.com/            
             https://www.forta.com/         
```
---

```
(TEXT)
"101", "Ben", "Forta"
"102", "Jim", "James"

"103", "Roberta", "Robertson"
"104", "Bob", "Bobson"
```
```
(SEARCH)
[\r]?\n[\r]?\n
```
```
(RESULT)
                     
                     

                             
                      
```

### 구간 지정하기

```
(TEXT)
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
      MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
      LEFTMARGIN="0">
```
```
(SEARCH)
#[[:xdigit:]]{6}
#[[:xdigit:]]\{6\}
```
```
(RESULT)
               #336633        #FFFFFF 
                                                    
                     
```
---

```
(TEXT)
4/8/03
10-6-2004
2/2/2
01-01-01
```
```
(SEARCH)
\d{1,2}[-\/]\d{1,2}[-\/]\d{2,4}
\d\{1,2\}[-/]\d\{1,2\}[-/]\d\{2,4\}
```
```
(RESULT)
4/8/03
10-6-2004
     
01-01-01
```
---

```
(TEXT)
1001: $496.80
1002: $1290.69
1003: $26.43
1004: $613.42
1005: $7.61
1006: $414.90
1007: $25.00
```
```
(SEARCH)
\d+: \$\d{3,}\.\d{2}
\d\+: \$\d\{3,\}\.\d\{2\}
```
```
(RESULT)
1001: $496.80
1002: $1290.69
            
1004: $613.42
           
1006: $414.90
            
```

### 과하게 일치하는 상황 방지하기

```
(TEXT)
This offer is not available to customers
living in <B>AK</B> and <B>HI</B>.
```
```
(SEARCH)
<[Bb]>.*</[Bb]>
<[Bb]>.*<\/[Bb]>
```
```
(RESULT)
                                        
          <B>AK</B> and <B>HI</B> 
```
---

```
(TEXT)
This offer is not available to customers
living in <B>AK</B> and <B>HI</B>.
```
```
(SEARCH)
<[Bb]>.*?</[Bb]>
<[Bb]>.\{-}<\/[Bb]>
```
```
(RESULT)
                                        
          <B>AK</B>     <B>HI</B> 
```

## 위치 찾기

### 경계 지정하기

```
(TEXT)
The cat scattered his food all over the room.
```
```
(SEARCH)
cat
```
```
(RESULT)
    cat  cat                                 
```

### 단어 경계 지정하기

```
(TEXT)
The cat scattered his food all over the room.
```
```
(SEARCH)
\bcat\b
\<cat\>
```
```
(RESULT)
    cat                                      
```
---

```
(TEXT)
The captain wore this cap and cape proudly as
he sat listening to the recap of how his
crew saved the men from a capsized vessel.
```
```
(SEARCH)
\bcap
\<cap
```
```
(RESULT)
    cap               cap     cap            
                                        
                          cap             
```
---

```
(TEXT)
The captain wore this cap and cape proudly as
he sat listening to the recap of how his
crew saved the men from a capsized vessel.
```
```
(SEARCH)
cap\b
cap\>
```
```
(RESULT)
                      cap                    
                          cap           
                                          
```
---

```
(TEXT)
Please enter the nine-digit id as it
appears on your color - coded pass-key.
```
```
(SEARCH)
\B-\B
```
```
(RESULT)
                                    
                      -                
```

### 문자열 경계 지정하기

```
(TEXT)
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap"
```
```
(SEARCH)
<?xml.*\?>
```
```
(RESULT)
<?xml version="1.0" encoding="UTF-8" ?>
                                                  
                                                       
                                                 
```
---

```
(TEXT)
This is bad, real bad!
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap"
```
```
(SEARCH)
<?xml.*\?>
```
```
(RESULT)
                      
<?xml version="1.0" encoding="UTF-8" ?>
                                                  
                                                       
                                                 
```
---

```
(TEXT)
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap"
```
```
(SEARCH)
^\s*<?xml.*\?>
```
```
(RESULT)
<?xml version="1.0" encoding="UTF-8" ?>
                                                  
                                                       
                                                 
```
---

```
(SEARCH)
</[Hh][Tt][Mm][Ll]>\s*$
```
---

```
(TEXT)
<SCRIPT>
function doSpellCheck (form, field) {
  // Make sure not empty
  if (field.value == '') {
    return false;
  }
  // Init
  var windowName='spellWindow';
  var spellCheckURL='spell.cfm?formname=comment&fieldname='+field.name;
  ...
  // Done
  return false;
}
</SCRIPT>
```
```
(SEARCH)
(?m)^\s*//.*$
```
```
(RESULT)
        
                                     
  // Make sure not empty
                          
                 
   
  // Init
                               
                                                                       
     
  // Done
               
 
         
```

## 하위 표현식 사용하기

### 하위 표현식 이해하기

```
(TEXT)
Hello, my name is Ben&nbsp;Forta, and I am
the tutor of books on SQL, ColdFusion, WAP,
Windows&nbsp;&nbsp;2000, and other subjects.
```
```
(SEARCH)
&nbsp;{2,}
```
```
(RESULT)
                                          
                                           
                                            
```

### 하위 표현식으로 묶기

```
(TEXT)
Hello, my name is Ben&nbsp;Forta, and I am
the tutor of books on SQL, ColdFusion, WAP,
Windows&nbsp;&nbsp;2000, and other subjects.
```
```
(SEARCH)
(&nbsp;){2,}
```
```
(RESULT)
                                          
                                           
       &nbsp;&nbsp;                         
```
---

```
(TEXT)
Pinging hog.forta.com [12.159.46.200]
with 32 bytes of data:
```
```
(SEARCH)
\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}
```
```
(RESULT)
                       12.159.46.200 
                      
```
---

```
(TEXT)
Pinging hog.forta.com [12.159.46.200]
with 32 bytes of data:
```
```
(SEARCH)
(\d{1,3}\.){3}\d{1,3}
```
```
(RESULT)
                       12.159.46.200 
                      
```
---

```
(TEXT)
ID:042
SEX: M
DOB: 1967-08-17
Status: Active
```
```
(SEARCH)
19|20\d{2}
```
```
(RESULT)
      
      
     19        
              
```
---

```
(TEXT)
ID:042
SEX: M
DOB: 1967-08-17
Status: Active
```
```
(SEARCH)
(19|20)\d{2}
\(19\|20\)\d\{2\}
```
```
(RESULT)
      
      
     1967      
              
```

### 중첩된 하위 표현식

```
(SEARCH)
(\d{1,3}\.){3}\d{1,3}
```
---

```
(TEXT)
Pinging hog.forta.com [12.159.46.200]
with 32 bytes of data:
```
```
(SEARCH)
(((\d{1,2})|(1\d{2})|(2[0-4]\d)|(25[0-5]))\.){3}((\d{1,2})|(1\d{2})|(2[0-4]\d)|(25[0-5]))
```
```
(RESULT)
                       12.159.46.200 
                      
```

## 역참조 사용하기

### 역참조 이해하기

```
(TEXT)
<BODY>
<H1>Welcome to my Homepage</H1>
Content is divided into two sections:<BR>
<H2>ColdFusion</H2>
Information about Macromedia ColdFusion.
<H2>Wireless</H2>
Information about Bluetooth, 802.11, and more.
</BODY>
```
```
(SEARCH)
<[hH]1>.*</[hH]1>
```
```
(RESULT)
      
<H1>Welcome to my Homepage</H1>
                                         
                   
                                        
                 
                                              
       
```
---

```
(TEXT)
<BODY>
<H1>Welcome to my Homepage</H1>
Content is divided into two sections:<BR>
<H2>ColdFusion</H2>
Information about Macromedia ColdFusion.
<H2>Wireless</H2>
Information about Bluetooth, 802.11, and more.
</BODY>
```
```
(SEARCH)
<[hH][1-6]>.*?</[hH][1-6]>
```
```
(RESULT)
      
<H1>Welcome to my Homepage</H1>
                                         
<H2>ColdFusion</H2>
                                        
<H2>Wireless</H2>
                                              
       
```
---

```
(TEXT)
<BODY>
<H1>Welcome to my Homepage</H1>
Content is divided into two sections:<BR>
<H2>ColdFusion</H2>
Information about Macromedia ColdFusion.
<H2>Wireless</H3>
Information about Bluetooth, 802.11, and more.
</BODY>
```
```
(SEARCH)
<[hH][1-6]>.*?</[hH][1-6]>
```
```
(RESULT)
      
<H1>Welcome to my Homepage</H1>
                                         
<H2>ColdFusion</H2>
                                        
<H2>Wireless</H3>
                                              
       
```

### 역참조로 찾기

```
(TEXT)
This is a block of of text,
several words here are are
repeated, and and they
should not be.
```
```
(SEARCH)
[ ]+(\w+)[ ]+\1
```
```
(RESULT)
                of of      
                   are are
          and and     
              
```
---

```
(TEXT)
<BODY>
<H1>Welcome to my Homepage</H1>
Content is divided into two sections:<BR>
<H2>ColdFusion</H2>
Information about Macromedia ColdFusion.
<H2>Wireless</H2>
Information about Bluetooth, 802.11, and more.
<H2>This is not valid HTML</H3>
</BODY>
```
```
(SEARCH)
<[hH]([1-6])>.*?</[hH]\1>
<[hH]\([1-6]\)>.*<\/[hH]\1>
```
```
(RESULT)
      
<H1>Welcome to my Homepage</H1>
                                         
<H2>ColdFusion</H2>
                                        
<H2>Wireless</H2>
                                              
                               
       
```

### 치환 작업 수행하기

```
(TEXT)
Hello, ben@forta.com is my email address.
```
```
(SEARCH)
\w+[\w\.]*@[\w\.]+\.\w+
```
```
(RESULT)
       ben@forta.com                     
```
---

```
(TEXT)
Hello, ben@forta.com is my email address.
```
```
(SEARCH)
\w+[\w\.]*@[\w\.]+\.\w+
```
```
(SUBSTITUTE)
<A HREF="mailto:$1">$1</A>
```
```
(RESULT)
Hello, <A HREF="mailto:ben@forta.com">ben@forta.com</A> is my email address.
```
---

```
(TEXT)
313-555-1234
248-555-9999
810-555-9000
```
```
(SEARCH)
(\d{3})(-)(\d{3})(-)(\d{4})
```
```
(SUBSTITUTE)
($1) $3-$5
```
```
(RESULT)
(313) 555-1234
(248) 555-9999
(810) 555-9000
```
---

| 메타 문자 | 설명 |
|-------|--------|
| `\E` | \L 혹은 \U 변환의 끝을 나타낸다. |
| `\l` | 다음에 노는 글자를 소문자로 변환한다. |
| `\L` | \E를 만날 때까지 모든 문자를 소문자로 변환한다. |
| `\u` | 다음에 오는 글자를 대문자로 변환한다. |
| `\U` | \E를 만날 때까지 모든 문자를 대문자로 변환한다. |
---

```
(TEXT)
<BODY>
<H1>Welcome to my Homepage</H1>
Content is divided into two sections:<BR>
<H2>ColdFusion</H2>
Information about Macromedia ColdFusion.
<H2>Wireless</H3>
Information about Bluetooth, 802.11, and more.
<H2>This is not valid HTML</H3>
</BODY>
```
```
(SEARCH)
(<[hH]1>)(.*?)(</[hH]1>)
```
```
(SUBSTITUTE)
$1\U$2\E$3
```
```
(RESULT)
      
                               
                                         
                   
                                        
                 
                                              
                               
       
```

## 전방탐색과 후방탐색

### 전후방탐색 살펴보기

```
(TEXT)
<HEAD>
<TITLE>Ben Forta's Homepage</TITLE>
</HEAD>
```
```
(SEARCH)
<[tT][iI][tT][lL][eE]>.*</[tT][iI][tT][lL][eE]>
```
```
(RESULT)
      
<TITLE>Ben Forta's Homepage</TITLE>
       
```

### 전방탐색 - 앞으로 찾기

```
(TEXT)
http://www.forta.com/
https://mail.forta.com/
ftp://ftp.forta.com/
```
```
(SEARCH)
.+(?=:)
```
```
(RESULT)
http                 
https                  
ftp                 
```
---

```
(TEXT)
http://www.forta.com/
https://mail.forta.com/
ftp://ftp.forta.com/
```
```
(SEARCH)
.+(:)
```
```
(RESULT)
http:                
https:                 
ftp:                
```

### 후방탐색 - 뒤로 찾기

```
(TEXT)
ABC01: $23.45
HGG42: $5.31
CFMX1: $899.00
XTC99: $69.96
Total items found: 4
```
```
(SEARCH)
\$[0-9\.]+
```
```
(RESULT)
       $23.45
       $5.31
       $899.00
       $69.96
                    
```
---

```
(TEXT)
ABC01: $23.45
HGG42: $5.31
CFMX1: $899.00
XTC99: $69.96
Total items found: 4
```
```
(SEARCH)
[0-9\.]+
```
```
(RESULT)
    1   23.45
   42   5.31
    1   899.00
   99   69.96
                   4
```
---

```
(TEXT)
ABC01: $23.45
HGG42: $5.31
CFMX1: $899.00
XTC99: $69.96
Total items found: 4
```
```
(SEARCH)
(?<=\$)[0-9\.]+
```
```
(RESULT)
        23.45
        5.31
        899.00
        69.96
                    
```

### 전방탐색과 후방탐색 함께 사용하기

```
(TEXT)
<HEAD>
<TITLE>Ben Forta's Homepage</TITLE>
</HEAD>
```
```
(SEARCH)
(?<=<[tT][iI][tT][lL][eE]>).*(?=</[tT][iI][tT][lL][eE]>)
```
```
      
      
       Ben Forta's Homepage        
       
```

### 부정형 전후방탐색

| 종류 | 설명 |
|-------|--------|
| `(?=)`  | 긍정형 전방탐색 |
| `(?!)`  | 부정형 전방탐색 |
| `(?<=)` | 긍정형 후방탐색 |
| `(?<!)` | 부정형 후방탐색 |
---


```
(TEXT)
I paid $30 for 100 apples,
50 oranges, and 60 pears.
I saved $5 on this order.
```
```
(SEARCH)
(?<=\$)\d+
```
```
(RESULT)
        30                
                         
         5               
```
---

```
(TEXT)
I paid $30 for 100 apples,
50 oranges, and 60 pears.
I saved $5 on this order.
```
```
(SEARCH)
\b(?<!\$)\d+\b
```
```
(RESULT)
               100        
50              60       
                         
```
---

```
(TEXT)
I paid $30 for 100 apples,
50 oranges, and 60 pears.
I saved $5 on this order.
```
```
(SEARCH)
(?<!\$)\d+
```
```
(RESULT)
         0     100        
50              60       
                         
```

## 조건 달기

### 왜 조건을 다는가

```
(TEXT)
123-456-7890
(123)456-7890
(123)-456-7890
(123-456-7890
1234567890
123 456 7890
```
```
(SEARCH)
\(?\d{3}\)?-?\d{3}-\d{4}
```
```
(RESULT)
123-456-7890
(123)456-7890
(123)-456-7890
(123-456-7890
          
            
```

### 조건 사용하기

```
(TEXT)
<!-- Nav bar -->
<TD>
<A HREF="/home"><IMG SRC="/images/home.gif"></A>
<IMG SRC="/images/spacer.gif">
<A HREF="/search"><IMG SRC="/images/search.gif"></A>
<IMG SRC="/images/spacer.gif">
<A HREF="/help"><IMG SRC="/images/help.gif"></A>
</TD>
```
```
(SEARCH)
(<[Aa]\s+[^>]+>\s*)?<[Ii][Mm][Gg]\s+[^>]+>(?(1)\s*<\[Aa]>)
```
```
(RESULT)
                
    
<A HREF="/home"><IMG SRC="/images/home.gif"></A>
<IMG SRC="/images/spacer.gif">
<A HREF="/search"><IMG SRC="/images/search.gif"></A>
<IMG SRC="/images/spacer.gif">
<A HREF="/help"><IMG SRC="/images/help.gif"></A>
     
```
---

```
(TEXT)
123-456-7890
(123)456-7890
(123)-456-7890
(123-456-7890
1234567890
123 456 7890
```
```
(SEARCH)
(\()?\d{3}(?(1)\)|-)\d{3}-\d{4}
```
```
(RESULT)
123-456-7890
(123)456-7890
              
             
          
            
```
---

```
(TEXT)
11111
22222
33333-
44444-4444
```
```
(SEARCH)
\d{5}(-\d{4})?
```
```
(RESULT)
11111
22222
33333
44444-4444
```
---

```
(TEXT)
11111
22222
33333-
44444-4444
```
```
(SEARCH)
\d{5}(?(?=-)-\d{4})
```
```
(RESULT)
11111
22222
      
44444-4444
```
