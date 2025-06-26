# Is it compulsory to always write ansible playbooks No, u may want to do simple task then #use adhoc commands such as below 

ansible -i inventory all -a "ls -lart"
# to create a file text.txt on all machines
ansible -i inventory all -a "touch text.txt"
# now make directory cloud on all machines

ansible -i inventory all -a "mkdir cloud"
# remove the cloud folder on all machines
ansible -i inventory all -a "rm -r cloud"
# To check the disk space on all hosts in an inventory file
ansible -i inventory all -m shell -a 'df -h'
# ansible ad hoc command to check the free memory or memory usage of hosts

ansible -i inventory all -a "free -m"
# to find ids on host machines

ansible -i inventory webservers -m shell -a 'id'
# first create a file touch /tmp/my-file.txt on the control server and push it to all #machines
# copy from the source to host machines
 touch /tmp/my-file.txt
 ansible -i inventory webservers -m copy -a "src=/tmp/my-file.txt dest=/tmp/my-file.txt"
 # to install apache on all machines

ansible -i inventory webservers -m apt -a 'name=apache2 state=present'
# You can check the status of a specific service on single hosts or server1

ansible -i inventory -m service -a 'name=apache2 state=started'