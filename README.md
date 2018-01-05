# Synopsis:
An Ansible template which helps you to create/ modify/ delete AWS EC2 security groups

Creation:
 * Create security groups

Modification:
 * Modify security groups

Deletion:
 * Delete security groups

# Prerequisets:
* Ansible 2.4
* Python 2.7.10
* AWS Account and configured Access Key and Secret Access Key
* Set following AWS environment variable:
  - AWS_ACCESS_KEY_ID
  - AWS_SECRET_ACCESS_KEY

# Usage:

* Modify variables in 'group_vars/all/main.yml' to own needs.
  - Define aws_region
  - Define company name
  - Define Network Environment example: Test, DEV
  - Define VPC ID (optional)
  - Define VPC network adress block (optional)
  - Define Security groups and rules

Security groups can be defined in 'group_vars/all/main.yml' or as extra yaml file with the option --extra-vars.

To create a security group
```
# ansible-playbook aws_create_sg.yml (--extra-vars "@create_sg.yml)
```
To modify a security group
```
# ansible-playbook aws_mod_sg.yml (--extra-vars "@mod_sg.yml)
```
To delete a security group
```
# ansible-playbook aws_del_sg.yml (--extra-vars "@mod_sg.yml)
```

Important notes:

* Ansible creates security groups with the following name scheme:
```
"vpc_{{ company }}_ENV_{{ aws_environment }}_sg_{{ item.name }}" 
```
* During creation of a security group Ansible checks if a security group with the same name already exist and exit with an error
* During modifying of a security group Ansible checks if a security group exists looking up for the security group name
* During deletion of a securitu group Ansible checks if the defined security groups exists looking up for the security group name

# TO-DOs:
[TO-DOs](./TODO.md)

# Changelog:
[Changelog](./CHANGELOG.md)

# Contributing:
For any questions use github or email: github@mbloch.de
