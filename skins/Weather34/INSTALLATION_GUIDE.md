# Installation Guide

Before you start it is a wise precaution to backup your databases, settings1.php and any customised files you wish to keep.

This installation guide assumes that you are already reasonably familiar with WeeWX and that it is already installed on your computer along with a webserver, php and curl. For a light-touch webserver.

If you have not already done so, you must update your WeeWX installation to version 3.9.2 or later. This is required to facillitate nested copying during the skin install process. Follow the various installation type links on this page http://www.weewx.com/docs/ for instructions on updating.

If you are carrying out a fresh install of WeeWX, my own personal preference is to use the setup.py method (http://www.weewx.com/docs/setup.htm). However, this increases the chances of requiring more path edits in the configuration files. Alternatively use one of the dedicated packaged installs (http://www.weewx.com/docs/debian.htm, http://www.weewx.com/docs/redhat.htm, http://www.weewx.com/docs/suse.htm or http://www.weewx.com/docs/macos.htm).

* Please familiarise yourself with the location of your WeeWX system files including your bin/user folder, skins folder and weewx.conf file. If you are unsure where to find these, please refer to the installation processes here: - http://www.weewx.com/docs/ which shows various WeeWX installation scenarios.

IMPORTANT. After installing PHP please make sure you install all the PHP modules appropriate for your version of PHP. Failure to due so may mean that forecasts and current conditions fail to update. This is an example for PHP7.3 modules on a Debian based distribution: -

	sudo apt-get install php-cli php-fpm php-json php-sqlite3 php-zip php-gd  php-mbstring php-curl php-xml php-pear php-bcmath
	sudo apt-get install libapache2-mod-php
	sudo a2enmod php7.3
	sudo systemctl restart apache2

* Install PyePhem (https://rhodesmill.org/pyephem/). Typically for a Debian based distro use 'sudo apt-get install python-ephem'


Once completed, make sure you save weewx.conf

* If you have have the CRT extension (Cumulus Real-Time) extension installed, unless you require it for another purpose, you can remove it now. (sudo ./wee_extension --uninstall crt)


* Download the current version of weewx-Weather34-master.zip file at https://github.com/steepleian/weewx-Weather34 to your bin folder (/home/weewx/bin for a setup.py install or /usr/bin for a DEB install).

* From the command line run the following code: -

		cd /home/weewx/bin (or cd /usr/bin)
		sudo ./wee_extension --install weewx-Weather34-master.zip
		
* After installation stop WeeWX and edit the weewx-conf file. Check that the install process added the following two sections. Adjust the paths to match your server if required. PLEASE NOTE. Do not change the unit_system from METRICWX. Selection of your unit preferences are made via the settings page (see below). The unit setting on other WeeWX skins you may be using will not be affected.

		# Options for extension 'Weather34'
		[Weather34RealTime]
   			 binding = loop
   			 unit_system = METRICWX
    			 filename = /var/www/weewx/w34realtime.txt
    
    			# RetainLoopValues 
    			exclude_fields = rain
    			cache_stale_time = 900
   			cache_directory = /tmp

		##############################################################################

		[Weather34WebServices]
    			filename = /var/www/weewx/weather34/settings1.php
			
* Once completed, make sure you save weewx.conf
			
* Start WeeWX.

* After around 5min your should find that folder the weather34 folder has been created in the weewx folder. [your_path]/weewx/weather34 will now be the location of the Weather34 skin in your web server.

* Stop WeeWX and change all files and folders recursively in the root of your server to 0775 using CHMOD and user to your Linux login name and groups to www-data using CHOWN, either via the CLI or your server Control Panel (if you employ one). I use Webmin http://www.webmin.com/deb.html, an open source control panel which will make your tasks much easier.

### IMPORTANT

* Restart weeWX.

* You can now test that the template is working by opening it up in your browser. Initially you will see random demo data. Click on the menu button at the top-left corner and select settings. This will open up a web form in which you apply your own settings. Pay particular attention to the location of the w34realtime.txt file being generated on a loop cycle by weeWX. The default location is “/[html_root]/weewx/w34realtime.txt” (for example /var/www/html/weewx/w34realtime.txt).

* A new feature is an alternative method of obtaining api data from web services (eg forecasts, metar, etc). This is particularly suitable for those who's servers/isps setups do not allow the weewxcron method. It also allows you to specify the frequency of calls so as not to exceed daily limits or put too much strain on the server. Selection of these services can be made towards the foot of the settings form page. If you use this method you must disable the weewxcron method by reanaming the file weewxcron.php to weewxcron.disabled. If you prefer to continue with the weewxcron method, set the 'Select web service codes' field in the settings form page to a blank (there is a blank option in the drop-down selection list)

* For an in depth guide on configuring a remote server please refer to 'taylormia_remote_server_setup.pdf'

* Finally re-start weewx and refresh your browser and you should see your own live weather station data. If things go wrong, check your settings carefully ensuring that the w34realtime.txt file and API keys and tokens have been correctly entered. 

* If you have any issues please raise directly with steepleian@gmail.com.
