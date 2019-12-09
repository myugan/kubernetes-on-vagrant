IMAGE = "ubuntu/bionic64"
N = 2

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.disksize.size = '20GB'
    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
    end
      
    config.vm.define "k8s-master" do |master|
        master.vm.box = IMAGE
        master.vm.network "private_network", ip: "192.168.10.11"
        master.vm.hostname = "k8s-master"
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "main.yml"
            ansible.tags = "master"
            ansible.extra_vars = {
                node_ip: "192.168.10.11",
            }
        end
    end

    (1..N).each do |i|
        config.vm.define "k8s-worker-#{i}" do |worker|
            worker.vm.box = IMAGE
            worker.vm.network "private_network", ip: "192.168.10.#{i + 11}"
            worker.vm.hostname = "k8s-worker-#{i}"
            worker.vm.provision "ansible" do |ansible|
                ansible.playbook = "main.yml"
                ansible.tags = "worker"
                ansible.extra_vars = {
                    node_ip: "192.168.10.#{i + 11}",
                }
            end
        end
    end
end
