Bamboo Configuration for a Java-based Project
=============

To demonstrate the Bamboo plugin for Jenkins, let's create a new Bamboo project for a Java project.

Click the `Create Plan` link included on the top-right of the header bar.

![Create Plan](##create-plan.png##)

Click the `Create New Plan` link.

![Create New Plan](##create-new-plan.png##)

Enter `Sauce Demo` in the `Project` field.

Enter `SAUCE` in the `Project Key` field.

Enter `Java` in the `Plan Name` field.

Enter `DEMO` in the `Plan Key` field.

![New Plan Details](##new-plan-details.png##)

Select `Git` in the `Source Repository` drop down list.

Enter `https://github.com/rossrowe/sauce-ci-java-demo` in the `Repository URL` field.

Enter `master` in the `Branch` field

![Source Repository Details](##plan-git.png##)

Click the `Configure Tasks` button to continue.

![Configure Tasks](##configure-tasks.png##)

Click the `Add Task` button.

![Add Task](##add-task.png##)

Click the `Maven Task 3.x` link.

![Maven Task](##maven-task.png##)

Enter `Run Tests` in the `Task Description` field.  Click the `Save` button.

The default values entered should be fine, so click the `Create` button.  We need to enter the Sauce configuration after the plan has been configured, so don't select the `Enable this plan` checkbox just yet.

Click the `Default Job` link on the left-hand navigation pane.

![Default Job](##default-job.png##)

Click on the `Miscellaneous` tab

![Misc tab](##misc-tab.png##)

Select the `Enable Sauce OnDemand` checkbox to enable the plugin.  The `Enable Sauce Connect` checkbox should be selected by default.  When selected, the Sauce plugin will launch an instance of [Sauce Connect](http://saucelabs.com/docs/sauce-connect) prior to the running of your Job.  This instance will be closed when the Job completes.

Select a browser to run our tests against from the `Browser` drop down list (let's pick Firefox 15 running in Windows 2008)

![Sauce options](##sauce-options.png##)

Click the `Save` button.  That's it, our configuration is all setup, let's run the tests!

* _Next_: [Integration with tests](##04-Integration-with-tests.md##)