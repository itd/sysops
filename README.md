# sysops: System Operations as Code

Rick Fisher - January 30, 2019

----

This will setup a web-based service. 
First, it will set up a virtual machine using Hashicorp's Vagrant. 
Post-deploy, the vagrant build will fire Ansible to execute
a playbook that will:

- Install and configure Nginx
- Push content (all managed via git)
- Set up basic system security firewall ports
- Start web services
- Configure services to be persistent (will start on system reboot)


Although this demo deploys VMs locally via Vagrant and Virtualbox, 
various public and private cloud environments can be managed with 
orchestration tools such as:

- Hashicorp: [Terraform](https://www.terraform.io/docs/index.html)
- RedHat/Ansible: [Ansible](https://docs.ansible.com)
- SaltStack: [Salt](https://docs.saltstack.com/en/latest/)
- Canonical: [Juju](https://jujucharms.com/)
- OpenStack: [Heat](https://wiki.openstack.org/wiki/Heat)
- AWS: [CloudFormation](https://docs.aws.amazon.com/cloudformation) _Note: AWS-specific_
- Google: [Cloud Deployment manager](https://cloud.google.com/deployment-manager/)
- Microsoft: [Azure Resource Manager (ARM)](https://docs.microsoft.com/en-us/azure/azure-resource-manager/)

## Prerequisites
- Ansible 2.6+ is installed and accessible to the user running Vagrant. [Reference vagrant site](https://www.vagrantup.com/docs/provisioning/ansible.html)
- Vagrant and VirtualBox are installed and configured. 
  Linux users may opt for libvirt/KVM as an alternative to VirtualBox.
- The playbook assumes Ubuntu 18.04+ (Bionic)
- The vagrant box is added

### How to add the vagrant box:
Do this ahead of time to speed-up the demo!

    vagrant box add generic/ubuntu1804
    

## How to use this  

Copy the code to your local dir

Run the following from the command line:

    vagrant up --provider=virtualbox

Other popular provider options include: ```vmware_fusion, libvirt, docker, hyper-v```

Ref: [Vagrant providers](https://www.vagrantup.com/docs/providers/basic_usage.html)

Vagrant will create the VM and automatically provision the system using ansible.

The output on the command line will show:

    "msg": [
        "~@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@",
        "~ ----> the remote IP address is:",
        "~      http://xxx.xxx.xxx.xxx",
        "~@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@",
        ""
    ]

Cut-n-paste the URL into your browser, and it "should" work.

 
 