## Playbook
```
ansible-playbook main.yml -i host --ask-vault-pass -vv
```


## Vagrantfile
simple Centos machine

## Vagrantfile_openshift_complete

Complete OCP installation: https://blog.openshift.com/using-openshift-3-on-your-local-environme

Step 7: Authenticate to OpenShift 3 with the web console

Now that we have everything up and running, you probably want to authenticate to the platform.  Let’s start by using the web console.  Open up your browser and go to the following URL:

https://10.2.2.2:8443




## Vagrant Centos Gui
```
config.vm.provider "virtualbox" do |v|
  v.gui = true
  v.memory = 2048
  v.cpus = 2
end
```

### Log into your vm:

```
$ vagrant ssh
```

Then switch to root:

```
$ sudo -i 
```

Then install the gui desktop collection of packages:

```
$ yum groupinstall -y 'gnome desktop'
$ yum install -y 'xorg*'
```


Next uninstall the following packages:

```
yum remove -y initial-setup initial-setup-gui
```

These packages are to do with agreeing to EULA agreements, which means it requires user interaction, which can prevent automated startups via vagrant.

### Next switch to the gui target:

```
$ systemctl isolate graphical.target
$ systemctl set-default graphical.target   # to make this persistant
```

You should now see the gui desktop in your virtualbox window. If not, then try restarting the box:

```
$ vagrant halt ; vagrant up
```
