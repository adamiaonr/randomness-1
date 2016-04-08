# Sync NTP time on linux

## Set timezone

## get time from server

```
ntpdte -b 0.pool.ntp.org
```
- `-b` steps the current time instead of skewing
- `-u` use unpriviledged port (no suitable server is founddue to blocked ports)
- server options:
	1. `us.pool.ntp.org`
	2. `0.pool.ntp.org`
