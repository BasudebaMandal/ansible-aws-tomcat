# ansible-aws-tomcat



On Target Server:
----------------

A)Login as root using the keypairs

B) Setup the necessary users and their passwords with

# sudo adduser USERNAME
# sudo passwd USERNAME

useradd -u 2000 -m ransible
password ransible (ransible123)

C) To enable ec2 instance for logging in by using user not keypair.

Edit /etc/ssh/sshd_config setting

For a valid user to login with no key
PasswordAuthentication yes

Also want root to login also with no key
PermitRootLogin yes

D) Enable user twith sudo capabilities

In /etc/sudoers, add below entry at bottom of the file for enabling sudo access.

ransible        ALL=(ALL)       NOPASSWD: ALL

E) Install wget and libselinux-python package
 yum install libselinux-python wget

G)Disable selinux
vi /etc/sysconfig/selinux

-------------

On Ansible Engine server:
------------------------
A)Create passwordless login between ansible engine and target application server.

ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub abcuser@10.101.41.38 and press enter (twice/thrice)


B) code downloaded to a folder from git
cp -rp /etc/ansible/ansible.cfg  .

Change the remote_user to ransible and inventory to hosts.
