# TimeZone

This package provides time zone database and time zone aware `DateTime`
object.

Current Time Zone database version:
[2017c](http://www.iana.org/time-zones/repository/releases/tzcode2017c.tar.gz)

## Initialization

TimeZone objects require time zone data, so the first step is to load
one of our [time zone databases](#databases).

We are providing two different APIs for browsers and standalone
environments.

### Initialization for browser environment

Import `package:timezone/browser.dart` library and run async function
`Future initializeTimeZone([String path])`.

```dart
import 'package:timezone/browser.dart';

initializeTimeZone().then((_) {
  final detroit = getLocation('America/Detroit');
  final now = new TZDateTime.now(detroit);
});
```

### Initialization for standalone environment

Import `package:timezone/standalone.dart` library and run async function
`Future initializeTimeZone([String path])`.

```dart
import 'package:timezone/standalone.dart';

initializeTimeZone().then((_) {
  final detroit = getLocation('America/Detroit');
  final now = new TZDateTime.now(detroit);
});
```

### Local Location

By default, when library is initialized, local location will be `UTC`.

To overwrite local location you can use `setLocalLocation(Location
location)` function.

```dart
initializeTimeZone().then((_) {
  final detroit = getLocation('America/Detroit');
  setLocalLocation(detroit);
});
```

## API

### Location

> Each location in the database represents a national region where all
> clocks keeping local time have agreed since 1970. Locations are
> identified by continent or ocean and then by the name of the
> location, which is typically the largest city within the region. For
> example, America/New_York represents most of the US eastern time
> zone; America/Phoenix represents most of Arizona, which uses
> mountain time without daylight saving time (DST); America/Detroit
> represents most of Michigan, which uses eastern time but with
> different DST rules in 1975; and other entries represent smaller
> regions like Starke County, Indiana, which switched from central to
> eastern time in 1991 and switched back in 2006.
>
> [The tz database](http://www.twinsun.com/tz/tz-link.htm)

#### Get location by Olsen timezone ID

```dart
final detroit = getLocation('America/Detroit');
```

We don't provide any functions to get locations by timezone
abbreviations because of the ambiguities.

> Alphabetic time zone abbreviations should not be used as unique
> identifiers for UTC offsets as they are ambiguous in practice. For
> example, "EST" denotes 5 hours behind UTC in English-speaking North
> America, but it denotes 10 or 11 hours ahead of UTC in Australia;
> and French-speaking North Americans prefer "HNE" to "EST".
>
> [The tz database](http://www.twinsun.com/tz/tz-link.htm)

### TimeZone

TimeZone object represents time zone and contains offset, dst flag,
and name in the abbreviated form.

```dart
final timeInUtc = new DateTime.utc(1995, 1, 1);
final timeZone = detroit.timeZone(timeInUtc.millisecondsSinceEpoch);
```

### TimeZone aware DateTime

`TZDateTime` object implements standard `DateTime` interface and
contains information about location and time zone.

```dart
final date = new TZDateTime(detroit, 2014, 11, 17);
```

#### Converting DateTimes between Time Zones

To convert between time zones, just create a new `TZDateTime` object
using `from` constructor and pass `Location` and `DateTime` to the
constructor.

```dart
final localTime = new DateTime(2010, 1, 1);
final detroitTime = new TZDateTime.from(time, detroit);
```

This constructor supports any objects that implements `DateTime`
interface, so you can pass native `DateTime` object or ours
`TZDateTime`.

## <a name="databases"></a> Time Zone databases

We are using [IANA Time Zone Database](http://www.iana.org/time-zones)
to build our databases.

We are currently building three different database variants:

- default (doesn't contain deprecated and historical zones with some
  exceptions like US/Eastern). 308kb/72kb gzip
- all (contains all data from the
  [IANA Time Zone Database](http://www.iana.org/time-zones)). 370kb/100kb
  gzip
- 2010-2020 (default database that contains historical data from 2010
  until 2020). 71kb/16kb gzip

### Updating Time Zone databases

Script for updating Time Zone database, it will automatically download
[the IANA Time Zone Database](http://www.iana.org/time-zones) and
compile into our native format.

```sh
$ pub run tool/get -s 2017c
```

Argument `-s` is for specifying source version.