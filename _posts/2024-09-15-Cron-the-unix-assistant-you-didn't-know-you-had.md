---
title: Cron-the Unix assistant you didn't know you had
excerpt: 
date: 2024-09-15
toc: true
tags:
  - linux
  - tutorials
header:
  teaser: /images/2024-09-15-Cron-the-unix-assistant-you-didn't-know-you-had/2024-09-15-Cron-the-unix-assistant-you-didn't-know-you-had-20240915122634371.png
---
{: .notice--primary}
*A short tutorial on automating recurring tasks on Unix systems with Cron.*

![2024-09-15-Cron-the-unix-assistant-you-didn't-know-you-had-20240915122634371](/images/2024-09-15-Cron-the-unix-assistant-you-didn't-know-you-had/2024-09-15-Cron-the-unix-assistant-you-didn't-know-you-had-20240915122634371.png){: width="50%"}

Do you have recurring tasks that thus far you had to run on your Unix (Linux/ Mac) system manually? This could be anything from making scheduled backups of a folder to syncing the contents of a file with a remote server. Fortunately, for us Unix users, there's a built-in service that allows you to automate all of this. Enter Cron.

#  Backing up with Cron 

Say we have a folder, `/home/ukh/MatD3` that needs backing up weekly. First we write a shell script to compress that directory and save it as a tar file with the date in the directory `/home/ukh/MatD3_backups/`. We will also check  for backups older than 90 days and delete them.

`backup-weekly.sh`:
```bash
tar -zcf /home/ukh/MatD3_backups/MatD3-$(date +%m%d%Y).tar.gz -C /home/ukh MatD3
find /home/ukh/MatD3_backups/* -mtime +90 -delete
```

You can run this script and test if it works. If it does, then we can move on to the step of automating the task with Cron.

## Adding a Cron job

To add a task to Cron, you can open the `crontab` file with the command: `crontab -e` and it will open with your default editor.
Add the following line to `crontab` to run the `backup-weekly.sh` script every week.

```shell
30 0 * * 1 sh /home/ukh/cronscripts/backup-weekly.sh
```

Remember to provide the absolute path of the `backup-weekly.sh` script. The syntax, `30 0 * * 1` tells Cron to run this task every Monday at 12:30 AM. The Cron syntax follows the format, `[minute (m)|hour (h)|day of month (dom)|month (mon)|day of week (dow)]`. The \* means "for any". For a verbose interpretation of the format, check out [this](https://crontab.guru) website.[^1]  

# Backing up to a remote server

It's always a good idea to backup your data externally in case something happens to your local system. `rsync` is a great utility that allows syncing a directory with another location. Unlike `scp` which performs a plain linear copy, locally, or over a network, `rsync` employs a special delta transfer algorithm and a few optimizations to make the operation a lot faster.[^2]

Let's say we want to sync our local directory `/home/ukh/MatD3_backups` with a similar location in a remote server, `timewarp-02.egr.duke.edu`. For this to be automated with Cron, it is important that you have your `ssh-keys` set for a password-less connection with the remote server. Read more on how to do that [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2).[^3]  

First let's test the `rsync` command, 

```shell
rsync -a --delete /home/ukh/MatD3_backups/ ukh@timewarp-02.egr.duke.edu:/home/ukh/MatD3_backups
```

If you get a `protocol version mismatch -- is your shell clean?` error, this is because your remote server outputs something to the terminal, probably due to output statements in the remote server's `.bashrc` or another startup script. To check this, run the following command and remove whatever is outputting to the terminal. `out.dat` should be a zero-length file.

```bash
rsh ukh@timewarp-02.egr.duke.edu /bin/true > out.dat
```

Once, you have that working we can automate the task with Cron. Add the following to your `crontab` which you can open with `crontab -e`.

```shell
0 2 * * * rsync -a --delete /home/ukh/MatD3_backups/ ukh@timewarp-02.egr.duke.edu:/home/ukh/MatD3_backups
```

`0 2 * * *` means run this task at 02:00 AM everyday. `--delete` will ensure that the expired backups will be deleted on the remote server as well. Note the forward slash in the local directory and the lack of one in the remote directory. This is to avoid making an additional directory `MatD3_backups` within the remote directory.  

If everything works, then you'll have a system that automatically makes scheduled backups and syncs them with a remote server. 
Happy Cron-ing!
# References

[^1]: [https://crontab.guru/](https://crontab.guru/) 
[^2]: [https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync](https://stackoverflow.com/questions/20244585/how-does-scp-differ-from-rsync)
[^3]: [https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2)