# 손에 잡히는 정규 표현식: Regular Expressions in 10 minutes

## 문자 하나 찾기

### 문자 그대로 찾기

```
(TEXT)
Hello, my name is Ben. Please visit
my website at http://www.forta.com/
```
```
Ben
my
```

### 모든 문자 찾기

```
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
sales.
```

```
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
sales.
```

```
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
.a.
```

```
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
.a..
```

### 특수 문자 찾기

```
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
.a.\.xls
```

## 문자 집합으로 찾기

### 여러 문자 중 하나와 일치시키기


```
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
[ns]a.\.xls
```

```
The phrase "regular expression" is often
abbreviated as RegEx or regex.
```
```
[Rr]eg[Ee]x
```

### 문자 집합 범위 사용하기

```
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
[ns]a[0123456789]\.xls
```

```
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
[ns]a[0-9]\.xls
```

```
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
      MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
      LEFTMARGIN="0">
```
```
#[0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f][0-9A-Fa-f]
```

### 제외하고 찾기

```
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
[ns]a[^0-9]\.xls
```

## 메타 문자 사용하기

### 이스케이프 다시 살펴보기

```
var myArray = new Array();
...
if (myArray[0] == 0) {
}
...
```
```
myArray[0]
```

```
var myArray = new Array();
...
if (myArray[0] == 0) {
}
...
```
```
myArray\[0\]
```

```
\home\ben\sales\
```
```
\\
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

```
"101", "Ben", "Forta"
"102", "Jim", "James"

"103", "Roberta", "Robertson"
"104", "Bob", "Bobson"
```
```
\r\n\r\n
```

### 특정한 문자 형태와 일치시키기


| 메타 문자 | 설명 |
|-------|--------|
| `\d` | 숫자 하나 ([0-9]와 같다) |
| `\D` | 숫자를 제외한 문자 하나 ([^0-9]와 같다) |

```
var myArray = new Array();
...
if (myArray[0] == 0) {
}
...
```
```
myArray\[\d\]
```

| 메타 문자 | 설명 |
|-------|--------|
| `\w` | 대소문자와 밑중릉 포함하는 모든 영숫자 ([a-zA-Z0-9_]와 같다) |
| `\W` | 영숫자나, 밑줄이 아닌 모든 문자 ([^a-zA-Z0-9_]와 같다) |

```
11213
A1C2E3
48075
48237
M1B4F2
90046
H1H2H2
```
```
\w\d\w\d\w\d
```

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

```
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
      MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
      LEFTMARGIN="0">
```
```
#[[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]][[:xdigit:]]
```

## 반복 찾기

### 몇 번 일치하는가?

```
Send personal email to ben@forta.com. For questions
about a book use support@forta.com. Feel free to send
unsolicited email to spam@forta.com (wouldn't it be
nice if it were than simple, huh?).
```
```
\w+@\w+\.\w+
```

```
Send personal email to ben@forta.com or
ben.forta@forta.com. For questions about a
book use support@forta.com. If your message
is urgent try ben@urgent.forta.com. Feel
free to send unsolicited email to
spam@forta.com (wouldn't it be nice if
it were that simple, huh?)
```
```
\w+@\w+\.\w+
```

```
Send personal email to ben@forta.com or
ben.forta@forta.com. For questions about a
book use support@forta.com. If your message
is urgent try ben@urgent.forta.com. Feel
free to send unsolicited email to
spam@forta.com (wouldn't it be nice if
it were that simple, huh?)
```
```
[\w.]+@[\w.]+\.\w+
```

```
Hello .ben@forta.com is my email address.
```
```
[\w.]+@[\w.]+\.\w+
```

```
Hello .ben@forta.com is my email address.
```
```
\w+[\w.]+@[\w.]+\.\w+
```

```
The URL is http://www.forta.com/, to connect
securely use https://www.forta.com/ instead.
```
```
http://[\w.\]+
```

```
The URL is http://www.forta.com/, to connect
securely use https://www.forta.com/ instead.
```
```
https?://[\w.\]+
```

```
"101", "Ben", "Forta"
"102", "Jim", "James"

"103", "Roberta", "Robertson"
"104", "Bob", "Bobson"
```
```
[\r]?\n[\r]?\n
```

### 구간 지정하기

```
<BODY BGCOLOR="#336633" TEXT="#FFFFFF"
      MARGINWIDTH="0" MARGINHEIGHT="0" TOPMARGIN="0"
      LEFTMARGIN="0">
```
```
#[[:xdigit:]]{6}
```

```
4/8/03
10-6-2004
2/2/2
01-01-01
```
```
\d{1,2}[-\/]\d{1,2}[-\/]\d{2,4}
```

```
1001: $496.80
1002: $1290.69
1003: $26.43
1004: $613.42
1005: $7.61
1006: $414.90
1007: $25.00
```
```
\d+: \$\d{3,}\.\d{2}
```

### 과하게 일치하는 상황 방지하기

```
This offer is not available to customers
living in <B>AK</B> and <B>HI</B>.
```
```
<[Bb]>.*</[Bb]>
```

```
This offer is not available to customers
living in <B>AK</B> and <B>HI</B>.
```
```
<[Bb]>.*?</[Bb]>
<[Bb]>.\{-}<\/[Bb]>

