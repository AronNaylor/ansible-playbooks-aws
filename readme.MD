## Setup

Dynamic invetory needs to be placed in it's own directory, witht he following file structure:

```name_aws_ec2.yml```

You then reference that inventory file in the ansible config.

## Enable plugin

You then need to add the plugin you are using to the ansible.config file

```enable_plugins = aws_ec2```

## Calling ansible-inventory

```ansible-inventory --list --yaml```

## Using in Playbooks

For the hosts variable, set up so you can pass it in from the terminal:

```- hosts: "{{ passed_in_hosts }}"```

You can then call the file as usual with ```-e``` flag:

``` ansible-playbook -e "passed_in_hosts=all" playbooks/display-ec2-details.yml ```

## To terminate multiple ec2's using extra-vars

``` ansible-playbook -e '{"passed_in_hosts": [i-0df23ea3b68f25418, i-071bf878dffe317da]}' playbooks/terminate-ec2.yml ```
