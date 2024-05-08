0x0A. Configuration management
Resource

    Intro to Configuration Management
    Puppet resource type: file (Check "Resource types" for all manifest types in the left menu)
    Puppet’s Declarative Language: Modeling Instead of Scripting
    Puppet lint
    Puppet emacs mode
    Puppet CookBook

Installing puppet and puppet-lint

# installing puppet and puppet-lint
wget https://apt.puppet.com/puppet7-release-focal.deb && \
    dpkg -i puppet7-release-focal.deb && \
    apt-get update && \
    apt-get install puppet-agent puppet-lint -y

# confirming installation
puppet -V
puppet-lint -v

# If you get an error saying puppet command not found, source the path
source /etc/profile.d/puppet-agent.sh

Tasks
0. Create a file
1. Install a package
2. Execute a command
