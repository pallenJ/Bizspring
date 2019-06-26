## 자바에서의 날짜 Control

1. Java Date
> 자바의 기본 날짜/시간을 다루는 객체

* 객체 생성
	```java
	Date date = new Date(); //현재의 날짜와 시간을 저장한 객체 생성
	```
* Date 클래스의 주요 get 메소드

	|       메소드      	|                기능                	|
	|:-----------------:	|:----------------------------------:	|
	|     getDate()     	|       달의 날짜를 변환(1~31)       	|
	|      getDay()     	|        주의 날짜를 반환(0~6)       	|
	|   getFullYear()   	|       년도를 반환(4자리 숫자)      	|
	|     getMonth()    	|           달을 반환(0~11)          	|
	|     getHours()    	|          시간을 반환(0~23)         	|
	|    getMinutes()   	|           분을 반환(0~59)          	|
	|    getSeconds()   	|           초를 반환(0~59)          	|
	| getMilliseconds() 	|     1000분의 1초를 반환(0~999)     	|
	|      parse()      	| Date String을 분석하여 Date로 반환 	|

* Date 클래스의 주요 set 메소드

	|       메소드      	|            기능            	|
	|:-----------------:	|:--------------------------:	|
	|     setDate()     	|   달의 날짜를 설정(1~31)   	|
	|   setFullYear()   	|   년도를 설정(4자리 숫자)  	|
	|     setMonth()    	|       달을 설정(0~11)      	|
	|     setHours()    	|      시간을 반환(0~23)     	|
	|    setMinutes()   	|       분을 반환(0~59)      	|
	|    setSeconds()   	|       초를 반환(0~59)      	|
	| setMilliseconds() 	| 1000분의 1초를 반환(0~999) 	|

2. Java Date와 Calendar의 문제점

	|         문제점         	|                                                    설명                                                   	|
	|:----------------------:	|:---------------------------------------------------------------------------------------------------------:	|
	|    불변 객체가 아님    	|                          set으로 인한 시간변경은 누군가 악의적으로 변경할 수 있음                         	|
	|     상수 필드 남용     	|                                  처음 보거나 잘 모르는 경우 해석이 어려움                                 	|
	|    헷갈리는 월 지정    	| 달을 설정(0~11)1월을 0으로 표현하는 문제  Calendar.OCTOBER로 월을 지정하지만 실질적인 값은 9(!=10)인 문제 	|
	|  일관성 없는 요일 상수 	|                                 일요일이 0인 경우, 일요일이 1인 경우 존재                                 	|
	| Date와 Calendar의 분담 	|                            2개의 객체를 생성하며 프로세스를 거쳐서 메모리 낭비                            	|

	이러한 이유로 많은 개발자들은 Joda Time이나 Java 8 LocalDateTime을 사용.
2. Joda Time
	* Date와 Calendar의 단점을 보완하기 위해 만들어진 오픈 API
3. Java LocalDateTime
	* Date와 Calendar의 단점을 보완하기 위해 Java 8 에서 새로 생긴 클래스
	* Joda Time의 영향을 받아 비슷하게 설계됨 => 사용법이 거의 비슷

	1. 사용법
		```java
		LocalDateTime currentDateTime = LocalDateTime.now();    // 컴퓨터의 현재 날짜와 시간 정보. 결과 : 2019-06-26T17:34:07.757  
		LocalDateTime targetDateTime = LocalDateTime.of(int year, int month, int dayOfMonth, int hour, int minute, int second, int nanoOfSecond)
		```
	* 주요 시간 연산 메소드

	|            메소드            |       기능       |
	|:----------------------------:|:----------------:|
	|   plusYears(), minusYears()   | 년도 더하기 빼기 |
	|  plusMonths(), minusMonths()  |  월 더하기 빼기  |
	|    plusDays(), minusDays()    |  일 더하기 빼기  |
	|   plusHours(), minusHours()   | 시간 더하기 빼기 |
	| plusMinutes(), minusMinutes() |  분 더하기 빼기  |
	| plusSeconds(), minusSeconds() |  초 더하기 빼기  |
	| plusNanos(), minusNanos() |  나노초 더하기 빼기  |

	* 주요 시간 설정 메소드

	|            메소드            |       기능       |
	|:----------------------------:|:----------------:|
	|   withYear()   | 년도 설정 |
	|  withMonth()  |  월 설정  |
	|    withDayOfMonth()    |  일 설정  |
	|   withHour()   | 시간 설정 |
	| withMinute() |  분 설정  |
	| withSecond() |  초 설정  |
	| withNano() |  나노초 설정  |

	2. 포맷팅
	* LocalDate, LocalTime, LocaDateTime, ZonedDateTime 클래스의 `format(DateTimeFormatter formatter)` 메소드를 사용해서 원하는 문자열로 변환시킬 수 있다.

		```java
		LocalDateTime now = LocalDateTime.now();
		DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy년 M월 d일 a h시 m분");
		String nowString = now.format(dateTimeFormatter);   // 결과 : 2019년 6월 26일 오후 5시 20분
		```
		
[참조사이트](https://hamait.tistory.com/205)
