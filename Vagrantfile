#!/usr/bin/env ruby

Vagrant::Config.run do |config|
  config.vm.box = "base"

  config.vm.forward_port 80, 8080, :auto => true

  config.vm.provision :chef_solo do |chef|
    
    chef.cookbooks_path = "cookbooks", "my_cookbooks"
    
    chef.add_recipe "apt"
    chef.add_recipe "build-essential"    
    
    chef.add_recipe "java"
    chef.add_recipe "ruby_build"
    chef.add_recipe "rbenv::system"

    chef.add_recipe "python"    
    
    chef.add_recipe "redis" # custom. just installs the redis-server package
    #chef.add_recipe "tabula"

    chef.json = {
      "rbenv" => {
        "rubies" => ["1.9.3-p392", "jruby-1.7.3"]
      }
    }
  end
end