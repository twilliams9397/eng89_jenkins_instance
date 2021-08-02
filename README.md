# creating a Jenkins instance in vagrant
- set up VM with vagrantfile below:
```ruby
Vagrant.configure("2") do |config|

	config.vm.box = "hashicorp/bionic64"
	config.vm.network "private_network", ip: "192.168.10.100"
	config.vm.provision "shell", path: "provision.sh"

end

```
- the provision.sh contains the necessary install commands:
```linux
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt install openjdk-11-jdk -y
java -version
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo apt-get update -y
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ >> /etc/apt/sources.list.d/jenkins.list'
sudo apt-get install jenkins -y
```
- after sshing in (`vagrant ssh`) follow installation commands from https://www.jenkins.io/doc/book/installing/linux/ to install jenkins into vagrant machine
- go to the ip set in the vagrant file and add :8080 to access the jenkins server
- go to `/var/lib/jenkins/secrets/initialAdminPassword` to access
- if access is denied use `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`

# using amazon ec2 instance