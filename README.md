# K8s-multinode-local

The purpose of this project is to create a Kubernetes cluster with one master and more nodes on a host.
All the nodes are created as VM. Using Vagrant and ansible the project get more structure and is easy to use.

The code was adapted from the article: (https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant) for my Mac Pro.

### Versions used:

- Vagrant 2.2.9
- Ansible 2.9.6
- Oracle VM 6.0.22
- Calico v3.15.0
## How to use it

### Start:
	vagrant up

### Test it from master node:
	vagrant ssh k8s-master 	# ssh to master
	kubectl get pods --all-namespaces
	tail -f /var/log/syslog

### Test it from host:
	mkdir ~/.kube
	sudo scp vagrant@192.168.50.10:/home/vagrant/.kube/config
	sudo chown $(id -un):$(id -gn) ~/.kube/config
	kubectl get pods --all-namespaces

### Stop and restart:
	vagrant halt

### Restart:
  	vagrant up
  
### Remove:
	vagrant destroy
  
## The same purpose projects:
- (https://github.com/maxim-zakharenkov/k8s-vagrant-ansible)
- (https://www.itwonderlab.com/ansible-kubernetes-vagrant-tutorial)
