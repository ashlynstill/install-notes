# Mac Dev Environment Setup
How to set up your new shiny Macbook like the rest of the super cool AJC news apps team

1. Things in code blocks... 

        $ like this! i'm a command!

    ...are what you put in the command line in your terminal application.

2. If the command starts with a ``$``, that just signifies a new prompt line in the terminal. Don't copy the ``$``, but copy everything after it.
	
	Example 1:

		$ COPY ALL OF THIS TEXT BUT NOT THE DOLLAR SIGN PLZ
	
	Example 2:

		NO DOLLAR SIGN ON THIS LINE SO COPY THE WHOLE LINE!

3. If something is incorrect on here or you have an issue, let me know! astill [at] ajc [dot] com


**Open up your terminal application and let's get started!**


## Xcode command-line Tools

    $ xcode-select --install

Your laptop should prompt you to install the command line tools. Install the tools and move on once that process has completed (about 5 minutes).

If it doesn't install, or there isn't an update for Xcode to install the tools, you'll have to download the command line tools from [here](http://developer.apple.com/downloads/index.action). You have to register, or you can log in with your Apple ID.

Search for "command line tools," and download the package appropriate to your version of OS X. Double click on the .dmg file in your downloads file, and proceed to install.


## Install homebrew
Homebrew is a package manager for your Mac, and helps with installing all the wonderful things you need in your development environment.

    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

It will ask for your password – type that, hit enter, then paste this command to make sure test homebrew:

	$ brew doctor

If everything checks out okay and homebrew is ready to install stuff, your terminal will print:

	Your system is ready to brew.

If anything isn't working properly, homebrew will tell you. Follow their instructions to get things working correctly.

####If you get ``Warning: /usr/bin occurs before /usr/local/bin``...
..run the command below, as recommended by Homebrew:

	$ echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile

This command takes everything between the single quotes and adds it (>>) to a file called .bash_profile in your user’s root directory (~/). Every time you open a new Terminal window or tab, .bash_profile is called. The export PATH line tells your system to look in /usr/local/bin first. Now run:

	$ source ~/.bash_profile
	$ brew doctor

Your system should be ready to brew now.


## Create local bin directory (``~/bin``) and ``.bash_profile``

	$ mkdir ~/bin

Add local bin directory to PATH in ``.bash_profile``
	
	$ vim ~/.bash_profile

Paste ``export PATH=$HOME/bin/usr/local/bin:$PATH:$HOME/.rvm/bin`` at top. 

Hit ``esc``, type ``:wq``, then hit enter to save and quit.

*Useful: If you just type ``:q`` instead of ``:wq`` it quits without saving the file.*

## Install Sublime Text 3

Download from [here](http://www.sublimetext.com/3) and follow install instructions

Link to ``subl`` in new ``/bin`` directory

	$ ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl ~/bin/subl


## Install git

	$ brew update
	$ brew install git

Easy enough. To make sure everything is still working with homebrew, run
	
	$ brew doctor

If you get ``Warning: /usr/bin occurs before /usr/local/bin``, run the command below, as recommended by Homebrew:
	
	$ echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile

Then run the following to reload the .bash_profile and test homebrew again

	$ source ~/.bash_profile
	$ brew doctor

Your system should be ready to brew now. To verify:

	$ which git

You should get ``/usr/local/bin/git``

Now, you can configure your git settings:
	
	$ git config --global user.name "Your Full Name"
	$ git config --global user.email "Your Email Address"
	$ git config --global color.ui auto
	$ git config --global core.editor subl

## Install RVM with Ruby

	$ \curl -sSL https://get.rvm.io | bash -s stable --ruby

## Install Python

	$ brew install python
	$ brew install python3
	$ brew linkapps

Add to ``.bash_profile``

	$ echo "export PYTHONPATH='brew --prefix'/lib/python2.7/site-packages:$PYTHONPATH" >> ~/.bash_profile

#### VirtualEnv:

	$ pip install virtualenv
	$ pip install virtualenvwrapper
	$ echo "export WORKON_HOME=$HOME/.virtualenvs" >> ~/.bash_profile
	$ echo "export PROJECT_HOME=$HOME/src" >> ~/.bash_profile
	$ echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.bash_profile


## MySQL

	$ brew install mysql --enable-load-infile --enable-memcached --with-archive-storage-engine --with-blackhole-storage-engine
	$ ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LauchAgents

Sequel Pro download [here](http://www.sequelpro.com/)


## PostgreSQL/Postgis

Be forewarned: Some of these things take a ~ looooong ~ time and make your computer sound like an airplane.

	$ brew install postgresql
	$ ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
	$ pip install numpy
	$ brew install proj geos json-c gdal
	$ brew install postgis --with-gui
	$ initdb /usr/local/var/postgres -E utf8
	$ pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start


## Node.js & Grunt CLI

	$ brew install nodejs
	$ npm install -g grunt-cli

## Perlbrew

	$ /curl -L http://install.perlbrew.pl | bash
	$ echo "source: ~/perl5/perlbrew/etc/bashrc" >> ~/.bash_profile

## Other install stuff
	
#### Quantum GIS: 

Install GDAL 1.10 and GQGIS from: [http://www.kyngchaos.com/software/qgis](http://www.kyngchaos.com/software/qgis)

#### XQuartz (Mac port of the X window system)

[https://xquartz.macosforge.org/landing/](https://xquartz.macosforge.org/landing/)


