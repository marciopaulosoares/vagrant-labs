## Enable vagrant in windows subsystem

https://www.vagrantup.com/docs/other/wsl

~~~
$ export VAGRANT_WSL_ENABLE_WINDOWS_ACCESS="1"
~~~
~~~
$ export PATH="$PATH:/mnt/c/Program Files/Oracle/VirtualBox"
~~~

### In ubuntu subsystem
* vagrant up

## sample vagrant file
~~~
Vagrant.configure(2) do |config|
	config.vm.define "devops-box" do |devbox|
		devbox.vm.box = "ubuntu/focal64"
    		#devbox.vm.network "private_network", ip: "192.168.199.9"
    		#devbox.vm.hostname = "devops-box"
      		devbox.vm.provision "shell", path: "scripts/install.sh"
    		devbox.vm.provider "virtualbox" do |v|
    		  v.memory = 4096
    		  v.cpus = 2
			  v.customize [ "modifyvm", :id, "--uartmode1", "disconnected"]
			  v.gui = true
    		end
	end
end
~~~
