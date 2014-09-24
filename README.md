# rbcal

A Unix cal/ncal command replacement, written in Ruby. 

## Features

Doesn't support all the options in the stock Unix/Linux/OS X versions,
such as handling Julian calendars, etc. However, it does have a few
additional features:

 * displaying an arbitrary month range (currently only within the same year)
 * always show week numbers to the left
 * use ANSI colors to highlight the current date, public holidays,
   and other "notable" dates, like daylight saving time changes
 * support for configuring your own list of dates to highlight via a
   configuration file (~/.rbcal)

The public holidays etc. are currently only shown based on the rules
for the *Finnish* calendar; there are going to be some differences
in other countries.


## Usage Examples

    rbcal               # display current month
	rbcal 05 2014       # display May 2014
	rbcal 10-12 2013    # display Oct-Dec 2013
	rbcal 7-10          # display July-October for current year
    rbcal 2015          # display full year, Jan-Dec 2015


## Installing

Requires Ruby 1.9.x/2.x - does *NOT* work with Ruby 1.8.7. The exact
version cutoff hasn't been determined. The reason is mainly because
the program utilizes the `Date` stdlib class heavily, and some of the
features used aren't available in 1.8.7; since it has been
end-of-lifed already, I have no interest in doing the workarounds to
support it. Also, recent versions not tested with 1.9.x either,
and 1.9.3 will reach end of support in 2015 as well, so no plans to
put effort into that either.

There is a simple shell script to install the program for use,
`install`. However it's very basic and just copies the main script
into `~/bin/rbcal` and the example configuration file into `~/.rbcal`.

The install script isn't extremely robust, but it does check that the
`~/bin` directory exists and doesn't overwrite a previous
configuration file (`~/.rbcal`). You can also easily do the same thing
manually and choose where to put the script, what to name it, whether
to include the config file or not, etc.

## The Configuration File

The `~/.rbcal` configuration file is a simple text file that lists dates
that should be highlighted. The dates are listed each on their own row
with the format `day month [year]`, meaning that the year is optional,
and if it's not provided, the date is highlighted for all
years. There's no annotation for the dates, as in the calendar display
there's no room for showing the reason for highlighting each day. This
feature isn't meant to be a replacement for a full-blown calendar app
with appointments, alerts etc., just reminders that certain dates are
noteworthy.


## Future Development

Possible enhancements, no concrete implementation plan or schedule at
the moment: 

 * displaying a month range across different years,
   such as 11-2013 - 03-2014
 * options to customize color output or turn it off completely
 * other output formatting options, e.g. specifying the number of
   columns, leaving out week numbers, ...


## Copyright & License

(c) Ville Siltanen 2013-2014; MIT license.
