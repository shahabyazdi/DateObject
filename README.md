# Date Object

supported calendars: `gregorian` , `persian` , `arabic`
default: `gregorian`

supported locals: `en` , `fa` , `ar`
default: `en`

React: [react-date-object](https://github.com/shahabyazdi/react-date-object)

# Install

## npm:

```shell
npm install date-object --save
```

## yarn:

```shell
yarn add date-object
```

# Usage

```javascript
var DateObject = require("date-object");

var dateObject = new DateObject();
```

# Example

## 1- new instance

### 1-1- String (year month day hour minute second millisecond meridiem)

```javascript
var date = new DateObject("2020 8 21 11 55 36 100 am");

date.format("YYYY/MM/DD hh:mm:ss.SSS a"); //2020/08/21 11:55:36.100 am

date = new DateObject("2020/08/01");

date.format("YYYY/MM/DD hh:mm:ss.SSS a"); //2020/08/01 00:00:00.0 am
```

### 1-2- Number (unix timestamp)

```javascript
var date = new DateObject(1597994736);

date.format("dddd DD MMMM @ hh:mm:ss.SSS a"); //Friday 21 August @ 11:55:36.0 am
```

### 1-3- JavaScript Date

```javascript
var $date = new Date(2019, 8, 20);

var date = new DateObject($date);

date.format(); //2019/09/20
```

### 1-4- DateObject

```javascript
var $date = new DateObject("2019/09/20");

var date = new DateObject($date);

date.format(); //2019/09/20
```

### 1-5- Object

#### 1-5-1-

```javascript
{
  date: String , Number(unix timestamp), JavaScript Date or DateObject, //default new Date()
  calendar: `gregorian`, `persian` or `arabic`, //default `gregorian`
  local: `en`, `fa` or `ar`, //default `en`
  format: `String` //default `YYYY/MM/DD`
}

```

```javascript
var date = new DateObject({
  date: new Date(),
  calendar: "gregorian",
  local: "en",
});

date.format(); //2020/08/21

date = new DateObject({
  date: new Date(),
  calendar: "persian",
  local: "fa",
});

date.format(); //۱۳۹۹/۰۵/۳۱

date = new DateObject({
  date: "31 Mordad 1399",
  calendar: "persian",
  local: "en",
  format: "DD MMMM YYYY",
});

date.format(); //31 Mordad 1399
```

#### 1-5-2-

```javascript
{
  year: Number,
  month: Number,
  day: Number,
  hour: Number, //default 0
  minute: Number, //default 0
  second: Number, //default 0
  millisecond: Number, //default 0
  calendar: `gregorian`, `persian` or `arabic`, //default `gregorian`
  local: `en`, `fa` or `ar`, //default `en`
  format: String //default `YYYY/MM/DD`
}

```

```javascript
var date = new DateObject({
  year: 2020,
  month: 8,
  day: 21,
  hour: 12,
  minute: 20,
  second: 36,
  milisecond: 152,
  format: "dddd DD MMMM YYYY",
});

date.format(); //Friday 21 August 2020

date = new DateObject({
  year: 1399,
  month: 5,
  day: 31,
  calendar: "persian",
  local: "en",
  format: "dddd DD MMMM YYYY",
});

date.format(); //Jomeh 31 Mordad 1399

date = new DateObject({
  year: 1399,
  month: 5,
  day: 31,
  calendar: "persian",
  local: "fa",
  format: "dddd DD MMMM YYYY",
});

date.format(); //جمعه ۳۱ مرداد ۱۳۹۹
```

## 2- setter methods

```javascript
var date = new DateObject();

date
  .setCalendar("gregorian")
  .setFormat("YYYY-MM-DD HH:mm:ss.SSS")
  .setLocal("en")
  .setYear(2020)
  .setMonth(8)
  .setDay(21)
  .setHour(12)
  .setMinute(20)
  .setSecond(14)
  .setMillisecond(200);

date.format(); //2020-09-21 12:20:14.200

date
  .setCalendar("persian")
  .setYear(1399)
  .setMonth(8)
  .setDay(21)
  .setFormat("dddd DD MMMM YYYY");

date.format(); //Jomeh 21 Azar 1399
```

## 3- get and set

```javascript
var date = new DateObject();

date.format(); //2020/08/21

date.year += 2;
date.month += 2;
date.day += 2;
date.hour += 2;
date.minute += 2;
date.second += 2;
date.millisecond += 2;

date.format(); //2022/10/23

console.log(date.month);

/**
 *  {
 *    name: 'October',
 *    shortName: 'Oct',
 *    length: 31,
 *    index: 9,
 *    number: 10,
 *    toString: [Function (anonymous)]
 *  }
 */

console.log(date.weekDay);

/**
 * {
 *   name: 'Sunday',
 *   shortName: 'Sun',
 *   index: 0,
 *   number: 1,
 *   toString: [Function (anonymous)]
 * }
 */

console.log(`${date.weekDay.name} ${date.year}/${date.month}/${date.day}`); //Sunday 2022/10/23

date.year = 2020;
date.month = 8;
date.day = 21;

date.isLeap; //true
date.isValid; //true
date.month.name; //August
date.month.length; //31
date.month.index; //7
date.month.number; //8

date.weekDay.name; //Friday
date.weekDay.index; //5
date.weekDay.number; //6

date.dayOfBeginning; //737658
date.dayOfYear; //234
date.daysLeft; //132
date.weekOfYear; //34
date.unix; //1597951800

date.weeks; // array [{ name: 'Sunday', shortName: 'Sun', ...}]
date.months; //array [{ name: 'January', shortName: 'Jan', ...}]
date.leaps; //array [4,   8,  12,  16,  20,...]
```

## 4- parse method

```javascript
var date = new DateObject();

date._format = "dddd DD MMMM YYYY";

date.parse("Monday 24 August 2020");
date.format("YYYY/MM/DD"); //2020/08/24

date.parse("Friday 07 August 2020");
date.format("YYYY-MM-DD"); //2020-08-07

date.setCalendar("persian").setFormat("YYYY/MM/DD").parse("1399/06/03");
date.format(); //1399/06/03

date.setFormat("YYYY/MM/DD HH:mm").parse("1399/06/03 12:32");
date.format("dddd DD MMMM @ hh:mm a"); //Doshanbeh 03 Shahrivar @ 12:32 am
```

## 5- getProperty

```javascript
let date = new DateObject({
  calendar: "arabic",
  date: "1442/01/01",
  local: "ar",
});

date.getProperty("M"); //1
date.format("M"); //١

typeof date.getProperty("D"); //number
typeof date.format("D"); //string

Number(date.getProperty("YYYY")); //1442
Number(date.format("YYYY")); //NaN
```

## 6- other methods

```javascript
var date = new DateObject();

date.toFirstOfWeek(); //2020/08/16
date.toFirstOfMonth(); //2020/08/01
date.toFirstOfYear(); //2020/01/01
date.toFirstWeekOfYear(); //2020/01/05
date.toLastOfMonth(); //2020/01/31
date.toLastOfWeek(); //2020/02/01
date.toLastOfYear(); //2020/12/31
date.toLastWeekOfYear(); //2020/12/27

date.toString(); //2020/12/27
date.toDate(); //instanceof Date
date.toUnix(); //1609014600
date.toJulianDay(); //2459210
date.valueOf(); //737786
date.toObject();
/**
 *{
 *    year: 2020,
 *    month: {
 *        length: 31,
 *        name: 'December',
 *        shortName: 'Dec',
 *        index: 11,
 *        number: 12,
 *        toString: [Function (anonymous)]
 *    },
 *    day: 27,
 *    weekDay: {
 *        index: 0,
 *        number: 1,
 *        toString: [Function: toString],
 *        name: 'Sunday',
 *        shortName: 'Sun'
 *    },
 *    hour: 11,
 *    minute: 8,
 *    second: 34,
 *    millisecond: 0,
 *    weekOfYear: 52,
 *    dayOfYear: 362,
 *    daysLeft: 4,
 *    calendar: 'gregorian',
 *    local: 'en'
 *}
 */
```

# using calendars, format & locals

```javascript
var date = new DateObject({ calendar: "gregorian", format: "dddd DD MMMM" });

date.format(); //Friday 21 August

date.calendar = "persian"; //Jomeh 31 Mordad
date.local = "fa"; //جمعه 31 مرداد
date._format = "YY/MM/DD"; //۹۹/۰۵/۳۱

date.setCalendar("gregorian").setLocal("en"); //20/08/21

date = new DateObject(new Date());

date.convert("persian").format(); //1399/05/31
date.convert("arabic").format(); //1442/01/02
```

# format types

| Type |       Example       |          Description          | Availability (Parse /Format) |
| ---- | :-----------------: | :---------------------------: | ---------------------------- |
| YYYY |        2020         |           full year           | both                         |
| YY   |         20          |         2 digits year         | both                         |
| MMMM |      December       |          month name           | both                         |
| MMM  |         Dec         |       month short name        | both                         |
| MM   |   03, 09, 10, ...   |     2 digits month number     | both                         |
| M    |    3, 9, 10, ...    |         month number          | both                         |
| DDDD |         09          |          day of year          | format                       |
| DDD  |          9          |          day of year          | format                       |
| DD   | 03, 09, 10, 17, ... |     2 digits day of month     | both                         |
| D    |    3, 9 ,10, 17     |         day of month          | both                         |
| WW   |    week of year     |      01, 03, 24, 33, ...      | format                       |
| W    |    week of year     |       1, 3, 24. 33, ...       | format                       |
| dddd |    week day name    | Saturday, Sunday, Monday, ... | format                       |
| ddd  | week day short name |      Sat, Sun, Mon, ...       | format                       |
| HH   | 03, 09, 10, 17,...  | 2 digits hour (24 hour mode)  | both                         |
| H    |  3, 9, 10, 17,...   |      hour (24 hour mode)      | both                         |
| hh   | 03, 09, 10, 17,...  | 2 digits hour (12 hour mode)  | both                         |
| h    |  3, 9, 10, 17,...   |      hour (12 hour mode)      | both                         |
| mm   | 03, 09, 10, 17,...  |        2 digits minute        | both                         |
| m    |  3, 9, 10, 17,...   |            minute             | both                         |
| ss   | 03, 09, 10, 17,...  |        2 digits second        | both                         |
| s    |  3, 9, 10, 17,...   |            second             | both                         |
| SSS  |         100         |     3 digits millisecond      | both                         |
| SS   |         10          |     2 digits millisecond      | both                         |
| S    |         10          |      1 digit millisecond      | both                         |
| A    |         AM          |           meridiem            | both                         |
| a    |         am          |      meridiem lowercase       | both                         |
