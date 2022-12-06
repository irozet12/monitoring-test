# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.synced_folder "./provisioning", "/vagrant/provisioning"
  config.vm.define "promigraph"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.extra_vars = {
      node_exporter_ver: "1.1.2",
      prometheus_ver: "v2.40.5",
      grafana_ver: "9.2.3",
      grafana_admin: "admin",
      grafana_passwd: "admin"
    }
  end
end
