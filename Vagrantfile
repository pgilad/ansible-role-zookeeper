VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.ssh.insert_key = false
    config.vm.box_check_update = false
    config.vm.box = 'ubuntu/trusty64'
    config.vm.network :private_network, ip: '192.168.50.5'

    config.vm.provider :virtualbox do |v|
        v.memory = 2000
        v.cpus = 2
        v.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        v.customize ['modifyvm', :id, '--ioapic', 'on']
    end

    config.vm.define 'zookeeper' do |machine|
        machine.vm.provision :ansible do |ansible|
            ansible.sudo = "yes"
            ansible.playbook = 'tests/test.yml'
            ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
        end
    end
end
