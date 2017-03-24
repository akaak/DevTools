### Using SSH

- using and switching github accounts
- how ssh identifies get used http://stackoverflow.com/questions/7548158/having-trouble-switching-github-accounts-on-terminal 



### What is ssh-agent?

- using ssh-agent with ssh http://mah.everybody.org/docs/ssh -- old article

- https://developer.github.com/guides/using-ssh-agent-forwarding/
- how does ssh-agent work? http://rabexc.org/posts/using-ssh-agent 

Instead, do the following:
<http://apple.stackexchange.com/questions/48502/how-can-i-permanently-add-my-ssh-private-key-to-keychain-so-it-is-automatically>

-- add automatically

----

ssh-cws@~ $ eval "$(ssh-agent -s)"
Agent pid 1049
cws@~ $ ssh-add -K ~/.ssh/do-disoka1
Identity added: /Users/ak/.ssh/do-disoka1 (/Users/ak/.ssh/do-disoka1)
cws@~ $ 

----



- if SSH is not enabled on the mac os x then, <https://bluishcoder.co.nz/articles/mac-ssh.html>

useful ssh background info: <http://www.linuxjournal.com/article/4412?page=0,1>
