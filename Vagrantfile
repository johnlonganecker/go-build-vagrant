Vagrant.configure("2") do |config|
  config.vm.box = "tkausl/golang"

  config.vm.synced_folder ".", "/vagrant/src/github.com/starkandwayne/shield", create: true
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provision "shell", inline: <<-SHELL
  mkdir /vagrant/pkg
  mkdir /vagrant/bin

  chown -R vagrant:vagrant /vagrant/src
  chown -R vagrant:vagrant /vagrant/pkg
  chown -R vagrant:vagrant /vagrant/bin

  su - vagrant bash -c 'go get github.com/tools/godep'
  su - vagrant bash -c 'go get github.com/onsi/ginkgo/ginkgo'
  su - vagrant bash -c 'go get github.com/onsi/gomega'
  SHELL

end
