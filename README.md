Getting things done with Mouf
=============================

Mouf is a graphically oriented dependency injection framework. It is very modular and by
itself, it doesn't do much. But it comes with a bunch of libraries (MVC framework, ORM, etc...)

The _Getting Things Done_ project is an attempt to help you jump into the Mouf bandwagon, by
providing you with a full framework made of libraries designed for Mouf.

[Have a look at the manual, and start doing things right now with Mouf](http://mouf-php.com/packages/mouf/getting-things-done-basic-edition/)

Getting things done is a project helping you having a full featured development environment, featuring the Mouf2 framework and the most common libraries working with Mouf2 (MVC framework, ORM, etc...)

	# Let's download composer. If you don't have CURL installed
	# see other Composer install techniques at http://getcomposer.org/download/ 
	curl -s https://getcomposer.org/installer | php
	
	# Let's get started!
	php composer.phar create-project -s dev mouf/getting-things-done-basic-edition