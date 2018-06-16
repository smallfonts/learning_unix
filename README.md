# learning_unix

## Searching for help

### Man commands

```
man 1 <command/application> (eg. man 1 apt-get)
man 2 <SystemCall>
man 3 <LibraryCall>
man 4 <Drivers> 
man 5 <Files> (eg. man 5 smb.conf)
```

> TIP: use more / less command shortcuts for naviation


### which command

If you want to know whether a command is installed or want to know it's path, you type
```
which <command>
```

### update man page

```
Red Hat: makewhatis
Ubuntu, SUSE: mandb
```

## Package management

### Problem of traditional installations

Traditional methods of installing a packing includes unzipping .tar.gz file and compiling a package with ./configure and make install

Such method of installations poses the below problem
1. Does not handle dependecies
2. It may override customized configuration files
3. It's hard to uninstall, especially if it was compiled from source
you don't have an atomic way of uninstalling the program. You have to trace every file that has been modified during make install and restore them.


### Benefits of packages
1. They preserve configuration files. If a new version of a configuration file is to be installed, it is saved as pkg.rpm.new. For example. when a newe version of httpd is installed, the httpd.conf is created httpd.conf.rmpnew
2. Dependencies are considered during installation
3. Pre and post install scripts can be deployed with the application
4. Multiple packages can be wrapped inside the same package for complex installations
5. They can be easily uninstalled including or excluding their dependencies

|System|Package Name| Installation command |
|Red Hat, SUSE| Red Hat Package .rpm| rpm <package>|
|Ubuntu, Debian| .deb| dpkg <package>|

#### Using RPM

query if rpm package is installed
```
rpm -qa | grep fxconnect-datasource
```
install package
> NOTE: rpm does not handle dependencies automatically. For example, if you tried to install vim using rpm -i vi, you will find that you will have to download other dependencies before the install of vim can proceed
```
rpm -i <package>
```
remove (erase) package
```
rpm -e <package>
```

