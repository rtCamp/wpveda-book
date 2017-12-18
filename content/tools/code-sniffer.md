# Code Sniffer

_**TODOs**_

* [ ] Write about how to install _**phpcs** in Mac_

### Install `PEAR`

```
sudo apt-get install php-pear
```

### Install PHP\_CodeSniffer

```
pear install PHP_CodeSniffer
```

## Setup WordPress Coding Standards

```
cd $(pear config-get php_dir)/PHP/CodeSniffer/Standards
```

```
git clone git://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards.git
```

To setup WordPress Coding Standards

```
ln -s WordPress-Coding-Standards/WordPress WordPress
ln -s WordPress-Coding-Standards/WordPress-Core WordPress-Core
ln -s WordPress-Coding-Standards/WordPress-Docs WordPress-Docs
ln -s WordPress-Coding-Standards/WordPress-VIP WordPress-VIP
ln -s WordPress-Coding-Standards/WordPress-Extra WordPress-Extra
```

There are other standards as well such as WordPress-Core, WordPress-VIP & WordPress-Extra.

The WordPress standard encompasses a superset of the sniffs that the WordPress community may need. It includes sniffs for Core standards, but then it also includes sniffs for the WordPress VIP coding requirements, as well as some best practice Extras. If you just use the WordPress standard, you'll get everything. But if you're not working in the WordPress VIP environment, for example, this won't good for you. So there are additional standards included in this project, standards which include a subset of the sniffs in the WordPress standard. You can use all of the following as standard names when invoking phpcs:

* **WordPress-Core:** Sniffs that seek to implement the Core coding standards and go no further.
* **WordPress-VIP:** Core sniffs plus sniffs specifically implemented to check against the VIP coding requirements
* **WordPress-Extra:** Core sniffs plus any extras that are best practices but could be controversial.
* **WordPress-Docs:** Check the whether documentation is added properly or not.

Here is one liner

```
sudo apt-get -y install php-pear && sudo pear install PHP_CodeSniffer && cd $(pear config-get php_dir)/PHP/CodeSniffer/Standards && sudo git clone git://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards.git && sudo ln -s WordPress-Coding-Standards/WordPress WordPress && sudo ln -s WordPress-Coding-Standards/WordPress-Core WordPress-Core && sudo ln -s WordPress-Coding-Standards/WordPress-Docs WordPress-Docs && sudo ln -s WordPress-Coding-Standards/WordPress-VIP WordPress-VIP && sudo ln -s WordPress-Coding-Standards/WordPress-Extra WordPress-Extra
```



