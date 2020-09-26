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

