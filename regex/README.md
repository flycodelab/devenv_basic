# 손에 잡히는 정규 표현식: Regular Expressions in 10 minutes
## 문자 하나 찾기

```
Hello, my name is Ben. Please visit
my website at http://www.forta.com/
```
```
Ben
my
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
[ns]a.\.xls
```
