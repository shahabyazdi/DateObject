# Date Object

supported calendars: `gregorian` , `persian` , `arabic` , `indian`
default: `gregorian`

supported locales: `en` , `fa` , `ar` , `hi`
default: `en`

React: [react-date-object](https://github.com/shahabyazdi/react-date-object)

[Descriptions](https://shahabyazdi.github.io/react-multi-date-picker/date-object/)

# Versions before 2.0.0

The way to entering `calendars` and `locales` for the versions before 2.0.0 is different.

To see the readme file for v1.x click <a href="https://github.com/shahabyazdi/date-object/tree/v1.x#readme" target="_blank">here</a>

# 1- Install

## 1-1- npm:

```shell
npm install date-object --save
```

## 1-2- yarn:

```shell
yarn add date-object
```

## 1-3- jsDelivr:

```javascript
<script src="https://cdn.jsdelivr.net/npm/date-object@latest/dist/umd/date-object.min.js"></script>
```

# 2- Usage

```javascript
var DateObject = require("date-object");
var date = new DateObject();

console.log(date.format()); //2021/06/10
```

# 3- Calendars

**You only need to import Calendar if you want to use a calendar other than Gregorian.**

<table>
<thead>
<tr>
<th>Calendar</th>
<th>CJS</th>
<th>ES</th>
<th>UMD</th>
</th>
</thead>
<tbody>

<tr>
<td>gregorian</td>
<td>/calendars/cjs/gregorian.js</td>
<td>/calendars/es/gregorian.js</td>
<td>/calendars/umd/gregorian.min.js</td>
<tr>

<tr>
<td>persian</td>
<td>/calendars/cjs/persian.js</td>
<td>/calendars/es/persian.js</td>
<td>/calendars/umd/persian.min.js</td>
<tr>

<tr>
<td>arabic</td>
<td>/calendars/cjs/arabic.js</td>
<td>/calendars/es/arabic.js</td>
<td>/calendars/umd/arabic.min.js</td>
<tr>

<tr>
<td>indian</td>
<td>/calendars/cjs/indian.js</td>
<td>/calendars/es/indian.js</td>
<td>/calendars/umd/indian.min.js</td>
<tr>

</tbody>
</table>

<br>

<details>
  <summary>Examples</summary>

## 3-1- Persian Calendar (Solar Hijri)

```javascript
var DateObject = require("date-object");
var persian = require("date-object/calendars/cjs/persian");

var date = new DateObject({ calendar: persian });

console.log(date.format()); //1400/03/20
```

## 3-2- Arabic Calendar (Islamic Hijri)

```javascript
var DateObject = require("date-object");
var arabic = require("date-object/calendars/cjs/arabic");

var date = new DateObject({ calendar: arabic });

console.log(date.format()); //1442/10/29
```

## 3-3- Indian Calendar

```javascript
var DateObject = require("date-object");
var indian = require("date-object/calendars/cjs/indian");

var date = new DateObject({ calendar: indian });

console.log(date.format()); //1943/03/20
```

</details>

<br>

# 4- Locales

**You only need to import Locale if you want to use a locale other than En.**

<table>
<thead>
<tr><th colspan="2" rowspan="2"></th><th colspan="4">Calendars</th></tr>
<tr>
<th>Gregorian</th>
<th>Persian</th>
<th>Arabic</th>
<th>Indian</th>
</tr>
<thead/>
<tbody>
<tr>
<th rowspan="4">Locales</th>
<th>English</th>
<td>gregorian_en</td>
<td>persian_en</td>
<td>arabic_en</td>
<td>indian_en</td>
</tr>

<tr>
<th>Farsi</th>
<td>gregorian_fa</td>
<td>persian_fa</td>
<td>arabic_fa</td>
<td>indian_fa</td>
</tr>

<tr>
<th>Arabic</th>
<td>gregorian_ar</td>
<td>persian_ar</td>
<td>arabic_ar</td>
<td>indian_ar</td>
</tr>

<tr>
<th>Hindi</th>
<td>gregorian_hi</td>
<td>persian_hi</td>
<td>arabic_hi</td>
<td>indian_hi</td>
</tr>

</tbody>
</table>

<br>

<details>
  <summary>Examples</summary>

## 4-1- Persian Calendar, Farsi Locale

```javascript
var DateObject = require("date-object");
var persian = require("date-object/calendars/cjs/persian");
var persian_fa = require("date-object/locales/cjs/persian_fa");

var date = new DateObject({ calendar: persian, locale: persian_fa });

console.log(date.format()); //۱۴۰۰/۰۳/۲۰
```

## 4-2- Arabic Calendar, Arabic Locale

```javascript
var DateObject = require("date-object");
var arabic = require("date-object/calendars/cjs/arabic");
var arabic_ar = require("date-object/locales/cjs/arabic_ar");

var date = new DateObject({ calendar: arabic, locale: arabic_ar });

console.log(date.format()); //١٤٤٢/١٠/٢٩
```

## 4-3- Indiann Calendar, Hindi Locale

```javascript
var DateObject = require("date-object");
var indian = require("date-object/calendars/cjs/indian");
var indian_hi = require("date-object/locales/cjs/indian_hi");

var date = new DateObject({ calendar: indian, locale: indian_hi });

console.log(date.format()); //१९४३/०३/२०
```

</details>

<br>

# 5- Examples

## 5-1- new instance

### 5-1-1- String (year month day hour minute second millisecond meridiem)

```javascript
var DateObject = require("date-object");
var date = new DateObject("2020 8 21 11 55 36 100 am");

console.log(date.format("YYYY/MM/DD hh:mm:ss.SSS a")); //2020/08/21 11:55:36.100 am

date = new DateObject("2020/08/01");

console.log(date.format("YYYY/MM/DD hh:mm:ss.SSS a")); //2020/08/01 12:00:00.000 am
```

### 5-1-2- Number (unix time in milliseconds)

```javascript
var DateObject = require("date-object");
var date = new DateObject(1597994736000);

console.log(date.format("dddd DD MMMM @ hh:mm:ss.SSS a")); //Friday 21 August @ 11:55:36.000 am
```

### 5-1-3- JavaScript Date

```javascript
var DateObject = require("date-object");
var $date = new Date(2019, 8, 20);
var date = new DateObject($date);

console.log(date.format()); //2019/09/20
```

### 5-1-4- DateObject

```javascript
var DateObject = require("date-object");
var $date = new DateObject("2019/09/20");
var date = new DateObject($date);

console.log(date.format()); //2019/09/20
```

### 5-1-5- Object

#### 5-1-5-1-

```javascript
{
  date: String , Number(unix time in milliseconds), Date or DateObject, //default new Date()
  calendar: Calendar, //default gregorian
  locale: Locale, //default en
  format: String, //default `YYYY/MM/DD`
  ignoreList:Array//If the format contained words that should be ignored
}

```

```javascript
var DateObject = require("date-object");
var persian = require("date-object/calendars/cjs/persian");
var persian_fa = require("date-object/locales/cjs/persian_fa");
var persian_en = require("date-object/locales/cjs/persian_en");

var date = new DateObject({
  date: new Date(),
});

console.log(date.format()); //2020/08/21

date = new DateObject({
  date: new Date(),
  calendar: persian,
  locale: persian_fa,
});

console.log(date.format()); //۱۳۹۹/۰۵/۳۱

date = new DateObject({
  date: "31 Mordad 1399",
  format: "DD MMMM YYYY",
  calendar: persian,
  locale: persian_en,
});

console.log(date.format()); //31 Mordad 1399
```

#### 5-1-5-2-

```javascript
{
  year: Number,
  month: Number,
  day: Number,
  hour: Number, //default 0
  minute: Number, //default 0
  second: Number, //default 0
  millisecond: Number, //default 0
  calendar: Calendar, //default gregorian
  locale: Locale, //default en
  format: String, //default `YYYY/MM/DD`
  ignoreList:Array//If the format contained words that should be ignored
}

```

```javascript
var DateObject = require("date-object");
var persian = require("date-object/calendars/cjs/persian");
var persian_en = require("date-object/locales/cjs/persian_en");
var persian_fa = require("date-object/locales/cjs/persian_fa");

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

console.log(date.format()); //Friday 21 August 2020

date = new DateObject({
  year: 1399,
  month: 5,
  day: 31,
  calendar: persian,
  locale: persian_en,
  format: "dddd DD MMMM YYYY",
});

console.log(date.format()); //Jomeh 31 Mordad 1399

date = new DateObject({
  year: 1399,
  month: 5,
  day: 31,
  calendar: persian,
  locale: persian_fa,
  format: "dddd DD MMMM YYYY",
});

console.log(date.format()); //جمعه ۳۱ مرداد ۱۳۹۹
```

## 5-2- convert(calendar:Calendar, locale?:Locale)

If you use the convert method without argument, the date will be converted to Gregorian calendar.

The second argument (Locale) is optional.

```javascript
var DateObject = require("date-object");
var gregorian = require("date-object/calendars/cjs/gregorian");
var persian = require("date-object/calendars/cjs/persian");
var arabic = require("date-object/calendars/cjs/arabic");
var indian = require("date-object/calendars/cjs/indian");

var date = new DateObject();

console.log(date.format()); //2020/10/31

date.convert(persian);
console.log(date.format()); //1399/08/10

date.convert(arabic);
console.log(date.format()); //1442/03/14

date.convert(indian);
console.log(date.format()); //1942/08/09

date.convert(gregorian); //or date.convert()
console.log(date.format()); //2020/10/31
```

## 5-3- format(token:String)

default format is YYYY/MM/DD.
to see all format types click [here](#6--Formatting-Tokens)

```javascript
var DateObject = require("date-object");
var date = new DateObject();

consoel.log(date.format()); //2020/10/31
consoel.log(date.format("MM/DD/YYYY")); //10/31/2020
consoel.log(date.format("MMM/DD/YYYY HH:mm:ss")); //Oct/31/2020 18:17:28
consoel.log(date.format("dddd DD MMMM YYYY, hh:mm:ss A")); //Saturday 31 October 2020, 06:19:18 PM
consoel.log(date.format("ddd DD MMM YYYY, hh:mm a")); //Sat 31 Oct 2020, 06:20 pm
```

### formatting with ignore list:

```javascript
var DateObject = require("date-object");
var date = new DateObject();

console.log(
  date.format("hours:HH minutes:mm seconds:ss", ["hours", "minutes", "seconds"])
); //hours:12 minutes:22 seconds:40

console.log(date.format("it's HH o'clock", ["it's", "o'clock"])); //it's 12 o'clock

console.log(
  date.format(`DD MMMM at hh:mm ${date.hour >= 12 ? "Afternoon" : "Morning"}`, [
    "at",
    "Afternoon",
    "Morning",
  ])
); //11 November at 12:22 Afternoon
```

## 5-4- setter methods

```javascript
var DateObject = require("date-object");
var gregorian = require("date-object/calendars/cjs/gregorian");
var persian = require("date-object/calendars/cjs/persian");
var indian = require("date-object/calendars/cjs/indian");
var gregorian_en = require("date-object/locales/cjs/gregorian_en");
var persian_en = require("date-object/locales/cjs/persian_en");
var indian_en = require("date-object/locales/cjs/indian_en");

var date = new DateObject();

date
  .setCalendar(gregorian)
  .setFormat("YYYY-MM-DD HH:mm:ss.SSS")
  .setLocale(gregorian_en)
  .setYear(2020)
  .setMonth(9)
  .setDay(21)
  .setHour(12)
  .setMinute(20)
  .setSecond(14)
  .setMillisecond(200);

console.log(date.format()); //2020-09-21 12:20:14.200

date
  .setCalendar(persian)
  .setLocale(persian_en)
  .setYear(1399)
  .setMonth(9)
  .setDay(21)
  .setFormat("dddd DD MMMM YYYY");

console.log(date.format()); //Jom'eh 21 Azar 1399

date.setDate(new Date(2020, 9, 27)).setLocale(gregorian_en); //(calendar is set to gregorian)

console.log(date.format()); //Tuesday 27 October 2020

date.setDate(
  new DateObject({
    calendar: indian,
    locale: indian_en,
    year: 1942,
    month: 8,
    day: 5,
  })
); //format is set based on given DateObject (default:YYYY/MM/DD)

console.log(date.format()); //1942/08/05
```

## 5-5- get and set

```javascript
var DateObject = require("date-object");
var date = new DateObject();

console.log(date.format()); //2020/08/21

date.year += 2;
date.month += 2;
date.day += 2;
date.hour += 2;
date.minute += 2;
date.second += 2;
date.millisecond += 2;

console.log(date.format()); //2022/10/23

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

var { year, month, weekDay, day } = date;

console.log(`${weekDay.name} ${year}/${month}/${day}`); //Sunday 2022/10/23

date.year = 2020;
date.month = 8;
date.day = 21;

date.isLeap; //true
date.isValid; //true
date.isUTC; //false
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
date.unix; //1597951800 (unix time in seconds)

date.weekDays; // array [{ name: 'Sunday', shortName: 'Sun', ...}]
date.months; //array [{ name: 'January', shortName: 'Jan', ...}]
date.leaps; //array [4,   8,  12,  16,  20,...]

date.calendar.name; //gregorian
```

## 5-6- parse(date:String)

Remember that parsing date is based on the format you set

```javascript
var DateObject = require("date-object");
var persian = require("date-object/calendars/cjs/persian");
var persian_en = require("date-object/locales/cjs/persian_en");
var date = new DateObject();

date._format = "dddd DD MMMM YYYY";

date.parse("Monday 24 August 2020");
console.log(date.format("YYYY/MM/DD")); //2020/08/24

date.parse("Friday 07 August 2020");
console.log(date.format("YYYY-MM-DD")); //2020-08-07

date
  .setCalendar(persian)
  .setLocale(persian_en)
  .setFormat("YYYY/MM/DD")
  .parse("1399/06/03");
console.log(date.format()); //1399/06/03

date.setFormat("YYYY/MM/DD HH:mm").parse("1399/06/03 12:32");
console.log(date.format("dddd DD MMMM @ hh:mm a")); //Doshanbeh 03 Shahrivar @ 12:32 pm
```

## 5-7- getValue

```javascript
var Dateobject = require("date-object");
var arabic_ar = require("date-object/locales/cjs/arabic_ar.js");

var date = new DateObject({
  date: "1442/01/01",
  calendar: arabic,
  locale: arabic_ar,
});

console.log(date.getValue("M")); //1
console.log(date.format("M")); //١

console.log(typeof date.getValue("D")); //number
console.log(typeof date.format("D")); //string

console.log(Number(date.getValue("YYYY"))); //1442
console.log(Number(date.format("YYYY"))); //NaN
```

## 5-8- add(duration:Number or String,type:String)

<table>
  <tr>
    <th colspan="3">Types</td>
  </tr>
  <tr>
    <td>years</td>
    <td>year</td>
    <td>y</td>
  </tr>
  <tr>
    <td>months</td>
    <td>month</td>
    <td>M</td>
  </tr>
  <tr>
    <td>days</td>
    <td>day</td>
    <td>d</td>
  </tr>
  <tr>
    <td>hours</td>
    <td>hour</td>
    <td>h</td>
  </tr>
  <tr>
    <td>minutes</td>
    <td>minute</td>
    <td>m</td>
  </tr>
  <tr>
    <td>seconds</td>
    <td>second</td>
    <td>s</td>
  </tr>
  <tr>
    <td>milliseconds</td>
    <td>millisecond</td>
    <td>ms</td>
  </tr>
</table>

```javascript
var DateObject = require("date-object");
var date = new DateObject("2020/10/07 5:35:24 pm");

date.setFormat("YYYY/MM/DD hh:mm:ss.SSS");

console.log(date.add(2, "years").format()); //2022/10/07 05:35:24.000
console.log(date.add("1", "month").format()); //2022/11/07 05:35:24.000
console.log(date.add(3, "d").format()); //2022/11/10 05:35:24.000
console.log(date.add(4, "hours").format()); //2022/11/10 09:35:24.000
console.log(date.add(1, "minute").format()); //2022/11/10 09:36:24.000
console.log(date.add("20", "s").format()); //2022/11/10 09:36:44.000
console.log(date.add(100, "milliseconds").format()); //2022/11/10 09:36:44.100
```

## 5-9- subtract(duration:Number or String,type:String)

<table>
  <tr>
    <th colspan="3">Types</td>
  </tr>
  <tr>
    <td>years</td>
    <td>year</td>
    <td>y</td>
  </tr>
  <tr>
    <td>months</td>
    <td>month</td>
    <td>M</td>
  </tr>
  <tr>
    <td>days</td>
    <td>day</td>
    <td>d</td>
  </tr>
  <tr>
    <td>hours</td>
    <td>hour</td>
    <td>h</td>
  </tr>
  <tr>
    <td>minutes</td>
    <td>minute</td>
    <td>m</td>
  </tr>
  <tr>
    <td>seconds</td>
    <td>second</td>
    <td>s</td>
  </tr>
  <tr>
    <td>milliseconds</td>
    <td>millisecond</td>
    <td>ms</td>
  </tr>
</table>

```javascript
var DateObject = require("date-object");
var yesterday = new DateObject().subtract(1, "day");
```

## 5-10- set method

### 5-10-1 set(key:String,value:Any)

```javascript
var DateObject = require("date-object");
var indian = require("date-object/calendars/cjs/indian");
var persian = require("date-object/calendars/cjs/persian");
var indian_hi = require("date-object/locales/cjs/indian_hi");
var persian_en = require("date-object/locales/cjs/persian_en");
var date = new DateObject(); //2020/10/31

console.log(date.set("year", 2021)); //2021/10/31
console.log(date.set("month", 1)); //2021/01/31
console.log(date.set("day", 7)); //2021/01/07
console.log(date.set("format", "MM/DD/YYYY")); //01/07/2021
console.log(date.set("calendar", indian)); //10/17/1942
console.log(date.set("locale", indian_hi)); //१०/१७/१९४२
console.log(date.set("date", new Date())); //2020/10/31 (calendar is set to gregorian)
console.log(
  date.set("date", new DateObject({ calendar: persian, locale: persian_en }))
); //1399/08/10 (calendar & locale is set to given values)
```

### 5-10-2 set(object)

```javascript
var DateObject = require("date-object/index");
var persian = require("date-object/calendars/cjs/persian");
var gregorian = require("date-object/calendars/cjs/gregorian");
var persian_en = require("date-object/locales/cjs/persian_en");
var gregorian_en = require("date-object/locales/cjs/gregorian_en");

var date = new DateObject(); //2020/10/31

console.log(
  date
    .set({ calendar: persian, locale: persian_en, format: "dddd DD MMMM YYYY" })
    .format()
); //Shanbeh 10 Aban 1399

console.log(
  date
    .set({
      calendar: gregorian,
      locale: gregorian_en,
      year: 2020,
      month: 11,
      day: 12,
    })
    .format()
); //Saturday 12 December 2020

console.log(date.set(new DateObject().toObject()).format()); //2020/10/31

console.log(
  date.set({ format: "Date:MM/DD/YYYY", ignoreList: ["Date"] }).format()
); //Date:10/31/2020
```

## 5-11- toUTC()

```javascript
var DateObject = require("date-object");
var arabic = require("date-object/calendars/cjs/arabic");
var gregorian = require("date-object/calendars/cjs/gregorian");
var arabic_en = require("date-object/locales/cjs/arabic_en");
var gregorian_en = require("date-object/locales/cjs/gregorian_en");
var date = new Date(); //Wed Oct 14 2020 11:12:18 GMT+0330

var dateObject = new DateObject({
  date,
  calendar: arabic,
  locale: arabic_en,
  format: "ddd, DD MMM YYYY HH:mm:ss",
});

console.log(dateObject.format()); //Arb, 26 Sa 1442 11:12:18

console.log(`
dateUTC      : ${date.toUTCString()}
arabicUTC    : ${dateObject.toUTC().toString()}
gregorianUTC : ${dateObject.convert(gregorian, gregorian_en).toString()}
`);

/**
 * dateUTC      : Wed, 14 Oct 2020 07:42:18 GMT
 * arabicUTC    : Arb, 26 Sa 1442 07:42:18
 * gregorianUTC : Wed, 14 Oct 2020 07:42:18
 */
```

## 5-12- custom months, week days & digits

See the example below in case you want to use your personal data instead of default months, week days & digits

```javascript
var DateObject = require("date-object");
var date = new DateObject();

console.log(date.format("MMMM MMM")); //November Nov
console.log(date.format("dddd ddd")); //Monday Mon
console.log(date.format("D")); //2

date.months = [
  ["jan", "j"], //[["name","shortName"], ... ]
  ["feb", "f"],
  ["mar", "m"],
  ["apr", "a"],
  ["may", "m"],
  ["jun", "j"],
  ["jul", "j"],
  ["aug", "a"],
  ["sep", "s"],
  ["oct", "o"],
  ["nov", "n"],
  ["dec", "d"],
];

date.weekDays = [
  ["su", "s"], //[["name","shortName"], ... ]
  ["mo", "m"],
  ["tu", "t"],
  ["we", "w"],
  ["th", "t"],
  ["fr", "f"],
  ["sa", "s"],
];

/**
 * This is just a test to display digits.
 * The Greek number system does not work like this.
 */
date.digits = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"];

console.log(date.format("MMMM MMM")); //nov n
console.log(date.format("dddd ddd")); //mo m
console.log(date.format("D")); //II

console.log(date.month);

/**
 *{
 * name: 'nov',
 * shortName: 'n',
 * length: 30,
 * index: 10,
 * number: 11,
 * toString: [Function (anonymous)]
 * valueOf: [Function: valueOf]
 *}
 */

console.log(date.weekDay);

/**
 *{
 * name: 'mo',
 * shortName: 'm'
 * index: 1,
 * number: 2,
 * toString: [Function: toString],
 * valueOf: [Function: valueOf]
 *}
 */

console.log(date.digits);

/**
 * [
 *  '',    'I',   'II',
 *  'III', 'IV',  'V',
 *  'VI',  'VII', 'VIII',
 *  'IX'
 * ]
 */
```

You can use `date.setMonths(months).setWeekDays(weekDays).setDigits(digits)` as well

## 5-13- other methods

```javascript
var DateObject = require("date-object");
var date = new DateObject();

console.log(date.toFirstOfWeek().format()); //2020/08/16
console.log(date.toFirstOfMonth().format()); //2020/08/01
console.log(date.toFirstOfYear().format()); //2020/01/01
console.log(date.toFirstWeekOfYear().format()); //2020/01/05
console.log(date.toLastOfMonth().format()); //2020/01/31
console.log(date.toLastOfWeek().format()); //2020/02/01
console.log(date.toLastOfYear().format()); //2020/12/31
console.log(date.toLastWeekOfYear().format()); //2020/12/27

console.log(date.toString()); //2020/12/27
console.log(date.toDate()); //2020-12-27T07:38:34.724Z
console.log(date.toUnix()); //1609054714 (unix time in seconds)
console.log(date.toJulianDay()); //2459210
console.log(date.toObject());
/**
 *{
 *  year: 2020,
 *  month: {
 *    name: 'December',
 *    shortName: 'Dec',
 *    length: 31,
 *    index: 11,
 *    number: 12,
 *    toString: [Function: toString],
 *    valueOf: [Function: valueOf]
 *  },
 *  day: 27,
 *  weekDay: {
 *    name: 'Sunday',
 *    shortName: 'Sun',
 *    index: 0,
 *    number: 1,
 *    toString: [Function: toString],
 *    valueOf: [Function: valueOf]
 *  },
 *  hour: 11,
 *  minute: 8,
 *  second: 34,
 *  millisecond: 724,
 *  weekOfYear: 52,
 *  dayOfYear: 362,
 *  daysLeft: 4,
 *  calendar: {
 *    name: 'gregorian',
 *    startYear: 1,
 *    yearLength: 365,
 *    epoch: 1721424,
 *    century: 20,
 *    weekDaysIndex: [
 *      0, 1, 2, 3,
 *      4, 5, 6
 *    ],
 *    getMonthLengths: [Function: getMonthLengths],
 *    isLeap: [Function: isLeap],
 *    getLeaps: [Function: getLeaps],
 *    getDayOfYear: [Function: getDayOfYear],
 *    getAllDays: [Function: getAllDays],
 *    leapsLength: [Function: leapsLength],
 *    guessYear: [Function: guessYear]
 *  },
 *  locale: {
 *    months: [
 *      [Array], [Array],
 *      [Array], [Array],
 *      [Array], [Array],
 *      [Array], [Array],
 *      [Array], [Array],
 *      [Array], [Array]
 *    ],
 *    weekDays: [
 *      [Array], [Array],
 *      [Array], [Array],
 *      [Array], [Array],
 *      [Array]
 *    ],
 *    digits: [
 *      '0', '1', '2', '3',
 *      '4', '5', '6', '7',
 *      '8', '9'
 *    ],
 *    meridiems: [ [Array], [Array] ]
 *  },
 *  format: 'YYYY/MM/DD',
 *  ignoreList: []
 *}
 */
console.log(date.toJSON()); //1609054714724

console.log(JSON.stringify({ date })); //{"date":1609054714724}
console.log(new DateObject(date.toJSON()).format()); //2020/12/27
```

## 5-14 valueOf()

returns unix time in milliseconds

```javascript
var DateObject = require("date-object");

var persian_calendar = require("date-object/calendars/cjs/persian");
var arabic_calendar = require("date-object/calendars/cjs/arabic");
var indian_calendar = require("date-object/calendars/cjs/indian");

var gregorian = new DateObject();
var persian = new DateObject({ date: gregorian, calendar: persian_calendar });
var arabic = new DateObject({ date: gregorian, calendar: arabic_calendar });
var indian = new DateObject({ date: gregorian, calendar: indian_calendar });

console.log(gregorian.valueOf(), gregorian.format()); //1604824018304 2020/11/08
console.log(persian.valueOf(), persian.format()); //1604824018304 1399/08/18
console.log(indian.valueOf(), indian.format()); //1604824018304 1942/08/17
console.log(arabic.valueOf(), arabic.format()); //1604824018304 1442/03/22

console.log(persian - gregorian === 0); //true
```

## 5-15- using calendars, format & locales

```javascript
var DateObject = require("date-object/index");
var gregorian = require("date-object/calendars/cjs/gregorian");
var persian = require("date-object/calendars/cjs/persian");
var arabic = require("date-object/calendars/cjs/arabic");
var persian_fa = require("date-object/locales/cjs/persian_fa");
var gregorian_en = require("date-object/locales/cjs/gregorian_en");

var date = new DateObject({
  calendar: gregorian,
  format: "dddd DD MMMM",
});

console.log(date.format()); //Friday 21 August

date.calendar = persian;
date.locale = persian_fa; //جمعه 31 مرداد
console.log(date.format());

date._format = "YY/MM/DD";
console.log(date.format()); //۹۹/۰۵/۳۱

date.setCalendar(gregorian).setLocale(gregorian_en);
console.log(date.format()); //20/08/21

date = new DateObject(new Date());

console.log(date.convert(persian).format()); //1399/05/31
console.log(date.convert(arabic).format()); //1442/01/02
```

# 6- Formatting Tokens

| Token |            Example            |         Description          | Availability (Parse /Format) |
| ----- | :---------------------------: | :--------------------------: | ---------------------------- |
| YYYY  |             2020              |          full year           | both                         |
| YY    |              20               |        2 digits year         | both                         |
| MMMM  |           December            |          month name          | both                         |
| MMM   |              Dec              |       month short name       | both                         |
| MM    |        03, 09, 10, ...        |    2 digits month number     | both                         |
| M     |         3, 9, 10, ...         |         month number         | both                         |
| DDDD  |              09               |         day of year          | format                       |
| DDD   |               9               |         day of year          | format                       |
| DD    |      03, 09, 10, 17, ...      |    2 digits day of month     | both                         |
| D     |         3, 9 ,10, 17          |         day of month         | both                         |
| WW    |      01, 03, 24, 33, ...      |         week of year         | format                       |
| W     |       1, 3, 24. 33, ...       |         week of year         | format                       |
| dddd  | Saturday, Sunday, Monday, ... |        week day name         | format                       |
| ddd   |      Sat, Sun, Mon, ...       |     week day short name      | format                       |
| dd    |         01,02,...,07          |   2 digits week day number   | format                       |
| d     |           1,2,...,7           |       week day number        | format                       |
| HH    |      03, 09, 10, 17,...       | 2 digits hour (24 hour mode) | both                         |
| H     |       3, 9, 10, 17,...        |     hour (24 hour mode)      | both                         |
| hh    |      03, 09, 10, 17,...       | 2 digits hour (12 hour mode) | both                         |
| h     |       3, 9, 10, 17,...        |     hour (12 hour mode)      | both                         |
| mm    |      03, 09, 10, 17,...       |       2 digits minute        | both                         |
| m     |       3, 9, 10, 17,...        |            minute            | both                         |
| ss    |      03, 09, 10, 17,...       |       2 digits second        | both                         |
| s     |       3, 9, 10, 17,...        |            second            | both                         |
| SSS   |              100              |     3 digits millisecond     | both                         |
| SS    |              10               |     2 digits millisecond     | both                         |
| S     |               1               |     1 digit millisecond      | both                         |
| A     |              AM               |           meridiem           | both                         |
| a     |              am               |      meridiem lowercase      | both                         |
