.PHONY: vm

VAGRANT_BOXES_DIRECTORY=/Volumes/backup/Docker/Vagrant
VM_MAC_BOX_NAME_MAC="yzgyyang/macOS-10.14"

vm-setup:
	@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$HOME/DevOps/vm vagrant plugin install vagrant-disksize

vm-start-%:
	# Values : macos, windows
	@ echo "The external hard disk should be connected."
	@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$HOME/DevOps/vm vagrant provision $*
	@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$HOME/DevOps/vm vagrant up $*
	# Pour se connecter par SSH depuis un Mac, ajouter dans le fichier /etc/ssh/ssh_config une ligne "HostkeyAlgorithms ssh-dss,ssh-rsa"

vm-macos-start:
	@ echo "The external hard disk should be connected."
	VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$HOME/DevOps/vm VAGRANT_VAGRANTFILE=Vagrantfile.macos vagrant up
	#@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$HOME/DevOps/vm vagrant provision $*
	# Pour se connecter par SSH depuis un Mac, ajouter dans le fichier /etc/ssh/ssh_config une ligne "HostkeyAlgorithms ssh-dss,ssh-rsa"

#vm_launch_mac:
	#@ echo "The external hard disk should be connected."
	#@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$HOME/DevOps/vm vagrant up ubuntu
	#@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) vagrant box list -i

vm-list:
	@ echo "The external hard disk should be connected."
	VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) vagrant box list -i

vm-stop-%:
	# Values : macos, windows
	@ echo "The external hard disk should be connected."
	@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$HOME/DevOps/vm vagrant halt $*
