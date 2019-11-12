# davidAnsible

This repo is part of a workshop for provisioning and orchestrating local servers with the help of `Ansible` and Vagrant.

`Ansible` is a tool that lets you provision a bunch of servers with the same configuration without doing manual processes, also helps on automating scaling and provisioning from scratch. In more techie terms, `Ansible` generates an abstraction layer to `bash programs` using `YAML` syntax.

There's a lot of foundation concepts around, you will need to check the official docs for it.

## Vagrant

The `Vagrantfile` placed on the root of this repo, is a script that will define two `ubuntu/trusty64` machines with a static network IP address, also will copy a local SSH key (whatever you created)
to that machine in order to interact with it, and finally will disable the default shared folder configured by Vagrant automatically.

## Ansible Files

If you are familiar with `Ansible` terms, you will find that. the `hosts` file is the `Ansible Inventory` file, basically lets you specify the hosts, alias, and users to provision.

Then, the `ansible.cfg` is the main configuration file of the tool, you can provide default behavior to the `hosts` and treat it as global variables. Very useful for simplifying params configuration (in CLI args).

The `remote.txt` is part of using `Ansible tasks` to copy a file from the `local` environment to the `remote` environment (inside the Vagrant machines). The `example.txt.j2` illustrates the way that you can handle and perform loops on `Ansible`.

Finally, we have the `nginx.yml` file, is a `Ansible playbook` that lists the instructions for preparing and automating the installation of an `Nginx` server in the provided hosts (`hosts` file).

## Usage

First, you will need to install `Vagrant` and `Virtualbox` before running the machines. Then, you will run the `vagrant up` command, and thats it.

Assuming you have the `Ansible` tool installed, you just can:

`ansible-playbook nginx.yml -b -K`

You can check the IP from your browser and see the `Welcome page` from `Nginx`

## Credits

 - [David E Lares](https://twitter.com/davidlares3)

## License

 - [MIT](https://opensource.org/licenses/MIT)
