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
* EC2.PY & EC2.INI are configured and loaded ( see https://github.com/ansible/ansible/tree/devel/contrib/inventory )
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
  - Define Security groups 
Security groups can be defined in main.yml or as extra yaml file with the option --extra-vars

Ansible creates security groups with the following name scheme:
```
"vpc_{{ company }}_ENV_{{ aws_environment }}_sg_{{ item.name }}"
```

Ansible use this name scheme to modify and delete security groups.

Important notes: 

* During creation of a security group Ansible test if a security group with the same name already exist and exit with an error
* During modifying a security group Ansible tests if a security group exist, if not it will fail


To create a security group
```
# ansible-playbook aws_create_sg.yml
```
To modify a security group
```
# ansible-playbook aws_mod_sg.yml
```

# TO-DOs:
[TO-DOs](./TODO.md)

# Changelog:
[Changelog](./CHANGELOG.md)

# Contributing:
For any questions use github or email: github@mbloch.de