```

## 위치 찾기

### 경계 지정하기

```
The cat scattered his food all over the room.
```
```
cat
```

### 단어 경계 지정하기

```
The cat scattered his food all over the room.
```
```
\bcat\b
\<cat\>
```

```
The captain wore this cap and cape proudly as
he sat listening to the recap of how his
crew saved the men from a capsized vessel.
```
```
\bcap
\<cap
```

```
The captain wore this cap and cape proudly as
he sat listening to the recap of how his
crew saved the men from a capsized vessel.
```
```
cap\b
cap\>
```

```
Please enter the nine-digit id as it
appears on your color - coded pass-key.
```
```
\B-\B
```

### 문자열 경계 지정하기

```
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap"
```
```
<?xml.*\?>
```

```
This is bad, real bad!
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap"
```
```
<?xml.*\?>
```

```
<?xml version="1.0" encoding="UTF-8" ?>
<wsdl:definitions targetNamespace="http://tips.cf"
xmlns:impl="http://tips.cf" xmlns:intf="http://tips.cf"
xmlns:apachesoap="http://xml.apache.org/xml-soap"
```
```
^\s*<?xml.*\?>
```

```
</[Hh][Tt][Mm][Ll]>\s*$
```

```
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
(?m)^\s*//.*$
```

## 하위 표현식 사용하기

### 하위 표현식 이해하기

```
Hello, my name is Ben&nbsp;Forta, and I am
the tutor of books on SQL, ColdFusion, WAP,
Windows&nbsp;&nbsp;2000, and other subjects.
```
```
&nbsp;{2,}
```

### 하위 표현식으로 묶기

```
Hello, my name is Ben&nbsp;Forta, and I am
the tutor of books on SQL, ColdFusion, WAP,
Windows&nbsp;&nbsp;2000, and other subjects.
```
```
(&nbsp;){2,}
```

```
Pinging hog.forta.com [12.159.46.200]
with 32 bytes of data:
```
```
\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}
```

```
Pinging hog.forta.com [12.159.46.200]
with 32 bytes of data:
```
```
(\d{1,3}\.){3}\d{1,3}
```

```
ID:042
SEX: M
DOB: 1967-08-17
Status: Active
```
```
19|20\d{2}
```

```
ID:042
SEX: M
DOB: 1967-08-17
Status: Active
```
```
(19|20)\d{2}
\(19\|20\)\d\{2\}
```

### 중첩된 하위 표현식

```
(\d{1,3}\.){3}\d{1,3}
```

```
Pinging hog.forta.com [12.159.46.200]
with 32 bytes of data:
```
```
(((\d{1,2})|(1\d{2})|(2[0-4]\d)|(25[0-5]))\.){3}((\d{1,2})|(1\d{2})|(2[0-4]\d)|(25[0-5]))
```

## 역참조 사용하기

### 역참조 이해하기

```
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
<[hH]1>.*</[hH]1>
```

```
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
<[hH][1-6]>.*?</[hH][1-6]>
```

```
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
<[hH][1-6]>.*?</[hH][1-6]>
```

### 역참조로 찾기

```
This is a block of of text,
several words here are are
repeated, and and they
should not be.
```
```
[ ]+(\w+)[ ]+\1
```

```
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
<[hH]([1-6])>.*?</[hH]\1>
<[hH]\([1-6]\)>.*<\/[hH]\1>
```

### 치환 작업 수행하기

```
Hello, ben@forta.com is my email address.
```
```
\w+[\w\.]*@[\w\.]+\.\w+
```

```
Hello, ben@forta.com is my email address.
```
```
\w+[\w\.]*@[\w\.]+\.\w+
```
```
<A HREF="mailto:$1">$1</A>
```

| 메타 문자 | 설명 |
|-------|--------|
| `\E` | \L 혹은 \U 변환의 끝을 나타낸다. |
| `\l` | 다음에 노는 글자를 소문자로 변환한다. |
| `\L` | \E를 만날 때까지 모든 문자를 소문자로 변환한다. |
| `\u` | 다음에 오는 글자를 대문자로 변환한다. |
| `\U` | \E를 만날 때까지 모든 문자를 대문자로 변환한다. |

```
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
(<[hH]1>)(.*?)(</[hH]1>)
```
```
$1\U$2\E$3
```

## 전방탐색과 후방탐색

### 전후방탐색 살펴보기
### 전방탐색 - 앞으로 찾기
### 후방탐색 - 뒤로 찾기
### 전방탐색과 후방탐색 함께 사용하기
### 부정형 전후방탐색

## 조건 달기

### 왜 조건을 다는가
### 조건 사용하기
