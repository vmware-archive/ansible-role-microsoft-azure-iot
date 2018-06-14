Azure IoT
=========

This role provides features to create and manage Azure IoT resources.

Build Status
------------

[![pipeline status](https://gitlab.eng.vmware.com/vmworld2018/ansible-role-azure-iot/badges/master/pipeline.svg)](https://gitlab.eng.vmware.com/vmworld2018/ansible-role-azure-iot/commits/master)

Requirements
------------

You will need to supply Azure credentials to run this role.  Create an
application principal as described here:
https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal

Role Variables
--------------

TBD.

Dependencies
------------

This role does not explicitly depend on any other roles.

Example Playbook
----------------

Here's an example playbook:

    - hosts: servers
      roles:
         - { role: vmware.azure-iot }

License
-------

Apache 2.0
