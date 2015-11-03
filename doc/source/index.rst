rsyslog_client role docs
========================

Installation and setup of rsyslog for client use. This role will ship any
and all logs passed into it to any valid rsyslog target.  The role was
designed to be used within OpenStack Ansible by leveraging multiple logging
hosts via the **rsyslog_all** group. However if that group is not defined
additional log shipping targets can be used instead.


Basic Role Example
^^^^^^^^^^^^^^^^^^

.. code-block:: yaml

    - role: "rsyslog_client"
      rsyslog_client_log_rotate_file: test_log_rotate
      rsyslog_client_log_dir: "/var/log"
      rsyslog_client_config_name: "99-test-rsyslog-client.conf"
      rsyslog_client_log_files:
        - /var/log/dmesg
        - /var/log/udev
