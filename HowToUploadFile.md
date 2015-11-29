# How to upload file using php-webdriver-bindings #

Here is example how to upload file using php-webdriver-bindings.
We just need to get input-file element, send file directory using sendKeys method and finally submit element.

```
            $element = $this->webdriver->findElementBy(LocatorStrategy::id, "inputId");

            $element->sendKeys(array('file directory'));
            $element->submit();
```

If the example above doesn't work, add call to sendFile() with file directory as argument, then use the returned file path from that call to pass to sendKeys like follows:

```
            $element = $this->webdriver->findElementBy(LocatorStrategy::id, "inputId");
            $remoteNodeLocation = $this->webdriver->sendFile("file directory");
            $element->sendKeys(array($remoteNodeLocation));
            $element->submit();
```

What this does is send the file from the machine running the PHP test to the machine that is executing the browser test (e.g. machine running Selenium server JAR or the Selenium Grid2 node running the test), and then WebDriver? will use the transferred file on the Selenium browser machine to upload to the actual site/app under test. This case is especially applicable when the PHP test machine is not same as the Selenium machine or Grid node. More details:

http://sauceio.com/index.php/2012/03/selenium-tips-uploading-files-in-remote-webdriver/

http://stackoverflow.com/questions/10559728/uploading-files-remotely-on-selenium-webdriver-via-php

The above code sample is the PHP implementation/version of the feature available to the Java and other official language bindings.