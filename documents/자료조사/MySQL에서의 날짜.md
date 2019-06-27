## MySQL에서의 날짜

1. DATE, DATETIME, TIMESTAMP 비교

	| 데이터 타입 |      값     |      기본 포맷      |        제공 범위        |
	|:-----------:|:-----------:|:-------------------:|:-----------------------:|
	|     DATE    |     날짜    |      YYYY-MM-DD     | 1000-01-01 ~ 9999-12-31 |
	|   DATETIME  | 날짜 + 시간 | YYYY-MM-DD HH:MM:SS | 1000-01-01 ~ 9999-12-31 |
	|  TIMESTAMP  | 날짜 + 시간 | YYYY-MM-DD HH:MM:SS | 1000-01-01 ~ 9999-12-31 |

* DATETIME과 TIMESTAMP의 차이점
	* DATETIME은 입력되는 날짜와 시간을 그대로 입력받음.
	* TIMESTAMP는 time_zone이라는 시스템 변수로 저장된 값을 기본으로 하여 날짜와 시간정보를 입력받음.

2. MySQL 시간 설정
	> DATE_ADD(기준 날짜, INTERVAL 숫자 인자) : 시간 더하기  
	> DATE_SUB(기준 날짜, INTERVAL 숫자 인자) : 시간 빼기

	* 사용가능한 인자

		|  인자  | 기능 |
		|:------:|:----:|
		| second |  초  |
		| minute |  분  |
		|  hour  | 시간 |
		|   day  |  일  |
		|  month |  달  |
		|  year  |  년  |

3. date_format을 이용하여 원하는 데이터 뽑기
	* `date_format` : MySQL에서 DATE, DATETIME, TIMESTAMP 값을 원하는 형태로 가져오기 위한 함수
		> ex) SELECT date_format(기준시간, '지정자') FROM `테이블명`;

		* 사용가능한 지정자

		|              <center>지정자              |      <center>설명                           |
		|:--------------------------------:|:---------------------------------------------------------:|
		|                %a                |              Weekday, 영문 약어 (Sun, …, Sat)             |
		| Weekday, 영문 약어 (Sun, …, Sat) |               Month, 영문 약어 (Jan, …, Dec)              |
		|                %c                |                      Month(1, …, 12)                      |
		|                %d                |         Day of the month, 두 자리 숫자(01, …, 31)         |
		|                %e                |                Day of the month (1, …, 31)                |
		|                %H                | Hour, 24시간 기준, 두 자리 수 이상 (00, …, 23, …, 100, …) |
		|                %h                |         Hour, 12시간 기준 두 자리 숫자 (01, …, 12)        |
		|                %i                |             Minutes , 두 자리 숫자(00, …, 59)             |
		|                %m                |              Month, 두 자리 숫자 (01, …, 12)              |
		|                %s                |             Seconds , 두 자리 숫자(00, …, 59)             |
		|                %U                |   Week, 두 자리 숫자, 일요일이 첫날인 주 단위(00, …, 53)  |
		|                %u                |   Week, 두 자리 숫자, 월요일이 첫날인 주 단위(00, …, 53)  |
		|                %Y                |             Year, 네 자리 숫자(0001, …, 9999)             |
		|                %y                |             Year, 두 자리 숫자(00, 01, …, 99)             |

		[참조 사이트](https://lightblog.tistory.com/155)
