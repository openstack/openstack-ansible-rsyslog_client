OpenStack rsyslog client
########################

Ansible role to deploy rsyslog for client use. This role will ship any and all
logs discovered in the ``rsyslog_client_log_dir`` directory to any valid
rsyslog target.  The role was designed to be used by OpenStack-Ansible by
leveraging multiple logging hosts via the **rsyslog_all** group. If that
inventory group is not defined additional log shipping targets can be defined
using ``rsyslog_client_user_defined_targets``

Default Variables
=================

.. literalinclude:: ../../defaults/main.yml
   :language: yaml
   :start-after: under the License.

Required Variables
==================

None

Example Playbook
================

.. code-block:: yaml

    - name: Install rsyslog
      hosts: rsyslog
      user: root
      roles:
        - role: "rsyslog_client"
          rsyslog_client_log_rotate_file: test_log_rotate
          rsyslog_client_log_dir: "/var/log"
          rsyslog_client_config_name: "99-test-rsyslog-client.conf"
          rsyslog_client_log_files:
            - /var/log/dmesg
            - /var/log/udev
