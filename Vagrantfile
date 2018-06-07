Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :forwarded_port, guest: 4567, host: 4567
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision "bootstrap",
    type: "shell",
    inline: <<-SHELL
      sudo apt-add-repository ppa:brightbox/ruby-ng
      sudo apt-get update
      sudo apt-get install -yq ruby2.4 ruby2.4-dev
      sudo apt-get install -yq pkg-config build-essential nodejs git libxml2-dev libxslt-dev
      sudo apt-get autoremove -yq
      gem2.4 install --no-ri --no-rdoc bundler
    SHELL

  # add the local user git config to the vm
  config.vm.provision "file", source: "~/.gitconfig", destination: ".gitconfig"

  config.vm.provision "install",
    type: "shell",
    inline: <<-SHELL
      echo "=============================================="
      echo "Installing app dependencies"
      sudo chown -R vagrant:root  /var/lib/gems
      cd /vagrant
      sudo bundle config build.nokogiri --use-system-libraries
      sudo bundle install
    SHELL

  config.vm.provision "run",
    type: "shell",
    run: "always",
    inline: <<-SHELL
      echo "=============================================="
      echo "Starting up middleman at http://localhost:4567"
      echo "If it does not come up, check the ~/middleman.log file for any error messages"
      cd /vagrant
      bundle exec middleman server --watcher-force-polling --watcher-latency=1 &> ~/middleman.log &
    SHELL
end