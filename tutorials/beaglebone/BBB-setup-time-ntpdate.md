#Setting time on a Beaglebone Black

## Set current time

`ntpdate` is claimed to be depriciated but still works:

```ntpdate -b -s -u pool.ntp.org```

This will change to the current time of your set location. The default timezone is UTC.

This does not need the NTP service installed just grabs the time from the ntp network.

`ntpdate` option explanations:

`-b`
    Force the time to be stepped using the settimeofday() system call, rather than slewed (default) using the adjtime() system call. This option should be used when called from a startup file at boot time.
    
`-s`
    Divert logging output from the standard output (default) to the system syslog facility. This is designed primarily for convenience of cron scripts.
    
`-t` timeout
    Specify the maximum time waiting for a server response as the value timeout, in seconds and fraction. The value is is rounded to a multiple of 0.2 seconds. The default is 1 second, a value suitable for polling across a LAN.
    
## Set timezone
