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

You need to run jdownloader in background, so you can use screen for that.

```
screen -S jdownloader
cd jd
java -jar JDownloader.jar -norestart
ctrl a+d
```
You need to do this everytime your shared server is restarted.

Go to https://my.jdownloader.org/ in your browser and login to your jd account

You will see a Jdownloader@username option click on it to access your jdownloader instance.
