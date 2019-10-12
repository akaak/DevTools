# Resources

## Serve github files
For serving static files Amazon S3 is a good solution. In addition, if you have files in github or as a gist then you can not really serve from there because the Content-Type header does not come out the way that the browsers want to see that file. You can get around this issue by serving these files through a service that can recognize the file content type.

- Create Git aliases
add the following to ''.gitconfig'
'''
[alias]
co = checkout
ci = commit
st = status
add-commit = !git add -A && git commit
alias = ! git config --get-regexp ^alias\. | sed -e s/^alias\.// -e s/\ /\ =\ /
'''


[RawGit](https://rawgit.com/) is a service that solves this problem. You can serve github and gist files with proper `Content-Type` header using RawGit. This works for file types such as HTML, JSON, CSS, JavaScript.

Try these two examples:
- Raw github [gist html file](https://gist.githubusercontent.com/akaak/840a8c44a9054a35fcb13198a7d6dc9b/raw/ac3423492386541a280892f711b11197c6f83687/simple-page.html) opens in the browser in raw html format. Try
[here](https://gist.githubusercontent.com/akaak/840a8c44a9054a35fcb13198a7d6dc9b/raw/ac3423492386541a280892f711b11197c6f83687/simple-page.html).
- Same gist html file hosted [via rawgit](https://cdn.rawgit.com/akaak/840a8c44a9054a35fcb13198a7d6dc9b/raw/6f3b746a534e8f456492568f67ca9acade0372c1/simple-page.html) opens in the browser in rendered form. Try [here](https://cdn.rawgit.com/akaak/840a8c44a9054a35fcb13198a7d6dc9b/raw/6f3b746a534e8f456492568f67ca9acade0372c1/simple-page.html).


**FILE CONTENT-TYPE HEADER VIA GIST:**

    $ curl -s -I https://gist.githubusercontent.com/akaak/840a8c44a9054a35fcb13198a7d6dc9b/raw/ac3423492386541a280892f711b11197c6f83687/simple-page.html | grep "^Content-Type"
    Content-Type: text/plain; charset=utf-8`

gives the Content-Type of **text/plain**. So, if you just pull up this url in the browser the browser does not render the page in HTML.

This is where <https://rawgit.com/> comes in useful. By running a github file or gist url through rawgit this service creates a caches version of this file and serves it via CDN and most importantly serves with the proper Content-Type header based on the file type.

**FILE CONTENT-TYPE HEADER VIA RAWGIT:**

    $ curl -s -I https://cdn.rawgit.com/akaak/840a8c44a9054a35fcb13198a7d6dc9b/raw/6f3b746a534e8f456492568f67ca9acade0372c1/simple-page.html | grep "^Content-Type"
    Content-Type: text/html;charset=utf-8

### How to only get the `Content-Type` from the curl response?
    curl -s -I https://cdn.rawgit.com/akaak/840a8c44a9054a35fcb13198a7d6dc9b/raw/6f3b746a534e8f456492568f67ca9acade0372c1/simple-page.html | grep "^Content-Type"`
    Content-Type: text/html;charset=utf-8

#### On a side note, how do you suppress progress meter from `curl`?

You can use the `-s` flag to use the curl in silent mode. This does not display the progress meter -
via [stackoverflow post](http://stackoverflow.com/questions/23675967/curl-show-content-type-only)


## Protecting AWS S3 buckets; for Static Website Hosting
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
Check git log in simple (pretty) format
`git log --pretty=oneline` is useful to see the summary of log in one line. Git's [viewing the commit history](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History) has many useful commands.

### Generate random text file

Generate a text file with 6 random dictionary words per line with a total of 10 Lines.
(from <http://www.skorks.com/2010/03/how-to-quickly-generate-a-large-file-on-the-command-line-with-linux/>)

`ruby -e 'a=STDIN.readlines;10.times do;b=[];6.times do; b << a[rand(a.size)].chomp end; puts b.join(" "); end' < /usr/share/dict/words > file.txt`

----
*last updated nov 2016 by [@akaak](http://github.com/akaak)*
