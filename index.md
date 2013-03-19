Getting things done with Mouf
=============================

Mouf is a graphically oriented dependency injection framework. It is very modular and by
itself, it doesn't do much. But it comes with a bunch of libraries (MVC framework, ORM, etc...)

The _Getting Things Done_ project is an attempt to help you jump into the Mouf bandwagon, by
providing you with a full framework made of libraries designed for Mouf.

The "basic edition" of "Getting things done" contains:

- A MVC framework: [Splash MVC](http://mouf-php.com/packages/mouf/mvc.splash/)
- A database ORM: [TDBM](http://mouf-php.com/packages/mouf/database.tdbm/)
- A form generator: [BCE](http://mouf-php.com/packages/mouf/mvc.bce/)
- A template based on Twitter Bootstrap: [BootstrapTemplate](http://mouf-php.com/packages/mouf/html.template.bootstrap/)
- A menu system: [html.widgets.menu](http://mouf-php.com/packages/mouf/html.widgets.menu/)
- A cache system: [CacheInterface](http://mouf-php.com/packages/mouf/utils.cache.cache-interface/), with [APC](http://mouf-php.com/packages/mouf/utils.cache.apc-cache/) and [filesystem](http://mouf-php.com/packages/mouf/utils.cache.file-cache/) implementations 
- An internationalisation mechanism: [Fine](http://mouf-php.com/packages/mouf/utils.i18n.fine/)
- A logger: [ErrorLogLogger](http://mouf-php.com/packages/mouf/utils.log.errorlog_logger/)

You can of course add or remove packages as you wish, this is only a starting set.

Installing the full environment
-------------------------------

The first step is installing the environment.
This can be done in 2 lines!
Open a terminal, create a directory that will contain your project, move in this directory and then type:

	# Let's download composer. If you don't have CURL installed
	# see other Composer install techniques at http://getcomposer.org/download/ 
	curl -s https://getcomposer.org/installer | php
	# At this point, you should have a composer.phar file in your directory.
	
	# Let's download the whole project!
	php composer.phar create-project -s dev mouf/getting-things-done-basic-edition
	
This will download and install the template project, along all the dependencies. It can take up to 5 minutes for
the complete download, so grab a cup of coffee, and come back when it is downloaded.

Is it downloaded? Then you need to run the Mouf install process. As with most of the work in Mouf,
this is web-based.
Open your browser:
	http://[your_domain]/[your_path]/vendor/mouf/mouf
	
This will open the Mouf administration interface. Most of the work with Mouf is done via
this administration interface. The admin interface will ask you credentials to create your admin accout.

Once this is done, Mouf is installed. However, there are a number of packages that we need to install.
Click on the "Run install tasks" button to go to the install page.

![Mouf run install tasks](http://mouf-php.com/packages/mouf/getting-things-done-basic-edition/doc/images/run_install_tasks.png "Run install tasks")

On the install tasks page, click the "Run the install tasks" again.

![Mouf run install tasks](http://mouf-php.com/packages/mouf/getting-things-done-basic-edition/doc/images/run_install_tasks_2.png "Run install tasks")

The install process will start asking you to set up a database connection, the ORM classes, a base controller, etc...

At the end of the process, you should have a fully running environment.

Congratulations! 