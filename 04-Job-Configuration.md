TeamCity Configuration for a Java-based Project
=============

To demonstrate the Sauce plugin for TeamCity, let's create a new TeamCity project for a Java project.

To create a new project, first click the `Administration` link on the top-right of the page.

![Administration](##administration.png##)

Click the `Create Project` button.

Enter `Sauce Demo` in the `Name` field, this should populate the `Project ID` field with `SauceDemo`.

Click the `Create` button.

![Create New Plan](##create-new-plan.png##)

Click the `VCS Roots` link.

![VCS Root Link](##vcs-root-link.png##)

Click the `Create VCS Root` button.

![VCS Root Button](##vcs-root-button.png##)

Enter `https://github.com/rossrowe/sauce-ci-java-demo.git` in the `Fetch URL` field.

Enter `master` in the `Default Branch` field.

Click the `Save Button`.

![Source Repository Details](##plan-git.png##)

Click the `Create Build Configuration` button.

![Create Build Configuration](##create-build-configuration.png##)

Enter `Maven` in the `Name` field

Click the `VCS Settings` button.

![Build Settings](##build-settings.png##)

Select the `https://github.com/rossrowe/sauce-ci-java-demo.git#master` option within the `attach existing VCS root` drop down list.

Click the `Add Build Step` button.

![Build Git](##build-git.png##)

Select `Maven` from the `Runner type` drop down list.

Enter `test` in the `Goals` field.

Click the `Save` button.

![Build Maven](##build-maven.png##)

Click the `Add Build Feature` button.

![Add Build Feature](##add-build-feature.png##)

Select `Sauce Labs Build Feature` from the drop down list.

![Sauce build feature](##sauce-build-feature.png##)

Enter the values of the username and access key you wish the Sauce plugin to use in the `Sauce User` and `Sauce Access Key` fields.

When the `Enable Sauce Connect` checkbox is selected, the Sauce plugin will launch an instance of [Sauce Connect](http://saucelabs.com/docs/sauce-connect) prior to the running of your Job.  This instance will be closed when the Job completes.

If a single browser is selected, then the `SELENIUM_PLATFORM`, `SELENIUM_VERSION`, `SELENIUM_BROWSER` and `SELENIUM_DRIVER` environment variables will be populated to contain the details of the selected browser.  If multiple browsers are selected, then the `SELENIUM_BROWSER` environment variable will be populated with a JSON-formatted string containing the attributes of the selected browsers.  An example of the JSON string is:

```json

[
	{
	"platform":"LINUX",
	"os":"Linux",
	"browser":"firefox",
	"url":"sauce-ondemand:?os=Linux&browser=firefox&browser-version=16",
	"browser-version":"16"
	},
	{
	"platform":"VISTA",
	"os":"Windows 2008",
	"browser":"iexploreproxy",
	"url":"sauce-ondemand:?os=Windows 2008&browser=iexploreproxy&browser-version=9",
	"browser-version":"9"
	}
]
```

The plugin will set a series of environment variables based on the information provided on the Job Configuration. These environment variables can either be explicitly referenced by your unit tests, or through the use of the [selenium-client-factory](https://github.com/infradna/selenium-client-factory) library.

* `SELENIUM_HOST` - The hostname of the Selenium server
* `SELENIUM_PORT` - The port of the Selenium server
* `SELENIUM_PLATFORM` - The operating system of the selected browser
* `SELENIUM_VERSION` - The version number of the selected browser
* `SELENIUM_BROWSER` - The browser name of the selected browser.
* `SELENIUM_DRIVER` - Contains the operating system, version and browser name of the selected browser, in a format designed for use by the [Selenium Client Factory]()
* `SAUCE_ONDEMAND_BROWSERS` - A JSON-formatted string representing the selected browsers
* `SELENIUM_URL` - The initial URL to load when the test begins
* `SAUCE_USER_NAME` - The user name used to invoke Sauce OnDemand
* `SAUCE_API_KEY` - The access key for the user used to invoke Sauce OnDemand

![Sauce options](##sauce-options.png##)

Click the `Save` button.  That's it, our configuration is all setup, let's run the tests!

* _Next_: [Integration with tests](##04-Integration-with-tests.md##)