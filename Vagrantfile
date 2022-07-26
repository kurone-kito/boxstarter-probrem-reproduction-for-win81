# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vagrant.plugins = ['vagrant-reload', 'vagrant-vbguest']

  config.vm.box = 'jaswsinc/windows81'
  config.vm.box_check_update = true

  config.vm.communicator = 'winrm'
  config.vm.guest = :windows
  config.vm.network :forwarded_port, guest: 5985, host: 5985, id: 'winrm', auto_correct: true
  config.vm.network :forwarded_port, guest: 3389, host: 3389, id: 'rdp', auto_correct: true

  config.vm.provider 'virtualbox' do |vb|
    vb.gui = true
    vb.linked_clone = true
  end

  config.vm.provision 'set to start the WinRM service promptly at startup to reduce the connection overhead', type: 'shell', inline: 'sc.exe config winrm start=auto'
  config.vm.provision 'deploy the setup.windows launcher', type: 'file', source: 'startup.cmd', destination: '$HOME/AppData/Roaming/Microsoft/Windows/Start Menu/Programs/Startup/boxstarter.cmd'
  config.vm.provision :reload

  config.winrm.password = 'Passw0rd!'
  config.winrm.retry_limit = 30
  config.winrm.retry_delay = 10
  config.winrm.username = 'IEUser'
end
