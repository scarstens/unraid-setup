#Unraid Bash Commands Cheat Sheet

## Copy all video files in subfolders to current folder

```bash
find . -type f -exec file -N -i -- {} + | sed -n 's!: video/[^:]*$!!p' | xargs -I '{}' mv {} ./
```

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

## Copy file to server using SCP via SSH RSA
```
scp -P 2222 -i ~/.ssh/id_rsa  0_Sethflix_Preroll.mkv sethcarstens@192.168.2.198:/mnt/user/Movies
0_Sethflix_Preroll.mkv
```
