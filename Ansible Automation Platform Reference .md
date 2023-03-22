# Ansible Automation Platform Reference Architecture

The Ansible Automation Platform 2.1 reference architecture provides an opinionated setup of deploying a highly available Ansible Automation Platform environment. It provides a step-by-step deployment procedure with the latest best practices to install and configure Ansible Automation Platform 2.1. It is best suited for system and platform administrators looking to deploy Ansible Automation Platform.

A pictorial representation of the environment used in this reference environment is shown in Figure 1.1, “Reference Architecture Overview”.

![reference](/AAP/images/reference.jpg)

The image above consists of two sites, Ansible Site 1 and Ansible Site 2 for high availability. Site one is an active environment while site two is a passive environment. Each site consists of:

three node automation controller cluster with one PostgreSQL database
three node automation hub cluster with one PostgreSQL database
Two execution nodes per automation controller cluster
Access to console.redhat.com services such as Red Hat Insights and Service Catalog
In order to achieve HA for the PostgreSQL databases, configuration as code in conjunction with Git webhooks are used when push or merge events are triggered on a Git repository which in turn will configure the specified event on both Ansible Site 1 and Ansible Site 2.

Finally, to ensure logging consistency, a highly available centralized logging environment is installed that both Ansible Automation Platform environments will use.

The full document can be found at: https://access.redhat.com/documentation/en-us/reference_architectures/2021/html/deploying_ansible_automation_platform_2.1/overview