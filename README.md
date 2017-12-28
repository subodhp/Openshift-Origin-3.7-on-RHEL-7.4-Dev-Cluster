# Openshift-Origin-3.7-on-RHEL-7.4-Dev-Cluster
Ansible setup Playbook for my Origin 3.7 Dev Cluster by Advanced Installation Method &amp; other misc scripts

Three VM's are hosted on VirtualBox. Admin Node, Master Node and App Node. For my setup, the Infra node responsibilities are merged with Master node.

Openshift Ansible Installer Version = openshift-ansible-openshift-ansible-3.7.16-1
Openshift Origin 3.7

OS Release -
NAME="Red Hat Enterprise Linux Server"
VERSION="7.4 (Maipo)"
ID="rhel"
ID_LIKE="fedora"
VARIANT="Server"
VARIANT_ID="server"
VERSION_ID="7.4"
PRETTY_NAME="Red Hat Enterprise Linux"
ANSI_COLOR="0;31"
CPE_NAME="cpe:/o:redhat:enterprise_linux:7.4:GA:server"
HOME_URL="https://www.redhat.com/"
BUG_REPORT_URL="https://bugzilla.redhat.com/"

REDHAT_BUGZILLA_PRODUCT="Red Hat Enterprise Linux 7"
REDHAT_BUGZILLA_PRODUCT_VERSION=7.4
REDHAT_SUPPORT_PRODUCT="Red Hat Enterprise Linux"
REDHAT_SUPPORT_PRODUCT_VERSION="7.4"
Red Hat Enterprise Linux Server release 7.4 (Maipo)
Red Hat Enterprise Linux Server release 7.4 (Maipo)

Useful Commands - 
hostnamectl set-hostname myadmin --static
nmcli con show -a
nmcli con add type ethernet con-name enp0s8 ifname enp0s8
subscription-manager register --username <<username>> --password <<password>> --auto-attach
yum install deltarpm
yum install -y net-tools
yum install wget git net-tools bind-utils iptables-services bridge-utils bash-completion kexec-tools sos psacct
iptables -t nat -A POSTROUTING -o enp0s8 -j MASQUERADE
systemctl stop firewalld
chgrp named -R /var/named
chown -R root:named /etc/named.conf
restorecon -rv /var/named
restorecon -rv /etc/named.conf
named-checkconf -z /etc/named.conf
echo "1" > /proc/sys/net/ipv4/ip_forward
ansible-playbook -i /etc/ansible/hosts ~/openshift-ansible-openshift-ansible-3.7.16-1/playbooks/byo/config.yml
