#Difference between classic Selenium and Webdriver (Selenium 2)

Selenium 1 used Javascript to control browser. It was fine for simple web apps, but the more ajax/other javascript logic was embedded in application the more problems it created.

Webdriver (now integral part of Selenium2) uses native browser extension (each browser needs its own implementation) which is controlled by test script. Webdriver tests script can connect directly to browser (for example using FirefoxDriver) or remotely through Selenium Server (using JsonWireProtocol).

Generally Webdriver approach is much more faster and reliable.

Recommended article: http://google-opensource.blogspot.com/2009/05/introducing-webdriver.html