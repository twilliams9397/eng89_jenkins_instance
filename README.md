# creating a Jemkins instance in vagrant
- set up VM with vagrantfile specifying ubuntu/xenial64, same as in https://github.com/twilliams9397/eng89_vagrant_VM
```ruby
Vagrant.configure("2") do |config|

config.vm.box = "ubuntu/xenial64"

end

```
- after sshing in (`vagrant ssh`) follow installation commands from https://www.jenkins.io/doc/book/installing/linux/ to install jenkins into vagrant machine
- install openjdk version 9