

In this blog post I am going to discuss some useful example on datetime in python. In Python, date is not a datatype but can be import as object from datetime module to manipulate date, times and intervals.


## Example to import and print current date and time -

```python
import datetime

print(datetime.datetime.now())

2021-03-09 07:22:15.183617 
```


There are following commonly used classes in datetime module -

    date class - Manipulating only dates i.e. year, month and day attributes.

    time class - Time independent of the day (hour, minute, second, microsecond)

    datetime class  - It is consist of date and time with year, month, day, hour, minute, second, microsecond attributes

    timedelta class - Duration of the time used for manipulating dates.



# Stringify the datetime objects :

The `strftime` method is used to stringify the datetime objects into string according to provided format. We can convert date, datetime and time objects to string using this method.


## This is an example to stringify the datetime objects:

```python
import datetime

# now date and time
datetime_now = datetime.datetime.now()

# year, month, day, hour, minute, second, and microsecond
print(datetime_now)

# 2021-03-10 17:56:01.806723
datetime_now_str = datetime_now.strftime("%b %d, %Y")

print(datetime_now_str)
# Mar 10, 2021
```

 

 Here,  %b stands for short version of month name i.e. Mar
        %d stands for day of month 01-31
        %Y stands for full version of yead i.e. 2021

 
Also there are many format codes some commonly used are discussed below:


    %d - Day of the month(01-31)

 
    %m - Month as number(01-12)
    %b - Short version of month(e.g. Mar)
    %B - Full version of Month name(e.g. March)

    %a - Short version of weekday(e.g. Wed)
    %A - Full version of weekday(e.g. Wednesday)
    %w - Weekday as number 0-6 and 0 is Sunday.

 

    %Y - Full version of year(e.g 2021)
    %y - Short version of year(e.g. 21)

 

    %I - Hour ranging 00-12
    %H - Hours ranging 00-23


    %p - AM/PM
    %M - Minutes ranging 00-59
    %S - Seconds ranging 00-59
    %f - Microseconds ranging 000000-999999
    %j - Day number of year ranging 001-366

	
	

# Conversion of string datetime to datetime object: 

The `strptime()` method is used to convert string datetime to datetime object.

we need to provide the string datetime format we are using by using codes discussed above to `strptime()`.

## Example to convert datetime string to datetime object

```python
from datetime import datetime

date_string = "March 11, 2021"

print("date_string =", date_string)
print("type of date_string =", type(date_string))
# date_string = March 11, 2021
# type of date_string = <class 'str'>

date_obj = datetime.strptime(date_string, "%B %d, %Y")

print("date_object =", date_obj)
print("type of date_object =", type(date_obj))
# date_object = 2021-03-11 00:00:00
# type of date_object = <class 'datetime.datetime'>
```


Get today's date and and ways to get month day, month and year.

```python
from datetime import date

# this is returns today date in YYYY-MM-DD pattern
today_date = date.today()
print(today_date)
# 2021-03-11

# to get month day, month, year
print(today_date.month)
# 3
print(today_date.day)
# 11
print(today_date.year)
# 2021
```


## Example to interact with time class:

    The datetime's time class is to access time and it's conversions

```python
from datetime import time

# initimization without parameter sets
# hour = 0, minute = 0, second = 0
time_obj = time()
print("time_obj =", time_obj)
# time_obj = 00:00:00

# arguments patern - time(hour, minute and second)
time_obj = time(23, 00, 28)
print("time_obj =", time_obj)
# time_obj = 23:00:28

# we can assign it with name if not following the positional
# arguments pattern
time_obj = time(minute = 10, second = 36, hour = 21)
print("time_obj =", time_obj)
# time_obj = 21:10:36

# time with microseconds time(hour, minute, second, microsecond)
time_obj = time(20, 12, 36, 554466)
print("time_obj =", time_obj)
# time_obj = 20:12:36.554466
```


## Also there is easy way to get it's attribtes like:

```python
print("time_obj hour -> ", time_obj.hour)
# time_obj hour ->  20
print("time_obj minutes -> ", time_obj.minute)
# time_obj minutes ->  12
print("time_obj seconds -> ", time_obj.second)
# time_obj seconds ->  36
print("time_obj microseconds -> ", time_obj.microsecond)
# time_obj microseconds ->  554466
```

 

 
# `timedelta` in datetime module:

The timedelta is duration of the time used for manipulating date, time, datetime objects.

## `timedelta` object can be created using the following way:

```python
import datetime

datetime.timedelta(
    days=0,
    seconds=0,
    microseconds=0,
    milliseconds=0,
    minutes=0,
    hours=0,
    weeks=0
        )
```

Let’s try examples of manipulating datetime, date, and time using timedelta object.

 
## Example of `timedelta` with datetime objects :

```python
from datetime import datetime, timedelta

current_datetime = datetime.now()
print('current datetime:', current_datetime)
# current datetime: 2021-03-11 02:57:18.799347

# one year future date by adding 365
datetime_after_one_year = current_datetime + timedelta(days=365)
print('one year from now date:', datetime_after_one_year)
# one year from now date: 2022-03-11 02:58:20.605825

# past dates
yesterday_datetime = current_datetime - timedelta(days=1)
print('yesterday datetime:', yesterday_datetime)
# yesterday datetime: 2021-03-10 02:59:29.567591
```


 

## Example of `timedelta` with date objects :

```python
from datetime import date, timedelta


current_date = date.today()
print('current date:', current_date)
# current date: 2021-03-11

tomorrow_date = current_date + timedelta(days=1)
print('tomorrow date:', tomorrow_date)
# tomorrow date: 2021-03-12

yesterday_date = current_date - timedelta(days=1)
print('yesterday date:', yesterday_date)
# yesterday date: 2021-03-10
```



## Example of `timedelta` with `time` objects :

 
```python
from datetime import timedelta, datetime

current_datetime = datetime.now()
print('current time:', current_datetime)
# current time: 2021-03-11 04:08:37.341550

current_time = current_datetime + timedelta(seconds=60)
print('one min from current time:', current_time)
# one min from current time: 2021-03-11 04:09:37.341550

print('Timedelta Object Representation:', repr(timedelta(days=2, seconds=40, hours=20, milliseconds=145)))
# Timedelta Object Representation: datetime.timedelta(days=2, seconds
# =72040, microseconds=145000)
```
