# -*- mode: ruby -*-
# vi: set ft=ruby:
home = ENV['HOME']

MACHINES = {
  :'node1' => {
      :box_name => "ubuntu/focal64",
      :box_url => "https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-vagrant.box",
      :box_cpu => "4",
      :box_mem => "16256",
      :priv_ip_addr => '192.168.56.201',
      :pub_ip_addr => '192.168.0.111',
    }
#   :'control' => {
#       :box_name => "ubuntu/focal64",
#       :box_url => "https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-vagrant.box",
#       :ip_addr => '192.168.56.202',
#   },
#   :'node3' => {
#       :box_name => "ubuntu/focal64",
#       :box_url => "https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-vagrant.box",
#       :ip_addr => '192.168.56.203',
#   }  

}

Vagrant.configure("2") do |config|

  MACHINES.each do |boxname, boxconfig|
      config.vm.define boxname do |box|
        
          box.vm.box_check_update = false

          box.vm.box = boxconfig[:box_name]
          box.vm.box_url  = boxconfig[:box_url]
          box.vm.host_name = boxname.to_s

          # box.vm.network "private_network", ip:boxconfig[:priv_ip_addr]
          box.vm.network "public_network", bridge: "enp5s0", ip:boxconfig[:pub_ip_addr]

          box.vm.provider :virtualbox do |vb|
            vb.name = boxname.to_s
            vb.customize ["modifyvm", :id, "--memory", boxconfig[:box_mem] || 1024 ]
            vb.customize ["modifyvm", :id, "--cpus", boxconfig[:box_cpu] || 1 ]
          end
          
        #   box.vm.provision "shell", inline: <<-SHELL
        #     sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
        #     sudo service sshd restart
        #   SHELL
      end
    end
      config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.galaxy_command = "ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path}"
        ansible.galaxy_role_file = 'requirements.yml'
        ansible.playbook = "playbook.yaml"
        ansible.become = "true"
        # ansible.verbose = "vvv"
      end
end
