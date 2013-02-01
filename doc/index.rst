Scrutinizer CI Documentation
============================

Getting Started
---------------
scrutinizer ci is a hosted continuous inspection service for open-source as well as private code.

It runs static code analysis tools, runtime inspectors, and can also run your very own checks in your favorite language.

Inspections can be triggered manually, through Git pushes, or also for GitHub pull requests. Depending on how an
inspection is triggered, scrutinizer does not scan your entire project, but only those parts that changed which provides
you with highly relevant information. Furthermore, scrutinizer ci employs algorithms to filter out noise that you have
previously ignored.

In the future, we also plan to add support for collecting code metrics. This can be information like how many classes
your project has, lines of code, but also opens up possibilities to track things like how your application's performance
has developed over-time, or how the amount of database queries changed. The latter can for example help you to identify
code that introduced certain performance degradations.

Supported Languages and Tools
-----------------------------
Below, is the list of languages that we support at the moment. In addition, you can also always run custom commands as
long as their output format is among our supported formats.

Finally, we always love to add built-in support for more languages. If we are missing your favorite language/tool, please
just `open an issue <https://github.com/scrutinizer-ci/scrutinizer/issues/new>`_.

.. toctree ::
    :glob:
    :titlesonly:

    tools/*/index

Configuration
-------------
Scrutinizer uses configuration data in Yaml format to determine which build steps to conduct, it scans different
locations for this data. The first source that exists, will win:

1. Configuration data when manually scheduling a command
2. ``.scrutinizer.yml`` file in the root directory of your repository
3. Repository-wide configuration data (defined under the "Settings" tab of your repository)

To learn more about the configuration structure, see the :doc:`configuration chapter <configuration/index>`.

