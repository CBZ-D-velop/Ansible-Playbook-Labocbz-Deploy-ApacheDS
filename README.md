# Ansible playbook: labocbz.deploy_apacheds

![Licence Status](https://img.shields.io/badge/licence-MIT-brightgreen)
![CI Status](https://img.shields.io/badge/CI-success-brightgreen)
![Testing Method](https://img.shields.io/badge/Testing%20Method-Ansible%20Molecule-blueviolet)
![Testing Driver](https://img.shields.io/badge/Testing%20Driver-docker-blueviolet)
![Language Status](https://img.shields.io/badge/language-Ansible-red)
![Compagny](https://img.shields.io/badge/Compagny-Labo--CBZ-blue)
![Author](https://img.shields.io/badge/Author-Lord%20Robin%20Crombez-blue)

## Description

![Tag: Ansible](https://img.shields.io/badge/Tech-Ansible-orange)
![Tag: Debian](https://img.shields.io/badge/Tech-Debian-orange)
![Tag: ApacheDS](https://img.shields.io/badge/Tech-ApacheDS-orange)
![Tag: SSL/TLS](https://img.shields.io/badge/Tech-SSL%2FTLS-orange)
![Tag: mTLS](https://img.shields.io/badge/Tech-mTLS-orange)

An Ansible playbook to deploy and configure ApacheDS on your host.

This playbook simplifies the installation and deployment of Apache Directory Server instances. The process begins by installing ApacheDS and subsequently copying the default instances to create the requested instances. Passwords and ports are also customized, and the instances are launched as services.

With this playbook, you can easily set up and manage ApacheDS instances, ensuring they meet your specific requirements. It's a powerful tool for streamlining the deployment of directory services and enhancing your directory server environment.

## Deployment diagramm

![Ansible-Playbook-Labocbz-Deploy-ApacheDS](./assets/Ansible-Playbook-Labocbz-Deploy-ApacheDS.drawio.svg)

This is a potential deployment achieved with this playbook. We can observe an ApacheDS service component, with the ApacheDS subsystem installed on a host. Within this setup, we have two LDAP instance components accessible through multiple ports. It's also possible to reinstall services without deploying new instances.

## Tests and simulations

### Basics

You have to run multiples tests. *tests with an # are mandatory*

```MARKDOWN
# syntax
# converge
# idempotence
# verify
side_effect
```

Executing theses test in this order is called a "scenario" and Molecule can handle them.

Molecule use Ansible and pre configured playbook to create containers, prepare them, converge (run the playbook) and verify its execution.
You can manage multiples scenario with multiples tests in order to get a 100% code coverage.

This playbook contains a ./tests folder. In this folder you can use the inventory or the tower folder to create a simualtion of a real inventory and a real AWX / Tower job execution.

### Command reminder

```SHELL
# Check your YAML syntax
yamllint -c ./.yamllint .

# Check your Ansible syntax and code security
ansible-lint --config=./.ansible-lint .

# Execute and test your playbook
molecule create
molecule list
molecule converge
molecule verify
molecule destroy

# Execute all previous task in one single command
molecule test
```

## Installation

To install this playbook, just copy/import this playbook or raw file into your fresh playbook repository or call it with the "include_playbook/import_playbook" module.

## Usage

### Vars

```YAML
# From inventory
---
# all vars from to put/from your inventory
# see tests/inventory/group_var for all groups and vars.
```

```YAML
# From AWX / Tower
---
all vars from to put/from AWX / Tower
```

## Architectural Decisions Records

Here you can put your change to keep a trace of your work and decisions.

### 2023-10-16: First Init

* First init of this playbook with the bootstrap_playbook playbook by Lord Robin Crombez

### 2023-10-19: Fix and push

* Playbook deploy ApacheDS
* Multiple instance are possible
* TLS available
* Edit of the default password

### 2023-12-16: System users

* Playbook can now use system users and address groups
* Updated with 10 years cert

### 2023-12-18: Fix and tests

* Fix default install
* Fix Java install
* Add tests for Java
* Boolean vars based deployment
* System user fix

### 2024-02-02: Latest

* Use latest version of role

### 2024-03-02: Remastered

* Imported new CICD
* Rework global on readme
* Rename of vars __ and refacto
* Removed free / remote user

### 2024-05-19: New CI

* Added Markdown lint to the CICD
* Rework all Docker images
* Change CICD vars convention
* New workers
* Removed all automation based on branch

## Authors

* Lord Robin Crombez

## Sources

* [Ansible playbook documentation](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_playbooks.html)
* [Ansible Molecule documentation](https://molecule.readthedocs.io/)
* [install_apacheds](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-ApacheDS.git)
