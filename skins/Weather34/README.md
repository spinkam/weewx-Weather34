# Weather34 skin for WeeWX
Weather Station website skin with Live Data for WeeWX versions 3.9.2 or later.

Version WX-UB40-IHVN-0.9.1

Packaged for installation using wee_extension ulility

This repository contains the WeeWX version of Brian Underdown's Weather34 website template set. Brian's main website is https://weather34.com/homeweatherstation/index.html In January, 2019, Brian asked others to take over the distribution/maintainence of his design whilst he concentrated on development only for MB NanoSD, called Weather34 MB-SMART. 

This version requires WeeWX version 3.9.2 or later software. WeeWX is available at http://weewx.com

This version is designed explicitly to harness the powerful WeeWX database to generate the weather data charts and statistical data. It is built on the current MB-UB40-IHVN which is now maintained by Lightmaster (Meteobridge-Weather34-Template). A key metric for this project is to maintain design, functional and performance parity with the MB-UB40 parent. 

This version is assembled as an install package and uses the WeeWX utility wee_extension to install. This greatly simplifies the installation process from that of previous versions. Depending on your own WeeWX setup, minor edits may be required to be made to weewx.conf and Weather34 skin.conf files. Please see the Weather34 skin Installation Guide for detailed instructions.

# What's New in this Version WX-UB40-IHVN-0.9.1

1. A significant re-write for the generation of live and archive data processes which no longer relies on lookup tables. This completely separates this WeeWX version of any reliance on tracking the Meteobridge-API on which the original version of this template was built. Weather34 for WeeWX will continue to track its MB counterpart aesthetically but it is purely a WeeWX power unit under the hood (bonnet to the Brits like me).

2. Live and archive data output now fixed to a METRICWX base, which must not be changed. This will not affect your main WeeWX settings or other skins that you may have installed.

3. Fixed unit conversion issues that some users have experienced with charts and almanacs.

4. Significant update of the key module weather34.py which drives this template courtesy of Jerry Dietrich. This update includes retention of live data in a cache preventing data gaps in w34realtime.txt file. This is particularly useful when using mutiple sensors with differing loop cycle frequencies. Also included in the module update is an alternative method of obtaining web service api data (for example forecasts, metar data etc). The default method is by weewxcron, however this sometimes does not work with some users' servers or hosts due to setups or restictions. The alternative method also allows better control over the frequency of calls, useful if the web services have daily limits.

5. Corrected the abbreviation of knots from 'kts' to the ISO preferred 'kn'

# Demo

A live example of Weather34 WeeWX skin can be seen at https://claydonsweather.org.uk

# Weather34 Historic Timeline of design 2014-2019 
https://weather34.com/homeweatherstation/weather34timeline/weather34timeline.html

# Template Screenshot
<p align="center">
  <img src="https://res.cloudinary.com/brian-underdown/image/upload/v1553679424/weather34_meteobridge2019_bzq4sa.png" width="550" title="weather34 meteobridge template ">
 
</p>

<p align="center">
  <img src="https://res.cloudinary.com/brian-underdown/image/upload/v1557158225/almanacs_m5vmum.jpg" width="550" title="weather34 meteobridge alamanacs ">
 
</p>

# Setup

Follow the instructions in the 'installation guide' (INSTALLATION_GUIDE.md) to install the template.
Browse to http://your/path/to/weewx/weather34/easywxsetup.php
There is no initial password when the page prompts the first time -- just press LOGIN to enter the page.
IMPORTANT set a password in the screen for future use -- your browser can remember it. This will make future updates    reasonably secure so only you can do the updates to the configuration.
Make setting entries in the easyweathersetup.php page and SAVE. The next time you run it, use the password you set in the step above.
Repeat running easywxsetup.php until the main screen appears as you like it.

# Diagnostics

A new utility diags.php was added to the distribution. It is useful for checking the installation of the WX-HWS template and showing (safely) the current settings.php/settings1.php file contents for debugging. Note: the entries for $password, $db_user, $db_pass are replaced with '********' to avoid unwanted disclosure of private information.

    run diags.php?show=info on your website to show the key info about the WX-HWS installation and required PHP function status
    run diags.php?show=settings on your website to safely show the current settings.php and settings1.php contents

