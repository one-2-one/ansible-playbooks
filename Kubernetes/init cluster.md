1. yum -y update
hostnamectl set-hostname kube-01
2. cat <<EOF>> /etc/hosts
ip.ip.ip.ip kube-01
ip.ip.ip.ip kube-02
ip.ip.ip.ip kube-03
EOF


yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin vim mc nc

cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF

yum install kubeadm-1.22 -y 

