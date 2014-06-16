# This repo is deprecated, this tutorial now resides [here](https://github.com/saucelabs/docs/blob/master/markdown/ci-integrations/teamcity.md).
Sauce Labs + TeamCity Tutorial
====

This is the source code used for the tutorial available at
[http://saucelabs.com/teamcity](http://saucelabs.com/teamcity).

Organization
----

The basis of the tutorial is a series of markdown files. These can be edited,
but special care must be taken because some unconventional symbols/expressions
are used to create special behavior when the files are rendered on Sauce's
website.

Images are in img/

Conventions
----

Tutorial pages can be linked to each other by wrapping a URL with `##`, as
in the following example:

    [Link to intro page](##00-Introduction.md##)

The link will be processed to point to the correct place in the Sauce website.

The same convention can be used for images. It is assumed they are in the `img`
directory so that prefix is not necessary:

    ![A Cool image](##my_cool_image.png##)

(This will display the image located at `img/my_cool_image.png`).

Blocks of text which should only show up for specific platforms should be
wrapped like so:

    <!-- SAUCE:BEGIN_PLATFORM:MAC|LINUX -->
    .... some mac/linux only text here ....
    <!-- SAUCE:END_PLATFORM -->

Platform names can be `MAC`, `LINUX`, or `WIN`, and can be unioned by using the
pipe symbol.

You can insert the Sauce username or access key like so:

        vendor\bin\sauce_config.bat <!-- SAUCE:USERNAME --> <!-- SAUCE:ACCESS_KEY -->

Which will show up as &lt;username&gt; and &lt;access_key&gt; if the user is
not logged in.

If the user is not logged in, you can generate an inline signup form with:

    <!-- SAUCE:LOGIN -->

Contributing
----

If you find errors in the tutorials or ways that they can be improved, please
fork and send a pull request. We'd love your help in making these the best
instructions ever on how to get started with Jenkins and Sauce
Labs!

Authors
----

*  Ross Rowe ([rossrowe](http://github.com/rossrowe/))
