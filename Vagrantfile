INTERNAL_NET_ONE="100.100.100."
INTERNAL_NET_TWO="192.168.1."
DOMAIN=".sample.com"
BOX="ubuntu/bionic64"

servers=[
  {
    :hostname => "server" + DOMAIN,
    :ip_one => INTERNAL_NET_ONE + "1",
    :ip_int_one => "1",
    :ram => "512",
    :cpu_count => "1",
    :cpu_cap => "50"
  },
  {
    :hostname => "nater" + DOMAIN,
    :ip_one => INTERNAL_NET_ONE + "2",
    :ip_int_one => "1",
    :ip_two => INTERNAL_NET_TWO + "1",
    :ip_int_two => "1",
    :ram => "512",
    :cpu_count => "1",
    :cpu_cap => "50"
  },
  {
    :hostname => "client" + DOMAIN,
    :ip_one => INTERNAL_NET_TWO + "2",
    :ip_int_one => "2",
    :ram => "512",
    :cpu_count => "1",
    :cpu_cap => "50"
  }
]

Vagrant.configure(2) do |config|
    config.vm.synced_folder ".", "/vagrant", disabled: true
    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = BOX
            node.vm.usable_port_range = (2200..2250)
            node.vm.hostname = machine[:hostname]
            node.vm.network "private_network", ip: machine[:ip_one], virtualbox__intnet: machine[:ip_int_one]
            if (!machine[:ip_int_two].nil?)
                node.vm.network "private_network", ip: machine[:ip_two], virtualbox__intnet: machine[:ip_int_two]
            end
            node.vm.provider "virtualbox" do |vb|
                vb.customize ["modifyvm", :id, "--memory", machine[:ram]]
                vb.customize ["modifyvm", :id, "--cpus", machine[:cpu_count]]
                vb.customize ["modifyvm", :id, "--cpuexecutioncap", machine[:cpu_cap]]
            end
        end
    end
end
