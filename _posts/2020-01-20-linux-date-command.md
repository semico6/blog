---
layout: post
title: "Linux date Command"
---

`$ date `

Let's go through the help page for `$ date --help`. 

```
Usage: date [OPTION]... [+FORMAT]
  or:  date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]
Display the current time in the given FORMAT, or set the system date.

Mandatory arguments to long options are mandatory for short options too.
  -d, --date=STRING          display time described by STRING, not 'now'
      --debug                annotate the parsed date,
                              and warn about questionable usage to stderr
  -f, --file=DATEFILE        like --date; once for each line of DATEFILE
  -I[FMT], --iso-8601[=FMT]  output date/time in ISO 8601 format.
                               FMT='date' for date only (the default),
                               'hours', 'minutes', 'seconds', or 'ns'
                               for date and time to the indicated precision.
                               Example: 2006-08-14T02:34:56-06:00
  -R, --rfc-email            output date and time in RFC 5322 format.
                               Example: Mon, 14 Aug 2006 02:34:56 -0600
      --rfc-3339=FMT         output date/time in RFC 3339 format.
                               FMT='date', 'seconds', or 'ns'
                               for date and time to the indicated precision.
                               Example: 2006-08-14 02:34:56-06:00
  -r, --reference=FILE       display the last modification time of FILE
  -s, --set=STRING           set time described by STRING
  -u, --utc, --universal     print or set Coordinated Universal Time (UTC)
      --help     display this help and exit
      --version  output version information and exit

FORMAT controls the output.  Interpreted sequences are:

  %%   a literal %
  %a   locale's abbreviated weekday name (e.g., Sun)
  %A   locale's full weekday name (e.g., Sunday)
  %b   locale's abbreviated month name (e.g., Jan)
  %B   locale's full month name (e.g., January)
  %c   locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
  %C   century; like %Y, except omit last two digits (e.g., 20)
  %d   day of month (e.g., 01)
  %D   date; same as %m/%d/%y
  %e   day of month, space padded; same as %_d
  %F   full date; same as %Y-%m-%d
  %g   last two digits of year of ISO week number (see %G)
  %G   year of ISO week number (see %V); normally useful only with %V
  %h   same as %b
  %H   hour (00..23)
  %I   hour (01..12)
  %j   day of year (001..366)
  %k   hour, space padded ( 0..23); same as %_H
  %l   hour, space padded ( 1..12); same as %_I
  %m   month (01..12)
  %M   minute (00..59)
  %n   a newline
  %N   nanoseconds (000000000..999999999)
  %p   locale's equivalent of either AM or PM; blank if not known
  %P   like %p, but lower case
  %q   quarter of year (1..4)
  %r   locale's 12-hour clock time (e.g., 11:11:04 PM)
  %R   24-hour hour and minute; same as %H:%M
  %s   seconds since 1970-01-01 00:00:00 UTC
  %S   second (00..60)
  %t   a tab
  %T   time; same as %H:%M:%S
  %u   day of week (1..7); 1 is Monday
  %U   week number of year, with Sunday as first day of week (00..53)
  %V   ISO week number, with Monday as first day of week (01..53)
  %w   day of week (0..6); 0 is Sunday
  %W   week number of year, with Monday as first day of week (00..53)
  %x   locale's date representation (e.g., 12/31/99)
  %X   locale's time representation (e.g., 23:13:48)
  %y   last two digits of year (00..99)
  %Y   year
  %z   +hhmm numeric time zone (e.g., -0400)
  %:z  +hh:mm numeric time zone (e.g., -04:00)
  %::z  +hh:mm:ss numeric time zone (e.g., -04:00:00)
  %:::z  numeric time zone with : to necessary precision (e.g., -04, +05:30)
  %Z   alphabetic time zone abbreviation (e.g., EDT)

By default, date pads numeric fields with zeroes.
The following optional flags may follow '%':

  -  (hyphen) do not pad the field
  _  (underscore) pad with spaces
  0  (zero) pad with zeros
  ^  use upper case if possible
  #  use opposite case if possible

After any flags comes an optional field width, as a decimal number;
then an optional modifier, which is either
E to use the locale's alternate representations if available, or
O to use the locale's alternate numeric symbols if available.

Examples:
Convert seconds since the epoch (1970-01-01 UTC) to a date
  $ date --date='@2147483647'

Show the time on the west coast of the US (use tzselect(1) to find TZ)
  $ TZ='America/Los_Angeles' date

Show the local time for 9AM next Friday on the west coast of the US
  $ date --date='TZ="America/Los_Angeles" 09:00 next Fri'

GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
Full documentation at: <http://www.gnu.org/software/coreutils/date>
or available locally via: info '(coreutils) date invocation'
```

This is the default format when you type in the  `$ date ` command and press Enter:
`Mon Jan 20 13:52:25 EST 2020`

There are a few optional formats you can choose. 

- ISO 8601 displays the date like: `2020-01-20T14:01:50-05:00`.
  - To format the date in this manner, type: `$ date -Iseconds`.
- RFC 5322 displays the date like: `Mon, 20 Jan 2020 14:03:11 -0500`.
  - To format the date in this manner, type: `$ date -R` 
- RFC 3339 displays the date like: `2020-01-20 14:04:49-05:00`.
  - To formate the date in this manner, type: `$ date --rfc-3339=seconds`.
- Coordinated Universal Time (UTC) displays the date like: `Mon Jan 20 19:05:58 UTC 2020`.
  - To view the UTC date, type: `$ date -u`.
- Custom display, for example: `Monday, January 20 2020 02:15pm EST`.
  - To view the custom date this way, type: `$ date "+%A, %B %d %Y %I:%M%P %Z"`

## Other uses of the date command

- Display the date from a string
  - `$ date --date="01/20/2020"` will display `Mon Jan 20 00:00:00 EST 2020`
- Display past dates
  - `$ date --date="yesterday"` will display `Sun Jan 19 14:31:00 EST 2020`
  - `$ date --date="53 days ago"` will display `Thu Nov 28 14:31:59 EST 2019`
- Display dates from a file (create a file called `dates.txt` and add Dec 21 2019 Jan 1 2020 on separate lines)
  - `$ date --file=dates.txt` will display `Sat Dec 21 00:00:00 EST 2019` on one line and `Wed Jan  1 00:00:00 EST 2020` on another.
- Display a file's last modification time
  - `$ date --reference dates.txt` will display `Mon Jan 20 14:34:49 EST 2020`
- Set the date and time
  - `sudo date -s "Tue Feb 21 12:00:00 PST 2021"` (note the `sudo`) will display `Sun Feb 21 15:00:00 EST 2021` (Don't forget to put it back to the right time!)
- Display the week number
  - `$ date +%W` will display `03`
- Display the day of the year
  - `$ date +%j` will display `020`
- Use the date command within a script or report
  - <pre><code>`$ echo "The date is" `date +%A` "generated at" `date +%T`</code></pre> will display <pre><code>The date is Monday generated at 16:46:35</code></pre>
- Set a custom default format for the date command
  - `$ sudo nano ./.bashrc` to edit `date` for all users, arrow down to the alias's section, and add `alias date='date "+%A, %B %d %Y %I:%M%P %Z"'` above the `fi` (or any format you prefer)
  - to apply the change, type `source ~/.bashrc`, then try running the `$ date` command again. The result will display: `Monday, January 20 2020 05:06pm EST`
