# Build Docker image by [Packer](http://www.packer.io/)

## How to run

Install Docker and Packer on the machine and execute the following command.

```
$ packer validate sample-app.json
$ packer build -var 'version=v1.0.0' -var 'jdk7-base-image-version=v1.0.0' -var 'app_destination=/app' -var 'app_binary_url=https://github.com/mohitarora/coreos-vagrant/raw/master/application/dropwizard-sample-1.0-SNAPSHOT.jar' -var 'app_conf_url=https://raw.githubusercontent.com/mohitarora/coreos-vagrant/master/application/sample.yml' sample-app.json
```

Once packer creates a docker container, ansible is used to provision the container. Once container is provisioned an image is created and pushed to docker index.

## Ansible 

Ansible command that packer runs inside docker container

```
$ ansible-playbook {{.PlaybookFile}} -c local -i "127.0.0.1,"
```