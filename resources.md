# Resources

### Protecting AWS S3 buckets; for Static Website Hosting
- [Basic HTTP Auth for S3; protecting a Static website via basic authentication](http://www.yegor256.com/2014/04/21/s3-http-basic-auth.html)
 **(service provided by <http://s3auth.com>)**

### Take Website Screenshots (using Cron)

Cron script to run every 10 minutes. Use <http://crontab.guru> for examples for cron and use `crontab` to setup cron.

`*/10 * * * * /PATH-TO-SCRIPT/SCRIPT.sh`

The `SCRIPT.sh` would be a shell script with the script to take the website screenshot and output to a file with a timestamp.

```
#!/bin/bash
/usr/local/bin/webkit2png -TF --delay=5 -o /PATH-TO-OUTPUT/FILENAME-`date +%m%d%Y-%H-%M-%S` --ignore-ssl-check http://www.WEBSITE.com
exit
```

### How to rollback git commits
Related Article: <http://stackoverflow.com/questions/927358/how-to-undo-last-commits-in-git>

Follow these four (4) steps to roll back or undo the latest commit

The commit message does not even get into the git log
Check the log with `git log` before and after the undo.

```
git reset --hard HEAD^ 
git commit -m 'rolling back'
git log --pretty=oneline
git push origin master --force
```


----
*last updated nov 2016 by [@akaak](http://github.com/akaak)*
