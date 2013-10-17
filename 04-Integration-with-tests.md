Integrating tests with the Bamboo Sauce OnDemand plugin
=============

To run the tests, go the Bamboo dashboard. The plan wasn't enabled when we it was created, so click the `Enable plan` image.

![Enable plan](##enable-plan.png##)

Once the plan has been enabled, click the `Run` image.

![Run plan](##run-plan.png##)

This should compile and run three tests.

Once the build has finished, navigate to the `Sauce Jobs` tab.

![Sauce Jobs](##sauce-jobs-tab.png##)

Clicking on one of the links will present a page containing the Sauce report, which will allow you to view the steps performed and watch a video of the test.

![Sauce Report](##sauce-report.png##)

That's it, we've successfully configured Bamboo to run our tests against Sauce OnDemand!

To summarise, in order to make the most use out of the Sauce Bamboo plugin, the following steps should be performed:

* Update tests to reference the environment variables set by the plugin
* Output the Sauce session id to the stdout to allow the Sauce plugin to associate test results to Sauce Jobs

Referencing Job Configuration
---

As mentioned previously, the Sauce Bamboo plugin will set a series of environment variables that reflect the values entered on the Bamboo Job Configuration screen.

Your test code will need to be updated to reference these environment variables.

Below is some sample Java code which demonstrates how to reference the environment variables that are set by the Bamboo plugin

<!-- SAUCE:LOGIN -->
```java
	DesiredCapabilities desiredCapabilities = new DesiredCapabilities();
	desiredCapabilities.setBrowserName(System.getenv("SELENIUM_BROWSER"));
	desiredCapabilities.setVersion(System.getenv("SELENIUM_VERSION"));
	desiredCapabilities.setCapability(CapabilityType.PLATFORM, System.getenv("SELENIUM_PLATFORM"));
	WebDriver driver = new RemoteWebDriver(
				new URL("http://<!-- SAUCE:USERNAME -->:<!-- SAUCE:ACCESS_KEY -->@ondemand.saucelabs.com:80/wd/hub"),
                desiredCapabilities);

```

Output Sauce Session id
---

As part of the post build activities, the Sauce plugin will parse the test result files. It attempts to identify lines in the stdout or stderr that are in the following format:

	SauceOnDemandSessionID=<some session id> job-name=<some job name>

The session id can be obtained from the `RemoteWebDriver` instance and the job-name can be any string, but is generally the name of the test class being executed.

Below is a Java sample that demonstrates outputting the session id to the Java stdout.

```java
private void printSessionId() {

        String message = String.format("SauceOnDemandSessionID=%1$s job-name=%2$s", (((RemoveWebDriver) driver).getSessionId()).toString(), "some job name");
        System.out.println(message);
    }
```

Selenium Client Factory
---
An alternative to explicitly referencing the environment variables in your test code is to use the [Selenium Client Factory]() library.  This allows you to construct your SeleniumRC or WebDriver instances in a single line, eg.

```java
WebDriver webDriver = SeleniumFactory.createWebDriver();
```

Implementations of the library exist for [Java](https://github.com/infradna/selenium-client-factory) and [Python](http://sauceio.com/index.php/2012/01/selenium-client-factory-for-python/)

* _Next_: Have a Python project? Check out the [Python job configuration](##04-Python-Job-Configuration.md##) instead.
