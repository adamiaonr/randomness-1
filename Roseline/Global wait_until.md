# Global wait_until
*Roseline QoT Stack*


### Introduce dummy system calls in LKM

Export system call table and introduce empty system calls for the following in loadable kernel module.

```
timeline_gettime();
timeline_wait_until(char * tl_name, timespec expiry);
timeline_register(char * tl_name, timeline_t *timeline);
timeline_create(char * tl_name, timeline_t *timeline);
```

**Note:** The timeline_t object defines properties of the timeline.

### Gain access to a separate timer

Enable a timer (preferably DM TIMER4 or similar; capable of external inputs).

Introduce a system call to set off an interrupt off this timer

### Timeline engine

*Based off of UCLA engine*

Implement a timeline datastructure with kernel relevant information. Create a timeline management system.

### QoT Features

Based on current drift estimates, perform default recomputations of the schedule at suggested periods

### Update from POSIX-clock

Timer updates 

