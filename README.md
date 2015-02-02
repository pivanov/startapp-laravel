Openshift-Laravel
=================

Use this repo to instantly create a Laravel 4.1 application on Openshift (https://www.openshift.com/)

Why Openshift is awesome for Laravel
------------------------------------
1. Free PaaS hosting for trying out code
2. Git push support
3. Full ssh access - great for running artisan commands 
4. Ability to schedule cron jobs and setup hooks
5. Easy to scale up

This repository will help you clone laravel 4.1 to your openshift gear with almost zero effort! It takes care of all the minutae involved in setup:

1. requirement of php directory (using symlink)
2. Composer installation (via hooks)
3. Dependency installation in the correct folder (composer install)
4. Using latest version of laravel (4.1.18 as of this writing)

How to use
----------

1. Log into your Openshift account
2. Under the "Applications tab", click on "New Application"
3. Select PHP 5.3 cartridge (or php 5.3 with Zend Server)
4. In the source code field, put in the address of this repository (https://github.com/mnshankar/openshift-laravel4.1)
5. Click on "Create Application"
6. Once your app is started, click on its url and you should see the Laravel welcome page!

NOTE
----
1. When creating your application in *Remember to select php 5.3*. The php 5.4 options that are currently available DO NOT have mcrypt bundled in them and so laravel will fail!

2. When cloning the repo to your local folder for development, bring down the package like so. The "laravel" folder can then be edited to contain your application logic:

```
git clone ssh://52ebddf14rtrec862e000040@php-mnshankar.rhcloud.com/~/git/php.git/
```

Remember
--------
1. The repo dir gets overwritten/refreshed *EVERY* time you do a git push.
2. Whenever you do a git push, composer repositories are (re) installed.
3. It is generally a bad idea to log into your gear via ssh and make code changes in your repo (as they will get wiped out during the next push!).
4. If you want something to remain between pushes, place them in the OPENSHIFT_DATA_DIR.
5. Composer install is time consuming, To prevent openshift from killing off the install task, a "process-timeout" config option has been set in composer.json.


Credits
-------
This repo borrows ideas from:
1. https://github.com/Fale/openshift-laravel4-quickstart
2. http://openshift.github.io/documentation/oo_user_guide.html
3. http://stackoverflow.com/questions/18094005/update-composer-phar-on-openshift

