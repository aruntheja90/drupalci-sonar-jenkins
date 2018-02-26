# DEPRECATED - Jenkins and SonarQube Drupal CI and Static Code Analysis

> **DEPRECATION NOTICE**: This project has been deprecated as of 2018; please see [Issue #27: Deprecate this project](https://github.com/geerlingguy/drupalci-sonar-jenkins/issues/27) for details and further discussion.

<img src="https://raw.githubusercontent.com/geerlingguy/drupalci-sonar-jenkins/master/screenshot.jpg" alt="Drupal CI SonarQube Dashboard" />

This Vagrant configuration (with Ansible for provisioning) will install Jenkins, PHP, SonarQube, and Drupal CI profiles for code analysis (along with a bunch of other required software).

How is this helpful? It's easy to track things like code complexity, lines of code, comment percentage, coding standards compliance, and test coverage over time. Code quality helps make Drupal more maintainable, especially as the project continues to grow!

## Quick Start Guide

### 1 - Install dependencies (VirtualBox, Vagrant, Ansible)

  1. Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads).
  2. Download and install [Vagrant](http://www.vagrantup.com/downloads.html).
  3. [Mac/Linux only] Install [Ansible](http://docs.ansible.com/intro_installation.html).
  4. Install Ansible roles: `ansible-galaxy install -r requirements.yml` (inside this directory).

Note for Windows users: *This guide assumes you're on a Mac or Linux host. Windows support may be added when I get a little more time; the main difference is Ansible needs to be bootstrapped from within the VM after it's created. See [JJG-Ansible-Windows](https://github.com/geerlingguy/JJG-Ansible-Windows) for more information.*

### 2 - Build the Virtual Machine

  1. Download this project and put it wherever you want.
  2. Open Terminal, cd to this directory (containing the `Vagrantfile` and this REAMDE file).
  3. Type in `vagrant up`, and let Vagrant do its magic.

Note: *If there are any errors during the course of running `vagrant up`, and it drops you back to your command prompt, just run `vagrant provision` to continue building the VM from where you left off. If there are still errors after doing this a few times, post an issue to this project's issue queue on GitHub with the error.*

### 3 - Configure your host machine to access the VM.

  1. [Edit your hosts file](http://www.rackspace.com/knowledge_center/article/how-do-i-modify-my-hosts-file), adding the line `192.168.99.9  drupalci.dev` so you can connect to the VMs.
  2. Open your browser and access [http://drupalci.dev/](http://drupalci.dev/).

## Notes

  - If you're running this on a production server (visible to the Internet), make sure you configure Jenkins and Sonar security, and set secret/complex MySQL passwords for both the root and sonar users! (When setting up Jenkins security, be careful to not lock yourself out; if you do, you need to edit the Jenkins config.xml file and restart Jenkins).
  - To shut down the virtual machine, enter `vagrant halt` in the Terminal in the same folder that has the `Vagrantfile`. To destroy it completely (if you want to save a little disk space, or want to rebuild it from scratch with `vagrant up` again), type in `vagrant destroy`.
  - Find out more about local development with Vagrant + VirtualBox + Ansible in this presentation: [Local Development Environments - Vagrant, VirtualBox and Ansible](http://www.slideshare.net/geerlingguy/local-development-on-virtual-machines-vagrant-virtualbox-and-ansible).
  - Learn about how Ansible can accelerate your ability to innovate and manage your infrastructure by reading [Ansible for DevOps](http://www.ansiblefordevops.com/).

## Author Information

This project was created in 2014 by [Jeff Geerling](https://jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
