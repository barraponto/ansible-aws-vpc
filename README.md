AWS VPC
=======

AWS VPC is a stub for defining AWS VPCs with minimal effort.

Requirements
------------

Depends on Python boto module, install with `pip install boto`.

Role Variables
--------------

Most variables come predictably from the [ec2_vpc module][1].
Internet Gateway route tables are automatically set up for subnets that
declare `internet_gateway` -- as long as you keep that magic route table
defined in `vars/main.yml`.

```yaml
aws_vpc_cidr_block: 172.0.0.0/16
aws_vpc_region: us-east-1
aws_vpc_resource_tags:
  Name: Default VPC
  ProvisionedBy: Ansible
aws_vpc_subnets:
  - cidr: 172.0.0.0/24
    internet_gateway: true
    resource_tags:
      Name: Default Subnet
      ProvisionedBy: Ansible
```

Example Playbook
----------------

This role can be run locally, from the localhost server.

    - hosts: localhost
      roles:
         - barraponto.aws_vpc

By default, it will register the default VPC under `aws_vpc_vpc`.
Should you need to operate in several VPCs in your playbook, the recommended
way right now would be to copy the role and rename it accordingly and
modifying the register variable declared in `tasks/main.yml`.

Parameterizing the register variable is a pending issue.
If you can contribute to it, please drop by the issue queue.

License
-------

BSD

Author Information
------------------

Please leave any support requests, bug reports or feature proposals in
Github Issue Queue: https://github.com/barraponto/ansible-aws-vpc
