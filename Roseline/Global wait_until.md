# Global wait_until
*Roseline QoT Stack*


### Introduce dummy system calls in LKM

Export System call table and introduce empty system calls for the following in loadable kernel module.

```
timeline_wait_until(char * tl_name, timespec expiry);
timeline_register(char * tl_name, ???)
timeline_create(char * tl_name)
```