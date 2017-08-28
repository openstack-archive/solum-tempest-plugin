Prerequisites
-------------

Before you install and configure the solum-tempest-plugin service,
you must create a database, service credentials, and API endpoints.

#. To create the database, complete these steps:

   * Use the database access client to connect to the database
     server as the ``root`` user:

     .. code-block:: console

        $ mysql -u root -p

   * Create the ``solum_tempest_plugin`` database:

     .. code-block:: none

        CREATE DATABASE solum_tempest_plugin;

   * Grant proper access to the ``solum_tempest_plugin`` database:

     .. code-block:: none

        GRANT ALL PRIVILEGES ON solum_tempest_plugin.* TO 'solum_tempest_plugin'@'localhost' \
          IDENTIFIED BY 'SOLUM_TEMPEST_PLUGIN_DBPASS';
        GRANT ALL PRIVILEGES ON solum_tempest_plugin.* TO 'solum_tempest_plugin'@'%' \
          IDENTIFIED BY 'SOLUM_TEMPEST_PLUGIN_DBPASS';

     Replace ``SOLUM_TEMPEST_PLUGIN_DBPASS`` with a suitable password.

   * Exit the database access client.

     .. code-block:: none

        exit;

#. Source the ``admin`` credentials to gain access to
   admin-only CLI commands:

   .. code-block:: console

      $ . admin-openrc

#. To create the service credentials, complete these steps:

   * Create the ``solum_tempest_plugin`` user:

     .. code-block:: console

        $ openstack user create --domain default --password-prompt solum_tempest_plugin

   * Add the ``admin`` role to the ``solum_tempest_plugin`` user:

     .. code-block:: console

        $ openstack role add --project service --user solum_tempest_plugin admin

   * Create the solum_tempest_plugin service entities:

     .. code-block:: console

        $ openstack service create --name solum_tempest_plugin --description "solum-tempest-plugin" solum-tempest-plugin

#. Create the solum-tempest-plugin service API endpoints:

   .. code-block:: console

      $ openstack endpoint create --region RegionOne \
        solum-tempest-plugin public http://controller:XXXX/vY/%\(tenant_id\)s
      $ openstack endpoint create --region RegionOne \
        solum-tempest-plugin internal http://controller:XXXX/vY/%\(tenant_id\)s
      $ openstack endpoint create --region RegionOne \
        solum-tempest-plugin admin http://controller:XXXX/vY/%\(tenant_id\)s
