Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.omnibus.chef_version = :latest # gets chef installed
  config.berkshelf.enabled = true

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "apt"
    chef.add_recipe "passenger_apache2"
    chef.add_recipe "postgresql"
    chef.add_recipe "postgresql::server"

    chef.json = {
      "postgresql" => {
        "password" => {
          "postgres" => "86643717dc6cb1111610b853bf48efbb" # this is just 'password.' should be changed for production, obviously.
        }
      }
    }
  end
end