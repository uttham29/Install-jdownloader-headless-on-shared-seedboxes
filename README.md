# Install-jdownloader-headless-on-shared-seedboxes

Create a jdownloader account at https://my.jdownloader.org/

To install jdownloader you need to check if your shared seedbox provider has java.

```
java -version
```

After confirming that you have java, create a directory called jd

```
mkdir jd
```

Download jdownloader jar files from this link

> https://mega.nz/file/rZtxUCZR#9Bwj14qpVzJmJVZvIoIHUFmuvbOLUlCjxuJViNEOy9E

Upload that file to folder jd using ftp or sftp

Then

```
cd jd
java -jar JDownloader.jar -norestart
```

In first run it will try to update itself, once updating is finished you will be asked to restart

run the same command again

```
java -jar JDownloader.jar -norestart
```
Enter y when it asks for logins.

Enter your jdownloader logins now.

After few seconds click ctrl+c

You need to run jdownloader in background, so you can "either" use screen or create a systemd file

```
screen -S jdownloader
cd jd
java -jar JDownloader.jar -norestart
```

or 

If you provider allows creation of systemd files

```
mkdir -p ~/.config/systemd/user
nano ~/.config/systemd/user/jdownloader.service
```

paste this in nano editor

```
[Unit]
Description=JDownloader Service
After=network.target

[Service]
Environment=JD_HOME=%h/jd
ExecStart=/usr/bin/java -Djava.awt.headless=true -jar %h/jd/JDownloader.jar

[Install]
WantedBy=multi-user.target
```

```
systemctl --user daemon-reload
systemctl enable --now --user jdownloader
systemctl status --user jdownloader
```

Go to https://my.jdownloader.org/ in your browser and login to your jd account

You will see a Jdownloader@username option click on it to access your jdownloader instance.
