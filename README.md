# ansible-role-qnd

This role is just and exercise. It builds a docker image from a dockefile and start N container from it, according to vars. It is not intended to be used in a real case.

# Requirements

* Ansible >= 2.1
* Python >= 2.6
* Docker-py >= 1.7.0
* Docker API >= 1.20

A public key must be provided for docker image build (see Dockerfile).

# Role Variables

See default/main.yml for example

    containers:
        "container_name": 
          image: MyImage
          tag: latest
          ipv4: 172.16.10.10
          ssh_from_host: True

Set ssh_from_host to True or False to enable access to container from host. 

     network_name: "MyNetworkName"
     subnet_class: 172.16.10.10/24
     gateway: 172.16.1.1

     dockerfile_path: ./path

Insert path of your dockerfile.

     key_to_keep: root_key

Provide a pattern to match authorized key to be kept. It should match what deployed from docker file.

     test_container: container_name

A container for testing connectivity to all other containers.

# Example playbook

    - hosts: localhost
      roles:
        - ansible-role-qnd

# Known issues
There is some issues with Ansible 2.6.x. See https://github.com/ansible/ansible/issues/42162
