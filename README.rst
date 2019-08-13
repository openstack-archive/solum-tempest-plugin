========================
Team and repository tags
========================

.. image:: https://governance.openstack.org/tc/badges/solum-tempest-plugin.svg
    :target: https://governance.openstack.org/tc/reference/tags/index.html

============================
Tempest Integration of Solum
============================

This directory contains Tempest tests to cover the Solum project, as well
as a plugin to automatically load these tests into tempest.

See the Tempest plugin docs for information on using it:
https://docs.openstack.org/tempest/latest/#using-plugins

* Free software: Apache license
* Documentation: https://docs.openstack.org/solum/latest/
* Source: https://opendev.org/openstack/solum-tempest-plugin
* Bugs: https://bugs.launchpad.net/solum

Running the tests
-----------------

To run all tests from this plugin, install Solum into your environment and
navigate to tempest directory::

    $ cd /opt/stack/tempest

Run this command::

    $ tox -e all-plugin -- solum_tempest_plugin

To run a single test case, run with the test case name, for example::

    $ tox -e all-plugin -- solum_tempest_plugin.camp.v1_1.test_plans.TestPlansController.test_create_camp_plan
