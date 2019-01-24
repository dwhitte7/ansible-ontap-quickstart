# Ansible for OnTap Quickstart 

This quickstart is created to expand the various examples that are listed on ansible.com and netapp.io to enable quick deployment and integration.

# Disclaimer
This Ansible quickstart and sample playbooks are written as best effort and provide no warranties or SLAs, expressed or implied.

# Repository includes:
1.  Ansible quick install RH7.5
2.  Sample Playbooks
3.  README
 
# Supported configurations:
1. RedHat 7.5
2. Ansible 2.6
3. Minimum ONTAP version - ONTAP 9.x

# Overview
This quickstart will help you setup/configure Ansible and the included NetApp modules and contains a few working examples to easily expand/adjust in your environment.



# Configuration
1   Install Ansible
Please follow your specific OS instructions form the official Ansible documentation here:
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

The following commands need to be run on the RedHat 7.5 host to complete the Ansible install, and dependencies on your server OS. The following is an example for RedHat 7.5,

subscription-manager register --username your_username --password your_password  
yum install python-pip python-wheel  
pip install --upgrade pip  
pip install ansible-lint  
pip install netapp-lib   
yum install rhel-7-server-extras-rpms  
yum install http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm  
yum install ansible  
yum install git  

2  NetApp cluster settings
Create a user and set the password for the ansible account:
Cluster::>security login create -user-or-group-name ansible -application ontapi -authentication-method password -role admin

Enable the API endpoint on the cluster in advanced mode:

Cluster::> set adv
Cluster::> system services web modify -http-enabled true

3   Download examples
On your host, find a suitable location and run the following command;
git clone  https://github.com/infragilis/ansible-ontap-quickstart

4   Set your variables
Open the vars.myml file and adjust to your environment, most variables will work without changing, the minimal changes are;
netapp_hostname: "clusterIP or name"
netapp_username: "ansible"
netapp_password: "xxx"

5   Test connectivity
Inside the example playbooks  there is a playbook called ‘facts.yml’ run the following command to test your connectivity.
ansible-playbook facts.yml
This should result in a large amount of data being returned from the cluster, or if anything is setup incorrect there will be clear errors to assist in troubleshooting, if more detailed troubleshooting is required run the playbook with debug enabled.
ansible-playbook facts.yml -vvv

7   Example playbooks

<coming soon>





# Support
Please enter an issue <<link required>> if you would like to report a defect
