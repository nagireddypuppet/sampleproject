1. Extracting hostnames
cut -d ',' -f 6 sample2-candidate-data.csv | cut -d '.' -f 1

2. Spliting csv based on TX and PX value
awk -F ',' '{print > ("hostnames"$3".csv")}' sample2-candidate-data.csv
cut -d '.' -f 1 hostnameTX.csv 
cut -d '.' -f 1 hostnamePX.csv


Standalone Puppet installation step on CentOS 6.10
---------------------------------------------------
# Install puppet repo
sudo rpm -ivh http://yum.puppetlabs.com/puppetlabs-release-el-6.noarch.rpm

# Check Repo
sudo yum repolist | grep puppet

# Install Puppet
sudo yum -y install puppet 

# Verify puppet version
puppet --version


README for running ntp Puppet Module
-------------
1. copy file and goto ntpmodule directory
cd ntpmodule

2. Replace template file path in init.pp file as template file is not put in the module directories
puppet will not able to resolve the relative path

3. Command to run module
puppet apply init.pp --debug

Note: ntp.conf.erb template is replica of input file in case 1 