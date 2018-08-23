# 0.5.0-dev

- Support a package-directory-free environment. In Dart 1.19, timezone is now
  compatible with `pub get --no-packages-dir`.
- **Breaking:** Remove initializeTimeZoneSync method; it is incompatible with
  the async method for resolving package URIs.
- Fix all strong mode _errors_ (thanks @har79).
- Add microsecond support (thanks @har79).
- Improve interaction between TZDateTime and native DateTime (thanks @har79).
- Fix TimeZone's `==` (thanks @har79).
- Many new dartdoc comments (thanks @har79).
- Time zone database updated to 2018c. For your convenience here are the
  announcements for [2015c], [2015d], [2015e], [2015f], [2015g], [2016a],
  [2016b], [2016c], [2016d], [2016e], [2016f], [2016g], [2016h], [2016i],
  [2017a], [2017b], [2017c], and [2018c].

[2015c]: http://mm.icann.org/pipermail/tz-announce/2015-April/000030.html
[2015d]: http://mm.icann.org/pipermail/tz-announce/2015-April/000031.html
[2015e]: http://mm.icann.org/pipermail/tz-announce/2015-June/000032.html
[2015f]: http://mm.icann.org/pipermail/tz-announce/2015-August/000033.html
[2015g]: http://mm.icann.org/pipermail/tz-announce/2015-October/000034.html
[2016a]: http://mm.icann.org/pipermail/tz-announce/2016-January/000035.html
[2016b]: http://mm.icann.org/pipermail/tz-announce/2016-March/000036.html
[2016c]: http://mm.icann.org/pipermail/tz-announce/2016-March/000037.html
[2016d]: http://mm.icann.org/pipermail/tz-announce/2016-April/000038.html
[2016e]: http://mm.icann.org/pipermail/tz-announce/2016-June/000039.html
[2016f]: http://mm.icann.org/pipermail/tz-announce/2016-July/000040.html
[2016g]: http://mm.icann.org/pipermail/tz-announce/2016-September/000041.html
[2016h]: http://mm.icann.org/pipermail/tz-announce/2016-October/000042.html
[2016i]: http://mm.icann.org/pipermail/tz-announce/2016-November/000043.html
[2017a]: http://mm.icann.org/pipermail/tz-announce/2017-February/000045.html
[2017b]: http://mm.icann.org/pipermail/tz-announce/2017-March/000046.html
[2017c]: http://mm.icann.org/pipermail/tz-announce/2017-October/000047.html
[2018c]: http://mm.icann.org/pipermail/tz-announce/2018-January/000048.html

# 0.4.3

- Fix Dart 1.14 incompatibility further.

# 0.4.2

- Bad pub publish. Ignore.

# 0.4.1

- Fix Dart 1.14 incompatibility with packageRoot returning null.

# 0.4.0

- Remove usage of tuple package.
- Upgrade unittest package to test.
- Fix database URL for "latest" database.
- Add tool/dartfmt for formatting source.

# 0.3.1

- `generate_data_subset` script is removed. It will be available as a
  separate package.

# 0.3.0

- Time zone database updated to 2015b.
- Removed local location detection heuristics (didn't worked properly).
  Local location is initialized with UTC location by default, use
  `setLocalLocation` to change local location.
- Time zone database format is changed; data is aligned.

# 0.2.5

- Fixed bug with String formatting (invalid offsets for minutes).

# 0.2.4

- Fixed bug with Calendar-type constructor.

# 0.2.3

- Added `initializeTimeZoneSync` function for standalone environments.
- Fixed bug with script path on Windows.

# 0.2.2

- TimeZone database updated to "2014j".
- "args" and "path" moved from dev dependencies to dependencies.

# 0.2.1

- `tzfile` library renamed to `tzdata`.
- Added `zone1970.tab` parser to `tzdata` library.
- Removed `package:collection` dependency.
