Vagrant.configure('2') do |config|
  config.vm.box = 'centos/7'

  # bastion VM
  config.vm.define 'bastion' do |bastion|
    bastion.vm.hostname = 'bastion.local'
    bastion.vm.network :private_network, ip: '192.168.13.100'

    # require vbguest plugin: vagrant plugin install vagrant-vbguest
    bastion.vbguest.auto_update = true
    bastion.vm.synced_folder '.', '/home/vagrant/ansible',
                             owner: 'vagrant', group: 'vagrant'

    bastion.vm.provision 'shell', inline: <<-SHELL
      sudo yum install epel-release -y
      sudo yum install ansible -y
    SHELL
  end

  # test server VM
  config.vm.define 'tomcat' do |tomcat|
    tomcat.vm.hostname = 'tomcat.local'
    tomcat.vm.network :private_network, ip: '192.168.13.113'

    tomcat.vbguest.auto_update = false
    tomcat.vm.synced_folder '.', '/vagrant', disabled: true
  end
end
