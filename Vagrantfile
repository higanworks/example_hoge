# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.omnibus.chef_version = :latest

  %w{vm1 vm2}.each do |name|
    config.vm.define name.to_sym do |config|
      config.vm.box = 'opscode-centos-6.5'
      config.vm.box_url = 'http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box'
      config.vm.hostname = name
    end
  end
  config.vm.provision "chef_client" do |chef|
    chef.chef_server_url = "https://api.opscode.com/organizations/nri_test01"
    chef.validation_key_path = File.expand_path("../.chef/nri_test01-validator.pem", __FILE__)
    chef.validation_client_name = "nri_test01-validator"
  end

  #
  # If you're using the Opscode platform, your validator client is
  # ORGNAME-validator, replacing ORGNAME with your organization name.
  #
  # If you have your own Chef Server, the default validation client name is
  # chef-validator, unless you changed the configuration.
  #
end
