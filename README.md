# Description
Let's understand the basic of OpenStack Heat

# Important points to read heat templates

It's important to understand that there are two types of heat template.

- Heat template:
  defines what the heat template creates.
  consists of the following sections:
  - parameters
  - resources
  - outputs

- Environment file:
  sets input parameter values, and defines mappings between custom resource types and template file paths.
  consists of the following sections
  - resource_registry
  - parameters
  - parameter_defaults

For more details, please refer to the following documents.

# Document

Heat template grammar
- https://access.redhat.com/documentation/en-us/red_hat_openstack_platform/16.2/html/advanced_overcloud_customization/assembly_understanding-heat-templates#doc-wrapper

Description of each Heat resource type
- https://docs.openstack.org/heat/train/template_guide/openstack.html

## Practice No.1 

Let's create a heat stack by the following command:

```
$ source overcloudrc
$ openstack stack create -t instance.yaml -e env.yaml my_stack
```

Before running this command, you would need to create a flavor, image and network.
You can modify env.yaml if needed.

## Practice No.2

Let's check the created resources

```
$ openstack stack list
$ openstack stack list --nested
$ openstack stack resource list my_stack
$ openstack stack resource list my_stack --nested 10
$ openstack stack show <stack>
$ openstack stack resource show <stack> <resource>
$ openstack server list
$ openstack port list
```

## Practice No.3

Let's check the assigined IP address using the following command.

```
$ openstack stack resource show <stack> <resource>
```

## Practice No.4

Let's delete the created stack on Practice No.1

```
$ openstack stack delete my_stack
```

## Practice No.5

Let's check that all resources were removed

```
$ openstack stack list
$ openstack stack list --nested
$ openstack stack resource list my_stack
$ openstack stack resource list my_stack --nested 10
$ openstack server list
$ openstack port list
```

## Practice No.6

Let's change the instance name by modifying env.yaml, and create a heat stack.

## Practice No.7

Let's make it possible to specify a fixed IP address assigned to the port in `env.yaml`.

## Practice No.8

Let's create two ports and assign them to an instance by modifying `instance.yaml` and `port.yaml`, and then create a heat stack.

## Practice No.9

Let's create a new template file `network.yaml` to create a network, then integrate the create file to existing temlate files.
Other files might need to be modified

## Practice No.10

I think it's good idea to automate the setup process of creating test instances/flavors/images/networks/etc after deploying OpenStack.
Let's create your own template files to setup your verificatoin lab after deploying OpenStack.
