# MPIA-Games-Docs
This documentation provides step-by-step instructions for setting up almpst all the scripts you will need on an MPIA Games website.

First, it covers how to set up Matomo Analytics, which is a powerful open-source web analytics platform that can help website owners track visitor behavior and gain insights into how their website is performing.

Next, it explains how to set up A/B testing, which is a technique that involves comparing two different versions of a webpage to see which one performs better. A/B testing can be used to optimize website design, improve conversion rates, and increase revenue.

The documentation also covers how to add the Smartlook code to a website. Smartlook is a powerful user behavior analytics tool that allows website owners to record and replay user sessions, analyze user behavior, and gain insights into how their website is being used.

In addition, the documentation explains how to add the Loading Bar script, which can be used to add a loading bar to a website to improve the user experience and reduce bounce rates.

The Parameters Forwarding script is also covered in this documentation, which allows website owners to forward certain parameters from the URL to their website's affiliate links. This is essential for monitoring the advertisments efficiency.

Finally, the documentation covers how to add the Map Resizer script, which can be used to automatically resize embedded maps on a website to fit the available space. This can help to improve the user experience and make it easier for visitors to navigate a website.

## Matomo Installation
<ol>
  <li>Install Matomo on-permise from their <a href="https://matomo.org/faq/on-premise/installing-matomo/">website</a></li>
  <li>Unzip the files</li>
  <li>Upload the files to the desired directory in your website using ftp</li>
  <li>Follow the steps and finish installing Matomo</li>
</ol>

This step is fairly easy, you just need to follow the Matomo installation guide and you will be fine

## The cloaking and the toggle
Cloaking is PHP code that simply shows a page to the real user different than the page viewed for google bots, this helps the page to be indexed probably in the search engines. Mainly you will have 4 files in each page
<ol>
  <li>index.php: Which will include the cloaking script</li>
  <li>index2.html: The white page (the travel agency page which is viewed to the search engines)</li>
  <li>content.php: The offer page (the casino page that is showed to the real users)</li>
  <li>toggle.php: The toggle page (the toggler that controls if the cloaking is on or off)</li>
</ol>

## Setting up index.php
Most of the time you won't need to change anything in this page. Its code is pretty straight forward and the comments well explains everything. However, here are some highlights.

Defining the names of the pages
```php
$CLOAKING['WHITE_PAGE'] = 'index2.html';//PHP/HTML file or URL used for bots
$CLOAKING['OFFER_PAGE'] = 'content.php';//PHP/HTML file or URL offer used for real users
```

Defining the allowed countries
```php
/* For example, if you enter 'RU,UA' in the next line, system will only allow users from Russia and Ukraine */
$CLOAKING['ALLOW_GEO'] = 'KW,AE,QA,CO,MA,EG';
```

