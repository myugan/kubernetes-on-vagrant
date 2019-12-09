### Kubernetes on Vagrant

Provisioning kubernetes cluster using kubeadm on Vagrant with following specs:

- Kubernetes v1.16.3
- Flannel
- Etcd 3.3.15

#### Requirement
- Ansible
- Vagrant
- VirtualBox

#### Tested On
- Ansible 2.9.1
- Vagrant 2.2.3
- VirtualBox 6.0.x

### How To

```bash
$ git clone https://github.com/myugan/kubernetes-on-vagrant
$ cd kubernetes-on-vagrant
$ vagrant up
```

#### References

- https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/