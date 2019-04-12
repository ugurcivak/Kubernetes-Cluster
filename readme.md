#######Turkish
## VirtualBox, Vagrant, ve Kubeadm ile Çoklu Kubernetes Kümesi Oluşturma

Bu doküman ile birden fazla sunucu kullanarak Kubernetes Cluster oluşturulabilir.

### Ön Gereksinimler
[**Vagrant**](https://www.vagrantup.com/downloads.html "Vagrant"), 2.2.4
[**Virtualbox**](https://www.virtualbox.org/wiki/Downloads "Virtualbox"), 6.0

### Nasıl Çalışır?

	vagrant up

veya

	vagrant up mast
	vagrant up node
	vagrant up node2*

Yeni bir Kubernetes kümesini başlatmak için aşağıdaki vagrant komutunu uygulayın, bir master ve bir node başlatacaktır. Dilersek Vagrantfile'ı düzenleyerek node sayısını arttırabiliriz.

VM adı ya da sunucu RAM değeri değiştirilebilir.

    config.vm.define "mast" do |mast|
    mast.vm.box = "ubuntu/bionic64"
	mast.vm.network "public_network", ip: "192.168.1.150"
	mast.vm.network "public_network", bridge: "enp0s8:wlp3s01"
    	mast.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.name = "master"
        vb.memory = "2048"
		end
	end

##Nasıl Kaldırılır?

Vagrant ile oluşturulan VM/leri tamamen kaldırmak için halt ve destroy komutlarını uygulayın.

	vagrant halt
	vagrant destroy 

veya

	vagrant halt node2
	vagrant destroy node2
