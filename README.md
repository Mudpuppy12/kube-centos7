# Lab setup for Kubernetes on Centos 7 using Google Cloud compute engine.

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

# Useful Links:
https://kubernetes.io/docs/tutorials/stateless-application/expose-external-ip-address/
http://www.tothenew.com/blog/how-to-install-kubernetes-on-centos/
http://terrenceryan.com/blog/index.php/making-kubernetes-ip-addresses-static-on-google-container-engine/

# BUGS
I can't seem to get service load-balancer working with GCE. There apparenly is some additional configuration, but is not documented well at all.
So auto-creation of external LB will not work

