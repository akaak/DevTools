## TOOLS TO INSTALL 
*(on a New Dev Machine)*

**Last updated: Nov 2016**

1. Install pip
sudo easy_install pip  via http://stackoverflow.com/questions/17271319/installing-pip-on-mac-os-x 

2. Install Homebrew from http://brew.sh/index.html 
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
Installs xcode along with this brew



3. Install wget (using brew): https://coolestguidesontheplanet.com/installing-homebrew-os-x-yosemite-10-10-package-manager-unix-apps/ 

4. Install htttpie  https://httpie.org/#installation  
Example: 
http 'https://stg-api.nhtsa.gov/vehicles/byYmmt?modelYear=2009&make=honda&model=accord' -p h


5. Customizing terminal prompt http://blog.taylormcgann.com/2012/06/13/customize-your-shell-command-prompt/  or
http://bashrcgenerator.com/  interactive tool

6. Install Jekyll
gem install jekyll

7. Install homebrew - go to brew.sh for install instructions



>> Versions 

----
```
ak ~ $ python -V
Python 2.7.10
ak ~ $ pip -V
pip 8.1.2 from /Library/Python/2.7/site-packages/pip-8.1.2-py2.7.egg (python 2.7)
ak ~ $ ruby -v
ruby 2.0.0p648 (2015-12-16 revision 53162) [universal.x86_64-darwin15]
ak ~ $ brew -v
Homebrew 1.0.6
Homebrew/homebrew-core (git revision 8898; last commit 2016-10-08)
ak ~ $
```
----


8. Virtual Env
Install [virtualenvwrapper](http://virtualenvwrapper.readthedocs.io/en/latest/install.html)

Use `lsvirtualenv` and 	`workon` to use a virtualenv. See the [quickstart](http://virtualenvwrapper.readthedocs.io/en/latest/install.html#quick-start) for more information.

_If you see error installing virtualenvwrapper with pip_ then see this [stackoverflow post](http://stackoverflow.com/questions/32086631/cant-install-virtualenvwrapper-on-osx-10-11-el-capitan) and install individually.

Some errors could be related to Python's [six](https://pythonhosted.org/six/) package dependencies/conflicts.

---

Why doesnt .bashrc run automatically in the Terminal?

See this for an answer: <http://apple.stackexchange.com/questions/12993/why-doesnt-bashrc-run-automatically>

as one poster wrote, OS X reads in this order:

1. /etc/profile
2. ~/.bash_profile
3. ~/.bash_login
4. ~/.profile

- put source ~/.bashrc in ~/.bash_profile

