Installing the Sauce plugin for TeamCity
=============

The Sauce OnDemand plugin for TeamCity can be installed by following these steps

# Download the [plugin zip file](https://repository-saucelabs.forge.cloudbees.com/release/com/saucelabs/teamcity/sauceplugin/<!-- SAUCE:PROP:teamcity-plugin-version -->/sauceplugin-<!-- SAUCE:PROP:teamcity-plugin-version -->.zip)
# Copy the zip file into your ~/.BuildServer/plugins directory

After the plugin has been installed, we will need to restart TeamCity for the plugin to be loaded.

Once TeamCity has been restarted, we can then configure the plugin to work with our environment.

* _Next_: [Configuring the Sauce TeamCity plugin](##04-Job-Configuration.md##)