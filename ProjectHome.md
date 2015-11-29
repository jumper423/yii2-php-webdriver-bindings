# Introduction #

This is site for developers of PHP bindings for Selenium WebDriver (Selenium 2).
This PHP library allows creating functional webdriver tests with PHP.

# Details #
Library comunicates with **Selenium Server** using [JsonWireProtocol](http://code.google.com/p/selenium/wiki/JsonWireProtocol).
Requires curl in PHP.
List of implemented methods: [implemented\_methods](implemented_methods.md).

<b>Latest version 0.9.1 works properly with Selenium server 2.37.0</b>

# Example #
```
require_once "phpwebdriver/WebDriver.php";
require("phpwebdriver/LocatorStrategy.php");

$webdriver = new WebDriver("localhost", "4444");
$webdriver->connect("firefox");                            
$webdriver->get("http://google.com");
$element = $webdriver->findElementBy(LocatorStrategy::name, "q");
$element->sendKeys(array("selenium google code" ) );
$element->submit();

$webdriver->close();

```
## combobox handling ##
```
        $this->webdriver->get($this->test_url);
        $element = $this->webdriver->findElementBy(LocatorStrategy::name, "sel1");
        $option3 = $element->findOptionElementByText("option 3");
        $option3->click();
        $this->assertTrue($option3->isSelected());

        $option2 = $element->findOptionElementByValue("2");
        $option2->click();
        $this->assertFalse($option3->isSelected());
        $this->assertTrue($option2->isSelected());
```

## Use your existing Selenium1 tests (also generated with Selenium IDE) ##
Use CWebDriverTestCase.php class which provides interface like classic selenium test class:
```
class WebTestCase extends CWebDriverTestCase
{
    protected function setUp()
    {
    	parent::setUp();
    	$this->setBrowserUrl('http://yourapp123.com');
    }

	/** generate screenshot if any test has failed */
    protected function tearDown()
    {
        if( $this->hasFailed() ) {
            $date = "screenshot_" . date('Y-m-d-H-i-s') . ".png" ;
            $this->webdriver->getScreenshotAndSaveToFile( $date );
        }
    	$this->close();
    }

    protected function testSomething( )
    {
        $this->open( "/index-test.php/user/login", "expect-div-with-this-id-after-load-page" );
        $this->type( "LoginForm_username", "your_login" );
        $this->type( "LoginForm_password", "your_pass" );
        $this->click( "login-button" );
		
        // getElement will try few times to find element 
        $this->getElement( LocatorStrategy::id, 'top-user-data' );
		
        $this->assertTrue( $this->isTextPresent( "Logged as: your_pass" ) );
    }
	//...
```
## Yii framework extension ##
Use Webdriver/Selenium2 in your Yii application: http://www.yiiframework.com/extension/webdriver-test




---

This project is sponsored by:  [3e software house](http://3e.pl)