Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end

  config.vm.define "roletester" do |roletester|
#   roletester.vm.box = "bento/centos-6.10"
#   roletester.vm.box = "clouddood/RH7.5_baserepo"
    roletester.vm.box = "clouddood/RH7.9_infra"
    roletester.vm.host_name = "roletester.test.dev"
    roletester.vm.network "private_network", ip: "192.168.60.40"
    roletester.ssh.forward_agent = true

    roletester.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_BaseSystem.yml"
      ansible.inventory_path = "vagrant_hosts"
#     ansible.extra_vars = {:zookeeper_id => "#{id}"}
#    ansible.tags = ansible_tags
#    ansible.verbose = ansible_verbosity
#    ansible.extra_vars = ansible_extra_vars
#    ansible.limit = ansible_limit
    end
  end
  config.vm.define "pgadmin" do |pgadmin|
#   pgadmin.vm.box = "bento/centos-6.10"
#   pgadmin.vm.box = "clouddood/RH7.5_baserepo"
    pgadmin.vm.box = "clouddood/RH7.9_infra"
    pgadmin.vm.host_name = "pgadmin.test.dev"
    pgadmin.vm.network "private_network", ip: "192.168.60.41"
    pgadmin.ssh.forward_agent = true

    pgadmin.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_pgadmin.yml"
      ansible.inventory_path = "vagrant_hosts"
#     ansible.extra_vars = {:zookeeper_id => "#{id}"}
#    ansible.tags = ansible_tags
#    ansible.verbose = ansible_verbosity
#    ansible.extra_vars = ansible_extra_vars
#    ansible.limit = ansible_limit
    end
  end
end
