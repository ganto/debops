Getting started
===============

.. contents::
   :local:

.. include:: ../../../includes/global.rst

Example inventory
-----------------

To manage the Check_MK agent on a given host or set of hosts, they need to be
added to the ``[debops_service_checkmk_agent]`` Ansible host group in the
inventory:

.. code:: ini

   [debops_service_checkmk_agent]
   hostname

Example playbook
----------------

If you are using this role without DebOps, here's an example Ansible playbook
that uses the ``debops.checkmk_agent`` role:

.. literalinclude:: ../../../../ansible/playbooks/service/checkmk_agent.yml
   :language: yaml

As you can see in this example playbook, the role makes use of a number of other roles to setup it’s environment.
Some of these dependency roles are only needed when services are detected.
This is true for the debops.mariadb_ role which is used to manage a database
user used to monitor the DBMS and databases by an automatically setup
and configured agent plugin. To ensure that
:envvar:`checkmk_agent__combined_plugins` is valid in the context of other
roles (in the same playbook) this variable is based on Ansible facts which are
setup by the ``debops.checkmk_agent/env`` role prior to other
dependency roles being called.
For more details, refer to :envvar:`checkmk_agent__plugin_autodetect`.
