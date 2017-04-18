# This is lab testing in google cloud for kubernetes

# - Pre Steps:

 * Launch 5 compute engines named [kube-master,  kube-minion1, kube-minion2, kube-minion3, kube-minion4] using Centos 7.0 image
 * Create an ssh key on the kube-master, and add it to the root account on all hosts
 * Enable PermitRootLogin without-password in /etc/sshd_config, and restart sshd
 * yum install ansible, and use the host file provided in /etc/ansible.

# - Run the Plays from the kube-master:
 * ansible-playbook setup.yml
 * ansible-playbook configs.yml
 * ansible-playbook startup.yml

# Enjoy!


