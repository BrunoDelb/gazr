VAGRANT_BOXES_DIRECTORY=$HOME/Vagrant/boxes
VM_MAC_BOX_NAME_MAC="yzgyyang/macOS-10.14"
VAGRANT_VM_DIR=$HOME/Vagrant/vm

vm-setup:
	@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$VAGRANT_VM_DIR vagrant plugin install vagrant-disksize

vm-start-%:
	# Values : macos, windows
	#@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$VAGRANT_VM_DIR vagrant provision $*
	@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$VAGRANT_VM_DIR vagrant up $*
	# To connect by SSH from a Mac, add in the file /etc/ssh/ssh_config a line "HostkeyAlgorithms ssh-dss,ssh-rsa"

vm-macos-start:
	VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$VAGRANT_VM_DIR VAGRANT_VAGRANTFILE=Vagrantfile.macos vagrant up
	#@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$VAGRANT_VM_DIR vagrant provision $*
	# To connect by SSH from a Mac, add in the file /etc/ssh/ssh_config a line "HostkeyAlgorithms ssh-dss,ssh-rsa"

#vm_launch_mac:
	#@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$VAGRANT_VM_DIR vagrant up ubuntu
	#@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) vagrant box list -i

vm-list:
	VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) vagrant box list -i

vm-stop-%:
	# Values : macos, windows
	@ VAGRANT_HOME=$(VAGRANT_BOXES_DIRECTORY) VAGRANT_CWD=$VAGRANT_VM_DIR vagrant halt $*

.PHONY: vm-setup vm-macos-start vm-list vm-start-macos vm-stop-macos vm-start-windows vm-stop-windows
