#You can use CWebDriverTestCase as a base class for your test.

Interface provided by CWebDriverTestCase is like classic Selenium PHPUnit\_Extensions\_SeleniumTestCase.

You can use CWebDriverTestCase like this:
```
<?php
require_once 'phpwebdriver/CWebDriverTestCase.php';
 
class WebTest extends CWebDriverTestCase
{
    protected function setUp()
    {
        $this->setBrowser('*firefox /usr/lib/firefox/firefox-bin');
        $this->setBrowserUrl('http://www.example.com/');
    }
 
    public function testTitle()
    {
        $this->open('http://www.example.com/');
        $this->assertTrue($this->webdriver->getTitle()=='Example Web Page');
    }
}
?>
```

You have methods: findElement, type, clear, select, click, isTextPresent.