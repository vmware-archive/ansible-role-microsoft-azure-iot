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

Getting Started
---------------

For development or testing of this role, follow these steps.

* Clone this repo
* Install ansible and other requirements with pip:
  ```
  pip install -r requirements.txt
  ```
* Install required dependency roles
  ```
  ansible-galaxy install -r requirements.yml
  ```
* You can test the role with:
  ```
  molecule converge
  ```

Alternatively, you can build a docker container and test that way.

* Clone this repo
* Build the docker images
  ```
  docker build -t vmware/azure-iot .
  ```
* Run the image on the target role
  ```
  docker run -it azure-iot
  ```

License
-------

Apache 2.0
