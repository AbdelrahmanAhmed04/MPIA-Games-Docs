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
   <li>toggle.php: The toggle page (the toggler that controls if the cloaking is on or off)</li>
  <li>content.php: The offer page (the casino page that is showed to the real users)</li>
</ol>

## Setting up index.php
Most of the time you won't need to change anything in this page. Its code is pretty straight forward and the comments well explains everything. However, here are some highlights. You will find the code in the repository.

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

Defining either to allow desktop users or not
```php
/* change 'false' to 'true' to block desctop devices */
$CLOAKING['BLOCK_DESCTOP'] = false;
```

As you can see the code is easy and you won't need to miss that much with the code, just change the allowed countries and you will be good to go.

## index2.html

It will be simple html static page used as the white page for the googkle bots, you will find some pages we used in the website you can check them out. Please note the following when applying a new white page

<ol>
  <li>Make sure to compress all the images used as much as you can</li>
  <li>Make sure the page is responsive across different devices</li>
  <li>Make sure that the translation is correct</li>
  <li>Make sure to include any keywords mentioned by the managers</li>
</ol>
## toggle.php

This is a simple page with few lines of code, mainly its objective is to enable changing the cloaking from on to off and vice versa without having to edit the code itself. Its code works as following
1- The first 30 lines of code are mainly for styling the form, pretty straight forward
2- From line 30 to line 80, it verifies the login form and if the credentials were correct, a table with the options to turn the cloaking on or off will appear
  ![image](https://user-images.githubusercontent.com/89594421/232647272-ef8d3b52-7a2b-49da-8f6b-d9950f4e988b.png)
3- Here comes the main functionality of the page, it checks the cloaking state which can be changed from the table mentioned above, if the cloaking is off the names of the pages change as following

  ```php
  		$cloaking = $_GET['cloaking'];
		
		if ($cloaking == 'off') {
			rename("index.php","index2.php");
			rename("index2.html","index.html");
			?>
			<script>alert("Cloaking has been turned off.");window.location=window.location.href.split("?")[0];</script>
			<?php
		}
  ```
As you can see, this changes the <em>index.php</em> to <em>index2.php</em> which completly disables the cloaking (as the cloaking script won't be excuted at all), while it changes the <em>index2.html</em> to <em>index.html</em> so it's excuted however a bot or a real user access the page


Otherwise, if the cloaking is on, this code will be excuted.
```php
	elseif($cloaking == 'on') {
			rename("index2.php","index.php");
			rename("index.html","index2.html");
			?>
			<script>alert("Cloaking has been turned on.");window.location=window.location.href.split("?")[0];</script>
			<?php
  ```

Most of the times, you don't need to edit any of the toggle.php <strong>except for the lines where the url of the current page is mentioned</strong>. For example here
```html
<td><button class="btn btn-info" onclick="window.location='https://arabcen.com/bwcgu/'">Test</button></td>
  ```
</ol>

