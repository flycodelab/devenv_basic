# 손에 잡히는 정규 표현식: Regular Expressions in 10 minutes

## 문자 하나 찾기

### 문자 그대로 찾기

```
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
| [\b] | 역스페이스 |
| \f | 페이지 넘김 (form feed) |
| \n | 줄바꿈 |
| \r | 캐리지 리턴 |
| \t | 탭 |
| \v | 수직 탭 |

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
| \d | 숫자 하나 ([0-9]와 같다) |
| \D | 숫자를 제외한 문자 하나 ([^0-9]와 같다) |

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
| \w | 대소문자와 밑중릉 포함하는 모든 영숫자 ([a-zA-Z0-9_]와 같다) |
| \W | 영숫자나, 밑줄이 아닌 모든 문자 ([^a-zA-Z0-9_]와 같다) |

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
| \s | 모든 공백 문자 ([\f\n\r\t\v]와 같다) |
| \S | 공백 문자가 아닌 모든 문자 ([^\f\n\r\t\v]와 같다) |

### 포직스 문자 클래스 사용하기

| 분류 | 내용 |
|-------|--------|
| [:alnum:] | 모든 영숫자 ([a-zA-Z0-9]와 같다) |
| [:alpha:] | 모든 영문자 ([a-zA-Z]와 같다) |
| [:blank:] | 빈칸(space)이나 탭 문자 ([\t ]와 같다) |
| [:cntrl:] | 아스키 제어문자 (아스키 0번부터 31, 127번) |
| [:digit:] | 모든 한 자리 숫자 ([0-9]와 같다) |
| [:graph:] | [:print:]와 동일하나 빈칸(space)은 제외 |
| [:lower:] | 모든 소문자 ([a-z]와 같다) |
| [:print:] | 출력 가능한 모든 문자 |
| [:punct:] | [:alnum:]이나 [:cntrl:]가 포함되지 않은 모든 문자 |
| [:space:] | 빈칸을 포함한 모든 공백 문자 ([\f\n\r\t\v ]와 같다) |
| [:upper:] | 모든 대문자 ([A-Z]와 같다) |
| \`[:xdigit:]\` | 모든 16진수 숫자 ([a-fA-F0-9]와 같다) |
