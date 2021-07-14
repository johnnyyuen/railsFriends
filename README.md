# Friends list app

> from Follow along video from youtube : https://www.youtube.com/watch?v=fmyvWz5TUWg&t=12417s

This app was developed from the Virtual Machine running in an Apple-Silicon-M1-CPU Macbook Air with UTM as the VM Host and running Ubuntu 20.04.2 guest OS
And then it push to the Heroku cloud services

Challenges:

> The VM Guest OS was not getting internet access
```
it fixed by updating the DNS server to 1.1.1.1 in the file /etc/resolv.conf
```
> The root filesystem (8GB root file system as the default setting from UTM) was not enough because when setup the postgresql DB, it used up 3GB to create the database.
```
I extended the root filesystem with 10GB by adding virtual disk file with the LVM commands
```
>This app was uploaded to Heroku https://friendsjysnt.herokuapp.com/, but initially the heroku cli is not working even I followed https://stackoverflow.com/questions/50492044/how-to-install-heroku-cli-on-raspberry-pi-3 to download the Heroku CLI for ARM. After research, below tasks need to be execute before it can successfully push to Heroku
``` 
sudo ln -s /usr/bin/node /usr/local/lib/heroku/bin/node

heroku git:remote -a friendsjysnt (friendsjysnt need to be updated to your app name)
bundle install --add-platform x86_64-linux
git push heroku main
```
