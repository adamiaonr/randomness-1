# NTFS mount on OSX with RW

## Modify fstab entry

- Open `/etc/fstab` with admin privileges
- Add drive entry either using Drive Label or UUID

```
LABEL="DRIVE_NAME" none ntfs rw,auto,nobrowse
```
OR

```
UUID=1234567812345678 none ntfs rw
```

`LABEL` examples:

- SEGATE: `LABEL=SEGATE none ntfs rw,auto,nobrowse`
- My Drive: `LABEL=MY\ DRIVE none ntfs rw,auto,nobrowse`