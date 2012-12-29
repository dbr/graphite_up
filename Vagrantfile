# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'rubygems'

Vagrant::Config.run do |config|
  config.vm.box = "lucid32"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"
  config.vm.host_name = "graphite"

  config.vm.forward_port(80, 8080)
  config.vm.forward_port(9292, 9999)
  config.vm.forward_port(2003, 2003)
  config.vm.forward_port(8125, 8125, :protocol => 'udp')

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ['cookbooks']
    chef.json.merge! :tz => 'America/Chicago'

    chef.add_recipe 'apt'
    chef.add_recipe 'timezone'
    chef.add_recipe 'graphite'
    chef.add_recipe 'statsd'
    chef.add_recipe 'diamond'
    chef.add_recipe 'psycopg2'
   end
end
