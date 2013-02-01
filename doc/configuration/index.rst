Configuration
=============

General Structure
-----------------
Let's take a quick look at the general configuration structure:

.. code-block :: yaml

    tools:
        # Here goes configuration for all built-in tools (see "Tools" below).

    jobs:
        # Defines the jobs that need to be run on each build. This also defines the job's dependencies, and
        # its artifacts that should be persisted. Scrutinizer will use this information to schedule jobs in
        # the optimal order and will automatically parallelize jobs where possible.

Tools
-----
Most tools allow you to specify a global configuration which is applicable to your entire project, and also to override
this global config for selected sub-paths. The general structure looks like this:

.. code-block :: yaml

    tools:
        tool-name:
            config:
                # Global Configuration goes here

            path_configs:
                -
                    paths: [some-dir/*]
                    config:
                        # Configuration for all files in some-dir/ goes here

In the sections for the different languages, you find all the specific options which are available for each tool.

Jobs
----
Scrutinizer allows you to define which jobs should be performed as part of the build process. A typical job list might
look like this:

.. code-block :: yaml

    jobs:
        install_vendors:
            cmd: ./bin/install_vendors.sh
            stop_on_failure: true

        php_md:
            tool: php_mess_detector

        my_custom_script:
            cmd: ./bin/check.sh %path%
            depends: ["install-vendors"]

The above job list would be translated by Scrutinizer to be run as follows:

1a) Run job "install_vendors" immediately on installed package
1b) Run the tool "php_mess_detector" immediately on installed package
2) When 1a) has finished, run job "my_custom_script" on the package state after "install_vendors"

