Vagrant.configure("2") do |config|

  config.vm.box = "morea-framework/basic-box"
  config.vm.network :forwarded_port, host: 4000, guest: 4000
  config.ssh.forward_agent = true

  # Check if ~/.gitconfig exists locally
  # If so, copy basic Git Config settings to Vagrant VM
  if File.exists?(File.join(Dir.home, ".gitconfig"))
      git_name = `git config user.name`   
      git_email = `git config user.email` 
      config.vm.provision :shell, :inline => "echo 'Saving local git username to VM...' && sudo -i -u vagrant git config --global user.name '#{git_name.chomp}'"
      config.vm.provision :shell, :inline => "echo 'Saving local git email to VM...' && sudo -i -u vagrant git config --global user.email '#{git_email.chomp}'"
  end

end