#Unraid Bash Commands Cheat Sheet

## Restart Gracefully:
```bash
/etc/rc.d/rc.unRAID stop && shutdown -r now
```

## Watch Syslog:
```bash
tail -f --lines=100 /var/log/syslog
```

## Restart Plex
```bash
etc/rc.d/rc.plexmediaserver start
```

```bash
etc/rc.d/rc.plexmediaserver restart
```
