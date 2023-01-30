# Provisioning project

​
What did you need to do to provision a vm to run mongo db?
-> configure vagrantfile and run it
​
What did you need to do to provision a vm to:
​

- Run the node.js application? -> provision installing npm
- Use the `nology.training` alias? -> create a new apache config file and swap it when the vagrant runs
- Use apache server to dirent traffic to a given port? -> configure apache config file
- How are you able to pass in the DB connection string? -> catch the IP, save it to the file and use it in script
  ​

---

​

## General Environment Questions

​

- What are development environments? -> collection of processes and tools that are used to develop the source code for a program or software product
- How do they relate to an application? -> Development environments enable developers to create and innovate without breaking something in a live environment.
  ​

### Virtual machines

​

- What is a virtual machine? -> A virtual machine (VM) is a virtual environment that functions as a virtual computer system with its own CPU, memory, network interface, and storage, created on a physical hardware system
- What does it allow you to do? -> By virtualizing your servers, you can place many virtual servers onto each physical server to improve hardware utilization. A VM provides an environment that is isolated from the rest of a system, so whatever is running inside a VM won’t interfere with anything else running on the host hardware.
- How have you used one? -> to set up database and node-app.
  ​

### Vagrant

​

- What is vagrant? -> Vagrant is an open-source software for building and maintaining portable virtual software development environments
- What is a `VagrantFile`? -> The primary function of the Vagrantfile is to describe the type of machine required for a project, and how to configure and provision these machines
  ​

#### CLI commands

​
| Command | What does it do? | When did you use it? |
| --------- | ---------------- | -------------------- |
| reload | reloads vm | after changing configuration |
| up | runs vm | starting vagrant |
| provision | provisions the vm | provisioning is installing and configuring software, including the operating system and applications, and connecting it to middleware, networks, and storage |
| destroy | destroys virtual machine | when shutting down the virtual machine |
| suspend | suspends the server | when you want to stop vm for some time |
| ssh | provides a secure encrypted connection between two hosts over an insecure network. This connection can also be used for terminal access, file transfers, and for tunneling other applications | when accessing terminal of the vm|
​

#### Provisioning

​

- What is Provisioning in relation to Vagrant?
  ​Provisioning in Vagrant allow you to automatically install software and alter configurations after running vagrant up

---
