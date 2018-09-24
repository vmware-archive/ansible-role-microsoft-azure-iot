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

You will most likely need to set all of the following values.

``` yaml
# The following come from the service application principal process described
# above.
azure_cli_application_id=<app id from application principal credentials>
azure_cli_application_key=<key from credentials>
azure_cli_tenant_id=<tenant from credentials>

# Name of the IoT Hub.
azure_iot_hub_name=my-iot-hub

# Resource group to contain the IoT resources (will be created if it doesn't exist).
azure_iot_group=my-iot-resources

# List of modules to deploy at the edge gateway. This is a sample module.
azure_modules:
  - name: tempSensor
    image: mcr.microsoft.com/azureiotedge-simulated-temperature-sensor:1.0
    desiredStatus: running
    restartPolicy: always
    createOptions: {}
    desiredProperties: {}

# Routes to ensure messages reach their destination.
azure_routes:
  - name: tempSensorToIoTHub
    route: FROM /messages/modules/tempSensor/outputs/* INTO $upstream

azure_device_stub: my-device
azure_device_count: 3

# Optional: name the deployment (to target all devices with a single deploy)
deployment_name: MyGlobalDeployment
```

Dependencies
------------

This role depends on:
* huxoll.azure-cli

Example Playbook
----------------

Here's an example playbook:

    - hosts: iot-api-box
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
