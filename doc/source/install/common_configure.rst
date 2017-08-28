2. Edit the ``/etc/solum_tempest_plugin/solum_tempest_plugin.conf`` file and complete the following
   actions:

   * In the ``[database]`` section, configure database access:

     .. code-block:: ini

        [database]
        ...
        connection = mysql+pymysql://solum_tempest_plugin:SOLUM_TEMPEST_PLUGIN_DBPASS@controller/solum_tempest_plugin