# License

Copyright (c) 2016-2019 by Brian Underdown (https://weather34.com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Template”), to deal in the Template without restriction, including without limitation the rights to, can use, can not copy without prior permission, can modify for personal use, can use and publish for personal use ,can not distribute without prior permission, can not sublicense without prior permission, and can not sell copies of the Template, and subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Template.

THE TEMPLATE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE TEMPLATE OR THE USE OR OTHER DEALINGS IN THE TEMPLATE.

Attribution-NonCommercial 4.0 International based on a work at https://weather34.com/homeweatherstation
Non-weeWX versions Available

# An Excerpt from Meteobridge-Weather34-Template MB-UB40-RRW README.md
Github repository for the Meteobridge version of the original weather34 template 
Weather Template for Meteobridge users only 

# This work is not permitted to be used in any other versions without prior permission unless listed below 
# Permission is granted for use in Cumulus version maintained by Ken True 
# Permission is granted for use in Weewx version maintained by Ian Millard

*This work means CSS/SVG/PHP .

Meteobridge Version available via download maintained by Lightmaster (https://github.com/lightmaster/Meteobridge-Weather34-Template)

Cumulus Version available via download and more info supported by Ken True ( https://github.com/ktrue/CU-HWS ). This version now also supports WeeWX and WeatherCat


Apart from Brian Underdown without him, this template would never exist, I would aslo like to acknowledge the following people: -

Jerry Dietrich for his massive contribution in converting my wild ideas into reality, putting me straight on my mediocre coding skills and having the patience of a dozen saints.

William Bailey aka Lightmaster who maitains the MB version of Weather34. Incredibly helpful and always on the end of Telegram when I need a chat, night or day.

Ken True for sharing files and who makes my job of maintaining the weeWX version so much easier.

Thomas Sosio for his invaluable contribution in producing the Meteobridge lookup code to translate WeeWX database output.

David Marshall for contributing technical knowledge and solutions to create the wxchart .tmpl files and alternative solutions for weather alerts.

Taylormia for contributing his excellent setup example for instances where weeWX and server/template are remote to each other.

Gary Portellas for a helpful suggestion to further simplify the installation process.

All those unamed people who have helped me with testing updates

# Alternative versions

# Meteobridge
you can find the Meteobridge version maintained by Lightmaster (William) at 
https://github.com/weather34/Meteobridge-Weather34-Template34/

# Cumulus
you can find the Cumulus version maintained by Ken True (Saratoga) at 
https://github.com/ktrue/CU-HWS

# Weewx
you can find a Weewx version maintained by Ian Millard is also avaialble via 
https://github.com/steepleian/weewx-Weather34

# Weatherflow
you can find a Weatherflow version not maintained but fully tested as of May 5th 2019 
https://github.com/weather34/Weather34-Weatherflow


# This work is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License.
http://creativecommons.org/licenses/by-nc-nd/4.0/

# Credits and thanks to the contributors who made this all possible since 2015.

 Erik M Madsen for language idea and initial script
 
 Paul @komoka weather in Canada for continous support and testing 
 
 Josep for Spanish/Catalan language translation and for many ideas and refinements
 
 Pascal Catte French translation and ideas fowarded 
 
 Steve the developer of Cumulus for support and providing a platform to resolve issues 
 
 Mats Ahlklo Swedish translation and his work on using Davis weatherlink 
 
 Betejuice (Cumulus Forum) for providing a solution for meteor shower listings 
 
 Ken True (Saratoga) for kindly granting permission allowing use of many scripts he developed which gave inspiration and ideas  though not used today it was the inspiration that allowed to do something more suited to the design. 
 
 Eric Rechlin Special thanks for originally creating the theme switching and extensive work on metrics/non metrics
 
 Boris at smartbedded (meteobridge) for ongoing support and upkeep of meteobridge 
 
 Wim van der Kuil for the original meteobridge script 
 
 David St John at weatherflow for providing hardware for testing and his non bias logical views 
 
 Paul Wilman , Tina Thomas, Vaggos , Chuck M , Aaron Gersztoff , Ian Millard, and many many more for continous constructive supportive feedback .. 
